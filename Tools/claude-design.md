---
name: claude-design
description: Claude Design (claude.ai/design) — Workflow, Upload-Regeln, Design System erstellen
metadata:
  type: reference
---

# Claude Design — Tool Know-How

#claude-design #design #tools

## Was ist Claude Design?
Visuelles Design-Tool von Anthropic (claude.ai/design) — erstellt Prototypen, Slide Decks, Design Systems. Kein HTML-Editor, kein Code-Output. Für UI-Iteration und visuelle Vorlagen.

## Design System Setup-Workflow
1. **Neues Projekt** erstellen → Typ wählen (Prototype / Slide deck / Other)
2. **"Company name and blurb"** ausfüllen: `<Firmenname>: <Branche, Team-Grösse, Produkt-Kontext>`
3. **"Any other notes"**: Primärfarbe HEX, Schrift, Stil-Direktiven, Sprache, App-Module
4. **Design-Ressourcen** hochladen (alle optional):
   - "Link code from GitHub" → raw.githubusercontent.com URL
   - "Link code from your computer" → **ORDNER** (nicht Datei!) via Chrome/Edge
   - "Upload a .fig file" → Figma-Export
   - "Add fonts, logos and assets" → PNG/SVG Logo, Schrift-Dateien

## Wichtig: Ordner statt Datei
"Link code from your computer" erwartet einen **Ordner**, keine einzelne Datei.
→ Unterordner erstellen, Dateien hineinkopieren, dann Ordner auswählen.

## GitHub Raw URL Format
```
https://raw.githubusercontent.com/<username>/<repo>/main/<pfad/datei.html>
```

## ZHT Design System
- Lokaler Ordner: `ZHT/Design Dateien/zht-design-system/` (index.html + logo-zht.png)
- GitHub: `https://raw.githubusercontent.com/4jvwvjc5sk-del/second-brain/main/assets/zht-design-system.html`
- Primärfarbe: `#066533` (ZHT Grün), Font: DM Sans, Stil: Clean/Flat/Professional

## Verbindungen
- [[Projekte/workspace-eigenbau]] — Workspace-Projekt das Claude Design nutzt
- [[Tools/github]] — GitHub Upload-Workflow
