# KI-Lösungen für KMU & EPU — Schweizer Kontext

#ki #kmu #epu #schweiz #ndsg #tools #automatisierung

Quellvideo: WKO Webinar "Praxisorientierte KI-Lösungen: KI Dokumente bearbeiten" (Juli 2023)
Recherche: NotebookLM Notebook `b5e8b7bf-3283-4536-8870-a5994660dd2c` — 120 Quellen (Stand 08.06.2026)

---

## Tool-Empfehlungen für die Schweiz

### Schweizer / datensouveräne Lösungen (bevorzugt bei sensiblen Daten)

| Tool | Preis | Stärken | Schwächen |
|------|-------|---------|-----------|
| **Euria** (Infomaniak) | Kostenlos in kSuite | RZ Genf/Lausanne, kein CLOUD Act, kein Training mit Daten | Modellqualität unter GPT-4 bei komplexen Tasks |
| **NetsafeAI** | Auf Anfrage (eher für KMU) | ISO 27001, Swiss Hosting, Cloud-Act-frei, Automation-Pipelines | Höherer Setup-Aufwand |
| **Apertus** (ETH/EPFL) | Kostenlos (Open Source) | On-Premises, Daten verlassen Haus nie, CH-Landessprachen | Braucht IT-Know-how + GPU |
| **Schweizerdeutsch Übersetzer App** | Abo-Modell | Transkription Mundart, Swiss Hosting | Nur Audio-zu-Text, kein Allzweck-Assistent |

### Globale Plattformen (Business-Tarife Pflicht)

| Tool | Preis | Stärken | Achtung |
|------|-------|---------|---------|
| **Microsoft 365 Copilot** | CHF 18–30/Nutzer/Mt | Deep Office-Integration, 14 Min./Tag Ersparnis | US CLOUD Act — Datenresidenz CH ab 2026 angekündigt |
| **ChatGPT Team/Enterprise** | $25–30/Nutzer/Mt | Bestes Reasoning, Custom GPTs | Hosting USA, nDSG-AVV nur in Bezahlversion |
| **Google Gemini Workspace** | $14–30/Nutzer/Mt | Recherche, 2M Token Kontext | Google-Ökosystem-Fokus |
| **Langdock** | ~€23/Nutzer/Mt | EU-Server, modellagnostisch (GPT + Claude + Gemini) | Keine native Word/Excel-Integration |
| **DeepL Pro** | — | Hochwertige Übersetzungen, Datensicherheit | Nur Übersetzung |
| **Perplexity.ai** | — | Recherche mit Quellenangaben | — |

**Regel: Gratis-Versionen (ChatGPT Free, Copilot Free) für Geschäftsdaten = No-Go.** Kein AVV, Daten gehen ins Training.

---

## Rechtslage Schweiz: nDSG

Das nDSG gilt seit **1. September 2023** — keine Übergangsfristen mehr.

### Sofort-Pflichten (bereits überfällig wenn nicht erledigt)

| Massnahme | Grundlage |
|-----------|-----------|
| AVV mit allen Cloud-KI-Anbietern abschliessen | Art. 9 nDSG |
| Inventar aller genutzten Tools erstellen (inkl. Shadow-AI) | Art. 22 nDSG |
| Interne KI-Richtlinie: welche Tools für welche Daten erlaubt | Best Practice |
| Datenschutzerklärung um KI-Nutzung ergänzen | Art. 19 nDSG |
| Chatbots als KI kennzeichnen | Art. 19 nDSG |
| KI-generierte Inhalte / Deepfakes labeln | Art. 19 nDSG |
| Mitarbeiterschulungen dokumentieren | Art. 6 EU AI Act (de-facto CH) |

### Sanktionen
- Bis **CHF 250'000** — persönlich (nicht nur Unternehmen!)
- Berufsgeheimnisträger (Ärzte, Anwälte, Treuhänder): Art. 321 StGB — bis 3 Jahre Freiheitsstrafe bei ungeschützter Dateneingabe

### CH vs. EU im Vergleich
| Punkt | Schweiz (nDSG) | EU (DSGVO + AI Act) |
|-------|---------------|---------------------|
| Datenschutzrecht | nDSG (seit Sept. 2023) | DSGVO |
| KI-Regulierung | EU AI Act nicht bindend, aber de-facto relevant | Direkt bindend |
| Strafen | CHF 250k (persönlich) | Bis 35 Mio. € / 7% Umsatz |
| CLOUD Act Risiko | Zentrales Thema | Weniger thematisiert |

### Besonderheit US CLOUD Act
US-Behörden können auf Daten bei US-Providern zugreifen — auch wenn Daten physisch in Zürich/Genf liegen. Microsoft plant CH-Datenresidenz für Copilot ab 2026. Bis dahin: für sehr sensible Daten Schweizer Hosting bevorzugen.

---

## Quick Wins: Grösster ROI für Schweizer KMU

| Use Case | Tool | Zeitersparnis | CHF-Wert |
|----------|------|---------------|----------|
| E-Mail-Entwürfe & Triage | Euria / Copilot Outlook | 17 Std./Woche (20 MA) | ~3'400/Mt |
| Dokumentenverarbeitung / Belege | NetsafeAI / sevDesk KI | 12 Std./Woche | ~2'400/Mt |
| Meeting-Protokolle (inkl. Mundart) | Schweizerdeutsch App / Copilot | 45–60 Min./Woche/MA | — |
| Angebotserstellung Handwerk | Copilot in Word | 30 Min./Angebot | — |
| Übersetzungen | DeepL Pro | Extern-Kosten gespart | — |

**ROI Schweiz:** Ø 3.70 CHF Ertrag pro investiertem Franken
**Gesamtpotential:** CHF 5'000–15'000 Ersparnis/Monat für typisches KMU

---

## Einstiegsempfehlung

1. **KI-Readiness-Check** machen (CHF 2'000–5'000, externe Berater oder WKO-Äquivalent SECO)
2. **Sofort**: alle genutzten Tools inventarisieren, AVVs abschliessen, Gratis-Versionen ablösen
3. **Einstiegstool**: Euria (kostenlos, Schweizer Hosting) für erste Experimente ohne Rechtsrisiko
4. **Skalieren**: Copilot oder ChatGPT Team für Office-Integration, wenn Datenschutz geklärt

---

## NotebookLM Recherche-Details

- Notebook-ID: `b5e8b7bf-3283-4536-8870-a5994660dd2c`
- Quellen: 120 (Stand 08.06.2026) — YouTube + WKO-Seiten + CH/EU-Datenschutz-Quellen + Tool-Vergleiche
- Erstellt: 08.06.2026
- Themen abgedeckt: Tool-Empfehlungen CH, nDSG-Pflichten, Use Cases, ROI-Zahlen

## Verbindungen

- [[user-profil]] — User lebt in der Schweiz, ZHT-Arbeit
- [[tools]] — API Keys & MCP Server
