# Tools & API Verbindungen

## Prinzip: API statt MCP
Wo möglich API Keys direkt nutzen statt MCP Server.
MCP Server laden den gesamten Tool-Kontext bei jedem Chat — das frisst Tokens.

## Aktive MCP Server
- obsidian: `npx -y mcp-obsidian "{{YOUR_OBSIDIAN_VAULT_PATH}}"` ✓ Konfiguriert in `.mcp.json`
- gemini: `npx -y @rlabs-inc/gemini-mcp` ✓ Konfiguriert in `.mcp.json` — Text/Code-Completion, Deep Research, Code Review, Bildgenerierung (Imagen), Video (Veo), 30+ Tools

## API Keys (Namen, keine echten Keys hier!)
- Notion API: → in Claude Code Umgebung gespeichert
- Google Drive API: → in Claude Code Umgebung gespeichert
- Gemini API: → in `~/.claude/settings.json` als `GEMINI_API_KEY` gespeichert

## Mind Space (OnePlus → Second Brain) — IDEE, noch nicht eingerichtet
- Nutzer macht Screenshot auf OnePlus (Mind Space / Gemini-Integration)
- Idee: Screenshots → definierter Google Drive Ordner
- Claude prüft diesen Ordner bei Bedarf und liest neue Infos ins Second Brain ein
- Status: Ordner noch nicht definiert, Einrichtung ausstehend

## Empfehlung: Connector Tool
Zentrales Tool für sichere API-Verbindungen (DSGVO-konform, DE-gehostet).
Claude bekommt nur den Master-API-Key, nicht die Plaintext-Credentials.

## MCP Server reduzieren
In Claude Code Settings: nur 1-2 MCP Server aktiv lassen.
Alle anderen deaktivieren → spart massiv Tokens pro Session.
