# 10 · Betrugslandschaft Deutschland — Taxonomie und Interventions-Angriffspunkte

## Warum diese Datei wichtig ist

Bevor ein Featureset entworfen werden kann, muss präzise verstanden sein, *wovor* SeniorShield eigentlich schützt. Diese Datei ist die mit Quellen belegte Wissensbasis dazu: eine Taxonomie der Betrugsmaschen gegen Senior:innen in Deutschland, ihre psychologischen und technischen Mechanismen, ihre Kanäle und Geldabfluss-Wege — und vor allem die **Interventions-Angriffspunkte**: die Stellen im Betrugsablauf, an denen eine technische Zweitmeinung/Warnung wirksam ansetzen kann.

Die Datei speist direkt das Produktkonzept ([`01_concept_and_product.md`](01_concept_and_product.md)) und ergänzt die Marktdaten ([`02_market_and_competition.md`](02_market_and_competition.md)). Quellen sind am Ende vollständig gelistet; im Text wird der Quelltyp (offizielle Statistik vs. Schätzung/Dunkelfeld) jeweils gekennzeichnet.

## Methodischer Vorbehalt zur Datenlage

Drei Dinge sind vorab wichtig, weil sie jede Zahl in dieser Datei relativieren:

Erstens erfasst die **Polizeiliche Kriminalstatistik (PKS)** die meisten dieser Maschen *nicht* als eigene Kategorie. Romance Scam, Cybertrading, Tech-Support-Scam und pushTAN-Betrug laufen unter Sammeltatbeständen (§ 263 StGB Betrug, § 263a StGB Computerbetrug). Nur „Enkeltrick/Schockanruf" und „falscher Polizeibeamter" werden im sonstigen Betrug separat zugeordnet. Maschen-spezifische bundesweite Jahresschäden existieren daher oft nur als LKA-Umfragen, Einzeloperationen oder Schätzungen.

Zweitens ist das **Dunkelfeld durchgängig hoch**. Scham ist bei Senior-Betrug das dominante Anzeige-Hemmnis — besonders bei Romance Scam und Gewinnversprechen. Offizielle Fallzahlen sind Untergrenzen.

Drittens dominieren zunehmend **Auslandstaten**: organisierte Callcenter in Türkei, Osteuropa, Westbalkan und Libanon. Das BKA verzeichnete 2024 neben 743.472 Inlands-Betrugsfällen zusätzlich 513.518 aus dem Ausland heraus begangene Fälle (BKA, veröffentlicht 25.04.2025). Aufklärung und Geldrückholung sind dadurch strukturell erschwert.

## Die übergreifende Struktur: organisierter Callcenterbetrug

Mehrere der wichtigsten Maschen (Enkeltrick, Schockanruf, falsche Polizei, falsche Bankmitarbeiter, Gewinnversprechen) fasst die Polizei unter **„organisierter Callcenterbetrug"** zusammen. Sie teilen Täterstruktur, Kanäle und Psychologie und unterscheiden sich vor allem in der Legende. Die arbeitsteilige Hierarchie (Quelle: Polizei Bayern) ist für das Produktdesign relevant, weil sie zeigt, wo die Masche *verwundbar* ist:

Der **Keiler** ruft aus dem Auslands-Callcenter an und führt das Einstiegsgespräch. Der **Abschließer** übernimmt zur Tatvollendung. Der **Logistiker** koordiniert die Abholung. Der **Abholer** („Runner") nimmt Bargeld/Wertsachen physisch entgegen — er ist die Schwachstelle der Bande, weil er zum Opfer kommen muss. Genau deshalb ist die Geldübergabe vor Ort der späteste, aber empirisch wirksamste Interventionspunkt (siehe Abschnitt Interventions-Angriffspunkte).

## Taxonomie der Maschen

Die folgende Taxonomie gruppiert nach **Erstkanal und Wirkprinzip**, weil das die produktrelevante Achse ist: Sie bestimmt, welche Schutzschicht greifen kann.

### Familie A — Akute Telefon-Schockmaschen (Stress + Autorität, sofortige Geldübergabe)

**A1 · Enkeltrick.** Anruf bei meist älteren, alleinstehenden Personen, Einstieg „Rate mal, wer dran ist?". Täter gibt sich als Enkel/Verwandter aus, täuscht akuten Geldengpass vor (Unfall, Wohnungs-/Autokauf), kann nicht selbst kommen, kündigt einen Boten an, vereinbart ein Kennwort. Bundesweit **6.656 Fälle 2024** (BKA, ca. −50 % ggü. 2023; verifiziert). Geldabfluss: Bargeldabholung durch den Abholer unter Nennung des Kennworts.

**A2 · Schockanruf.** Anrufer gibt sich als Verwandter *oder* als Polizist/Anwalt/Arzt aus und täuscht eine akute Notlage vor — typisch: naher Angehöriger hat einen tödlichen Verkehrsunfall verursacht, sofort ist eine „Kaution" nötig. Das Opfer wird **stundenlang in der Leitung gehalten** (Verbindung wird nie unterbrochen), um Isolation von Dritten zu erzwingen. Kein separater Bundeswert; Regional Oberbayern Nord 2024: 2.860 Anrufe falscher Polizisten/Verwandter, in 170 Fällen 4,4 Mio. € Beute. Geldabfluss: Bargeld, Schmuck, **Goldbarren/-münzen** an Abholer (dokumentierte Einzelfälle bis 500.000–1 Mio. €).

**A3 · Falsche Polizeibeamte / falsche Staatsanwälte.** Legende: angebliche Einbruchserie in der Nachbarschaft, das Vermögen sei zu Hause/im Schließfach „nicht mehr sicher" und werde zur „Sicherung" abgeholt; oder das Bargeld sei „Falschgeld". Zentrales technisches Merkmal: **Call-ID-Spoofing der 110** oder echter Dienststellennummern. Bundesweit **3.904 Fälle falsche Polizisten + ~1.600 weitere falsche Amtsträger 2024** (BKA, verifiziert). Baden-Württemberg 2024: Komplex falsche Polizei/Enkeltrick/Schockanruf zusammen 8.780 Fälle, 18,4 Mio. € Schaden.

Wichtig: Die echte Polizei ruft **nie** unter 110 an. Seit 1.12.2022 müssen TK-Anbieter Anrufe abbrechen, die 110/112 oder Auslandsanrufe mit deutscher Absendernummer anzeigen (TKG) — Täter weichen daher zunehmend auf unterdrückte Rufnummern aus (Quelle: Verbraucherzentrale).

### Familie B — Telefon-Manipulation mit digitalem Geldabfluss

**B1 · Falsche Bankmitarbeiter / pushTAN-Manipulation.** Anruf eines angeblichen Bankmitarbeiters: Hinweis auf eine „verdächtige Buchung", die man per pushTAN „stoppen" solle. Tatsächlich autorisiert jede Freigabe eine **Überweisung der Täter** vom Opferkonto; die Täter sind oft schon eingeloggt. Verstärkt durch **Call-ID-Spoofing** (Display zeigt die echte Bank-Nummer; dokumentierter Fall: Nummer bis auf die letzte Ziffer identisch mit der Haspa). Keine separate Bundesstatistik (geht in Computerbetrug auf). Geldabfluss: vom Opfer autorisierte Überweisung — in der Regel **nicht zurückbuchbar**. Sofortsperre über 116 116.

**B2 · Tech-Support-Scam (falscher Microsoft-Support).** Erstkontakt per Kaltanruf *oder* Pop-up/Sperrbildschirm mit gefälschter Viruswarnung und eingeblendeter Rückrufnummer, teils mit Alarmtönen. Opfer ruft an, Täter lassen **Fernwartungssoftware (AnyDesk/TeamViewer)** installieren — bewusst seriöse Tools, damit Antivirus nicht anschlägt — und greifen aufs Online-Banking zu. Microsoft-Befragung 2021 (keine Polizeistatistik): 47 % der Deutschen kontaktiert, 4 % der Opfer verloren Geld, Ø-Schaden 109 €. Hinweis: Microsofts Eigenbefragung verortet die Geldverlust-Opfer eher bei jüngeren, internetaffinen Nutzern — Polizei/Verbraucherzentrale sehen dagegen Ältere als Hauptzielgruppe. Geldabfluss: Fernzugriff aufs Banking, Betragsmanipulation, Guthaben-/Prepaidkarten.

### Familie C — Text-/Messenger-basierter Betrug

**C1 · Digitaler Enkeltrick / „Hallo Mama" (Messenger-Betrug).** SMS oder WhatsApp von unbekannter Nummer: „Hallo Mama, mein Handy ist kaputt, neue Nummer". Nach kurzem Vertrauensaufbau folgt eine „dringende Rechnung", die das Kind angeblich nicht selbst zahlen könne; Geld geht an Konten von „Finanzagenten". Holprige Sprache wird durchs „neue Handy" plausibilisiert. Geht in der PKS-Sammelkategorie „Enkeltrick/Schockanruf" auf. Regionale Indikatoren (Presse/Polizei, Schätzung): Brandenburg 3.110 WhatsApp-Betrugsanzeigen 2024 (Verdopplung ggü. 2023); typische Einzelsumme 1.000–3.000 €. Ein Ermittlungsverfahren dokumentierte 16.000 Anbahnungs-SMS in 10 Tagen.

**C2 · Phishing (E-Mail).** Gefälschte Bank-/Dienst-Mail mit Link zu einer Fake-Seite; Vorwand „Daten aktualisieren" oder „Konto wird gesperrt", oft mit Frist. Warnzeichen laut BSI: **TAN-Abfrage, ohne selbst eine Transaktion ausgelöst zu haben**. Altersübergreifend (Massenversand). BSI betont: das alte Erkennungsmerkmal „schlechtes Deutsch" greift durch KI-Texte nicht mehr.

**C3 · Smishing (Betrugs-SMS: Paket/Zoll/Bank).** SMS angeblich vom Paketdienst („Paket hängt fest", „Zollgebühr fällig") mit Link auf Fake-Seite oder zur App-Installation (Schadsoftware wie FluBot). Köder: Neugier/Paketerwartung + niedrige Beträge (0,99–3,99 €) senken die Hemmschwelle, Kreditkartendaten einzugeben. Echte Zollgebühren werden nie vorab über eine Webseite kassiert (Quelle: Zoll).

**C4 · Quishing (QR-Code-Betrug).** Manipulierter QR-Code führt auf Fake-Seite; tückisch, weil viele Smartphones die Ziel-URL nicht vorab zeigen. Verbreitung meist **offline**: gefälschte Bankbriefe per Post („photoTAN aktualisieren"), überklebte QR-Codes an Lade-/Parksäulen, Fake-Strafzettel, ÖPNV-Plakate. BSI meldet (01.04.2026) eine neue Welle mit KI-perfekt formulierten Texten, gezielt gegen Bankkunden.

### Familie D — Langzeit-Vertrauensmaschen (Beziehung als Waffe)

**D1 · Romance Scam / Love Scam.** Vier-Phasen-Modell (Polizei München): Kontaktaufnahme über Dating-/soziale Netzwerke → wochen- bis monatelanger Vertrauensaufbau bis zur emotionalen Abhängigkeit → eine Notlage kurz vor dem ersten Treffen → Geldforderung, danach immer weitere. Täter erfragen früh Familienstand und Vermögen und dosieren die Forderungen entsprechend. Opfer laut deutschen Polizeiprofilen „nahezu ausschließlich weiblich und alleinstehend"; Sachsen 2023: ~67 % Frauen, über 70 % im Alter 40–69. Bundesweit ≥ **50 Mio. € Schaden 2024** (Umfrage WEISSER RING bei allen 16 LKAs — Untergrenze, keine PKS-Zahl). Hohes Dunkelfeld.

**D2 · Krypto-/Investmentbetrug (Cybertrading, „Pig Butchering").** Köder über gefälschte Trading-Plattformen, beworben in sozialen Medien, oft mit **Deepfake-Promi-Werbung** (Günther Jauch, Frank Thelen u.a.). Niedrige Erst-Einzahlung mit sichtbaren *fingierten* Gewinnen → Druck auf immer größere Summen → bei Auszahlungswunsch Forderung nach „Steuern/Gebühren". Realer Handel findet meist nicht statt. „Pig Butchering" verschmilzt D1 und D2: emotionale Bindung als Türöffner, Fake-Trading-App als Geldabfluss. DE-Region Hamburg 2024: ~500 Fälle / ~15 Mio. € (sekundär); Verbraucherzentrale-Schätzung Gesamtschaden „mehrere Milliarden Euro". Vergleich FBI/USA 2024: Investment-Scam 5,8 Mrd. USD, Elder Fraud 60+ 4,9 Mrd. USD, Pig Butchering am häufigsten.

**D3 · Gewinnspiel-/Lotteriebetrug.** Anruf über angeblichen hohen Gewinn, Auszahlung nur gegen Vorkasse („Gebühren/Steuern/Notarkosten"). Täter geben sich als Anwälte/Notare aus, agieren aus Callcentern (Türkei u.a.), tarnen die Nummer als deutsche Ortsnummer. BKA: seit 2010 bis zu **300.000 Fälle / über 32 Mio. €** identifiziert. Zielgruppe vorwiegend ältere Bürger. Geldabfluss: Vorkasse per Überweisung, Bargeldversand, Geldtransferdienste, teils Gutscheinkarten/Krypto.

## Querschnitt 1: Die psychologische „Betriebssystem"-Ebene

Über alle Familien hinweg arbeiten die Maschen mit einem kleinen, wiederkehrenden Satz von Manipulationshebeln. Diese Hebel — nicht die einzelnen Legenden — sind das eigentliche Angriffsziel eines Schutzprodukts, weil eine App nicht jede neue Geschichte kennen kann, wohl aber das wiederkehrende Muster:

**Autorität.** Polizei, Staatsanwalt, Bank, Microsoft, Notar. Senior-Kohorten sind durch Sozialisation tendenziell autoritätsgläubiger — der zentrale Hebel bei A2, A3, B1, B2, D3.

**Künstlicher Zeitdruck.** „Sofort", „nur noch heute", „die Leitung darf nicht unterbrochen werden". Druck dient gezielt dazu, rationale Verhaltensregeln auszuhebeln. Die Polizei selbst formuliert: Opfer bemerken den Betrug „oft erst, wenn es zu spät ist".

**Angst / Schock.** Unfall, Haft, gesperrtes Konto, Virus. Der Schock-Einstieg schaltet überlegtes Handeln aus.

**Isolation.** Das stundenlange In-der-Leitung-Halten (A2/A3) und der Geheimhaltungsdruck („absolutes Stillschweigen") verhindern gezielt die naheliegendste Schutzhandlung — bei Dritten rückfragen.

**Vertrautheit / emotionale Bindung.** „Hallo Mama" (C1), Liebesbeziehung (D1), geklonte Stimme des Enkels. Hebelt Skepsis durch vorgetäuschte Nähe aus.

**Gier / Hoffnung.** Gewinn (D3), Rendite (D2). Reziprozität und Sunk-Cost halten Opfer in der Masche: nach der ersten Zahlung wird der Irrtum kaum noch hinterfragt.

Diese Liste ist die belastbarste Grundlage für die Klassifikations-Heuristik der Second-Opinion-Engine: Sie ist masche-übergreifend, sprachlich erkennbar und ändert sich kaum, während die konkreten Legenden ständig wechseln.

## Querschnitt 2: Kanäle und Geldabfluss

Die **Erstkanäle** verteilen sich auf Telefon (A1–A3, B1, B2, D3), Messenger/SMS (C1, C3), E-Mail (C2), QR/Post/Offline (C4) und soziale/Dating-Netzwerke (D1, D2). Für die Plattform-Strategie heißt das: Eine reine App-Lösung erreicht den Telefon-Erstkontakt nur eingeschränkt (vgl. Plattform-Restriktionen in [`05_platform_and_legal.md`](05_platform_and_legal.md)) — was die Architektur-Entscheidung für den *transparenten Begleitmodus* und die *Second-Opinion-Engine* (Nutzer bringt den Beleg aktiv ein) stützt.

Der **Geldabfluss** ist die kritischste Stelle, weil er meist irreversibel ist: Bargeldabholung durch den Runner (A1–A3), vom Opfer autorisierte Echtzeitüberweisung (B1, C1 — nicht zurückbuchbar), Fernzugriff aufs Banking (B2, D2), Krypto-Transfer (D2), Vorkasse/Geldtransferdienste/Gutscheinkarten (D3). Money-Mule- und Finanzagenten-Netzwerke verschleiern die Spur sofort. Konsequenz fürs Produkt: Wirksamer Schutz muss **vor** dem Geldabfluss greifen — jede Intervention danach ist Schadensbegrenzung, nicht Schutz.

## Querschnitt 3: Die KI-Eskalation

KI verändert die Bedrohungslage nicht durch eine neue Masche, sondern durch **Skalierung und Glaubwürdigkeit** der bestehenden. Drei belegte Entwicklungen sind für das Produkt entscheidend:

**Stimmenklon (Voice Cloning).** Aus ca. **drei Sekunden** öffentlich verfügbarem Audio lässt sich eine Stimme mit ~85 % Übereinstimmung klonen (McAfee 2023, verifiziert; n=7.000 in 9 Ländern inkl. Deutschland). Weltweit gab 1 von 4 Befragten an, selbst oder im Umfeld einen Stimmklon-Betrug erlebt zu haben; von den direkt Kontaktierten verloren 77 % Geld. Damit fällt der bisher wichtigste Laien-Verdachtsanker weg — „die Stimme klingt fremd" funktioniert nicht mehr.

**Deepfake-Werbung.** KI-Videos prominenter Personen machen Investment- und Gesundheitsbetrug glaubwürdig (D2). Ein dokumentierter Fall: über 120 Anleger, mehr als 1,3 Mio. € Schaden (WELT, 04.12.2025).

**KI-Phishing/-Vishing.** Das BSI warnt vor sprachlich fehlerfreien Phishing-Texten (das alte Erkennungsmerkmal „Rechtschreibfehler" entfällt) und vor Deepfake-Stimmen im CEO-Betrug.

Die wichtigste produktstrategische Folgerung: **Erkennungs-Tipps („achte auf technische Makel") veralten; robuste Verhaltensregeln (Rückruf unter bekannter Nummer, Familien-Codewort, niemals Geld an Unbekannte) bleiben gültig.** Genau diese Regeln sind aber im akuten Schock schwer abrufbar — die Lücke, die ein Produkt füllen muss.

## Interventions-Angriffspunkte: wo eine technische Zweitmeinung ansetzen kann

Der Betrugsablauf lässt sich als „Kill Chain" mit fünf Phasen lesen. Für jede ist relevant, wer heute interveniert und mit welcher Wirkung — und wo die Lücke ist, die SeniorShield adressieren kann.

**Phase 0 — Vor dem Kontakt (Prävention/Härtung).** Heute: Aufklärungskampagnen, Telefonbucheintrag kürzen. Wirkung begrenzt, weil Wissen im Schock ausgehebelt wird. *Produkt-Ansatz:* Risikoprofil, Mikro-Training mit lokalen Fällen, Familien-Codewort vorab vereinbaren.

**Phase 1 — Eingehender Kontakt (Anruf/Nachricht).** Heute: Carrier-Filter wie Telekom „Call Check" (über 300.000 Warnungen/Tag, verifiziert) prüfen gegen Datenbanken bekannter Nummern. **Grenze (laut Telekom selbst): nicht unfehlbar; erfasst v.a. bekannte Nummern, nicht den neuen, individuell zugeschnittenen Anruf.** *Produkt-Ansatz:* Pre-Call-Warnung (Schicht 1) als komplementäre, crowdgespeiste Schicht; bei Messenger/SMS/QR die Beleg-basierte Prüfung.

**Phase 2 — Manipulation (das laufende Gespräch).** Heute: **kein systematischer technischer Interventionspunkt.** Genau hier wirkt der Schock, hier ist das Opfer isoliert. Dies ist die zentrale Lücke. *Produkt-Ansatz:* der transparente Begleitmodus (Schicht 3) — die hörbare Ansage bricht Heimlichkeit und Isolation, die Live-Klassifikation gibt eine Zweitstimme im Moment des Drucks.

**Phase 3 — Entscheidung / Beleg vorhanden.** Heute: Familie, falls erreichbar (scheitert oft an Scham/Isolation). *Produkt-Ansatz:* Second-Opinion-Engine (Schicht 2) — Foto/Screenshot/Sprachnotiz/Nummer in unter 30 Sekunden zu farbkodierter Empfehlung; graduiertes Vertrauenspersonen-System als menschliche Eskalation.

**Phase 4 — Geldübergabe/-abfluss (letzter Verteidigungsring).** Heute der **empirisch wirksamste, aber späteste** Punkt: aufmerksames **Bankschalter-Personal** stoppt dokumentiert zahlreiche Abhebungen (belegte Fälle: Frechen, Wallenhorst, Emsdetten, Aachen, Konstanz). Schwäche: greift erst beim Abheben, hängt am einzelnen Mitarbeiter und am Bargeld-Weg — bei digitaler Echtzeitüberweisung (B1) fehlt dieser Ring ganz.

Der entscheidende Befund für das Featureset: **Zwischen dem Carrier-Filter (Phase 1, nur bekannte Nummern) und dem Bankschalter (Phase 4, nur Bargeld, nur spät) klafft genau in Phase 2/3 — dem Moment des Schocks und der Entscheidung — eine systematische Interventionslücke.** Das ist der plausibelste Ansatzpunkt für SeniorShield und deckt sich exakt mit der „Akut-Hilfe-Lücke" der Marktthese.

## Folgerungen für das Featureset (Mapping auf die drei Schutzschichten)

Die Recherche stützt die bestehende Architektur und schärft die Prioritäten:

Die **Second-Opinion-Engine (Schicht 2)** ist der MVP-Kern, weil sie Phase 3 über *alle* Familien hinweg adressiert — entscheidend ist, dass die Klassifikation auf den masche-übergreifenden psychologischen Hebeln (Autorität, Zeitdruck, Angst, Isolation, Vertrautheit, Gier) aufsetzt, nicht auf einzelnen Legenden, die ständig wechseln. Die vier Eingabemodi decken die Kanäle ab: Foto/Screenshot (C1–C4, D), Sprachnotiz (A, B), Nummer (A3, B1, D3), geführte Q&A (alles ohne Beleg).

Der **transparente Begleitmodus (Schicht 3)** adressiert die zentrale, heute unbesetzte Phase-2-Lücke bei den Telefon-Schockmaschen (Familie A/B) — und seine Abschreckungs-Ansage ist gerade gegen die Heimlichkeits- und Isolations-Hebel zielgenau.

Die **Pre-Call-Warnung (Schicht 1)** ist komplementär zu Carrier-Diensten und am stärksten bei den nummernbasierten Maschen (A3, D3).

Querschnittsfunktionen mit hohem belegtem Hebel: das **Familien-Codewort** (von Polizei und FTC als „derzeit wirksamster Schutz gegen Voice Cloning" benannt) gehört prominent ins Vertrauenspersonen-System; die **konservative Konfidenz mit menschlicher Eskalation** ist gegen das False-Negative-Risiko bei hohen Einzelschäden (D2) unverzichtbar.

Offene, feature-relevante Frage für die nächste Iteration: Romance/Investment-Maschen (Familie D) laufen über Wochen und über Kanäle, die eine App schwer „mithört" — hier ist eher ein heuristisch-konversationelles Frühwarnmuster (Kanalwechsel weg von der Plattform, früh nach Handynummer gefragt, „letzte Hoffnung", Auszahlung nur gegen Gebühren) gefragt als eine Akut-Intervention. Das sollte beim Studiendesign und beim MVP-Scope explizit entschieden werden.

## Quellen

Hinweis: Quelltyp ist gekennzeichnet — *offiziell* (Behörde/PKS), *Umfrage/Studie* (methodisch von der PKS zu trennen), *Schätzung/Presse* (Einordnung, mit Vorsicht). Zwei Headline-Zahlen wurden zusätzlich verifiziert: BKA-Fallzahlen 2024 und McAfee-Stimmklon-Studie.

### Offizielle Statistiken und Behörden

- BKA — Betrugskriminalität 2024: Rückgang bei Fallzahlen (Enkeltrick 6.656; falsche Polizisten 3.904; ~1.600 weitere falsche Amtsträger) — https://www.bka.de/SharedDocs/Kurzmeldungen/DE/Kurzmeldungen/250425_Entwicklung_Betrugskriminalit%C3%A4t.html — 2025 *(offiziell, verifiziert)*
- BKA — Bundeslagebild Cybercrime 2024 (131.391 Inlandsfälle; 201.877/513.518 Auslandstaten; Computerbetrug 82 %) — https://www.bka.de/DE/AktuelleInformationen/StatistikenLagebilder/Lagebilder/Cybercrime/2024/CC_2024.html — 2025 *(offiziell)*
- BKA — Polizeiliche Kriminalstatistik 2024 — https://www.bka.de/DE/AktuelleInformationen/StatistikenLagebilder/PolizeilicheKriminalstatistik/PKS2024/pks2024_node.html — 2025 *(offiziell)*
- BKA — Betrügerische Gewinnversprechen / Call-Center-Betrug (seit 2010 bis zu 300.000 Fälle / >32 Mio. €) — https://www.bka.de/DE/UnsereAufgaben/Deliktsbereiche/BetruegerischeGewinnversprechen/callCenterBetrug.html *(offiziell)*
- BKA — Bundeslagebild Wirtschaftskriminalität 2024 — https://www.bka.de/DE/Presse/Listenseite_Pressemitteilungen/2025/Presse2025/250731_PM_BLB_Wikri24.html — 2025 *(offiziell)*
- BKA — Operation Final Exchange (47 Geldwäsche-Exchanges stillgelegt) — https://www.bka.de/DE/Presse/Listenseite_Pressemitteilungen/2024/Presse2024/240919_PM_finalexchange.html — 2024 *(offiziell)*
- Innenministerium Baden-Württemberg — Schlag gegen international organisierten Telefonbetrug (12 Callcenter, 20 Festnahmen, ~10 Mio. € verhindert) — https://im.baden-wuerttemberg.de/de/service/presse-und-oeffentlichkeitsarbeit/pressemitteilung/pid/schlag-gegen-international-organisierten-telefonbetrug — 2024 *(offiziell)*
- BaFin — Vorsicht vor betrügerischen Handelsplattformen — https://www.bafin.de/DE/verbraucherinnen-verbraucher/themen-finanzprodukte/finanzbetrug-erkennen/anlagebetrug/betruegerische-handelsplattformen/betruegerische-handelsplattformen_node.html *(offiziell)*
- Zoll — Phishing-Mails und gefälschte Bescheide — https://www.zoll.de/DE/Privatpersonen/Postsendungen-Internetbestellungen/Phishing-Mails-und-gefaelschte-Bescheide/phishing-mails-und-gefaelschte-bescheide_node.html *(offiziell)*

### Polizeiliche Kriminalprävention und LKAs

- Polizei Bayern (PP München) — Organisierter Callcenterbetrug: Phasenmodell, Täterrollen, Opfermerkmale — https://www.polizei.bayern.de/schuetzen-und-vorbeugen/beratung/039355/index.html — 2025 *(offiziell, beste Primärquelle zu Ablauf/Psychologie)*
- Polizei München / Bayern — Romance Scam / Love Scam (4-Phasen-Modell) — https://www.polizei.bayern.de/schuetzen-und-vorbeugen/beratung/018837/index.html *(offiziell)*
- Polizei Bayern — WhatsApp-„Hallo Mama"-Ermittlungserfolg Nürnberg (16.000 Anbahnungs-SMS) — https://www.polizei.bayern.de/aktuelles/pressemitteilungen/066045/index.html — 2024 *(offiziell)*
- polizei-beratung.de — Schockanrufe: Panikmache am Telefon (Originalwortlaut Verhaltensregeln) — https://www.polizei-beratung.de/aktuelles/detailansicht/schockanrufe-panikmache-am-telefon-legen-sie-sofort-auf/ *(offiziell)*
- polizei-beratung.de — Enkeltrick (Tipps Ihrer Polizei) — https://www.polizei-beratung.de/themen-und-tipps/betrug/enkeltrick/ *(offiziell)*
- polizei-beratung.de — Romance-Scamming — https://www.polizei-beratung.de/themen-und-tipps/sicher-handeln/onlinebetrug-maschen/romance-scamming-liebesbetrug/ *(offiziell)*
- polizei-beratung.de — Trading-Scam — https://www.polizei-beratung.de/aktuelles/detailansicht/trading-scam/ *(offiziell)*
- polizei-beratung.de — Tech-Support-Scams: Falsche Microsoft-Mitarbeiter — https://www.polizei-beratung.de/aktuelles/detailansicht/tech-support-scams-falsche-microsoft-mitarbeiter-am-telefon/ *(offiziell)*
- LKA Niedersachsen (polizei-praevention.de) — Microsoft-Support-Betrugsmasche — https://www.polizei-praevention.de/aktuelles/microsoft-support-betrugsmasche.html — 2024 *(offiziell)*
- LKA Niedersachsen — Gefälschter QR-Code auf Parkscheinautomat (Quishing) — https://www.polizei-praevention.de/aktuelles/gefaelschter-qr-code-auf-parkscheinautomat-fuehrt-zu-phishingseite-im-aussehen-von-easypark.html — 2024 *(offiziell)*
- LKA NRW — Quishing: gefälschte Bank-Briefe — https://lka.polizei.nrw/presse/quishing-gefaelschte-briefe-von-vermeintlichen-kreditinstituten-im-umlauf — 2024/2025 *(offiziell)*
- Polizei NRW — Schockanruf bei Senior, aufmerksamer Bankmitarbeiter erkennt Betrug — https://polizei.nrw/presse/241205-2-schockanruf-bei-senior-aufmerksamer-bankmitarbeiter-erkennt-betrug — 2024 *(offiziell, Interventionsbeleg)*
- Polizei NRW — Emsdetten: Bankpersonal verhindert Auszahlung — https://polizei.nrw/presse/emsdetten-schockanruf-bei-seniorin-bankpersonal-verhindert-auszahlung *(offiziell, Interventionsbeleg)*
- Gemeinde Wallenhorst — Bankmitarbeiter verhindert Betrug nach Schockanruf (50.000 €) — https://www.wallenhorst.de/rathaus-politik/aktuelles/meldung/bankmitarbeiter-verhindert-betrug-nach-schockanruf.html *(offiziell/kommunal, Interventionsbeleg)*

### BSI, Verbraucherzentrale, Bankenverband

- BSI — Wie erkenne ich Phishing in E-Mails und auf Webseiten? — https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Cyber-Sicherheitslage/Methoden-der-Cyber-Kriminalitaet/Spam-Phishing-Co/Passwortdiebstahl-durch-Phishing/Wie-erkenne-ich-Phishing-in-E-Mails-und-auf-Webseiten/wie-erkenne-ich-phishing-in-e-mails-und-auf-webseiten.html *(offiziell)*
- BSI — Smishing/SMS-Phishing (FluBot/TeaBot) — https://www.bsi.bund.de/DE/Service-Navi/Presse/Alle-Meldungen-News/Meldungen/Smishing_SMS-Phishing_141021.html — 2021 *(offiziell)*
- BSI — KI-gestützte QR-Code-Betrügereien (Quishing-Welle) — https://www.bsi.bund.de/DE/Service-Navi/Abonnements/Newsletter/Buerger-CERT-Abos/Newsletter-Einfach-Cybersicher/Einfach_Cybersicher_260401/_documents/Basics_3_Quishing.html — 01.04.2026 *(offiziell)*
- BSI — Cybersicherheitsvorfall AnyDesk — https://www.bsi.bund.de/SharedDocs/Cybersicherheitswarnungen/DE/2024/2024-213655-1032.html — 2024 *(offiziell)*
- BSI — Digitaler Verbraucherschutz Jahresrückblick 2024 (Phishing/Deepfake-Vishing) — https://www.bsi.bund.de/DE/Service-Navi/Presse/Pressemitteilungen/Presse2025/250314_DVS-Jahresrueckblick_2024.html — 2025 *(offiziell)*
- Verbraucherzentrale — „Hallo Mama, Hallo Papa": Betrug über WhatsApp und SMS — https://www.verbraucherzentrale.de/wissen/digitale-welt/mobilfunk-und-festnetz/hallo-mama-hallo-papa-betrugsversuche-ueber-whatsapp-und-sms-72910 — 2024 *(offiziell)*
- Verbraucherzentrale — Paketdienst-SMS: Vorsicht, Abzocke! (Smishing) — https://www.verbraucherzentrale.de/wissen/digitale-welt/mobilfunk-und-festnetz/paketdienstsms-vorsicht-abzocke-58988 — 2025 *(offiziell)*
- Verbraucherzentrale — Quishing: Falsche QR-Codes — https://www.verbraucherzentrale.de/wissen/digitale-welt/phishingradar/quishing-falsche-qrcodes-in-mails-briefen-oepnv-und-strassenverkehr-98612 — 2025 *(offiziell)*
- Verbraucherzentrale — Vorsicht: Falsche Polizisten am Telefon (Spoofing, TKG-Pflicht) — https://www.verbraucherzentrale.de/wissen/vertraege-reklamation/abzocke/vorsicht-falsche-polizisten-am-telefon-12273 — 2025 *(offiziell)*
- Verbraucherzentrale — Vorsicht: Betrügerisches Online-Trading — https://www.verbraucherzentrale.de/wissen/geld-versicherungen/vorsicht-betruegerisches-onlinetrading-54699 *(offiziell, Schätzung „mehrere Mrd. €")*
- Verbraucherzentrale — Deepfakes mit Promis für Fake-Werbung — https://www.verbraucherzentrale.de/wissen/digitale-welt/phishingradar/taeuschend-echt-wie-kriminelle-deepfakes-mit-promis-fuer-fakewerbung-nutzen-108311 — 2026 *(offiziell)*
- Verbraucherzentrale Hamburg — Warnung vor falschen Bank-Anrufen (pushTAN) — https://www.vzhh.de/themen/finanzen/konto-karte/warnung-vor-falschen-bank-anrufen — 2025 *(offiziell)*
- Bankenverband — Fake-Anrufe: Falsche Bankangestellte — https://bankenverband.de/verbraucher/fake-anrufe-falsche-bankangestellte-am-telefon *(Verband)*

### Umfragen/Studien und KI-Bedrohung

- McAfee — Beware the Artificial Impostor (3 Sekunden Audio, 1 von 4 betroffen, 77 % Geldverlust) — https://www.mcafee.com/blogs/privacy-identity-protection/artificial-imposters-cybercriminals-turn-to-ai-voice-cloning-for-a-new-breed-of-scam/ — 2023 *(Studie, n=7.000 inkl. DE; verifiziert)*
- Microsoft — Studie zu Tech-Support-Scams in Deutschland (47 % kontaktiert, Ø 109 €) — news.microsoft.com — 2021 *(Eigenbefragung, keine Polizeistatistik)*
- Bitkom — Bilanz Cyberkriminalität 2023 (13 % Online-Banking-Betrug, Ø 262 €) — https://www.bitkom.org/Presse/Presseinformation/Bilanz-Cyberkriminalitaet-7-von-10-betroffen — 2024 *(Branchenumfrage)*
- WEISSER RING Magazin — Love-Scam ≥ 50 Mio. € (Umfrage bei allen 16 LKAs) — https://wr-magazin.de/wrtags/love-scamming/ — 2024/2025 *(Umfrage, Untergrenze)*
- FTC — Scammers use AI to enhance family emergency schemes — https://consumer.ftc.gov/consumer-alerts/2023/03/scammers-use-ai-enhance-their-family-emergency-schemes — 2023 *(Behörde USA, Vergleich)*
- FBI IC3 — 2024 Internet Crime Report (Elder Fraud 60+ 4,9 Mrd. USD; Pig Butchering) — https://www.ic3.gov/AnnualReport/Reports/2024_IC3Report.pdf — 2025 *(offiziell USA, Vergleich)*

### Carrier-Intervention und Presse (Einordnung/Schätzung)

- Deutsche Telekom — Call Check / Branded Calls (>300.000 Warnungen/Tag) — https://www.telekom.com/de/medien/medieninformationen/detail/branded-calls-1100682 — 2025/2026 *(Unternehmensangabe)*
- Neue Osnabrücker Zeitung (Presseportal) — >117 Mio. € Schaden / ~99.000 Versuche 2023 (LKA-Auswertung) — https://www.presseportal.de/pm/58964/5875459 — 2024 *(Presse-Aggregation, methodisch heterogen)*
- WELT — Deepfake-Investment: >120 Anleger, >1,3 Mio. € — 04.12.2025 *(Presse, Einzelfall)*
- ZDF — Betrugsmasche mit Deepfake-Promis — https://www.zdf.de/nachrichten/panorama/kriminalitaet/betrug-promi-deepfake-werbevideos-geldanlage-100.html *(Presse)*

### Nicht ausreichend belegte Angaben (bewusst nicht als Fakt übernommen)

- „KI-Betrug verursacht in DE >10 Mrd. €/Jahr" — nur in Presse-Sekundärquelle (ad-hoc-news), keine Behörden-Primärquelle. Vor Nutzung im Pitch über den BSI-Lagebericht absichern.
- „Verdopplung der Deepfake-Vishing-Vorfälle 2024→2025" — als BSI-Bezug in Presse zitiert, Primärquelle nicht eingesehen.
- Abholer-Pauschale „~500–1.000 €" — aus präventiver Sekundärquelle, nicht aus einer Primärseite; als Schätzwert behandeln.
