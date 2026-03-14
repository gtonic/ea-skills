# DACH Zivilrechtliches Framework für IT-Verträge

Diese Referenz deckt die zivilrechtlichen Grundlagen für IT-Verträge im DACH-Raum ab.
Lese diese Datei, wenn die rechtliche Einordnung eines IT-Vertrags, AGB-Kontrolle,
Gewährleistungsfragen oder Schadensersatzbewertungen relevant sind.

## Inhaltsverzeichnis
1. Vertragstypen-Qualifikation (IT-spezifisch)
2. AGB-Recht und Inhaltskontrolle
3. Gewährleistungsrecht
4. Schadensersatz und Haftung
5. Vertragsstrafe
6. Kündigung und Beendigung
7. Vergaberecht und öffentliche IT-Beschaffung
8. Länderspezifische Besonderheiten (AT, DE, CH)

---

## 1. Vertragstypen-Qualifikation (IT-spezifisch)

Die rechtliche Einordnung eines IT-Vertrags bestimmt, welche gesetzlichen Regelungen gelten.
Im DACH-Raum ist die Unterscheidung zwischen Werkvertrag und Dienstvertrag fundamental.

### Werkvertrag (§ 631 BGB / § 1165 ABGB / Art. 363 OR)
**Geschuldet**: Konkreter Erfolg (ein funktionierendes, spezifiziertes System/Werk)
**Konsequenzen**:
- Abnahmepflicht und -recht (§ 640 BGB)
- Gewährleistung beginnt mit Abnahme
- Vergütung bei Nicht-Erfolg fraglich
- Mängelrechte: Nacherfüllung → Selbstvornahme → Rücktritt/Minderung → Schadensersatz
- Kündigung: Besteller kann jederzeit kündigen (§ 648 BGB), schuldet aber vereinbarte Vergütung
  abzgl. ersparter Aufwendungen

**IT-typische Werkverträge**:
- Erstellung von Individualsoftware
- Systemintegration/Implementierung eines ERP/CRM/etc.
- Erstellung eines Pflichtenhefts (wenn als eigenständiger Werkvertrag beauftragt)
- Datenmigration (konkreter, messbarer Erfolg)
- Website-/App-Entwicklung

### Dienstvertrag (§ 611 BGB / § 1151 ABGB / Art. 319 OR)
**Geschuldet**: Tätigkeit/Bemühung (nicht aber ein konkreter Erfolg)
**Konsequenzen**:
- Keine Abnahme
- Vergütung für die Tätigkeit (auch wenn Erfolg ausbleibt)
- Kündigung jederzeit möglich (§ 621 BGB; bei Vertrauensverhältnis: § 627 BGB ohne Frist)
- Keine werkvertragliche Gewährleistung, aber Schlechtleistung → Schadensersatz

**IT-typische Dienstverträge**:
- IT-Beratung / Consulting
- Support / Hotline (2nd/3rd Level)
- Managed Services (laufender IT-Betrieb)
- Schulung / Training
- IT-Projektmanagement (wenn kein Ergebnis geschuldet)

### Mietvertrag (§ 535 BGB / § 1090 ABGB)
**Geschuldet**: Gebrauchsüberlassung einer Sache auf Zeit
**Konsequenzen**:
- Mietrechtliche Gewährleistung (Mängelbeseitigung, Minderung §§ 535, 536 BGB)
- Vermieter muss Sache in gebrauchsfähigem Zustand erhalten
- Keine Abnahme
- Kündigung nach Mietrecht (§ 580a BGB)

**IT-typische Mietverträge**:
- SaaS (herrschende Meinung, BGH tendiert zur Mietqualifikation)
- Hardware-Leasing
- Hosting (Serverkapazität als Gebrauchsüberlassung)

### Gemischte Verträge
Die meisten IT-Verträge kombinieren Elemente. Einordnung nach dem **Schwerpunkt** der Leistung
oder **Trennungstheorie** (jeder Leistungsteil wird nach seinem Typ beurteilt):

| Vertrag | Anteile |
|---|---|
| IT-Outsourcing | Transition (Werk) + Run (Dienst) + Hosting (Miete) |
| Wartungsvertrag | Fehlerbehebung (Werk) + Support (Dienst) + Updates (Werk/Lizenz) |
| Cloud mit Implementierung | Setup (Werk) + SaaS-Nutzung (Miete/Dienst) + Customizing (Werk) |

### Entscheidungsbaum Vertragstyp
```
Wird ein konkretes, messbares Ergebnis geschuldet?
  → JA → Werkvertrag
    → Abnahme, Gewährleistung (§ 634a BGB), Vergütung erst bei Erfolg
  → NEIN → Wird eine Sache zur zeitweisen Nutzung überlassen?
    → JA → Mietvertrag
      → Gebrauchserhaltungspflicht, Mietminderung, Mietrecht-Kündigung
    → NEIN → Dienstvertrag
      → Tätigkeit geschuldet, keine Abnahme, Schlechtleistung → SE
```

---

## 2. AGB-Recht und Inhaltskontrolle

### Grundsatz
Allgemeine Geschäftsbedingungen (AGB) unterliegen einer strengen Inhaltskontrolle, die es im
Common Law (UK/US) in dieser Form nicht gibt. Dies ist einer der größten Unterschiede zum
bestehenden Contract Analysis Skill.

### Deutschland (§§ 305-310 BGB)

#### Einbeziehungskontrolle (§ 305 Abs. 2 BGB)
AGB werden nur Vertragsbestandteil, wenn der Verwender:
1. Bei Vertragsschluss ausdrücklich auf sie hinweist
2. Der anderen Partei die Möglichkeit gibt, in zumutbarer Weise Kenntnis zu nehmen
3. Die andere Partei mit ihrer Geltung einverstanden ist

**IT-Praxis**: AGB per Link in der E-Mail-Signatur reicht NICHT. AGB müssen aktiv zur Kenntnis
gebracht werden.

#### Überraschende Klauseln (§ 305c BGB)
Klauseln, die so ungewöhnlich sind, dass der Vertragspartner nicht mit ihnen zu rechnen braucht,
werden nicht Vertragsbestandteil.
**IT-Beispiel**: Eine Klausel in einem SaaS-AGB, die dem Anbieter erlaubt, Kundendaten für eigene
Zwecke zu nutzen, ist überraschend und unwirksam.

#### Klauselverbote ohne Wertungsmöglichkeit (§ 309 BGB) -- Immer unwirksam:
- **Nr. 7a**: Haftungsausschluss für Körperschäden durch leichte Fahrlässigkeit
- **Nr. 7b**: Haftungsausschluss für sonstige Schäden bei grober Fahrlässigkeit
- **Nr. 8a**: Ausschluss des Rücktrittsrechts bei Mängeln (Werkvertrag)
- **Nr. 8b (ff)**: Beschränkung der Nacherfüllung auf eine Art (nur Reparatur ODER Ersatzlieferung)
- **Nr. 9**: Vertragslaufzeit >2 Jahre bei Dauerschuldverhältnis (B2C)
- **Nr. 12**: Beweislastumkehr zu Lasten des Vertragspartners

#### Klauselverbote mit Wertungsmöglichkeit (§ 308 BGB) -- Im Einzelfall unwirksam:
- **Nr. 4**: Änderungsvorbehalt (in AGB nur wirksam, wenn hinreichend bestimmt und zumutbar)
- **Nr. 5**: Fingierte Erklärungen (fiktive Abnahme nur, wenn angemessene Frist + Hinweis)
- **Nr. 6**: Fiktion des Zugangs

#### Generalklausel (§ 307 BGB) -- Unwirksam bei unangemessener Benachteiligung:
Eine Klausel ist unwirksam, wenn sie den Vertragspartner entgegen den Geboten von Treu und
Glauben unangemessen benachteiligt. Insbesondere wenn:
- Sie mit wesentlichen Grundgedanken der gesetzlichen Regelung nicht vereinbar ist
- Sie wesentliche Rechte oder Pflichten einschränkt, die sich aus der Natur des Vertrags ergeben

**BGH-Rechtsprechung für IT-Verträge**:
- Haftungsbeschränkung in AGB nur wirksam mit Vorbehalt für Kardinalpflichten (wesentliche
  Vertragspflichten) und Vorsatz/grobe Fahrlässigkeit
- Pauschalierter Schadensersatz in AGB: Muss Möglichkeit des Nachweises eines geringeren Schadens
  vorsehen (§ 309 Nr. 5 BGB)
- Gerichtsstandsklausel: Bei B2B in AGB grundsätzlich zulässig

### Österreich (§ 879 ABGB, KSchG)

#### § 879 Abs. 3 ABGB (Gröbliche Benachteiligung)
AGB-Klauseln sind unwirksam, wenn sie den Vertragspartner **gröblich benachteiligen**.
Maßstab: objektive Äquivalenzstörung oder Verdünnung der Hauptleistung.

#### Konsumentenschutzgesetz (KSchG)
Gilt im B2C-Verkehr. Wesentliche Bestimmungen:
- **§ 6 KSchG**: Katalog unwirksamer Klauseln (vergleichbar § 309 BGB, aber mit Besonderheiten)
- **§ 6 Abs. 1 Z 1 KSchG**: Ausschluss der Gewährleistung unwirksam
- **§ 6 Abs. 1 Z 9 KSchG**: Ungewöhnlich lange Bindungsfristen unwirksam
- **§ 6 Abs. 3 KSchG**: Unklare/unlesbare Klauseln gehen zu Lasten des Verwenders

Auch im **B2B-Bereich** wendet die österreichische Rechtsprechung die Generalklausel des § 879
Abs. 3 ABGB streng an.

### Schweiz (OR)

#### Kein eigenständiges AGB-Gesetz
Die Schweiz hat kein mit §§ 305ff BGB vergleichares AGB-Recht. Stattdessen:
- **Art. 8 UWG**: Unzulässige AGB bei einem erheblichen und ungerechtfertigten Missverhältnis
  (seit 2012, eingeführt durch die UWG-Revision)
- **Ungewöhnlichkeitsregel**: Überraschende Klauseln werden nicht Vertragsbestandteil
  (BGE 135 III 1 E. 2.1)
- **Unklarheitenregel**: Unklare Klauseln gehen zu Lasten des Verwenders

#### Praxistipp Schweiz
Die AGB-Kontrolle ist in der Schweiz schwächer als in DE/AT. Dennoch: Grob unbillige Klauseln
können über Art. 8 UWG oder Art. 2 ZGB (Treu und Glauben) angegriffen werden.

### AGB vs. Individualvereinbarung -- Abgrenzungskriterien
| Kriterium | AGB | Individualvereinbarung |
|---|---|---|
| Vorformuliert | Ja, für Vielzahl von Verträgen | Nein, individuell ausgehandelt |
| Verhandelbar | Nein, "take it or leave it" | Ja, tatsächlich verhandelt |
| Beweislast | Verwender muss beweisen, dass individuell ausgehandelt | Angreifender muss AGB-Eigenschaft beweisen |
| Inhaltskontrolle | Ja (§§ 305ff BGB / § 879 ABGB) | Nur §§ 134, 138 BGB (Sittenwidrigkeit, Gesetzesverstoß) |

**IT-Praxis**: Die meisten IT-Anbieterverträge sind AGB, auch wenn als "Vertrag" tituliert.
Selbst wenn einzelne Klauseln verhandelt wurden, sind die übrigen Klauseln weiterhin AGB.
Nur die konkret ausgehandelte Klausel ist Individualvereinbarung.

---

## 3. Gewährleistungsrecht

### Deutschland (BGB)

#### Werkvertrag (§§ 633-639 BGB)
- **Mangelbegriff** (§ 633 BGB): Abweichung von vereinbarter Beschaffenheit (subjektiver Mangel)
  oder von üblicher Beschaffenheit (objektiver Mangel, seit 1.1.2022 Reform)
- **Mängelrechte** (§ 634 BGB): Nacherfüllung (§ 635) → Selbstvornahme (§ 637) → Rücktritt/Minderung
  (§ 638) → Schadensersatz (§ 636)
- **Verjährung** (§ 634a BGB):
  - 2 Jahre ab Abnahme (Standardsoftware, IT-Systeme)
  - 5 Jahre ab Abnahme bei Bauwerken (relevant bei fest eingebauter Gebäudetechnik)
  - 3 Jahre ab Kenntnis bei arglistig verschwiegenen Mängeln
- **Verkürzte Verjährung in AGB**: Nur bei B2B wirksam, nicht unter 1 Jahr (BGH-Rechtsprechung),
  bei B2C gesetzliche Frist nicht verkürzbar (§ 309 Nr. 8b BGB)

#### Kaufvertrag (§§ 433-479 BGB) -- für Standardsoftware-Kauf
- **Mangelbegriff** (§ 434 BGB): Subjektiver + objektiver Mangel (seit Reform 1.1.2022: beide
  müssen kumulativ erfüllt sein)
- **Verjährung**: 2 Jahre ab Lieferung (§ 438 BGB)
- **Beweislastumkehr**: Bei Verbrauchern 1 Jahr (§ 477 BGB, seit Reform 2022)

### Österreich (ABGB)

#### Gewährleistung (§§ 922-933b ABGB)
- **Mangelbegriff** (§ 922 ABGB): Sach- und Rechtsmangel, bedungene und gewöhnlich vorausgesetzte
  Eigenschaften
- **Rechte**: Verbesserung/Austausch (Primärbehelfe) → Preisminderung/Wandlung (Sekundärbehelfe)
- **Verjährung**: **3 Jahre** ab Übergabe bei beweglichen Sachen (§ 933 ABGB) -- länger als in DE!
  30 Jahre bei unbeweglichen Sachen
- **Vermutungsfrist**: 6 Monate ab Übergabe wird vermutet, dass Mangel bereits bei Übergabe
  vorlag (§ 924 ABGB). Bei Verbrauchern seit 1.1.2022: 12 Monate.
- **Keine Abnahmeregelung** im ABGB vergleichbar § 640 BGB, aber faktische Übernahme wirkt ähnlich

### Schweiz (OR)

#### Werkvertrag (Art. 363-379 OR)
- Abnahme und Prüfungspflicht (Art. 367 OR)
- Mängelrüge **unverzüglich** nach Entdeckung (Art. 367 Abs. 1 OR) -- bei verspäteter Rüge:
  Anspruchsverlust!
- Verjährung: 2 Jahre ab Abnahme (Art. 371 OR), bei unbeweglichen Werken: 5 Jahre
- Rechte: Wandlung oder Minderung (Art. 368 OR), Nachbesserung nur bei entsprechender Vereinbarung

#### Kaufrecht (Art. 197-210 OR)
- Prüfungs- und Rügepflicht (Art. 201 OR): Käufer muss Sache **sofort** prüfen und Mängel
  **unverzüglich** rügen (im Handelsverkehr streng gehandhabt)
- Verjährung: 2 Jahre ab Lieferung (Art. 210 OR)

### Gewährleistung in IT-Verträgen -- Praxisregeln
| Thema | DE | AT | CH |
|---|---|---|---|
| Werkvertrag-Verjährung | 2 Jahre ab Abnahme | 3 Jahre ab Übergabe | 2 Jahre ab Abnahme |
| Kaufvertrag-Verjährung | 2 Jahre ab Lieferung | 3 Jahre ab Übergabe | 2 Jahre ab Lieferung |
| Rügepflicht | Keine (außer Kaufrecht im Handelsverkehr (§ 377 HGB)) | § 377 UGB (Handelsverkehr) | Strenge Rügepflicht (Art. 201, 367 OR) |
| Verkürzung in AGB (B2B) | Möglich, min. 1 Jahr | Stark eingeschränkt (§ 879 ABGB) | Grundsätzlich möglich |
| Verkürzung in AGB (B2C) | Nicht unter gesetzl. Minimum | Nicht zulässig (§ 9 KSchG) | Eingeschränkt (Art. 8 UWG) |
| Beweislastumkehr (B2C) | 12 Monate (seit 2022) | 12 Monate (seit 2022) | Keine gesetzliche |

---

## 4. Schadensersatz und Haftung

### Grundlegende Unterschiede zum Common Law
Im DACH-Recht gibt es **keine Unterscheidung zwischen "direct" und "consequential/indirect damages"**
wie im Common Law. Stattdessen:

- **Adäquanztheorie**: Ersatzfähig sind Schäden, die nach der allgemeinen Lebenserfahrung als Folge
  des schädigenden Ereignisses zu erwarten waren (adäquater Kausalzusammenhang)
- **Schutzzweck der Norm**: Ersatzfähig nur, soweit der eingetretene Schaden im Schutzbereich der
  verletzten Pflicht liegt
- **Voller Schadensausgleich**: Der Geschädigte ist so zu stellen, wie er ohne das schädigende
  Ereignis stehen würde (§§ 249ff BGB / §§ 1293ff ABGB)
- **Kein Strafschadensersatz** (punitive damages): Im DACH-Recht ausgeschlossen

### Vertragliche Haftungsbeschränkungen

#### Nicht ausschließbar (zwingend):
- **Vorsatz** (§ 276 Abs. 3 BGB / § 1294 ABGB): IMMER vollumfänglich haftbar
- **Grobe Fahrlässigkeit**: In AGB nicht ausschließbar (§ 309 Nr. 7b BGB)
- **Körper-/Lebensschäden**: In AGB nicht ausschließbar, auch bei leichter Fahrlässigkeit
  (§ 309 Nr. 7a BGB)
- **Arglistiges Verschweigen von Mängeln**: Haftung nicht ausschließbar

#### Standard-Haftungsklausel für IT-Verträge (DACH-konform):
Eine wirksame Haftungsklausel in IT-AGB muss typischerweise enthalten:
1. Unbeschränkte Haftung für Vorsatz, grobe Fahrlässigkeit, Körper-/Lebensschäden
2. Bei leichter Fahrlässigkeit: Haftung beschränkt auf "wesentliche Vertragspflichten"
   (Kardinalpflichten) -- begrenzt auf den vertragstypisch vorhersehbaren Schaden
3. Haftungshöchstbetrag (Cap) für sonstige Schäden
4. Keine Unterscheidung "direct/indirect damages" (DACH-fremd)

**BGH-Formel** ("Kardinalpflicht-Vorbehalt"): In AGB ist eine Haftungsbeschränkung nur wirksam,
wenn sie die Haftung für die Verletzung wesentlicher Vertragspflichten (deren Erfüllung die
ordnungsgemäße Durchführung des Vertrags überhaupt erst ermöglicht und auf deren Einhaltung der
Vertragspartner regelmäßig vertrauen darf) auf den vertragstypisch vorhersehbaren Schaden begrenzt.

### Typische Haftungscaps in IT-Verträgen (Marktstandard DACH)
| Vertragswert | Üblicher Cap | Bemerkung |
|---|---|---|
| <100k EUR | 1-2x Gesamtvergütung | Minimum: Jahresentgelt |
| 100k-500k EUR | 1x Jahresentgelt | Oft Klausel "je Schadensfall und gesamt" |
| 500k-2M EUR | 1x Jahresentgelt oder Festbetrag | Separate Caps für Datenschutz möglich |
| >2M EUR | Individuell verhandelt | Oft gestaffelt nach Schadensart |

### Vertragsstrafe (§§ 339-345 BGB / § 1336 ABGB)
Im DACH-Recht (anders als im Common Law, wo "penalties" unwirksam sind) ist die Vertragsstrafe
ein anerkanntes und übliches Instrument:
- **Zulässigkeit**: Grundsätzlich wirksam, auch in AGB (mit Grenzen)
- **AGB-Grenze**: Vertragsstrafe darf nicht unverhältnismäßig hoch sein (5% des betroffenen
  Auftragswerts als Richtwert, max. 10% gesamt nach BGH-Rechtsprechung für Bauverträge,
  auf IT übertragbar)
- **Richterliches Mäßigungsrecht** (§ 343 BGB / § 1336 Abs. 2 ABGB): Gericht kann
  unverhältnismäßig hohe Vertragsstrafe herabsetzen
- **IT-Praxis**: Vertragsstrafen bei Meilensteinverzug (0,2-0,5% pro Woche Verzug, Cap 5%),
  bei SLA-Verstößen (Service Credits als qualifizierte Vertragsstrafe)

### Verschuldensvermutung bei Vertragsverletzung
- **DE** (§ 280 Abs. 1 S. 2 BGB): Schuldner muss beweisen, dass er die Pflichtverletzung nicht
  zu vertreten hat (Beweislastumkehr zugunsten des Gläubigers)
- **AT** (§ 1298 ABGB): Ebenso Beweislastumkehr bei vertraglicher Haftung
- **CH** (Art. 97 OR): Schuldner muss sich exkulpieren

---

## 5. Kündigung und Beendigung

### Ordentliche Kündigung
| Vertragstyp | DE | AT | CH |
|---|---|---|---|
| Werkvertrag | § 648 BGB: Besteller kann jederzeit kündigen (muss aber vereinbarte Vergütung minus ersparte Aufwendungen zahlen) | § 1168 ABGB: Besteller kann vor Vollendung ("jederzeit") | Art. 377 OR: Schadenersatz |
| Dienstvertrag | § 621 BGB: Frist abhängig von Vergütungsperiode | § 1158 ABGB: Fristen je nach Dauer | Art. 337 OR: fristlos bei wichtigem Grund |
| Mietvertrag (SaaS) | § 580a BGB: Frist je nach Mietperiode | § 560 ZPO + ABGB | Art. 266a OR: 6 Monate |

### Außerordentliche Kündigung (wichtiger Grund)
- **§ 314 BGB / § 1117 ABGB**: Dauerschuldverhältnisse können aus wichtigem Grund jederzeit
  gekündigt werden. Dies ist **zwingendes Recht** und kann vertraglich nicht ausgeschlossen werden.
- **Nachfrist**: Grundsätzlich erforderlich, es sei denn, die Nachfrist ist aussichtslos oder
  der Vertragsbruch so schwer, dass die Fortsetzung unzumutbar ist.
- **IT-typische wichtige Gründe**: Andauernde SLA-Verletzung trotz Nachfrist, Datenschutzverletzung,
  Insolvenz, wesentliche Vertragsverletzung.

### Automatische Verlängerung
- **B2C (§ 309 Nr. 9 BGB)**: Erstlaufzeit max. 2 Jahre, Verlängerung max. 1 Jahr, Kündigung
  3 Monate vor Ablauf. Gilt auch für SaaS im B2C-Bereich.
- **B2B**: Grundsätzlich frei vereinbar, aber unangemessene Bindung über § 307 BGB / § 879 ABGB
  angreifbar.
- **Hinweispflicht**: Seit 1.3.2022 in DE: Unternehmer müssen Verbraucher vor automatischer
  Verlängerung rechtzeitig hinweisen, sonst ist jederzeit kündbar (§ 309 Nr. 9 BGB nF).

---

## 6. Vergaberecht und öffentliche IT-Beschaffung

### EU-Vergaberichtlinien
- **RL 2014/24/EU** (klassische Vergabe): Ab Schwellenwert 143.000 EUR (zentrale Regierungsstellen)
  bzw. 221.000 EUR (sonstige öffentliche Auftraggeber)
- **RL 2014/25/EU** (Sektorenauftraggeber): Schwellenwert 443.000 EUR

### Deutschland: EVB-IT
Die **Ergänzenden Vertragsbedingungen für die Beschaffung von IT-Leistungen** sind der Standard
für öffentliche IT-Beschaffung in Deutschland:

| EVB-IT-Muster | Anwendungsfall |
|---|---|
| EVB-IT Kauf | Standardsoftware-Kauf |
| EVB-IT Überlassung Typ A | Zeitlich befristete Überlassung gegen Einmalvergütung |
| EVB-IT Überlassung Typ B | Zeitlich befristete Überlassung gegen wiederkehrende Vergütung |
| EVB-IT Dienstleistung | IT-Beratung, Support, Schulung |
| EVB-IT System | Systemlieferung (Hardware + Software + Integration) |
| EVB-IT Systemlieferung | Komplexe Systemlieferung mit Implementierung |
| EVB-IT Erstellung | Individualsoftware-Erstellung (Werkvertrag) |
| EVB-IT Instandhaltung | Software-Wartung und -Pflege |
| EVB-IT Cloud | Cloud-Services (SaaS, IaaS, PaaS) -- **seit 2022** |

**Praxis**: EVB-IT sind nicht AGB des Auftraggebers, sondern einvernehmlich gestellte Klauselwerke.
Sie unterliegen grundsätzlich der AGB-Kontrolle, genießen aber eine gewisse Vermutung der
Ausgewogenheit.

### Österreich: BVergG und ÖNORM
- **Bundesvergabegesetz 2018 (BVergG 2018)**: Umsetzung der EU-Vergaberichtlinien
- **ÖNORM A 2050**: Allgemeine Vergabegrundsätze
- **ÖNORM A 2060**: Allgemeine Vertragsbestimmungen für IT-Leistungen
- **ÖNORM A 2063**: Besondere Vertragsbestimmungen für IT-Leistungen (Ergänzung zu A 2060)

### Schweiz
- **Bundesgesetz über das öffentliche Beschaffungswesen (BöB)**: Gilt für Bundesstellen
- **WTO-GPA**: Schwellenwerte nach WTO Government Procurement Agreement
- **Keine SIA-Normen für IT** im engeren Sinn, aber SIA-Normen für IT-nahe Engineering-Leistungen

---

## 7. Länderspezifische Besonderheiten

### Österreich (AT)
- **ABGB** statt BGB, aber viele Parallelvorschriften
- **UGB** (Unternehmensgesetzbuch) statt HGB für Handelsrecht
- **Unternehmensbegriff** statt Kaufmannsbegriff
- **Gewährleistung**: 3 Jahre (nicht 2 wie in DE) -- wichtig bei IT-Projekten!
- **§ 934 ABGB (laesio enormis)**: Aufhebung des Vertrags wenn Leistung weniger als die
  Hälfte des Werts der Gegenleistung beträgt (bei B2B abdingbar, bei B2C nicht)
- **Datenschutzbehörde Wien** (nicht BfDI wie in DE)
- **DSG** (Datenschutzgesetz 2018): Nationale Ergänzung zur DSGVO mit Besonderheiten
  (z.B. § 12 DSG Bildverarbeitung, § 2 DSG Datengeheimnis)
- **NIS-Gesetz (NISG)**: Umsetzung der NIS2-RL, in Kraft seit [Umsetzungsfrist laufend]

### Deutschland (DE)
- **BGB**: Bürgerliches Gesetzbuch als Kerngesetz
- **AGB-Recht (§§ 305-310 BGB)**: Strengste AGB-Kontrolle im DACH-Raum
- **HGB**: Handelsgesetzbuch (§ 377 HGB: Rügepflicht im Handelsverkehr)
- **BfDI und Landesbeauftragte**: Datenschutzaufsicht auf Bundes- und Landesebene
- **NIS2UmsuCG**: NIS-2-Umsetzungs- und Cybersicherheitsstärkungsgesetz (in Umsetzung)
- **IT-Sicherheitsgesetz 2.0**: Erweiterte Pflichten für KRITIS-Betreiber
- **GoBD**: Grundsätze ordnungsmäßiger Buchführung -- relevant für IT-Systeme die
  Finanzdaten verarbeiten (Aufbewahrung, Unveränderbarkeit, Nachvollziehbarkeit)

### Schweiz (CH)
- **OR** (Obligationenrecht) statt BGB
- **Schwächere AGB-Kontrolle** (kein eigenes AGB-Gesetz, nur Art. 8 UWG + Richterrecht)
- **Strengere Rügepflicht** (Art. 201, 367 OR): Mängel SOFORT rügen, sonst Anspruchsverlust
- **nDSG** (neues Datenschutzgesetz, in Kraft seit 1.9.2023): Eigenes Regime, DSGVO-ähnlich
  aber nicht identisch. Keine Angemessenheitsentscheidung nötig (CH hat eigenen Angemessenheitsbeschluss der EU).
- **Kein umfassendes NIS2-Äquivalent**, aber Informationssicherheitsgesetz (ISG) und
  Meldepflicht für Cyberangriffe auf kritische Infrastrukturen (seit 1.4.2025)
- **Swiss Finish**: Tendenz zu strengerer Regulierung als EU-Minimum in Datenschutz und
  Finanzmarktrecht
