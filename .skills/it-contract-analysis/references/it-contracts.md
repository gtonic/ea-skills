# IT-Verträge -- Klauselanalyse Referenz (EU/DACH)

Diese Referenz deckt die Klauselanalyse für IT-spezifische Vertragstypen im DACH-Raum ab.
Lese diese Datei bei der Prüfung von SaaS-, Cloud-, Outsourcing-, Implementierungs-,
Lizenz-, Hosting-, Wartungs- oder Beratungsverträgen.

## Inhaltsverzeichnis
1. SaaS / Cloud Subscription
2. Software-Lizenzverträge
3. IT-Systemintegration / Implementierung (Werkvertrag)
4. IT-Outsourcing / Managed Services
5. IT-Beratung (Dienstvertrag)
6. Hosting / Colocation
7. Wartungs- und Pflegeverträge
8. KI-/AI-Service-Verträge
9. IT-Template-Items (50-Punkte-Muster)
10. Red Flags Schnellreferenz

---

## 1. SaaS / Cloud Subscription

### Rechtliche Einordnung
SaaS-Verträge werden in der DACH-Rechtsprechung überwiegend als **Mietvertrag** (§ 535 BGB /
§ 1090 ABGB) mit dienstvertraglichen Elementen qualifiziert. Dies hat Konsequenzen:
- Mietrecht: Gewährleistung richtet sich nach Mietrecht (Mängelbeseitigung, Minderung)
- Kein Abnahmeerfordernis (anders als Werkvertrag)
- Ordentliche Kündigung nach § 580a BGB möglich, wenn vertraglich nicht ausgeschlossen

Neuere Rechtsprechung (BGH, OLG-Urteile) und Literatur tendieren bei Standard-SaaS zunehmend
zum **Dienstvertrag** (keine Gewährleistung für ein bestimmtes Werk, sondern für die laufende
Bemühung der Bereitstellung). Die Einordnung hängt vom konkreten Vertragsinhalt ab.

### Materielle Klauseln

#### Leistungsbeschreibung / Service Description
**Prüfe**: Funktionsumfang (Verweis auf Dokumentation?), Versionen-Politik, Feature-Roadmap bindend?,
Abgrenzung Standardfunktionalität vs. Customizing, Mandantenfähigkeit, Integrations-APIs.
**Red flags**: Leistungsbeschreibung nur per Verweis auf Website (kann einseitig geändert werden),
"Features subject to change", kein Versionsmanagement.

#### Verfügbarkeit / Uptime SLA
**Prüfe**: Verfügbarkeitszusage (99,5% / 99,9% / 99,95% / 99,99%), Messperiode (monatlich empfohlen),
Berechnung (Gesamtminuten minus geplante Wartung minus Ausfallminuten), geplante Wartungsfenster
(Dauer, Voranmeldefrist, Ausschluss Geschäftszeiten), Eskalationsstufen, Ausnahmen (höhere Gewalt,
Kundeninfrastruktur, Drittanbieter).
**Marktstandard**: 99,5% (Basis) bis 99,95% (geschäftskritisch). 99,99% nur bei High Availability.
**Red flags**: Keine numerische Verfügbarkeitszusage ("best efforts"), keine Messmethodik definiert,
Wartungsfenster ohne Vorankündigung, SLA gilt nicht für einzelne Module/APIs, Messperiode = jährlich
(verschleiert monatliche Ausfälle).

| Verfügbarkeit | Max. Ausfall/Monat | Max. Ausfall/Jahr | Einordnung |
|---|---|---|---|
| 99,0% | 7h 18min | 87h 36min | Niedrig -- nur für unkritische Systeme |
| 99,5% | 3h 39min | 43h 48min | Basis |
| 99,9% | 43min 50s | 8h 46min | Standard geschäftskritisch |
| 99,95% | 21min 55s | 4h 23min | Hoch |
| 99,99% | 4min 23s | 52min 36s | Sehr hoch (HA-Architektur erforderlich) |

#### Service Credits
**Prüfe**: Berechnungsmethode (% der Monatsgebühr pro SLA-Verletzung), Credit-Cap (typisch 10-30%
der Monatsgebühr), kumulativ oder pro Vorfall, Service Credit als einziger Rechtsbehelf oder
zusätzlich zu Schadensersatz, Eskalation von Credits zu Sonderkündigungsrecht.
**Red flags**: Credits <10% der Monatsgebühr (kein Anreiz), Credits als ausschließlicher
Rechtsbehelf (Schadensersatz ausgeschlossen -- in AGB nach § 309 Nr. 7 BGB problematisch wenn
Körperschäden oder Vorsatz/grobe Fahrlässigkeit betroffen), kein Eskalationspfad zu Kündigung,
Credits werden nur auf Antrag gewährt (nicht automatisch).

#### Datenhoheit und Datenlokalisierung
**Prüfe**: Eigentum/Hoheit an Kundendaten (Klarstellung, dass Daten dem Kunden gehören),
Verarbeitungsstandorte (EU/EWR?), Drittlandtransfer (SCCs, Angemessenheitsbeschluss),
Subprocessor-Standorte, Datenresidenz-Garantie (Daten verlassen EU/EWR nicht),
Verschlüsselung (at rest / in transit / Schlüsselmanagement).
**Red flags**: Keine Datenstandortgarantie, Datenverarbeitung in USA ohne SCCs/Angemessenheitsbeschluss,
Anbieter beansprucht Nutzungsrechte an Kundendaten (z.B. für Analytics, Training), keine
Verschlüsselung at rest, Kunden hat keinen Zugang zu Verschlüsselungsschlüsseln bei hochsensiblen Daten.

#### Exit / Datenmigration
**Prüfe**: Datenexport-Format (offenes, maschinenlesbares Format gem. Data Act Art. 23),
Export-Frist (wann nach Vertragsende?), Kosten für Datenexport (Data Act Art. 25: dürfen nicht
über Kosten hinausgehen), Transition Assistance (Dauer, Umfang), Bridge-Phase (Weiterbetrieb
während Migration), Löschungspflicht nach vollständigem Export.
**Red flags**: Kein Datenexport vorgesehen, nur proprietäres Format, Löschung sofort nach
Vertragsende ohne Exportfrist, keine Transition Assistance, Export nur gegen unverhältnismäßige
Gebühren (Verstoß gegen Data Act).

#### Einseitige Änderungsrechte
**Prüfe**: Änderung der Leistungsbeschreibung, Änderung der AGB/ToS, Änderung der Preise,
Vorankündigungsfrist, Widerspruchsrecht des Kunden, Sonderkündigungsrecht bei wesentlichen Änderungen.
**Red flags**: Einseitige Änderung der Leistung ohne Zustimmung (in AGB nach § 308 Nr. 4 BGB
Änderungsvorbehalt unzumutbar wenn nicht hinreichend bestimmt), keine Vorankündigung,
kein Sonderkündigungsrecht bei Verschlechterung, Preiserhöhung ohne Index-Bindung oder Cap.

---

## 2. Software-Lizenzverträge

### Rechtliche Einordnung
- **Kauf einer Standardsoftware-Kopie** (Download/Datenträger): Kaufvertrag (§ 433 BGB) nach
  BGH-Rechtsprechung (BGH, Urt. v. 18.10.2023 - I ZR 51/23 zu UsedSoft)
- **Zeitlich befristete Nutzungsüberlassung**: Mietvertrag oder Lizenzvertrag sui generis
- **Individualsoftware-Erstellung**: Werkvertrag (§ 631 BGB)

### Materielle Klauseln

#### Nutzungsrechte / License Scope
**Prüfe**: Nutzungsart (§ 31 UrhG: einfach/ausschließlich), räumlich (DACH/EU/weltweit),
zeitlich (unbefristet/befristet), inhaltlich (Named User / Concurrent / Site / Enterprise / CPU),
Bearbeitungsrecht (§ 69c Nr. 2 UrhG), Vervielfältigungsrecht (§ 69c Nr. 1 UrhG, Sicherungskopie
§ 69d Abs. 2 UrhG zwingend), Dekompilierung (§ 69e UrhG: zum Zweck der Interoperabilität zwingend
erlaubt).
**Red flags**: Nutzungsrechte erlöschen bei Kündigung des Wartungsvertrags (Lock-in), kein
Bearbeitungsrecht bei Individualsoftware (abhängig vom Anbieter), Audit-Klausel mit
unverhältnismäßigen Zugriffsrechten, True-Up-Mechanismus ohne Fairness-Grenzen.

#### Software-Audit
**Prüfe**: Audit-Häufigkeit, Vorankündigungsfrist (mind. 30 Tage), Umfang (nur lizenzierte Software),
Durchführung (durch Anbieter oder unabhängigen Dritten), Kosten (wer zahlt?), Konsequenzen bei
Unterlizenzierung, Datennutzung der Audit-Ergebnisse.
**Red flags**: Audit jederzeit ohne Vorankündigung, Anbieter hat unbeschränkten Zugang zu
Kundensystemen, Nachlizenzierung zu Listenpreisen (ohne Rabatte), Audit-Kosten trägt Kunde
auch bei Compliance.

#### Open Source Compliance
**Prüfe**: Open-Source-Offenlegung (Bill of Materials / SBOM), Copyleft-Komponenten (GPL, AGPL,
LGPL), Abgrenzung zu proprietärem Code, Indemnification bei Lizenzverletzung, SBOM-Aktualisierung.
**Red flags**: Keine Open-Source-Offenlegung, AGPL-Komponenten in SaaS ohne Offenlegung, keine
Freistellung bei IP-Verletzung durch Open-Source-Nutzung, Copyleft-Kontamination möglich.

#### Quellcode-Hinterlegung (Escrow)
**Prüfe**: Escrow-Agent (neutral, z.B. NCC Group, Iron Mountain), Hinterlegungsumfang (Source Code +
Build-Scripts + Dokumentation + Datenbank-Schemata), Herausgabebedingungen (Insolvenz,
Einstellung der Wartung, wesentlicher Vertragsbruch), Verifikation (regelmäßige Build-Prüfung),
Update-Pflicht (bei neuen Releases).
**Red flags**: Kein Escrow bei geschäftskritischer Individualsoftware, Herausgabe nur bei Insolvenz
(nicht bei Wartungseinstellung), keine Verifikation (Code kann veraltet/unbrauchbar sein).

---

## 3. IT-Systemintegration / Implementierung (Werkvertrag)

### Rechtliche Einordnung
IT-Implementierungsverträge sind in der Regel **Werkverträge** (§ 631 BGB / § 1165 ABGB).
Konsequenzen:
- **Abnahmepflicht** (§ 640 BGB): Auftraggeber muss das Werk abnehmen wenn es vertragsgemäß ist
- **Gefahrübergang** bei Abnahme
- **Verjährung der Gewährleistung** beginnt mit Abnahme (§ 634a BGB: 2 Jahre bei Standardsoftware)
- **Erfolgsbezogener Vergütungsanspruch**: Kein Erfolg = kein Vergütungsanspruch für den Werkteil

### Materielle Klauseln

#### Leistungsbeschreibung / Pflichtenheft
**Prüfe**: Detaillierungsgrad, funktionale vs. technische Spezifikation, Verantwortung für
Erstellung (Auftraggeber/Auftragnehmer/gemeinsam), Verbindlichkeit (Anlage zum Vertrag?),
Abgrenzung Soll/Ist, Mitwirkungspflichten des Auftraggebers.
**Red flags**: Kein Pflichtenheft bei Festpreis-Werkvertrag (unkontrollierbares Scope-Risiko),
"to be defined" im Pflichtenheft, widersprüchliche Anforderungen, keine Mitwirkungspflichten definiert.

#### Abnahme / Acceptance Testing
**Prüfe**: Abnahmeverfahren (formal mit Protokoll), Abnahmekriterien (messbar, aus Pflichtenheft
abgeleitet), Abnahmephasen (Teilabnahmen bei Meilensteinen), Abnahmefrist (typisch 14-30 Tage),
Testumgebung (Verantwortung), Testdaten, fiktive Abnahme (automatisch nach Fristablauf),
Mängelklassen (kritisch/schwer/leicht) und deren Einfluss auf Abnahme, Teilabnahme und
Gesamtabnahme, Vorbehalt bekannter Mängel bei Abnahme.
**Red flags**: Keine definierten Abnahmekriterien, fiktive Abnahme nach <5 Arbeitstagen, einzige
Mängelklasse (alles oder nichts), Abnahme ohne Testphase, Teilabnahme gilt als Gesamtabnahme.

#### Meilensteine und Vergütung
**Prüfe**: Meilensteinplan (realistisch?), Meilenstein-Zahlungen (an Abnahme geknüpft?),
Vorauszahlungen, Schlussrechnung nach Gesamtabnahme, Einbehalt bis Mängelbeseitigung.
**Red flags**: >50% Vorauszahlung ohne Sicherheit (Bankgarantie/Bürgschaft), Zahlung nicht an
Abnahme geknüpft, kein Einbehalt bei bekannten Mängeln.

#### Change Request Management
**Prüfe**: Formales Verfahren (schriftlicher CR), Bewertungsfrist (typisch 5-10 Arbeitstage),
Impact-Analyse (Kosten + Zeitplan), Genehmigung vor Umsetzung, Anpassung Pflichtenheft,
Eskalation bei Uneinigkeit, CR-Vergütungsmodell (Festpreis/T&M/Capped T&M).
**Red flags**: Kein CR-Verfahren, ANbieter kann CRs einseitig ablehnen, CRs nur auf T&M ohne Cap,
mündliche Änderungen ohne Dokumentation, keine Zeitplan-Anpassung bei CRs.

#### Projektgovernance
**Prüfe**: Lenkungsausschuss (Besetzung, Turnus, Entscheidungsbefugnis), Projektleiter beider
Seiten (namentlich benannt?), Berichtspflichten (Statusberichte, Format, Turnus), Eskalationsverfahren
(Stufen, Fristen), Risikomanagement, Kommunikationswege.
**Red flags**: Kein Lenkungsausschuss, Anbieter kann Projektleiter ohne Zustimmung austauschen,
keine regelmäßigen Statusberichte vertraglich vereinbart.

---

## 4. IT-Outsourcing / Managed Services

### Rechtliche Einordnung
IT-Outsourcing ist typischerweise ein **typengemischter Vertrag** (Dienstvertrag + werkvertragliche
Elemente). Oft als **Dauerschuldverhältnis** zu qualifizieren mit den Konsequenzen:
- Ordentliche Kündigung möglich (§ 314 BGB bei wichtigem Grund jederzeit)
- Transition-In/Out sind werkvertragliche Elemente (Abnahmepflicht)
- Laufender Betrieb ist dienstvertragliches Element

### Materielle Klauseln

#### Transition-In (Übernahme)
**Prüfe**: Transitionsplan, Due-Diligence-Phase, Personalübergang (§ 613a BGB Betriebsübergang?),
Knowledge Transfer, Zeitplan, Verantwortlichkeiten, Transformationsleistungen, Go-Live-Kriterien.
**Red flags**: Kein Transitionsplan, Personalübergang nicht adressiert, keine Knowledge-Transfer-Phase,
fixer Go-Live-Termin ohne Qualitäts-Gate, Transition-Kosten nicht gedeckelt.

#### Personalklauseln
**Prüfe**: Key Personnel (namentlich benannt?), Austausch-Verfahren (Zustimmung des Kunden),
Qualifikationsanforderungen, Abwerbungsverbot, Personalübergang bei Exit (Rück-Übernahme?),
Arbeitnehmerüberlassung (AÜG-Risiko bei Einsatz beim Kunden).
**Red flags**: Kein Key-Personnel-Schutz, Anbieter kann beliebig Personal austauschen,
Scheinselbständigkeits-Risiko (§ 7 SGB IV / § 4 Abs. 2 ASVG) nicht adressiert,
Arbeitnehmerüberlassung ohne AÜG-Erlaubnis.

#### Benchmarking
**Prüfe**: Benchmarking-Recht (ab Vertragsjahr 2-3), Benchmarker-Auswahl (unabhängig),
Vergleichsumfang, Anpassungsmechanismus bei über-Markt-Preisen, Anbieter-Gegenrecht (Match or Explain),
Kosten des Benchmarkings.
**Red flags**: Kein Benchmarking bei >3 Jahre Laufzeit, Anbieter wählt Benchmarker, Anpassung gedeckelt
oder verzögert, kein funktionaler Vergleich (nur Preis, nicht Leistung).

#### Step-In Rights
**Prüfe**: Auslösende Ereignisse, Ankündigungsfrist, Umfang (teilweise/vollständig), Kostenverteilung,
Datenzugang und Systemzugang während Step-In, Rückkehr zum Normalbetrieb.
**Red flags**: Kein Step-In-Recht bei kritischen Services, Step-In nur bei Insolvenz (nicht bei
SLA-Versagen), Anbieter kann Step-In durch Verweigerung von Zugang blockieren.

#### Exit / Transition-Out
**Prüfe**: Exit-Plan (vorab definiert), Transition-Assistance-Pflicht (Dauer: 6-12 Monate),
Vergütung während Exit, Datenrückgabe (Format, Frist), Personalrückübernahme-Option, Reverse
Knowledge Transfer, Bridge-Betrieb, Löschungspflicht nach Exit.
**Red flags**: Keine Exit-Regelung, Exit-Assistance nur 30 Tage, keine Datenrückgabe-Garantie,
Exit-Vergütung prohibitiv hoch (Vendor Lock-in), kein Reverse Knowledge Transfer.

---

## 5. IT-Beratung (Dienstvertrag)

### Rechtliche Einordnung
IT-Beratung ist grundsätzlich ein **Dienstvertrag** (§ 611 BGB / § 1151 ABGB), es sei denn ein
konkretes Ergebnis geschuldet wird (dann Werkvertrag). Konsequenzen:
- Kein Abnahmeerfordernis
- Vergütung für die Tätigkeit, nicht für den Erfolg
- Kündigung jederzeit möglich (§ 627 BGB bei Vertrauensverhältnis ohne Frist)

### Materielle Klauseln

#### Vergütungsmodell
**Prüfe**: Time & Material (T&M) vs. Festpreis vs. Capped T&M, Tagessatz/Stundensatz,
Reisekosten, Nebenkosten, Budgetrahmen/Cap, Abrechungsperioden, Rechnungsstellung und
Zahlungsfristen (§ 286 BGB: Verzug nach 30 Tagen).
**Red flags**: Open-ended T&M ohne Budget-Limit, Tagessätze ohne Leistungsdefinition, Abrechnung
in 15-Minuten-Takten (Aufrundungsrisiko), keine Leistungsnachweise/Timesheets.

#### Scheinselbständigkeit (§ 7 SGB IV / § 4 ASVG)
**Prüfe**: Weisungsfreiheit (oder faktische Eingliederung?), eigene Arbeitsmittel, Arbeitsort-Flexibilität,
Vertretungsmöglichkeit, wirtschaftliche Abhängigkeit, Tätigkeit für mehrere Auftraggeber.
**Red flags**: Berater arbeitet dauerhaft nur für einen Auftraggeber, vollständige Eingliederung
in Kundenorganisation, Weisungsgebundenheit, keine eigenen Arbeitsmittel, Vertretungsausschluss.

---

## 6. Hosting / Colocation

### Materielle Klauseln

#### Verfügbarkeit und Redundanz
**Prüfe**: Tier-Level des Rechenzentrums (Tier I-IV nach Uptime Institute), Verfügbarkeitszusage,
Redundanzkonzept (N+1, 2N), Stromabsicherung (USV, Dieselaggregate), Netzwerkredundanz.
**Red flags**: Kein Tier-Level genannt, keine Redundanz bei Strom/Netzwerk, SLA unter 99,9% für
geschäftskritische Systeme.

#### Physische Sicherheit und Zutritt
**Prüfe**: Zutrittskonzept (wer, wann, wie), Zutrittsprotokollierung, Begleitung, Videoüberwachung,
Voranmeldefrist, Notfallzutritt.
**Red flags**: Kundenzutritt nicht geregelt, keine Protokollierung, Anbieter-Mitarbeiter haben
uneingeschränkten Zugang zu Kundenhardware.

#### Datenlokalisierung
**Prüfe**: Standort(e) des Rechenzentrums, Backup-Standort, Replikationsstandort, EU/EWR-Garantie,
Zertifizierungen (ISO 27001, SOC 2 Type II, C5-Testat BSI).
**Red flags**: Kein festgelegter Standort, Daten können ohne Zustimmung in Drittländer repliziert
werden, keine ISO 27001 oder vergleichbare Zertifizierung.

---

## 7. Wartungs- und Pflegeverträge

### Rechtliche Einordnung
Typischerweise **gemischter Vertrag**:
- Fehlerbehebung = Werkvertrag (geschuldeter Erfolg: Fehler ist behoben)
- Support/Hotline = Dienstvertrag (Bemühen, Anfragen zu beantworten)
- Updates/Upgrades = hängt ab: Patches (werkvertraglich), neue Versionen (ggf. zusätzliche Lizenz)

### Materielle Klauseln

#### Support-Level und Reaktionszeiten
**Prüfe**: Support-Stufen (1st/2nd/3rd Level), Erreichbarkeit (5x8 / 7x24), Reaktionszeit vs.
Lösungszeit (unterschiedliche Begriffe!), Priorisierung (P1/P2/P3/P4), Wer klassifiziert?,
Eskalationswege, Workaround-Pflicht.
**Red flags**: Nur 1st-Level-Support ohne Zugang zu Entwicklern, keine Lösungszeit-SLA
("reasonable efforts"), Kunde kann Priorität nicht setzen, keine 24/7-Erreichbarkeit für kritische
Systeme, keine Workaround-Pflicht.

#### Updates, Upgrades und Patches
**Prüfe**: Definition (Security Patch / Bugfix / Minor Update / Major Upgrade), was ist im
Wartungsentgelt enthalten (typisch: Patches + Minor Updates), Major-Upgrade-Policy (separat
lizenziert?), Update-Pflicht des Anbieters (Sicherheitslücken), Kompatibilitätsgarantie,
Update-Plan/Roadmap.
**Red flags**: Keine Security-Patch-Pflicht, Major-Upgrades erzwingen Neulizenzierung, Updates
können bestehende Funktionalität entfernen, End-of-Life ohne Vorwarnfrist.

#### Abkündigungsschutz / End-of-Life
**Prüfe**: Vorwarnfrist bei Abkündigung (typisch 12-24 Monate), Extended Support Option,
Migrationspfad, Quellcode-Herausgabe bei Abkündigung (wenn Escrow vereinbart).
**Red flags**: Keine Vorwarnfrist, Abkündigung bedeutet Ende des Supports sofort, kein Migrationspfad,
Wartungsgebühr steigt bei Extended Support um >50%.

---

## 8. KI-/AI-Service-Verträge

### Rechtliche Einordnung
Noch nicht vollständig durch Rechtsprechung geklärt. Tendenz:
- KI-SaaS: Dienstvertrag/Mietvertrag (analog SaaS)
- KI-Modell-Erstellung: Werkvertrag (wenn konkretes Modell mit messbarer Qualität geschuldet)
- KI-Beratung: Dienstvertrag

### Materielle Klauseln

#### EU AI Act Compliance
**Prüfe**: Risikoklassifizierung (verboten / hochrisiko / begrenzt / minimal), Anforderungen je
Risikoklasse (Art. 6ff EU AI Act), CE-Konformitätskennzeichnung bei Hochrisiko, technische
Dokumentation (Art. 11), menschliche Aufsicht (Art. 14), Transparenzpflichten (Art. 52: Nutzer
müssen wissen, dass sie mit KI interagieren), Registrierungspflicht (EU-Datenbank).
**Red flags**: Keine Risikoklassifizierung im Vertrag, Hochrisiko-KI ohne Konformitätsbewertung,
keine menschliche Aufsicht vorgesehen, keine Transparenz gegenüber Endnutzern.

#### Haftung bei KI-Entscheidungen
**Prüfe**: Wer haftet für fehlerhafte KI-Outputs (Anbieter, Nutzer, gemeinsam)?, Haftungscap
für KI-spezifische Schäden, Beweislastverteilung (EU KI-Haftungsrichtlinie: Beweislasterleichterung
bei Verstoß gegen AI Act), Versicherung für KI-Risiken.
**Red flags**: Vollständiger Haftungsausschluss für KI-Outputs, keine Beweislastverteilungs-Regelung,
kein Haftungscap (unbeschränkte Haftung des Nutzers für KI-Ergebnisse), keine Versicherung.

#### Trainingsdaten und Datenschutz
**Prüfe**: Werden Kundendaten für Training verwendet?, Opt-Out-Möglichkeit, DSGVO-Rechtsgrundlage
für Training (Art. 6 DSGVO), Anonymisierung/Pseudonymisierung, Urheberrechts-Compliance der
Trainingsdaten, Ergebniseigentum (wem gehören KI-generierte Outputs?).
**Red flags**: Anbieter trainiert mit Kundendaten ohne Zustimmung, kein Opt-Out, keine
DSGVO-Rechtsgrundlage für Training, unklares Eigentum an KI-generierten Outputs.

---

## 9. IT-Template-Items (50-Punkte-Muster)

Dieses Template deckt die wesentlichen Prüfpunkte für IT-Verträge im DACH-Raum ab.
Verwende es als Checkliste für template-driven Reviews.

### Vertragliche Grundlagen (Items 1-8)
1. Vertragstyp (rechtliche Qualifikation: Werk-/Dienst-/Miet-/Lizenzvertrag)
2. Vertragsparteien (korrekte Firmierung, Vertetungsbefugnis)
3. Anwendbares Recht und Gerichtsstand
4. Vertragslaufzeit und Verlängerung
5. Ordentliche Kündigung (Frist, Form)
6. Außerordentliche Kündigung (wichtiger Grund, Nachfrist)
7. Schriftformklausel / Form der Änderung
8. AGB oder Individualvereinbarung (Einbeziehung, Vorrang)

### Leistung und Vergütung (Items 9-18)
9. Leistungsbeschreibung / Pflichtenheft
10. Leistungsabgrenzung (was ist nicht im Scope)
11. Vergütungsmodell (Festpreis / T&M / Subscription)
12. Preisanpassungsmechanismus (Index, Cap, Häufigkeit)
13. Zahlungsbedingungen (Fälligkeit, Verzug)
14. Meilensteine und Teilzahlungen (bei Werkvertrag)
15. Change Request Verfahren
16. Mitwirkungspflichten des Auftraggebers
17. Personal und Key Personnel
18. Subunternehmer-Einsatz (Genehmigungspflicht)

### Qualität und Abnahme (Items 19-26)
19. Abnahmekriterien und -verfahren (bei Werkvertrag)
20. Abnahmefrist und fiktive Abnahme
21. Service Level Agreements (SLA)
22. Verfügbarkeit und Messmethodik
23. Service Credits und Rechtsbehelfe
24. Eskalationsverfahren bei SLA-Verletzung
25. Reporting und Berichtspflichten
26. Benchmarking-Recht (bei >3 Jahre Laufzeit)

### Gewährleistung und Haftung (Items 27-33)
27. Gewährleistungsfrist und -umfang
28. Mängelrechte (Nacherfüllung, Minderung, Rücktritt)
29. Haftungshöchstbetrag (Cap)
30. Haftungsausschlüsse (zulässig unter DACH-Recht?)
31. Kardinalpflichten-Vorbehalt
32. Vertragsstrafe (§§ 339ff BGB)
33. Freistellung (IP-Verletzung, Datenschutz)

### Datenschutz und Sicherheit (Items 34-40)
34. Auftragsverarbeitungsvertrag (AVV) gem. Art. 28 DSGVO
35. Technisch-organisatorische Maßnahmen (TOMs)
36. Sub-Processor Management (Genehmigung, Widerspruch)
37. Datenlokalisierung (EU/EWR-Garantie)
38. Drittlandtransfer (SCCs, Angemessenheitsbeschluss)
39. Meldepflicht bei Datenschutzverletzungen (72h)
40. NIS2-Sicherheitsanforderungen und Meldepflichten

### Geistiges Eigentum (Items 41-44)
41. IP-Zuordnung (Background / Foreground IP)
42. Nutzungsrechte (Umfang, Dauer, Bearbeitungsrecht)
43. Open-Source-Compliance (SBOM, Copyleft)
44. Quellcode-Hinterlegung (Escrow)

### Vertragsbeendigung und Exit (Items 45-50)
45. Exit-Management und Transition Assistance
46. Datenherausgabe (Format, Frist, Kosten)
47. Löschungspflicht nach Vertragsende
48. Bridge-Betrieb während Transition
49. Übergangsregelungen für Lizenzen und Zugänge
50. Abtretung und Change of Control

---

## 10. Red Flags Schnellreferenz

### Sofort eskalieren (RED / CRITICAL)
- Kein AVV bei Verarbeitung personenbezogener Daten
- Vollständiger Haftungsausschluss für Vorsatz/grobe Fahrlässigkeit (§ 276 Abs. 3 BGB: nichtig)
- Datenverarbeitung in Drittland ohne Rechtsgrundlage
- Werkvertrag ohne Abnahmekriterien und Festpreis >100k EUR
- Keine Exit-/Datenherausgabe-Regelung bei Lock-in-gefährdeten Services
- AGB mit einseitigem Änderungsrecht für wesentliche Leistungsbestandteile
- Kein Kündigungsrecht bei Dauerschuldverhältnis >2 Jahre
- Copyleft-Kontamination (GPL/AGPL) ohne Offenlegung
- NIS2-pflichtige Einrichtung ohne Sicherheitsklauseln im IT-Vertrag
- Hochrisiko-KI ohne EU AI Act Konformitätsbewertung

### Verhandeln (YELLOW / MEDIUM-HIGH)
- SLA unter Marktstandard für die Kritikalität
- Service Credits als einziger Rechtsbehelf
- Wartungsfenster in Geschäftszeiten
- Kein Benchmarking bei Laufzeit >3 Jahre
- Preisanpassung >CPI ohne Cap
- Key Personnel nicht namentlich benannt
- Kein Escrow bei Individualsoftware
- Change Requests nur auf T&M ohne Cap
- Automatische Vertragsverlängerung ohne Hinweispflicht
- Nutzungsrechte erlöschen bei Kündigung Wartungsvertrag
