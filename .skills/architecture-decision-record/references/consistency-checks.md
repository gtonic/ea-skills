# ADR-Konsistenzprüfung — Referenz

## Bestehende ADRs finden

### Suchstrategie

Durchsuche das Repository nach ADR-Dateien mit folgenden Mustern:

```
**/adr/**/*.md
**/docs/decisions/**/*.md
**/doc/adr/**/*.md
**/decisions/**/*.md
**/architecture/decisions/**/*.md
**/doc/architecture/decisions/**/*.md
```

Zusätzlich nach Index-Dateien:

```
**/adr/README.md
**/decisions/README.md
**/adr/index.md
**/DECISIONS.md
```

### ADR-Erkennung

Eine Markdown-Datei ist wahrscheinlich ein ADR, wenn:

1. **Dateiname** dem Muster `NNNN-*.md` folgt (z.B. `0001-use-madr.md`)
2. **Inhalt** typische ADR-Abschnitte enthält: `## Status`, `## Context`, `## Decision`
3. **Frontmatter** ein `status`-Feld enthält
4. **Verzeichnis** eines der bekannten ADR-Verzeichnisse ist

---

## Konsistenzprüfung — Prüfkategorien

### 1. Technologie-Konflikte

**Prüfung**: Wählt der neue ADR eine Technologie, die ein bestehender ADR bereits
für denselben Einsatzzweck festgelegt hat?

| Konflikttyp | Beispiel | Schwere |
|---|---|---|
| **Direkte Ersetzung** | ADR-0002: PostgreSQL als DB → Neuer ADR: MongoDB als DB | 🔴 Hoch |
| **Überlappung** | ADR-0003: Redis als Cache → Neuer ADR: Memcached als Cache | 🔴 Hoch |
| **Ergänzung** | ADR-0002: PostgreSQL als OLTP-DB → Neuer ADR: ClickHouse als Analytics-DB | 🟢 Kein Konflikt |
| **Teilkonflikt** | ADR-0005: REST für alle APIs → Neuer ADR: gRPC für Service-to-Service | 🟡 Mittel |

**Prüflogik:**

```
FÜR JEDEN bestehenden ADR mit Status "Accepted":
  WENN gleiche Technologie-Kategorie (DB, Cache, Messaging, API-Style, Auth, ...):
    WENN gleicher Einsatzzweck/Scope:
      → 🔴 WARNUNG: Direkter Konflikt
      → Empfehlung: Neuer ADR sollte alten als "Superseded" markieren
    WENN überlappender Scope:
      → 🟡 HINWEIS: Scope-Abgrenzung prüfen
      → Empfehlung: Einsatzbereiche explizit abgrenzen
```

### 2. Architekturprinzip-Konflikte

**Prüfung**: Verletzt der neue ADR ein Architekturprinzip, das ein bestehender ADR festlegt?

| Prinzip (aus ADR) | Neuer ADR | Konflikt? |
|---|---|---|
| "Microservices-Architektur" | Shared Database für 3 Services | 🔴 Ja |
| "Cloud-native, containerisiert" | VM-basiertes Deployment | 🔴 Ja |
| "API-First Design" | Direkte DB-Zugriffe zwischen Services | 🔴 Ja |
| "Event-Driven Architecture" | Synchrone REST-Calls für alle Integrationen | 🟡 Teilweise |

**Prüflogik:**

```
FÜR JEDEN bestehenden ADR der ein Prinzip/Pattern festlegt:
  PRÜFE ob der neue ADR:
    - Das Prinzip explizit verletzt
    - Eine Ausnahme vom Prinzip darstellt (kann legitim sein)
    - Das Prinzip ergänzt oder verfeinert

  BEI VERLETZUNG:
    → 🔴 WARNUNG ausgeben
    → Empfehlung: Ausnahme begründen ODER Prinzip-ADR aktualisieren

  BEI AUSNAHME:
    → 🟡 HINWEIS: "Ausnahme zu ADR-XXXX — bitte explizit begründen"
```

### 3. Constraint-Konflikte

**Prüfung**: Widerspricht der neue ADR einem Constraint aus einem bestehenden ADR?

Typische Constraint-Kategorien:

| Constraint | Beispiel |
|---|---|
| **Budget** | ADR-0001: "Max. 100k/Jahr für Cloud" → Neuer ADR wählt Service für 80k/Jahr (verbleibendes Budget?) |
| **Compliance** | ADR-0004: "Alle Daten in EU" → Neuer ADR wählt US-only SaaS |
| **Technologie-Stack** | ADR-0003: "Java/Spring für alle Backend-Services" → Neuer ADR wählt Python/FastAPI |
| **Vendor** | ADR-0006: "Azure als Cloud-Provider" → Neuer ADR nutzt AWS-spezifischen Service |

### 4. Abhängigkeits-Konflikte

**Prüfung**: Baut der neue ADR auf Annahmen auf, die durch bestehende ADRs möglicherweise
nicht mehr gelten?

```
FÜR den neuen ADR:
  IDENTIFIZIERE Abhängigkeiten:
    - Welche Infrastruktur setzt der ADR voraus?
    - Welche anderen Entscheidungen werden als gegeben angenommen?
    - Welche ADRs werden referenziert?

  PRÜFE ob die Abhängigkeiten noch gelten:
    - Referenzierte ADRs noch "Accepted" (nicht Deprecated/Superseded)?
    - Vorausgesetzte Infrastruktur noch verfügbar?
    - Annahmen noch korrekt?
```

---

## ADR-Beziehungen

### Beziehungstypen

| Beziehung | Syntax im ADR | Bedeutung | Aktion |
|---|---|---|---|
| **Supersedes** | `Supersedes: [ADR-XXXX](link)` | Neuer ADR ersetzt alten vollständig | Alter ADR → Status `Superseded by ADR-YYYY` |
| **Amends** | `Amends: [ADR-XXXX](link)` | Neuer ADR ändert Teile des alten | Alter ADR bleibt `Accepted`, Verweis ergänzen |
| **Links to** | `Links to: [ADR-XXXX](link)` | Inhaltlicher Zusammenhang | Keine Statusänderung |
| **Depends on** | `Depends on: [ADR-XXXX](link)` | Setzt Entscheidung aus anderem ADR voraus | Abhängigkeit dokumentieren |
| **Contradicts** | `Contradicts: [ADR-XXXX](link)` | Bewusster Widerspruch (mit Begründung) | Ausnahme dokumentieren |

### Supersede-Workflow

Wenn ein neuer ADR einen bestehenden ersetzt:

**1. Neuer ADR:**
```markdown
## More Information

* Supersedes: [ADR-0003](0003-rest-api-for-all-services.md) — gRPC bietet bessere
  Performance für Service-to-Service-Kommunikation (siehe Decision Drivers).
```

**2. Alter ADR aktualisieren:**
```markdown
## Status

~~Accepted~~ Superseded by [ADR-0007](0007-grpc-for-service-communication.md)
```

Auch im Frontmatter:
```yaml
---
status: "superseded by ADR-0007"
date: 2025-01-15
superseded-by: "0007-grpc-for-service-communication.md"
superseded-date: 2025-03-20
---
```

### Amend-Workflow

Wenn ein neuer ADR einen bestehenden teilweise ändert:

**1. Neuer ADR:**
```markdown
## More Information

* Amends: [ADR-0002](0002-postgresql-as-primary-db.md) — Ergänzt die Entscheidung um
  Read Replicas für Analytics-Queries.
```

**2. Alter ADR ergänzen** (unter `## More Information`):
```markdown
* Amended by: [ADR-0008](0008-postgresql-read-replicas.md) — Read Replicas ergänzt.
```

---

## Konsistenzprüfung — Ausgabeformat

### Bei Konflikten

```markdown
> ⚠️ **Konsistenzwarnung**
>
> Die Entscheidung in diesem ADR steht möglicherweise im Widerspruch zu:
>
> | ADR | Titel | Konflikttyp | Beschreibung |
> |---|---|---|---|
> | [ADR-0003](0003-rest-api.md) | REST API for all Services | 🔴 Technologie | Neuer ADR wählt gRPC, bestehender ADR legt REST fest |
> | [ADR-0001](0001-cloud-native.md) | Cloud-Native Architecture | 🟡 Prinzip | VM-Deployment widerspricht Cloud-Native-Prinzip |
>
> **Empfohlene Aktionen:**
> 1. ADR-0003 als `Superseded by ADR-NNNN` markieren
> 2. Ausnahme zu ADR-0001 explizit in diesem ADR begründen
```

### Ohne Konflikte

```markdown
> ✅ **Konsistenzprüfung bestanden**
>
> Keine Widersprüche zu den {N} bestehenden ADRs im Repository gefunden.
>
> **Verwandte ADRs:**
> - [ADR-0002](0002-postgresql.md) — Builds on: Datenbankwahl als Grundlage
> - [ADR-0005](0005-event-sourcing.md) — Related: Event-Store nutzt gleiche DB
```

### Wenn keine ADRs existieren

```markdown
> ℹ️ **Erster ADR im Repository**
>
> Keine bestehenden ADRs gefunden. Dies wird ADR-0001.
> Empfehlung: Lege ein ADR-Verzeichnis an (`docs/decisions/`) und erstelle
> eine README.md mit dem Decision Log.
```

---

## Best Practices für ADR-Pflege

### Regelmäßige Reviews

| Intervall | Prüfung |
|---|---|
| **Bei jedem neuen ADR** | Konsistenzprüfung gegen alle bestehenden ADRs |
| **Quartalsweise** | Alle ADRs mit Status "Accepted" auf Aktualität prüfen |
| **Bei Major-Release** | ADR-Relevanz für neue Version prüfen |
| **Bei Team-Wechsel** | ADRs als Onboarding-Material nutzen, Verständlichkeit prüfen |

### Decision Log pflegen

Halte eine zentrale Übersicht aller ADRs aktuell:

```markdown
# Architecture Decision Log

> Letzte Aktualisierung: {Datum}

| # | Titel | Status | Datum | Entscheider |
|---|---|---|---|---|
| [0001](0001-use-madr.md) | Use MADR for ADRs | ✅ Accepted | 2025-01-10 | Team |
| [0002](0002-postgresql.md) | PostgreSQL as primary DB | ✅ Accepted | 2025-01-15 | Alice |
| [0003](0003-rest-api.md) | REST API for Services | ~~Accepted~~ | 2025-02-01 | Bob |
| → | Superseded by ADR-0007 | | 2025-03-20 | |
| [0007](0007-grpc-s2s.md) | gRPC for Service-to-Service | ✅ Accepted | 2025-03-20 | Alice |
```

### ADR-Hygiene-Checkliste

- [ ] Jeder ADR hat einen eindeutigen Status
- [ ] Superseded ADRs verweisen auf ihren Nachfolger
- [ ] Keine verwaisten ADRs (ohne Bezug zum aktuellen System)
- [ ] Decision Log ist aktuell
- [ ] Neue Team-Mitglieder können ADRs als Kontext für Architektur-Entscheidungen lesen
