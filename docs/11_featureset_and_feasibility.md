# 11 · Featureset und technische Machbarkeit

## Warum diese Datei wichtig ist

Diese Datei leitet aus der Betrugs-Taxonomie ([`10_fraud_landscape_research.md`](10_fraud_landscape_research.md)) ein konkretes Featureset ab und prüft jede Funktion gegen die Plattform-Realität ([`05_platform_and_legal.md`](05_platform_and_legal.md)). Sie ist die Brücke zwischen „wovor schützen wir" und „was bauen wir tatsächlich" — und damit die Grundlage für MVP-Scope, CTO-Gespräche und die Demonstration der technischen Machbarkeit gegenüber Investoren.

Detailgrad bewusst auf der **strategischen Ebene**: Erkennungsheuristik, Eingabemodus, Plattform-Machbarkeit, MVP-Priorität. Konkrete APIs, Datenflüsse und Modell-Pipelines folgen in einem separaten technischen Arbeitspaket (für CTO-Onboarding/technische DD).

## Die Designlogik: von psychologischen Hebeln zu Features

Der zentrale Befund aus Datei 10 bestimmt die gesamte Architektur: Über alle Betrugsfamilien hinweg wirken nur **sechs wiederkehrende psychologische Hebel** — Autorität, künstlicher Zeitdruck, Angst/Schock, Isolation, Vortäuschung von Vertrautheit, Gier/Hoffnung. Die einzelnen Legenden („Enkel im Unfall", „gesperrtes Konto", „Traumrendite") wechseln ständig; die Hebel bleiben stabil.

Daraus folgt das oberste Designprinzip des Featuresets: **Die Erkennung setzt auf den Hebeln auf, nicht auf den Legenden.** Eine Klassifikation, die „erkennt ein Auto­unfall-Szenario" lernt, ist nach der nächsten Maschen-Iteration veraltet. Eine Klassifikation, die „erkennt die Kombination aus Autoritätsbehauptung + extremem Zeitdruck + Geheimhaltungsforderung + Geldforderung" erkennt, bleibt robust. Das ist gleichzeitig der Defensibility-Anker (vgl. wissenschaftlich validierte UX in Datei 02) und die Antwort auf die KI-Eskalation, die klassische Erkennungs-Tipps entwertet.

Zweites Prinzip, direkt aus der Kill-Chain-Analyse: Wirksamer Schutz muss **vor dem Geldabfluss** greifen, weil dieser fast immer irreversibel ist. Features werden danach priorisiert, wie früh und wie zuverlässig sie in der Kill Chain ansetzen.

## Featurekatalog nach Schutzschichten

Die Features sind den drei Schutzschichten aus Datei 01 zugeordnet. Für jedes Feature: adressierte Betrugsfamilie/Phase, Erkennungsheuristik (welche Signale), Eingabemodus, Plattform-Machbarkeit, MVP-Priorität.

### Schicht 1 — Pre-Call-/Pre-Message-Warnung (Phase 1: eingehender Kontakt)

**F1.1 · Rufnummern-Warnung (Pre-Call).** Adressiert Familie A3 (falsche Polizei), B1 (falsche Bank), D3 (Gewinnspiel) — alle nummernbasiert. Heuristik: Abgleich eingehender Nummer gegen kontinuierlich gepflegte Datenbank (Crowdsourcing + BNetzA + Verbraucherzentralen + Polizei). Eingabemodus: passiv, kein Nutzerzutun. Plattform: **Android reaktiver** (CallScreeningService erlaubt Klassifikation eingehender Anrufe), **iOS nur statisch** (Call Directory Extension liefert vorab eine Nummernliste an die Telefon-App, kein Echtzeit-Crowdsourcing-Abgleich). Komplementär zu Carrier-Diensten (Telekom Call Check, >300.000 Warnungen/Tag), die aber laut Anbieter „nicht unfehlbar" sind und nur bekannte Nummern erfassen. **MVP: ja, mit klar kommunizierter Plattform-Asymmetrie.**

**F1.2 · Spoofing-Hinweis.** Adressiert A3/B1, deren Kernmechanik Call-ID-Spoofing der 110 oder echter Bank-Nummern ist. Heuristik: kontextuelle Aufklärung statt Erkennung — wenn eine als „Polizei/110" oder „Bank" angezeigte Nummer anruft, blendet die App den Hinweis ein, dass diese Anzeige fälschbar ist und die echte Polizei nie unter 110 anruft. Eingabemodus: passiv/kontextuell. Plattform: auf beiden machbar als Begleithinweis. **MVP: ja (geringer Aufwand, hoher Aufklärungswert).**

**F1.3 · SMS-/Link-Quarantäne.** Adressiert C3 (Smishing), C1 (Anbahnungs-SMS). Heuristik: Link-/Absender-Analyse, Mustererkennung typischer Smishing-Texte. Plattform: **starke Asymmetrie** — Android voller Lesezugriff (mit Onboarding-Aufwand), iOS nur rudimentärer Filter für unbekannte Absender; zudem hat Apple mit iOS 26 „Screen Unknown Senders" systemweit eingeführt, was den Eigen-Mehrwert auf iOS senkt. **MVP: nein — zweite Welle**, wie in Datei 05 festgelegt.

### Schicht 2 — Second-Opinion-Engine (Phase 3: Beleg vorhanden / Entscheidung) — MVP-Kern

Dies ist das Herzstück, weil es Phase 3 über **alle** Familien hinweg adressiert und nicht von Plattform-Audio-Restriktionen abhängt: Der Nutzer bringt den Beleg aktiv ein, statt dass die App heimlich mithört. Vier Eingabemodi:

**F2.1 · Foto/Screenshot-Prüfung.** Adressiert C1 (WhatsApp „Hallo Mama"), C2 (Phishing-Mail), C3 (Smishing), C4 (QR/Brief), D2 (Fake-Trading-Werbung). Heuristik: Bild-/Textverständnis (LLM-gestützt) extrahiert Inhalt → Hebel-Klassifikation (Autorität? Zeitdruck? Identitätsvortäuschung? Geldforderung? verdächtiger Link/Empfänger?). Eingabemodus: Foto oder Screenshot. Plattform: voll machbar auf beiden (Standard-Foto/Share-Sheet, keine Sonder-API). **MVP: ja, höchste Priorität.**

**F2.2 · Sprachnotiz-Prüfung (nachträglich).** Adressiert A1/A2/A3 (Telefon-Schockmaschen), B1/B2. Heuristik: Nutzer spricht *selbst und bewusst* nach einem verdächtigen Anruf nach, was gesagt wurde (oder nimmt eine eigene Gedächtnisnotiz auf) → Transkription → Hebel-Klassifikation. Wichtig: **nicht** das heimliche Mitschneiden des Anrufs (juristisch/technisch ausgeschlossen, Datei 05), sondern die selbst-initiierte Schilderung. Plattform: voll machbar (normales Mikrofon). **MVP: ja.**

**F2.3 · Nummern-Klassifikation.** Adressiert A3, B1, D3. Heuristik: Nutzer gibt die Anrufernummer ein → Datenbank-Abgleich + Spoofing-Hinweis (Brücke zu F1.1). Plattform: voll machbar. **MVP: ja.**

**F2.4 · Geführte Frage-Antwort-Sequenz.** Adressiert *alle* Familien, besonders Situationen ohne Beleg (laufender Druck, kein Screenshot). Heuristik: kurze, würdevolle Entscheidungsbaum-/Dialog-Sequenz, die gezielt die Hebel abfragt („Werden Sie zur Eile gedrängt? Sollen Sie es geheim halten? Wird Geld oder eine TAN verlangt?"). Dies ist auch der Träger der etablierten Verhaltensregeln (Rückruf unter bekannter Nummer, Familien-Codewort). Plattform: voll machbar. **MVP: ja.**

Output aller vier Modi einheitlich: farbkodierte Einschätzung in unter 30 Sekunden mit konkreter Handlungsempfehlung. Hybride Architektur aus LLM-Klassifikation und **konservativ-regelbasierter Validierung** — bei Unsicherheit immer Eskalation zu menschlicher Hilfe, nie ein falsches „alles in Ordnung" (False-Negative-Risiko, besonders bei sechsstelligen Einzelschäden in D2).

### Schicht 3 — Live-Begleitmodus (Phase 2: laufendes Gespräch) — die Interventionslücke

> **Korrektur Juni 2026:** Die ursprüngliche Annahme, eine App könne während des Anrufs den Lautsprecher übers Mikrofon mithören und eine Ansage ins Gespräch einspielen, wurde gegen primäre Quellen widerlegt — beides ist auf iOS und Android durch die Audio-Session-Arbitrierung blockiert (Details in [`05_platform_and_legal.md`](05_platform_and_legal.md), Abschnitt „Kritische Korrektur"). Schicht 3 ist daher in zwei Stufen gesplittet.

**F3.1a · Bildschirm-basierter Live-Begleiter (App, MVP).** Adressiert die zentrale, heute unbesetzte Phase-2-Lücke bei Familie A/B — **ohne Zugriff auf das Call-Audio.** Mechanik: Ein-Knopf-Aktivierung → die App führt parallel auf dem Bildschirm durch eine ruhige, großformatige Coaching-Sequenz (Hebel-Abfrage, Verhaltensregeln). Der Abschreckungseffekt entsteht **verhaltensbasiert**: Die App leitet den Senior an, einen Satz *selbst laut auszusprechen* („Ich lasse diesen Anruf gerade von meiner Sicherheits-App prüfen"). Das bricht die Hebel **Heimlichkeit/Isolation**, auf die A2/A3 zwingend angewiesen sind — ohne jeden Eingriff in den Audio-Stream und rechtlich unkritisch (kein fremdes Wort wird verarbeitet). Plattform: voll machbar auf beiden. **MVP: ja — aber unvalidiert**; der Validierungs-Steckbrief dazu steht in [`12_validation_brief_layer3.md`](12_validation_brief_layer3.md).

**F3.1b · Audio-Live-Begleitung (nur Hardware-Begleitgerät, Vision-Layer 2).** Echtes Mithören + Ansage in den Raum ist **nur out-of-band** realisierbar, über ein vom Telefon unabhängiges Gerät, das nicht der Audio-Session-Arbitrierung unterliegt. Damit wird der Hardware-Layer vom „80+-Komfort" zum einzigen tragfähigen Pfad für Live-Audio-Wirkung aufgewertet. Plattform: entfällt (eigene Hardware). **MVP: nein** — Vision-Layer 2.

### Querschnittsfunktionen

**F4.1 · Familien-Codewort.** Adressiert A1/A2 und besonders die KI-Stimmklon-Variante. Von Polizei und FTC als „derzeit wirksamster Schutz gegen Voice Cloning" benannt (Datei 10). Vorab im Vertrauenspersonen-System hinterlegtes Wort, das die App im Verdachtsfall abzufragen anleitet. Plattform: trivial machbar. **MVP: ja, prominent.**

**F4.2 · Graduiertes Vertrauenspersonen-System.** Menschliche Eskalation als Backup der konservativen Konfidenz. Strukturelle Resilienz gegen Caregiver-Fraud durch Wahl außerhalb der Pflegekonstellation. Plattform: machbar. **MVP: ja.**

**F4.3 · Risikoprofil-Assistent + Mikro-Training.** Phase-0-Härtung; Aktivierungs-Treiber gegen Drop-off. Plattform: machbar. **MVP: ja (schlank).**

**F4.4 · Heuristisches Frühwarnmuster für Langzeitmaschen (Familie D).** Adressiert Romance Scam / Pig Butchering, die über Wochen und plattformfern laufen und sich der Akut-Intervention entziehen. Heuristik: konversationelles Muster statt Einzelnachricht — Kanalwechsel weg von der Plattform, früh nach Handynummer gefragt, „letzte Hoffnung", abgesagte Treffen, niedrige Erst-Einzahlung mit sichtbaren Gewinnen, Auszahlung nur gegen Gebühren, Recovery-Anrufe Jahre später. Eingabemodus: Foto/Screenshot der Chatverläufe oder geführter Selbst-Check. Plattform: machbar über F2.1/F2.4. **MVP: reduziert** — als geführter Selbst-Check, volle Mustererkennung in zweiter Welle (siehe offene Frage unten).

## Plattform-Machbarkeitsmatrix

| Feature | iOS | Android | MVP |
|---|---|---|---|
| F1.1 Rufnummern-Warnung | Statisch (Call Directory) | Reaktiv (CallScreening) | Ja* |
| F1.2 Spoofing-Hinweis | Ja | Ja | Ja |
| F1.3 SMS-/Link-Quarantäne | Rudimentär (unbek. Absender) | Voll (mit Onboarding) | Nein (2. Welle) |
| F2.1 Foto/Screenshot | Voll | Voll | Ja (Top) |
| F2.2 Sprachnotiz (nachträglich) | Voll | Voll | Ja |
| F2.3 Nummern-Klassifikation | Voll | Voll | Ja |
| F2.4 Geführte Q&A | Voll | Voll | Ja |
| F3.1a Bildschirm-Live-Begleiter (kein Call-Audio) | Voll | Voll | Ja |
| F3.1b Audio-Live-Begleitung (Mithören/Ansage) | **Nicht als App** | **Nicht als App** | Nein (nur Hardware) |
| F4.1 Familien-Codewort | Voll | Voll | Ja |
| F4.2 Vertrauenspersonen | Voll | Voll | Ja |
| F4.3 Risikoprofil/Training | Voll | Voll | Ja |
| F4.4 Langzeit-Frühwarnung | Voll | Voll | Reduziert |

\* mit klar kommunizierter iOS/Android-Asymmetrie. Bewusst **nicht** versprochen (Datei 05): jedes In-Call-Audio durch die App (Mithören *und* Ansage ins Gespräch — auf beiden Plattformen blockiert), voller SMS-/E-Mail-Schutz auf iOS, Echtzeit-Anrufreaktion auf iOS, Stimmerkennung von Familienmitgliedern.

## Coverage-Map: welche Schicht greift bei welcher Masche

| Betrugsfamilie | Phase 1 (Kontakt) | Phase 2 (Gespräch) | Phase 3 (Beleg/Entscheidung) |
|---|---|---|---|
| A · Telefon-Schock (Enkeltrick/Schock/falsche Polizei) | F1.1/F1.2 | **F3.1a** (Bildschirm/Selbst-Ansage); F3.1b nur Hardware | F2.2/F2.3/F2.4, F4.1 |
| B · Telefon→digitaler Abfluss (Bank/Tech-Support) | F1.1/F1.2 | F3.1a | F2.2/F2.3/F2.4 |
| C · Text/Messenger (Hallo Mama/Phishing/Smishing/Quishing) | F1.3 (2. Welle) | — | **F2.1**/F2.4 |
| D · Langzeit-Vertrauen (Romance/Pig Butchering/Gewinnspiel) | — | — | **F2.1/F4.4**/F2.4 |

Lesart: Familie A wird auf allen drei Phasen abgedeckt — am stärksten durch den Begleitmodus (F3.1) in der sonst unbesetzten Phase 2. Familie C/D wird primär über die Second-Opinion-Engine (F2.1) abgefangen, weil hier ein Beleg (Screenshot) typischerweise existiert. Familie D bleibt die schwierigste — siehe offene Frage.

## MVP-Empfehlung und Sequenzierung

Der MVP sollte sich auf die Features konzentrieren, die (a) plattformneutral voll machbar sind, (b) früh in der Kill Chain oder in der unbesetzten Phase-2-Lücke greifen und (c) masche-übergreifend wirken:

**MVP-Kern (Welle 1):** F2.1–F2.4 (komplette Second-Opinion-Engine), F3.1a (Bildschirm-Live-Begleiter ohne Call-Audio), F4.1 (Codewort), F4.2 (Vertrauenspersonen), F1.1/F1.2 (Pre-Call-Warnung mit Asymmetrie-Kommunikation), F4.3 (schlankes Training).

**Welle 2 (nach Bank-Anker/erste Studiendaten):** F1.3 (SMS-Quarantäne, v.a. Android), volle F4.4-Mustererkennung für Langzeitmaschen, Voice-Klon-Erkennung als KI-Differenzierung, Banking-Integration (PSD2/PSD3).

Die **Android-first-Strategie** (Datei 05) wird durch die Matrix bestätigt: Die einzigen Features mit Plattform-Nachteil (F1.1, F1.3) sind auf Android stärker; die MVP-Kernfeatures (F2.x, F3.1) sind ohnehin plattformneutral, sodass eine iOS-Light-Variante parallel ohne Kernverlust möglich ist.

## Offene, feature-relevante Fragen

Erstens: **Familie D (Romance/Pig Butchering)** entzieht sich der Akut-Logik, weil sie über Wochen und plattformfern läuft. Die Entscheidung — geführter Selbst-Check im MVP vs. vollständige konversationelle Mustererkennung (datenhungriger, datenschutzsensibler) in Welle 2 — sollte beim Studiendesign und MVP-Scope explizit getroffen werden, weil sie Aufwand und DSGVO-Folgenabschätzung erheblich beeinflusst.

Zweitens: Die **Klassifikations-Architektur** (LLM lokal vs. Cloud, Konfidenz-Schwellen, Regel-Schicht) ist der größte technische Machbarkeits- und Datenresidenz-Hebel (DE-Hosting/BSI C5, Datei 05/08) und gehört in das nachgelagerte technische Arbeitspaket.

Drittens: Der **Begleitmodus (F3.1)** braucht das juristische Audit der finalen Architektur (Datei 05, § 201 StGB) als Voraussetzung, bevor er als Investoren-/Anwender-Versprechen kommuniziert wird.

→ Die juristischen und Studiendesign-Abhängigkeiten sind in [`07_roadmap_and_next_steps.md`](07_roadmap_and_next_steps.md) und [`08_risks_and_open_questions.md`](08_risks_and_open_questions.md) verortet.
