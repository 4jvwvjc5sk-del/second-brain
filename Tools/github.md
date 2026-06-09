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

## Verbindungen
- [[Tools/system-setup]] — Allgemeine System-Eigenheiten
