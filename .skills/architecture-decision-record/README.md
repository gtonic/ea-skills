# Architecture Decision Record (ADR) Skill

Strukturierte Erstellung, Bewertung und Verwaltung von Architecture Decision Records (ADRs)
nach dem MADR-Template (Markdown Any Decision Records v3.0).

## Überblick

Dieser Skill unterstützt Solution Architects und Enterprise Architects bei der systematischen
Dokumentation von Architekturentscheidungen:

- **Kontext-Analyse**: Entscheidungsfrage, Decision Drivers, Constraints, Stakeholder
- **Optionsbewertung**: Pro/Contra, Entscheidungsmatrix (Weighted Scoring), Utility Tree (ATAM)
- **Entscheidungsdokumentation**: MADR v3.0, Y-Statement, Kurzform
- **Konsistenzprüfung**: Automatische Erkennung von Widersprüchen zu bestehenden ADRs
- **Konsequenzen-Map**: Visualisierung von Auswirkungen und Folge-Entscheidungen

## Verzeichnisstruktur

```
architecture-decision-record/
├── SKILL.md                              ← Skill-Definition & Workflow
├── README.md                             ← Diese Datei
└── references/
    ├── madr-template.md                  ← MADR-Template (Voll, Y-Statement, Kurz), Status-Lifecycle, Namenskonventionen
    ├── decision-drivers.md               ← Bewertungsmethoden: Pro/Contra, Weighted Scoring, Utility Tree
    └── consistency-checks.md             ← Konsistenzprüfung, ADR-Beziehungen, Konflikt-Erkennung
```

## Methodik

### Workflow (6 Schritte)

| Schritt | Beschreibung |
|---|---|
| 1. Kontext klären | Entscheidungsfrage, Decision Drivers, Constraints, Stakeholder, bestehende ADRs suchen |
| 2. Optionen identifizieren | Mind. 2–3 Optionen inkl. Status Quo; Pro/Contra erfassen |
| 3. Optionen bewerten | Pro/Contra (einfach), Weighted Scoring (Standard), Utility Tree (komplex) |
| 4. ADR erstellen | MADR v3.0 Template mit Kontext, Drivers, Optionen, Entscheidung, Konsequenzen |
| 5. Konsistenzprüfung | Widersprüche zu bestehenden ADRs erkennen; Supersede/Amend-Logik |
| 6. Konsequenzen-Map | ASCII-Visualisierung von Auswirkungen (optional, bei komplexen Entscheidungen) |

### Bewertungsmethoden

| Komplexität | Methode | Wann |
|---|---|---|
| Einfach | Pro/Contra-Liste | 2 Optionen, klare Tendenz |
| Mittel | Entscheidungsmatrix (Weighted Scoring) | Mehrere Stakeholder, Dokumentationspflicht |
| Komplex | Utility Tree + Entscheidungsmatrix | ATAM, fundamentale Architekturentscheidung |

## Trigger-Beispiele

- *„Erstelle einen ADR für die Datenbankwahl"*
- *„Dokumentiere die Entscheidung für Microservices vs. Monolith"*
- *„Bewerte die Optionen für unsere Authentifizierungsstrategie"*
- *„Prüfe bestehende ADRs auf Konsistenz"*
- *„Erstelle eine Entscheidungsmatrix für die Cloud-Provider-Wahl"*
- *„Wir müssen begründen, warum wir Framework X gewählt haben"*

## Ausgabeformate

| Format | Beschreibung | Wann |
|---|---|---|
| **Vollständiger ADR** | MADR v3.0 mit allen Abschnitten | Standard — für alle wichtigen Entscheidungen |
| **ADR + Entscheidungsmatrix** | ADR mit gewichteter Bewertungstabelle | Bei mehreren Optionen und messbaren Drivers |
| **Lightweight ADR (Y-Statement)** | Einzeiler-Format für schnelle Doku | Einfache, wenig kontroverse Entscheidungen |
| **ADR + Konsequenzen-Map** | ADR mit ASCII-Visualisierung | Weitreichende Entscheidungen mit Folge-ADRs |
| **ADR-Übersicht / Decision Log** | Tabellarische Übersicht aller ADRs | Zur Pflege und Navigation |

## Referenzdateien

| Datei | Inhalt |
|---|---|
| [madr-template.md](references/madr-template.md) | MADR-Template in 3 Varianten (Voll, Y-Statement, Kurz), Status-Lifecycle, Namenskonventionen, Frontmatter |
| [decision-drivers.md](references/decision-drivers.md) | Pro/Contra, Weighted Scoring Matrix, Utility Tree (ATAM), ISO 25010 Qualitätsattribute, Sensitivitätsanalyse |
| [consistency-checks.md](references/consistency-checks.md) | ADR-Suche im Repo, 4 Prüfkategorien (Technologie, Prinzip, Constraint, Abhängigkeit), Beziehungstypen, Supersede/Amend-Workflow |

## Synergie mit anderen Skills

| Kombination | Mehrwert |
|---|---|
| **ADR + c4-architecture** | C4-Diagramme als Kontext im ADR referenzieren; bei architekturverändernden Entscheidungen aktualisierte Diagramme empfehlen |
| **ADR + it-solution-assessment** | Lösungsbewertung als Input für den ADR; Scoring-Ergebnisse in die Entscheidungsmatrix übernehmen |
| **ADR + it-contract-analysis** | Vertragliche Implikationen bei kommerziellen Entscheidungen berücksichtigen (Lizenz, Vendor Lock-in, Exit) |
