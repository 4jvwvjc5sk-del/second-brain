# Coolify Self-Hosting auf Hetzner VPS

#self-hosting #coolify #hetzner #vps #docker #traefik #ssl #anythingllm

Quelle: https://www.youtube.com/watch?v=foMhJ4epafU (Harald, Serverkiwissen.de)

---

## Was ist Coolify?

Open-Source-Platform zum einfachen Deployen, Verwalten und Monitoren von Anwendungen auf eigenem VPS.
- **Self-hosted**: Kostenlos für immer
- **Cloud (managed)**: $5/Monat
- Alternative zu Heroku, Netlify, Vercel
- Docker-basiert, eigene Datenhoheit, keine Vendor-Lock-ins

---

## Setup-Übersicht: Hetzner + Coolify

### 1. Hetzner VPS erstellen
- **Empfohlener Server:** CPX21 — 3 vCPUs, 4 GB RAM, 80 GB SSD (~€8.39/Monat)
- **OS:** Ubuntu 24.04 (manuelle Installation bevorzugen, nicht den Coolify-App-Template)
- **Standort:** Nürnberg oder beliebig
- **SSH-Key-Authentifizierung** aktivieren
- **Firewall zunächst deaktiviert lassen** (stört sonst Installationsskript)
- Backups aktivieren (kostet +20% des Serverpreises, spart Troubleshooting)

### 2. Coolify installieren
```bash
ssh root@<IP_ADDRESS>
# Root-Passwort setzen, System updaten
curl -sSL https://get.coolify.io/install.sh | bash
```
Nach Installation: Zugriff via `http://<IP>:8000`

### 3. Erster Login & Setup
- Admin-Account registrieren (Name, E-Mail, Passwort)
- Onboarding-Wizard: "Localhost" auswählen → direkt zum Dashboard

---

## Domain & SSL mit Wildcard-DNS

### Strategie
Coolify nutzt **Traefik** als Reverse Proxy + Let's Encrypt für automatische SSL-Zertifikate.
Wildcard-Subdomain (`*.domain.com`) → alle Apps bekommen automatisch HTTPS.

### DNS-Konfiguration (beim Registrar)
Zwei A-Records auf die VPS-IP zeigen:
| Host | Typ | Ziel |
|------|-----|------|
| `*` | A | VPS Public IP |
| `@` | A | VPS Public IP |

### Coolify-Einstellungen
- **Server Proxy Settings** → Wildcard-Domain eintragen: `https://domain.com`
- **Settings → Instance Settings** → Coolify-Domain setzen: `https://coolify.domain.com`
- **"Start Proxy"** klicken → Traefik startet, SSL-Zertifikate werden automatisch beantragt

---

## Firewall (Hetzner) — NACH Setup aktivieren

Drei Incoming-Rules setzen:
| Port | Protokoll | Zweck |
|------|-----------|-------|
| 22 | TCP | SSH |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |

**Wichtig:** Firewall erst nach vollständigem Coolify-Setup aktivieren!

---

## Anwendung deployen (Beispiel: AnythingLLM)

1. **Projects → Add** → Projekt benennen (z.B. "anythingllm")
2. **Production → Add New Resource** → Service-Katalog durchsuchen → "AnythingLLM" wählen
3. Destination-URL anpassen: `https://anythingllm.domain.com`
4. **Deploy** klicken → Docker-Image wird gepullt & Container gestartet

### Troubleshooting: Port-Mapping-Fehler
Wenn nach dem Deploy "no available server" erscheint:
→ **Edit Compose File** → unter `ports` manuell hinzufügen:
```yaml
ports:
  - "3001:3001"
```
→ Neu deployen

### Admin-Passwort finden
- **Environment Variables** des Deployments öffnen
- Token unter `SERVICE_PASSWORD_AUTHTOKEN` kopieren

---

## Apps aktualisieren
- **Advanced Settings** → Container-Image neu bauen (Rebuild)
- Oder: Service stoppen → neu starten

---

## Key Takeaways

1. **Wildcard-DNS** ist der eleganteste Ansatz: ein Record deckt alle Subdomains ab
2. **Traefik als Reverse Proxy** übernimmt Routing + SSL vollautomatisch
3. **Firewall zuletzt** konfigurieren — blockiert sonst den Installations-Skript
4. **Port-Mapping im Compose-File** manuell anpassen wenn Proxy-Verbindung fehlschlägt
5. Coolify eignet sich hervorragend für: Docker-Services, Datenbanken, APIs, KI-Tools auf einem VPS

---

## Verbindungen
- [[tools]] — VPS & Hosting-Tools
- [[Konzepte/second-brain-system]]
