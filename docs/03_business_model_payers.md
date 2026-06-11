# 03 · Geschäftsmodell und Bezahler-Architektur

## Grundprinzip

Die Endnutzerin — der Senior selbst — soll **niemals an einer Paywall stehen**, schon gar nicht im Moment der Krise. Monetarisierung läuft strukturell über Dritte: Banken (Fraud-Loss-Avoidance), Pflegekassen (Erstattung als DiPA), oder erwachsene Kinder (B2C-Familienabos). Niemand bezahlt im Akutmoment, niemand bezahlt aus Angst.

## Drei sich ergänzende Bezahler-Kanäle

### Kanal 1 — B2B2C über Sparkassen und Volksbanken (Primär-Anker)

**Bezahler:** Bank-Institut. **Nutzer:** Senior-Kund:in. **Treiber:** vermiedene Fraud-Schäden + regulatorischer Druck durch Verbraucherschutz und § 675u BGB.

**Marktstruktur:**

- Sparkassen-Finanzgruppe: ~370 selbstständige Sparkassen, 2,49 Bio. € Bilanzsumme (größter Finanzdienstleister Europas)
- Genossenschaftssektor: 700+ Volks- und Raiffeisenbanken
- Dezentral organisiert — kein Plug-and-Play-Vertrieb, jedes Haus entscheidet selbst

**Pricing-Hypothese:**

- Basic-Lizenz: **2–4 € pro Senior-Kunde pro Jahr** (Pre-Call-Warnung + Second-Opinion-Engine)
- Premium-Lizenz: **6–10 € pro Senior-Kunde pro Jahr** (zusätzlich Live-Hotline mit echten Berater:innen, später Banking-Integration)

**Beispielrechnung pro Anker-Institut:**
- Sparkasse mit 200.000 Kunden, davon 30–40 % Senior-Anteil (60.000–80.000 Personen)
- 80.000 × 3 € = **240 Tsd. € ARR pro Anker** (Basic)
- Skalierung auf 30–40 Anker über 3 Jahre = **6–10 Mio. € ARR**

**Vertriebslogik:**

- Erstgespräche mit Vorstand Privatkunden oder Leitung Fraud/Compliance einzelner Häuser
- Anker-Pilot mit 1–2 Sparkassen / VR-Banken in Norddeutschland (Standortvorteil Hannover)
- Skalierung über DSGV-/BVR-Empfehlung oder über Verbund-IT-Dienstleister (Finanz Informatik, Atruvia)
- Politisch sensibles Thema mit Pressepotenzial ("Sparkasse schützt Senioren") — vorteilhaft

### Kanal 2 — DiPA-Erstattung über Pflegekasse (Strategischer Hebel)

**Bezahler:** Pflegekasse via DiPA-Erstattung nach § 40a SGB XI. **Nutzer:** Pflegebedürftige in Pflegegrad 1–5 (häusliche Pflege) + pflegende Angehörige.

**Erstattungsstruktur seit 1.1.2026:**

- **40 € pro Monat** für die DiPA selbst
- **30 € pro Monat** für ergänzende Unterstützungsleistungen (eUL) durch ambulante Pflegedienste
- Gesamt: bis zu **70 € pro Monat pro Pflegebedürftiger**

**Marktgröße:** 4 Mio. Pflegebedürftige in häuslicher Versorgung. Mit BEEP-Erweiterung (Angehörigenentlastung als pflegerischer Nutzen) realistisch erweiterbar auf 5–7 Mio. Haushalte mit mindestens einer pflegebedürftigen Person.

**Beispielrechnung:**

- 1–2 % Penetration des 4-Mio.-Pools = 40–80 Tsd. Nutzer:innen
- Bei 40 €/Monat × 12 = 480 € pro Nutzer:in pro Jahr
- → **19–38 Mio. € ARR-Potenzial allein aus diesem Kanal**

**Strategischer Wert:** First-Mover in leerem BfArM-Verzeichnis (Details in [`04_dipa_pathway.md`](04_dipa_pathway.md)). Erstattung gesetzlich garantiert. Schwer kopierbar durch internationale Wettbewerber.

**Caveat:** Pfad ist anspruchsvoll (Wirknachweis-Studie, BfArM-Antrag, 12–24 Monate Vorlauf), aber durch BEEP-Erprobungsverfahren erstmals venture-fähig.

### Kanal 3 — B2C-Familienabos (Margen-Kanal)

**Bezahler:** Erwachsene Kinder von Senior:innen (Sandwich-Generation). **Nutzer:** Senior + Familie.

**Pricing-Hypothese:**

- **12–19 € pro Monat** im Familien-Tier (1 Senior + bis zu 4 Vertrauenspersonen)
- Premium-Familien-Tier: 25–35 € pro Monat (1–3 Senioren + erweiterte Familie + Live-Hotline)

**Beispielrechnung:**

- 10.000 zahlende Familien-Abos in Jahr 3 × ~15 €/Monat × 12 = **1,8 Mio. € ARR**
- Vergleich zu Carefull: 119,99 USD/Jahr — vergleichbares Preisniveau

**Charakteristika:**

- Margenstark, aber Volumen-begrenzt
- Hohe Customer Acquisition Costs in einem hart umkämpften Werbeumfeld
- Hohe Abbruchquoten in den ersten 90 Tagen — Onboarding-Investition entscheidend
- *Nicht* primärer Volumen-Treiber, sondern Long-Tail-Ergänzung neben den institutionellen Kanälen

## Sequenzierung (3-Jahres-Aufbau)

| Phase | Primärfokus | Sekundärfokus |
|---|---|---|
| Jahr 1 (Pre-Seed → MVP) | Anker-Bank-Pilot | DiPA-Vorprüfung |
| Jahr 2 (Seed) | DiPA-Antrag (Erprobungsverfahren) + 5–10 Bank-Anker | B2C-Vorläufer |
| Jahr 3 (Series A) | DiPA-Listung + Bank-Skalierung | B2C-Aufbau, Carrier-Partnerschaft |

## Umsatz-Mix-Hypothese (Jahr 3)

| Kanal | ARR-Anteil | Charakter |
|---|---|---|
| Bank-Lizenzen | 60–70 % | Hochskaliert, defensiv |
| DiPA-Erstattung | 20–30 % | Wachstumshebel, hochmargig |
| B2C-Familienabos | 5–10 % | Margen, Long Tail |
| Services (Beratung, Übungen) | 5 % | Übergangs, sinkend über Zeit |

## Margen-Annahmen (Grobschätzung)

- **Banking-Lizenzen:** 75–85 % Bruttomarge (geringe Akquise-Kosten, hohe Lizenz-Marge nach Anker-Anbahnung)
- **DiPA:** 60–70 % Bruttomarge (regulatorische Compliance-Kosten, eUL-Anteil geht an Pflegedienste)
- **B2C:** 50–65 % Bruttomarge (hohe CAC, höhere Marketing-Investition)

## Was wir NICHT machen werden

- **Kein Performance-Marketing** in Phase 1. CAC zu hoch, Botschaft schwer zu landen ohne in Angstmacherei zu kippen.
- **Keine White-Label-Lizenzierung an Versicherer** in Phase 1, weil das die Markenbildung blockiert.
- **Keine Senior-Hardware** im MVP (Hardware-Begleitgerät ist Vision-Layer, nicht Geschäftskern).
- **Kein Einstieg in andere Märkte** (z.B. Österreich, Schweiz) vor Series A. Markt-spezifische Inhalte und regulatorische Pfade sind je Land neu.

## Schlüssel-Risiken im Geschäftsmodell

→ Detailliert in [`08_risks_and_open_questions.md`](08_risks_and_open_questions.md). Kurz:

- **Adoption-Risiko bei Endnutzerin** (Senior-Drop-off in den ersten 90 Tagen). Wirksamster Hebel: Bank- oder Pflegedienst-vermitteltes Onboarding statt Self-Service.
- **Bezahler-Fragmentierung** auf der Bank-Seite (370+700 Häuser, kein zentraler Hebel)
- **DiPA als Versprechen, nicht Garantie** — Verfahren neu, Pflegekassen-Bewilligungspraxis unerprobt
