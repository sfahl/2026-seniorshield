# 08 · Risiken und offene Fragen

## Lesehilfe

Diese Datei ist *bewusst ehrlich* zu den Schwachstellen der Idee. Sie ist nicht für Investoren gedacht, sondern für die interne Arbeit. Sie ergänzt das Pitch-Dokument und das Pitch-Deck, die naturgemäß stärker positionierend sind.

Drei Kategorien:

- **Strukturelle Risiken** — bekannt, mit Mitigation strategisch adressierbar
- **Offene Fragen** — Entscheidungen, die noch zu treffen sind, mit Auswirkung auf Strategie
- **Annahmen, die wir explizit machen** — Stellen, an denen wir auf Basis unvollständiger Information entschieden haben

---

## Strukturelle Risiken

### 1. Beamtenstatus und NHG-Nebentätigkeit

**Risiko:** Das niedersächsische Beamtenrecht erlaubt Nebentätigkeiten nur unter klaren Bedingungen. Eine genehmigungspflichtige Tätigkeit, die nicht angezeigt oder genehmigt ist, kann disziplinarrechtliche Konsequenzen haben — bis hin zum Verlust des Beamtenstatus in extremen Fällen.

**Mitigation:**
- Frühe Anzeige und ggf. Genehmigung der Nebentätigkeit
- Minderheitsbeteiligung ohne operative Geschäftsführung (Beirat-Vorsitz)
- Sauber dokumentierter Zeitaufwand (typisch max. 1 Tag/Woche, hier vermutlich noch weniger)
- Trennung zwischen wissenschaftlicher Lehrstuhltätigkeit und Beirat-Funktion

**Restrisiko:** Auch bei sauberer Anzeige können sich Anforderungen ändern (Wissenschaftsfreiheitsgesetz, Hochschulgesetz). Ein konservativer Berater empfiehlt, alle Equity-Erlöse rechtzeitig juristisch zu dokumentieren und Aktivitäten klar zu trennen.

### 2. KKMU-Wettbewerbsverbot

**Risiko:** Aus früheren Beteiligungen bestehen vertragliche Wettbewerbsabgrenzungen. Eine neue Gründung in einem benachbarten Bereich könnte als Wettbewerbsverstoß ausgelegt werden, mit zivilrechtlichen Folgen.

**Mitigation:**
- Schriftliche Abgrenzung der Geschäftsfelder mit Mitgesellschaftern vor Gründungs-Vertrag
- Klare strategische Differenzierung (KKMU adressiert KMU-Cybersecurity B2B, SeniorShield adressiert Senior:innen B2B2C)
- Notarielle Bestätigung als Conditions Precedent in Pre-Seed-Term-Sheet

**Restrisiko:** Wettbewerbsverbots-Verträge enthalten oft generische Formulierungen ("Cybersicherheit"). Auch eine offensichtlich abgegrenzte Tätigkeit kann formal in den Schutzbereich fallen. Anwaltsmemorandum unverzichtbar.

### 3. Co-Founder-Risiko

**Risiko:** Ohne CEO mit operativem Banking-Profil und CTO mit B2B2C-SaaS-Erfahrung sind alle Pläne hypothetisch. Eine falsche Wahl kostet 12–18 Monate und ist im Cap-Table schwer rückgängig zu machen.

**Mitigation:**
- Reverse Vesting für *alle* Gründer (inkl. Sascha) über 4 Jahre mit 1-Jahr-Cliff
- Probemonate vor Gründung (formale Beratungsverträge, dann Festanstellung)
- Klare Rollenabgrenzung mit dokumentierten Erwartungen

**Restrisiko:** Co-Founder-Fit ist erfahrungsgemäß auch nach ausführlichen Vorgesprächen schwer vorherzusagen. Investoren wissen das und akzeptieren ein 1-Jahres-Cliff als üblich.

### 4. Adoption-Risiko bei Endnutzerin

**Risiko:** Selbst gut designte Senior-Apps haben 60–80 % Drop-off in den ersten 90 Tagen. Self-Service-Onboarding scheitert oft.

**Mitigation:**
- **Bank-vermitteltes Onboarding** im Anker-Pilot (Bank-Mitarbeiter:in installiert App in Senior-Beratungs-Termin gemeinsam)
- **Pflegedienst-vermitteltes Onboarding** über eUL-Anteil der DiPA-Erstattung
- Mikro-Training-Funktion mit lokalen Fall-Geschichten als Aktivierungs-Treiber
- Periodische Sicherheits-Check-ups im 3-Monats-Rhythmus

**Restrisiko:** Adoption ist *nicht* durch UX-Polish allein lösbar. Es braucht ein Aktivierungs-Konzept, das eingebettet ist in Lebenswelt — und das wird im MVP wahrscheinlich noch nicht perfekt sein.

### 5. KI-Vertrauens-Risiko (False Negatives)

**Risiko:** Wenn die App einmal eine offensichtliche Betrugssituation als "harmlos" klassifiziert und ein Senior 50.000 € verliert, kann das Vertrauen sofort kippen — das Produkt wäre öffentlich verbrannt.

**Mitigation:**
- Konservative Konfidenz-Schwellen mit Default zu "im Zweifel menschliche Hilfe"
- 24/7-Hotline mit echten Berater:innen als Premium-Tier (wichtigste Komponente, nicht nachgeschobenes Feature)
- Klare Kommunikation der Limitationen im Onboarding
- Hybride Architektur LLM + Regel-Schicht, statt LLM-only

**Restrisiko:** Selbst bei konservativem Design ist ein einzelner Fehl-Fall medial verheerend. Krisen-Kommunikations-Plan vorbereiten *bevor* der erste Fall passiert.

### 6. Datenresidenz und Souveränität

**Risiko:** Verarbeitung sensibler Inhalte (Stimmaufnahmen, private Kommunikation, Finanzdaten in Folge-Schritten) bei US-Cloud-Provider gefährdet BSI-/Pflegekassen-Anschlussfähigkeit.

**Mitigation:**
- Hosting in Deutschland ab Tag 1 (Ionos, Hetzner, OVH-DE, T-Systems)
- BSI C5 Testat als 18-Monats-Ziel
- ISO 27001 in Vorbereitung
- DSGVO-Folgenabschätzung früh

**Restrisiko:** DE-Hosting ist teurer und potenziell langsamer als AWS/GCP. Engineering-Komplexität bei ML-Inferenz auf DE-souveränen Stacks.

### 7. DiPA als Versprechen, nicht Garantie

**Risiko:** Das Erprobungsverfahren ist neu, BfArM-Praxis empirisch unerprobt, Pflegekassen-Bewilligungspraxis ebenfalls. Antrag kann scheitern, sich verzögern, Auflagen enthalten, die das Geschäftsmodell beeinflussen.

**Mitigation:**
- BfArM-Beratung früh in Anspruch nehmen
- Wirknachweis-Studie methodisch sauber von Beginn an
- Geschäftsmodell auch ohne DiPA tragfähig (Bank-Kanal als Primär-Anker)
- DiPA als strategischer Hebel, nicht als Existenzgrundlage

**Restrisiko:** Wenn DiPA scheitert, fehlt 30–50 % des potenziellen ARR-Wachstums. Investoren-Story wird schwächer.

### 8. Forschungsethik-Dilemma (Dual Use)

**Risiko:** Wir arbeiten in der Produktentwicklung mit echten Senior:innen in echten Risiko-Situationen. Die Trennung zwischen "Produkt-Validierung" und "akademischer Forschung" muss juristisch und ethisch sauber sein, sonst entsteht ein Reputations- und Compliance-Risiko sowohl für die LUH als auch für das Startup.

**Mitigation:**
- IRB-Reviews für alle Studien getrennt zwischen Universität und Startup
- Keine Dual-Use-Daten zwischen Lehrstuhl und Startup ohne explizite Einwilligung der Teilnehmer:innen
- Saubere getrennte Vereinbarungen mit Probanden für Forschung vs. Produkt
- Beirat-Mitglied mit Forschungsethik-Expertise

**Restrisiko:** Auch bei sauberer Trennung kann der öffentliche Eindruck einer Vermischung entstehen.

### 9. Plattform-Asymmetrie iOS vs. Android

**Risiko:** Wenn die iOS-Variante deutlich weniger Funktionsumfang liefert als die Android-Variante, kann das einen erheblichen Anteil der Premium-Senior-Zielgruppe (iPhone-affin, höheres Einkommen) ausschließen.

**Mitigation:**
- Klare Kommunikation der Asymmetrie im Marketing
- Android-first-Strategie für Studien und Anker-Bank-Pilot
- iOS-Strategie als zweite Welle, mit klaren Erwartungen
- Apple-Public-Health-Programme sondieren

**Restrisiko:** Apple könnte zukünftig restriktiver werden statt liberaler. Es gibt keine Garantie, dass sich der Funktionsumfang auf iOS ausbauen lässt.

---

## Offene Fragen — Entscheidungen, die noch zu treffen sind

### Frage 1 — Produktname

**SeniorShield** ist Arbeitstitel. Kritik: zu angelsächsisch, zu frontal-sicherheitsbetont, möglicherweise stigmatisierend ("Senior" als Label, das viele Betroffene nicht für sich annehmen).

Alternative Richtungen:
- Neutralere Namen ("Beistand", "Sicherer Ruf", "Wegweiser")
- Markenname ohne semantische Senior-Anbindung (Vorbild Audible, Notruf-Knopf-Bezeichnungen)
- Aus dem Funktions-Wortfeld ("Zweite Meinung", "Klarheit", "Schutzkreis")

**Entscheidung:** Vor Markenregistrierung mit Senior-Zielgruppe testen.

### Frage 2 — DiPA-Anspruchsgruppe (Senior oder Angehöriger)

Beide sind nach BEEP möglich. Die DiPA-Studie ist methodisch sauberer, wenn wir uns für eine primäre Anspruchsgruppe entscheiden.

**Hypothese:** "Senior als primäre Anspruchsgruppe, Angehörige als sekundäre". Ökologische Validität wird am Senior gemessen, Angehörigenentlastung als sekundäres Outcome.

**Entscheidung:** Im Studiendesign-Arbeitspaket final klären.

### Frage 3 — Carrier-Partnerschaft (Telekom) — wann?

Deutsche Telekom hat seit Dezember 2025 Call Check aktiv. Eine frühe Partnerschaft (statt späterer Skalierung) könnte Netzzugang zu Anrufs-Metadaten geben, aber auch in Abhängigkeit drücken.

**Entscheidung:** Sondierungsgespräch in Phase 2 oder 3, formelle Partnerschaft erst ab Series A.

### Frage 4 — Internationale Expansion (AT/CH/NL) — wann?

Naheliegend nach DiPA-Listung. Aber: jedes Land hat eigene regulatorische und sprachliche Anforderungen.

**Entscheidung:** Erst ab Series A, mit klarer Reihenfolge (AT zuerst — gleiche Sprache, ähnliche Bankenlandschaft).

### Frage 5 — 24/7-Hotline mit echten Berater:innen — Aufbau wie?

Das Premium-Feature. Aber teurer Aufbau:
- Eigener Service-Center: 10–15 Mitarbeitende ab Seed, Standort wählen (Hannover, Berlin, ggf. Outsource-Partner)
- Outsourcing an Call-Center mit Senior-Service-Erfahrung
- Wohlfahrtsverband als Partner (Caritas, Diakonie haben Hotline-Infrastruktur)

**Entscheidung:** Wahrscheinlich Hybrid (Outsource für Erstaufnahme, Eskalation zu eigenen geschulten Mitarbeitenden). In Seed-Vorbereitung pilotieren.

### Frage 6 — Wann starten wir mit der Banken-Akquise?

Verlockend früh — sehr lange Verkaufszyklen. Aber: ohne MVP keine glaubwürdige Demo, ohne Co-Founder keine glaubwürdige Sales-Story.

**Entscheidung:** Erste *informelle* Sondierungsgespräche in Phase 1 (parallel zur Co-Founder-Suche), formelle Pilot-Verhandlungen erst nach Pre-Seed.

---

## Annahmen, die wir explizit machen

Diese Annahmen sind unsere "Best Guess" mit unvollständiger Information. Sie sollten regelmäßig überprüft werden.

1. **"Das DiPA-Verzeichnis bleibt 2026/2027 zentral leer."** Beobachtung: Stand Frühjahr 2026 leer. Annahme: 5–10 erste Listungen über die nächsten 18 Monate. Falsifizierbar durch BfArM-Pressemitteilungen.

2. **"Banken-Anker-Pilot in Norddeutschland gewinnbar."** Annahme basiert auf Standortvorteil Hannover und persönlichen Netzwerken. Falsifizierbar durch 5–7 ergebnislose Sondierungsgespräche.

3. **"BEEP-Gesetz öffnet Angehörigenentlastung als pflegerischen Nutzen sauber."** Annahme basiert auf Gesetzestext. Falsifizierbar durch BfArM-Beratungsgespräch, in dem die Kategorie inhaltlich nicht anerkannt wird.

4. **"Plattform-Restriktionen iOS/Android bleiben über 24 Monate stabil."** Annahme ungefährdet bzgl. Verschärfung. Aber: Apple könnte EU-Anpassungen über DMA-Druck ändern.

5. **"Sascha's Beamtenstatus erlaubt die Konstruktion."** Annahme basiert auf NHG-Standardpraxis. Falsifizierbar durch Anwalts-Memorandum, das anderen Schluss kommt.

6. **"Carefull et al. expandieren nicht vor 2027 nach Deutschland."** Annahme basiert auf bisherigen Aktivitäten. Falsifizierbar durch CrunchBase- oder Pitchbook-Signale.

---

## Was wir bei jeder Phase-Übergabe überprüfen sollten

Vor jeder Phasenübergang (M3 → M4, M9 → M10, M14 → M15) ein **Go/No-Go-Review** mit den folgenden Fragen:

1. Sind die strukturellen Risiken der Vorphase abgearbeitet oder mit klaren Mitigationen versehen?
2. Sind die offenen Fragen der Vorphase entschieden?
3. Haben sich die Annahmen seit der letzten Überprüfung bestätigt oder geschwächt?
4. Sind die operativen Meilensteine erreicht — oder gibt es Anpassungsbedarf?

Ohne Go/No-Go-Disziplin akkumulieren sich Risiken bis zur Krise.
