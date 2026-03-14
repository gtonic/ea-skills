# NFR-Checklist Skill

Systematische Erhebung, Dokumentation und Priorisierung von Non-Functional Requirements (NFRs)
nach ISO 25010 und TOGAF-Qualitätsattributen.

## Überblick

Dieser Skill unterstützt Solution Architects bei der strukturierten Erfassung nicht-funktionaler
Anforderungen — die wichtigsten Treiber für Architekturentscheidungen und zugleich die am
häufigsten vergessenen Anforderungen in Projekten:

- **Interaktiver Dialog**: Kategorie für Kategorie durch 11 Qualitätsattribute (ISO 25010 + TOGAF)
- **Messbare Kriterien**: Quality Attribute Scenarios mit Stimulus, Response Measure, Schwellenwerten
- **Priorisierung**: MoSCoW + Architekturrelevanz (H/M/L) mit Priorisierungsmatrix
- **Architektur-Tactics**: Konkrete Maßnahmen pro NFR inklusive Trade-offs
- **Defaults**: Vorkonfigurierte Schwellenwerte je nach Systemkritikalität

## Verzeichnisstruktur

```
nfr-checklist/
├── SKILL.md                                  ← Skill-Definition & Workflow (6 Schritte)
├── README.md                                 ← Diese Datei
└── references/
    ├── iso25010-quality-model.md              ← 11 Qualitätsattribute, Sub-Charakteristiken, Szenario-Vorlagen
    ├── nfr-catalog-template.md                ← Katalog-Templates (Voll, Kompakt, Karten), Messkriterien-Referenz
    └── architecture-tactics.md                ← Architektur-Tactics pro Qualitätsattribut, Trade-offs, Mapping
```

## Methodik

### Workflow (6 Schritte)

| Schritt | Beschreibung |
|---|---|
| 1. Kontext erfassen | System, Typ, Kritikalität, Stakeholder, bestehende Anforderungen |
| 2. NFR-Kategorien durchgehen | Interaktiver Dialog durch 11 Kategorien (ISO 25010 + TOGAF) |
| 3. NFRs priorisieren | MoSCoW + Architekturrelevanz, Priorisierungsmatrix |
| 4. Architekturmaßnahmen ableiten | Tactics pro NFR, Trade-offs, ADR-Empfehlungen |
| 5. NFR-Katalog erstellen | Strukturiertes Ausgabeformat (4 Varianten) |
| 6. Validierung | Vollständigkeits- und Qualitätsprüfung |

### NFR-Kategorien (11)

| # | Kategorie | Quelle | Architekturrelevanz |
|---|---|---|---|
| 1 | Performance Efficiency | ISO 25010 | Sehr hoch |
| 2 | Reliability | ISO 25010 | Sehr hoch |
| 3 | Security | ISO 25010 | Sehr hoch |
| 4 | Scalability | TOGAF | Hoch |
| 5 | Maintainability | ISO 25010 | Hoch |
| 6 | Compatibility | ISO 25010 | Mittel |
| 7 | Portability | ISO 25010 | Mittel |
| 8 | Usability | ISO 25010 | Mittel |
| 9 | Functional Suitability | ISO 25010 | Niedrig |
| 10 | Compliance | Cross-cutting | Hoch |
| 11 | Operational | TOGAF | Hoch |

## Trigger-Beispiele

- *„Erhebe die NFRs für unser neues System"*
- *„Erstelle einen NFR-Katalog für die Web-App"*
- *„Welche Verfügbarkeitsanforderungen brauchen wir?"*
- *„Definiere Performance-Anforderungen für die API"*
- *„Welche Architekturmaßnahmen ergeben sich aus den NFRs?"*
- *„Prüfe ob wir NFRs vergessen haben"*
- *„SLA für das neue System definieren"*

## Ausgabeformate

| Format | Beschreibung | Wann |
|---|---|---|
| **Vollständiger NFR-Katalog** | Alle NFRs mit Szenarien, Messkriterien, Maßnahmen | Standard — umfassende Dokumentation |
| **Übersichtstabelle** | Kompakte Tabelle (ID, Metrik, Schwellenwert, Prio) | Für Präsentationen, Reviews |
| **NFR-Karten** | Eine Karte pro NFR (Workshop/Backlog-Format) | Für Stakeholder-Workshops, Sprint-Planung |
| **Architekturimplikationen-Report** | Fokus auf architekturtreibende NFRs und Tactics | Für Architecture Board, ADR-Input |

## Referenzdateien

| Datei | Inhalt |
|---|---|
| [iso25010-quality-model.md](references/iso25010-quality-model.md) | 11 Qualitätsattribute mit Sub-Charakteristiken, Metriken, Stakeholder-Fragen, Szenario-Vorlagen, Übersichtsgrafik |
| [nfr-catalog-template.md](references/nfr-catalog-template.md) | 4 Template-Varianten (Voll, Kompakt, Karten, Status), Messkriterien-Referenztabelle, Verifikationsmethoden |
| [architecture-tactics.md](references/architecture-tactics.md) | Tactics für alle 11 Kategorien, Trade-offs, NFR→Tactic-Schnellreferenz |

## Synergie mit anderen Skills

| Kombination | Mehrwert |
|---|---|
| **nfr-checklist + architecture-decision-record** | NFRs sind die wichtigsten Decision Drivers für ADRs. Bei Architekturrelevanz H wird ein ADR empfohlen. |
| **nfr-checklist + c4-architecture** | C4-Diagramme zeigen, welche Komponenten von welchen NFRs betroffen sind. Deployment-Diagramme referenzieren Verfügbarkeits-/Skalierbarkeits-NFRs. |
| **nfr-checklist + it-solution-assessment** | NFRs liefern die Bewertungskriterien für die Lösungsbewertung. Der Kriterienkatalog wird gegen den NFR-Katalog abgeglichen. |
| **nfr-checklist + it-contract-analysis** | Compliance- und Security-NFRs fließen in die Vertragsprüfung ein (SLA, Verfügbarkeitsgarantien, Datenschutz). |
