# On-Premises-Kriterienkatalog

Spezifische Bewertungskriterien für On-Premises- und selbst betriebene Softwarelösungen.

## 1. Frontend-Technologie

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O01 | **UI-Framework** | ●● | Welches Framework (React, Angular, Vue, Blazor, Vaadin, Thymeleaf)? Version? |
| O02 | **Browser-Support** | ●● | Welche Browser und Versionen? Chromium-only? Mobile-Support? |
| O03 | **Client-Typ** | ●● | Web (SPA/MPA), Desktop (Electron, WPF, WinForms), Mobile Native? |
| O04 | **Progressive Web App** | ● | PWA-fähig? Offline-Fähigkeit? |
| O05 | **Barrierefreiheit** | ●● | WCAG 2.1 AA? Keyboard-Navigation? Screen Reader? EAA-Konformität? |
| O06 | **Lokalisierung** | ● | Mehrsprachigkeit? Deutsch vorhanden? RTL-Support? |

### Scoring-Guide

| Score | Frontend |
|---|---|
| 0 | Veraltetes Framework (End-of-Life), kein Webzugang, nur proprietärer Client |
| 1 | Web-UI vorhanden, aber veraltetes Framework, eingeschränkter Browser-Support |
| 2 | Modernes Web-Framework, aktuelle Browser unterstützt, responsive |
| 3 | Modernes Framework (aktuelle LTS), PWA, Accessibility, Mobile-optimiert |

---

## 2. Backend-Technologie

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O07 | **Sprache / Framework** | ●●● | Java/Spring, .NET, Node.js, Go, Python/Django? Version? LTS? |
| O08 | **Architekturstil** | ●● | Monolith, Modular Monolith, Microservices, Event-Driven? |
| O09 | **API-Layer** | ●●● | REST, GraphQL, gRPC, SOAP? OpenAPI-Spec vorhanden? |
| O10 | **Messaging** | ●● | Message Broker benötigt? RabbitMQ, Kafka, ActiveMQ? |
| O11 | **Caching** | ● | Redis, Memcached, Hazelcast? Für welche Anwendungsfälle? |
| O12 | **Background Processing** | ● | Job-Scheduler integriert? Externe Abhängigkeit (Quartz, Hangfire)? |
| O13 | **Konfigurationsmanagement** | ●● | Environment-Variablen, Config-Dateien, Vault-Integration? Secrets-Handling? |

### Scoring-Guide

| Score | Backend |
|---|---|
| 0 | End-of-Life Framework/Sprache, keine API, proprietäres Protokoll |
| 1 | Aktive Sprache, aber älteres Framework, eingeschränkte API |
| 2 | Aktuelles LTS-Framework, REST-API, Standard-Architektur |
| 3 | Aktuelles Framework, saubere API, modulare Architektur, gut dokumentiert |

---

## 3. Datenbank-Support

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O14 | **Unterstützte RDBMS** | ●●● | PostgreSQL, SQL Server, Oracle, MySQL/MariaDB? Versionen? |
| O15 | **NoSQL-Support** | ● | MongoDB, Redis, Elasticsearch als Datenspeicher? |
| O16 | **Schema-Management** | ●● | Flyway, Liquibase, EF Migrations? Automatisch oder manuell? |
| O17 | **HA-Fähigkeit** | ●●● | Clustering, Replikation, Always-On, Patroni? Failover automatisch? |
| O18 | **Backup-Strategie** | ●●● | Point-in-Time-Recovery? Backup-Empfehlungen? Konsistenzprüfung? |
| O19 | **Datenbankgröße** | ●● | Erwartete Größe nach 1/3/5 Jahren? Wachstumsprognose? Archivierung? |
| O20 | **Verschlüsselung** | ●●● | TDE (Transparent Data Encryption)? Column-Level Encryption? |

### Scoring-Guide

| Score | Datenbank |
|---|---|
| 0 | Nur proprietäre DB, kein HA-Support, keine Verschlüsselung |
| 1 | Unterstützt gängige DB, aber kein HA, manuelle Migrationen |
| 2 | PostgreSQL/SQL Server unterstützt, HA-fähig, automatische Migrationen |
| 3 | Multi-DB-Support, HA out-of-the-box, TDE, dokumentiertes Schema-Management |

---

## 4. Runtime-Umgebung

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O21 | **Deployment-Varianten** | ●●● | VM, Container (Docker), Kubernetes, Bare-Metal? Was ist empfohlen? |
| O22 | **Container-Support** | ●●● | Offizielle Docker-Images? Dockerfile mitgeliefert? OCI-kompatibel? |
| O23 | **Kubernetes-Support** | ●● | Helm Charts? Operator? StatefulSet-fähig? liveness/readiness Probes? |
| O24 | **Betriebssystem** | ●● | Linux-Distros (RHEL, Ubuntu, Debian, Alpine)? Windows Server? Versionen? |
| O25 | **Runtime-Abhängigkeiten** | ●● | JRE/JDK, .NET Runtime, Node.js Version? Kompatibilitätsmatrix? |
| O26 | **Infrastructure-as-Code** | ● | Terraform-Module, ARM/Bicep-Templates, Ansible-Playbook mitgeliefert? |

### Scoring-Guide

| Score | Runtime |
|---|---|
| 0 | Nur Bare-Metal, spezifisches OS, nicht containerisierbar |
| 1 | VM-Deployment möglich, Container experimentell |
| 2 | Docker-Images offiziell, Kubernetes-Support, gängige OS-Versionen |
| 3 | Container-native, Helm Charts, Operator, IaC-Templates, Multi-Arch (amd64/arm64) |

---

## 5. Systemanforderungen & Sizing

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O27 | **Minimale Hardware** | ●● | CPU, RAM, Storage für Einstieg? |
| O28 | **Sizing-Empfehlung** | ●● | Sizing-Guide pro Nutzeranzahl? (z.B. S/M/L/XL) |
| O29 | **Netzwerk-Anforderungen** | ●● | Benötigte Ports, Protokolle, Bandbreite? Firewall-Regeln dokumentiert? |
| O30 | **Storage-Anforderungen** | ●● | Lokal, SAN, NAS, S3-kompatibel? IOPS-Anforderungen? |
| O31 | **Externe Abhängigkeiten** | ●●● | Internet-Zugang benötigt (Lizenzserver, Telemetrie, Updates)? Air-Gap-fähig? |

### Scoring-Guide

| Score | Sizing |
|---|---|
| 0 | Keine Sizing-Dokumentation, unverhältnismäßige Anforderungen |
| 1 | Grobe Angaben, keine Sizing-Tabelle, fehlende Netzwerk-Doku |
| 2 | Sizing-Guide vorhanden, Netzwerk dokumentiert, gängige Storage-Optionen |
| 3 | Detaillierte Sizing-Tabelle, Capacity Planning Tool, Air-Gap-fähig |

---

## 6. Deployment & Skalierung

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O32 | **Deployment-Modell** | ●●● | Single-Node, Clustered, HA, Active-Active, Multi-Site? |
| O33 | **Horizontale Skalierung** | ●● | Scale-out möglich? Stateless-Komponenten? Shared-Nothing? |
| O34 | **Vertikale Skalierung** | ●● | Scale-up-Grenzen? Ab wann wird horizontal nötig? |
| O35 | **Load Balancing** | ●● | Integriert oder extern? Session Affinity benötigt? Health Checks? |
| O36 | **Zero-Downtime Deployment** | ●● | Rolling Update? Blue-Green? Canary? Oder Downtime nötig? |
| O37 | **Rollback** | ●●● | Rollback-Strategie dokumentiert? Automatisch oder manuell? Datenbank-Rollback? |

### Scoring-Guide

| Score | Deployment |
|---|---|
| 0 | Nur Single-Node, kein HA, Downtime bei Updates |
| 1 | HA möglich mit manuellem Setup, Downtime bei Updates |
| 2 | Clustered/HA out-of-the-box, Rolling Updates möglich, Rollback dokumentiert |
| 3 | Active-Active, Zero-Downtime, Auto-Scaling, automatischer Rollback |

---

## 7. Monitoring & Observability

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O38 | **Health Checks** | ●●● | HTTP Health/Readiness Endpoints? Detaillierte Checks (DB, Queue, Disk)? |
| O39 | **Metriken** | ●● | Prometheus/OpenTelemetry-Export? JMX? Custom Metrics? |
| O40 | **Logging** | ●●● | Strukturierte Logs (JSON)? Konfigurierbare Log-Levels? Correlation IDs? |
| O41 | **Tracing** | ●● | Distributed Tracing? OpenTelemetry-Support? Jaeger/Zipkin-kompatibel? |
| O42 | **Alerting** | ● | Integrierte Alerts? Webhook/SNMP für externe Alerting-Systeme? |
| O43 | **Dashboard** | ● | Admin-Dashboard integriert? Grafana-Templates mitgeliefert? |

### Scoring-Guide

| Score | Monitoring |
|---|---|
| 0 | Keine Health Checks, nur File-Logs ohne Struktur |
| 1 | Basis Health Check, Logging vorhanden aber unstrukturiert |
| 2 | Health/Readiness, strukturierte Logs, Prometheus-Metriken |
| 3 | OpenTelemetry (Metrics + Logs + Traces), Grafana-Dashboards, Alerting-Integration |

---

## 8. Update & Patch-Prozess

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O44 | **Release-Kadenz** | ●● | Wie oft erscheinen neue Versionen? Patch/Minor/Major-Zyklus? |
| O45 | **Security Patches** | ●●● | Wie schnell werden CVEs gepatcht? Separate Security-Releases? |
| O46 | **LTS-Versionen** | ●● | Long-Term-Support-Variante? Support-Dauer? |
| O47 | **Update-Prozess** | ●●● | Dokumentierter Upgrade-Pfad? In-Place oder Migration? Downtime? |
| O48 | **Breaking Changes** | ●● | Wie werden Breaking Changes kommuniziert? Deprecation-Policy? |
| O49 | **Kompatibilitätsmatrix** | ●● | Welche Versionen welcher Abhängigkeiten sind unterstützt? |
| O50 | **Rollback nach Update** | ●●● | Rollback-Prozedur dokumentiert? Getestet? Datenbank-Rückwärtskompatibilität? |

### Scoring-Guide

| Score | Update-Prozess |
|---|---|
| 0 | Keine dokumentierte Update-Prozedur, seltene Patches |
| 1 | Updates vorhanden, aber manuell und komplex, kein LTS |
| 2 | Reguläre Releases, dokumentierter Upgrade-Pfad, LTS verfügbar |
| 3 | Automatisierbare Updates, schnelle Security Patches, Rollback-getestet, LTS |

---

## 9. Lizenzmodell

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O51 | **Lizenztyp** | ●● | Perpetual, Subscription, Open Source? Community vs. Enterprise Edition? |
| O52 | **Lizenzmetrik** | ●● | Per Core, Per User, Per Instance, Per Node? Named vs. Concurrent? |
| O53 | **Kosten-Transparenz** | ●● | Klare Preisliste? Versteckte Kosten (Support, Updates, Module)? |
| O54 | **Audit-Klausel** | ● | Lizenz-Audit durch Vendor? Unter welchen Bedingungen? Frist? |
| O55 | **Inkludierter Support** | ●● | Was ist im Preis enthalten? Updates? Patches? Support-Level? |
| O56 | **Escrow** | ● | Source Code Escrow verfügbar? Auslösebedingungen? |

---

## 10. Erweiterbarkeit & Customizing

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O57 | **Plugin-System** | ●● | Erweiterbar via Plugins/Extensions? Marketplace? |
| O58 | **SDK / API** | ●● | Developer SDK vorhanden? Dokumentation? Programmiersprache? |
| O59 | **Scripting** | ● | Integrierte Scripting-Engine? Groovy, JavaScript, Python, Lua? |
| O60 | **Custom UI** | ●● | UI anpassbar? White-Labeling? Custom Themes? |
| O61 | **Workflow-Engine** | ● | Integrierte Workflow-/BPMN-Engine? Anpassbare Geschäftsprozesse? |
| O62 | **Upgrade-Sicherheit** | ●●● | Bleiben Customizations bei Updates erhalten? Dokumentierte Extension Points? |

### Scoring-Guide

| Score | Erweiterbarkeit |
|---|---|
| 0 | Keine Erweiterungsmöglichkeit, Black Box |
| 1 | Basis-Konfiguration, aber kein Plugin-System, kein SDK |
| 2 | Plugin-System oder SDK, dokumentierte Extension Points, Customizations update-sicher |
| 3 | Offenes Plugin-Ökosystem + SDK + Scripting + API + dokumentierte Architektur |

---

## 11. Dokumentation

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| O63 | **Installationsanleitung** | ●●● | Schritt-für-Schritt? Für alle Deployment-Varianten? |
| O64 | **Admin-Guide** | ●● | Betriebshandbuch? Konfigurationsreferenz? Troubleshooting? |
| O65 | **API-Dokumentation** | ●● | OpenAPI/Swagger? Aktuell? Mit Beispielen? |
| O66 | **Architektur-Dokumentation** | ●● | Systemarchitektur beschrieben? Komponentendiagramm? |
| O67 | **Release Notes** | ●● | Für jede Version? Mit Breaking Changes? Migrationshinweisen? |
| O68 | **Qualität** | ● | Aktualität? Vollständigkeit? Sprache (DE/EN)? Suchfunktion? |
