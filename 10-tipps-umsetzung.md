# 10 Tipps: Token-Limit niemals erreichen

Quelle: https://www.youtube.com/watch?v=qOnwO5HCZ_Y

## Tipp 1: Second Brain / Wiki ✅ UMGESETZT
Obsidian Vault als Second Brain — Claude Code liest Markdown-Dateien direkt.
→ `~/Desktop/AI/Claude/Obsidian/Claude Code/Second Brain/`
- Claude liest Infos nur wenn nötig, nicht permanent
- Ersetzt ständige Rückfragen und riesige Kontextmengen
- MCP Server: `obsidian` (konfiguriert in `.mcp.json`)

## Tipp 2: Weniger MCP Connections ⚠️ MANUELL PRÜFEN
Jeder MCP Server lädt seinen gesamten Tool-Kontext bei jeder Session.
→ In Claude Code: nur 1-2 MCP Server aktiv lassen
→ Alle nicht genutzten deaktivieren

## Tipp 3: Claude Code statt Claude Chat ✅ BEREITS AKTIV
Du nutzt Claude Code — das ist bereits optimal.
Claude Code arbeitet mit Skripten und Dateien statt alles in den Kontext zu laden.

## Tipp 4: /compact nutzen ✅ SKILL VORHANDEN
Befehl: `/compact`
→ Fasst langen Chat zusammen, reduziert Kontext drastisch
→ VORHER: Wichtige Infos ins Second Brain schreiben!
Reihenfolge: Infos sichern → /compact → weiterarbeiten

## Tipp 5: API statt MCP ✅ DOKUMENTIERT
→ Siehe [[tools]]
API Keys direkt in Claude Code Umgebung speichern.
API Aufrufe kosten weniger Kontext als MCP Tool-Ladung.

## Tipp 6: CLAUDE.md schlank halten ✅ UMGESETZT
→ CLAUDE.md enthält NUR Zeiger auf Second Brain (Obsidian Vault)
→ Kein Inhalt direkt in CLAUDE.md
→ Keine Claude Memories — stattdessen Second Brain nutzen

## Tipp 7: Investieren 💰 DEINE ENTSCHEIDUNG
- 20€/Monat: Privat OK
- 90€/Monat: Produktiv empfohlen
- 180€/Monat: Parallele Sessions möglich
Zweiter Account: Ausloggen → einloggen → Second Brain zeigen → sofort weitermachen

## Tipp 8: Nutzungslimits prüfen 👀 MANUELL
In Claude Account: Nutzungslimits und verfügbares Budget regelmässig prüfen.
Claude schenkt ab und zu Budget — mitnehmen!
Kein eigenes Geld ins Budget einzahlen (geht zu schnell weg).

## Tipp 9: Neue Session pro Aufgabe ✅ DOKUMENTIERT
→ Nicht wie bei ChatGPT: ein Chat pro Kunde/Projekt
→ Stattdessen: neuer Chat pro Aufgabe
→ Kontext kommt aus Second Brain, nicht aus Session-History
Workflow: Second Brain lesen → Aufgabe → Ergebnis sichern → neue Session

## Tipp 10: Connector Tool 🔧 OPTIONAL
Proprietary Tool des Video-Creators (startandconnect.com).
- Zentrale, sichere API-Verbindungen
- DSGVO-konform, in Deutschland gehostet
- Claude bekommt nur Master-Key, nicht Plaintext-Credentials
→ https://startandconnect.com/spotlight
