# Claude Code Second Brain — Setup

Ein persistentes Wissenssystem für Claude Code. Claude liest diese Markdown-Dateien direkt — kein Tool, kein Overhead.

## Was ist das?

Statt Claude in jeder Session alles neu zu erklären, liegt der Kontext in strukturierten `.md`-Dateien. Claude liest nur was relevant ist — spart Tokens, spart Zeit.

## Schnellstart

### 1. Obsidian Vault einrichten (empfohlen)
```
Obsidian → Neuer Vault → Diesen Ordner als Vault öffnen
```
Obsidian ist optional — die Dateien sind plain Markdown und funktionieren ohne es.

### 2. Persönliches Profil anlegen
```bash
cp user-profil.TEMPLATE.md user-profil.md
```
Öffne `user-profil.md` und ersetze alle `{{PLATZHALTER}}`:

| Platzhalter | Beispiel |
|-------------|---------|
| `{{YOUR_NAME}}` | Max Muster |
| `{{YOUR_EMAIL}}` | max@firma.ch |
| `{{YOUR_COMPANY}}` | Meine Firma AG |
| `{{YOUR_INTERESTS}}` | Krypto, AI-Automation, n8n |
| `{{YOUR_LANGUAGE}}` | Deutsch |

`user-profil.md` ist in `.gitignore` — deine Daten bleiben lokal und kommen nie auf GitHub.

### 3. MCP Server konfigurieren (optional)
Öffne `tools.md` und ersetze `{{YOUR_OBSIDIAN_VAULT_PATH}}` mit dem absoluten Pfad zu diesem Ordner:
```
/Users/dein-name/Desktop/AI/Claude/Obsidian/Claude Code
```

### 4. CLAUDE.md anpassen
Passe den Pfad in deiner `CLAUDE.md` auf den lokalen Pfad dieses Ordners an.

### 5. Erste Session starten
Sage Claude am Anfang jeder Session:
```
Lies /pfad/zu/diesem/ordner/00-START-HIER.md
```
Oder richte einen Session-Start-Hook ein, der das automatisch tut.

## Struktur

```
Second Brain/
├── 00-START-HIER.md          ← Claude liest das zuerst
├── SETUP.md                  ← diese Datei
├── regeln.md                 ← Verhaltensregeln für Claude
├── tools.md                  ← MCP Server & API Infos
├── workflows.md              ← Wiederkehrende Abläufe
├── user-profil.TEMPLATE.md   ← Vorlage (kopieren → user-profil.md)
├── user-profil.md            ← deine persönliche Version (gitignored)
├── Konzepte/                 ← Konzept-Notizen & Lernmaterial
└── Projekte/                 ← Ein File pro Projekt
    └── TEMPLATE.md           ← Vorlage für neue Projekte
```

## Philosophie

- **Keine Claude Memories** — alles im Second Brain, nicht in Claudes interner Erinnerung
- **Eine Session pro Aufgabe** — neuer Chat, Kontext kommt aus den Dateien
- **Schlank halten** — nur relevante Files laden, nicht alles auf einmal
- **Vor `/compact`** — Erkenntnisse erst ins Second Brain schreiben

## Eigene Projekte hinzufügen

```bash
cp Projekte/TEMPLATE.md Projekte/mein-projekt.md
```
Füll die Vorlage aus — Claude kennt dann deinen Projektkontext in jeder Session.
