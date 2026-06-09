# MCP Server

#konzept #claude-code #tools #optimierung

Model Context Protocol — Schnittstelle zwischen Claude Code und externen Tools/Services.

## Das Problem

Jeder aktive MCP Server lädt seinen gesamten Tool-Kontext bei jeder Session → Token-Verbrauch steigt massiv.

## Regel

Maximal 1–2 MCP Server aktiv. Alle anderen deaktivieren.

## Aktive MCP Server (Remy)

- `obsidian` — Zugriff auf Second Brain Vault
  `npx -y mcp-obsidian "/Users/remyzeindler/Desktop/AI/Claude/Obsidian/Claude Code"`
- `gemini` — Text/Code-Completion, Deep Research, Code Review, Bildgenerierung (Imagen), Video (Veo), 30+ Tools
  `npx -y @rlabs-inc/gemini-mcp` — API Key in `~/.claude/settings.json` als `GEMINI_API_KEY`

## API vs MCP

Wo möglich: direkte API-Calls statt MCP.
→ [[../tools]]

## Verbindungen

- [[token-sparen]] — MCP als Haupt-Kostenstelle
- [[second-brain-system]] — obsidian MCP als Ausnahme
- [[../tools]] — API als Alternative
- [[../10-tipps-umsetzung]] — Tipp 2 und 5
