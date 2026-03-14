# Decision Drivers & Optionsbewertung — Referenz

## Bewertungsmethoden

### 1. Pro/Contra-Liste (einfach)

Für einfache Entscheidungen mit 2 Optionen und klarer Tendenz.

```markdown
### Option A: PostgreSQL

* ✅ Team hat 5 Jahre Erfahrung
* ✅ Open Source, keine Lizenzkosten
* ✅ Hervorragende JSON-Unterstützung (JSONB)
* ❌ Horizontale Skalierung aufwändig
* ❌ Kein nativer Graph-Support

### Option B: MongoDB

* ✅ Horizontale Skalierung out-of-the-box
* ✅ Schema-Flexibilität
* ❌ Team muss MongoDB erst lernen (3–6 Monate)
* ❌ Lizenzkosten bei Enterprise-Features
* ❌ ACID-Transaktionen nur eingeschränkt
```

---

### 2. Entscheidungsmatrix / Weighted Scoring (Standard)

Für Entscheidungen mit mehreren Optionen und Treibern. Die Standardmethode.

#### Schritt-für-Schritt

**1. Decision Drivers identifizieren und gewichten**

| Driver | Gewicht | Begründung |
|---|---|---|
| Performance (Latenz < 100ms P99) | 5 (Hoch) | SLA-Anforderung |
| Wartbarkeit / Codequalität | 4 (Hoch) | Langfristige Entwicklung |
| Team-Erfahrung | 4 (Hoch) | Time-to-Market entscheidend |
| Betriebskosten (jährlich) | 3 (Mittel) | Budgetrahmen 50k/Jahr |
| Community / Ecosystem | 2 (Niedrig) | Nice-to-have, nicht kritisch |

**Gewichtungsskala:**

| Wert | Bedeutung | Beschreibung |
|---|---|---|
| 5 | Must-have | Nicht verhandelbar, K.O.-Kriterium |
| 4 | Hoch | Wichtig, signifikanter Einfluss |
| 3 | Mittel | Relevant, aber nicht entscheidend |
| 2 | Niedrig | Nice-to-have |
| 1 | Minimal | Kaum relevant, nur bei Gleichstand |

**2. Optionen bewerten**

| Bewertung | Symbol | Punkte | Beschreibung |
|---|---|---|---|
| Sehr gut | `++` | +2 | Erfüllt Driver vollständig, kein Trade-off |
| Gut | `+` | +1 | Erfüllt Driver größtenteils |
| Neutral | `o` | 0 | Weder Vorteil noch Nachteil |
| Schlecht | `-` | -1 | Erfüllt Driver schlecht, Trade-off |
| Sehr schlecht | `--` | -2 | Versagt bei diesem Driver, K.O.-Risiko |

**3. Matrix berechnen**

| Driver | Gewicht (G) | Option A | Score A | Option B | Score B | Option C | Score C |
|---|---|---|---|---|---|---|---|
| Performance | 5 | ++ | 10 | + | 5 | o | 0 |
| Wartbarkeit | 4 | + | 4 | ++ | 8 | + | 4 |
| Team-Erfahrung | 4 | ++ | 8 | - | -4 | o | 0 |
| Betriebskosten | 3 | o | 0 | + | 3 | ++ | 6 |
| Community | 2 | + | 2 | + | 2 | - | -2 |
| **Gesamt** | | | **24** | | **14** | | **8** |

> Score = Gewicht × Bewertungspunkte

**4. Ergebnis interpretieren**

- **Klarer Gewinner** (Abstand > 20%): Empfehlung aussprechen
- **Knapper Vorsprung** (Abstand < 20%): Trade-offs explizit diskutieren,
  Sensitivitätsanalyse empfehlen
- **Gleichstand**: Auf K.O.-Kriterien prüfen, zusätzliche Drivers identifizieren

---

### 3. Utility Tree (komplex / ATAM)

Für komplexe Architekturentscheidungen, Architecture Tradeoff Analysis Method (ATAM),
oder wenn Qualitätsattribute hierarchisch strukturiert werden müssen.

#### Aufbau

```
                        ┌──────────────┐
                        │   Utility    │
                        │  (Gesamt-    │
                        │   nutzen)    │
                        └──────┬───────┘
                               │
               ┌───────────────┼───────────────┐
               │               │               │
               ▼               ▼               ▼
        ┌────────────┐  ┌────────────┐  ┌────────────┐
        │ Performance│  │ Security   │  │Modifiability│
        │  (30%)     │  │  (25%)     │  │  (25%)     │
        └──────┬─────┘  └──────┬─────┘  └──────┬─────┘
               │               │               │
          ┌────┴────┐    ┌────┴────┐     ┌────┴────┐
          │         │    │         │     │         │
          ▼         ▼    ▼         ▼     ▼         ▼
      Latenz    Throughput AuthN   AuthZ  Plugin   API
      (H,H)     (H,M)    (H,H)  (H,M)  (M,H)   (M,M)

      (Wichtigkeit, Schwierigkeit)
      H=High, M=Medium, L=Low
```

#### Schritt-für-Schritt

**1. Qualitätsattribute identifizieren** (oberste Ebene)

Verwende ISO 25010 als Checkliste:

| Qualitätsattribut | Beschreibung | Typische Szenarien |
|---|---|---|
| **Performance Efficiency** | Latenz, Throughput, Ressourcenverbrauch | "API-Response < 200ms" |
| **Reliability** | Verfügbarkeit, Fehlertoleranz, Wiederherstellung | "99.9% Uptime" |
| **Security** | Vertraulichkeit, Integrität, Authentizität | "DSGVO-konform" |
| **Maintainability** | Modularität, Testbarkeit, Analysierbarkeit | "Unabhängig deploybar" |
| **Portability** | Anpassbarkeit, Installierbarkeit | "Multi-Cloud-fähig" |
| **Compatibility** | Interoperabilität, Koexistenz | "REST + GraphQL" |
| **Usability** | Erlernbarkeit, Bedienbarkeit | "Onboarding < 1 Tag" |
| **Functional Suitability** | Korrektheit, Vollständigkeit | "Alle Use Cases abgedeckt" |

**2. Quality Attribute Scenarios formulieren**

Für jedes relevante Qualitätsattribut mindestens ein konkretes Szenario:

| Teil | Beschreibung | Beispiel |
|---|---|---|
| **Stimulus** | Auslösendes Ereignis | "100 gleichzeitige API-Requests" |
| **Source** | Woher kommt der Stimulus | "Endbenutzer via Web-App" |
| **Environment** | Unter welchen Bedingungen | "Normalbetrieb, Peak-Hour" |
| **Artifact** | Was wird beeinflusst | "Order-Service" |
| **Response** | Erwartete Reaktion | "Alle Requests werden bearbeitet" |
| **Response Measure** | Messbare Metrik | "P99 Latenz < 200ms" |

**3. Prioritäten zuweisen**

Jedes Szenario bewerten nach:
- **Wichtigkeit** für das Business (H/M/L)
- **Schwierigkeit** der Umsetzung (H/M/L)

**Priorisierungsmatrix:**

|  | Schwierigkeit: H | Schwierigkeit: M | Schwierigkeit: L |
|---|---|---|---|
| **Wichtigkeit: H** | ⚡ Architektur-kritisch | ⚡ Architektur-relevant | ✅ Muss funktionieren |
| **Wichtigkeit: M** | ⚠️ Risiko beachten | 📋 Standard-Anforderung | ✅ Einfach umsetzbar |
| **Wichtigkeit: L** | ❓ Hinterfragen (lohnt sich?) | 📋 Nice-to-have | ➡️ Später |

**4. Optionen gegen den Utility Tree bewerten**

Jede Option wird gegen die priorisierten Szenarien bewertet:

| Szenario | Prio | Option A | Option B | Option C |
|---|---|---|---|---|
| Latenz < 200ms (H,H) | ⚡ | ++ | + | o |
| 99.9% Uptime (H,M) | ⚡ | + | ++ | + |
| DSGVO-konform (H,H) | ⚡ | + | + | ++ |
| Plugin-Architektur (M,H) | ⚠️ | -- | ++ | o |
| Multi-Cloud (M,M) | 📋 | o | + | ++ |

---

## Decision Drivers — Häufige Kategorien

### Technische Drivers

| Kategorie | Beispiel-Driver |
|---|---|
| **Performance** | Latenz, Throughput, Ressourcenverbrauch, Skalierbarkeit |
| **Reliability** | Verfügbarkeit (SLA), Disaster Recovery, Fehlertoleranz |
| **Security** | Verschlüsselung, Authentifizierung, Autorisierung, Compliance |
| **Maintainability** | Code-Qualität, Testbarkeit, Deployment-Frequenz |
| **Interoperability** | API-Standards, Protokolle, Datenformate |
| **Scalability** | Horizontal, Vertikal, Auto-Scaling |

### Organisatorische Drivers

| Kategorie | Beispiel-Driver |
|---|---|
| **Team-Skills** | Erfahrung mit Technologie X, Verfügbarkeit von Experten |
| **Time-to-Market** | Deadline, Sprint-Planung, MVP-Zeitrahmen |
| **Budget** | Lizenzkosten, Infrastrukturkosten, Personalkosten |
| **Vendor** | Lock-in-Risiko, Support-Qualität, Roadmap-Alignment |
| **Compliance** | DSGVO, NIS2, Branchenstandards, Audit-Anforderungen |
| **Organisation** | Conway's Law, Team-Topologies, Verantwortlichkeiten |

### Business Drivers

| Kategorie | Beispiel-Driver |
|---|---|
| **Business Value** | Umsatzpotenzial, Kosteneinsparung, Effizienzgewinn |
| **Risk** | Marktrisiko, Technologierisiko, Regulatorisches Risiko |
| **Strategy** | Digital-Strategie, Cloud-First, Buy-vs-Build |
| **Stakeholder** | Kundenanforderungen, Management-Vorgaben, Partner |

---

## Sensitivitätsanalyse

Bei knappen Ergebnissen in der Entscheidungsmatrix:

1. **Gewichtung variieren**: Was passiert, wenn Driver X wichtiger/unwichtiger wird?
2. **Bewertung hinterfragen**: Sind die Bewertungen belastbar? Basieren sie auf Fakten oder Annahmen?
3. **K.O.-Kriterien identifizieren**: Gibt es einen Driver, bei dem `--` ein Ausschlusskriterium ist?

```markdown
### Sensitivitätsanalyse

**Was wäre wenn...**

| Szenario | Auswirkung auf Ergebnis |
|---|---|
| Performance-Gewicht von 5 auf 3 | Option A: 14, Option B: 14 → Gleichstand |
| Team-Erfahrung von 4 auf 2 | Option A: 16, Option B: 18 → Option B gewinnt |
| Security wird K.O.-Kriterium | Option C scheidet aus (Bewertung: --) |

**Fazit**: Ergebnis ist robust, solange Performance und Team-Erfahrung hoch gewichtet bleiben.
```
