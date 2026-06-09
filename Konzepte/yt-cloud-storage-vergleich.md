# Cloud Storage Vergleich 2024/2025 — Anbieter, Preise, Sicherheit, Zero-Knowledge

#cloud-storage #zero-knowledge #cryptomator #nextcloud #datenschutz

Quelle: [YouTube-Video "CLOUD-Vergleich: Wieso WIR von Dropbox WEG sind"](https://www.youtube.com/watch?v=LOO_rlL0XdU)

NotebookLM Notebook ID: `d6baaf9e-05a9-4bd3-9d2d-a28955e9d60a`
Conversation ID: `f5c614de-2420-4109-a2b6-e5afa574b549`
Quellen: 46 (ready)

---

## Kernproblem & Kontext
Der Presenter musste 80 TB Teamdaten von Dropbox migrieren (Unlimited-Policy gestrichen). Auslöser für einen umfassenden Anbietervergleich. Wichtige Erkenntnis: "Unlimited" ist oft nur Marketing — Anbieter lehnen Migrationen grosser Datenmengen ab.

## Pflicht-Kriterien für seriösen Cloud-Speicher
1. **Dateiversionierung** — schützt vor Ransomware (verschlüsselte Files wiederherstellbar)
2. **Sharing & Syncing** — Link-Sharing, Ordner-Synchronisation
3. **Automatische Sync-Clients** — Windows, macOS, Android, iOS

Disqualifizierte Anbieter (fehlende Features):
- Amazon Drive: keine Versionierung
- Apple iCloud: keine systemweite Versionierung
- MagentaCloud/Telekom: keine Versionierung

---

## Preisvergleich (pro TB/Monat)

| Anbieter | Preis/TB/Monat | Gratis-Speicher | Zero-Knowledge | Serverstandort |
|----------|----------------|-----------------|----------------|----------------|
| **OneDrive (Family)** | ~€1.38 | 5 GB | Nein | USA/EU |
| **Dropbox** | ~€1.30 | 2 GB | Nein | USA |
| **Filen.io** | ~€2.83 | 10 GB | **Ja (Open-Source)** | Deutschland |
| **pCloud** | ~€4.16 | 10 GB | Nur Crypto-Ordner | Luxemburg/USA |
| **Google Drive** | ~€5.00 | 15 GB | Nein | USA |
| **Tresorit** | ~€6–10 | 3 GB | **Ja** | Schweiz/EU |
| **OpenDrive** | ~$10 (unlimited) | – | Nein | USA |
| **Box.com** | ~€13.50+ (unlimited) | – | Nein | USA |
| **IDrive** | sehr günstig | 10 GB | Nein | USA |
| **MEGA** | günstig | 20 GB | **Ja** | Neuseeland |

---

## Zero-Knowledge Verschlüsselung — Vergleich

| Merkmal | Tresorit | pCloud | Filen.io | Sync.com |
|---------|----------|--------|----------|----------|
| Umfang | Vollständig (alle Pläne) | Nur Crypto-Ordner (kostenpflichtig) | Vollständig | Vollständig |
| Open-Source | Nein | Nein | **Ja** | Nein |
| Serverstandort | **Schweiz & EU** | Luxemburg/USA | **Deutschland** | Kanada |
| Besonderheit | SwissSign, Outlook-Integration | $100k Hack-Kopfgeld nie gewonnen | Tier-3/4 RZ Deutschland | Office-Bearbeitung ohne ZK-Verlust |
| ISO 27001 | Ja | – | – | HIPAA/PIPEDA |

**Weitere ZK-Anbieter:** Proton Drive (CH), Internxt (Open-Source, post-quantum), MEGA

---

## Empfehlungen nach Nutzertyp

### Privatnutzer (Budget)
- **Kostenlos:** MEGA (20 GB, ZK inklusive)
- **Bezahlt:** IDrive (10 TB für $4.98 im ersten Jahr)

### Kreative & Fotografen (grosse Datenmengen)
- **pCloud** — Lifetime-Kauf (2 TB für einmalig ~$399), RAW-Vorschau, kein Dateigrössenlimit
- **Adobe Creative Cloud** — falls ohnehin in Lightroom/Photoshop-Workflow

### Schweizer KMU (nDSG-Konformität)
- **Tresorit** — Schweizerische Post, Daten in CH/EU, SwissSign, HIPAA-konform
  - Preis: ~$19/Nutzer/Monat (Business)
- **Alternative: Proton Drive** — ebenfalls CH-Sitz, verschlüsselte Suite

### Tech-affine Nutzer (volle Kontrolle)
- **Nextcloud** — Open-Source, Self-Hosting auf eigenem VPS/NAS, kostenlos (+ Serverkosten)
- **Internxt** — Open-Source-Apps, WebDAV/CLI, post-quantum-Verschlüsselung, Lifetime-Deals

---

## Der Cryptomator-Trick

**Konzept:** Lokale Verschlüsselung VOR dem Upload — günstiger Standard-Cloud-Speicher (Google Drive, OneDrive) wird dadurch Zero-Knowledge-kompatibel.

### Technische Funktionsweise
- Erstellt lokale "Tresore" (Vaults)
- Virtuelles Laufwerk im Betriebssystem (wie USB-Stick)
- **Einzeldatei-Verschlüsselung** (effizient: bei Änderung nur 1 Block synct)
- Cloud sieht nur unleserliche Zeichenfolgen + verschlüsselte Datenpakete

### Vorteile
- Features grosser Anbieter (Google Workspace, MS 365) + eigene Sicherheit
- Unabhängig vom Sicherheitsversprechen des Anbieters
- Günstiger als spezialisierte ZK-Anbieter

### Einschränkungen
- Keine Cloud-Kollaboration (kein gleichzeitiges Bearbeiten im Browser)
- Eingeschränktes Teilen (Empfänger braucht Tresor-Zugang)
- Performance-Overhead (CPU-Last, langsamere Synchronisation grosser Mengen)
- Metadaten sichtbar (Dateianzahl und ungefähre Grösse)
- Gelegentliche Stabilitätsprobleme bei grossen Tresoren

### Wann sinnvoll
Wenn man MS365/Google Workspace für Kollaboration nutzt, aber sensible Daten (z.B. Buchhaltung, Verträge) zusätzlich schützen will.

---

## Wichtige Warnung: "Unlimited" ist oft fake
- Dropbox: von echtem Unlimited → jetzt 15 TB/Nutzer (min. 3 Nutzer)
- Sync.com: lehnte 80-TB-Migration ab trotz "Unlimited"
- OpenDrive: keine Medien-Libraries, keine NAS-Backups erlaubt
- Box.com: höhere File-Size-Limits erst ab Enterprise-Plan

---

## Ergänzte Anbieter (fehlten im Video)

| Anbieter | Preis/TB | Zero-Knowledge | Serverstandort | nDSG-Fokus |
|----------|----------|----------------|----------------|------------|
| **Infomaniak kDrive** | Günstig, skalierbar | Verschlüsselt (CH-unabhängig) | **Schweiz** | **Explizit nDSG-konform** |
| **Proton Drive** | ~$4–15/Mt (Suite) | Vollständig | **Schweiz** + DE | **Sehr hoch (FADP/nDSG)** |
| **MEGA** | ~$3.26/TB | Ja (Architektur umstritten seit 2022) | EU/Kanada/NZ | Gering |
| **Internxt** | ~$1.67–6/TB | Ja + Post-Quanten | EU (DE/FR/PL) | DSGVO |
| **Icedrive** | ~$4.92/TB | Nur Crypto-Ordner | UK/DE/USA | DSGVO |
| **Wasabi** | $6.99/TB (ab 07/2026: $7.99) | SSE-C (kundeneigene Schlüssel) | Global (inkl. EU/DE) | DSGVO (Backup-Tool) |
| **Strato HiDrive** | – | Nein | Deutschland | DSGVO |
| **Seafile** | Open-Source | Optional | Self-hosted | Selbst bestimmbar |

### Infomaniak kDrive (grösste Lücke im Video)
- Vollständig in der Schweiz entwickelt und gehostet (zwei CH-Rechenzentren)
- **Explizit nDSG-konform**, US Cloud Act inkompatibel
- kSuite: kollaboratives Paket inkl. Office, Mail, Kalender
- Empfehlung: Beste Preis/Compliance-Balance für Schweizer KMU

### Proton Drive
- Teil des Proton-Ökosystems (Mail, Kalender, VPN, Drive)
- Vollständige Zero-Knowledge-Verschlüsselung, Schweizer Recht
- SOC 2 Type II, ISO 27001, HIPAA-Zertifizierung
- Proton Docs: kollaboratives Bearbeiten ohne ZK zu brechen

### MEGA — Vorsicht
- 2022 identifizierte Forscher Architektur-Schwachstellen im ZK-System
- Trotz ZK-Marketing: Datenschutz-Geschichte umstritten
- Nützlich für grosse Gratis-Mengen, nicht für sensitive Geschäftsdaten

### Wasabi — nur für Tech-User/Backup
- Kein klassischer Cloud-Speicher — S3-kompatibler Objektspeicher
- Kein Sync-Client, kein Web-Upload für Endnutzer
- Ideal als Backend für Backup-Software (z.B. Veeam, Duplicati, Restic)

---

## Schweizer Kontext (nDSG)
- **Infomaniak kDrive**: Beste Wahl Preis/Compliance — CH-Sitz, explizit nDSG-konform, kSuite für Kollaboration
- **Tresorit**: Goldstandard Sicherheit — Schweizer Post, SwissSign, HIPAA; teurer aber kompromisslos
- **Proton Drive**: Verschlüsseltes Ökosystem — CH-Sitz, ISO 27001, Proton Docs
- **Filen.io**: Budget-ZK — DE-Server (DSGVO), Open-Source; wenn DE-Jurisdiction reicht
- Cryptomator + OneDrive: pragmatisch wenn MS365 vorhanden (ABER: OneDrive-Server in USA, nur Inhalt verschlüsselt)
