# EU-Regulierung für IT-Verträge -- Referenz

Diese Referenz deckt die wesentlichen EU-Regulierungen ab, die bei der Prüfung von IT-Verträgen
im DACH-Raum relevant sind. Lese diese Datei, wenn DSGVO-, NIS2-, AI Act-, Data Act- oder
sonstige regulatorische Compliance-Fragen in IT-Verträgen zu bewerten sind.

## Inhaltsverzeichnis
1. DSGVO / GDPR -- Datenschutz-Grundverordnung
2. NIS2 -- Netz- und Informationssicherheits-Richtlinie
3. EU AI Act -- KI-Verordnung
4. Data Act -- Datenverordnung
5. Digital Services Act (DSA) / Digital Markets Act (DMA)
6. eIDAS 2.0
7. Cyber Resilience Act (CRA)
8. Prüfmatrix: Welche Regulierung betrifft welchen IT-Vertrag?

---

## 1. DSGVO / GDPR (VO (EU) 2016/679)

### Relevanz für IT-Verträge
Die DSGVO betrifft nahezu jeden IT-Vertrag, in dem personenbezogene Daten verarbeitet werden.
Die vertragliche Absicherung ist nicht optional, sondern **gesetzlich vorgeschrieben**.

### Art. 28 DSGVO -- Auftragsverarbeiter (AVV-Pflichtinhalte)
Jeder Vertrag mit einem Auftragsverarbeiter **muss** folgende Elemente enthalten:

| Nr. | Pflichtinhalt (Art. 28 Abs. 3 DSGVO) | Prüfpunkt im Vertrag |
|---|---|---|
| 1 | Gegenstand und Dauer der Verarbeitung | Klar definiert in AVV oder Hauptvertrag? |
| 2 | Art und Zweck der Verarbeitung | Spezifisch benannt (nicht "all purposes")? |
| 3 | Art der personenbezogenen Daten | Kategorien aufgelistet? Besondere Kategorien (Art. 9)? |
| 4 | Kategorien betroffener Personen | Mitarbeiter, Kunden, Nutzer etc.? |
| 5 | Weisungsbindung (lit. a) | Verarbeitung nur auf dokumentierte Weisung? Hinweispflicht bei rechtswidrigen Weisungen? |
| 6 | Vertraulichkeit (lit. b) | Personal zur Vertraulichkeit verpflichtet? |
| 7 | Technisch-organisatorische Maßnahmen (lit. c) | TOMs nach Art. 32 definiert? Konkretes Sicherheitsniveau? |
| 8 | Subunternehmer (lit. d) | Genehmigungsverfahren (einzeln/allgemein)? Widerspruchsrecht? Durchgriff? |
| 9 | Unterstützung Betroffenenrechte (lit. e) | Auftragsverarbeiter unterstützt bei Art. 15-22? |
| 10 | Unterstützung Sicherheitspflichten (lit. f) | Meldepflicht bei Datenschutzverletzungen (Art. 33/34)? |
| 11 | Löschung/Rückgabe nach Vertragsende (lit. g) | Wahl des Verantwortlichen? Frist? Nachweis? |
| 12 | Nachweispflichten und Audits (lit. h) | Recht auf Audits (vor Ort oder Zertifikat)? |

### Drittlandtransfer (Kapitel V DSGVO)
| Mechanismus | Beschreibung | Prüfpunkt |
|---|---|---|
| Angemessenheitsbeschluss (Art. 45) | EU-Kommission hat angemessenes Datenschutzniveau festgestellt | Gilt für: Schweiz, UK, Japan, Südkorea, USA (DPF seit 2023) u.a. |
| Standardvertragsklauseln (Art. 46 Abs. 2 lit. c) | EU-Standardklauseln (SCCs, Version 2021/914) | Welches Modul? (C2C, C2P, P2P, P2C) TIA durchgeführt? |
| Binding Corporate Rules (Art. 47) | Konzerninterne Regeln, genehmigt von Aufsichtsbehörde | Seltener, nur bei großen Konzernen |
| Ausnahmen (Art. 49) | Einwilligung, Vertragserfüllung, zwingende Gründe | Nur Ausnahmefälle, nicht für regelmäßige Transfers |

**Praxis-Prüfung Drittlandtransfer**:
1. Werden Daten außerhalb EU/EWR verarbeitet? (Auch Fernzugriff = Transfer!)
2. Hat das Land einen Angemessenheitsbeschluss?
3. Wenn nein: Sind SCCs abgeschlossen? Welches Modul?
4. Wurde ein Transfer Impact Assessment (TIA) durchgeführt? (Nach Schrems II erforderlich)
5. Sind zusätzliche technische Maßnahmen implementiert? (Verschlüsselung, Pseudonymisierung)

### Bußgeldrahmen DSGVO
- **Art. 83 Abs. 4**: Bis 10 Mio EUR oder 2% des weltweiten Jahresumsatzes (Auftragsverarbeiter-Pflichten, TOMs, Meldepflichten)
- **Art. 83 Abs. 5**: Bis 20 Mio EUR oder 4% des weltweiten Jahresumsatzes (Grundsätze, Betroffenenrechte, Drittlandtransfer)

### Red Flags DSGVO in IT-Verträgen
- Kein AVV obwohl personenbezogene Daten verarbeitet werden
- AVV fehlen Pflichtinhalte (oft: keine TOMs, keine Subprocessor-Regelung)
- Pauschale Genehmigung aller Subprocessors ohne Widerspruchsrecht
- Datenverarbeitung in USA ohne DPF-Zertifizierung oder SCCs
- Meldepflicht bei Datenschutzverletzung >72h (oder gar nicht geregelt)
- TOMs nur als "state of the art" ohne Konkretisierung
- Kein Audit-Recht (oder nur "summary report" statt echtem Audit)
- Daten werden nach Vertragsende nicht gelöscht/zurückgegeben

---

## 2. NIS2-Richtlinie (RL (EU) 2022/2555)

### Überblick
Die NIS2-Richtlinie erweitert die Cybersicherheitspflichten erheblich. Sie betrifft nicht nur
die regulierten Einrichtungen selbst, sondern auch deren **IT-Lieferkette**.

### Betroffene Einrichtungen
| Kategorie | Sektoren | Schwellenwerte |
|---|---|---|
| **Wesentliche Einrichtungen** | Energie, Transport, Bankwesen, Finanzmarktinfrastruktur, Gesundheit, Trinkwasser, Abwasser, Digitale Infrastruktur, ICT-Service-Management (B2B), öffentliche Verwaltung, Weltraum | Groß: >250 MA oder >50M EUR Umsatz |
| **Wichtige Einrichtungen** | Post, Abfallwirtschaft, Chemie, Lebensmittel, Verarbeitendes Gewerbe, Digitale Dienste (Online-Marktplätze, Suchmaschinen, soziale Netzwerke), Forschung | Mittel: >50 MA oder >10M EUR Umsatz |

### NIS2-Pflichten mit Vertragsrelevanz

#### Lieferkettensicherheit (Art. 21 Abs. 2 lit. d)
Einrichtungen müssen **Sicherheit in der Lieferkette** gewährleisten, einschließlich
sicherheitsbezogener Aspekte der Beziehungen zu ihren **IT-Dienstleistern**.

**Vertragliche Pflichtklauseln (empfohlen)**:
1. **Sicherheitsanforderungen**: Mindeststandard (ISO 27001, BSI C5, SOC 2 Type II)
2. **Meldepflichten**: Sicherheitsvorfälle innerhalb von 24h (Frühwarnung), 72h (förmliche Meldung), 1 Monat (Abschlussbericht)
3. **Audit-Rechte**: Recht auf Sicherheitsaudits (vor Ort oder durch Dritte)
4. **Zertifizierungen**: Nachweis über gültige Zertifizierung
5. **Incident Response**: Zusammenarbeit bei Sicherheitsvorfällen
6. **Unterauftragnehmer**: Durchgriff der Sicherheitsanforderungen

#### Meldepflichten (Art. 23)
| Frist | Pflicht |
|---|---|
| 24 Stunden | Frühwarnung an zuständige Behörde (CSIRT) |
| 72 Stunden | Qualifizierte Meldung (Bewertung, Schwere, Indikatoren) |
| 1 Monat | Abschlussbericht (Ursache, Maßnahmen, grenzüberschreitende Auswirkungen) |

#### Persönliche Haftung der Geschäftsleitung (Art. 20)
Die Geschäftsleitung (Vorstand, GF) muss die Cybersicherheitsmaßnahmen **billigen und überwachen**.
Bei Pflichtverletzung: **persönliche Haftung** möglich.

### Bußgeldrahmen NIS2
- **Wesentliche Einrichtungen**: Bis 10 Mio EUR oder 2% des weltweiten Jahresumsatzes
- **Wichtige Einrichtungen**: Bis 7 Mio EUR oder 1,4% des weltweiten Jahresumsatzes

### Umsetzung in DACH
| Land | Umsetzungsgesetz | Status |
|---|---|---|
| DE | NIS2UmsuCG (NIS-2-Umsetzungs- und Cybersicherheitsstärkungsgesetz) | Verzögert, erwartet 2025/2026 |
| AT | NISG 2024 (NIS-Gesetz Novelle) | In Umsetzung |
| CH | ISG (Informationssicherheitsgesetz) + Meldepflicht-VO | Teilweise in Kraft (kein vollständiges NIS2-Äquivalent) |

### Red Flags NIS2 in IT-Verträgen
- Vertrag mit wesentlicher/wichtiger Einrichtung ohne Sicherheitsklauseln
- Keine Meldepflicht für Sicherheitsvorfälle definiert
- Kein Audit-Recht für Sicherheitsüberprüfungen
- Keine Anforderung an Sicherheitszertifizierung (ISO 27001, BSI C5, SOC 2)
- Subunternehmer-Kette ohne Durchgriff der Sicherheitsanforderungen
- Keine Incident-Response-Zusammenarbeit vorgesehen
- Sicherheitsniveau nicht am Stand der Technik (Art. 21 Abs. 1)

---

## 3. EU AI Act (VO (EU) 2024/1689)

### Relevanz für IT-Verträge
Der AI Act betrifft IT-Verträge, wenn KI-Systeme entwickelt, bereitgestellt oder eingesetzt
werden. Die Pflichten variieren je nach Risikoklasse.

### Risikoklassen und Vertragspflichten
| Risikoklasse | Beispiele | Vertragspflichten |
|---|---|---|
| **Verboten** (Art. 5) | Social Scoring, biometrische Echtzeit-Fernidentifizierung (mit Ausnahmen), Emotionserkennung am Arbeitsplatz | Nicht vertraglich vereinbar. Vertrag über verbotene Anwendung = nichtig. |
| **Hochrisiko** (Art. 6, Anhang III) | KI in Medizinprodukten, Kreditscoring, Personalauswahl, Justiz, Strafverfolgung, Migration, kritische Infrastruktur | CE-Konformität, Qualitätsmanagementsystem, technische Dokumentation, Logging, menschliche Aufsicht, Registrierung, Transparenz |
| **Begrenzt** (Art. 50) | Chatbots, Deepfakes, Emotionserkennung (nicht-Arbeitsplatz) | Transparenzpflicht: Nutzer muss wissen dass er mit KI interagiert |
| **Minimal** | Spamfilter, KI-gestützte Dokumentsuche, Sprachassistenten | Keine besonderen Pflichten, aber Verhaltenskodex empfohlen |

### GPAI-Modelle (General Purpose AI, Art. 51-56)
Für **Anbieter von Foundation Models / LLMs** (wie GPT, Claude, Gemini):
- Transparenzpflichten (Trainingsdata, technische Dokumentation)
- Bei **systemischem Risiko** (>10^25 FLOP Training): Zusätzliche Pflichten (Red Teaming,
  Adversarial Testing, Incident Reporting)

### Vertragliche Implikationen AI Act
| Vertragsklausel | Pflicht | Betrifft |
|---|---|---|
| Risikoklassifizierung | Einordnung des KI-Systems im Vertrag | Anbieter + Betreiber |
| Konformitätserklärung | CE-Kennzeichnung bei Hochrisiko, Verweis im Vertrag | Anbieter |
| Menschliche Aufsicht | Regelung wer die Aufsichtspflicht ausübt | Betreiber |
| Transparenz | Pflicht zur Information der Nutzer über KI | Anbieter + Betreiber |
| Logging/Monitoring | Wer speichert Logs, wie lange, wer hat Zugang | Anbieter + Betreiber |
| Haftung | Verteilung bei KI-Fehlern, Beweislast | Anbieter + Betreiber |
| Trainingsdaten | Nutzung von Kundendaten zum Training | Anbieter |
| Konformitätsbewertung | Pflicht zur Durchführung, Update bei Änderungen | Anbieter |

### Zeitplan AI Act
| Datum | Inkrafttreten |
|---|---|
| 2.8.2024 | Veröffentlichung im Amtsblatt |
| 2.2.2025 | Verbotene Praktiken (Art. 5) gelten |
| 2.8.2025 | GPAI-Pflichten gelten, Governance (Art. 51-56) |
| 2.8.2026 | Hochrisiko-KI-Systeme in Anhang III gelten |
| 2.8.2027 | Hochrisiko-KI in regulierten Produkten (Anhang I) gelten |

### Red Flags AI Act in IT-Verträgen
- KI-Einsatz ohne Risikoklassifizierung
- Hochrisiko-KI ohne CE-Konformitätserklärung
- Keine Regelung zur menschlichen Aufsicht
- Keine Transparenz gegenüber Endnutzern über KI-Einsatz
- Kundendaten zum KI-Training ohne Zustimmung
- Keine Regelung zu KI-Haftung und Beweislast
- Deepfake-Erzeugung ohne Kennzeichnungspflicht

---

## 4. Data Act (VO (EU) 2023/2854)

### Überblick
Der Data Act regelt den Zugang zu und die Nutzung von maschinengenerierten Daten und hat
erhebliche Auswirkungen auf Cloud- und IoT-Verträge.

### Anwendungsbeginn: 12. September 2025

### Kernpflichten mit Vertragsrelevanz

#### Cloud-Switching (Kapitel VI, Art. 23-31)
**Pflichten für Cloud-/SaaS-Anbieter**:
- **Wechselrecht**: Kunde muss zu anderem Anbieter wechseln können
- **Übergangsfristen**: Max. 30 Tage für Datenherausgabe (nach Übergangsfrist: sofort)
- **Kosten**: Wechselgebühren müssen schrittweise auf null sinken
  (nach 12.1.2027: keine Wechselgebühren mehr, Art. 29 Abs. 1)
- **Datenformat**: Offenes, maschinenlesbares Standardformat
- **Funktionale Äquivalenz**: Bei IaaS: Output muss auf anderem Anbieter funktional äquivalent
  laufen können
- **Interoperabilität**: Offene Schnittstellen und Interoperabilitäts-Spezifikationen

#### Datenbereitstellungspflichten (Kapitel II-III, Art. 3-12)
- Nutzer von IoT-Produkten haben Recht auf die von ihren Geräten erzeugten Daten
- Hersteller/Diensteanbieter müssen Zugang bereitstellen (kostenlos, kontinuierlich, in Echtzeit)

#### Schutz vor missbräuchlichen Vertragsklauseln (Art. 13)
- Vertragliche Klauseln zum Datenzugang sind **unwirksam** wenn sie einseitig auferlegt werden
  und den Datenzugang unangemessen beschränken
- Graue/schwarze Liste missbräuchlicher Klauseln (ähnlich AGB-Kontrolle)

### Red Flags Data Act in IT-Verträgen
- Lock-in-Klauseln die Datenmigration verhindern oder unverhältnismäßig verteuern
- Proprietäres Datenformat ohne Export in offenes Format
- Wechselgebühren nach 12.1.2027
- Kein Datenzugang für IoT-Nutzer
- Klauseln die Datenweitergabe an Dritte unangemessen beschränken

---

## 5. Digital Services Act (DSA) / Digital Markets Act (DMA)

### DSA (VO (EU) 2022/2065)
**Relevanz für IT-Verträge**: Betrifft Verträge mit Online-Plattformen und Hosting-Diensten.
- Transparenzpflichten für Algorithmen
- Content-Moderation-Pflichten
- Haftungsregime für Hosting-Provider (Art. 6: "Notice and Action")
- Pflicht zur Meldestelle für illegale Inhalte

### DMA (VO (EU) 2022/1925)
**Relevanz für IT-Verträge**: Betrifft Verträge mit "Gatekeepern" (Apple, Google, Microsoft,
Amazon, Meta, ByteDance, Samsung u.a.).
- Interoperabilitätspflichten
- Verbot der Selbstbevorzugung
- Datenportabilität für Business-Nutzer

**Praxisrelevanz**: Meist indirekt relevant, z.B. wenn ein IT-Vertrag die Nutzung einer
Gatekeeper-Plattform voraussetzt und der Gatekeeper seine Bedingungen aufgrund des DMA ändern muss.

---

## 6. eIDAS 2.0 (VO (EU) 2024/1183)

### Relevanz für IT-Verträge
- **EU Digital Identity Wallet**: Pflicht zur Akzeptanz ab 2027 für bestimmte Dienste
- **Elektronische Signaturen**: Qualifizierte elektronische Signatur (QES) hat Beweiskraft
  einer handschriftlichen Unterschrift (Art. 25 Abs. 2 eIDAS)
- **Vertrauensdienste**: Zeitstempel, Siegel, Zustellung -- vertraglich relevant für
  Formvorschriften und Nachweisbarkeit

### Prüfpunkte in IT-Verträgen
- Ist die vereinbarte Schriftform durch QES ersetzbar? (§ 126a BGB: ja, wenn nicht notariell)
- Akzeptiert der Vertrag elektronische Signaturen? Welche Stufe (einfach, fortgeschritten, qualifiziert)?
- Werden Vertrauensdienste genutzt? Wer ist der Vertrauensdiensteanbieter?

---

## 7. Cyber Resilience Act (CRA) (VO (EU) 2024/2847)

### Überblick
Der CRA schafft horizontale Cybersicherheitsanforderungen für **Produkte mit digitalen Elementen**
(Software und Hardware), die auf dem EU-Markt bereitgestellt werden.

### Anwendungsbeginn
- Veröffentlichung: 2024
- Pflichten greifen stufenweise: ab 11.12.2027 vollständig anwendbar
- Meldepflichten: ab 11.9.2026

### Relevanz für IT-Verträge
| Pflicht | Vertragsklausel |
|---|---|
| Security by Design | Sicherheitsanforderungen in Leistungsbeschreibung |
| Vulnerability Management | Pflicht zur Bereitstellung von Sicherheitsupdates (min. 5 Jahre) |
| SBOM (Software Bill of Materials) | Pflicht zur Offenlegung von Komponenten |
| CE-Kennzeichnung | Konformitätserklärung für digitale Produkte |
| Meldepflicht | Aktiv ausgenutzte Schwachstellen: Meldung an ENISA innerhalb 24h |

### Red Flags CRA in IT-Verträgen
- Software-Produkt ohne CE-Konformitätserklärung (ab 2027)
- Keine Sicherheitsupdate-Pflicht über Vertragslaufzeit
- Kein SBOM bereitgestellt
- Keine Meldepflicht für Schwachstellen vereinbart

---

## 8. Prüfmatrix: Welche Regulierung betrifft welchen IT-Vertrag?

| IT-Vertragstyp | DSGVO/AVV | NIS2 | AI Act | Data Act | CRA | DSA/DMA | eIDAS |
|---|---|---|---|---|---|---|---|
| SaaS/Cloud | ✅ Immer | ✅ Wenn Kunde wesentl./wichtig | ⚠️ Wenn KI-Feature | ✅ Cloud-Switching | ⚠️ Wenn Softwareprodukt | ⚠️ Wenn Plattform | ⚠️ Wenn Signatur |
| Softwarelizenz | ✅ Wenn personenbez. Daten | ⚠️ Wenn kritisch | ⚠️ Wenn KI | ⚠️ Wenn IoT-Daten | ✅ Ab 2027 | ❌ | ⚠️ |
| IT-Implementierung | ✅ Wenn personenbez. Daten | ⚠️ Wenn für NIS2-Einrichtung | ⚠️ Wenn KI-System | ❌ | ⚠️ Wenn Produktentwicklung | ❌ | ❌ |
| IT-Outsourcing | ✅ Immer | ✅ Oft | ⚠️ Wenn KI-Feature | ✅ Datenzugang | ❌ | ❌ | ⚠️ |
| IT-Beratung | ✅ Wenn Datenzugang | ⚠️ Selten | ⚠️ Selten | ❌ | ❌ | ❌ | ❌ |
| Hosting/Colocation | ✅ Immer | ✅ Digitale Infrastruktur | ❌ | ✅ Cloud-Switching | ❌ | ⚠️ Wenn Hosting-Provider | ❌ |
| KI-Service | ✅ Immer | ⚠️ | ✅ Immer | ⚠️ Wenn Datenzugang | ⚠️ | ⚠️ Wenn KI-Plattform | ❌ |
| Wartung/Pflege | ✅ Wenn Datenzugang | ⚠️ | ❌ | ❌ | ✅ Update-Pflicht | ❌ | ❌ |

✅ = Regelmäßig anwendbar | ⚠️ = Im Einzelfall prüfen | ❌ = Typischerweise nicht anwendbar
