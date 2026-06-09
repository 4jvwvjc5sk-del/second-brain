---
name: github
description: GitHub ohne gh CLI — curl REST API, Token-Typen, Second Brain Repo, Push-Workflow
metadata:
  type: reference
---

# GitHub — Tool Know-How

#github #tools #git

## Credentials
- Username: `4jvwvjc5sk-del`
- Second Brain Repo: `https://github.com/4jvwvjc5sk-del/second-brain` (public, gitignored: `user-profil.md`)
- **`gh` CLI ist NICHT installiert** — GitHub-Zugriff via `curl` + GitHub REST API

## Token-Typen
- Für Repo-Erstellung: **Classic Token** (`ghp_...`) verwenden
- Fine-grained Tokens haben komplexe Permissions → vermeiden für einfache Operationen

## Push (Second Brain)
```bash
cd "Obsidian/Claude Code/Second Brain" && git add . && git commit -m "..." && git push
```

## Repo erstellen via API
```bash
curl -X POST -H "Authorization: Bearer $TOKEN" https://api.github.com/user/repos -d '{"name":"..."}'
```

## TextEdit Token-Extraktion
Falls Token in TextEdit (`.rtf`) gespeichert:
```bash
strings <datei.rtf> | grep -oE 'ghp_[A-Za-z0-9_]+'
```

## Token erneuern (bei Push-Fehler "Invalid username or token")
1. Neuen Classic Token auf github.com/settings/tokens generieren
2. `git remote set-url origin https://<neuer-token>@github.com/4jvwvjc5sk-del/second-brain.git`

## Verbindungen
- [[Tools/system-setup]] — Allgemeine System-Eigenheiten
