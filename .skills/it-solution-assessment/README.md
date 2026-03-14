# IT Solution Assessment

Strukturierte Bewertung von IT-Projektanträgen für SaaS- und On-Premises-Lösungen.

## Überblick

Dieser Skill befähigt GitHub Copilot, IT-Lösungen systematisch zu bewerten — ob SaaS-Dienst oder On-Premises-Software. Er liefert eine gewichtete Gesamtbewertung mit Ampelsystem, K.O.-Kriterien-Prüfung und konkreter Handlungsempfehlung.

**Kombiniert fünf Bewertungsdimensionen:**

1. **Vendor Assessment** — Firmensitz, Eigentümerstruktur, Stabilität, Marktposition
2. **Sicherheit & Compliance** — Zertifizierungen, Verschlüsselung, DSGVO, NIS2
3. **SaaS-Kriterien** — Data Residency, SLA, API, Multi-Tenancy, Datenportabilität
4. **On-Prem-Kriterien** — Technologie-Stack, Runtime, Deployment, Skalierbarkeit
5. **Integration & Architektur** — API, Protokolle, IdP-Anbindung, Systemlandschaft

> **Hinweis**: Der Skill unterstützt bei der strukturierten Bewertung, ersetzt aber keine formale Beschaffungsentscheidung. Alle Bewertungen sollten von den zuständigen Fachbereichen (IT, Security, Legal, Einkauf) geprüft werden.

## Verzeichnisstruktur

```
.skills/it-solution-assessment/
├── SKILL.md                          # Hauptinstruktionen & Methodik
├── README.md                         # Diese Datei
└── references/
    ├── saas-criteria.md              # SaaS-Kriterienkatalog mit Prüffragen
    ├── onprem-criteria.md            # On-Prem-Kriterienkatalog mit Prüffragen
    ├── vendor-assessment.md          # Vendor Due Diligence Checkliste
    ├── security-compliance.md        # Sicherheit, Zertifikate, Regulatorik
    └── scoring-templates.md          # Bewertungsvorlagen & Vergleichsmatrix
```

## Trigger-Beispiele

- *„Bewerte diese SaaS-Lösung für uns"*
- *„Erstelle einen IT-Steckbrief für [Produkt]"*
- *„Vergleiche Lösung A vs. Lösung B"*
- *„IT-Projektantrag bewerten"*
- *„Vendor Due Diligence für [Anbieter]"*
- *„Make-or-Buy-Analyse"*
- *„On-Prem vs. SaaS Vergleich"*

## Ausgabeformate

| Format | Zweck | Zielgruppe |
|---|---|---|
| **Steckbrief** | Einseitige Zusammenfassung mit Ampel | Management, IT-Leitung |
| **Detailbewertung** | Vollständige Kriterienmatrix mit Scores | IT-Architektur, Security |
| **Vergleichsmatrix** | Gegenüberstellung 2–3 Lösungen | Entscheidungsgremien |
| **Entscheidungsvorlage** | Formale Vorlage für IT-Board | Lenkungsausschuss |

## Bewertungsschema

```
Score:    0 = nicht erfüllt     1 = teilweise     2 = erfüllt     3 = übertrifft

Gewicht:  ●●● Kritisch (×3)    ●● Wichtig (×2)   ● Nice-to-have (×1)

Ampel:    ≥ 80% GRÜN           60–79% GELB        < 60% ROT
```

### K.O.-Kriterien (Score 0 → automatisch ROT)

- Data Residency nicht EU (wenn gefordert)
- Keine SSO/OIDC-Fähigkeit
- Kein AVV/DPA verfügbar (SaaS)
- Keine Zertifizierung (ISO 27001 / SOC 2)
- Keine Verschlüsselung at rest & in transit
- Vendor-Lock-in ohne Datenexport
- End-of-Life absehbar (< 3 Jahre)

## Beispiel: SaaS-Steckbrief

```markdown
# IT-Lösungsbewertung: Contoso Project Hub

## Steckbrief

| Merkmal | Detail |
|---|---|
| Produkt | Contoso Project Hub v3.2 |
| Anbieter | Contoso Inc., San Francisco, ~2.000 MA |
| Typ | SaaS (Multi-Tenant) |
| Einsatzzweck | IT-Projektportfolio-Management |
| Gesamtscore | 78% 🟡 |

## Gesamtbewertung

| Kategorie          | Score | Gewicht | Ergebnis |
|---------------------|-------|---------|----------|
| Vendor              | 2.4   | ●●      | 4.8/6   |
| Sicherheit          | 2.7   | ●●●     | 8.1/9   |
| SaaS-Kriterien      | 2.1   | ●●●     | 6.3/9   |
| Integration         | 2.0   | ●●      | 4.0/6   |
| **Gesamt**          |       |         | **78%** 🟡 |

## Empfehlung

Bedingt empfohlen. Stärken bei Sicherheit (SOC 2 Type II, ISO 27001),
Schwäche bei API-Umfang (kein Bulk-Export) und Data Residency
(Backup-Standort USA). Auflagen: Verhandlung EU-only Backup,
API-Roadmap für Bulk-Export einholen.
```

## Referenzdateien

| Datei | Inhalt | Wann gelesen |
|---|---|---|
| [saas-criteria.md](references/saas-criteria.md) | SaaS-spezifischer Kriterienkatalog | Bei SaaS-Bewertungen |
| [onprem-criteria.md](references/onprem-criteria.md) | On-Prem-spezifischer Kriterienkatalog | Bei On-Prem-Bewertungen |
| [vendor-assessment.md](references/vendor-assessment.md) | Vendor Due Diligence | Immer |
| [security-compliance.md](references/security-compliance.md) | Sicherheit & Regulatorik | Immer |
| [scoring-templates.md](references/scoring-templates.md) | Bewertungsvorlagen | Immer |
