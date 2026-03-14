# ISO 25010 Qualitätsmodell — Referenz

> Basierend auf ISO/IEC 25010:2023 (Product Quality Model) ergänzt um
> TOGAF-spezifische Qualitätsattribute und praxisrelevante Erweiterungen.

## Qualitätsattribute und Sub-Charakteristiken

### 1. Performance Efficiency (Leistungseffizienz)

Leistung relativ zu den eingesetzten Ressourcen unter festgelegten Bedingungen.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Time Behaviour** | Antwort- und Verarbeitungszeiten | Latenz (P50, P95, P99), TTFB, Seitenladezeit | „Welche Antwortzeit ist für den User akzeptabel?" |
| **Throughput** | Verarbeitungskapazität pro Zeiteinheit | Requests/s, Transaktionen/min, Messages/s | „Wie viele Transaktionen pro Sekunde werden erwartet?" |
| **Resource Utilization** | Ressourcenverbrauch | CPU%, Memory%, Disk I/O, Netzwerk-Bandbreite | „Gibt es Budgetlimits für Infrastruktur?" |
| **Capacity** | Maximale Grenzwerte | Max. Datenmenge, Max. User, Max. Connections | „Wie viele Daten/User muss das System maximal handhaben?" |

**Szenario-Vorlage:**

```
WENN [Anzahl] Benutzer gleichzeitig [Aktion] ausführen (unter [Bedingung]),
DANN antwortet das System in ≤ [Latenz] (P[Percentile])
UND verarbeitet ≥ [Throughput] Requests/s
BEI einem Ressourcenverbrauch von ≤ [CPU]% CPU, ≤ [RAM] GB RAM.
```

---

### 2. Reliability (Zuverlässigkeit)

Fähigkeit, die geforderten Funktionen unter festgelegten Bedingungen für einen bestimmten Zeitraum zu erfüllen.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Availability** | Betriebsbereitschaft | Uptime %, SLA-Level, geplante Wartungsfenster | „Welches Verfügbarkeits-SLA wird benötigt?" |
| **Fault Tolerance** | Betrieb trotz Fehler | Fehlerrate, Degradation-Verhalten | „Was soll passieren, wenn eine Komponente ausfällt?" |
| **Recoverability** | Wiederherstellung nach Ausfall | RTO, RPO, MTTR | „Wie schnell muss das System nach einem Ausfall wieder laufen?" |
| **Maturity** | Stabilität über Zeit | MTBF, Fehlerrate pro Release | „Wie stabil muss das System über Monate sein?" |

**Verfügbarkeits-Referenztabelle:**

| SLA | Downtime/Jahr | Downtime/Monat | Downtime/Woche | Typischer Einsatz |
|---|---|---|---|---|
| 99% | 3.65 Tage | 7.31h | 1.68h | Interne Tools |
| 99.5% | 1.83 Tage | 3.65h | 50.4min | Business-Applikationen |
| 99.9% | 8.77h | 43.8min | 10.1min | E-Commerce, SaaS |
| 99.95% | 4.38h | 21.9min | 5.04min | Finanzplattformen |
| 99.99% | 52.6min | 4.38min | 1.01min | Kritische Infrastruktur |
| 99.999% | 5.26min | 26.3s | 6.05s | Telekommunikation, Medizin |

**Szenario-Vorlage:**

```
WENN [Ausfallszenario] eintritt (z.B. DB-Node fällt aus),
DANN erkennt das System den Fehler in ≤ [Detection-Time],
SCHALTET auf Failover um in ≤ [Failover-Time],
UND stellt den Normalbetrieb wieder her in ≤ [Recovery-Time] (RTO)
MIT maximalem Datenverlust von ≤ [RPO].
```

---

### 3. Security (Sicherheit)

Schutz von Informationen und Daten vor unbefugtem Zugriff und Manipulation.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Confidentiality** | Schutz vor unbefugtem Zugriff | Verschlüsselungsstandard, Zugriffskontrollen | „Welche Daten sind vertraulich / besonders schützenswert?" |
| **Integrity** | Schutz vor Manipulation | Checksummen, Signierung, Tamper Detection | „Muss die Integrität von Daten kryptographisch überprüfbar sein?" |
| **Non-repudiation** | Nachweisbarkeit von Aktionen | Audit-Logs, digitale Signaturen | „Müssen Aktionen gerichtsfest nachweisbar sein?" |
| **Accountability** | Zuordnung zu Akteuren | Identity Management, Audit-Trail | „Wer darf was? Wie wird nachverfolgt?" |
| **Authenticity** | Prüfung der Identität | AuthN-Standard (OIDC, SAML, MFA) | „Welcher Auth-Mechanismus? MFA erforderlich?" |

**Szenario-Vorlage:**

```
WENN ein [Angreifer/Benutzer] versucht [Angriff/Zugriff],
DANN [verhindert/erkennt/protokolliert] das System dies
INNERHALB von [Zeitrahmen]
UND benachrichtigt [Rolle/System].
```

---

### 4. Scalability (Skalierbarkeit) — TOGAF-Erweiterung

Fähigkeit, mit wachsender Last umzugehen.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Horizontal Scaling** | Mehr Instanzen hinzufügen | Max. Instanzen, Scale-out-Zeit | „Muss das System horizontal skalieren können?" |
| **Vertical Scaling** | Mehr Ressourcen pro Instanz | Max. CPU/RAM pro Instanz | „Reicht vertikale Skalierung aus?" |
| **Elasticity** | Automatische Anpassung an Last | Auto-Scale-Trigger, Scale-in/out-Zeit | „Soll das System automatisch skalieren?" |
| **Load Handling** | Verhalten unter Spitzenlast | Peak-to-Average-Ratio, Burst-Kapazität | „Wie sehen typische Lastspitzen aus? Saisonale Muster?" |
| **Data Scalability** | Wachstum der Datenmenge | Wachstumsrate, Partitionierungsstrategie | „Wie schnell wächst die Datenmenge? Plan für 1/3/5 Jahre?" |

**Szenario-Vorlage:**

```
WENN die Last von [Normal] auf [Peak] steigt (Faktor [X]),
DANN skaliert das System in ≤ [Zeit] automatisch,
UND hält die Performance-SLAs ein (Latenz ≤ [Wert])
BEI Kosten von maximal [Faktor Y] × Normalkosten.
```

---

### 5. Maintainability (Wartbarkeit)

Aufwand für Änderungen, Fehlerbehebung und Weiterentwicklung.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Modularity** | Unabhängigkeit der Komponenten | Kopplung, Kohäsion, Service-Grenzen | „Müssen Komponenten unabhängig deploybar sein?" |
| **Reusability** | Wiederverwendbarkeit | Shared Libraries, API-Standardisierung | „Gibt es Shared Components / Libraries?" |
| **Analysability** | Verständlichkeit des Systems | Code-Dokumentation, Observability | „Wie schnell muss ein neuer Entwickler produktiv sein?" |
| **Modifiability** | Änderbarkeit | Change Lead Time, Deployment-Frequenz | „Wie oft wird deployed? CI/CD vorhanden?" |
| **Testability** | Testbarkeit | Test-Coverage, Test-Pyramide | „Welche Test-Arten sind gefordert? Coverage-Ziel?" |

**Szenario-Vorlage:**

```
WENN ein Entwickler [eine typische Änderung] durchführen muss,
DANN ist die Änderung in ≤ [Zeit] implementiert, getestet und deployed,
OHNE andere Komponenten zu beeinflussen,
MIT einer Test-Abdeckung von ≥ [Coverage]%.
```

---

### 6. Compatibility (Kompatibilität)

Fähigkeit, mit anderen Systemen zusammenzuarbeiten und koexistieren.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Interoperability** | Datenaustausch mit anderen Systemen | API-Standards, Datenformate, Protokolle | „Mit welchen Systemen muss integriert werden?" |
| **Co-existence** | Parallelbetrieb ohne Beeinträchtigung | Shared Resources, Isolation | „Läuft das System neben anderen auf gleicher Infrastruktur?" |
| **Backward Compatibility** | Kompatibilität mit älteren Versionen | API-Versioning, Schema-Evolution | „Müssen alte API-Versionen weiter unterstützt werden?" |

---

### 7. Portability (Portierbarkeit)

Fähigkeit, in unterschiedlichen Umgebungen eingesetzt zu werden.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Adaptability** | Anpassung an neue Umgebungen | Konfigurierbarkeit, Environment-Abstraction | „Muss das System in verschiedenen Umgebungen laufen?" |
| **Installability** | Aufwand für Installation | Setup-Zeit, Automatisierungsgrad | „Wie wird deployed? IaC vorhanden?" |
| **Replaceability** | Austauschbarkeit | Vendor Lock-in, Standard-Schnittstellen | „Muss ein Cloud-Provider-Wechsel möglich sein?" |

---

### 8. Usability (Gebrauchstauglichkeit)

Effektivität, Effizienz und Zufriedenheit der Benutzer.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Learnability** | Erlernbarkeit | Onboarding-Zeit, Schulungsaufwand | „Wie schnell muss ein neuer User produktiv sein?" |
| **Operability** | Bedienbarkeit | Task Completion Rate, Error Rate | „Wie komplex sind die typischen Workflows?" |
| **Error Protection** | Fehlervermeidung/Recovery (UX) | Undo-Fähigkeit, Validierung | „Wie kritisch sind Fehleingaben?" |
| **Accessibility** | Barrierefreiheit | WCAG-Level (A, AA, AAA) | „Muss WCAG 2.1 AA erfüllt werden? (EU Accessibility Act!)" |
| **User Interface Aesthetics** | Ästhetik | UI/UX Guidelines, Design System | „Gibt es ein Corporate Design System?" |

---

### 9. Functional Suitability (Funktionale Eignung)

Grad der Abdeckung der funktionalen Anforderungen.

| Sub-Charakteristik | Beschreibung | Typische Metriken | Fragen an Stakeholder |
|---|---|---|---|
| **Functional Completeness** | Vollständigkeit | Feature Coverage | „Welche Funktionen sind Must-have für MVP?" |
| **Functional Correctness** | Korrektheit | Bug-Rate, Acceptance-Test-Pass-Rate | „Wie werden korrekte Ergebnisse sichergestellt?" |
| **Functional Appropriateness** | Angemessenheit | Task-Success-Rate | „Unterstützt die Lösung die Workflows effizient?" |

---

### 10. Compliance (Cross-cutting)

Einhaltung von Gesetzen, Standards und organisatorischen Richtlinien.

| Bereich | Typische Anforderungen | Fragen an Stakeholder |
|---|---|---|
| **Datenschutz** | DSGVO, CCPA, Löschkonzept, AVV | „Werden personenbezogene Daten verarbeitet?" |
| **Regulatorik** | NIS2, PCI-DSS, HIPAA, MaRisk | „Welche branchenspezifischen Regulierungen gelten?" |
| **Standards** | ISO 27001, SOC 2, BSI Grundschutz | „Welche Zertifizierungen werden gefordert?" |
| **Audit** | Audit-Trail, Log-Retention, Revisionssicherheit | „Muss das System auditierbar sein? Aufbewahrungsfristen?" |
| **Barrierefreiheit** | EU Accessibility Act, WCAG 2.1 AA | „Fällt das System unter den EU Accessibility Act?" |

---

### 11. Operational (Cross-cutting) — TOGAF-Erweiterung

Anforderungen an Betrieb, Monitoring und Deployment.

| Bereich | Typische Anforderungen | Fragen an Stakeholder |
|---|---|---|
| **Monitoring / Observability** | Metrics, Logs, Traces, Dashboards | „Was muss überwacht werden? Welches Tool-Stack?" |
| **Alerting** | Schwellenwerte, Eskalation, On-Call | „Wer wird bei Problemen benachrichtigt? 24/7?" |
| **Deployment** | CI/CD, Blue-Green, Canary, Rollback | „Wie wird deployed? Rollback-Strategie?" |
| **Backup / Restore** | Backup-Frequenz, Retention, Restore-Test | „Wie oft Backup? Wurde Restore jemals getestet?" |
| **Logging** | Structured Logging, Retention, SIEM | „Welche Events müssen geloggt werden? Wie lange aufbewahren?" |
| **Configuration** | Config-Management, Secrets, Feature Flags | „Wie werden Konfigurationen und Secrets verwaltet?" |
| **Disaster Recovery** | DR-Plan, Failover-Region, DR-Test | „Gibt es einen DR-Plan? Wie oft wird getestet?" |

---

## ISO 25010 Qualitätsmodell — Übersichtsgrafik

```
                          ┌──────────────────────┐
                          │    System/Software    │
                          │    Produktqualität    │
                          │     (ISO 25010)       │
                          └──────────┬───────────┘
                                     │
    ┌──────────┬──────────┬──────────┼──────────┬──────────┬──────────┬──────────┬──────────┐
    │          │          │          │          │          │          │          │          │
    ▼          ▼          ▼          ▼          ▼          ▼          ▼          ▼          ▼
┌────────┐┌────────┐┌────────┐┌────────┐┌────────┐┌────────┐┌────────┐┌────────┐┌────────┐
│Perfor- ││Relia-  ││Secu-   ││Scala-  ││Maintain││Compat- ││Porta-  ││Usa-    ││Func.   │
│mance   ││bility  ││rity    ││bility  ││ability ││ibility ││bility  ││bility  ││Suit-   │
│Effic.  ││        ││        ││(TOGAF) ││        ││        ││        ││        ││ability │
└───┬────┘└───┬────┘└───┬────┘└───┬────┘└───┬────┘└───┬────┘└───┬────┘└───┬────┘└───┬────┘
    │         │         │         │         │         │         │         │         │
  Time      Avail-   Confid-   Horiz.    Modul-   Interop.  Adapt-   Learn-   Complete-
  Behav.    ability  entiality Scaling   arity              ability  ability  ness
  Through-  Fault    Integrity Vertical  Reusa-   Co-exist. Install- Operab.  Correct-
  put       Toler.   Non-Rep.  Elastic.  bility             ability  Access.  ness
  Resource  Recover. Account.  Load      Analys.  Backward  Replace- Error    Approp.
  Util.     Maturity Authent.  Data Sc.  Modif.   Compat.   ability  Protect.
  Capacity                               Testab.                     Aesthet.

  + Cross-cutting: Compliance (DSGVO, NIS2, ...) | Operational (Monitoring, Deployment, DR)
```
