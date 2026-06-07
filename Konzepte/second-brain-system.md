# Second Brain System

#konzept #obsidian #wissensmanagement

Persistentes Gedächtnis in Obsidian das über Claude-Sessions hinweg erhalten bleibt.

## Warum kein Claude Memory?

Claude's eingebautes Memory ist unzuverlässig und teuer. Markdown-Dateien im Obsidian Vault sind:
- Permanent gespeichert
- Versionierbar
- Von Claude direkt lesbar
- Für Remy sichtbar (Obsidian App)

## Vault-Struktur

- Vault 1 (dieses Second Brain): Claude-Arbeitskontext
- Vault 2 (Ablage): Persönliche Notizen

## Session-Start Protokoll

1. `00-START-HIER.md` lesen → [[../00-START-HIER]]
2. Relevante Projektdatei laden
3. Aufgabe erledigen
4. Ergebnisse sichern → neue Session

## Verbindungen

- [[../00-START-HIER]] — Session-Start
- [[../regeln]] — Arbeitsregeln
- [[../user-profil]] — Wer ist Remy
- [[mcp-server]] — wie Claude das Vault liest
- [[token-sparen]] — warum das Token spart
- [[parallel-sessions]] — mehrere Sessions nutzen dasselbe Brain
