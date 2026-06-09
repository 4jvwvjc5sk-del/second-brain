---
name: notebooklm
description: NotebookLM Know-How — Quellen, Deep Research, Rate Limits, Fallbacks, Patterns
metadata:
  type: reference
---

# NotebookLM — Tool Know-How

#notebooklm #tools #research

## Grundregeln
- Minimum **10 Quellen** pro Notebook — Deep Research nutzen, selektiv importieren
- `notebooklm source delete` immer mit `--yes` Flag (ohne Flag scheitert in nicht-interaktiven Kontexten)

## Deep Research
- Rate-Limited? → Fallback: mehrere `notebooklm source add-research --mode fast` Runden **sequenziell** mit verschiedenen Queries
- `notebooklm source add-research` via `&` parallel starten → Queries registrieren sich gar nicht (`status: no_research`) — **immer sequenziell**
- Nach `research wait` Timeout: Quellen zählen mit `notebooklm source list | grep -c "ready"` — Import oft trotzdem erfolgreich

## Quellen-Import
- Paywalled/geblockte URLs: heise.de, businessinsider.com, box.com/pricing (Cloudflare), direkte Anbieter-Sites → **Cloudwards-Reviews** als zuverlässige Alternative
- `notebooklm ask` kann mit `RPCResponseTooLargeError` scheitern bei breiten Fragen → Fragen immer auf Teilaspekte eingrenzen

## YouTube + NotebookLM Workflow
- "analyse/recherche erstellen" bei YT-Videos = immer NotebookLM-Research-Workflow starten (Video + Deep Research + Fragen)
- YouTube-URLs VOR `gemini-youtube-summary` auf `?v=<id>` kürzen — Playlist-Parameter (`&list=`, `&index=`) → `INVALID_ARGUMENT`

## Ablage
- Strukturiertes YT-Wissen (Lernnotizen, Erkenntnisse) → `Second Brain/Konzepte/yt-<thema>.md`
- Nach jedem neuen Konzepte-File: Tabelle in `00-START-HIER.md` aktualisieren
- **`Konzepte/yt-*.md` = reines Wissen** — nie daraus ableiten, dass etwas deployed/installiert ist; aktiver Status → `user-profil.md` (Infrastruktur) oder `Projekte/*.md`

## Verbindungen
- [[tools]] — MCP Server und API Keys
- [[workflows]] — Research-Workflow im Detail
