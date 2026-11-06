# Demo-Geschichte: vom Beleg zum veränderten Cashflow

Diese Ergänzung gehört zum Bauauftrag. Alle Kunden, Zahlungshistorien und Nachrichten sind fiktiv. Die tatsächlich ausgeführte Jev-Prüfung bleibt davon getrennt: Ein Fixture enthält die erwartete Antwort, keinen bereits erfolgten Modellaufruf.

## Der sichtbare Nutzen

1. Demo-Daten laden. Der Plan zeigt im Basisfall keinen negativen Wochenschlussbestand.
2. Zahlungstreue öffnen. Studio Nord hat in zwölf vollständig bezahlten Demo-Rechnungen eine mediane Verspätung von 14 Tagen. Die Stichprobengrösse und der Zeitraum sind sichtbar.
3. Die vorbereitete Kunden-E-Mail laden. Sie kündigt für dieselbe CHF-14'000-Rechnung eine Zahlung am 2. Dezember statt 18. November an.
4. "Mit Jev prüfen" starten. Während die echte Anfrage läuft, bleibt der Plan bedienbar und der Dokumentbereich zeigt den Status. Danach stehen erkanntes Datum, zugehörige Rechnung und Originalsatz nebeneinander.
5. André bestätigt "Als Szenario übernehmen". Der Basisplan und die ursprüngliche Fälligkeit bleiben erhalten. Jetzt erscheint das bekannte Minimum CHF -5'000; der Endsaldo bleibt CHF 2'000.
6. Eine zweite Nachricht bestreitet eine Rechnungsposition, nennt aber keinen neuen Zahlungstermin. Die App markiert Klärungsbedarf und erfindet kein Datum.

Im Vortrag genügt die erste Nachricht. Streitfall und Teilzahlung sind vorbereitete zusätzliche Beispiele, keine weiteren Live-Bauaufträge.

## Daten und Berechnungen

- `fixtures/payment-history.json`: 48 vollständig bezahlte historische Rechnungen, vier fiktive Kunden, Mai bis Oktober 2026. Stichtag 6. November. Diese Rechnungen gehören nicht zu den offenen Bewegungen des sechs Wochen umfassenden Plans.
- `fixtures/expected-payment-history.json`: unabhängig berechnete Sollwerte für Anzahl, Pünktlichkeit und mediane Verspätung.
- `fixtures/payment-messages.json`: drei fiktive Nachrichten mit erwarteten Klassifikationen für Zusage, Streit und Teilzahlungsankündigung. Die importierbaren Dateien stehen unter `fixtures/messages/`; der Hauptfall ist `studio-nord-zusage.eml`.

Pünktlich bedeutet vollständig bezahlt am oder vor Fälligkeit. Für die Verspätungsstatistik gilt `max(0, fullyPaidDate - dueDate)` in Kalendertagen. Der Median wird über die vollständig bezahlten Rechnungen des angezeigten Zeitraums berechnet. Bei einem halben Tag für einen Terminvorschlag auf den nächsten ganzen Tag aufrunden. Keine Beobachtung nach dem Stichtag verwenden.

Ein Vorschlag aus Historie benötigt in dieser Demo mindestens fünf passende Beobachtungen und zeigt ihre Anzahl. Diese Grenze ist eine Darstellungsregel, keine statistische Validierung. Bei zu wenig Historie erscheint "Noch keine ausreichende Zahlungshistorie". Ein neuer Kunde erhält keinen erfundenen Score.

Die Quote bezieht sich ausdrücklich auf die vollständig bezahlten Rechnungen der Stichprobe. Offene, überfällige Rechnungen werden daneben separat gezählt; sie dürfen nicht als pünktlich gelten oder die bezahlte Stichprobe unbemerkt verändern. Die Demo-Historie ist keine allgemeine Kalibrierung eines Vorhersagemodells.

## Zusätzliche analytische Ansichten

- Balken je Kunde: pünktlich/verspätet, mit Anzahl der beobachteten Rechnungen.
- Verspätung in Tagen je Kunde: einzelne Beobachtungen und Median, statt unbegründeter Ausfallwahrscheinlichkeit.
- Drei vergleichbare Termine für eine offene Rechnung: vertragliche Fälligkeit, Vorschlag aus Historie und belegte Kundenzusage. Herkunft immer sichtbar.
- Auswirkungen im Cashflow: unveränderter Basisplan gegenüber einem bewusst übernommenen Szenario.
- Liste der Prüfhinweise: Zahlungszusage, strittige Position, angekündigte Teilzahlung oder fehlender Termin. Jeder Hinweis öffnet die Quelle.

Jev wählt Nachrichtentyp, Bezug zur Rechnung, explizites Datum und gegebenenfalls Betrag aus belegten Kandidaten. Code berechnet Quoten, Median, Kalenderdaten und Salden. Jevs Confidence beschreibt die Modellantwort auf die Textfrage; sie wird niemals als Wahrscheinlichkeit einer künftigen Zahlung dargestellt.

## Vertrag für echte Daten

Eigene Zahlungshistorie darf nur aus bestätigten tatsächlichen Zahlungsdaten bestehen. Eine importierte Rechnung oder der Satz "Wir haben überwiesen" beweist keinen Kontoeingang. Im ersten Prototyp genügt ein manuell bestätigter historischer Datensatz; Bank-/Buchhaltungsanbindung bleibt ausserhalb des Auftrags.

Speichere Historie getrennt von offenen Planeinträgen: lokale ID, Gegenpartei-Zuordnung, Rechnungsnummer, Rechnungsbetrag, CHF, Fälligkeit, Datum der vollständigen Zahlung und Herkunft `demo` oder `manual_confirmed`. Historische Datensätze zählen nie als künftige Einnahmen. Mehrdeutige Kundennamen benötigen eine bestätigte Zuordnung.

Nachrichtenanalysen speichern Quellen-ID, Rechnungsbezug, Status, Modell/Fragenversion, erkannte Zusage oder Streitmeldung und die verwendeten Originalstellen. Ohne klare Zuordnung oder bei fehlendem Datum keine automatische Terminänderung. Teilzahlungsankündigungen verändern weder den offenen Betrag noch den Status "bezahlt". Ein Datumswechsel geschieht nur nach Nutzerbestätigung als Szenario.

Erweitere die Service-Verträge um `loadPaymentHistory`, `saveConfirmedPaymentHistory`, `analyzePaymentMessage` und `applyPaymentProposalToScenario`. Nutze dieselbe geschützte TypeSafe-Konfiguration und dieselben Fehlerzustände wie beim Import. Der laufende Request darf die Oberfläche nicht blockieren; ein weiterer Jobdienst ist für diese begrenzte Demo nicht nötig.

## Abnahme dieser Ergänzung

- H01: Alle vier Kundensummen und Mediane stimmen exakt mit der Fixture überein; der eigene Plan ohne Historie zeigt keine Demo-Werte.
- H02: Alle historischen Zahlungen liegen am oder vor dem Stichtag. Sie verändern die sechs zukünftigen Wochensalden nicht.
- H03: Mindestens die Zusage und der Streitfall laufen gegen die echte Jev-API. Gefundener Originaltext und Datum passen zur Quelle. Die Sollantworten werden nicht als API-Antworten ausgegeben.
- H04: Die bestätigte Zusage verschiebt nur income-02 auf den 2. Dezember und liefert die bestehenden Szenario-Sollwerte. Ablehnen und wiederholtes Übernehmen sind ohne Doppeländerung möglich.
- H05: Streit ohne Datum erzeugt keinen Termin; Teilzahlungsankündigung keinen tatsächlichen Zahlungseingang. Neue oder geänderte Nachrichten machen frühere Vorschläge erkennbar veraltet.
- H06: Quoten/Median/Einzelbeobachtungen sind in Light und Dark lesbar, der Zeitraum und die Stichprobengrösse stehen direkt am Chart. Keine Zahlungs- oder Ausfallwahrscheinlichkeit aus Jev-Confidence.

Diese Ergänzung ist erst abgenommen, wenn H01 bis H06 tatsächlich geprüft wurden. Die zusätzliche Zahlungshistorie und Nachrichtenprüfung sind in den Paper-Frames `payment-history-light` und `payment-history-dark` dargestellt. Das belegt den Entwurf, noch keine bestandene Funktionsprüfung.

## Öffentliche Firmeninformationen

Als spätere Erweiterung eignen sich überprüfbare Registerinformationen und Veröffentlichungen über Konkursverfahren. Die Zürcher Notariate verweisen für den Verfahrensstand auf die [SHAB-Publikationen](https://www.notariate-zh.ch/de/konkurs/konkursverzeichnis). Eine Veröffentlichung benötigt eindeutige Firmenzuordnung, Datum und Originalquelle. Ein fehlender Treffer ist kein Bonitätsnachweis.

Betreibungsregisterauszüge sind kein frei abrufbarer universeller Credit Score. Drittauszüge verlangen einen Interessennachweis; Bonitätsauskunfteien haben eigene Zugangs- und Bearbeitungsbedingungen. Siehe [Kanton Basel-Stadt](https://www.bs.ch/en/topics/personliches-und-wohnen/wohnen/ordering-extract-debt-enforcement-register) und [EDÖB](https://www.edoeb.admin.ch/de/kredit-inkasso). Kein Live-Credit-Connector in diesem Bauauftrag.

Für eine spätere Darstellung solcher Signale nur vollständig fiktive Firmenprofile verwenden, eindeutig "simulierte Firmeninformation" nennen und keine erfundene SHAB-Quellenadresse anzeigen. Keine realen Firmen mit erfundenen Zahlungsausfällen oder Konkursmeldungen verbinden.

Weitere mögliche Erweiterungen sind Kundenkonzentration, ungewöhnliche Kostenänderungen und geänderte Bankverbindungen. Sie sind Ideen, keine zusätzliche Pflichtimplementierung dieses Auftrags. Eine Auffälligkeit ist ein Prüfhinweis und kein Betrugsnachweis.
