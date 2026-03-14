# IT-Vertragsanalyse Skill (EU/DACH)

Strukturierte, quantitative IT-Vertragsrisikoanalyse für den EU/DACH-Rechtsraum (Österreich, Deutschland, Schweiz, EU).

## Überblick

Dieser Skill befähigt GitHub Copilot, IT-Verträge systematisch zu analysieren, zu bewerten und Handlungsempfehlungen (Redlines) zu generieren. Er kombiniert zwei Disziplinen:

1. **Klauselweise Abweichungsprüfung** (Ampelsystem: GRÜN/GELB/ROT) – Ist eine Klausel akzeptabel, verhandelbar oder ein Dealbreaker nach DACH-Zivilrecht?
2. **Quantitative Risikobewertung** (Schwere × Wahrscheinlichkeit, Score 1–25) – Wie schwerwiegend ist das Risiko und wie wahrscheinlich ist der Eintritt?

Das Ergebnis ist ein vollständiges Risikoregister mit Ampelklassifikation, numerischem Score, rechtlicher Einordnung und fertigen Redline-Formulierungen.

> **Hinweis**: Der Skill unterstützt bei rechtlichen Workflows, ersetzt aber keine Rechtsberatung. Alle Analysen sollten von qualifizierten Rechtsexperten geprüft werden.

## ⚠️ Vertraulichkeitshinweis

> **Dieser Skill verarbeitet potenziell vertrauliche Vertragsdaten.**
>
> Er darf **nur in einem abgesicherten Enterprise-Umfeld** verwendet werden:
> - Azure OpenAI im eigenen Tenant
> - GitHub Copilot Enterprise/Business mit Data Protection
> - Self-hosted LLM
>
> **Bei Aktivierung fragt der Skill aktiv ab**, ob ein abgesicherter Endpunkt vorliegt.
> Ohne Bestätigung wird die Analyse **nicht durchgeführt**.
>
> Bei Nutzung über öffentliche/kostenlose AI-Endpunkte können vertrauliche Vertragsdaten
> an Dritte gelangen — ein potenzieller Verstoß gegen DSGVO, Vertraulichkeitsvereinbarungen
> und interne Compliance-Richtlinien.

## Verzeichnisstruktur

```
.skills/it-contract-analysis/
├── SKILL.md                          # Hauptdatei: Methodik und Anweisungen
├── README.md                         # Diese Datei
├── references/
│   ├── it-contracts.md               # IT-Vertragstypen & Klauselanalyse (50-Punkte-Checkliste)
│   ├── dach-legal-framework.md       # DACH-Zivilrecht (BGB, ABGB, OR, AGB-Recht)
│   └── eu-regulations.md             # EU-Regulatorik (DSGVO, NIS2, AI Act, Data Act)
└── evals/
    ├── evals.json                    # 10 Evaluierungs-Szenarien mit Erwartungen
    └── sample-contracts/
        ├── 01-saas-vertrag-cloudflow.md     # Muster-SaaS-Vertrag (mit Red Flags)
        └── 02-erp-implementierung-werkvertrag.md  # Muster-ERP-Werkvertrag
```

### SKILL.md (Hauptdatei)

Die zentrale Datei, die Copilot als Anweisung liest. Enthält:

- **YAML Frontmatter** – Name, Beschreibung und Trigger-Schlüsselwörter für die Skill-Erkennung
- **Kernmethodik** – 7-Schritte-Prozess von Vertragsklassifikation bis Analysekommentar
- **IT-spezifische Klauselanalyse** – Prüfpunkte für SLA, Abnahme, Gewährleistung, Haftung, AVV, Kündigung, Exit, IP, Change Request, NIS2, AI Act
- **Portfolio-Analyse** – Methodik für Multi-Vertrags-Bewertungen
- **Ausgabeformate** – Deutsche Spaltenüberschriften, Risikoregister-Struktur
- **Prüfcheckliste** – Qualitätssicherung vor Auslieferung
- **Eskalationskriterien** – Wann externe Rechtsberatung empfohlen wird

### Referenzdateien

Der Skill liest diese Dateien kontextabhängig nach, bevor er eine Analyse durchführt:

| Datei | Inhalt | Wann gelesen |
|---|---|---|
| `references/it-contracts.md` | Klauselanalyse für 8 IT-Vertragstypen, 50-Punkte-Prüftemplate, Red-Flags-Schnellreferenz | Bei jeder IT-Vertragsprüfung |
| `references/dach-legal-framework.md` | Vertragstypen-Qualifikation (Werkvertrag/Dienstvertrag), AGB-Recht, Gewährleistung, Haftung, Vertragsstrafe, Vergaberecht | Bei rechtlicher Einordnung, AGB-Kontrolle |
| `references/eu-regulations.md` | DSGVO/AVV-Pflichten, NIS2-Lieferkette, AI Act, Data Act, DSA/DMA, eIDAS, CRA | Bei regulatorischen Fragen |

### Evaluierungsdaten

- `evals/evals.json` – 10 Test-Szenarien mit detaillierten Erwartungen
- `evals/sample-contracts/` – 2 realistische Musterverträge mit eingebauten Problemen

## Unterstützte IT-Vertragstypen

| Vertragstyp | Rechtliche Einordnung | Typische Prüfschwerpunkte |
|---|---|---|
| SaaS / Cloud Subscription | Mietvertrag (§ 535 BGB) / Dienstvertrag | SLA, Verfügbarkeit, Datenlokalisierung, Exit, AVV |
| Software-Lizenzvertrag | Lizenz-/Kaufvertrag (§ 453 BGB) | Nutzungsrechte, Audit, Unterlizenzierung, Laufzeit |
| IT-Systemintegration | **Werkvertrag** (§ 631 BGB / § 1165 ABGB) | Abnahme, Leistungsbeschreibung, Change Request, Meilensteine |
| IT-Outsourcing / Managed Services | Dienstvertrag mit werkvertraglichen Elementen | SLA, Transition, Exit, Personal |
| IT-Beratung | Dienstvertrag (§ 611 BGB) | T&M vs. Festpreis, Ergebnisverantwortung, IP |
| Hosting / Colocation | Mietvertrag mit Dienstleistungselementen | Verfügbarkeit, Datensicherheit, Zutritt |
| Wartungs-/Pflegevertrag | Werkvertrag + Dienstvertrag | Reaktionszeiten, Updates/Upgrades, Abkündigung |
| AVV / Datenverarbeitungsvertrag | Gesetzlich vorgeschrieben (Art. 28 DSGVO) | TOMs, Subunternehmer, Weisungsbindung, Löschung |
| KI-/AI-Service-Vertrag | Je nach Leistung (Dienst-/Werkvertrag) | AI Act-Konformität, Transparenz, Haftung |

## Methodik (7 Schritte)

1. **Vertrag klassifizieren** – Status (Entwurf/Abgeschlossen/Vorlage), Vertragstyp, Seite, anwendbares Recht, Prüfkontext
2. **Template-gesteuerte vs. freie Prüfung** – Jeden Prüfpunkt auf den Vertrag abbilden, fehlende Klauseln explizit als Befund markieren
3. **Abweichungsklassifikation (Ampel)** – GRÜN (akzeptabel), GELB (verhandeln), ROT (eskalieren) gegen Basislinie
4. **Quantitative Risikobewertung** – Schwere (1–5) × Wahrscheinlichkeit (1–5) = Score (1–25), Stufen: NIEDRIG / MITTEL / HOCH / KRITISCH
5. **Redline-Generierung** – Fertiger Klauseltext auf Deutsch, Priorität (Muss/Soll/Kann), Fallback-Position, rechtliche Begründung
6. **Rechtliche Einordnung** – Werkvertrag/Dienstvertrag, AGB/Individualvereinbarung, zwingendes/dispositives Recht, Regulatorik
7. **Analysekommentar** – Bezug zur Rechtslage, AGB-Tauglichkeit, regulatorische Implikationen

## Nutzung

### Voraussetzungen

- GitHub Copilot (Chat) mit Skill-Unterstützung
- Der Skill muss im Workspace unter `.skills/it-contract-analysis/` liegen

### Beispiel-Prompts

**Einzelvertragsanalyse:**
```
Prüfe den beiliegenden SaaS-Vertrag aus Kundensicht. Wir sind ein österreichisches 
Unternehmen. Der Vertrag ist noch nicht unterschrieben. Bitte erstelle eine 
Risikobewertung mit Redlines.
```

**DSGVO/AVV-Compliance:**
```
Bewerte die DSGVO-Compliance des vorliegenden Cloud-Vertrags. Personenbezogene 
Daten von 500 Mitarbeitern werden verarbeitet. Ist der AVV vollständig?
```

**NIS2-Prüfung:**
```
Wir fallen unter NIS2 als wesentliche Einrichtung (Energie). Prüfe unseren 
IT-Outsourcing-Vertrag auf NIS2-Lieferkettenpflichten.
```

**AGB-Kontrolle:**
```
Prüfe, ob die Standard-AGB des US-SaaS-Anbieters einer AGB-Kontrolle nach 
österreichischem Recht standhalten.
```

**Portfolio-Analyse:**
```
Erstelle eine Risikobewertung über unser IT-Vertragsportfolio (8 SaaS-Verträge, 
12 Managed-Services-Verträge). Fokus auf Vendor-Konzentration und DSGVO-Exposure.
```

**Werkvertrag-Qualifikation:**
```
Der Vertrag ist als "Dienstleistungsvertrag" tituliert, enthält aber Festpreis, 
Abnahme und definierte Meilensteine. Ist das wirklich ein Dienstvertrag?
```

### Tipps für optimale Ergebnisse

- **Vertragstext bereitstellen**: Den Vertrag als Datei im Workspace ablegen oder als Text im Chat einfügen
- **Kontext angeben**: Seite (Kunde/Anbieter), Rechtsordnung (AT/DE/CH), Status (Entwurf/unterschrieben)
- **Prüfkontext spezifizieren**: Verhandlung, Due Diligence, Compliance-Audit, Verlängerung, Vergabe
- **Fokus setzen**: Bei Bedarf auf bestimmte Klauseln oder Rechtsgebiete fokussieren (z.B. "nur Haftung und Gewährleistung")

## Testen und Evaluieren

### Evaluierungs-Suite

Die Datei `evals/evals.json` enthält 10 Testszenarien mit detaillierten Erwartungen:

| Nr. | Szenario | Schwerpunkt |
|---|---|---|
| 1 | SaaS-Vertrag Review (AT, Kundenseite) | Vollständige Analyse mit Mustervertrag |
| 2 | ERP-Implementierung Werkvertrag | Werkvertrag-Spezifika, Abnahme, Pflichtenheft |
| 3 | DSGVO/AVV Compliance Check | Drittlandtransfer, TOMs, Sub-Processor |
| 4 | NIS2-Lieferketten-Prüfung | Kritische Infrastruktur, Meldepflichten |
| 5 | AGB-Kontrolle SaaS Terms | Inhaltskontrolle nach österreichischem Recht |
| 6 | IT-Portfolio Due Diligence (PE) | Multi-Vertrag, Materiality, CoC-Klauseln |
| 7 | Werkvertrag vs. Dienstvertrag | Vertragstypqualifikation |
| 8 | KI-Service-Vertrag / AI Act | Hochrisiko-KI, CV-Screening |
| 9 | Data Act Cloud-Switching | Anbieterwechsel, Datenportabilität |
| 10 | Multi-Vertrag Template Review | 50-Punkte-Checkliste über 2 Verträge |

### Manuelles Testen

1. **Mustervertrag laden**: Öffne einen der Verträge aus `evals/sample-contracts/`
2. **Prompt eingeben**: Verwende den Prompt aus dem entsprechenden Eval-Szenario in `evals/evals.json`
3. **Ergebnis prüfen**: Vergleiche die Ausgabe mit den `expectations` im jeweiligen Eval-Eintrag

**Beispiel für Eval 1 (SaaS-Vertrag):**

```
# Öffne die Datei:
evals/sample-contracts/01-saas-vertrag-cloudflow.md

# Verwende diesen Prompt:
Ich bin Jurist bei den Kommunalbetrieben Dornbirn und soll den beiliegenden 
SaaS-Vertrag mit CloudTech Solutions prüfen. Wir sind der Kunde. Der Vertrag ist 
noch nicht unterschrieben (Entwurf). Bitte prüfe den Vertrag umfassend aus unserer 
Sicht und gib mir eine Risikobewertung mit Redlines. Österreichisches Recht ist 
anwendbar.
```

**Erwartete Qualitätskriterien:**
- Referenzdateien werden gelesen (erkennbar an spezifischen Norm-Zitaten)
- Vertragstyp und Rechtsordnung korrekt identifiziert
- Ampelklassifikation (GRÜN/GELB/ROT) für jeden Prüfpunkt
- Numerische Risikoscores (Schwere × Wahrscheinlichkeit) ohne Rechenfehler
- Redlines auf Deutsch mit Norm-Verweisen
- Fehlende Klauseln als Befund markiert (nicht übersprungen)

### Automatisiertes Testen

Die `evals.json` ist so strukturiert, dass sie in ein automatisiertes Eval-Framework integriert werden kann:

```json
{
  "id": 1,
  "title": "SaaS-Vertrag Review",
  "prompt": "...",
  "files": ["evals/sample-contracts/01-saas-vertrag-cloudflow.md"],
  "expected_output": "Freitext-Beschreibung des erwarteten Ergebnisses",
  "expectations": [
    "Identifiziert den Vertrag als ENTWURF",
    "Liest references/it-contracts.md",
    "Markiert fehlenden AVV als ROT/KRITISCH"
  ]
}
```

Jedes `expectations`-Array enthält einzeln prüfbare Kriterien, die als Checkliste oder für LLM-basierte Bewertung verwendet werden können.

## Abgedeckte Rechtsgebiete

### DACH-Zivilrecht
- **Österreich**: ABGB, UGB, KSchG, DSG
- **Deutschland**: BGB, HGB, UWG
- **Schweiz**: OR, DSG nF

### EU-Regulatorik
- DSGVO (Datenschutz-Grundverordnung)
- NIS2 (Netz- und Informationssicherheit)
- EU AI Act (KI-Verordnung)
- Data Act (Datenverordnung)
- DSA / DMA (Digital Services Act / Digital Markets Act)
- eIDAS 2.0
- Cyber Resilience Act (CRA)

### Fachspezifisch
- AGB-Kontrolle (§§ 305–310 BGB, § 879 ABGB, KSchG)
- Werkvertrag vs. Dienstvertrag
- EVB-IT / ÖNORM-Standards
- Vergaberecht (öffentliche IT-Beschaffung)

## Zusammenspiel mit anderen Skills

Dieser Skill ergänzt den allgemeinen **Contract Analysis Skill** (`skills/contract-analysis`) für den DACH/EU-IT-Bereich. Die Routing-Logik in der SKILL.md stellt sicher, dass Anfragen automatisch an den richtigen Skill geleitet werden:

- **Dieser Skill**: IT-Vertragstypen, DACH/EU-Recht, DSGVO/AVV, NIS2, AGB-Kontrolle, Werkvertrag-Analyse
- **Contract Analysis Skill**: UK-Recht, Bauverträge, Beschaffung, Arbeitsrecht, Immobilien, allgemeine PE Due Diligence

## Lizenz

Siehe [LICENSE](../../LICENSE) im Wurzelverzeichnis des Repositories.
