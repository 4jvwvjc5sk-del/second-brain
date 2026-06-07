# LensReader

#projekt #pwa #web-app

## Was ist das?
PWA: Bilder/Text vorlesen — OCR (Tesseract.js) erkennt Text aus Fotos, ElevenLabs-TTS liest vor mit Wort-für-Wort-Highlight.
- **Source**: `~/Desktop/AI/Claude/VoiceReader/` (index.html, sw.js, manifest.json, icons)
- **Live**: https://resilient-figolla-46c92b.netlify.app/ (Netlify, Deploy via **Drag & Drop**, kein Git/CLI)
- **Installiert**: als Brave-PWA (`LensReader.app`)
- Single-File-Architektur: gesamtes JS/CSS in `index.html`, kein Build-Step.

## Deploy-Workflow
1. Lokal testen: `cd VoiceReader && python3 -m http.server 8000` → http://localhost:8000 (nicht file://, SW braucht http)
2. Ordner `VoiceReader/` per Drag & Drop auf app.netlify.com → Deploys
3. **Wichtig**: bei jeder Änderung an cachebaren Dateien `CACHE`-Version in `sw.js` hochzählen, sonst liefert der Service Worker bestehenden Nutzern die alte Version. Aktuell: `lensreader-v2`.

## Stand 07.06.2026 — Optimierungen umgesetzt
Drei Fixes + Icon-Angleichung (alles in index.html):
1. **`_dur`-Bug (kritisch)**: Multi-Chunk-Timing nutzte `b._dur` (immer undefined) → Wort-Highlight bei Texten >2500 Zeichen falsch. Jetzt via `character_end_times_seconds` korrekt kumuliert.
2. **`syncHighlight` Performance**: linearer O(n)-Scan + alle-Wörter-toggle pro Frame → ersetzt durch Binary Search + `wordMap[]` + inkrementelle DOM-Updates (nur geänderte Wörter).
3. **Parallele TTS-Calls**: Chunks via `Promise.all` statt sequentiell → Wartezeit von Σ auf max(T).
4. Base64-Decode-Schleife → `Uint8Array.from(...)`.
5. Header-Icon (war Mikrofon) an App-Icon (Linse + Schallwellen) angeglichen.

## Stand 07.06.2026 — Logo-Caching-Fix (sw.js)
Problem: User sah in der installierten PWA weiterhin das alte Logo, obwohl alle Icon-Dateien (icon.svg, icon-192/512.png, maskable) lokal bereits das neue Linsen-Design zeigen.
Ursache: Service Worker nutzt cache-first; alte Icon-PNGs lagen im Runtime-Cache und wurden nie ersetzt, weil der `activate`-Cleanup nur bei geändertem Cache-Namen alte Caches löscht — `CACHE` stand aber unverändert auf `lensreader-v2`.
Fix in `sw.js`:
1. `CACHE` → `lensreader-v3` (purged beim nächsten Laden alle alten Caches inkl. gestaltete Icons).
2. Alle Icon-PNGs ins `ASSETS`-Precaching aufgenommen, damit sie deterministisch frisch im neuen Cache liegen.
**Noch nötig (User):** Netlify neu deployen (Drag & Drop) + PWA in Brave neu installieren (deinstallieren → neu „Installieren"), da das OS das Installer-Icon separat und sehr hartnäckig cached.

## Stand 07.06.2026 — sw.js Bug-Audit (8× Gemini + Claude-Review)

Vollständiger Gemini-Audit von `sw.js` mit 8 Passes (bugs + quality focus) und Claude-Gegenprüfung jedes Passes.

### Behobene Bugs
1. **Async-Termination** — `caches.open().then(put)` war fire-and-forget; SW konnte vorher terminieren → `async/await` mit `event.respondWith` kapselt alles korrekt
2. **Kein `.catch()` beim fetch** — offline = unhandled TypeError → outer try/catch + `Response.error()` statt `throw`
3. **`url.includes()` unsicher** → `new URL().hostname === host` via `NETWORK_ONLY.some()`
4. **Non-HTTP-Schemes crashen Cache API** → `if (!url.protocol.startsWith('http')) return`
5. **Range-Requests brechen Safari Audio** → `if (request.headers.has('range')) return`
6. **Malformed URL crasht SW** → `try { url = new URL(...) } catch { return }`
7. **Navigation cached immer `/index.html` überschrieben** → `cache.put(request, ...)` statt fixem Key
8. **HTTP-Errors (500/404) bei Navigation nicht abgefangen** → `if (!res.ok) throw` → Fallback auf cachedtes `/index.html`
9. **`ignoreSearch: true` global** (war kurz drin) → Entfernt; würde falsche Query-Param-Antworten liefern; nur für Navigation-Fallback

### Bewusst abgelehnte Vorschläge
- **Opaque Responses cachen** (`res.status === 0`) — unkontrollierte Grösse, Sicherheitsrisiko
- **`Promise.allSettled` für addAll** — Assets sind kontrolliert; all-or-nothing ist gewünschtes Verhalten
- **Zwei separate Caches** (static/dynamic) — Overkill für diese PWA-Grösse
- **Cache-Limit-Funktion** — kein messbares Problem bei dieser App-Grösse

### Verbleibende bekannte Einschränkungen (bewusst akzeptiert)
- Infinite Cache Growth bei dynamischen Assets (kein Limit)
- Audio offline nicht verfügbar (range-bypass deaktiviert SW-Caching für Media)

### CACHE-Version
Aktuell: `lensreader-v3` (korrekt — wurde beim Logo-Fix gesetzt)

## Stand 07.06.2026 — speak/syncHighlight Vollaudit + Fixes (Gemini + Claude)

Gemini-Audit aller kritischen JS-Funktionen in `index.html` (speak, syncHighlight, chunkText, playBtn, callEL). Mehrere Passes.

### Behobene kritische Bugs
1. **MP3-Buffer-Merge (kritisch)** — Binäres Zusammenkleben mehrerer MP3-Chunks ist kein gültiges Audio-Format; ID3-Header korrumpieren die Wiedergabe, `audioEl.duration` war falsch → **Architektur-Wechsel: sequentielles Chunk-Playback** (eigene Blob-URLs pro Chunk, `audioEl.onended` → nächster Chunk)
2. **Timing-Drift bei Multi-Chunk** — `cumulativeOffset` ignorierte Silence-Padding am Chunk-Ende → **Gelöst automatisch**: per-Chunk-Timings ohne cumulative offset, da jeder Chunk eigenes `audioEl.currentTime` ab 0
3. **chunkText Regex verliert letzten Satz** — `/[^.!?]+[.!?]+/g` matcht nur Sätze MIT Satzzeichen, Rest wird verworfen → **Fix**: `lastIndexOf(' ', max)` Word-Boundary-Split + `[\s\S]*?(?:[.!?\n]+|$)` Regex
4. **Pause bei `currentTime=0` löst neuen API-Call aus** — `audioEl.currentTime > 0` Check schlägt fehl → **Fix**: `chunkBlobUrls.length > 0` als Prüfung
5. **Kein AbortController** — `fetch`-Requests liefen nach Stop weiter, verbrauchten API-Quota → **Fix**: `abortController.signal` in `callEL()`, neu erstellt bei jedem `speak()`
6. **`Promise.all` für alle Chunks** — bei vielen Chunks → ElevenLabs 429 Rate Limit → **Fix**: sequentielle `await callEL()` pro Chunk
7. **Highlight-Glitch beim Chunk-Übergang** — `currentTime` reset auf 0 → `activeIdx = -1` → alle Highlights gelöscht → **Fix**: bei `activeIdx === -1 && timings.length > 0` auf letztes Wort des Vorgänger-Chunks halten
8. **Progress-Bar off-by-one** — `activeIdx / totalWordCount` erreicht nie 100% → **Fix**: `(activeIdx + 1) / totalWordCount`
9. **Memory Leak bei API-Fehler** — Blob-URLs von partial generierten Chunks nie revoked → **Fix**: catch-Block revoked + reset `audioEl.src`
10. **Replay nach Playback-Ende** — `chunkBlobUrls.length > 0` aber `currentChunkIdx >= length` → kein Restart → **Fix**: Replay-Branch in playBtn-Handler

### Neue State-Variablen
```javascript
let chunkBlobUrls = [];    // Blob-URL pro Chunk (statt merged MP3)
let chunkTimings = [];     // Timing-Array pro Chunk (kein cumulative offset)
let currentChunkIdx = 0;
let abortController = null;
let totalWordCount = 0;
```

### Wichtig für Deploy
- `CACHE`-Version in `sw.js` auf `lensreader-v4` setzen vor Netlify-Deploy
- `audioEl.play()` gibt Promise zurück — `.then()/.catch()` korrekt verkettet

### Verbleibende bekannte Einschränkungen (bewusst akzeptiert)
- Gapless Playback nicht möglich mit HTML5 Audio (kurze Lücke zwischen Chunks)
- Kein Spam-Click-Debounce auf playBtn (Gemini empfohlen, aufgeschoben)

## Verbindungen
- [[regeln]] — Coding-Workflow mit Gemini (PFLICHT)
