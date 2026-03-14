# NFR-Katalog-Template — Referenz

## Vollständiges Template

```markdown
# NFR-Katalog: [Systemname]

> **Erstellt**: [Datum] | **Version**: [1.0] | **Status**: [Draft | Review | Approved]
> **System**: [Systemname / Projektname]
> **Systemtyp**: [Web-App | API | Mobile | Batch | IoT | ...]
> **Kritikalität**: [Mission-critical | Business-critical | Business-operational | Office]
> **Stakeholder**: [Liste der beteiligten Personen/Rollen]
> **Nächster Review**: [Datum]

---

## Zusammenfassung

### Statistik

| Kategorie | Must | Should | Could | Won't | Gesamt |
|---|---|---|---|---|---|
| Performance Efficiency | | | | | |
| Reliability | | | | | |
| Security | | | | | |
| Scalability | | | | | |
| Maintainability | | | | | |
| Compatibility | | | | | |
| Portability | | | | | |
| Usability | | | | | |
| Functional Suitability | | | | | |
| Compliance | | | | | |
| Operational | | | | | |
| **Gesamt** | | | | | |

### Top-5 Architektur-treibende NFRs

| Rang | NFR-ID | Beschreibung | Architekturimplikation |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |

---

## NFR-Detailkatalog

### [Kategorie]

#### [NFR-ID]: [Titel]

| Feld | Wert |
|---|---|
| **ID** | NFR-{KAT}-{NNN} |
| **Kategorie** | [Hauptkategorie] > [Sub-Charakteristik] |
| **Titel** | [Kurzbeschreibung] |
| **Priorität (Business)** | Must / Should / Could / Won't |
| **Architekturrelevanz** | H / M / L |
| **Stimulus** | [Auslösendes Ereignis] |
| **Stimulus Source** | [Woher kommt der Stimulus] |
| **Environment** | [Unter welchen Bedingungen] |
| **Artifact** | [Betroffene Komponente/Service] |
| **Response** | [Erwartetes Verhalten] |
| **Response Measure** | [Messbare Metrik + Schwellenwert] |
| **Aktueller Stand** | [Baseline / noch nicht gemessen] |
| **Architekturmaßnahme** | [Tactic / Pattern / Technologie] |
| **Trade-off** | [Was kostet diese Maßnahme] |
| **Verifikation** | [Wie wird geprüft: Test, Monitoring, Review] |
| **Verantwortlich** | [Team / Person] |
| **Verwandte NFRs** | [NFR-IDs bei Abhängigkeiten/Konflikten] |
| **ADR-Referenz** | [ADR-ID falls vorhanden] |

---
```

## Kurzform-Template (Tabellarisch)

Für kompakte Darstellung, z.B. in Confluence oder als Übersicht:

```markdown
# NFR-Katalog: [Systemname] (Kompaktform)

| ID | Kategorie | Sub-Char. | Titel | Metrik | Schwellenwert | Prio | Arch | Maßnahme | Verifikation |
|---|---|---|---|---|---|---|---|---|---|
| NFR-PE-001 | Performance | Time Behaviour | API-Antwortzeit | Latenz P95 | ≤ 200ms | Must | H | Redis-Cache | k6 Load-Test |
| NFR-PE-002 | Performance | Throughput | Verarbeitungskapazität | Requests/s | ≥ 1000 | Must | H | Horizontal Scaling | Benchmark |
| NFR-RE-001 | Reliability | Availability | Systemverfügbarkeit | Uptime | ≥ 99.9% | Must | H | Active-Passive Cluster | Monitoring |
| NFR-RE-002 | Reliability | Recoverability | Recovery Time | RTO | ≤ 1h | Must | M | Auto-Failover, Backup | DR-Test |
| NFR-RE-003 | Reliability | Recoverability | Recovery Point | RPO | ≤ 15min | Must | M | WAL-Shipping, Streaming Repl. | Restore-Test |
| NFR-SE-001 | Security | Authenticity | Authentifizierung | Auth-Standard | OIDC + MFA | Must | H | Entra ID / Keycloak | Pen-Test |
| NFR-SE-002 | Security | Confidentiality | Verschlüsselung | Standard | AES-256/TLS 1.3 | Must | M | At rest + in transit | Security Audit |
| NFR-SC-001 | Scalability | Elasticity | Auto-Scaling | Scale-out-Zeit | ≤ 2min | Should | H | K8s HPA | Load-Test |
| NFR-MA-001 | Maintainability | Modifiability | Deployment-Frequenz | Frequenz | ≥ 1x/Woche | Should | M | CI/CD Pipeline | DORA Metrics |
| NFR-CP-001 | Compliance | Datenschutz | DSGVO-Konformität | Compliance | 100% | Must | M | AVV, Löschkonzept | Audit |
```

## NFR-Karten-Template (Workshop-Format)

Für interaktive Workshops, Backlog-Items oder Stakeholder-Reviews:

```markdown
---
### NFR-PE-001: API-Antwortzeit
**Kategorie**: Performance Efficiency > Time Behaviour
**Priorität**: ⚡ Must | Architektur: 🔴 Hoch

**Szenario**:
WENN 500 Benutzer gleichzeitig die REST-API aufrufen (Peak Hour),
DANN antwortet das System in ≤ 200ms (P95),
UND in ≤ 500ms (P99).

**Aktuell**: 350ms (P95) — Baseline aus Last-Test Dezember 2024
**Ziel**: ≤ 200ms (P95) — Verbesserung um 43%

**Maßnahme**: Redis-Cache für häufige Abfragen, Connection Pooling
**Trade-off**: Cache-Invalidierung erhöht Komplexität
**Verifikation**: k6 Load-Test vor jedem Release, Grafana-Dashboard im Betrieb

**Verantwortlich**: Team Backend | **ADR**: — | **Sprint**: Q2/2025
---
```

## Messkriterien-Referenz

### Häufige Metriken nach Kategorie

| Kategorie | Metrik | Einheit | Typische Schwellenwerte |
|---|---|---|---|
| **Performance** | Latenz (P50, P95, P99) | ms | 50 / 200 / 500 ms |
| | Throughput | req/s | 100 – 10.000 |
| | TTFB (Time to First Byte) | ms | ≤ 200ms |
| | Seitenladezeit | s | ≤ 3s |
| **Reliability** | Verfügbarkeit | % pro Jahr | 99% – 99.999% |
| | RTO (Recovery Time Objective) | min/h | 15min – 24h |
| | RPO (Recovery Point Objective) | min/h | 0 – 24h |
| | MTBF (Mean Time Between Failures) | h/Tage | System-abhängig |
| | MTTR (Mean Time To Repair) | min/h | ≤ 1h |
| **Security** | Pen-Test-Ergebnis | Findings | 0 Critical, 0 High |
| | Verschlüsselung | Standard | AES-256, TLS 1.3 |
| | MFA-Abdeckung | % | 100% für Admin/Privileged |
| | Patch-Frequenz | Tage | Critical: ≤ 24h |
| **Scalability** | Max. concurrent Users | Anzahl | System-abhängig |
| | Scale-out-Zeit | min | ≤ 2min |
| | Peak-to-Average-Ratio | Faktor | 3x – 10x |
| **Maintainability** | Deployment-Frequenz | /Woche | ≥ 1x (DORA) |
| | Change Lead Time | h/Tage | ≤ 1 Tag (DORA) |
| | Change Failure Rate | % | ≤ 15% (DORA) |
| | MTTR (für Changes) | h | ≤ 1h (DORA) |
| | Test-Coverage | % | ≥ 80% |
| **Usability** | WCAG-Level | A/AA/AAA | AA (EU Standard) |
| | Onboarding-Zeit | h/Tage | ≤ 1 Tag |
| | Task Completion Rate | % | ≥ 95% |
| **Compliance** | Audit-Log Retention | Monate/Jahre | 6 Monate – 10 Jahre |
| | DSGVO-Konformität | % | 100% |
| | Löschfrist | Tage | ≤ 30 Tage nach Anfrage |
| **Operational** | Alert Response Time | min | ≤ 5min (Critical) |
| | Backup-Frequenz | h | ≤ 1h / ≤ 24h |
| | Restore-Test-Intervall | Monate | ≤ 3 Monate |
| | Log Retention | Tage | 30 – 365 Tage |

### Verifikationsmethoden

| Methode | Wann einsetzen | Tools (Beispiele) |
|---|---|---|
| **Load-Test** | Performance, Scalability | k6, Gatling, JMeter, Locust |
| **Chaos Engineering** | Reliability, Fault Tolerance | Chaos Monkey, Litmus, Gremlin |
| **Penetration Test** | Security | OWASP ZAP, Burp Suite |
| **Security Audit** | Security, Compliance | Qualys, Nessus, Snyk |
| **DR-Test** | Reliability (RTO/RPO) | Manuell / automatisiert |
| **DORA Metrics** | Maintainability | Sleuth, LinearB, Jellyfish |
| **Monitoring / APM** | Alle (laufend) | Grafana, Datadog, Dynatrace |
| **Accessibility Audit** | Usability (WCAG) | axe, Lighthouse, WAVE |
| **Code Review** | Maintainability | SonarQube, CodeClimate |
| **Compliance Audit** | Compliance | Manuell / GRC-Tools |

---

## Versionierung des NFR-Katalogs

```markdown
## Änderungshistorie

| Version | Datum | Autor | Änderung |
|---|---|---|---|
| 1.0 | 2025-01-15 | [Name] | Initiale Erstellung |
| 1.1 | 2025-02-01 | [Name] | NFR-PE-003 hinzugefügt, NFR-RE-001 Schwellenwert angepasst |
| 2.0 | 2025-04-01 | [Name] | Compliance-Kategorie erweitert (NIS2), Review nach Architektur-Workshop |
```

## Statusmodell für NFR-Katalog

```
  ┌────────┐
  │ Draft  │ ← Initiale Erstellung
  └───┬────┘
      │ Review durch Stakeholder
      ▼
  ┌────────┐
  │ Review │ ← Feedback einarbeiten
  └───┬────┘
      │ Freigabe durch Architecture Board / PO
      ▼
  ┌──────────┐
  │ Approved │ ← Verbindlich für das Projekt
  └───┬──────┘
      │ Änderung nötig (neue Anforderung, geänderte Rahmenbedingungen)
      ▼
  ┌──────────┐
  │ Updated  │ → Zurück zu Review
  └──────────┘
```
