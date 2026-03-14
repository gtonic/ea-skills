# Sicherheit & Compliance — Kriterienkatalog

Bewertungskriterien für Sicherheit, Zertifizierungen und regulatorische Compliance. Gilt für SaaS und On-Premises gleichermaßen.

## 1. Zertifizierungen & Audits

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| C01 | **ISO 27001** | ●●● | Zertifiziert? Scope korrekt (inkl. Produkt/Service)? Zertifikat aktuell? Ausstellende Stelle akkreditiert? |
| C02 | **SOC 2 Type II** | ●●● | Vorhanden? Welche Trust Service Criteria (Security, Availability, Confidentiality, Privacy, Processing Integrity)? Berichtszeitraum? |
| C03 | **ISO 27017 / 27018** | ●● | Cloud-spezifische Zertifizierungen vorhanden? (Besonders relevant für SaaS) |
| C04 | **C5 (BSI)** | ●● | C5-Testat vorhanden? Relevant für deutsche öffentliche Auftraggeber und regulierte Branchen |
| C05 | **CSA STAR** | ● | Cloud Security Alliance STAR Level? Self-Assessment oder Audit? |
| C06 | **TISAX** | ● | Relevant für Automotive-Zulieferer. TISAX-Label vorhanden? Assessment Level? |
| C07 | **Branchenspezifisch** | ●● | HIPAA (Gesundheit), PCI DSS (Payment), FedRAMP, ISAE 3402? — je nach Branche |
| C08 | **Pentest-Reports** | ●● | Regelmäßige Penetrationstests? Durch wen? Ergebnisse einsehbar (NDA)? Frequenz? |
| C09 | **Bug Bounty** | ● | Öffentliches Bug-Bounty-Programm? Vulnerability Disclosure Policy? |
| C10 | **Audit-Recht** | ●● | Kann der Kunde (oder Dritter) eigene Audits durchführen? Vertraglich geregelt? |

### Scoring-Guide

| Score | Zertifizierungen |
|---|---|
| 0 | Keine Zertifizierung, kein Pentest, keine Audit-Möglichkeit |
| 1 | Selbstauskunft (SOC 2 Type I oder ISO 27001 angestrebt), kein aktueller Pentest |
| 2 | ISO 27001 ODER SOC 2 Type II aktuell, regelmäßiger Pentest, Audit-Recht |
| 3 | ISO 27001 + SOC 2 Type II + branchenspezifisch, jährlicher Pentest, Bug Bounty, Audit-Recht |

### Zertifizierungs-Relevanzmatrix

| Zertifizierung | SaaS | On-Prem | Wann besonders relevant |
|---|---|---|---|
| ISO 27001 | ●●● | ●● | Immer — Basiszertifizierung |
| SOC 2 Type II | ●●● | ● | SaaS, Cloud Services |
| ISO 27017/27018 | ●●● | — | Cloud-Dienste |
| C5 (BSI) | ●●● | — | Öffentlicher Sektor DE, regulierte Branchen |
| CSA STAR | ●● | — | Cloud-Bewertung, Ergänzung zu ISO 27001 |
| TISAX | ● | ● | Automotive |
| PCI DSS | ●● | ●● | Zahlungsverarbeitung |
| HIPAA | ●● | ●● | Gesundheitswesen (US-Kontext) |

---

## 2. Verschlüsselung

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| C11 | **Encryption at Rest** | ●●● | AES-256? Welcher Modus? Full-Disk oder Application-Level? |
| C12 | **Encryption in Transit** | ●●● | TLS 1.2+? (TLS 1.3 bevorzugt). Welche Cipher Suites? HSTS? |
| C13 | **Key Management** | ●●● | Wie werden Schlüssel verwaltet? HSM? KMS? Rotation? |
| C14 | **BYOK / HYOK** | ●● | Bring Your Own Key? Hold Your Own Key? Customer Managed Keys? |
| C15 | **End-to-End Encryption** | ● | E2E-Verschlüsselung verfügbar? Für welche Daten? |
| C16 | **Certificate Management** | ●● | TLS-Zertifikat-Management? Auto-Renewal? Custom Domains? |

### Scoring-Guide

| Score | Verschlüsselung |
|---|---|
| 0 | Keine Verschlüsselung at rest, TLS < 1.2 |
| 1 | TLS 1.2, AES-256 at rest, aber kein KMS, keine Key Rotation |
| 2 | TLS 1.2+, AES-256 at rest, KMS mit Rotation, HSM-backed |
| 3 | TLS 1.3, AES-256, KMS + BYOK/HYOK, HSM, E2E Option, Auto-Rotation |

---

## 3. Authentifizierung & Zugriffskontrolle

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| C17 | **SSO-Fähigkeit** | ●●● | SAML 2.0, OIDC? Welche IdPs unterstützt? Multi-IdP? |
| C18 | **Multi-Faktor-Authentifizierung** | ●●● | MFA erzwingbar? Welche Faktoren (TOTP, FIDO2, SMS, Push)? |
| C19 | **Entra ID Integration** | ●●● | Direkte Integration? App Registration? Enterprise App? |
| C20 | **User Provisioning** | ●● | SCIM 2.0? JIT Provisioning? Automatische Deprovisioning? |
| C21 | **RBAC / ABAC** | ●●● | Rollenbasierte Zugriffskontrolle? Attributbasiert? Granularität? |
| C22 | **Privileged Access** | ●●● | Admin-Zugang abgesichert? Separate Admin-Rollen? Just-in-Time Access? |
| C23 | **API-Authentifizierung** | ●● | OAuth 2.0 Client Credentials? API Keys? Token-Rotation? Scopes? |
| C24 | **Conditional Access** | ●● | Wird Conditional Access des IdP respektiert? Geräte-Compliance? IP-Einschränkung? |

### Scoring-Guide

| Score | Authentifizierung |
|---|---|
| 0 | Nur lokale Accounts, kein MFA, kein SSO |
| 1 | SSO vorhanden (SAML oder OIDC), MFA optional, kein SCIM |
| 2 | SSO + MFA erzwingbar + SCIM + RBAC + Entra ID Integration |
| 3 | SSO + MFA (FIDO2) + SCIM + ABAC + Conditional Access + JIT Admin + API OAuth 2.0 |

---

## 4. Datenschutz & DSGVO

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| C25 | **AVV / DPA** | ●●● | Auftragsverarbeitungsvertrag vorhanden? Art. 28 DSGVO konform? |
| C26 | **TOM (Technisch-Organisatorische Maßnahmen)** | ●●● | Dokumentiert? Aktuell? Angemessen für Datenart? |
| C27 | **Subprocessor-Management** | ●● | Liste vorhanden? Änderungsbenachrichtigung? Widerspruchsrecht? |
| C28 | **DPIA-Support** | ●● | Unterstützung bei Datenschutz-Folgenabschätzung? Zuarbeit? |
| C29 | **Betroffenenrechte** | ●● | Unterstützung bei Auskunft, Löschung, Portabilität (Art. 15–20)? Tooling? |
| C30 | **Datenlöschung** | ●●● | Garantierte Löschung nach Vertragsende? Frist? Nachweis? Auch Backups? |
| C31 | **Data Processing Locations** | ●●● | Wo werden Daten verarbeitet? EU-only möglich? Transfers nur mit SCCs? |
| C32 | **Privacy by Design** | ●● | Datenminimierung? Zweckbindung? Löschkonzept? Anonymisierung/Pseudonymisierung? |
| C33 | **Datenschutzbeauftragter** | ● | Vendor hat benannten DSB? Kontaktdaten veröffentlicht? |

### Scoring-Guide

| Score | DSGVO |
|---|---|
| 0 | Kein AVV, keine TOM, keine DSGVO-Awareness |
| 1 | AVV vorhanden, aber generisch; TOM-Verweis ohne Detail; keine Löschgarantie |
| 2 | DSGVO-konformer AVV, detaillierte TOM, Subprocessor-Liste, Löschgarantie |
| 3 | AVV + detaillierte TOM + Subprocessor-Mgmt + DPIA-Support + Privacy by Design + DSB + Löschnachweis |

---

## 5. NIS2-Relevanz

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| C34 | **Lieferkettenpflichten** | ●●● | Ist der Vendor in einer NIS2-relevanten Lieferkette? Awareness vorhanden? |
| C35 | **Incident Reporting** | ●●● | Meldepflicht-Unterstützung? 24h-Erstmeldung, 72h-Folgemeldung? Automatisierte Benachrichtigung? |
| C36 | **Risikomanagement** | ●● | Dokumentiertes Risikomanagement nach NIS2 Art. 21? |
| C37 | **Business Continuity** | ●● | BCP/BCM vorhanden? Getestet? Dokumentiert? |
| C38 | **Vulnerability Management** | ●●● | Patch-Management-Prozess? CVE-Handling? Zeitrahmen für kritische Patches? |

### Scoring-Guide

| Score | NIS2 |
|---|---|
| 0 | Keine NIS2-Awareness, kein Incident Reporting, kein Patch-Management |
| 1 | Basis-Awareness, aber keine formale Umsetzung |
| 2 | Incident Reporting, Risikomanagement, Vulnerability Management dokumentiert |
| 3 | NIS2-konform, BCP getestet, SLA für Critical Patches < 48h, automatisiertes Reporting |

---

## 6. Netzwerk- & Infrastruktursicherheit

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| C39 | **Netzwerksegmentierung** | ●●● | DMZ, Segmentierung, Micro-Segmentation? Zero Trust? |
| C40 | **DDoS-Schutz** | ●● | DDoS-Mitigation? WAF? Rate Limiting? (Besonders relevant für SaaS) |
| C41 | **Intrusion Detection** | ●● | IDS/IPS vorhanden? SIEM? SOC? 24/7 Monitoring? |
| C42 | **Private Connectivity** | ●● | Private Link, VPN, ExpressRoute, Direct Connect? (SaaS) |
| C43 | **IP-Whitelisting** | ●● | IP-basierter Zugriff konfigurierbar? Für API und UI? |
| C44 | **WAF** | ●● | Web Application Firewall? OWASP Top 10 Coverage? |

### Scoring-Guide

| Score | Netzwerksicherheit |
|---|---|
| 0 | Keine Segmentierung, kein DDoS-Schutz, kein IDS |
| 1 | Basis-Firewall, CDN mit DDoS-Schutz, keine Private Connectivity |
| 2 | Segmentiert, WAF, IDS, DDoS-Schutz, IP-Whitelisting, Private Link Option |
| 3 | Zero Trust Network, SOC 24/7, Private Link + VPN, WAF + DDoS + IDS/IPS |

---

## 7. Audit & Logging

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| C45 | **Audit Trail** | ●●● | Lückenloser Audit Trail? Wer hat wann was geändert? Unveränderlich? |
| C46 | **Log-Retention** | ●● | Wie lange werden Logs aufbewahrt? Konfigurierbar? Compliance-konform? |
| C47 | **Log-Export** | ●● | Logs exportierbar? In welchem Format? Streaming zu SIEM? |
| C48 | **SIEM-Integration** | ●● | Syslog, CEF, LEEF, Azure Sentinel, Splunk? |
| C49 | **Admin-Aktivitäten** | ●●● | Werden Admin-Aktionen separat protokolliert? Privileged Activity Logging? |
| C50 | **Datenzugriffs-Logging** | ●● | Wird Datenzugriff (nicht nur Änderungen) geloggt? Konfigurierbar? |

### Scoring-Guide

| Score | Audit & Logging |
|---|---|
| 0 | Kein Audit Trail, keine Logs verfügbar |
| 1 | Basis-Logging (Login-Events), kein Export, kurze Retention |
| 2 | Audit Trail, konfigurierbare Retention, Log-Export, Admin-Logging |
| 3 | Unveränderlicher Audit Trail, SIEM-Integration, Datenzugriffs-Logging, > 1 Jahr Retention |

---

## Regulatorische Schnellprüfung

Prüfe basierend auf dem Organisationskontext, welche Regulierung relevant ist:

| Organisation | Relevante Regulierung | Priorität |
|---|---|---|
| **Jede Organisation (EU)** | DSGVO, NIS2 (ab 10/2024), EAA (ab 06/2025) | ●●● |
| **Öffentlicher Sektor (DE)** | C5, EVB-IT, BSI-Grundschutz | ●●● |
| **Öffentlicher Sektor (AT)** | ELGA, E-Government-Gesetz, NISG | ●●● |
| **Gesundheitswesen** | DSGVO Art. 9, ELGA (AT), Krankenanstaltengesetz | ●●● |
| **Finanzsektor** | DORA, MaRisk, BAIT/VAIT, EBA-Guidelines | ●●● |
| **Automotive** | TISAX, IATF 16949 | ●● |
| **Kritische Infrastruktur** | NIS2, KRITIS-Verordnung (DE), NISG (AT) | ●●● |
| **AI-Einsatz** | EU AI Act, Hochrisiko-Klassifikation | ●●● |
