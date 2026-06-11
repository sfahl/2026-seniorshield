# 12 · Validierungs-Steckbrief — Schicht 3 Stufe A (F3.1a)

## Worum es geht

Die Juni-2026-Korrektur ([`05_platform_and_legal.md`](05_platform_and_legal.md)) hat die App-seitige In-Call-Audio-Mechanik gestrichen. Schicht 3 ruht im MVP jetzt auf **Stufe A (F3.1a)**: ein bildschirmbasierter Live-Begleiter ohne Call-Audio, dessen Abschreckungswirkung **verhaltensbasiert** entsteht — der Senior spricht selbst laut aus, dass der Anruf gerade von einer Sicherheits-App geprüft wird ([`11_featureset_and_feasibility.md`](11_featureset_and_feasibility.md)).

Diese Mechanik ist **unvalidiert**. Sie ersetzt das bisher als stärkstes Differenzierungsmerkmal markierte Feature und darf nicht ohne Beleg in Pitch, DiPA-Antrag oder MVP-Scope übernommen werden. Dieser Steckbrief definiert, wie sie geprüft wird.

## Die zentrale methodische Trennung

Der Erfolg von F3.1a hängt an zwei **verschiedenen** Wirkungsketten, die getrennt getestet werden müssen, weil sie unterschiedliche Methoden verlangen:

**Kette 1 — Deployability (am Nutzer messbar):** Kann und wird die Zielperson die selbst-gesprochene Ansage im akuten Schock-/Druckmoment tatsächlich abrufen und aussprechen? Versteht sie den Bildschirm-Begleiter, folgt sie ihm, fühlt sie sich handlungsfähiger? Das ist im Labor mit simulierten Anrufen sauber testbar.

**Kette 2 — Deterrence (am Täter wirksam, aber nicht direkt messbar):** Bricht der Täter den Betrugsversuch ab, wenn die Ansage fällt? Diese Kette ist der eigentliche Schutzanspruch — aber man kann aus offensichtlichen ethischen und rechtlichen Gründen **keine echten Täter rekrutieren oder provozieren**. Kette 2 ist daher nur über Proxy-Methoden zugänglich (Evidenzsynthese, Experten-Elicitation, retrospektive Fallanalyse, später Felddaten).

Diese Trennung ist der Kern des Steckbriefs. Ein häufiger Fehler wäre, aus einer gelungenen Labor-Deployability (Kette 1) auf reale Schutzwirkung (Kette 2) zu schließen. Beides muss separat belegt werden.

## Hypothesen

**Kette 1 (Deployability):**

- **H1 (Abruf unter Stress):** Unter induziertem Zeitdruck/Stress setzen Teilnehmer:innen mit F3.1a die Prüf-Ansage signifikant häufiger ein als eine Kontrollgruppe ohne App die Standard-Schutzhandlung (auflegen/rückfragen).
- **H2 (Verständlichkeit/Tempo):** Der Bildschirm-Begleiter wird im akuten Moment verstanden und befolgt (Comprehension, Time-to-first-Action innerhalb eines definierten Fensters).
- **H3 (Selbstwirksamkeit):** F3.1a erhöht die wahrgenommene Selbstwirksamkeit im Umgang mit Verdachtsanrufen gegenüber Kontrolle (validierte Skala).

**Kette 2 (Deterrence, proxy-belegt):**

- **H4 (Abbruch-Plausibilität):** Die offene Selbst-Ansage erzeugt bei Tätern eine Abbruchwahrscheinlichkeit, die der einer dritten anwesenden Person / einer Transparenz-Intervention nahekommt. Belegweg: Evidenzsynthese + Experten-Elicitation, später Feld.

## Gestufter Validierungsplan

### Tier 0 — Schreibtisch: Evidenzsynthese + Experten-Elicitation (Wochen 1–6, niedrige Kosten)

Adressiert primär Kette 2. Bündelt die vorhandene Evidenz, dass Täter bei Transparenz/Heimlichkeitsbruch abbrechen ([`10_fraud_landscape_research.md`](10_fraud_landscape_research.md): Bankschalter-Interventionen, das stundenlange In-der-Leitung-Halten als Isolationshebel, Polizei-Verhaltensregeln), und ergänzt sie um strukturierte Experten-Urteile:

- **LKA/BKA-Ermittler:innen** aus dem Callcenter-Betrugs-Bereich: Wie reagieren Täter auf erkennbare Drittbeobachtung/Transparenz im laufenden Gespräch?
- **Scam-Baiter-Community / dokumentierte Mitschnitte:** beobachtete Abbruchauslöser.
- **Optional, mit Sorgfalt:** ehemalige Täter / Aussteiger über Mittler (Aussteigerprogramme), rein qualitativ.
- **Methode:** strukturierte Elicitation (z. B. kalibrierte Schätzungen), nicht anekdotisch. Output: begründete Bandbreite für die Abbruchwahrscheinlichkeit + Liste der Bedingungen, unter denen die Selbst-Ansage *nicht* wirkt (z. B. besonders aggressive falsche-Polizei-Skripte).

**Gate 0:** Wenn Experten die verhaltensbasierte Selbst-Ansage als plausibel wirksam einschätzen → Tier 1. Wenn sie überwiegend Wirkungslosigkeit oder Eskalationsrisiko sehen → F3.1a-Mechanik überdenken, bevor Laborkosten anfallen.

### Tier 1 — Laborstudie mit simulierten Anrufen (Monate 2–6)

Adressiert Kette 1 vollständig und Kette 2 indirekt (perceived deterrence). Dies ist das methodische Heimspiel des Lehrstuhls (Senior-USP, randomisierte Designs).

**Design:** randomisiert, drei Arme (between-subjects, ggf. teilweise within mit verschiedenen Szenarien):

- **Arm K (Kontrolle):** simulierter Verdachtsanruf, keine App.
- **Arm A1 (Bildschirm-Begleiter):** F3.1a nur als Bildschirm-Coaching, ohne Selbst-Ansage-Aufforderung.
- **Arm A2 (Bildschirm-Begleiter + Selbst-Ansage):** vollständiges F3.1a inkl. Aufforderung, den Prüf-Satz laut auszusprechen.

Der Vergleich A1 vs. A2 isoliert den spezifischen Beitrag der Selbst-Ansage — die eigentlich offene Frage.

**Simulierter Anruf (Wizard-of-Oz):** geschulte Schauspieler:innen spielen standardisierte Schockanruf-/Enkeltrick-/falsche-Bank-Skripte (aus den Familien A/B in Datei 10). Realistischer Druck *kontrolliert* und ethisch vertretbar induziert (klare Obergrenzen, kein realer Schaden, sofortiges Debriefing). Es geht nicht um echte Täuschung über Geld, sondern um eine ökologisch valide Stress-/Druck-Situation.

**Stichprobe:** Senior:innen unterschiedlicher Tech-Affinität und Alterskohorten (inkl. 75+); Rekrutierung über bestehende LUH/CISPA-Senior-Panels, BAGSO/Wohlfahrtsverbände. Fallzahl per Power-Analyse auf den primären Endpunkt (Deployment-Rate, H1); als Orientierung passt dies in den in [`07_roadmap_and_next_steps.md`](07_roadmap_and_next_steps.md) skizzierten Studienrahmen (n=200–400).

**Endpunkte / Instrumente:**

- *Primär (H1):* Deployment-Rate der Schutzhandlung bzw. Selbst-Ansage (beobachtet/kodiert).
- *Sekundär (H2):* Time-to-first-Action; Comprehension-Check des Bildschirm-Begleiters; Bedien-Fehlerrate.
- *Sekundär (H3):* wahrgenommene digitale Sicherheit und Selbstwirksamkeit (validierte Skalen, dieselben wie in der DiPA-Wirknachweis-Logik, Datei 04/07).
- *Sekundär (Kette 2, proxy):* perceived deterrence / Glaubwürdigkeit der Ansage aus Nutzersicht; qualitatives Erleben (würde ich das real tun?).
- *Begleitend:* Caregiver-Burden-Effekt bei beteiligten Angehörigen (Angehörigenentlastung als DiPA-Argument).

**Gate 1:** A2 zeigt signifikant höhere Deployment-Rate und Selbstwirksamkeit ohne Eskalations-/Überforderungssignale → F3.1a für MVP bestätigt. Kein Unterschied A1 vs. A2 → Selbst-Ansage streichen, reinen Bildschirm-Begleiter behalten. Überforderung/Verschlechterung → F3.1a-UX grundlegend überarbeiten.

### Tier 2 — Ökologische Validität / Feld (ab Anker-Bank-Pilot, Monate 9+)

Adressiert Kette 2 erstmals real. Im Anker-Bank-Pilot ([`03_business_model_payers.md`](03_business_model_payers.md), [`07_roadmap_and_next_steps.md`](07_roadmap_and_next_steps.md)) mit echten, vom Nutzer als verdächtig markierten Anrufen: selbstberichtete Outcomes (Abbruch des Anrufs nach Ansage, vermiedene Übergaben), gekoppelt an die ohnehin laufende Wirknachweis-Studie. Kein RCT auf Täterseite möglich — aber Vorher-Nachher- und Nutzungs-Korrelations-Evidenz.

## Separater Technik-Test: akustische Restpfade (Geräte-Matrix)

Unabhängig von der Verhaltensvalidierung sollte die technische Sperre **empirisch auf einer Geräte-Matrix** bestätigt werden, damit die Architektur-Aussage belastbar dokumentiert ist (für CTO-Gespräche/technische DD). Dies ist ein reiner Technik-Test, keine Humanstudie:

- **Aufbau:** Test-App mit `AudioRecord` (Android, `AudioSource.MIC`) bzw. `AVAudioSession`-Aufnahme (iOS) während eines aktiven Anrufs auf Lautsprecher; je für Mobilfunk, WhatsApp, Telegram.
- **Matrix:** mind. je 2 aktuelle Pixel-/Samsung-/Mittelklasse-Android-Geräte über zwei Android-Versionen + 2 iPhones über zwei iOS-Versionen.
- **Messung Android:** `adb shell dumpsys audio` auf `muted: true` prüfen und Buffer auf Stille analysieren; dokumentiert, ob/auf welchen OEMs ein akustischer Restpfad „leakt".
- **Messung iOS:** Interruption-/Suspension-Verhalten der Audio-Session protokollieren.
- **Zweck:** Bestätigt die Sperre als Tatsache (statt als Literaturschluss) und identifiziert etwaige OEM-Ausnahmen — relevant nur für die Frage, ob ein optionaler, klar als „best effort/gerätabhängig" gekennzeichneter Pfad existiert (kein MVP-Versprechen).

## Ethik / IRB

- **Getrennte IRB-Voten** für Universität vs. Startup, keine Dual-Use-Datenvermischung ohne explizite Einwilligung ([`08_risks_and_open_questions.md`](08_risks_and_open_questions.md), Forschungsethik-Dilemma).
- **Stress-Induktion mit klaren Grenzen:** simulierte Anrufe, kein realer finanzieller Druck, jederzeitiger Abbruch, strukturiertes Debriefing; besondere Vulnerabilität der Zielgruppe (Hochaltrige, evtl. kognitive Einschränkungen) berücksichtigen.
- **Keine Provokation realer Täter** in keiner Tier-Stufe.
- Beirat-Mitglied mit Forschungsethik-Expertise einbeziehen.

## Entscheidungs-Gates (Zusammenfassung)

| Gate | Frage | Konsequenz bei Nein |
|---|---|---|
| 0 | Halten Experten die Selbst-Ansage für plausibel wirksam? | F3.1a-Mechanik vor Laborkosten überdenken |
| 1 | Setzen Senior:innen die Ansage im Stress ein, fühlen sich handlungsfähiger, ohne Überforderung? | Selbst-Ansage streichen oder UX überarbeiten |
| 2 | Brechen reale Anrufe nach der Ansage ab (Felddaten)? | Schicht-3-Schutzanspruch nur über Hardware-Layer (Stufe B) tragen |

## Grobaufwand und Sequenz

Tier 0 (6 Wochen, niedrige Kosten) → Tier 1 (Laborstudie, in den bestehenden UX-Studienrahmen Monat 4–9 integrierbar) → Tier 2 (mit Anker-Pilot ab Monat 9). Tier 0 und der Technik-Matrix-Test können sofort und parallel starten; beide sind günstig und liefern schnelle Go/No-Go-Signale, bevor größere Mittel gebunden werden. Die operativen Instrumente dazu (Experten-Interviewleitfaden, Geräte-Matrix-Test-Spezifikation) stehen in [`13_tier0_field_materials.md`](13_tier0_field_materials.md).

→ Verknüpft mit dem Studiendesign-Arbeitspaket in [`07_roadmap_and_next_steps.md`](07_roadmap_and_next_steps.md) und der DiPA-Wirknachweis-Logik in [`04_dipa_pathway.md`](04_dipa_pathway.md): dieselben validierten Skalen (wahrgenommene Sicherheit, Selbstwirksamkeit, Caregiver Burden) tragen doppelt — F3.1a-Validierung *und* DiPA-Nutzennachweis.
