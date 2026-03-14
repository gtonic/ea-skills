# EA Skills

Enterprise Architecture Skills für GitHub Copilot — spezialisierte Fähigkeiten für Architektur-Dokumentation, IT-Vertragsanalyse und IT-Lösungsbewertung im EU/DACH-Kontext.

## Installation

Alle Skills installieren:

```bash
npx skills add gtonic/ea-skills
```

Einzelnen Skill installieren:

```bash
npx skills add gtonic/ea-skills/c4-architecture
npx skills add gtonic/ea-skills/it-contract-analysis
npx skills add gtonic/ea-skills/it-solution-assessment
```

## Voraussetzungen

- GitHub Copilot (Chat) mit Skill-Unterstützung
- Skills werden im Workspace unter `.skills/` abgelegt

## Übersicht

| Skill | Zweck | Sprache | Besonderheit |
|---|---|---|---|
| [c4-architecture](#c4-architecture) | Architektur-Dokumentation (C4-Modell) | DE / EN | ASCII-Notation, 5 Diagrammtypen |
| [it-contract-analysis](#it-contract-analysis) | IT-Vertragsrisikoanalyse | DE | ⚠️ Enterprise-Endpunkt erforderlich |
| [it-solution-assessment](#it-solution-assessment) | IT-Lösungsbewertung | DE | SaaS/On-Prem-Vergleich, K.O.-Kriterien |

## Enthaltene Skills

### c4-architecture

Generiert Software-Architektur-Dokumentation nach dem C4-Modell in ASCII-Notation.

| Eigenschaft | Detail |
|---|---|
| **Diagrammtypen** | System Context, Container, Component, Deployment, Dynamic |
| **Notation** | ASCII (keine Mermaid-Abhängigkeit) |
| **Zielgruppe** | Solution Architects, Integration Architects, Entwickler, DevOps |
| **Sprachen** | DE / EN |

**Trigger-Beispiele:**
- *„Erstelle ein C4-Diagramm für unser System"*
- *„Zeige den Authentifizierungsflow als Dynamic Diagram"*
- *„Dokumentiere die Container-Architektur"*
- *„Schnittstellenkommunikation zwischen System A und B"*

```
.skills/c4-architecture/
├── SKILL.md                        # Hauptinstruktionen
├── README.md                       # Dokumentation & Beispiele
└── references/
    ├── c4-syntax.md                # ASCII-Notationsreferenz
    ├── common-mistakes.md          # Anti-Patterns & Fehlervermeidung
    └── advanced-patterns.md        # Microservices, Event-Driven, Deployment, Dynamic Patterns
```

---

### it-contract-analysis

> ⚠️ **Erfordert abgesicherten Enterprise-AI-Endpunkt** — Der Skill fragt vor jeder Analyse aktiv ab, ob ein abgesicherter Endpunkt vorliegt. Ohne Bestätigung wird die Analyse verweigert.

Strukturierte, quantitative IT-Vertragsrisikoanalyse für den EU/DACH-Rechtsraum (AT, DE, CH, EU).

| Eigenschaft | Detail |
|---|---|
| **Methodik** | Ampelsystem (GRÜN/GELB/ROT) + Risikoscore (1–25) |
| **Rechtsräume** | ABGB, BGB, OR, DSGVO, NIS2, AI Act, Data Act, EVB-IT |
| **Vertragstypen** | SaaS, Cloud, Outsourcing, Systemintegration, Softwarelizenz, IT-Beratung, AVV |
| **Sprache** | DE |

**Trigger-Beispiele:**
- *„Analysiere diesen SaaS-Vertrag"*
- *„IT-Vertragsrisikobewertung für den Cloud-Vertrag"*
- *„Prüfe die DSGVO/AVV-Compliance"*
- *„Erstelle ein Risikoregister für das Vertragsportfolio"*

```
.skills/it-contract-analysis/
├── SKILL.md                        # Methodik & Anweisungen
├── README.md                       # Dokumentation
├── references/
│   ├── it-contracts.md             # IT-Vertragstypen & 50-Punkte-Checkliste
│   ├── dach-legal-framework.md     # DACH-Zivilrecht
│   └── eu-regulations.md           # EU-Regulatorik
└── evals/
    ├── evals.json                  # Evaluierungs-Szenarien
    └── sample-contracts/           # Musterverträge
```

---

### it-solution-assessment

Strukturierte Bewertung von IT-Projektanträgen für SaaS- und On-Premises-Lösungen.

| Eigenschaft | Detail |
|---|---|
| **Methodik** | Gewichtetes Scoring (0–3) + Ampelsystem (GRÜN/GELB/ROT) + K.O.-Kriterien |
| **Lösungstypen** | SaaS, On-Premises, Hybrid, Vergleich |
| **Bewertungsdimensionen** | Vendor, Sicherheit, Compliance, Architektur, Integration, Betrieb |
| **Sprache** | DE |

**Trigger-Beispiele:**
- *„Bewerte diese SaaS-Lösung"*
- *„Erstelle einen IT-Steckbrief für [Produkt]"*
- *„Vergleiche Lösung A vs. Lösung B"*
- *„IT-Projektantrag bewerten"*
- *„Vendor Due Diligence für [Anbieter]"*

```
.skills/it-solution-assessment/
├── SKILL.md                        # Hauptinstruktionen & Methodik
├── README.md                       # Dokumentation & Beispiele
└── references/
    ├── saas-criteria.md            # SaaS-Kriterienkatalog (55 Kriterien)
    ├── onprem-criteria.md          # On-Prem-Kriterienkatalog (68 Kriterien)
    ├── vendor-assessment.md        # Vendor Due Diligence (29 Kriterien)
    ├── security-compliance.md      # Sicherheit & Regulatorik (50 Kriterien)
    └── scoring-templates.md        # Bewertungsvorlagen & Vergleichsmatrix
```

## Skill-Zusammenspiel

Die Skills können unabhängig voneinander oder kombiniert eingesetzt werden:

- **c4-architecture** + **it-solution-assessment**: Architekturdiagramme als Grundlage für die technische Bewertung einer Lösung
- **it-contract-analysis** + **it-solution-assessment**: Vertragsprüfung ergänzt die Vendor-/Compliance-Bewertung
- **it-contract-analysis** erkennt automatisch, ob der allgemeine [Contract Analysis Skill](https://github.com/skills/contract-analysis) installiert ist, und delegiert nicht-IT-spezifische Verträge (Bau, Arbeitsrecht, Immobilien) dorthin

## Lizenz

MIT — siehe [LICENSE](../LICENSE).