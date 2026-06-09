---
name: system-setup
description: System-Eigenheiten macOS — ffmpeg, yt-dlp, Chrome Headless, kein Homebrew, Binary-Pfade
metadata:
  type: reference
---

# System-Setup — macOS Eigenheiten

#system #tools #setup

## Package Manager
- **Homebrew ist NICHT installiert** — kein `brew install`
- User-Binaries nach `~/.local/bin/` (ist im PATH)

## ffmpeg / ffprobe
- Download von **evermeet.cx** als ZIP (arm64)
- Entpacken → nach `~/.local/bin/`

## yt-dlp
```bash
pip3 install yt-dlp
ln -s $(which yt-dlp) ~/.local/bin/yt-dlp
```

## Chrome Headless — PDF-Generierung
```bash
Google\ Chrome --headless --print-to-pdf=<out.pdf> --print-to-pdf-no-header --no-pdf-header-footer <in.html>
```
- Für HTML → PDF Workflow (z.B. Verträge)
- Gemini für HTML-Review häufig nicht verfügbar (503) → selbst reviewen, User informieren

## Terminal-Eigenheiten
- `read -s` im Terminal funktioniert nicht zuverlässig → Secrets via Texteditor in Datei eintragen
- TextEdit speichert als `.rtf` → Token-Extraktion: `strings <datei> | grep -oE 'ghp_[A-Za-z0-9_]+'`

## Plugin-Updates
Geänderte Plugin-Commands wirken erst in der **nächsten Session** — der Command wird beim Sessionstart geladen, nicht live aktualisiert.

## EPS → PNG Konvertierung
- `sips -s format png file.eps` → schlägt fehl (Error 13)
- `qlmanage -t -s 400 -o dir/ file.eps` → produziert keinen Output für EPS
- ✅ Funktioniert: **osascript via Preview-App**:
```applescript
tell application "Preview"
  open POSIX file "/pfad/datei.eps"
  delay 2
  save front document in POSIX file "/pfad/output.png"
  close front document saving no
end tell
```

## Verbindungen
- [[Tools/github]] — GitHub ohne gh CLI
- [[Projekte/]] — Projektspezifische Tool-Setups
