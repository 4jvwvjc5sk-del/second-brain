---
name: automatisierung-framework
description: Entscheidungsframework für Automatisierungen — regelbasiert vs. KI vs. Agent
metadata:
  type: reference
---

# Automatisierungs-Entscheidungsframework

#automatisierung #n8n #ki-agent #framework

Bei jeder Automatisierungs- oder KI-Anfrage **von oben nach unten** durchgehen — erste zutreffende Kategorie wählen:

| Typ | Wann verwenden | Merkmale |
|-----|----------------|----------|
| **1. Regelbasierte Automatisierung** | Klares "wenn X → dann Y", kein Interpretationsbedarf | Kein KI-Schritt nötig; schnell, zuverlässig, günstig |
| **2. KI Automatisierung** | Fester Workflow, aber ein Schritt braucht KI (z.B. Klassifizierung, Textgenerierung) | Struktur ist vordefiniert; KI ist nur ein Schritt im Ablauf |
| **3. Halbautomatisch / Human in the Loop** | Automation läuft selbständig, hält aber an kritischen Stellen an | KI macht Vorarbeit, Mensch gibt grünes Licht |
| **4. KI Agent** | Konzeptionell einfach, aber kombinatorisch komplex (viele mögliche Tool-Reihenfolgen) | NUR wenn: sehr spezifischer Use Case + keine sinnvolle feste Reihenfolge definierbar |

## Faustregel
**Einfacher ist oft besser.** Agenten nur wenn wirklich nötig — Halluzinationen multiplizieren sich mit jedem Loop.

## KI Agent VERMEIDEN wenn
- Fehler kritisch sind (Buchhaltung, Fakten, Kalender-Einträge)
- Die Reihenfolge der Schritte klar definierbar ist
- Mehrere Agenten hintereinander geschaltet werden müssten

## Verbindungen
- [[automation-advisor]] — Skill für n8n Workflow-Planung
- [[workflows]] — Standard-Workflows
