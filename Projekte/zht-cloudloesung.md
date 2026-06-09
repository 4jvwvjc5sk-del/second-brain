# ZHT CloudLösung — Entscheidungsgrundlage 2026

#zht #cloud #microsoft365 #airtable #ndsg

## Status
Aktiv — Geschäftsführer hat Sicherheitsbedenken gegenüber kleineren Anbietern geäussert.

## Erhaltene Dokumente (in `/ZHT/CloudLösung/Erhaltene Vergleiche/`)
- `zht-systemlandschaft-v2.html` — Pro/Kontra Apple/Google/Microsoft, Empfehlung M365
- `zht-kostenübersicht.html` — Detailrechnung M365 + Airtable: CHF 414/Mt, CHF 4'990/Jahr
- `zht-google-vs-microsoft.html` — Direktvergleich: Google CHF 88/Mt vs M365 CHF 249/Mt

## Team
- 9 Büro (inkl. Remy): Edgar Stalder, Nici Baldegger, Luca Zeindler, Sarah Pfeifer, Cécile Fehr, Daniel Zeindler, Julia Raths, Matteo Mercurio, Rémy Zeindler
- 5 Monteure: Lucio Cragnolini, Raphael Künzi, Shpetim Selmanja, Lion Kram, Mhadi Taktak

## Empfehlung (Konsens aller Dokumente)
Microsoft 365 Business Premium + Airtable + WhatsApp Business + n8n (schrittweise)

## Kernerkenntnis zur Systemauswahl
Das grösste Problem bei ZHT ist nicht Kommunikation, sondern:
- Fehlende Disposition / Kalenderkoordination
- Keine zentrale Dateiablage
- Keine Automationen

Deshalb M365 (starke Kalender, Ressourcenplanung, Shared Mailboxen, Abacus-Integration) vor Google (modern/AI, aber schwächer bei KMU-Disposition und Abacus).

---

## Kostenoptimierung (nicht in Originaldokumenten)

**Frontline Lizenzen für 5 Monteure:**

| Plan | CHF/User/Mt | 5 Monteure/Mt | Eignung Monteure |
|------|-------------|---------------|-----------------|
| F1 | **CHF 1.82** | CHF 9.10 | Kalender, Teams, SharePoint lesen — ausreichend |
| F3 | ~CHF 7.30 | CHF 36.50 | + Office mobil editierbar |
| Business Premium | CHF 17.80 | CHF 89.00 | Überdimensioniert |

**Ersparnis mit F1 für Monteure:** ~CHF 940/Jahr
**⚠ ZEITKRITISCH:** M365 F1-Preis steigt ab 1. Juli 2026 (~+33%). Bis 30. Juni entscheiden.

**Gesamtkosten optimiert:**
- M365 (9× Premium + 5× F1): CHF 169/Mt
- Airtable (9× Büro): ~CHF 165/Mt
- **Total: ~CHF 334/Mt = CHF 4'010/Jahr** (statt CHF 4'990)

---

## nDSG Compliance (nicht in Originaldokumenten)

**Pflicht-Massnahmen (auch KMU):**
1. Microsoft DPA im Admin Center akzeptieren
2. Transfer Impact Assessment dokumentieren (Microsoft stellt Vorlage)
3. MFA für alle 14 User aktivieren

**⚠ EINMALIGE Setup-Entscheidung:** Switzerland North Datencenter (Zürich) beim Tenant-Erstellung wählen — nachträgliche Änderung NICHT möglich. Daten bleiben physisch in der Schweiz.

**Airtable separat:** Airtable = AWS US-East. Separaten Airtable DPA in den Kontoeinstellungen aktivieren (für Kundendaten/Projekttagebücher).

---

## Abacus Integration (bestätigt)
Abacus hat natives Office Add-in für: Outlook, Word, Excel, PowerPoint, Teams, SharePoint.
Preis auf Anfrage: +41 71 292 25 25. Bestätigt Vorteil M365 vs. Google für Abacus-Workflow.

---

## Sicherheitseinwand Geschäftsführer (Infomaniak/Tresorit "schwächer")

**Antwort: Der Vergleich vermischt zwei verschiedene Sicherheitsdimensionen.**

| Dimension | Microsoft/Google | Tresorit/Infomaniak |
|-----------|-----------------|---------------------|
| Infrastruktur-Sicherheit | ✅ Weltklasse | ⚠ Kleiner, aber zertifiziert |
| Datenzugriff (Zero-Knowledge) | ❌ Provider kann lesen | ✅ Mathematisch ausgeschlossen |
| Rechtlicher Schutz (CLOUD Act) | ❌ US-Behörden können zugreifen | ✅ Schweizer Recht, kein CLOUD Act |
| nDSG Compliance-Aufwand | Mittel (Konfiguration nötig) | Tief (by design) |

**Fazit:** Für ZHT's Kernsysteme (Mail, Kalender, Disposition) ist M365 die richtige Wahl — Infrastruktur-Argument des GF gilt hier. ABER: Für sensible Kundendaten (Verträge, Gebäudepläne, persönliche Kundendaten) kann eine zusätzliche Zero-Knowledge-Schicht sinnvoll sein (Cryptomator kostenlos, oder kleines Tresorit Business).

**Positionierung der Alternativanbieter:**
- **Infomaniak kSuite** = VOLLSTÄNDIGER Workspace (Mail=kMail, Kalender, kChat, kMeet Video, kDrive, OnlyOffice-Editor). ~CHF 7.33/User/Mt. Direkte Konkurrenz zu M365/Google — NICHT nur Dateiablage. Aber: Abacus-Integration nicht bestätigt → dritte Wahl für ZHT.
- **Tresorit / Proton Drive** = reine Dateiablage (Zero-Knowledge), kein Produktivitäts-Stack. Können neben M365 betrieben werden (Tresorit: Outlook Add-in, Teams Add-in, SSO via Entra ID), aber Teams/SharePoint bleiben Storage-Backend — Tresorit ist parallel, nicht tief eingebettet.
- **Proton Drive / kDrive** = standalone, keine nativen M365-Plugins. kDrive: WebDAV-Zugriff möglich, aber keine Teams/SharePoint-Synchronisation.
- **Integration ZK-Anbieter in M365/Google**: Parallel ja, tief eingebettet nein. Cryptomator = pragmatischste ZK-Ergänzung (gratis, direkt auf OneDrive).

---

## Einmalkosten (nicht in Originaldokumenten)

| Posten | Schätzung |
|--------|-----------|
| SharePoint-Struktur (IT-Partner) | CHF 2'000–5'000 |
| Datenmigration iCloud → OneDrive | CHF 500–2'000 |
| Schulung 14 Personen | CHF 1'000–3'000 |
| Airtable-Setup | CHF 1'500–4'000 |
| **Total einmalig** | **CHF 5'000–14'000** |

---

## Gemini Code-Review (zht-analyse-erweiterung.html)

Gemini hat 3 Runden analysiert — folgende Bugs gefunden und gefixt:

| Bug | Schwere | Fix |
|-----|---------|-----|
| `overflow:hidden` überschreibt `overflow-x:auto` in `.table-wrap` → Tabelle scrollt nie | Kritisch | `overflow-y:hidden` statt `overflow:hidden` |
| `display:block` auf `<table>` bricht native Tabellen-Layout-Algorithmus | Kritisch | `display:block` entfernt, stattdessen `.table-wrap` Divs um alle 3 Tabellen |
| Redundante `border-bottom-left/right-radius` auf letzten Tabellenzeilen | Minor | Entfernt, `overflow:hidden` auf Parent reicht |
| `.cost-table` fehlte `min-width:560px` → quetscht auf Mobile statt zu scrollen | Bug | `min-width:560px` ergänzt |
| `tr:last-child` nicht auf `tbody` beschränkt → bei 1-Zeilen-Tabelle wird Header-Row dunkel | Edge Case | `tbody tr:last-child` überall |
| `th` in letzter Zeile erbt `text-transform:uppercase` und `font-size:11px` | Visuell | `text-transform:none; letter-spacing:normal; font-size:14px` auf letzter Zeile |
| `1.5px` Border → Sub-pixel Rendering auf Low-DPI | Minor | `1px` durchgehend |

Erste Gemini-Anfrage: 503 UNAVAILABLE (hohe Last) → selbst weitergegangen, dann zweite Runde erfolgreich.

## Quellen
- [Microsoft 365 F1 CH Preise](https://www.microsoft.com/de-ch/microsoft-365/enterprise/f1)
- [nDSG Microsoft 365 Compliance (sidd.swiss)](https://www.sidd.swiss/einblicke/microsoft-365-datenschutz-schweiz/)
- [Abacus Office Add-in](https://www.abacus.ch/abacus-marketplace/produkte/abacus-office-add-in)
- Cloud Storage Wissen: [[Konzepte/yt-cloud-storage-vergleich]]
