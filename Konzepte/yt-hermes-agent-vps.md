# Hermes Agent: VPS-Installation (richtig gemacht)

#hermes #vps #self-hosting #ai-agent #nous-research

Quelle: YouTube "Alle installieren Hermes falsch (meine VPS-Methode ist einfacher)"
URL: https://www.youtube.com/watch?v=vS1z8IMcM5Q

---

## Was ist Hermes Agent?

Hermes Agent ist ein **selbstverbessernder KI-Agent** von Nous Research. Das Kernkonzept: Der Agent erstellt Skills aus Erfahrung, verbessert diese während der Nutzung, und baut über Sessions hinweg ein Bild des Users auf.

**Unterschied zu normalen Agenten:** Hermes lernt aktiv — er nudgt sich selbst, Wissen zu persistieren, und verbessert seine Fähigkeiten im Betrieb.

GitHub: https://github.com/NousResearch/hermes-agent
Lizenz: MIT | Sprache: Python 82%, TypeScript 13%

---

## Kernfeatures

| Feature | Details |
|---------|---------|
| **Lernschleife** | Agent erstellt automatisch Skills nach komplexen Aufgaben, verfeinert diese laufend |
| **Persistentes Gedächtnis** | Erinnerungen über Sessions hinweg, FTS5-Volltextsuche in Konversationen |
| **Multi-Platform-Gateway** | Telegram, Discord, Slack, WhatsApp, Signal, E-Mail — ein Prozess |
| **Parallelisierung** | Isolierte Sub-Agenten für parallele Workstreams |
| **Cron-Scheduler** | Automatisierte Aufgaben mit natürlichsprachigen Anweisungen |
| **200+ Modelle** | OpenRouter, OpenAI, Anthropic, Custom Endpoints — kein Vendor Lock-in |
| **TUI** | Terminal UI mit Mehrzeilen-Bearbeitung und Autovervollständigung |

---

## Warum die meisten falsch installieren

**Häufiger Fehler:** Natives Windows oder manuell über mehrere Einzelschritte.

- **Windows native:** Funktioniert nicht. Hermes läuft nur auf Linux/macOS/WSL2.
- **Komplexe manuelle Installation:** Viele Einzelbefehle, 20-30 Minuten, fehleranfällig.

---

## Die richtige VPS-Methode (einfacher)

### Minimale Anforderungen
- **Ohne Browser-Tools:** 1 vCPU / 1–2 GB RAM / 20 GB Speicher
- **Mit Browser-Automation:** 2 vCPU / 4–8 GB RAM
- **Kosten:** $5–7/Monat VPS (z.B. Hetzner) + $2–15/Monat LLM API

### Schnellinstallation (One-Liner)
```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

### Schritt-für-Schritt

1. **VPS aufsetzen** (Ubuntu/Debian empfohlen)
   ```bash
   apt update && apt install -y git curl ca-certificates
   ```

2. **Non-Root User anlegen** (Security Best Practice)
   ```bash
   adduser hermes && usermod -aG sudo hermes
   ```

3. **Hermes installieren** (One-Liner oben)

4. **Konfigurieren**
   ```bash
   hermes setup   # Wizard: LLM Provider + API Key auswählen
   hermes doctor  # Funktionscheck
   ```

5. **Als Service dauerhaft laufen lassen** (systemd)
   ```bash
   # /etc/systemd/system/hermes.service erstellen
   systemctl enable hermes && systemctl start hermes
   ```

6. **Optional: Docker für Isolation**
   ```bash
   # docker-compose.yml mit nousresearch/hermes-agent:latest
   docker compose up -d
   ```

### Docker-Methode (Production-empfohlen)
```yaml
# docker-compose.yml
services:
  hermes:
    image: nousresearch/hermes-agent:latest
    volumes:
      - ~/.hermes:/root/.hermes
    restart: unless-stopped
```

---

## Deployment-Optionen

| Option | Wann | Aufwand |
|--------|------|---------|
| **Lokal** | Testen, Development | Minimal |
| **VPS (bare metal)** | Produktiv, günstig | Gering |
| **Docker auf VPS** | Production, Isolation | Mittel |
| **Hostinger One-Click** | Kein Shell-Wissen | Minimal |
| **Modal** | Serverless | Mittel |

---

## Kontext für Remys Setup

- **Kein VPS aktiv** — Remy betreibt aktuell keinen eigenen VPS (Stand: Juni 2026)
- Coolify- und Docker-Wissen ist vorhanden (→ [[yt-coolify-self-hosting]], [[yt-self-hosting-docker-traefik]]), aber nicht umgesetzt
- Falls ein VPS aufgesetzt wird: Hermes passt gut als Docker-Container auf Coolify/Hetzner
- Hermes Gateway-Mode könnte Telegram-Automation ersetzen/ergänzen (→ n8n-Workflows)
- 64.000 Token Kontextfenster empfohlen → Claude Opus oder Sonnet als Backend sinnvoll
