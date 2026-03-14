# SaaS-Kriterienkatalog

Spezifische Bewertungskriterien für Software-as-a-Service-Lösungen.

## 1. Data Residency & Datenverarbeitung

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S01 | **Speicherort der Daten** | ●●● | In welcher Region/welchem Land werden Daten gespeichert? Ist EU/EWR garantiert? Ist der Standort vertraglich fixiert? |
| S02 | **Verarbeitungsstandorte** | ●●● | Wo werden Daten verarbeitet (kann von Speicherort abweichen)? Gibt es Transfers in Drittländer? |
| S03 | **Backup-Standorte** | ●●● | Wo liegen Backups? Ebenfalls EU? Geo-Redundanz innerhalb EU? |
| S04 | **Support-Zugriff** | ●● | Haben Support-Mitarbeiter aus Nicht-EU-Ländern Zugriff auf Produktivdaten? Unter welchen Bedingungen? |
| S05 | **Datenklassifikation** | ●●● | Welche Datentypen werden verarbeitet? PII, Gesundheitsdaten (Art. 9 DSGVO), Finanzdaten, Geschäftsgeheimnisse? |
| S06 | **Datentrennung** | ●● | Wie werden Mandantendaten getrennt? Logisch (Schema) oder physisch (Instanz)? |

### Scoring-Guide

| Score | Data Residency |
|---|---|
| 0 | Keine Kontrolle über Speicherort, Daten außerhalb EU ohne SCCs |
| 1 | EU-Speicherung optional (Aufpreis), Backup ggf. außerhalb EU |
| 2 | EU-Speicherung Standard, vertragliche Zusicherung, Backup in EU |
| 3 | Wahlmöglichkeit EU/AT/DE/CH, physische Isolation, kein Drittland-Transfer |

---

## 2. Service Level Agreement (SLA)

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S07 | **Uptime-Garantie** | ●●● | Garantierte Verfügbarkeit? Definition (nur Compute? inkl. Storage, API, UI?) |
| S08 | **Messmethode** | ●● | Wie wird Uptime gemessen? Welcher Zeitraum (monatlich/jährlich)? Statuspage öffentlich? |
| S09 | **Maintenance Windows** | ●● | Geplante Wartungsfenster? Abzug von Uptime-Berechnung? Vorlaufzeit für Ankündigung? |
| S10 | **RTO / RPO** | ●●● | Recovery Time Objective / Recovery Point Objective? Vertraglich zugesichert? |
| S11 | **SLA-Credits** | ●● | Gibt es Kompensation bei Unterschreitung? Automatisch oder auf Antrag? Höhe? |
| S12 | **Incident Response** | ●● | Reaktionszeiten nach Severity? Eskalationspfade? 24/7 oder Business Hours? |
| S13 | **Kumulierte Ausfälle** | ● | Regelung für wiederholte SLA-Verletzungen? Sonderkündigungsrecht? |

### Scoring-Guide

| Score | SLA |
|---|---|
| 0 | Keine SLA oder „best effort" |
| 1 | SLA < 99.5%, keine Credits, vage Definitionen |
| 2 | SLA ≥ 99.9%, Credits, klare Messmethode, definierte RTO/RPO |
| 3 | SLA ≥ 99.95%, automatische Credits, Multi-Region HA, RTO < 1h / RPO < 15min |

---

## 3. API & Integration

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S14 | **API-Verfügbarkeit** | ●●● | Gibt es eine öffentliche API? Welcher Typ (REST, GraphQL, SOAP, OData)? |
| S15 | **API-Umfang** | ●●● | Deckt die API alle relevanten Entitäten/Funktionen ab? CRUD vollständig? |
| S16 | **API-Dokumentation** | ●● | OpenAPI/Swagger vorhanden? Aktualität? Beispiele? SDK? |
| S17 | **Versionierung** | ●● | API-Versionierungsstrategie? Deprecation-Policy? Breaking Changes? |
| S18 | **Rate Limits** | ●● | Limits pro Minute/Stunde? Burst-Fähigkeit? Erhöhung möglich? |
| S19 | **Webhooks / Events** | ●● | Können Events abonniert werden? Webhook-Reliability? Retry-Logik? |
| S20 | **Bulk-Operationen** | ●● | Batch-API für Massenoperationen? Import/Export via API? |
| S21 | **Sandbox / Test** | ● | Testumgebung mit API-Zugang? Separate Instanz oder Feature-Flags? |

### Scoring-Guide

| Score | API |
|---|---|
| 0 | Keine API verfügbar |
| 1 | API vorhanden, aber eingeschränkt (nur read, wenige Entitäten, schlechte Doku) |
| 2 | Vollständige REST/GraphQL-API, dokumentiert, Webhooks vorhanden |
| 3 | Vollständige API + SDK + Sandbox + Bulk-Ops + Events + Rate Limits transparent |

---

## 4. Authentifizierung & Identity-Integration

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S22 | **SSO-Protokolle** | ●●● | SAML 2.0, OIDC, WS-Federation? Welche IdPs unterstützt? |
| S23 | **Entra ID Integration** | ●●● | Direkte Integration mit Microsoft Entra ID? App-Registrierung erforderlich? |
| S24 | **MFA** | ●●● | MFA nativ oder via IdP? FIDO2/Passkeys unterstützt? |
| S25 | **User Provisioning** | ●● | SCIM 2.0 Support? Automatische User-/Gruppen-Synchronisation? |
| S26 | **Conditional Access** | ●● | Respektiert Conditional Access Policies des IdP? Device Compliance? |
| S27 | **Session Management** | ●● | Session-Timeout konfigurierbar? Token-Lifetime? Force Logout? |

### Scoring-Guide

| Score | Authentifizierung |
|---|---|
| 0 | Nur lokale Accounts, kein SSO |
| 1 | SAML oder OIDC vorhanden, aber kein SCIM, kein Conditional Access |
| 2 | OIDC + SAML, Entra ID unterstützt, SCIM vorhanden, MFA via IdP |
| 3 | Vollständige Entra ID Integration, SCIM, Conditional Access, Passkeys, konfigurierbare Sessions |

---

## 5. Multi-Tenancy & Architektur

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S28 | **Tenant-Modell** | ●● | Shared, Pool, Dedicated? Isolierungsgrad? |
| S29 | **Noisy Neighbor** | ●● | Schutz vor Leistungseinbußen durch andere Tenants? Resource Limits? |
| S30 | **Tenant-Konfiguration** | ● | Welche Anpassungen sind pro Tenant möglich? Custom Fields, Workflows, Branding? |
| S31 | **Architektur-Transparenz** | ● | Gibt es ein Architektur-Whitepaper? Security Whitepaper? Trust Center? |

---

## 6. Datenportabilität & Exit

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S32 | **Datenexport** | ●●● | Welche Formate (JSON, CSV, XML, SQL Dump)? Vollständiger Export aller Daten? |
| S33 | **Bulk-Export-API** | ●● | Programmatischer Vollexport via API? Inkrementeller Export? |
| S34 | **Migration-Tools** | ● | Stellt der Anbieter Migrationshilfen bereit? Dokumentierte Exit-Prozedur? |
| S35 | **Datenlöschung** | ●● | Garantierte Löschung nach Vertragsende? Frist? Nachweis? |
| S36 | **Transition-Periode** | ●● | Zugriff auf Daten nach Kündigung (z.B. 90 Tage)? Read-only? Export? |
| S37 | **Lock-in-Risiko** | ●●● | Proprietäre Formate? Proprietäre Workflows? Migrationsaufwand? |

### Scoring-Guide

| Score | Datenportabilität |
|---|---|
| 0 | Kein Datenexport möglich, vollständiger Lock-in |
| 1 | Manueller Export (CSV), nicht alle Entitäten, keine API |
| 2 | API-Export aller Daten, Standard-Formate, dokumentierte Exit-Prozedur |
| 3 | Vollständiger API-Export + Migrationstool + Transition-Periode + Löschnachweis |

---

## 7. Backup & Disaster Recovery

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S38 | **Backup-Strategie** | ●●● | Wie oft? Inkrementell/Vollständig? Retention? Standort? |
| S39 | **Self-Service-Restore** | ●● | Point-in-Time Recovery möglich? Granularität (Datensatz vs. Datenbank)? |
| S40 | **Geo-Redundanz** | ●● | Multi-Region? Automatisches Failover? RPO bei Region-Ausfall? |
| S41 | **DR-Tests** | ● | Regelmäßige DR-Tests durch Anbieter? Ergebnisse einsehbar? |

---

## 8. Preismodell & Kosten

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S42 | **Lizenzmodell** | ●● | Per User, Per Consumption, Tiered, Flat? Named vs. Concurrent? |
| S43 | **Preistransparenz** | ●● | Öffentliche Preisliste? Versteckte Kosten (Storage, API-Calls, Add-ons)? |
| S44 | **Skalierungskurve** | ●● | Wie verändern sich Kosten bei Wachstum? Mengenrabatte? Deckelung? |
| S45 | **Vertragslaufzeit** | ●● | Mindestlaufzeit? Kündigungsfrist? Jährlich vs. monatlich? |
| S46 | **True-up / Nachlizenzierung** | ● | Regelung bei Überschreitung? Automatisch oder auf Antrag? |

---

## 9. Support & Change Management

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S47 | **Support-Tiers** | ●● | L1/L2/L3 Struktur? Premium Support verfügbar? |
| S48 | **Reaktionszeiten** | ●● | SLA für Support-Ticket-Bearbeitung nach Severity? |
| S49 | **Sprache** | ● | Deutschsprachiger Support? In welchem Tier? |
| S50 | **Release Notes** | ●● | Regelmäßige Release Notes? Vorab-Ankündigung von Breaking Changes? |
| S51 | **Opt-in/Opt-out** | ●● | Kontrolle über Update-Zeitpunkt? Staged Rollout? Early Access? |
| S52 | **Erreichbarkeit** | ●● | 24/7 oder Business Hours? Zeitzone? Kanäle (Telefon, Chat, E-Mail, Portal)? |

---

## 10. Accessibility & Compliance

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| S53 | **WCAG-Konformität** | ●● | WCAG 2.1 Level AA? VPAT / Accessibility Statement? |
| S54 | **European Accessibility Act** | ●● | Konformität mit EAA (ab 28.06.2025)? |
| S55 | **Barrierefreiheit** | ● | Screen Reader Support, Keyboard-Navigation, Kontraste? |

---

## Subprocessor-Checkliste

Zusätzlich zur Kriterienbewertung, prüfe die Subprocessor-Kette:

| Prüfpunkt | Detail |
|---|---|
| Subprocessor-Liste verfügbar? | Öffentlich oder auf Anfrage? |
| Änderungsbenachrichtigung | Vorab-Information bei neuen Subprocessors? Frist? |
| Widerspruchsrecht | Kann gegen neue Subprocessors Widerspruch eingelegt werden? |
| Subprocessor-Standorte | Alle in EU/EWR? Falls nicht: SCCs vorhanden? |
| Subprocessor-Zweck | Klar dokumentiert, warum jeder Subprocessor eingesetzt wird? |
