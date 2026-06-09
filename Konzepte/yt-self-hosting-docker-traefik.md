# Self-Hosting mit Docker & Traefik (n8n, NocoDB)

#self-hosting #docker #traefik #n8n #vps #security #dsgvo

Quelle: https://www.youtube.com/watch?v=hzzobM3sYpg

> **Status: Reines Wissen — nicht umgesetzt (Stand: Juni 2026)**
> Kein VPS aktiv, kein self-hosted n8n oder NocoDB. Dieses Dokument ist ein Wissens-Speicher, kein Abbild der laufenden Infrastruktur.

---

## Kernidee

Firmen können sensible Daten DSGVO-konform verarbeiten, indem sie Open-Source-Tools auf einem eigenen VPS (EU) selbst hosten statt auf US-Cloud-Dienste zu setzen.

---

## Architektur-Übersicht

```
Internet
   │
[Port 80/443 offen]
   │
[Traefik Reverse Proxy]
   │  ← Automatisches SSL (Let's Encrypt)
   │  ← Routing via Domain-Labels
   │
[n8n Container]   [NocoDB Container]   [weitere Apps...]
   │
[PostgreSQL] ← isoliertes Internal Network (n8n_internal)
             ← NICHT im Internet exponiert
```

---

## Komponenten

### VPS / Server
- Anbieter: **Hetzner** oder **Hostinger** (EU-Rechenzentrum)
- Betriebssystem: Docker-vorinstalliertes Template wählen
- Minimaler Plan (KVM 2) reicht für mehrere Container

### Docker
- Containers isolieren Apps voneinander → keine Dependency-Konflikte
- Leichtgewichtiger als VMs
- `docker-compose.yml` für Multi-Container-Setups

### Traefik (Reverse Proxy)
- Einziger Eingang: Port 80 und 443
- Generiert SSL-Zertifikate automatisch via **Let's Encrypt**
- Routing per Label-Konfiguration im docker-compose.yml
- Shared external network: `traefik_web`

### Netzwerk-Sicherheit
- Datenbank-Container IMMER in **isoliertem Internal Network** (`n8n_internal`)
- DB kommuniziert nur mit App-Container, nicht mit Traefik/Internet
- Alle anderen Ports geschlossen → Bots finden keine offenen Angriffsflächen

---

## Setup-Reihenfolge

1. **VPS kaufen** (Hetzner/Hostinger, EU, Docker-Template)
2. **DNS A-Record** setzen: `n8n.domain.com` → Server-IP
3. **Traefik deployen** (docker-compose mit shared `traefik_web` network)
4. **App deployen** (z.B. n8n mit PostgreSQL):
   - `traefik_web` network einbinden (für Routing)
   - `n8n_internal` network für DB (isoliert)
   - Traefik-Labels im compose-file setzen (Domain, HTTPS)
5. **Weitere Apps** folgen demselben Muster — Traefik läuft bereits

---

## Sicherheits-Konzepte

### Ports & Angriffsfläche
- Ports = "Zimmer in einem Haus" (HTTP=80, HTTPS=443, n8n=5678)
- Offene Ports werden von Bots aktiv gescannt
- Lösung: Nur 80/443 offen, alles über Traefik leiten

### HTTPS & MITM
- HTTP: Passwörter, Session-Cookies, API Keys im Klartext übertragbar
- HTTPS: End-to-End-Verschlüsselung, digitale Signaturen, Domain-Validierung
- Traefik übernimmt SSL-Zertifikat-Management vollautomatisch

### Datenbank-Isolation
- PostgreSQL nie direkt im Internet — immer im internen Docker-Netz
- App-Container kann DB erreichen, Traefik/Internet nicht
- Verhindert direkten DB-Zugriff von aussen

---

## Erweiterbarkeit

Das Muster ist für beliebige weitere Open-Source-Apps wiederverwendbar:
- **NocoDB** (Airtable-Alternative) → gleicher Traefik-Stack, neues Subdomain
- Weitere Apps: gleiche Struktur, neue `docker-compose.yml` + DNS-Eintrag

---

## Relevanz für Remys Stack

- Direkt anwendbar für **n8n Self-Hosting** (statt Cloud)
- Grundlage für DSGVO-konformes KI-Automatisierungs-Setup
- Pattern gilt auch für zukünftige Projekte (z.B. eigene APIs, Datenbanken)

---

## Verbindungen

- [[workflows]] — n8n Workflow-Dokumentation
- [[Konzepte/yt-coolify-self-hosting]] — Coolify als Alternative (GUI-basiert)
- [[tools]] — VPS & Server-Tools
