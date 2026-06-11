# 05 · Plattform- und Rechtsanalyse

## Warum diese Datei wichtig ist

Die Architektur-Entscheidung in [`01_concept_and_product.md`](01_concept_and_product.md) ist nicht beliebig gewählt, sondern Ergebnis einer intensiven Prüfung der Plattform-Restriktionen auf iOS und Android sowie der deutschen Strafrechts- und Datenschutzlage. Wer diese Datei nicht gelesen hat, wird die Produkt-Wahl nicht vollständig verstehen — und ist anfällig dafür, im Investoren- oder Anwender-Gespräch ein Versprechen abzugeben, das wir technisch oder juristisch nicht halten können.

## Plattform-Restriktionen — iOS

**Audio-Zugriff während Telefonaten:** Die App-Sandbox-Architektur blockiert Drittanbieter-Apps vom Audio-Stream während eines Telefongesprächs. Es gibt keinen offiziellen API-Weg, um In-Call-Audio zu erfassen.

**Native Anrufaufzeichnung:** Apple hat in iOS 18.1 native Call Recording mit Transkription eingeführt, **aber die EU ist regional explizit ausgenommen.** In Deutschland ist die Aufnahmefunktion auch nach Apple-Intelligence-Rollout im April 2025 nicht verfügbar.

**Call-Logs:** Komplett gesperrt für Drittanbieter — Anruf-Historie kann nicht gelesen oder exportiert werden.

**Caller-ID / Blocking:** Über die Call Directory App Extension (CXCallDirectoryExtensionContext) seit iOS 10 möglich. Die Extension liefert eine Liste bekannter Nummern an die System-Telefon-App, die dann beschriftet oder blockiert. Statische Mechanik — keine Echtzeit-Klassifikation eingehender Anrufe, kein Crowdsourcing-Live-Abgleich.

**SMS-Zugriff:** Nur über ILMessageFilterExtension. **Massive Einschränkungen:** App sieht nur SMS von unbekannten Absendern (nicht von gespeicherten Kontakten). Keine Speicherung oder Export. Nur Klassifikation + Routing. SMS-Historie unzugänglich.

**E-Mail-Zugriff:** Keine systemweite Filterung möglich. Nur als eigene Mail-App mit eigenen IMAP/OAuth-Verbindungen.

## Plattform-Restriktionen — Android

**Audio-Zugriff während Telefonaten:** Seit **Android 10** (2019) Mikrofon-Zugriff für In-Call-Audio blockiert. Workaround über Accessibility API funktionierte bis Mai 2022, wurde dann per Google Play Store Policy explizit untersagt. **Nur vorinstallierte Default-Telefon-Apps** (Google Phone, Samsung Phone) haben Zugriff auf den Audio-Stream.

**Native Call Recording:** Auf Pixel-Geräten seit November 2025 verfügbar — als System-Funktion mit Hinweis-Audio-Ansage, nicht als API für Drittanbieter.

**SMS-Zugriff:** Voller Lesezugriff möglich über READ_SMS-Berechtigung — aber erfordert erhebliches Datenschutz-Onboarding und ist von Google Play Policies seit 2019 stark beschränkt (nur für Default-SMS-Apps mit klarem Use Case).

**Caller-ID / Blocking:** Über CallScreeningService und RoleManager API. Mehr Flexibilität als auf iOS, aber Google hat ebenfalls verschärft.

## Strukturelle Konsequenz für das Produkt

Eine App, die im Hintergrund mithört, kann auf beiden Plattformen mit den offiziellen Vertriebskanälen (App Store, Play Store) **nicht existieren**. Workarounds (Root, Sideloading, GrapheneOS) sind für unsere Senior-Zielgruppe ausgeschlossen.

Die ursprünglich angedachte "heimliche Live-Coaching-Funktion" (App hört unsichtbar mit) ist damit **strukturell nicht umsetzbar** — weder auf iOS in Deutschland (Audio gesperrt, EU-Ausschluss) noch auf Android (API-Zugang seit 2019 gesperrt).

## Rechtsanalyse — § 201 StGB

§ 201 Abs. 1 StGB stellt das **unbefugte Aufnehmen des nichtöffentlich gesprochenen Wortes auf einen Tonträger** unter Strafe. Strafrahmen: Freiheitsstrafe bis zu drei Jahren oder Geldstrafe. Selbst die Teilnahme an einem Gespräch berechtigt nicht zur Aufnahme ohne Zustimmung aller anderen Beteiligten.

### Differenzierung 1 — Live-Transkription ohne Audio-Persistenz

Mehrere übereinstimmende juristische Kommentare (Datenschutz-Notizen, BRANDI Rechtsanwälte, intelli-revolution.de, unternehmensstrafrecht.de):

> *"Eine Live-Transkription, bei der keine Tonspur abgelegt, sondern der gesprochene Inhalt lediglich kurzzeitig verarbeitet wird, fällt nicht unter den Straftatbestand."*

Bedingung: keine Zwischenspeicherung auf Tonträger oder Server. Reines flüchtiges Verarbeiten im Arbeitsspeicher. Sobald irgendwo eine Audiodatei persistiert wird (auch nur auf Server-Cache), ist § 201 erfüllt.

**Aber:** § 201 Abs. 2 Nr. 1 stellt zusätzlich das **Abhören mit einem Abhörgerät** unter Strafe — und die DSGVO greift parallel und unabhängig vom Strafrecht. Auch ohne Tatbestandserfüllung des Aufnehmens kann die Verarbeitung von Sprache eine datenschutzrechtliche Hürde darstellen.

### Differenzierung 2 — Notwehr / notwehrähnliche Lage

BVerfG-Entscheidung 2002 (1 BvR 1611/96, 1 BvR 805/98) erkennt Ausnahmen an: "Anfertigung heimlicher Tonbandaufnahmen zur Feststellung der Identität eines anonymen Anrufers, der Verleumdungen ausspricht" und "Maßnahmen zur Feststellung erpresserischer Drohungen" — also genau die Schockanruf-/Enkeltrick-Konstellation.

BGH-Folge-Rechtsprechung (XII ZB 107/08, BAG 2 AZR 537/06): wer diskriminiert, beleidigt, bedroht oder genötigt wird, kann sich auf notwehrähnliche Lage berufen. Aufnahme dann im Regelfall verwertbar.

**Aber:** Diese Rechtfertigung greift retrospektiv und situationsabhängig. Sie taugt nicht als allgemeine Vorab-Rechtfertigung für eine immer-eingeschaltete App. Wir können sie als zusätzliche Stütze anführen, aber nicht als primäre Argumentationslinie.

### Differenzierung 3 — Einwilligung mit Hinweis (Callcenter-Logik)

Wenn der Anrufer ausdrücklich darauf hingewiesen wird, dass das Gespräch verarbeitet wird, und das Gespräch trotzdem fortsetzt, liegt **konkludente Einwilligung** vor. Das ist die Standardpraxis bei Callcenter-Mitschnitten ("Dieses Gespräch wird zu Qualitätszwecken aufgezeichnet"). **Diese Mechanik können wir uns zunutze machen — und sie ist die Grundlage der jetzigen Architektur.**

## KRITISCHE KORREKTUR (Juni 2026): die akustische In-Call-Annahme hält nicht

Die ursprüngliche Architektur-Wahl unten beruhte auf der Annahme, eine Dritt-App könne während eines laufenden Anrufs (auf Lautsprecher) über das *normale* Mikrofon den Lautsprecher akustisch mithören und zugleich eine Ansage *in das Gespräch* einspielen — „plattformneutral, keine Sonder-API". **Eine intensive Prüfung gegen primäre Quellen (Apple- und Android-Doku, Entwicklerforen) hat diese Annahme widerlegt — in beide Richtungen, auf beiden Plattformen.**

**Mithören (Audio-Capture) während eines Calls:**

- *iOS:* Sobald die Audio-Session eines Anrufs (Mobilfunk *oder* CallKit-VoIP wie WhatsApp/Telegram) aktiv wird, **deaktiviert iOS die Audio-Session der Dritt-App** und stellt eine Interruption zu; die App wird häufig suspendiert. Mikrofon-Input ist exklusiv beim Call. Es gibt kein Entitlement und keinen Hintergrund-Modus, der gleichzeitiges Mithören erlaubt — Apple-Mitarbeiter bestätigen im Entwicklerforum, dass es dafür keine öffentliche API gibt. Selbst Apples eigene Sprachmemo-App verweigert die Aufnahme während eines Anrufs.
- *Android:* Die Regeln unter „Sharing audio input" (ab Android 10) **silencen** eine gewöhnliche Mic-Aufnahme während `MODE_IN_CALL` *und* `MODE_IN_COMMUNICATION` (VoIP). VoIP-Apps nutzen `VOICE_COMMUNICATION` (privacy-sensitive, höhere Priorität) → die Dritt-App bekommt Stille. Die einzigen Pfade zu Call-Audio sind ein privilegierter vorinstallierter Dialer (`CAPTURE_AUDIO_OUTPUT`) oder ein AccessibilityService — letzterer **seit Mai 2022 für Call-Recording aus dem Play Store verbannt**. Der Lautsprecher-Trick „funktioniert auf manchen OEM-Geräten", ist aber nie garantiert.

**Ansage in das Gespräch (Audio-Playback) während eines Calls:**

- *iOS:* Das Einspielen von Tönen in einen aktiven Call ist stark eingeschränkt und in neueren Versionen (iOS 17+) faktisch nicht mehr möglich; die App-Audio wird vom Call ducked/unterbrochen.
- *Android:* Es gibt **keine öffentliche API, um Audio in den Call-Uplink einzuspeisen**. Bleibt nur die akustische Kopplung über den Lautsprecher — fragil, lautstärke- und geräteabhängig, nicht garantiert.

**Konsequenz:** Ein In-Call-Live-Mechanismus (Mithören *oder* Ansage ins Gespräch) ist **als regelkonforme Dritt-App auf keiner der beiden Plattformen tragfähig**. Die Audio-Session-Arbitrierung blockiert ihn auf OS-Ebene — nicht bloß undokumentiert, sondern dokumentiert und durchgesetzt. Quellen siehe Datei [`10_fraud_landscape_research.md`](10_fraud_landscape_research.md)-Methodik und das technische Verifikations-Arbeitspaket; Kernbelege: Apple Audio Session Programming Guide / `interruptionNotification`; Apple Developer Forums (kein öffentliches API, FB18434531); Android „Sharing audio input" und AOSP „Concurrent capture"; Google-Play-Policy zum Accessibility-Call-Recording-Verbot (2022).

### Übersicht 

|#|Mechanismus|Beispiel-Apps|Bekommt den Gesprächsinhalt?|Wo läuft die Analyse?|Für dich nutzbar?|
|---|---|---|---|---|---|
|1|**Rufumleitung in die Cloud** (bedingte Weiterleitung → Server-Bot)|RoboKiller, YouMail, Truecaller Assistant, **Gini**|✅ voll|☁️ Cloud|✅ (= dein VoIP-Weg, aber Cloud)|
|2|**Dreier-Konferenz auf Aufnahme-Leitung**|TapeACall, viele iOS-Recorder|✅ voll|☁️ Cloud|⚠️ manuell, nicht echtzeit|
|3|**Netz-/Carrier-seitige Analyse**|Hiya (Samsung Smart Call, AT&T)|❌ nur Label/Reputation|📡 Mobilfunknetz|❌ braucht Carrier-Deal|
|4|**Nur Metadaten + Reputations-DB**|Truecaller, Hiya, Clever Dialer|❌ nur Nummer|Gerät/Cloud|✅ aber inhaltsblind|
|5|**Privilegierte System-/OEM-Funktion**|Pixel Call Screen/Live Caption, **Samsung Bixby Text Call**, iOS 18|✅ voll, **lokal, Echtzeit**|📱 on-device|❌ nur OEM/OS|
|6|**Root / Shizuku / ADB-privilegiert**|BCR, ACR Phone Helper (Shizuku)|✅ voll (beide Seiten)|📱 on-device|✅ für Studiengeräte|
|7|**Accessibility-Aufnahme**|Cube ACR (älter), ACR|⚠️ meist nur eigene Stimme|📱 on-device|❌ unzuverlässig, Play-verboten|
|8|**VoIP-eigene App** (Audio gehört der App)|WhatsApp/Signal, Softphones|✅ voll, lokal|📱 on-device|✅ (= dein VoIP-Dialer)|

## Die Mechanismen im Detail

**1 — Rufumleitung in die Cloud.** Der Standardweg der „KI-Anrufschützer". Per _bedingter Rufumleitung_ (Carrier-Codes) gehen abgelehnte/unbeantwortete Anrufe an die Server des Anbieters; dort läuft Spracherkennung + KI + Sprachausgabe, das Gerät bekommt nur Transkript/Risiko-Score zurück. RoboKiller braucht explizit „Conditional Call Forwarding", YouMail _ersetzt deine Mailbox_. **Das ist exakt der Gini-Mechanismus** — und derselbe Trick wie dein VoIP-Weg, nur dass die Analyse in der **Cloud** statt auf dem Gerät passiert.

**2 — Dreier-Konferenz.** Genau deine frühere „Teilnehmer einladen"-Idee, gelöst über einen Server: [TapeACall](https://www.tapeacall.com/blog/how-to-record-iphone-calls-the-comprehensive-guide) startet einen zweiten Anruf zur eigenen Aufnahme-Nummer und _merged_ ihn als dritten Konferenzteilnehmer; diese Leitung zeichnet auf. Funktioniert auf iOS, weil Konferenz-Calls über die CallKit-UI erlaubt sind — aber manuell pro Anruf und nicht für Echtzeit-Warnungen geeignet.

**3 — Netz-/Carrier-seitig.** [Hiya](https://www.hiya.com/samsung/products-smart-call) (hinter Samsung Smart Call und AT&T Call Protect) analysiert **im Netz** des Carriers, pro Anruf, anhand von Mustern im Netzwerkverkehr — das Gerät bekommt nur die Kategorie („Verdacht auf Betrug"). **Kein Audio-Zugriff auf dem Gerät**, dafür eine Carrier-Partnerschaft nötig.

**4 — Nur Metadaten.** Die meisten „Spam-Blocker" (Truecaller etc.) gleichen nur die _Nummer_ gegen riesige Crowd-Datenbanken ab und nutzen `CallScreeningService` (Android) bzw. `CallDirectory` (iOS), um vor dem Klingeln zu blocken/labeln. Smooth und Store-konform — fängt aber **keine** inhaltsbasierten Schock-/Enkeltrick-Anrufe mit gespoofter/unbekannter Nummer.

**5 — Privilegierte System-Funktion — der wichtigste Vergleich für dich.** **Samsung Bixby Text Call** ist quasi _dein Use-Case in fertig_: es nimmt Anrufe an, **transkribiert die Gegenseite in Echtzeit komplett on-device** („On-Device Bixby … without transferring any data online"). Genauso Pixel Live Caption/Call Screen und iOS 18.1 (Aufnahme + Transkript **lokal** via Apple Intelligence). **Das beweist: dein Ziel ist technisch real — aber nur das OEM/Betriebssystem darf es.** Für Dritte gesperrt.

**6 — Root / Shizuku.** [BCR](https://github.com/chenxiaolong/BCR) und ACR Phone Helper bekommen _echtes Zwei-Wege-Audio_ lokal, indem sie sich die privilegierte Berechtigung `CAPTURE_AUDIO_OUTPUT` per Root **oder Shizuku** holen. **Shizuku ist hier interessant für dich:** es erteilt App-Komponenten ADB-/Shell-Rechte **ohne Root**, über einen einmaligen ADB-Befehl. Für Endnutzer/Ältere zu fummelig — aber für **deine eigenen Studien-/Testgeräte** ein gangbarer Weg zu sauberem Zwei-Wege-Audio, lokal, ohne Custom-ROM.

**7 — Accessibility.** Wie früher diskutiert: auf modernem Android meist nur die eigene Stimme, seit Mai 2022 im Play Store verboten (Sideload geht). Unzuverlässig.

**8 — VoIP-eigene App.** Signal/WhatsApp besitzen ihr Anruf-Audio (self-managed `ConnectionService`); ein Softphone genauso. **Das ist dein VoIP-Dialer-Weg** — der einzige, der vollen Inhalt + lokale Analyse + Geräteunabhängigkeit kombiniert.

### Korrigierte Architektur-Wahl für Schicht 3

Schicht 3 wird in zwei Realisierungsstufen getrennt:

**Stufe A — Bildschirm-basierter Live-Begleiter (App, MVP-tauglich, kein Call-Audio).** Der Senior drückt im Verdachtsfall den großen Knopf; die App **greift nicht auf das Call-Audio zu**, sondern führt parallel auf dem Bildschirm durch eine ruhige, großformatige Coaching-Sequenz (geführte Q&A, vgl. F2.4): „Werden Sie zur Eile gedrängt? Wird eine TAN/Geld verlangt? Echte Polizei verlangt nie Geld." Der **Abschreckungseffekt** wird verhaltensbasiert statt per Audio-API erzeugt: Die App leitet den Senior an, einen Satz **selbst laut auszusprechen** („Ich lasse diesen Anruf gerade von meiner Sicherheits-App prüfen"). Das bricht die Heimlichkeit — den zentralen Hebel der Täter — *ohne* jeden Eingriff in den Audio-Stream. Nach dem Auflegen: Sprachnotiz-Analyse (F2.2). Rechtlich unkritisch, weil kein fremdes Wort verarbeitet wird.

**Stufe B — Hardware-Begleitgerät (Vision-Layer 2, echte In-Call-Audio-Wirkung).** Die ursprünglich angedachte Mechanik (eigenes Mikrofon hört den Lautsprecher, eigene Ansage in den Raum) ist **nur out-of-band realisierbar** — also über ein vom Telefon unabhängiges Hardware-Gerät, das nicht der Audio-Session-Arbitrierung des Telefons unterliegt. Dieser Befund **erhöht die strategische Bedeutung des Hardware-Layers**: Er ist nicht bloß eine 80+-Komfortvariante, sondern der einzige tragfähige Pfad für echte Live-Audio-Begleitung. Details unten unter „Hardware-Alternative".

---

## Ursprüngliche Architektur-Wahl (überholt — zur Nachvollziehbarkeit dokumentiert)

> Hinweis: Der folgende Abschnitt ist durch die Korrektur oben überholt, was die *technische* Machbarkeit der In-Call-Audio-Mechanik betrifft. Die *rechtliche* und *wirkungstheoretische* Analyse bleibt gültig und ist in die korrigierte Stufe A eingeflossen.

Statt heimlicher Live-Coaching-Funktion: **Transparenter Begleitmodus mit Abschreckungs-Ansage.**

Mechanik (technisch überholt):
1. Senior bekommt verdächtigen Anruf, drückt einen einzigen großen Knopf in der App ("Diesen Anruf prüfen lassen")
2. App weist an: "Bitte stellen Sie den Anruf auf Lautsprecher und legen Sie das Telefon auf den Tisch."
3. App spielt deutliche Audio-Ansage *in das Gespräch* — **technisch nicht tragfähig, siehe Korrektur oben**
4. Mikrofon erfasst Lautsprecher-Audio, lokale Live-Transkription — **technisch nicht tragfähig, siehe Korrektur oben**

**Rechtlich (weiterhin gültig):** Wo eine Verarbeitung stattfindet und der Anrufer informiert ist → konkludente Einwilligung; bei lokaler Verarbeitung ohne Audio-Speicherung greift § 201 vermutlich nicht. Zusätzlich Notwehr-Argument verfügbar. In Stufe A entfällt die Frage ohnehin, weil kein fremdes Wort verarbeitet wird.

**Wirkungstheoretisch (weiterhin gültig, jetzt verhaltensbasiert umgesetzt):** Die offene Ansage ist die Hauptschutzwirkung. Schockanruf-/Enkeltrick-Täter arbeiten mit Heimlichkeit und brechen ab, sobald Transparenz entsteht. In Stufe A wird dieser Effekt dadurch erzeugt, dass der **Senior selbst** den Prüf-Satz ausspricht — gleiche Abschreckung, ohne Audio-API.

## SMS-Quarantäne — die zweite Asymmetrie

Auf iOS nur als rudimentäre Spam-Filter-Variante möglich (Message Filter Extension, nur unbekannte Absender, keine Speicherung). Auf Android voller Lesezugriff (mit erheblichem Onboarding).

**Strategische Konsequenz:** SMS-Quarantäne ist *kein* MVP-Feature, sondern Erweiterung in zweiter Welle. Außerdem hat Apple mit iOS 26 "Screen Unknown Senders" als systemweite Funktion eingeführt — der Mehrwert einer eigenständigen SMS-Quarantäne auf iOS sinkt damit.

## Plattform-Strategie

**Empfehlung:** Android-first mit ca. 3 Monaten Vorlauf, iOS-Light parallel.

Begründung:
- Android: mehr Funktionsumfang möglich, mehr empirische Daten für DiPA-Studie
- iOS: bewusst reduzierter Funktionsumfang mit klarer Kommunikation an Nutzer:innen
- Senior-Zielgruppe in Deutschland verteilt sich ~60:40 Android:iOS (mit Varianz nach Einkommen und Alterskohorte)
- Hannover/CISPA-Standort hat Zugang zu Senior-UX-Studien für beide Plattformen

## Hardware-Alternative — Vision-Layer (nicht MVP)

Ein separates Hardware-Gerät ("Schutz-Lautsprecher") parallel zum Telefon umgeht alle App-Store- und Plattform-Restriktionen, weil es nicht auf System-APIs angewiesen ist und **nicht der Audio-Session-Arbitrierung des Telefons unterliegt**. Aktivierung über großen physischen Knopf, Audio-Erfassung über eigenes Mikrofon, Ansage über eigenen Lautsprecher in den Raum.

**Wann interessant:** Für die 80+-Zielgruppe, die mit Smartphone-UX überfordert ist. Als Premium-Variante mit DiPA-Wirknachweis-Vorteil (Hardware-Variante leichter standardisiert messbar). **Nicht im MVP.**

**Statusänderung durch die Juni-2026-Korrektur:** Die Hardware-Variante ist nicht mehr nur „nice to have für Hochaltrige", sondern der **einzige tragfähige Pfad für echte Live-Audio-Begleitung** (Mithören + Ansage in den Raum, den die Call-Mikrofone bei Lautsprecher-Betrieb akustisch übertragen). Sie sollte daher in der Produktstrategie aufgewertet und im Wirknachweis-Studiendesign früh als eigener Arm mitgedacht werden — bleibt aber außerhalb des MVP-Scopes.

## Konkrete nächste Schritte (Plattform und Recht)

1. **Juristisches Audit** der finalen Architektur durch zwei bis drei Strafrechts- und Telekommunikationsrechts-Anwält:innen. 4–6 Wochen Vorlauf, niedriger vierstelliger Beratungsaufwand. Output: Memorandum, das im Investoren-Pitch und im DiPA-Antrag verwendet werden kann.
2. **Technische Voruntersuchung** mit einem iOS-Entwickler, der Erfahrung mit CallKit, Call Directory Extensions und ILMessageFilterExtension hat. Mögliche Kontakte: Truecaller-Deutschland, Hiya, tellows (Hannover — Standortvorteil).
3. **DSGVO-Folgenabschätzung** früh ansetzen — vermutlich ohnehin Pflicht im DiPA-Antrag. Verarbeitung sensibler Inhalte (Stimmaufnahmen, Screenshots privater Kommunikation, Finanzdaten in Folge-Schritten) begründet hohe Anforderungen.
4. **Datenresidenz-Entscheidung:** Hosting in Deutschland (Zielbild: BSI C5 Testat) ist keine Nice-to-have, sondern Eintrittskarte für Banken und Pflegekassen.

## Was wir Investoren NICHT versprechen

- "Heimliche Hintergrund-Erkennung von Betrugsanrufen" — strukturell nicht möglich, juristisch nicht erlaubt
- "Voller SMS-/E-Mail-Schutz auf iOS" — Plattform lässt das nicht zu
- "Echtzeit-Reaktion auf eingehende Anrufe von Crowdsourcing-Daten" — auf iOS nicht möglich, auf Android nur eingeschränkt
- "Stimmen-Erkennung von Familienmitgliedern bei Schockanruf" — technisch unzuverlässig in dieser Anwendung
- "Live-Mithören des laufenden Anrufs durch die App" — auf iOS und Android durch Audio-Session-Arbitrierung blockiert (Juni-2026-Korrektur); nur per Hardware-Begleitgerät out-of-band realisierbar
- "Einspielen einer Warn-Ansage in das laufende Gespräch durch die App" — keine öffentliche API (Uplink gesperrt; iOS-Playback im Call blockiert); echte In-Call-Wirkung nur per Hardware-Begleitgerät

→ Was wir *stattdessen* versprechen, steht in [`01_concept_and_product.md`](01_concept_and_product.md) und [`02_market_and_competition.md`](02_market_and_competition.md).
