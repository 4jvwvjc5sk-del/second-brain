# Regeln & Direktiven

#regeln #claude-code #direktiven

## Token-Spar-Regeln
- Neue Session pro Aufgabe starten (nicht alles in einen langen Chat)
- Infos ins Second Brain schreiben, KEINE Claude Memories anlegen
- CLAUDE.md schlank halten — nur Zeiger, kein Inhalt
- MCP Server minimieren — nur wirklich benötigte aktiv lassen
- API statt MCP wo möglich (kostet weniger Kontext)
- Vor `/compact`: relevante Ergebnisse ins Second Brain sichern

## Arbeitsregeln
- Antworten auf Deutsch, ausser der User schreibt auf Englisch
- Kein Kommentar-Spam im Code
- Direkt und konkret — keine langen Erklärungen wenn nicht nötig
- Bei neuen Projekten: Projektdatei in `Second Brain/Projekte/` anlegen

## Workflow pro Aufgabe
1. Second Brain lesen (nur relevante Dateien)
2. Aufgabe erledigen
3. Erkenntnisse ins Second Brain schreiben
4. Session beenden oder `/compact` nutzen

## Compact-Trigger (WICHTIG)
Wenn der User "compact", "/compact" oder "komprimiere" schreibt:
1. Zuerst: alle relevanten Erkenntnisse, Entscheidungen und Ergebnisse der aktuellen Session ins Second Brain schreiben (passendes File in `Projekte/` oder `regeln.md`)
2. Dann: `/compact` ausführen
Diese Regel gilt immer, ohne dass der User es jedes Mal sagen muss.

## Coding-Workflow mit Gemini (PFLICHT, User-Direktive 07.06.2026)
Bei JEDER Code-Aufgabe (Vibe Coding, Optimierung, Bugfix) — Reihenfolge:
1. **Gemini primär**: Code-Generierung & Analyse zuerst über Gemini laufen lassen
   (`mcp__gemini__gemini-analyze-code`, focus: bugs/quality/security/performance;
   `gemini-run-code` für Sandbox-Tests). Gemini macht die Hauptarbeit — nicht Claude.
2. **Claude überprüft** das Gemini-Ergebnis, passt an und wiederholt bei Bedarf (Iteration).
3. **Fallback bei Gemini-Fehler** (Quota erschöpft / API-Error): selbst weitermachen,
   aber dem User TRANSPARENT melden, dass die Änderung ungeprüft ist. Nie still überspringen.
4. Bei **visuellem/UI Code**: Screenshot → Gemini analyze-image → Feedback dokumentieren.
5. **Alles ins Second Brain schreiben** (`Projekte/<projektname>.md`, nie nur im Chat):
   was gebaut wurde, Gemini-Feedback (Kernpunkte), gefolgte Entscheidungen.
- Durchgesetzt durch PostToolUse-Hook `.claude/hooks/gemini-reminder.py` (feuert bei Code-Edits).

## Verbindungen
- [[00-START-HIER]] — Session-Start
- [[workflows]] — Standard-Workflows
- [[Konzepte/token-sparen]] — Token-Strategien
- [[user-profil]] — User-Präferenzen
