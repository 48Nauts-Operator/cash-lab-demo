# Fiktive Testdaten

Alle Firmen, Rechnungen, Nachrichten und Zahlungen in diesem Verzeichnis sind synthetisch. Nichts wurde versendet. Die `.eml` ist eine lokale Datei mit Adressen unter `example.test`.

- `demo-plan.json` und `expected-demo.json`: sechs Wochen, CHF-14'000-Rechnung, Referenzsalden und Analytics-Summen.
- `imports/`: sechs PDF-Dateien, eine E-Mail mit zwei PDF-Anhängen und sechs Textfälle; `expected.json` enthält die erwartete Behandlung.
- `payment-history.json` und `expected-payment-history.json`: 48 vollständig bezahlte Rechnungen und Zahlungstreue je Kunde. Keine zukünftigen Kontobewegungen.
- `payment-messages.json`: Zahlungszusage, bestrittene Position und Teilzahlungsankündigung. `expected` sind Sollwerte für spätere Tests, keine bereits erzeugten Jev-Antworten.
- `messages/`: dieselben drei Geschichten als importierbare `.eml`-Dateien; `studio-nord-zusage.eml` ist die Hauptvorführung.

`02-scan-invoice.pdf` enthält absichtlich nur ein gerendertes Bild, keine Textschicht. `06-encrypted.pdf` ist absichtlich passwortgeschützt. Das fiktive Fixture-Passwort ist `synthetic-fixture-only`; der Produktimport soll die Datei ablehnen. Fehlende Fälligkeit und mehrere Rechnungen pro PDF sind bewusst enthaltene Grenzfälle.

Die synthetischen Eingabedateien sind vorbereitet. Dieses Repository enthält keinen Generatorcode. Ihre Sollwerte sind Prüfvorgaben, keine Ergebnisse der neu zu bauenden Anwendung.

Die Fixture-Dateien und Rechensollwerte wurden lokal geprüft. Extraktionsqualität, OCR, echte Jev-Antworten und Browserintegration müssen erst die spätere Anwendung nachweisen.
