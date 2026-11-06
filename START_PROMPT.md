# Startprompt für den Demo-Testlauf

Für einen Wiederholungslauf auf GitVM zuerst `docs/gitvm-run.md` lesen und dessen Modus, Release-Gate, Startpaket, Timer und Ersatzstand anwenden. Das vorbereitete Template enthält Werkzeuge und Abhängigkeiten. Ein vollständiger Neubau startet mit dem Paket `blank`; `ready` bleibt die separate fertige Ersatzversion. Ohne bestandene öffentliche Abnahme nur private Erreichbarkeit melden. 20 Minuten sind ein zu messendes Ziel.

Ziel ist ausschliesslich `https://github.com/48Nauts-Operator/cash-lab-demo.git`. Arbeite in dessen frischem Checkout und prüfe den Git-Remote. Dieses Repository enthält nur Bauunterlagen, Designreferenzen und synthetische Eingaben. Die Anwendung entsteht während dieses Laufs. Kopiere keinen fertigen Stand aus einem anderen Repository.

Baue Cashflow Lab in diesem Repository vollständig gemäss `BUILD_SPEC.md` und `DEMO_STORY.md`. Lies zuerst `AGENTS.md`, `docs/preflight.md` und die Fixtures. Prüfe vorhandenen Code, bevor du neu anlegst. Ziel ist eine lokal bedienbare, dauerhaft speichernde Anwendung, deren Demo und echte Importwege im Browser geprüft sind.

Führe G0 bis G5 aus: Voraussetzungen prüfen, das vorbereitete Design aus Cash-Lab-Demo-01 über Paper MCP lesen, gegen sämtliche Anforderungen visuell und funktional prüfen und nötige Revisionen abschliessen. Danach Anwendung implementieren, reale Integrationen und Browserabläufe testen, Fehler beheben und den fertigen Stand dokumentieren. Arbeite nach bestandenen Gates selbständig weiter. Eine menschliche Zwischenfreigabe ist für routinemässige lokale Schritte nicht nötig.

Gestaltung: Light und Dark, blaue Akzente, Dark mit dunkelgrauem Verlauf. Theme-Wechsel nur als Sonnen-/Mond-Icon mit zugänglichem Namen. Rechts ein einklappbarer Bereich für Dokumente, Rechnungen und Importstatus. Erhalte Entwürfe beim Einklappen. Verwende den geprüften Master; die kurze Paper-Demo arbeitet auf einer Kopie.

Baue drei echte Seiten: Plan, Analysen und Settings. Settings enthalten Firmendaten sowie Jev-Key, Modell und Verbindungstest ohne Offenlegung gespeicherter Secrets. Analysen zeigen Forecast, geplante Volumen, Kostenkategorien und das belegte Jev-Ergebnis je Rechnung. Auf dunklem Grund müssen alle Texte und Icons hell und gut lesbar bleiben.

Nutze die vorbereiteten 48 fiktiven historischen Rechnungen für Zahlungstreue und typische Verspätung je Kunde. Lass Jev die synthetische Studio-Nord-E-Mail tatsächlich prüfen. Erst nach Nutzerbestätigung wird deren Zahlungstermin als Szenario übernommen. Historische Zahlungen zählen nicht erneut in den Forecast. Modell-Confidence wird nie als Zahlungswahrscheinlichkeit angezeigt. Keine echte Bonitätsauskunft oder Bankanbindung vortäuschen.

Nutze den Demo-Daten-Button und den festgelegten CHF-Datensatz. Implementiere Import von PDF mit Text, lesbaren gescannten PDF sowie `.eml` mit PDF-Anhängen und eingefügtem E-Mail-Text. Zeige Herkunft und bearbeitbare Werte vor jeder Übernahme. Jev wählt belegte Werte; Code berechnet Geld und Kalenderdaten. Nutzer bestätigen Ein-/Ausgang, offenen Betrag und erwartetes Zahlungsdatum. Lieferantenrechnungen müssen als Ausgaben mit Kostenkategorie erkannt werden. Eine vorgegebene Zahlungsrichtung gehört zur Jev-Eingabe und zur Einwilligung. Originalwährung erhalten; USD/EUR/GBP nur mit angezeigtem datiertem ECB-Kurs und separater Bestätigung in CHF übernehmen. Fehlende oder veraltete Kurse niemals ersetzen.

Der TypeSafe-Schlüssel wird über lokale serverseitige Konfiguration bereitgestellt. Prüfe seine Verfügbarkeit ohne ihn auszugeben. Fehlende Zugänge, nicht verbundene Paper-Dateien und unbekannte Postfachanforderungen darfst du nicht erfinden. Der vereinbarte Ausgangsumfang ist E-Mail-Datei/Text; ein direkt verbundenes Postfach ist kein heimlicher Ersatz und keine Voraussetzung für diese Version.

Wenn dieser Auftrag ausdrücklich als Multi-Agent-Lauf gestartet wird, verteile die in `BUILD_SPEC.md` benannten Rollen. Ein Integrator bleibt für den gesamten Ablauf verantwortlich. Halte die Designfreigabe und gemeinsam festgeschriebenen Verträge ein. Bei einem einzelnen Agenten laufen dieselben Aufgaben nacheinander.

Beende die Arbeit erst nach den Abnahmekriterien oder mit einem belegten externen Blocker. Teste selbst, statt mir die Prüfung zu überlassen. Keine simulierten Erfolgsmeldungen, keine toten Buttons, keine ausgelassenen Pflichtfunktionen. Änderungen an bestehenden Portbelegungen oder anderen Anwendungen sind nicht Teil des Auftrags.

Liefere die lokale URL, echte Start-/Stoppbefehle, Testnachweise, Screenshots mit synthetischen Daten und den dokumentierten Stand. Committe den fertigen lokalen Stand. Push und Veröffentlichung richten sich nach meiner ausdrücklichen Freigabe im ausführenden Gespräch.
