# Scoring-Templates & Bewertungsvorlagen

Vorlagen für die strukturierte Bewertung von IT-Lösungen.

## 1. Bewertungsschema

### Score-Definition

| Score | Bedeutung | Icon |
|---|---|---|
| **3** | Übertrifft Anforderungen — Best Practice | 🟢 |
| **2** | Erfüllt Anforderungen — Standard | 🟢 |
| **1** | Teilweise erfüllt — mit Einschränkungen / Auflagen | 🟡 |
| **0** | Nicht erfüllt / nicht vorhanden | 🔴 |
| **–** | Nicht bewertet — Information ausstehend | ⬜ |

### Gewichtung

| Gewicht | Bedeutung | Faktor | Darstellung |
|---|---|---|---|
| **Kritisch** | K.O.-fähig, regulatorisch oder sicherheitsrelevant | ×3 | ●●● |
| **Wichtig** | Wesentlich für Betrieb und Integration | ×2 | ●● |
| **Nice-to-have** | Wünschenswert, aber nicht entscheidend | ×1 | ● |

### Ampelsystem

| Gesamtscore | Ampel | Bewertung |
|---|---|---|
| ≥ 80% | 🟢 GRÜN | Empfohlen |
| 60–79% | 🟡 GELB | Bedingt empfohlen — Auflagen definieren |
| < 60% | 🔴 ROT | Nicht empfohlen |
| K.O.-Kriterium = 0 | 🔴 ROT | Automatisch ROT, unabhängig vom Gesamtscore |

---

## 2. Detailbewertung — SaaS

### Vorlage

```markdown
# Detailbewertung: [Produktname] (SaaS)

**Bewertungsdatum:** [Datum]
**Bewerter:** [Name/Rolle]
**Version:** [Produktversion]
**Datenquellen:** [Aufzählung der verwendeten Dokumente]

## Vendor Assessment

| # | Kriterium | Gewicht | Score | Evidenz / Kommentar |
|---|---|---|---|---|
| V01 | Firmensitz & Jurisdiktion | ●●● | _/3 | |
| V02 | Niederlassungen | ●● | _/3 | |
| V03 | Gründungsjahr | ●● | _/3 | |
| V04 | Mitarbeiterzahl | ●● | _/3 | |
| V05 | Branchenfokus | ● | _/3 | |
| V06 | Eigentümerstruktur | ●●● | _/3 | |
| V07 | Investor / Muttergesellschaft | ●● | _/3 | |
| V08 | Finanzielle Stabilität | ●●● | _/3 | |
| V09 | Übernahme-Risiko | ●● | _/3 | |
| V10 | Insolvenz-Risiko | ●●● | _/3 | |
| V11 | Marktposition | ●● | _/3 | |
| V12 | Kunden im DACH-Raum | ●● | _/3 | |
| V13 | Kundenzahl | ●● | _/3 | |
| V16 | Release-Kadenz | ●● | _/3 | |
| V19 | End-of-Life-Risiko | ●●● | _/3 | |
| V21 | Implementierungspartner | ●● | _/3 | |
| V25 | Vertragsende-Szenario | ●●● | _/3 | |
| V28 | Datenrückgabe | ●●● | _/3 | |

**Kategorie-Score Vendor:** ___ / ___ = ___%

## Sicherheit & Compliance

| # | Kriterium | Gewicht | Score | Evidenz / Kommentar |
|---|---|---|---|---|
| C01 | ISO 27001 | ●●● | _/3 | |
| C02 | SOC 2 Type II | ●●● | _/3 | |
| C03 | ISO 27017/27018 | ●● | _/3 | |
| C04 | C5 (BSI) | ●● | _/3 | |
| C08 | Pentest-Reports | ●● | _/3 | |
| C10 | Audit-Recht | ●● | _/3 | |
| C11 | Encryption at Rest | ●●● | _/3 | |
| C12 | Encryption in Transit | ●●● | _/3 | |
| C13 | Key Management | ●●● | _/3 | |
| C14 | BYOK / HYOK | ●● | _/3 | |
| C17 | SSO-Fähigkeit | ●●● | _/3 | |
| C18 | MFA | ●●● | _/3 | |
| C19 | Entra ID Integration | ●●● | _/3 | |
| C20 | User Provisioning (SCIM) | ●● | _/3 | |
| C21 | RBAC / ABAC | ●●● | _/3 | |
| C25 | AVV / DPA | ●●● | _/3 | |
| C26 | TOM | ●●● | _/3 | |
| C27 | Subprocessor-Mgmt | ●● | _/3 | |
| C30 | Datenlöschung | ●●● | _/3 | |
| C34 | NIS2-Lieferkettenpflichten | ●●● | _/3 | |
| C35 | Incident Reporting | ●●● | _/3 | |
| C38 | Vulnerability Management | ●●● | _/3 | |
| C45 | Audit Trail | ●●● | _/3 | |
| C47 | Log-Export | ●● | _/3 | |

**Kategorie-Score Sicherheit:** ___ / ___ = ___%

## SaaS-spezifische Kriterien

| # | Kriterium | Gewicht | Score | Evidenz / Kommentar |
|---|---|---|---|---|
| S01 | Speicherort der Daten | ●●● | _/3 | |
| S02 | Verarbeitungsstandorte | ●●● | _/3 | |
| S03 | Backup-Standorte | ●●● | _/3 | |
| S05 | Datenklassifikation | ●●● | _/3 | |
| S07 | Uptime-Garantie | ●●● | _/3 | |
| S10 | RTO / RPO | ●●● | _/3 | |
| S11 | SLA-Credits | ●● | _/3 | |
| S14 | API-Verfügbarkeit | ●●● | _/3 | |
| S15 | API-Umfang | ●●● | _/3 | |
| S16 | API-Dokumentation | ●● | _/3 | |
| S19 | Webhooks / Events | ●● | _/3 | |
| S22 | SSO-Protokolle | ●●● | _/3 | |
| S25 | User Provisioning | ●● | _/3 | |
| S32 | Datenexport | ●●● | _/3 | |
| S37 | Lock-in-Risiko | ●●● | _/3 | |
| S38 | Backup-Strategie | ●●● | _/3 | |
| S42 | Lizenzmodell | ●● | _/3 | |
| S43 | Preistransparenz | ●● | _/3 | |
| S47 | Support-Tiers | ●● | _/3 | |
| S50 | Release Notes | ●● | _/3 | |

**Kategorie-Score SaaS:** ___ / ___ = ___%

## Integration & Architektur

| # | Kriterium | Gewicht | Score | Evidenz / Kommentar |
|---|---|---|---|---|
| Enterprise-Anbindung (VPN/Private Link) | ●● | _/3 | |
| IdP-Integration (Entra ID) | ●●● | _/3 | |
| Bestehende Systemlandschaft (Passfähigkeit) | ●● | _/3 | |
| Standardprotokolle | ●● | _/3 | |
| Middleware-Kompatibilität | ● | _/3 | |

**Kategorie-Score Integration:** ___ / ___ = ___%

## K.O.-Kriterien

| Kriterium | Status | Kommentar |
|---|---|---|
| Data Residency EU | ✅ / ❌ | |
| SSO/OIDC (Entra ID) | ✅ / ❌ | |
| AVV/DPA vorhanden | ✅ / ❌ | |
| ISO 27001 oder SOC 2 Type II | ✅ / ❌ | |
| Verschlüsselung at rest & in transit | ✅ / ❌ | |
| Datenexport möglich | ✅ / ❌ | |
| End-of-Life > 3 Jahre | ✅ / ❌ | |

## Gesamtergebnis

| Kategorie | Gewicht | Score | Max | Prozent |
|---|---|---|---|---|
| Vendor Assessment | ●● | | | % |
| Sicherheit & Compliance | ●●● | | | % |
| SaaS-spezifisch | ●●● | | | % |
| Integration | ●● | | | % |
| **Gesamt** | | | | **__%** |

**Ampel:** 🟢 / 🟡 / 🔴

## Empfehlung

[Empfehlung mit Begründung]

## Auflagen (bei GELB)

- [ ] [Auflage 1]
- [ ] [Auflage 2]

## Offene Punkte

- [ ] [Fehlende Information 1]
- [ ] [Fehlende Information 2]
```

---

## 3. Detailbewertung — On-Premises

### Vorlage

```markdown
# Detailbewertung: [Produktname] (On-Premises)

**Bewertungsdatum:** [Datum]
**Bewerter:** [Name/Rolle]
**Version:** [Produktversion]
**Datenquellen:** [Aufzählung der verwendeten Dokumente]

## Vendor Assessment

[Identisch mit SaaS — siehe Vorlage oben]

## Sicherheit & Compliance

| # | Kriterium | Gewicht | Score | Evidenz / Kommentar |
|---|---|---|---|---|
| C01 | ISO 27001 (Vendor) | ●● | _/3 | |
| C08 | Pentest-Reports | ●● | _/3 | |
| C11 | Encryption at Rest | ●●● | _/3 | |
| C12 | Encryption in Transit | ●●● | _/3 | |
| C17 | SSO-Fähigkeit | ●●● | _/3 | |
| C18 | MFA | ●●● | _/3 | |
| C19 | Entra ID Integration | ●●● | _/3 | |
| C21 | RBAC / ABAC | ●●● | _/3 | |
| C38 | Vulnerability Management | ●●● | _/3 | |
| C45 | Audit Trail | ●●● | _/3 | |

**Kategorie-Score Sicherheit:** ___ / ___ = ___%

## On-Premises-spezifische Kriterien

| # | Kriterium | Gewicht | Score | Evidenz / Kommentar |
|---|---|---|---|---|
| O01 | UI-Framework | ●● | _/3 | |
| O02 | Browser-Support | ●● | _/3 | |
| O07 | Backend Sprache/Framework | ●●● | _/3 | |
| O08 | Architekturstil | ●● | _/3 | |
| O09 | API-Layer | ●●● | _/3 | |
| O14 | Unterstützte RDBMS | ●●● | _/3 | |
| O17 | DB HA-Fähigkeit | ●●● | _/3 | |
| O18 | Backup-Strategie | ●●● | _/3 | |
| O20 | DB-Verschlüsselung | ●●● | _/3 | |
| O21 | Deployment-Varianten | ●●● | _/3 | |
| O22 | Container-Support | ●●● | _/3 | |
| O23 | Kubernetes-Support | ●● | _/3 | |
| O24 | Betriebssystem | ●● | _/3 | |
| O27 | Minimale Hardware | ●● | _/3 | |
| O31 | Externe Abhängigkeiten | ●●● | _/3 | |
| O32 | Deployment-Modell | ●●● | _/3 | |
| O33 | Horizontale Skalierung | ●● | _/3 | |
| O36 | Zero-Downtime Deployment | ●● | _/3 | |
| O37 | Rollback | ●●● | _/3 | |
| O38 | Health Checks | ●●● | _/3 | |
| O39 | Metriken | ●● | _/3 | |
| O40 | Logging | ●●● | _/3 | |
| O44 | Release-Kadenz | ●● | _/3 | |
| O45 | Security Patches | ●●● | _/3 | |
| O47 | Update-Prozess | ●●● | _/3 | |
| O50 | Rollback nach Update | ●●● | _/3 | |
| O51 | Lizenztyp | ●● | _/3 | |
| O57 | Plugin-System | ●● | _/3 | |
| O62 | Upgrade-Sicherheit | ●●● | _/3 | |
| O63 | Installationsanleitung | ●●● | _/3 | |

**Kategorie-Score On-Prem:** ___ / ___ = ___%

## Integration & Architektur

| # | Kriterium | Gewicht | Score | Evidenz / Kommentar |
|---|---|---|---|---|
| API-Schnittstellen (Umfang) | ●●● | _/3 | |
| Standardprotokolle | ●● | _/3 | |
| IdP-Integration (Entra ID / LDAP) | ●●● | _/3 | |
| Bestehende Systemlandschaft | ●● | _/3 | |
| ETL/ELT-Fähigkeit | ●● | _/3 | |

**Kategorie-Score Integration:** ___ / ___ = ___%

## K.O.-Kriterien

| Kriterium | Status | Kommentar |
|---|---|---|
| SSO/OIDC (Entra ID) | ✅ / ❌ | |
| Verschlüsselung at rest & in transit | ✅ / ❌ | |
| Kompatibel mit Runtime-Infrastruktur | ✅ / ❌ | |
| Datenexport möglich | ✅ / ❌ | |
| End-of-Life > 3 Jahre | ✅ / ❌ | |
| Security Patches zeitnah | ✅ / ❌ | |

## Gesamtergebnis

| Kategorie | Gewicht | Score | Max | Prozent |
|---|---|---|---|---|
| Vendor Assessment | ●● | | | % |
| Sicherheit & Compliance | ●●● | | | % |
| On-Prem-spezifisch | ●●● | | | % |
| Integration | ●● | | | % |
| **Gesamt** | | | | **__%** |

**Ampel:** 🟢 / 🟡 / 🔴

## Empfehlung

[Empfehlung mit Begründung]

## Auflagen (bei GELB)

- [ ] [Auflage 1]

## Offene Punkte

- [ ] [Fehlende Information 1]
```

---

## 4. Vergleichsmatrix

### Vorlage

```markdown
# Lösungsvergleich: [Use Case]

**Bewertungsdatum:** [Datum]
**Verglichene Lösungen:** [Lösung A] vs. [Lösung B] (vs. [Lösung C])

## Steckbrief-Vergleich

| Merkmal | Lösung A | Lösung B |
|---|---|---|
| Produkt | | |
| Vendor | | |
| Typ | SaaS / On-Prem | SaaS / On-Prem |
| Sitz | | |
| Zertifizierungen | | |
| Preis (jährlich) | | |

## Bewertungsvergleich

| # | Kriterium | Gewicht | Lösung A | Lösung B |
|---|---|---|---|---|
| | **Vendor** | | | |
| V01 | Firmensitz | ●●● | _/3 | _/3 |
| V08 | Finanzielle Stabilität | ●●● | _/3 | _/3 |
| V12 | DACH-Referenzen | ●● | _/3 | _/3 |
| V19 | End-of-Life-Risiko | ●●● | _/3 | _/3 |
| | **Sicherheit** | | | |
| C01 | ISO 27001 | ●●● | _/3 | _/3 |
| C02 | SOC 2 Type II | ●●● | _/3 | _/3 |
| C11 | Encryption at Rest | ●●● | _/3 | _/3 |
| C17 | SSO | ●●● | _/3 | _/3 |
| C25 | AVV/DPA | ●●● | _/3 | _/3 |
| | **Funktional** | | | |
| | [Kriterium 1] | ●●● | _/3 | _/3 |
| | [Kriterium 2] | ●● | _/3 | _/3 |
| | [Kriterium 3] | ●● | _/3 | _/3 |
| | **Integration** | | | |
| | API-Umfang | ●●● | _/3 | _/3 |
| | Entra ID | ●●● | _/3 | _/3 |
| | Systemlandschaft | ●● | _/3 | _/3 |
| | **Gesamt** | | **__% 🟢🟡🔴** | **__% 🟢🟡🔴** |

## Stärken & Schwächen

### Lösung A
- **Stärken:** [...]
- **Schwächen:** [...]

### Lösung B
- **Stärken:** [...]
- **Schwächen:** [...]

## TCO-Vergleich (5 Jahre)

| Kostenposition | Lösung A | Lösung B |
|---|---|---|
| Lizenz/Abo (5 Jahre) | | |
| Implementierung | | |
| Schulung | | |
| Laufender Betrieb (intern) | | |
| Support (extern) | | |
| Migration | | |
| **Total** | **€ ___** | **€ ___** |

## Empfehlung

[Vergleichende Empfehlung]
```

---

## 5. Score-Berechnung

### Formel

```
Kategorie-Score = Σ (Score_i × Gewicht_i) / Σ (3 × Gewicht_i) × 100%

Wobei: Gewicht ●●● = 3, ●● = 2, ● = 1

Gesamt-Score = (Score_Vendor × 2 + Score_Security × 3 + Score_Typ × 3 + Score_Integration × 2) 
               / (Max_Vendor × 2 + Max_Security × 3 + Max_Typ × 3 + Max_Integration × 2) × 100%
```

### Beispielberechnung

```
Vendor:      V01 (●●●, Score 2) + V08 (●●●, Score 3) + V12 (●●, Score 2) = 2×3 + 3×3 + 2×2 = 19
Max Vendor:  3×3 + 3×3 + 3×2 = 24
Score:       19/24 = 79%

Gesamtscore mit Kategorie-Gewichtung:
  Vendor (79%, Gewicht 2) + Security (85%, Gewicht 3) + SaaS (72%, Gewicht 3) + Integration (80%, Gewicht 2)
  = (79×2 + 85×3 + 72×3 + 80×2) / (100×2 + 100×3 + 100×3 + 100×2) × 100
  = (158 + 255 + 216 + 160) / 1000 × 100
  = 78.9% → 🟡 GELB
```
