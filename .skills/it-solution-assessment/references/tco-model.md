# TCO-Modell — Total Cost of Ownership (5 Jahre)

Referenzdatei für die vollständige Kostenermittlung von IT-Lösungen über einen 5-Jahres-Zeitraum.
Berücksichtigt sowohl sichtbare als auch versteckte Kosten für SaaS- und On-Premises-Lösungen.

## Wann diese Datei lesen

- Bei jeder Lösungsbewertung (ergänzend zum Scoring)
- Bei SaaS vs. On-Prem Vergleichen (Kostennormalisierung)
- Bei Entscheidungsvorlagen (TCO als Entscheidungsgrundlage)
- Bei Make-or-Buy-Analysen
- Bei Migrationsplanung (Ist-TCO vs. Soll-TCO)

---

## 1. TCO-Kostenkategorien

### 1.1 SaaS-Lösung

#### A — Laufende Abo-/Lizenzkosten

| Kostenposition | Berechnung | Typischer Anteil | Versteckte Kosten |
|---|---|---|---|
| **Basis-Subscription** | Preis × User × 60 Monate | 40–60% | Preiserhöhungen bei Verlängerung (typisch 5–10% p.a.) |
| **Zusatzmodule / Add-ons** | Pro Modul × 60 Monate | 5–15% | Oft nachträglich erforderlich für Basis-Funktionalität |
| **Storage-/Volumen-Kosten** | Pro GB/TB × geschätztes Wachstum | 3–8% | Exponentielles Datenwachstum nicht einkalkuliert |
| **API-Calls / Transaktionen** | Pro Call × geschätztes Volumen | 2–5% | Peaks und Batch-Jobs treiben Kosten |
| **Premium-Support** | Zusätzlich zum Basisvertrag | 5–10% | Basis-Support oft unzureichend für Enterprise |

#### B — Einmalkosten (Initial)

| Kostenposition | Berechnung | Versteckte Kosten |
|---|---|---|
| **Implementierung / Konfiguration** | Dienstleistungstage × Tagessatz | Scope Creep, Change Requests |
| **Datenmigration** | Komplexität × Volumen | Datenbereinigung, Mapping, mehrere Iterationen |
| **Integration (API/Middleware)** | Pro Schnittstelle × Aufwand | Bidirektionale Sync deutlich teurer als unidirektional |
| **Schulung** | Pro Rolle × Trainingstage | Produktivitätsverlust während Umstellung |
| **Projektmanagement** | Interner + externer Aufwand | PM-Overhead oft 15–25% der Implementierungskosten |
| **Change Management** | Kommunikation, Adoption | Häufig vergessen, aber kritisch für ROI |

#### C — Laufende Betriebskosten (intern)

| Kostenposition | Berechnung | Versteckte Kosten |
|---|---|---|
| **Interner Application Owner** | Anteil FTE × Gehalt × 60 Monate | Auch SaaS braucht interne Governance |
| **User-Administration** | Anteil FTE (Onboarding, Deprovisioning) | Steigt mit Fluktuation |
| **Monitoring & Incident Response** | Anteil FTE / ITSM-Tool | Integration in ITSM-Landschaft |
| **Vendor Management** | Reviews, Verhandlungen, Eskalationen | Oft unterschätzt bei Multi-SaaS |
| **Compliance-Pflege** | AVV-Review, Audit-Begleitung, DSGVO | Regulatorischer Aufwand wächst (NIS2, AI Act) |
| **Anpassungen / Konfiguration** | Laufende Änderungen, neue Workflows | Low-Code ≠ No-Cost |

#### D — Exit-/Migrationskosten (am Laufzeitende)

| Kostenposition | Berechnung | Versteckte Kosten |
|---|---|---|
| **Datenexport** | Aufwand für Export + Konvertierung | Proprietäre Formate, keine Bulk-API |
| **Transition Assistance** | Vom Anbieter berechnet (oft T&M) | Im Vertrag prüfen — oft nicht inkludiert |
| **Parallelbetrieb (Bridge)** | Doppelte Kosten für 3–6 Monate | Lizenzen laufen weiter bis Migration abgeschlossen |
| **Neues System aufbauen** | Implementierung Nachfolgelösung | Erfahrung aus altem System nutzbar? |

### 1.2 On-Premises-Lösung

#### A — Einmalkosten (Initial)

| Kostenposition | Berechnung | Versteckte Kosten |
|---|---|---|
| **Softwarelizenz** | Einmallizenz oder Subscription | Lizenzmodell-Wechsel (Perpetual → Subscription) |
| **Hardware / Infrastruktur** | Server, Storage, Netzwerk | Sizing für 5 Jahre vorausplanen → Überprovisionierung |
| **Virtualisierung / Container-Plattform** | VMware/Hyper-V/K8s Lizenzen | Lizenzkosten der Plattform selbst |
| **Implementierung / Customizing** | Dienstleistungstage × Tagessatz | Customizing-Aufwand oft 1,5–3× Lizenzkosten |
| **Datenmigration** | Komplexität × Volumen | Wie SaaS + zusätzlich Infrastruktur-Setup |
| **Integration** | Pro Schnittstelle × Aufwand | On-Prem-Integration oft komplexer (Firewall, VPN) |
| **Schulung** | Enduser + IT-Operations | IT-Ops-Training für Betrieb zusätzlich |
| **Projektmanagement** | Interner + externer Aufwand | Längere Projektlaufzeit = mehr PM-Aufwand |

#### B — Laufende Kosten (jährlich × 5)

| Kostenposition | Berechnung | Versteckte Kosten |
|---|---|---|
| **Wartung / Software-Support** | Typisch 18–22% der Lizenzkosten p.a. | Pflichtvoraussetzung für Updates und Patches |
| **Infrastruktur-Betrieb** | Strom, Kühlung, Rack-Space, Netzwerk | Anteilige Rechenzentrumskosten |
| **System-Administration** | FTE-Anteil (Patching, Monitoring, Backup) | 0,3–1,0 FTE je nach Komplexität |
| **Datenbank-Lizenz/-Wartung** | Oracle/MSSQL/PostgreSQL Support | DB-Lizenzkosten oft vergessen |
| **Backup & Disaster Recovery** | Storage, Replikation, DR-Standort | DR-Tests, Wiederherstellungszeiten |
| **Security-Updates & Patching** | Aufwand für Patch-Zyklen | Downtime-Fenster, Regressionstests |
| **Monitoring & Alerting** | Tool-Lizenzen + FTE-Anteil | Integration in zentrale Observability |
| **Compliance & Audit** | Jährliche Prüfungen, Dokumentation | ISO 27001 Rezertifizierung, Pentest |

#### C — Hardware-Refresh (im 5-Jahres-Zeitraum)

| Kostenposition | Berechnung | Versteckte Kosten |
|---|---|---|
| **Server-Refresh (nach 3–5 Jahren)** | Neue Hardware + Migration | Downtime, Kompatibilitätstests |
| **Storage-Erweiterung** | Zusätzliche Kapazität nach 2–3 Jahren | Datenwachstum oft unterschätzt |
| **Netzwerk-Upgrade** | Bei gestiegenem Traffic | Bandbreite, Firewall-Kapazität |

#### D — Exit-/Ablösekosten

| Kostenposition | Berechnung | Versteckte Kosten |
|---|---|---|
| **Rückbau Infrastruktur** | Decommissioning, Entsorgung | Datenlöschung (DSGVO-konform) |
| **Know-how-Verlust** | Wenn Fach-Admins nicht mehr verfügbar | Dokumentation oft unvollständig |
| **Datenexport** | Wie SaaS, aber Zugriff auf DB direkt | Komplexe Datenmodelle, historische Daten |

---

## 2. Versteckte Kostentreiber (beide Modelle)

| Kostentreiber | Beschreibung | Typischer Impact |
|---|---|---|
| **Preiserhöhungen (SaaS)** | 5–10% p.a. bei Vertragsverlängerung ohne Cap | +30–60% über 5 Jahre kumuliert |
| **Scope Creep** | Zusätzliche Anforderungen während Implementierung | +20–50% der Implementierungskosten |
| **User-Wachstum** | Mehr Nutzer als initial geplant | SaaS: linear; On-Prem: stufenweise (Lizenzpakete) |
| **Integrationsaufwand** | Schnittstellen zu Bestandssystemen | 1–3× so teuer wie erwartet |
| **Compliance-Aufwand** | DSGVO, NIS2, AI Act — wachsende Anforderungen | +10–20% der Betriebskosten |
| **Opportunitätskosten** | Interne IT-Ressourcen gebunden | On-Prem >> SaaS |
| **Produktivitätsverlust** | Einarbeitungszeit, Systemwechsel | 2–8 Wochen pro Rolle |
| **Vendor Lock-in Premium** | Anbieterwechsel wird teurer je länger man bleibt | Exponentiell mit Nutzungsdauer |

---

## 3. Ausgabeformate

### 3.1 TCO-Einzelbewertung (SaaS oder On-Prem)

```markdown
# TCO-Kalkulation: [Produktname] (5 Jahre)

## Parameter

| Parameter | Wert |
|---|---|
| Lösungstyp | SaaS / On-Premises |
| Betrachtungszeitraum | 5 Jahre (60 Monate) |
| Nutzeranzahl (Start → Jahr 5) | X → Y |
| Inflationsannahme | X% p.a. |
| Preiserhöhungsannahme (SaaS) | X% p.a. |
| Interner Stundensatz | € X |

## Kostenübersicht

| Kategorie | Jahr 1 | Jahr 2 | Jahr 3 | Jahr 4 | Jahr 5 | Gesamt |
|---|---|---|---|---|---|---|
| **Einmalkosten** | | — | — | — | — | |
| Lizenz / Setup | € | — | — | — | — | € |
| Implementierung | € | — | — | — | — | € |
| Migration | € | — | — | — | — | € |
| Schulung | € | — | — | — | — | € |
| **Laufende Kosten** | | | | | | |
| Abo / Wartung | € | € | € | € | € | € |
| Interner Betrieb | € | € | € | € | € | € |
| Support (extern) | € | € | € | € | € | € |
| Compliance | € | € | € | € | € | € |
| **Infrastruktur** ¹ | | | | | | |
| Hardware / Hosting | € | € | € | € | € | € |
| Hardware-Refresh | — | — | € | — | — | € |
| **Exit-Reserve** ² | | | | | | |
| Transition / Export | — | — | — | — | € | € |
| **Gesamt pro Jahr** | **€** | **€** | **€** | **€** | **€** | |
| **Kumuliert** | € | € | € | € | € | **€ TCO** |

¹ Nur On-Prem relevant. Bei SaaS in Abo-Kosten enthalten.
² Geschätzte Exit-Kosten als Reserve am Laufzeitende.

## Kostenverteilung

| Kategorie | Anteil | Betrag |
|---|---|---|
| Einmalkosten | X% | € |
| Laufende Kosten | X% | € |
| Infrastruktur | X% | € |
| Exit-Reserve | X% | € |
| **Total** | **100%** | **€ TCO** |

## Sensitivitätsanalyse

| Szenario | Veränderung | TCO-Impact |
|---|---|---|
| User +20% | X zusätzliche Nutzer ab Jahr 2 | +€ (+X%) |
| Preiserhöhung +10% p.a. | Statt X% p.a. | +€ (+X%) |
| Implementierung +30% | Scope Creep | +€ (+X%) |
| Hardware-Refresh früher (Jahr 3) | On-Prem only | +€ (+X%) |
```

### 3.2 TCO-Vergleich SaaS vs. On-Prem

```markdown
# TCO-Vergleich: [Produkt/Use Case]

## Parameter

| Parameter | SaaS-Lösung | On-Prem-Lösung |
|---|---|---|
| Produkt | [Name] | [Name] |
| Nutzer (Start → Jahr 5) | X → Y | X → Y |
| Preismodell | Per User/Monat | Perpetual + Wartung |

## 5-Jahres-Kostenvergleich

| Kategorie | SaaS | On-Prem | Delta |
|---|---|---|---|
| **Einmalkosten** | | | |
| Lizenz / Setup | € | € | € |
| Implementierung | € | € | € |
| Migration | € | € | € |
| Schulung | € | € | € |
| Hardware / Infra | — | € | € |
| *Summe Einmal* | *€* | *€* | *€* |
| **Laufende Kosten (5J)** | | | |
| Abo / Wartung | € | € | € |
| Interner Betrieb | € | € | € |
| Infrastruktur-Betrieb | — | € | € |
| Hardware-Refresh | — | € | € |
| Support | € | € | € |
| Compliance | € | € | € |
| *Summe Laufend* | *€* | *€* | *€* |
| **Exit-Reserve** | € | € | € |
| | | | |
| **TCO Gesamt (5 Jahre)** | **€** | **€** | **€** |
| **TCO pro User/Monat** | **€** | **€** | **€** |

## Break-Even-Analyse

| Kennzahl | Wert |
|---|---|
| SaaS günstiger bis | Jahr X (bei X Usern) |
| On-Prem günstiger ab | Jahr X (bei X Usern) |
| Break-Even-Punkt | X User / Monat Y |

## Nicht-monetäre Faktoren

| Faktor | SaaS | On-Prem |
|---|---|---|
| Time-to-Value | Wochen | Monate |
| Interne IT-Ressourcen | Gering | Hoch |
| Skalierungsflexibilität | Sofort | Hardware-abhängig |
| Kontrolle über Daten | Eingeschränkt | Vollständig |
| Update-Geschwindigkeit | Automatisch | Geplant |
| Vendor Lock-in Risiko | Hoch | Mittel |
| Compliance-Kontrolle | Geteilt | Vollständig |

## Empfehlung

[Kostenbasierte Empfehlung unter Berücksichtigung des Gesamtkontexts]
```

---

## 4. Kalkulationsregeln

### Preiserhöhungsprojektion (SaaS)

```
Jahr 1: Basispreis
Jahr N: Basispreis × (1 + Steigerungsrate)^(N-1)

Konservativ: 5% p.a. → 5 Jahre = Faktor 1,22 (= +22% auf Basispreis)
Realistisch: 7% p.a. → 5 Jahre = Faktor 1,40 (= +40% auf Basispreis)
Pessimistisch: 10% p.a. → 5 Jahre = Faktor 1,61 (= +61% auf Basispreis)
```

### User-Wachstumsprojektion

```
Linear:       Users_N = Users_Start + (Wachstum_p.a. × N)
Prozentual:   Users_N = Users_Start × (1 + Wachstumsrate)^N
```

### Interner Stundensatz (Vollkostenrechnung)

```
Interner Stundensatz = (Bruttojahresgehalt × 1,3 Lohnnebenkosten × 1,2 Overhead)
                       / (220 Arbeitstage × 8 Stunden × 0,8 Produktivitätsfaktor)

Beispiel:    (€ 70.000 × 1,3 × 1,2) / (220 × 8 × 0,8) = € 77,50 / Stunde
Vereinfacht: Bruttogehalt / 1.000 ≈ interner Stundensatz (Daumenregel)
```

### Infrastrukturkosten (On-Prem — pro Server/Jahr)

```
Typische Vollkosten pro physischem Server/Jahr (DACH):
- Strom + Kühlung:       € 1.500 – 3.000
- Rack-Space:            € 1.200 – 2.400
- Netzwerk-Anteil:       € 500 – 1.000
- Wartungsvertrag HW:    € 1.000 – 2.500
- Anteiliger Admin-FTE:  € 15.000 – 25.000

Gesamt pro Server/Jahr:  € 19.000 – 34.000

Bei Virtualisierung: pro VM typisch 20–40% eines physischen Servers
Bei Container/K8s: pro Workload typisch 10–25% eines physischen Servers
```
