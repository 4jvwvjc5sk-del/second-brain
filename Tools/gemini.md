---
name: gemini
description: Gemini MCP — Setup, Tools, Troubleshooting, Coding-Workflow, YouTube-Summary
metadata:
  type: reference
---

# Gemini MCP — Tool Know-How

#gemini #mcp #tools

## Setup
- Server heisst `gemini`
- Eintrag in `~/.claude/settings.json` unter `enabledMcpjsonServers` muss `"gemini"` enthalten
- API Key Format: `AQ...` (nicht `AIzaSy...`) — so liefert AI Studio den Key für `@rlabs-inc/gemini-mcp`
- Key liegt in `~/.claude/settings.json` unter `env.GEMINI_API_KEY`
- Tools laden via `ToolSearch select:mcp__gemini__<tool>` vor Aufruf

## Tools-Übersicht (wichtigste)
| Tool | Zweck |
|------|-------|
| `gemini-analyze-code` | Code-Review (focus: bugs/quality/security/performance) |
| `gemini-run-code` | Sandbox-Tests |
| `gemini-youtube-summary` | YouTube-Video analysieren (style: detailed) |
| `gemini-analyze-image` | Screenshots reviewen |
| `gemini-deep-research` | Tiefe Web-Recherche |
| `gemini-search` | Schnelle Suche |

## Coding-Workflow (Pflicht laut regeln.md)
1. **Gemini primär**: `gemini-analyze-code` macht Haupt-Analyse
2. **Claude überprüft** Ergebnis und passt an
3. **Fallback bei Fehler**: selbst weitermachen + User transparent melden
4. **Batch-Pattern**: Bei mehreren Edits an einer Datei — erst alle Edits, dann einmalig `gemini-analyze-code` auf Endergebnis

## Troubleshooting
- Gemini lädt nicht? → `~/.claude/settings.json` prüfen: `"gemini"` in `enabledMcpjsonServers`
- 503 / fetch failed → Temporär nicht verfügbar; Fallback: WebSearch/WebFetch + User informieren
- Quota erschöpft → selbst weitermachen, aber **explizit melden** dass Änderung ungeprüft ist

## YouTube-Summary Pattern
- URL auf `?v=<id>` kürzen — Playlist-Parameter weg (`&list=`, `&index=`)
- `style: detailed` für vollständige Analyse

## Verbindungen
- [[regeln]] — Coding-Workflow Detail
- [[Tools/notebooklm]] — YouTube + NotebookLM Kombination
