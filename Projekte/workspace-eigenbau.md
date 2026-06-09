# Projekt: Eigener Workspace (Eigenentwicklung)

#projekt #workspace #eigenentwicklung #abacus #ki

*Gestartet: 2026-06-09*

## Ziel
Eigene modulare Web-Plattform, ähnlich Microsoft 365 / kSuite — aber vollständig selbst gebaut und kontrolliert.

## Kern-Features
- Interner Chat (Slack/Teams-Ersatz)
- Kalender & Einsatzplanung
- Todo/Aufgaben (Todoist-Ersatz)
- Cloud-Speicher
- **Abacus ERP Integration** (Pflicht)
- KI-Assistent mit Spracheingabe (wie OpenLess/2KEY)
- Proaktive KI-Erinnerungen (Termine, Todos)
- Modularer Ausbau: Reparaturmeldung, Lagerbestand, Werkzeugbestand

## Empfohlener Tech-Stack

| Schicht | Tool |
|---------|------|
| Daten/API | Directus + PostgreSQL |
| Frontend | Next.js 15 + Shadcn/ui |
| Auth | NextAuth.js |
| Real-time | Socket.IO (self-hosted) |
| File Storage | MinIO (S3-kompatibel) |
| ASR Voice | Groq Whisper |
| LLM | Claude API |
| AI UI | Vercel AI SDK |
| Background Jobs | Inngest |
| Abacus | Maesn Unified API |
| Hosting | Hetzner VPS (Schweiz/Deutschland) |

## Phasenplan
1. **Monat 1–2**: Fundament (PostgreSQL, Directus, Next.js, Auth, Tasks)
2. **Monat 3–4**: Chat, Kalender, Kanban
3. **Monat 5–6**: Abacus (Maesn), File Storage
4. **Monat 7–8**: KI + Voice (Whisper + Claude + Inngest)
5. **Monat 9+**: Erweiterungsmodule (Lager, Reparaturen, Werkzeuge)

## Gemini Code-Review (Mockup, 2026-06-09)
- Bug behoben: `event.currentTarget` → `element`-Parameter (deprecated global, cross-browser-Risiko)
- Empfehlung für Produktion: `data-view`/`data-title` HTML-Attribute statt JS-Dictionary → neue Module nur im HTML ergänzen
- DOM-Elemente für Produktion cachen (einmalig selektieren statt bei jedem Klick)
- Für Mockup: Code ausreichend, keine weiteren Änderungen nötig

## Status
- Mockup v1 erstellt: `/AI/Claude/workspace-mockup.html`
- Mockup für gut befunden → Design-Iteration in claude.ai (einfacher für visuelle Iteration)
- Nach Design-Finalisierung: Phase 1 Implementierung starten (Directus + Next.js)

## Abacus-Module (geklärt)
- Stunden, Kundenstamm, Offerten, Service-Arbeiten → alles Standard REST API → Maesn reicht

## Design System (erstellt 2026-06-09)
- Primärfarbe: `#066533` (ZHT Grün, aus Logo extrahiert via Gemini URL-Analyse)
- Font: DM Sans (geometrische Grotesk, passt zu ZHT CI)
- Lokaler Ordner: `ZHT/Design Dateien/zht-design-system/` (self-contained, Logo base64-eingebettet)
- GitHub: `https://raw.githubusercontent.com/4jvwvjc5sk-del/second-brain/main/assets/zht-design-system.html`
- Claude Design: Ordner hochgeladen, Design System wird generiert (2026-06-09)
- Gemini-geprüft: cursor/pointer-events Konflikt behoben, grid minmax(0,1fr), logo max-height

## Offene Entscheidungen
- [ ] Design finalisieren (läuft in Claude Design)
- [ ] VPS-Provider bestätigen (Hetzner empfohlen)
- [ ] Domain für Workspace festlegen

## Recherche-Ergebnisse
→ Vollständiger Quervergleich: `Ablage/workspace-eigenbau-recherche.md`
→ Gemini Research ID: v1_ChdzZzhv...
→ NotebookLM Notebook: 2feeb034-6c96-4d84-b468-6a23d13edbe5
