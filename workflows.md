# Workflows & Prozesse

## Standard-Workflow pro Aufgabe
1. Neue Claude Code Session öffnen
2. `Second Brain/00-START-HIER.md` lesen lassen
3. Relevante Projektdatei angeben
4. Aufgabe erledigen
5. Ergebnisse/Learnings ins Second Brain schreiben
6. Session schliessen oder `/compact` nutzen

## Session-Handover ("Wo waren wir?")

**Permanentes Muster** — bei jedem Session-Ende (schlafen gehen, Pause, Unterbrechung):
1. Claude schreibt `Second Brain/naechste-session.md` mit: was erledigt, was offen, nächste Schritte
2. Bei nächster Session: User fragt "wo standen wir?" → Claude liest `naechste-session.md` und gibt Kurzantwort
3. Nach Erledigung der Aufgaben: `naechste-session.md` aktualisieren oder löschen

**Trigger-Sätze** (User schreibt eines davon):
- "wo standen wir?" / "wo waren wir?" / "was war nochmal der plan?"
- "ich gehe schlafen" / "bis morgen" / "mache eine pause"
→ Claude liest/schreibt `naechste-session.md` ohne Aufforderung

## Compact-Workflow (bei langen Sessions)
1. Wichtige Ergebnisse ins Second Brain schreiben
2. `/compact` eingeben
3. Claude komprimiert den Chat-Kontext
4. Weiterarbeiten mit reduziertem Token-Verbrauch

## Parallel-Sessions (für mehrere Projekte)
- Mehrere Claude Code Fenster/Tabs öffnen
- Jedes Fenster = eigene Session = eigene Aufgabe
- Second Brain ist shared → alle Sessions nutzen denselben Kontext
- Spart Tokens, weil keine langen Session-Histories mitgeschleppt werden

## Zweiter Account (wenn Limit erreicht)
1. Ausloggen aus aktuellem Account
2. Mit zweitem Account einloggen
3. Second Brain Pfad angeben → sofort weitermachen
4. Kein Setup nötig, alles im Second Brain vorhanden

## Autonome Nacht-Sessions
- Aufgabe klar definieren und ins Second Brain schreiben
- Claude Code Aufgabe starten
- Über Nacht/während Meetings laufen lassen
- Ergebnisse im Second Brain werden persistiert
