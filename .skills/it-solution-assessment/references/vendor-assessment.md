# Vendor Assessment — Due Diligence Checkliste

Bewertungskriterien für die Anbieter-Due-Diligence, anwendbar auf SaaS- und On-Premises-Lösungen.

## 1. Unternehmensprofil

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| V01 | **Firmensitz & Jurisdiktion** | ●●● | In welchem Land ist der Hauptsitz? Welches Recht gilt? EU/EWR oder Drittland? |
| V02 | **Niederlassungen** | ●● | Gibt es Niederlassungen in AT/DACH/EU? Lokale Ansprechpartner? |
| V03 | **Gründungsjahr** | ●● | Wie lange existiert das Unternehmen? Marktreife? |
| V04 | **Mitarbeiterzahl** | ●● | Gesamtanzahl? Davon in R&D? Support? |
| V05 | **Branchenfokus** | ● | Spezialisierung auf bestimmte Branchen? Relevanz für eigene Branche? |

### Scoring-Guide

| Score | Unternehmensprofil |
|---|---|
| 0 | Startup < 2 Jahre, kein EU-Sitz, keine lokale Präsenz |
| 1 | Etabliert, aber kein EU-Sitz oder sehr kleines Team (< 20 MA) |
| 2 | EU-Sitz, > 50 MA, > 5 Jahre am Markt, DACH-Präsenz |
| 3 | EU-Sitz, > 200 MA, > 10 Jahre, Niederlassung AT/DACH, Branchenfokus |

---

## 2. Eigentümerstruktur & Finanzielle Stabilität

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| V06 | **Eigentümerstruktur** | ●●● | Börsennotiert, PE-owned, VC-finanziert, Familienunternehmen, Genossenschaft? |
| V07 | **Investor / Muttergesellschaft** | ●● | Wem gehört der Vendor? Sind die Eigentümer bekannt und stabil? US-Cloud-Act-relevant? |
| V08 | **Finanzielle Stabilität** | ●●● | Profitabel? Umsatzwachstum? Burn Rate (bei VC)? Kreditrating? |
| V09 | **Übernahme-Risiko** | ●● | Wurde das Unternehmen kürzlich übernommen? Ist eine Übernahme wahrscheinlich? Auswirkung auf Produkt? |
| V10 | **Insolvenz-Risiko** | ●●● | Gibt es Anzeichen für finanzielle Schwierigkeiten? Was passiert mit Daten/Software bei Insolvenz? |

### Bewertungshilfe Eigentümerstruktur

| Typ | Typische Risiken | Typische Stärken |
|---|---|---|
| **Börsennotiert** | Quartalsdruck, M&A-Risiko | Transparenz, Kapitalzugang, Compliance |
| **PE-owned** | Exit-Druck (3–7 Jahre), Kosteneinsparung, Produktkonsolidierung | Professionalisierung, Wachstumskapital |
| **VC-finanziert** | Burn Rate, Pivot-Risiko, Akquise als Exit | Innovationsgeschwindigkeit, Feature-Velocity |
| **Familienunternehmen** | Nachfolgethematik, begrenzte Skalierung | Langfristorientierung, Stabilität |
| **Open Source / Foundation** | Sustainability, Contributor-Abhängigkeit | Kein Vendor-Lock-in, Community, Transparenz |

### Scoring-Guide

| Score | Finanzielle Stabilität |
|---|---|
| 0 | Drohende Insolvenz, kein Funding, Produkt vor End-of-Life |
| 1 | VC-funded ohne Profitabilität, PE-Exit absehbar, hohe Abhängigkeit von wenigen Kunden |
| 2 | Profitabel oder gut finanziert, stabile Eigentümerstruktur, > 100 Kunden |
| 3 | Börsennotiert / profitabel, transparente Finanzen, >1000 Kunden, Investment Grade |

---

## 3. Marktposition & Referenzen

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| V11 | **Marktposition** | ●● | Einordnung in Gartner Magic Quadrant, Forrester Wave, IDC? Nische oder Mainstream? |
| V12 | **Kunden im DACH-Raum** | ●● | Referenzkunden in AT/DE/CH? In gleicher Branche? Vergleichbare Größe? |
| V13 | **Kundenzahl** | ●● | Gesamtanzahl Kunden? Enterprise-Kunden? Wachstum? |
| V14 | **Kundenzufriedenheit** | ● | G2, Capterra, Gartner Peer Insights — Bewertungen? |
| V15 | **Wettbewerber** | ● | Wer sind die Hauptkonkurrenten? Differenzierung? |

### Scoring-Guide

| Score | Marktposition |
|---|---|
| 0 | Unbekannt, keine Referenzen, kein Analyst-Ranking |
| 1 | Nischenanbieter, wenige Referenzen, keine DACH-Kunden |
| 2 | Etabliert in der Kategorie, DACH-Referenzen, Analyst-Ranking vorhanden |
| 3 | Leader/Strong Performer, >5 DACH-Referenzen in der Branche, >1000 Kunden |

---

## 4. Produkt-Roadmap & Innovation

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| V16 | **Release-Kadenz** | ●● | Wie oft erscheinen neue Versionen? Regelmäßig? |
| V17 | **Roadmap-Transparenz** | ●● | Wird die Roadmap geteilt? Können Kunden Features priorisieren? |
| V18 | **R&D-Investment** | ●● | Anteil der Entwicklungsressourcen? Wird aktiv weiterentwickelt? |
| V19 | **End-of-Life-Risiko** | ●●● | Ist das Produkt aktiv? Nachfolgeprodukt angekündigt? Migration geplant? |
| V20 | **Innovation** | ● | Nutzt moderne Technologien? AI/ML-Features? Technologisch zukunftsfähig? |

### Scoring-Guide

| Score | Roadmap |
|---|---|
| 0 | Produkt eingestellt oder End-of-Life absehbar (< 2 Jahre) |
| 1 | Wenige Updates, keine transparente Roadmap, einzelnes Entwicklungsteam |
| 2 | Regelmäßige Releases, Roadmap auf Anfrage, aktive Weiterentwicklung |
| 3 | Transparente Roadmap, Customer Advisory Board, regelmäßige Innovation, starkes R&D |

---

## 5. Partnernetzwerk & Ökosystem

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| V21 | **Implementierungspartner** | ●● | Zertifizierte Partner in AT/DACH? Erfahrene Implementierer? |
| V22 | **Ökosystem** | ● | Marketplace? Integrationen? Community? |
| V23 | **Schulungsangebot** | ● | Trainings, Zertifizierungen? Online / vor Ort? Sprache? |
| V24 | **Community** | ● | Aktive Community? Forum? User Groups in DACH? |

---

## 6. Exit-Strategie & Vendor-Risiko

| # | Kriterium | Gewicht | Prüffragen |
|---|---|---|---|
| V25 | **Vertragsende-Szenario** | ●●● | Was passiert bei Vertragsende? Datenzugang? Transition? |
| V26 | **Insolvenz-Szenario** | ●●● | Was passiert mit Daten/Software bei Insolvenz? Escrow? SPV? |
| V27 | **Produkteinstellung** | ●● | Verpflichtung zur Weiterführung (z.B. 12–24 Monate)? Migration-Support? |
| V28 | **Datenrückgabe** | ●●● | Garantierte Datenrückgabe? Format? Frist? Kosten? |
| V29 | **Schlüsselpersonen-Risiko** | ● | Abhängigkeit von einzelnen Personen beim Vendor? (bei kleinen Unternehmen) |

### Scoring-Guide

| Score | Exit-Strategie |
|---|---|
| 0 | Keine Exit-Regelung, kein Escrow, keine Datenrückgabe |
| 1 | Basis-Exit-Klausel, aber kein Escrow, unklare Transition |
| 2 | Dokumentierte Exit-Prozedur, Datenrückgabe garantiert, Transition-Support |
| 3 | Exit-Prozedur + Escrow + Transition-Support + Datenrückgabe + Mindestlaufzeit-Garantie |

---

## Red Flags (sofortige Warnung)

Folgende Signale erfordern besondere Aufmerksamkeit:

| Red Flag | Aktion |
|---|---|
| Vendor verweigert Auskunft zu Eigentümerstruktur | K.O.-Kandidat — Transparenz ist Grundvoraussetzung |
| Kein DACH-Referenzkunde trotz Marktbehauptung | Kritisch hinterfragen, ggf. Proof of Concept fordern |
| Kürzliche Übernahme durch PE mit Produktkonsolidierung | Roadmap-Garantien vertraglich absichern |
| End-of-Life angekündigt, kein Migrationsplan | Hohe Dringlichkeit für Exit-Strategie |
| Investor aus Nicht-EU mit Zugriffsmöglichkeit auf Daten | CLOUD Act / Drittland-Transfer prüfen |
| Nur ein einzelner Experte für Kernprodukt | Schlüsselpersonen-Risiko — Escrow und Support-SLA prüfen |
