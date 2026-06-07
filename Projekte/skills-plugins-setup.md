# Skills & Plugins Setup — Session 2026-06-02

## Status: Abgeschlossen

## Installierte Skills (aktiv in .claude/skills/)
- automation-advisor ✓
- present-variants ✓
- clarify-first ✓ (NEU)
- flut-pipeline ✓ (NEU)
- coin-deep-dive ✓
- krypto-marktanalyse ✓
- portfolio-tracker ✓
- technische-analyse ✓
- grill-me ✓
- chat-compaction ✓
- heikles-gespraech ✓
- ki-spuren-entfernen ✓
- meeting-notizen ✓
- morgen-briefing ✓
- recherche-bericht ✓
- rechnung-erstellen ✓
- schnellrecherche ✓
- vertrag-pruefen ✓

## Installierte Plugins (aktiv in .claude/plugins/)
- automation-advisor ✓
- catkingdom ✓ (Instagram/Kanalmanagement)
- DevPack-plugin ✓ (builder-guide + tech-support Skills)
- cowork-skillspack ✓ (CoWork Skills)

## Neue Hooks
- SessionStart Hook → .claude/settings.json
  Liest Second Brain beim Sessionstart automatisch
- automation-advisor UserPromptSubmit Hook (bereits vorhanden)

## Wichtige Regeln (festgelegt)
1. notebooklm-py Skill bei Research-Aufgaben automatisch laden
2. Second Brain bei jedem Sessionstart ohne Aufforderung lesen
3. clarify-first: Alle Fragen BEVOR Implementierung beginnt
4. flut-pipeline: YouTube→Reel ohne Kling AI (yt-dlp + Whisper + FFmpeg)

## Offene Aufgaben
- [ ] Flut-Pipeline testen (yt-dlp + Whisper + FFmpeg installiert?)
- [ ] NotebookLM Login: `notebooklm login` einmalig ausführen
- [ ] catkingdom Plugin: Was genau macht es? (Instagram-Kanal-Commands)

## Technische Details
- Plugin ohne Root-Ordner im ZIP → manuell in eigenen Unterordner extrahieren
- `claude plugin install <pfad>` funktioniert NICHT für lokale Plugins
- Lokale Plugins: direkt in .claude/plugins/ ablegen
