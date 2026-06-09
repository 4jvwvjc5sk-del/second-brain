# YT: 2KEY — Native Windows KI-App mit Claude Code

#youtube #claude-code #windows #app-inspiration #dev-workflow

**Quelle:** https://www.youtube.com/watch?v=iTRZat7urvs
**Datum gesehen:** 2026-06-07

> **Status: Reines Wissen — nicht nutzbar auf Remys System**
> 2KEY ist eine native Windows-App. Remy arbeitet auf macOS — die App selbst ist nicht einsetzbar.
> Relevant als Inspiration für eigene Projekte und für die Claude Code Workflow-Tipps (Abschnitt unten).

---

## Was ist 2KEY?

Native Windows-App (früher "Lume"), die KI unauffällig in den Arbeitsalltag integriert.

**Aktivierung:** `Ctrl + Win` — öffnet eine minimale "Pille"-Overlay am Bildschirmrand

**Funktionen per Sprache oder Text:**
- Markierten Text übersetzen / korrigieren / kürzen (direkt in Word, Gmail, etc.)
- Sprachmodus: Direktchat per Mikrofon mit TTS-Ausgabe
- PDF-Abschnitte erklären lassen
- Bilder analysieren (ins Kontext-Fenster laden)
- Diktieren (ersetzt Whisper-Tools)
- Betriebssystem steuern (geplant: "Ich gehe ins Studio" → OBS öffnen etc.)

**Tech-Stack:** C# / .NET (von Claude Code empfohlen für native Windows-App)
**Verteilung:** GitHub Releases (automatisches Update-System per Skript)
**Datenspeicherung:** `AppData\Roaming\Lume` für API-Keys, Settings, Memory

---

## Architektur-Prinzip: Hybrid-LLM

- **Lokale LLMs** (Ollama, RTX 3070 8GB): Datenschutz, günstig, aber schwächer
- **Online-APIs** (OpenAI, Anthropic, Gemini): für komplexe Tasks
- → Sensible Daten lokal, komplexe Aufgaben in die Cloud

---

## Dev-Tipps aus dem Video (Claude Code Workflow)

### 1. MVP zuerst, dann neuschreiben
- Prototyp mit **Electron/JS** gebaut → Konzept validiert
- Danach: komplette Neuentwicklung in **C#/.NET** für native Windows-Performance
- Lesson: Erst beweisen, dass das Konzept funktioniert — dann die richtige Architektur wählen

### 2. Kontext-Erhalt bei großen Projekten
Bei langen Claude Code Sessions verliert die KI den Überblick. Lösung:
- `docs/`-Ordner im Projekt anlegen
- `FOUNDATION.md` → Vision, Ziel, Architektur-Entscheide
- `STATUS.md` → Aktueller Stand, nächste Schritte, offene Punkte
- Claude liest diese Dateien zu Beginn jeder Session/Aufgabe ein → sofortiger Full-Context
- Claude hält diese Dateien nach Änderungen selbstständig aktuell

### 3. Prompts per Diktat erstellen
- Langen Prompt in ChatGPT einsprechen
- ChatGPT strukturiert ihn → Übergabe an Claude Code
- Spart Zeit beim Tippen komplexer Anforderungen

---

## App-Inspiration für eigene Projekte

Die Idee eines **System-weiten KI-Overlays** ist übertragbar:
- Tastenkombination → Kontext (Clipboard, Screenshot, aktives Fenster) → API → Ergebnis
- Minimales UI: keine App-Fenster, direktes Einfügen ins aktive Dokument
- Multi-Provider-Support: API-Key-Verwaltung für OpenAI/Anthropic/Gemini in den Settings

---

## Verbindungen
- [[regeln]] — Coding-Workflow mit Gemini
- [[workflows]] — Standard-Workflows Claude Code
- [[Konzepte/token-sparen]] — Kontext-Management
