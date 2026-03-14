# Vertragslebenszyklus — Fristen-Tracking

Referenzdatei für die systematische Erfassung und Überwachung aller vertragsrelevanten Fristen,
Termine und Meilensteine in IT-Verträgen.

## Wann diese Datei lesen

- Bei Vertragsportfolio-Übersichten (Fristen-Dashboard)
- Bei Verlängerungsprüfungen (Auto-Renewal-Analyse)
- Bei Kündigungsplanung (Exit-Timeline)
- Bei Compliance-Fristen (DSGVO-Löschfristen, NIS2-Meldepflichten)
- Bei Projektverträgen (Meilensteine, Abnahmen, Go-Live)

---

## 1. Fristen-Kategorien

### 1.1 Vertragslaufzeit

| Frist | Prüffrage | Typische Werte | Red Flag |
|---|---|---|---|
| **Erstlaufzeit** | Wie lange bindet der Vertrag initial? | 12–36 Monate | > 60 Monate ohne Sonderkündigungsrecht |
| **Verlängerungszeitraum** | Um wie lange verlängert sich der Vertrag automatisch? | 12 Monate | > 24 Monate Automatik-Verlängerung |
| **Kündigungsfrist (ordentlich)** | Wie viel Vorlauf braucht eine Kündigung? | 3–6 Monate vor Laufzeitende | > 12 Monate, < 1 Monat (zu kurz für Transition) |
| **Kündigungszeitpunkt** | Wann kann ordentlich gekündigt werden? | Zum Laufzeitende | Nur zu bestimmten Stichtagen |
| **Mindestlaufzeit** | Gibt es eine unkündbare Mindestphase? | Erstlaufzeit | Mindestlaufzeit > Erstlaufzeit |
| **Sonderkündigungsrecht** | Bei welchen Ereignissen kann vorzeitig gekündigt werden? | Insolvenz, Change of Control, wesentliche Pflichtverletzung | Kein Sonderkündigungsrecht definiert |

### 1.2 Automatische Verlängerung (Auto-Renewal)

| Prüfpunkt | Detail |
|---|---|
| **Auto-Renewal vorhanden?** | Ja/Nein — wenn nein, was passiert bei Ablauf? |
| **Opt-out-Frist** | Bis wann muss der Widerspruch eingehen? |
| **Erinnerungspflicht** | Muss der Anbieter vor Verlängerung informieren? (§ 309 Nr. 9 BGB bei AGB) |
| **Preisanpassung bei Verlängerung** | Gelten neue Preise? Index-Klausel? Unbeschränkte Erhöhung? |
| **Konditionen-Änderung** | Können sich AGB/SLA bei Verlängerung einseitig ändern? |

**DACH-Besonderheiten:**
- **DE (B2C/AGB)**: § 309 Nr. 9 BGB — Erstlaufzeit max. 2 Jahre, Verlängerung max. 1 Jahr, Kündigungsfrist max. 3 Monate
- **DE (B2B/AGB)**: Ähnliche Wertungen über § 307 BGB, aber nicht starr
- **AT (KSchG)**: Bei Verbraucherverträgen strenge Kontrolle automatischer Verlängerungen
- **CH**: Dispositive Regelung, aber Treu und Glauben (Art. 2 ZGB) als Grenze

### 1.3 Kündigungsfristen im Detail

| Kündigungsart | Frist | Voraussetzung | Rechtsgrundlage |
|---|---|---|---|
| **Ordentlich** | Vertraglich vereinbart (typisch 3–6 Monate) | Einhaltung der Frist und Form | Vertrag |
| **Außerordentlich (wichtiger Grund)** | Sofort / nach Nachfrist | Unzumutbarkeit der Fortsetzung | § 314 BGB / § 1118 ABGB |
| **Außerordentlich (Insolvenz)** | Sofort nach Kenntnis | Insolvenzantrag/-eröffnung Gegenseite | Vertrag + InsO/IO |
| **Außerordentlich (Change of Control)** | Vertraglich (typisch 30–90 Tage) | Gesellschafterwechsel > 50% | Vertrag |
| **Außerordentlich (Leistungsstörung)** | Nach erfolgloser Nachfrist | Wesentliche Pflichtverletzung, Schlechtleistung | § 323 BGB / § 918 ABGB |
| **Außerordentlich (Datenschutzverstoß)** | Sofort | Erheblicher DSGVO-Verstoß durch Auftragsverarbeiter | Art. 28 Abs. 3 lit. h DSGVO + Vertrag |
| **Widerruf (bei Verbrauchern)** | 14 Tage ab Vertragsschluss | Fernabsatz-/Außergeschäftsvertrag | §§ 355ff BGB / FAGG AT |

### 1.4 SLA-Review-Termine

| Termin | Prüffrage | Empfohlener Rhythmus |
|---|---|---|
| **SLA-Berichtsperiode** | Wann werden SLA-Reports fällig? | Monatlich |
| **SLA-Review-Meeting** | Wann wird die SLA-Performance formal bewertet? | Quartalsweise |
| **SLA-Neuverhandlung** | Wann können SLA-Zielwerte angepasst werden? | Jährlich / bei Verlängerung |
| **Service-Credit-Geltendmachung** | Bis wann müssen Credits beantragt werden? | Typisch 30 Tage nach Berichtsperiode |
| **Eskalationsfristen** | Wie schnell muss eskaliert werden? | Je nach Severity (critical: 1h, high: 4h) |

### 1.5 Projektmeilensteine (bei Werkverträgen / Implementierungen)

| Meilenstein | Frist | Konsequenz bei Verzug |
|---|---|---|
| **Kick-off** | [Datum] | Verzug Gesamtprojekt |
| **Anforderungsfreigabe / Pflichtenheft** | [Datum] | Mitwirkungsverzug Auftraggeber |
| **Design-/Architektur-Review** | [Datum] | Change-Request-Frist |
| **Testbereitstellung** | [Datum] | Verzug Auftragnehmer |
| **Abnahmetest** | [Datum, Dauer: X Tage] | Fiktive Abnahme bei Fristablauf? |
| **Go-Live** | [Datum] | Vertragsstrafe? |
| **Hypercare / Stabilisierung** | [Datum bis Datum] | Übergang in Regelbetrieb |
| **Gewährleistungsende** | [Datum] | Verjährung der Mängelrechte |

### 1.6 Compliance- und Regulatorik-Fristen

| Frist | Beschreibung | Zeitraum |
|---|---|---|
| **DSGVO — Datenschutzverletzung melden** | Meldung an Aufsichtsbehörde | 72 Stunden ab Kenntnis |
| **DSGVO — Betroffenenrechte** | Antwort auf Auskunfts-/Löschungsanfragen | 1 Monat (+ 2 Monate Verlängerung) |
| **DSGVO — AVV-Aktualisierung** | TOMs-Review, Sub-Processor-Updates | Mindestens jährlich |
| **DSGVO — Löschfristen** | Daten löschen nach Vertragsende | Gemäß Löschkonzept (typisch 30–90 Tage) |
| **NIS2 — Frühwarnung** | Erste Meldung an CSIRT | 24 Stunden |
| **NIS2 — Vorfallmeldung** | Detaillierte Meldung | 72 Stunden |
| **NIS2 — Abschlussbericht** | Umfassender Bericht | 1 Monat |
| **AI Act — Konformitätsbewertung** | Vor Inverkehrbringen von Hochrisiko-KI | Vor Go-Live |
| **Aufbewahrungspflichten** | Steuer-/Handelsrecht (UGB, HGB, BAO) | 7 Jahre (AT, CH) / 10 Jahre (DE) |

---

## 2. Ausgabeformat: Fristen-Tracker

### 2.1 Einzelvertrag — Fristen-Übersicht

```markdown
# Fristen-Tracker: [Vertragsbezeichnung]

| # | Frist | Datum / Zeitraum | Erinnerung | Status | Ampel |
|---|---|---|---|---|---|
| 1 | Erstlaufzeit endet | TT.MM.JJJJ | — | Aktiv | 🟢 |
| 2 | Kündigungsfrist (ordentlich) | X Monate vor Laufzeitende | TT.MM.JJJJ | Offen | 🟡 |
| 3 | Nächstes Kündigungsfenster | TT.MM.JJJJ | TT.MM.JJJJ | Offen | 🟡 |
| 4 | Auto-Renewal-Opt-out bis | TT.MM.JJJJ | TT.MM.JJJJ (–30 Tage) | Offen | 🔴 |
| 5 | SLA-Review | Quartalsweise | Nächster: TT.MM.JJJJ | Wiederkehrend | 🟢 |
| 6 | AVV/TOMs-Review | Jährlich | Nächster: TT.MM.JJJJ | Wiederkehrend | 🟢 |
| 7 | Preisanpassung möglich ab | TT.MM.JJJJ | TT.MM.JJJJ (–60 Tage) | Offen | 🟡 |
| 8 | Gewährleistung endet | TT.MM.JJJJ | TT.MM.JJJJ (–30 Tage) | Aktiv | 🟢 |
| 9 | Daten-Löschfrist nach Ende | +X Tage nach Vertragsende | — | Inaktiv | — |

## Kritische Fristen (nächste 90 Tage)

| Frist | Datum | Handlung erforderlich |
|---|---|---|
| [Frist] | TT.MM.JJJJ | [Beschreibung der Maßnahme] |

## Empfehlung

[Konkreter Hinweis, welche Fristen Aufmerksamkeit brauchen]
```

### 2.2 Portfolio — Fristen-Dashboard

```markdown
# Fristen-Dashboard: IT-Vertragsportfolio

Stand: [Datum]

## Übersicht

| Kennzahl | Wert |
|---|---|
| Aktive Verträge | X |
| Fristen nächste 90 Tage | X |
| Kritische Fristen (🔴) | X |
| Auto-Renewal ohne Opt-out-Planung | X |

## Nächste Kündigungsfenster

| Vertrag | Anbieter | Typ | Kündigungsfrist bis | Verlängerung um | Ampel |
|---|---|---|---|---|---|
| [Vertrag A] | [Anbieter] | SaaS | TT.MM.JJJJ | 12 Monate | 🔴 |
| [Vertrag B] | [Anbieter] | Outsourcing | TT.MM.JJJJ | 24 Monate | 🟡 |
| [Vertrag C] | [Anbieter] | Wartung | TT.MM.JJJJ | 12 Monate | 🟢 |

## Verträge mit Auto-Renewal (nächste 6 Monate)

| Vertrag | Opt-out bis | Verlängerung | Preisänderung | Status |
|---|---|---|---|---|
| [Vertrag] | TT.MM.JJJJ | +X Monate | Ja (Index) / Nein / Unklar | ⏳ / ✅ / ❌ |

## SLA-Review-Kalender

| Vertrag | Nächster Review | Frequenz | Letzter Score |
|---|---|---|---|
| [Vertrag] | TT.MM.JJJJ | Quartalsweise | 99,8% ✅ |

## Compliance-Fristen

| Vertrag | Frist | Typ | Fällig |
|---|---|---|---|
| [Vertrag] | AVV-Review | DSGVO | TT.MM.JJJJ |
| [Vertrag] | TOMs-Nachweis | DSGVO | TT.MM.JJJJ |
| [Vertrag] | NIS2-Audit | NIS2 | TT.MM.JJJJ |

## Handlungsempfehlungen

1. 🔴 **[Vertrag A]**: Kündigungsfenster in X Tagen — Entscheidung über Verlängerung treffen
2. 🟡 **[Vertrag B]**: SLA-Review überfällig — Termin vereinbaren
3. 🟡 **[Vertrag C]**: AVV nicht aktualisiert seit > 12 Monaten — TOMs-Review anstoßen
```

---

## 3. Fristen-Extraktion aus Vertragstext

### Extraktionsregeln

Bei der Analyse eines Vertrags systematisch alle Fristen identifizieren und in die Fristen-Tabelle eintragen:

1. **Laufzeit-Klauseln** suchen: "Laufzeit", "Vertragsbeginn", "Vertragsdauer", "befristet", "unbefristet"
2. **Kündigungs-Klauseln** suchen: "Kündigung", "Kündigungsfrist", "kündbar", "ordentlich", "außerordentlich", "fristlos", "wichtiger Grund"
3. **Verlängerungs-Klauseln** suchen: "verlängert sich", "automatisch", "stillschweigend", "Opt-out", "Widerspruch"
4. **Fristen in Klauseln** suchen: "innerhalb von X Tagen/Wochen/Monaten", "spätestens", "unverzüglich", "bis zum", "Frist"
5. **SLA-Termine** suchen: "Review", "Berichtszeitraum", "Service Credit", "Eskalation"
6. **Projekt-Meilensteine** suchen: "Meilenstein", "Phase", "Abnahme", "Go-Live", "Kick-off", "Übergabe"

### Warnsignale bei Fristen

| Warnsignal | Bewertung | Empfehlung |
|---|---|---|
| Keine Laufzeit definiert (bei Dauerschuldverhältnis) | 🔴 ROT | Laufzeit und Kündigungsrecht vereinbaren |
| Automatische Verlängerung > 24 Monate | 🔴 ROT | Auf max. 12 Monate begrenzen |
| Kündigungsfrist > 12 Monate | 🔴 ROT | Branchenüblich 3–6 Monate |
| Kein Sonderkündigungsrecht | 🟡 GELB | Mindestens bei Insolvenz und wesentlicher Pflichtverletzung |
| Kein SLA-Review-Mechanismus | 🟡 GELB | Quartalsweisen Review vereinbaren |
| Keine Transition-Frist nach Kündigung | 🔴 ROT | Bridge-Phase (3–6 Monate) vereinbaren |
| Fiktive Abnahme nach < 5 Tagen | 🔴 ROT | Mindestens 10–20 Arbeitstage |
| Keine Erinnerungspflicht vor Auto-Renewal | 🟡 GELB | 30–60 Tage vor Opt-out-Frist |
| Preisanpassung ohne Cap bei Verlängerung | 🟡 GELB | Index-Bindung oder prozentualen Cap vereinbaren |
