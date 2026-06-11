# 01 · Produktkonzept und Architektur

## Vision

SeniorShield ist eine technische Schutzschicht für Senior:innen im Akutmoment eines Betrugsversuchs — eine niedrigschwellige, vertrauenswürdige Zweitmeinung, die das fehlende Bindeglied zwischen prophylaktischer Aufklärung (zu früh) und bankseitiger Anomalieerkennung (zu spät) schließt. Das Produkt arbeitet plattformneutral, hält die rechtlichen Grenzen von § 201 StGB und DSGVO strikt ein und wurde nach den Prinzipien evidenzbasierter Senior-UX entworfen.

## Problem-These (kondensiert)

Senior-Betrug ist primär kein Wissens-Problem, sondern ein Aktivierungs-Problem unter Stress. Aufklärungskampagnen erzeugen Wissen, das im Akutmoment durch emotionalen Druck, künstliche Zeitnot und Isolation der Betroffenen außer Kraft gesetzt wird. Familiäre Lösungen scheitern an Scham und am strukturellen Risiko von Caregiver-Fraud (etwa 30–40 % der erkannten Senior-Fraud-Fälle involvieren Personen aus dem engeren Umfeld).

→ Detaillierte Marktbegründung in [`02_market_and_competition.md`](02_market_and_competition.md).

## Architektur — drei Schutzschichten

Die finale Produktarchitektur wurde nach intensiver Prüfung der iOS/Android-Plattformrestriktionen und der deutschen Strafrechts- und Datenschutzlage geschärft. Sie ist *bewusst* anders als die ursprüngliche Idee einer heimlichen Live-Coaching-Funktion — die juristisch und technisch nicht tragfähig wäre. Die jetzige Architektur ist plattformneutral, rechtskonform und in der Schutzwirkung mindestens gleichwertig, weil sie an drei statt nur einem Punkt ansetzt.

### Schicht 1 — Pre-Call-Warnung

Eine kontinuierlich aktualisierte Datenbank bekannter Betrugsnummern wird über die Call-Directory-Mechanismen beider Mobil-Plattformen auf das Gerät gespielt. Verdächtige Anrufe werden bereits vor dem Annehmen markiert. Datenquellen: Crowdsourcing aus der eigenen Nutzerbasis, BNetzA, Verbraucherzentralen, Polizei-Datenbanken. Auf Android tendenziell mit höherer Reaktivität als auf iOS, weil dort die Echtzeit-API-Zugriffe enger sind — siehe [`05_platform_and_legal.md`](05_platform_and_legal.md).

### Schicht 2 — Second-Opinion-Engine (MVP-Kern)

Vier Eingabemodi:

1. **Foto/Screenshot** einer verdächtigen Nachricht (SMS, WhatsApp, E-Mail, Brief)
2. **Sprachaufnahme** nach einem Anruf (selbst initiiert vom Senior, nicht heimlich)
3. **Anrufer-Nummer** zur Weiterleitung / Klassifikation
4. **Geführte Frage-Antwort-Sequenz** für Situationen ohne Beleg

Output in unter 30 Sekunden: farbkodierte Einschätzung mit konkreter Handlungsempfehlung. Hybride Architektur aus LLM-gestützter Klassifikation (für Sprach- und Bildverstehen) und konservativ-regelbasierter Validierung (für falsche-negative Risiken — false negatives bei Senior-Betrug können sechsstelligen Schaden verursachen).

### Schicht 3 — Live-Begleitmodus

> **Korrektur Juni 2026:** Die ursprüngliche Variante (App hört den Lautsprecher übers Mikrofon mit und spielt eine Ansage ins Gespräch) ist technisch nicht tragfähig — iOS und Android blockieren In-Call-Audio für Dritt-Apps in beide Richtungen (Details und Quellen in [`05_platform_and_legal.md`](05_platform_and_legal.md)). Schicht 3 ist daher neu gefasst.

Im laufenden Verdachtsfall: Ein-Knopf-Aktivierung durch den Senior. Die App **greift nicht auf das Telefonat zu**, sondern begleitet parallel auf dem Bildschirm: ruhige, großformatige Coaching-Schritte (Abfrage der Manipulationshebel, Verhaltensregeln wie „echte Polizei verlangt nie Geld"). Der eigentliche Schutzmechanismus — das Brechen der Heimlichkeit — entsteht **verhaltensbasiert**: Die App leitet den Senior an, selbst laut zu sagen, dass der Anruf gerade von einer Sicherheits-App geprüft wird. Betrüger arbeiten mit Heimlichkeit und brechen ab, sobald Transparenz entsteht — dieser Effekt bleibt erhalten, ohne in den Audio-Stream einzugreifen, und ist rechtlich unkritisch (kein fremdes Wort wird verarbeitet). Nach dem Auflegen: Sprachnotiz-Analyse (Schicht 2).

Echtes Live-Mithören und eine Ansage *in* das Gespräch sind nur über ein vom Telefon unabhängiges **Hardware-Begleitgerät** realisierbar (Vision-Layer 2) — siehe [`05_platform_and_legal.md`](05_platform_and_legal.md).

## Querschnittsfunktionen

Die drei Schichten werden ergänzt durch:

- **Graduiertes Vertrauenspersonen-System.** Eine bis drei selbst gewählte Vertrauenspersonen, auch außerhalb der Familie. Konfigurierbare Rolle und Eingriffstiefe. Wichtig: strukturelle Resilienz gegenüber Caregiver-Fraud — der Senior kann bewusst Vertrauenspersonen außerhalb der unmittelbaren Pflegekonstellation wählen.
- **Adaptiver Risikoprofil-Assistent.** Würdevolle Mikro-Interaktionen erfassen Risikofelder (Online-Banking-Nutzung, soziale Isolation, kognitive Selbsteinschätzung, frühere Betrugserfahrungen). Schutzprofil wird personalisiert.
- **Mikro-Training mit lokalen Fällen.** Kurze, narrative Fall-Geschichten aus der eigenen Region (anonymisiert). Aktivierungs-Treiber: die App bleibt im Alltag relevant und ist im Krisenfall vertraut.
- **Senior-UX nach evidenzbasierten Prinzipien.** Kognitive Lastverteilung, B1-Sprache, vorhersehbare Navigation, respektvoller Ton — kein Infantilisieren. Validiert in randomisierten Studien.

## MVP-Scope (was rein, was raus)

**Im MVP:** Schicht 1 (Pre-Call-Warnung), Schicht 2 (Second-Opinion-Engine in allen vier Eingabemodi), Schicht 3 (transparenter Begleitmodus), graduiertes Vertrauenspersonen-System, Risikoprofil-Assistent, Mikro-Training.

→ Die detaillierte Ableitung der einzelnen Features aus der Betrugs-Taxonomie samt Erkennungsheuristik, Plattform-Machbarkeitsmatrix und MVP-Priorisierung steht in [`11_featureset_and_feasibility.md`](11_featureset_and_feasibility.md).

**Bewusst nicht im MVP:**

- Banking-Integration über PSD2/PSD3 (kommt in zweiter Welle, wenn Bank-Anker etabliert sind)
- Voice-Klon-Erkennung mit KI (zweite Welle, technologisches Differenzierungsmerkmal)
- 24/7-Hotline mit echten Berater:innen (Premium-Tier ab Seed-Runde)
- Caregiver-Dashboard für pflegende Angehörige (DiPA-Modul, kommt mit BfArM-Listung)
- Schwarmweisheit-Funktion (Community-Modul, dritte Welle)
- Hardware-Begleitgerät (Vision-Layer für 80+-Zielgruppe)

## Was bewusst herausgenommen wurde — und warum

Die ursprünglich angedachte heimliche Live-Coaching-Funktion (App hört im Hintergrund mit, transkribiert still, gibt unsichtbare Hinweise) wurde nach gründlicher rechtlicher und technischer Prüfung verworfen. Details in [`05_platform_and_legal.md`](05_platform_and_legal.md). Wichtig (Korrektur Juni 2026): Auch die zunächst als Ersatz gedachte transparente *App-Ansage ins Gespräch* ist technisch nicht tragfähig, weil iOS/Android In-Call-Audio für Dritt-Apps sperren. Die Schutzwirkung — das Brechen der Heimlichkeit — bleibt erhalten, wird aber verhaltensbasiert erzeugt (der Senior spricht den Prüf-Hinweis selbst aus) statt durch die App; echte Live-Audio-Wirkung ist dem Hardware-Layer vorbehalten.

## Designprinzipien (für Co-Founder-Onboarding und Vendor-Briefing)

1. *Würde geht vor Effizienz.* Kein UX-Element darf den Nutzer als unbeholfen markieren.
2. *Autonomie geht vor Surveillance.* Vertrauenspersonen sehen nur, was der Senior explizit freigibt.
3. *Konservative Konfidenz.* Bei Unsicherheit immer Eskalation zu menschlicher Hilfe, nie ein falsches "alles in Ordnung".
4. *Transparenz vor Heimlichkeit.* Auch dort, wo Heimlichkeit technisch möglich wäre, gewinnt Transparenz — weil sie Vertrauen schafft *und* Betrüger abschreckt.
5. *Evidenz vor Marketing.* Jede Claim, die wir machen, muss in einer öffentlich publizierten Studie verteidigbar sein.
