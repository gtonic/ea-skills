# Architektur-Tactics pro Qualitätsattribut — Referenz

> Architektur-Tactics sind bewährte Design-Entscheidungen, die gezielt ein bestimmtes
> Qualitätsattribut adressieren. Diese Referenz ordnet jedem NFR-Bereich konkrete
> Maßnahmen zu, inklusive Trade-offs.

## Performance Efficiency — Tactics

### Time Behaviour (Latenz reduzieren)

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Caching** | Häufige Abfragen im Cache halten (Redis, Memcached, CDN) | Hohe Read-Last, wiederholte Queries | Cache-Invalidierung, Stale Data |
| **Connection Pooling** | DB-/HTTP-Connections wiederverwenden | Viele kurzlebige Verbindungen | Pool-Erschöpfung bei Last, Konfigurationskomplexität |
| **Async Processing** | Aufwendige Operationen asynchron ausführen (Queue, Events) | Langlebige Operationen im Request-Pfad | Eventual Consistency, Fehlerbehandlung |
| **CDN** | Statische Assets nah am User ausliefern | Globale Benutzer, statische Inhalte | Kosten, Cache-Purging |
| **Read Replica** | Lesezugriffe auf Replikat-Datenbanken verteilen | Read-heavy Workloads | Replikation-Lag, Eventual Consistency |
| **Denormalisierung** | Daten für Leseoptimierung vorberechnen | Komplexe JOINs, häufige Aggregationen | Schreib-Performance, Datenredundanz |
| **Indexing** | Datenbank-Indizes optimieren | Langsame Queries | Write-Performance, Speicherverbrauch |

### Throughput (Durchsatz erhöhen)

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Horizontal Scaling** | Mehr Instanzen hinzufügen | Last übersteigt Single-Node-Kapazität | Koordinationsaufwand, State-Management |
| **Batch Processing** | Mehrere Operationen bündeln | Hohe Transaktionsvolumina | Latenz für Einzeloperationen |
| **Message Queue** | Lastspitzen über Queue abfedern | Burst-Traffic, Entkopplung | Latenz, Komplexität (Dead Letter Queue) |
| **Parallelisierung** | Aufgaben parallel ausführen | CPU-intensive Berechnungen | Thread-Safety, Debugging-Komplexität |
| **Rate Limiting** | Kontrolle der Anfragerate | Überlastschutz, Fair Use | Verlorene Requests bei Überschreitung |

### Resource Utilization (Ressourcen optimieren)

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Autoscaling** | Ressourcen automatisch anpassen | Variable Last | Cold-Start-Latenz, Kosten bei Fehlkonfiguration |
| **Serverless / FaaS** | Nur bei Bedarf ausführen | Sporadische Workloads | Cold Start, Vendor Lock-in |
| **Kompression** | Daten komprimieren (gzip, Brotli) | Hoher Netzwerk-Traffic | CPU-Overhead |
| **Lazy Loading** | Ressourcen erst bei Bedarf laden | Große Datenmengen, UI-initialer Load | Latenz beim Nachladen |

---

## Reliability — Tactics

### Availability (Verfügbarkeit erhöhen)

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Active-Active Cluster** | Mehrere aktive Instanzen in verschiedenen Zonen | ≥ 99.99% Verfügbarkeit | Hohe Kosten, Daten-Synchronisation |
| **Active-Passive Cluster** | Standby-Instanz für Failover | ≥ 99.9% Verfügbarkeit | Failover-Zeit, Ressourcen-Verschwendung |
| **Health Checks** | Regelmäßige Zustandsprüfung | Automatische Fehlererkennung | False Positives, Netzwerk-Overhead |
| **Load Balancer** | Traffic auf gesunde Instanzen verteilen | Mehrere Instanzen | Single Point of Failure (LB selbst) |
| **Rolling Deployment** | Schrittweises Update ohne Downtime | Zero-Downtime-Deployments | Langsamere Rollouts |
| **Blue-Green Deployment** | Parallele Umgebungen, sofortiger Switch | Schnelles Rollback nötig | Doppelte Infrastrukturkosten |

### Fault Tolerance (Fehlertoleranz)

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Circuit Breaker** | Fehlerhafte Aufrufe unterbrechen | Service-zu-Service-Kommunikation | Teilweiser Funktionsverlust |
| **Retry with Backoff** | Fehlgeschlagene Requests wiederholen | Transiente Fehler | Erhöhte Last bei Retry-Storm |
| **Bulkhead** | Ressourcen pro Service isolieren | Kaskadierenden Ausfall verhindern | Ressourcen-Fragmentierung |
| **Graceful Degradation** | Reduzierter Funktionsumfang statt Totalausfall | Nicht-kritische Features | UX-Verschlechterung |
| **Fallback** | Alternative Datenquelle / Default-Werte | Wenn primäre Quelle nicht verfügbar | Möglicherweise veraltete Daten |
| **Timeout** | Maximale Wartezeit für externe Aufrufe | Alle externen abhängigkeiten | Zu aggressive Timeouts → false fails |

### Recoverability (Wiederherstellbarkeit)

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Automated Failover** | Automatischer Umschaltung auf Standby | Kurze RTO (< 15min) | Komplexe Konfiguration, Split-Brain-Risiko |
| **Point-in-Time Recovery** | Datenbank auf Zeitpunkt zurücksetzen | Korruption, versehentliche Löschung | Speicher für WAL/Logs |
| **Backup / Restore** | Regelmäßige Datensicherung | Disaster Recovery | RPO-Lücke (Zeit seit letztem Backup) |
| **Immutable Infrastructure** | Infrastruktur wird neu erstellt, nie gepatcht | Schnelle Wiederherstellung | Build-Zeit, Image-Management |
| **Multi-Region** | Deployment in mehreren Regionen | Regionsweiter Ausfall | Daten-Replikation, Latenz, Kosten |

---

## Security — Tactics

### Authentication & Authorization

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **OIDC / OAuth2** | Token-basierte Authentifizierung | Web-Apps, APIs, SSO | Implementierungskomplexität |
| **MFA** | Multi-Faktor-Authentifizierung | Admin, Privileged Access, Compliance | User Experience |
| **RBAC / ABAC** | Rollen-/Attribut-basierte Autorisierung | Feingranulare Zugriffssteuerung | Konfigurationsaufwand |
| **API Gateway** | Zentrale Auth-Prüfung | Microservices | Single Point of Failure, Latenz |
| **Zero Trust** | Jeder Request wird verifiziert | Cloud-native, Remote Work | Komplexität, Performance |

### Data Protection

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Encryption at Rest** | Daten auf Speicher verschlüsseln (AES-256) | Personenbezogene/sensible Daten | Performance-Overhead (~5%) |
| **Encryption in Transit** | TLS 1.3 für alle Verbindungen | Alle externen Kommunikation | Certificate Management |
| **Data Masking** | Sensible Daten in Nicht-Prod maskieren | Testumgebungen, Logs | Datenqualität in Tests |
| **Tokenization** | Sensible Daten durch Token ersetzen | PCI-DSS, Kartennummern | Mapping-Management |
| **Key Management** | Zentrale Schlüsselverwaltung (HSM, KMS) | Verschlüsselung, Signierung | Kosten, Verfügbarkeit des KMS |

### Audit & Monitoring

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Audit-Logging** | Alle sicherheitsrelevanten Events loggen | Compliance, Forensik | Speicher, Performance |
| **SIEM-Integration** | Logs an Security-Monitoring senden | SOC, Echtzeit-Erkennung | Kosten, False Positives |
| **Intrusion Detection** | Anomale Zugriffsmuster erkennen | Externe Angriffe | False Positives, Tuning-Aufwand |
| **Vulnerability Scanning** | Regelmäßig auf Schwachstellen prüfen | Alle Systeme | Fix-Aufwand, Downtime bei Patches |

---

## Scalability — Tactics

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Horizontal Scaling** | Mehr Instanzen hinzufügen | Stateless Services, Read-heavy | Session-Management, Data Partitioning |
| **Database Sharding** | Daten auf mehrere DB-Instanzen verteilen | Große Datenmengen, hoher Write-Throughput | Query-Komplexität, Rebalancing |
| **CQRS** | Lese-/Schreib-Modell trennen | Unterschiedliche Lese-/Schreib-Muster | Eventual Consistency, Komplexität |
| **Event Sourcing** | Alle Änderungen als Events speichern | Audit, temporal Queries | Speicher, Replay-Komplexität |
| **Microservices** | System in unabhängige Services aufteilen | Unabhängige Skalierung pro Funktion | Distributed-System-Komplexität |
| **CDN / Edge Computing** | Berechnung/Auslieferung am Edge | Globale Nutzer, Latenz-sensitiv | Konsistenz, Debugging |
| **Data Partitioning** | Daten logisch/physisch partitionieren | Große Tabellen, Multi-Tenant | Cross-Partition-Queries |

---

## Maintainability — Tactics

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Hexagonal Architecture** | Ports & Adapters, Kern-Logik isoliert | Testbarkeit, Austauschbarkeit | Mehr Boilerplate, Lernkurve |
| **CI/CD Pipeline** | Automatisierte Build-Test-Deploy-Kette | Jedes Projekt | Initiale Setup-Zeit |
| **Feature Flags** | Features im Code ein-/ausschalten | Canary Releases, A/B-Tests | Flag-Hygiene, technische Schuld |
| **Semantic Versioning** | Klare Versionierung der API | Öffentliche APIs, Libraries | Disziplin, Kommunikation |
| **Structured Logging** | JSON-Logs mit Kontext | Fehlerbehebung, Observability | Log-Volumen |
| **OpenTelemetry** | Standardisierte Traces, Metrics, Logs | Microservices, Distributed Systems | Performance-Overhead (~2%) |
| **Infrastructure as Code** | Infrastruktur deklarativ verwalten | Cloud, Reproduzierbarkeit | Lernkurve (Terraform, Bicep, Pulumi) |
| **API Versioning** | API-Versionen parallel betreiben | Backward Compatibility | Wartung mehrerer Versionen |

---

## Compatibility — Tactics

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **API Gateway** | Zentrale Schnittstelle für Konsumenten | Viele Konsumenten, API-Evolution | Single Point of Failure, Latenz |
| **Schema Registry** | Zentrale Schema-Verwaltung (Avro, Protobuf) | Event-Driven, Messaging | Tooling-Abhängigkeit |
| **Anti-Corruption Layer** | Adapter zwischen altem und neuem System | Legacy-Integration | Implementierungsaufwand |
| **API Versioning** | /v1/, /v2/ parallel betreiben | API-Evolution ohne Breaking Changes | Wartungsaufwand |
| **Contract Testing** | Consumer-driven Contract Tests | Microservices, API-Integrationen | Test-Overhead |

---

## Portability — Tactics

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Containerisierung** | Docker-Container für Portabilität | Multi-Env, Multi-Cloud | Orchestrierung (K8s) nötig |
| **12-Factor App** | Cloud-native Design-Prinzipien | Neue Cloud-Anwendungen | Konformität erfordert Disziplin |
| **Abstraction Layer** | Cloud-spezifische Services abstrahieren | Multi-Cloud-Strategie | Nicht alle Features nutzbar |
| **Standard-Protokolle** | HTTP, gRPC, AMQP statt proprietärer Protokolle | Interoperabilität | Nicht immer performanteste Wahl |
| **IaC mit Abstraction** | Terraform (Multi-Cloud) statt Bicep/CDK | Multi-Cloud | Weniger Provider-spezifische Features |

---

## Compliance — Tactics

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Data Residency** | Daten in bestimmter Region halten | DSGVO, Datensouveränität | Performance (Latenz), Kosten |
| **Data Classification** | Daten nach Schutzbedarf klassifizieren | DSGVO, ISO 27001 | Initialer Aufwand |
| **Consent Management** | Einwilligungen verwalten | DSGVO, ePrivacy | UX-Overhead |
| **Audit Trail** | Revisionssichere Protokollierung | Finanz, Gesundheit, Behörden | Speicher, Performance |
| **Löschkonzept** | Automatische Datenlöschung nach Frist | DSGVO Art. 17 | Komplexität bei verteilten Daten |
| **Privacy by Design** | Datenschutz von Anfang an einbauen | Alle neuen Systeme | Höherer initialer Aufwand |
| **SBOM** | Software Bill of Materials | Supply Chain Security, NIS2 | Tooling, Pflege |

---

## Operational — Tactics

| Tactic | Beschreibung | Wann einsetzen | Trade-off |
|---|---|---|---|
| **Observability Stack** | Metrics + Logs + Traces integriert | Microservices, Cloud-native | Tool-Kosten, Datenvolumen |
| **Alerting mit Eskalation** | Schwellenwert-basierte Benachrichtigung | Alle produktiven Systeme | Alert Fatigue bei Fehlkonfiguration |
| **Runbook Automation** | Automatisierte Incident-Response | Wiederkehrende Incidents | Initiale Entwicklung |
| **GitOps** | Infrastruktur-Änderungen über Git | K8s-Umgebungen | Lernkurve |
| **Canary Deployment** | Neue Version schrittweise ausrollen | Risikominimierung bei Deployments | Monitoring-Infrastruktur nötig |
| **Database Migration Tool** | Schema-Änderungen versioniert (Flyway, Liquibase) | Alle DB-Anwendungen | CI/CD-Integration |
| **Secret Management** | Secrets in Vault/KMS verwalten | Alle produktiven Systeme | Verfügbarkeit des Vault |

---

## NFR → Tactic-Mapping (Schnellreferenz)

| NFR-Anforderung | Primäre Tactics | Sekundäre Tactics |
|---|---|---|
| Latenz ≤ 200ms | Caching, CDN, Read Replica | Connection Pooling, Indexing |
| Throughput ≥ 1000 rps | Horizontal Scaling, Async | Rate Limiting, Batch Processing |
| Verfügbarkeit ≥ 99.9% | Active-Passive, Health Checks | Circuit Breaker, Graceful Degradation |
| Verfügbarkeit ≥ 99.99% | Active-Active, Multi-Region | Blue-Green, Chaos Engineering |
| RTO ≤ 15min | Automated Failover, Multi-Region | Immutable Infra, IaC |
| RPO ≤ 1min | Streaming Replication, WAL | Multi-Region Write |
| DSGVO-Konformität | Encryption, Löschkonzept, Consent | Data Classification, Audit Trail |
| NIS2-Konformität | SBOM, Incident Response, Audit | Vulnerability Scanning, MFA |
| Horizontal Skalierung | Stateless Design, Container, K8s | CQRS, Sharding |
| Unabhängig deploybar | Microservices, CI/CD | API Versioning, Contract Testing |
| Multi-Cloud | Container, Abstraction Layer, IaC | Standard-Protokolle, 12-Factor |
| WCAG AA | Semantic HTML, ARIA, Color Contrast | Accessibility Audit, Keyboard Navigation |
