# MADR Template — Referenz

> Markdown Any Decision Records (MADR) v3.0.0
> Quelle: https://adr.github.io/madr/

## Template-Varianten

### Variante 1: Vollständiges MADR (Standard)

```markdown
---
status: "{proposed | accepted | deprecated | superseded by [ADR-NNNN](NNNN-titel.md)}"
date: {YYYY-MM-DD}
decision-makers: {Liste der Entscheider}
consulted: {Liste der Konsultierten}
informed: {Liste der Informierten}
---

# [ADR-NNNN] {Kurztitel der Entscheidung}

## Status

{Proposed | Accepted | Deprecated | Superseded by [ADR-NNNN](NNNN-titel.md)}

## Context and Problem Statement

{Beschreibung des Kontexts und der Entscheidungsfrage. 2–5 Sätze.
Formuliere als Frage: "Wie sollen wir ...?" oder "Welche Technologie sollen wir für ... wählen?"}

## Decision Drivers

* {Driver 1, z.B. "Hohe Verfügbarkeit (99.9%) erforderlich laut NFR-001"}
* {Driver 2, z.B. "Team hat Erfahrung mit Java/Spring, nicht mit Go"}
* {Driver 3, z.B. "Budget max. 50k EUR/Jahr für Infrastruktur"}
* {Driver 4, ...}

## Considered Options

* {Option 1}
* {Option 2}
* {Option 3}
* ...

## Decision Outcome

Chosen option: "{Option X}", because {Begründung in 1–3 Sätzen. Bezug zu den Decision Drivers.}

### Consequences

#### Good

* {Positive Konsequenz 1, z.B. "Reduziert Entwicklungszeit um ca. 30%"}
* {Positive Konsequenz 2}

#### Bad

* {Negative Konsequenz / Trade-off 1, z.B. "Vendor Lock-in bei Cloud-Provider X"}
* {Negative Konsequenz 2}

#### Neutral

* {Neutrale Konsequenz, z.B. "Erfordert Migration bestehender Daten"}

### Confirmation

{Wie wird überprüft, ob die Entscheidung korrekt umgesetzt wurde?
Beispiele: "Review der Implementierung in Sprint 5", "PoC-Ergebnisse bis KW 12",
"Monitoring: Latenz < 200ms im P99", "Architektur-Review nach 3 Monaten Betrieb"}

## Pros and Cons of the Options

### {Option 1}

{2–3 Sätze Beschreibung}

* Good, because {Argument mit Bezug zu Driver}
* Good, because {Argument}
* Neutral, because {Argument}
* Bad, because {Argument}

### {Option 2}

{2–3 Sätze Beschreibung}

* Good, because {Argument}
* Bad, because {Argument}
* Bad, because {Argument}

### {Option 3}

{2–3 Sätze Beschreibung}

* Good, because {Argument}
* Bad, because {Argument}

## More Information

{Links, Referenzen, verwandte ADRs, PoC-Ergebnisse, Tickets, C4-Diagramme.}

* Links to: [ADR-XXXX](XXXX-titel.md) — {Beziehung beschreiben}
* Supersedes: [ADR-YYYY](YYYY-titel.md) — {Warum ersetzt}
* Amends: [ADR-ZZZZ](ZZZZ-titel.md) — {Was wird geändert}
```

---

### Variante 2: Y-Statement (Lightweight)

Für schnelle, einfache Entscheidungen mit wenig Diskussionsbedarf:

```markdown
# [ADR-NNNN] {Kurztitel}

## Status

{Proposed | Accepted | Deprecated | Superseded}

In the context of {Use Case / System / Feature},
facing {Concern / Entscheidungsfrage},
we decided for {Entscheidung / Option},
and against {verworfene Optionen},
to achieve {gewünschtes Qualitätsziel / Ergebnis},
accepting {Trade-offs / Nachteile / Risiken}.
```

---

### Variante 3: Kurzform

Für Entscheidungen, die wenig Kontext brauchen (z.B. Team-interne Conventions):

```markdown
# [ADR-NNNN] {Kurztitel}

## Status

{Proposed | Accepted}

## Context

{1–3 Sätze Kontext}

## Decision

{1–3 Sätze: Was wurde entschieden und warum}

## Consequences

* {Konsequenz 1}
* {Konsequenz 2}
```

---

## Status-Lifecycle

```
  ┌──────────┐
  │ Proposed │ ─── Neuer ADR, noch nicht genehmigt
  └────┬─────┘
       │ Genehmigung durch Decision-Makers
       ▼
  ┌──────────┐
  │ Accepted │ ─── Gültige, aktive Entscheidung
  └────┬─────┘
       │
       ├─── Entscheidung veraltet (z.B. Technologie End-of-Life)
       │         ▼
       │    ┌────────────┐
       │    │ Deprecated │ ─── Nicht mehr empfohlen, aber noch in Betrieb
       │    └────────────┘
       │
       └─── Neue Entscheidung ersetzt diese
                  ▼
             ┌─────────────────────────────────────┐
             │ Superseded by [ADR-XXXX](link)      │ ─── Durch neuen ADR ersetzt
             └─────────────────────────────────────┘
```

### Status-Regeln

| Transition | Wann | Aktion |
|---|---|---|
| Proposed → Accepted | Genehmigung durch Stakeholder | Status aktualisieren, Datum setzen |
| Accepted → Deprecated | Technologie/Ansatz veraltet, noch kein Ersatz | Status aktualisieren, Begründung ergänzen |
| Accepted → Superseded | Neuer ADR ersetzt diesen | Alten ADR: `Superseded by ADR-XXXX`. Neuen ADR: `Supersedes ADR-YYYY` |
| Proposed → zurückgezogen | Entscheidung doch nicht nötig | Datei löschen oder Status `Rejected` (optional) |

---

## Namenskonventionen

### Dateiname

```
NNNN-kurztitel-mit-bindestrichen.md
```

- **NNNN**: 4-stellige, fortlaufende Nummer (0001, 0002, ...)
- **Kurztitel**: Beschreibender Titel in Kleinbuchstaben mit Bindestrichen
- Keine Sonderzeichen, Umlaute als ae/oe/ue

**Beispiele:**
- `0001-use-madr-for-adrs.md`
- `0002-postgresql-as-primary-database.md`
- `0003-event-driven-architecture-for-order-processing.md`
- `0004-authentication-via-entra-id.md`

### Verzeichnisstruktur

Empfohlene Standardverzeichnisse (in Reihenfolge der Präferenz):

```
docs/decisions/          ← Bevorzugt (GitHub/Azure DevOps Standard)
doc/adr/                 ← ADR-Tools-Konvention
docs/adr/                ← Alternative
decisions/               ← Flache Struktur
```

Falls bereits ADRs im Repository existieren, verwende das bestehende Verzeichnis.
Falls keines existiert, empfehle `docs/decisions/`.

### Frontmatter (optional, empfohlen)

YAML-Frontmatter für maschinenlesbare Metadaten:

```yaml
---
status: "accepted"
date: 2025-01-15
decision-makers: ["Alice (Lead Architect)", "Bob (Tech Lead)"]
consulted: ["Security Team", "DevOps"]
informed: ["Development Teams", "Product Owner"]
---
```

**RACI-Mapping im Frontmatter:**

| Feld | RACI | Beschreibung |
|---|---|---|
| `decision-makers` | R, A | Verantwortlich, Rechenschaftspflichtig |
| `consulted` | C | Vor der Entscheidung konsultiert |
| `informed` | I | Nach der Entscheidung informiert |

---

## Sprach-Empfehlungen

| Kontext | Empfehlung | Begründung |
|---|---|---|
| Internationales Team | Englisch | Verständlich für alle |
| Deutschsprachiges Team | Deutsch | Niedrigere Hürde, präzise Formulierungen |
| Gemischt | Englisch für ADR-Struktur, Deutsch für Inhalte | Kompromiss |

**MADR-Strukturelemente** (Section Headers) bleiben immer auf Englisch:
`Context and Problem Statement`, `Decision Drivers`, `Considered Options`,
`Decision Outcome`, `Consequences`, `Pros and Cons of the Options`, `More Information`.
