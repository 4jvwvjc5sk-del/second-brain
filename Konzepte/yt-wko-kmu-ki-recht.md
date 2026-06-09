# KI-Recht für Schweizer KMU/EPU — WKO Webinar (Rechtliche Aspekte)

#ki #recht #kmu #epu #ndsg #copyright #haftung #schweiz

**Quelle:** WKO Webinar-Reihe "KI-Lösungen für EPU und KMU" — Folge 9  
**YouTube:** https://www.youtube.com/watch?v=qvLhaJt4O3g  
**Referenten:** Hans Baldinger (WKOÖ), Dr. Alexandra Ciarnau (DORDA Law Firm, Wien)  
**Analysiert:** 2026-06-08  
**NotebookLM:** ID `20483e38-6190-443b-8097-79885e7030f2` | 45 Quellen | Conversation `29350df1-d3b7-4d5f-9b1b-60d171532b2c`  
**Verwandtes Konzept:** [[yt-wko-kmu-ki]] (Tools & Use Cases)

> ⚠️ **Schweiz-Hinweis:** Das Webinar bezieht sich auf österreichisches Recht (DSGVO, EU AI Act). Für die Schweiz gelten **nDSG** (in Kraft seit 01.09.2023) und **kein direkter EU AI Act** — die rechtlichen Prinzipien sind ähnlich, die konkreten Pflichten und Strafen unterscheiden sich jedoch.

---

## 1. Input-Daten: Was darf ich der KI geben?

### Copyright / Urheberrecht
- Öffentlich verfügbare Daten ≠ automatisch nutzbar
- **Text & Data Mining (TDM):** In der EU gibt es eine gesetzliche Ausnahme (auch kommerziell), solange der Rechteinhaber **nicht explizit widersprochen** hat (z.B. via `robots.txt` oder AGB)
- Plattformen (Social Media, Stock-Photo-Seiten) sperren KI-Crawler zunehmend per AGB → Scraping wäre dann illegal
- **CH-Kontext:** Schweizer Urheberrecht (URG) enthält eine ähnliche TDM-Ausnahme für Forschung; kommerzielle Nutzung ist enger gefasst als in der EU

### Betriebsgeheimnisse / Know-how-Schutz
- Mitarbeiter, die **proprietären Code, interne Finanzdaten oder Geschäftsstrategien** in öffentliche KI-Tools (gratis ChatGPT etc.) eingeben, riskieren den **Geheimnisschutz-Status zu verlieren**
- Diese Daten fliessen in den öffentlichen Trainingspool → **Konkurrenten könnten indirekt profitieren**
- **Lösung:** Nur Enterprise-/API-Versionen verwenden (vertragliche Datenisolation garantiert)

---

## 2. Datenschutz: Personendaten & KI

### Grundregel (nDSG / DSGVO-äquivalent)
- **Personendaten in öffentliche KI eingeben = fast immer rechtswidrig** ohne gültige Rechtsgrundlage
- Besonders sensible Daten (Gesundheit, politische Ansichten, Religion) erfordern **ausdrückliche Einwilligung**

### Automatisierte Entscheidungen
- Rein automatisierte Entscheide mit rechtlichen oder erheblichen Auswirkungen auf Personen sind **grundsätzlich verboten** (Art. 21 nDSG)
- Beispiele: automatisches Recruiting-Screening, Kredit-Scoring, Profilbildung
- **Pflicht:** Ein Mensch muss im Loop bleiben und die finale Entscheidung treffen
- Bekanntes Warnsignal: Österreichisches AMS-Algorithmus-Urteil (Profilbildung von Arbeitslosen ohne Korrekturmöglichkeit = rechtswidrig)

### Praktische Pflichten CH (nDSG)
| Pflicht | Detail |
|---------|--------|
| Verzeichnis der Bearbeitungstätigkeiten | Auch KI-gestützte Prozesse müssen dokumentiert sein |
| Datenschutz-Folgenabschätzung (DSFA) | Pflicht bei hohem Risiko (z.B. automatisiertes Profiling) |
| Meldepflicht bei Verletzungen | 72h an EDÖB (Eidg. Datenschutzbeauftragter) |
| Auskunftsrecht | Betroffene können Auskunft über automatisierte Entscheide verlangen |

---

## 3. Output-Daten: Wer besitzt KI-generierte Inhalte?

### Urheberrecht an KI-Output
- **Nur natürliche Personen** können Urheber sein — KI kann kein Urheberrecht halten
- **Simpler Prompt** ("schreib ein Gedicht über Sommer") → Output = **Public Domain**, kein Schutz
- **Detaillierter, kreativer Prompt** (spezifische Stilanweisungen, narrative Kontrolle) → möglicherweise **Urheberrecht des Prompters**
- **Grauzone:** Juristische Grenze zwischen "einfachem" und "kreativem" Prompt ist nicht klar definiert

### Praktische Konsequenz für KMU
- KI-generierte Texte/Bilder können von Mitbewerbern kopiert werden, wenn kein ausreichender menschlicher Beitrag vorliegt
- **Empfehlung:** KI-Output immer substanziell überarbeiten und als Basis nutzen, nicht direkt verwenden
- Tool-AGB prüfen: Manche Tools (z.B. Neuroflash) verzichten explizit auf Rechte am Output → kommerzielle Nutzung OK

---

## 4. Haftung: Wer haftet für KI-Fehler?

### Vertragshaftung
- Wenn ein Unternehmen KI-generierten Inhalt an Kunden liefert und dieser **Fehler enthält, plagiiert oder Markenrecht verletzt** → **volle Haftung beim Unternehmen**, nicht beim KI-Anbieter
- Beispiel: Texter verwendet KI, liefert plagiierten Text → Texter haftet gegenüber Klient

### Produkthaftung (Zukunft)
- Aktuell: Produkthaftung nur für physische Güter
- EU AI Act + EU-Produkthaftungsreform: **Softwareanbieter sollen direkt für KI-Schäden haften** (in der CH noch keine entsprechende Anpassung geplant)

### Datenschutz-Bussgelder (nDSG CH)
- Bis **CHF 250'000** Busse (Privatpersonen/Verantwortliche — anders als EU: **Individuen**, nicht Unternehmen, werden gebüsst)
- DSGVO-Bussgelder sind deutlich höher (bis €20 Mio / 4% Jahresumsatz) → CH ist milder, aber nicht bussgeldfrei

---

## 5. KI-Regulierung: EU AI Act vs. Schweiz

### EU AI Act (4 Risikostufen)
| Stufe | Beispiele | Konsequenz |
|-------|-----------|------------|
| Verboten | Social Scoring, biometrische Massenüberwachung | Vollständig verboten |
| Hohes Risiko | HR/Recruiting-KI, Kredit-Scoring, kritische Infrastruktur | Strenge Aufsicht, Audits, menschliche Kontrolle |
| Begrenztes Risiko | Chatbots | Transparenzpflicht ("Du sprichst mit einer KI") |
| Minimales Risiko | Spam-Filter, KI in Videospielen | Keine Regulierung |

### Schweiz
- EU AI Act gilt **nicht direkt** in der Schweiz
- Bundesrat beobachtet die Entwicklung — mögliche freiwillige Anpassung (wie bei DSGVO → nDSG)
- **Aktuell:** Bestehende Gesetze (nDSG, OR, URG, Kartellrecht) decken die meisten KI-Risiken ab
- **Empfehlung:** EU AI Act dennoch kennen, da Schweizer Unternehmen mit EU-Kunden/Partnern betroffen sein können (extraterritoriale Wirkung)

---

## 6. Interne KI-Richtlinien — Empfehlungen

### Warum Verbote nicht funktionieren
- Verbot → "Shadow IT": Mitarbeiter nutzen KI heimlich auf privaten Geräten
- Unkontrollierter Einsatz ist riskanter als geregelter Einsatz

### Minimalinhalt einer KI-Richtlinie für Schweizer KMU
```
1. Erlaubte Tools (genehmigte Liste)
2. Verbote: Keine Personendaten und keine Betriebsgeheimnisse in öffentliche KI-Tools
3. Enterprise-/API-Versionen verwenden (Datenisolation vertraglich gesichert)
4. Output immer prüfen (Fakten, Plagiats-Check, Markenrecht)
5. Schulung: Prompt Engineering Grundlagen
6. Verantwortlicher: Wer ist intern für KI-Compliance zuständig?
```

---

## 7. Sofort-Checkliste für Schweizer KMU/EPU

- [ ] **Kein Kunden-Personendaten** in öffentliche KI eingeben (nDSG-Verletzung)
- [ ] **Kein proprietärer Code / Finanzdaten** in gratis KI-Tools (Geheimnisschutz-Verlust)
- [ ] Enterprise-Version oder API verwenden (ChatGPT Team/Enterprise, Copilot for Business etc.)
- [ ] KI-Output **immer vor Veröffentlichung prüfen** (Fakten, Plagiat, Marke)
- [ ] Interne **KI-Nutzungsrichtlinie** schriftlich festhalten
- [ ] Automatisierte Entscheide mit Auswirkungen auf Personen → **Mensch im Loop**
- [ ] Tool-AGB lesen: Gehören Outputs dem Tool-Anbieter?

---

## NotebookLM Research — Schlüsselerkenntnisse (2026-06-08)

### nDSG-Pflichten für KMU (konkret)
- **Auftragsbearbeitungsvertrag (AVV)** mit KI-Anbieter zwingend wenn Personendaten verarbeitet werden
- **Datenschutzerklärung** anpassen: KI-Einsatz, Zweck und Tools offenlegen
- **DSFA** (Datenschutz-Folgenabschätzung) bei Profiling oder automatisierten Entscheiden mit hohem Risiko
- **Bussen bis CHF 250'000** treffen Einzelpersonen (nicht das Unternehmen!) — anders als EU
- Business-/Enterprise-Versionen (ChatGPT Team, M365 Copilot) sind nDSG-konform; Gratis-Versionen nicht

### Urheberrecht CH (2025/2026)
- Schweizer URG Art. 6: Nur natürliche Personen können Urheber sein → KI-Output ist Public Domain wenn kein wesentlicher menschlicher Beitrag
- **Motion Gössi** (2025): Parlament will Urheberrecht verschärfen — geschützte Werke nur mit Einwilligung für KI-Training
- Bundesrat: Vernehmlassungsvorlage zu KI-Regeln bis Ende 2026 geplant
- **Dokumentation des Entstehungsprozesses** (Prompts, Nachbearbeitung) = Beweis für Urheberrechtsschutz
- Schweizer Gerichte werden sich vorerst an deutschen/US-Urteilen orientieren (noch keine eigene Rechtsprechung)

### Aktionsplan KI-Compliance CH (priorisiert)
**Sofort (Monat 1):**
1. Schatten-KI inventarisieren (Mitarbeiter befragen ohne Sanktionen)
2. Datenklassifizierung: Öffentlich / Intern / Besonders schützenswert
3. Sofortverbot: Keine vertraulichen Daten in Gratis-KI-Tools

**Kurzfristig (Monat 1–3):**
4. Interne KI-Richtlinie erstellen (inkl. Human-over-the-loop Pflicht)
5. Umstieg auf Business-Lizenzen + AVV abschliessen
6. Datenschutzerklärung anpassen
7. Mitarbeiter-Schulung (30–60 Min., Fokus: Prompting + Datensicherheit)

**Mittelfristig (Monat 3–6):**
8. DSFA für riskante KI-Prozesse
9. KI-Output-Dokumentation einführen (Urheberrecht)
10. EU AI Act Pflichten prüfen (bei EU-Kunden)
11. Rechtsentwicklung verfolgen (Motion Gössi, Bundesrat-Vorlage 2026)

**Für sensible Branchen** (Treuhand, Recht, Medizin): Schweizer Hosting prüfen (AlpineAI, Swisscom Cloud)

## Quellen-Empfehlungen für Vertiefung
- EDÖB (Eidg. Datenschutzbeauftragter): edoeb.admin.ch — Leitlinien zu KI und nDSG
- SECO / kmu.admin.ch: Praxistipps für Schweizer KMU
- Homburger Rechtsanwälte: Swiss AI Regulation — Tailored Rules
- Pestalozzi Law: Navigating AI – Part 3: Liability
- EU AI Act Volltext: eur-lex.europa.eu (für CH-Unternehmen mit EU-Bezug relevant)
- SWICO Mustervorlage: KI-Leitlinie für Mitarbeitende (PDF, kostenlos)
