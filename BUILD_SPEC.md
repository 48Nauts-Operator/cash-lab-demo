# Cashflow Lab: verbindlicher Bauauftrag

Version 1, 6. November 2026. Zielrepository: `https://github.com/48Nauts-Operator/cash-lab-demo.git`.

Dieser Auftrag beschreibt den vollständigen lokalen Prototyp und die Vorbereitung eines kurzen Live-Baus. Ein fertiges Paper-Design ist der Ausgangspunkt. Der aktuelle Implementierungs- und Prüfstatus steht in `docs/preflight.md` und später in `memory/state.md`. Eine Spezifikation oder ein Design ist noch keine funktionierende Anwendung.

## 1. Ziel und feste Grenzen

André betreibt eine kleine Schweizer Dienstleistungsfirma. Er möchte erkennen, wie spätere Kundenzahlungen den verfügbaren Geldbestand verändern. Die Anwendung beantwortet: "Kann ich meine Ausgaben bezahlen, wenn mein Kunde zwei Wochen später zahlt?"

Erfolg bedeutet: Der Nutzer lädt Demo-Daten oder importiert eigene Rechnungen, prüft die erkannten Werte, übernimmt offene Ein- und Auszahlungen in einen Plan und sieht die Wirkung einer verschobenen Zahlung. Daten und Szenario bleiben nach einem Neustart erhalten.

Pflichtumfang:

- P01: Deutsche Oberfläche, CHF, sechs Wochen, Light und Dark Theme mit blauen Akzenten. Dark verwendet einen dunkelgrauen Verlauf, keine dunkelblaue Grundfläche.
- P02: Getrennter Demo-Plan und eigener Plan; sichtbarer Button "Demo-Daten laden".
- P03: Anfangsbestand, Planbeginn, Einnahmen, Ausgaben und erwartete Zahlungstermine bearbeiten.
- P04: Basisplan und Szenario vergleichen; Aktion "+14 Tage" und "Szenario zurücksetzen".
- P05: Echte PDF mit Text, lesbare gescannte PDF, `.eml` mit PDF-Anhängen und eingefügten E-Mail-Text importieren.
- P06: Belegte Vorschläge mit Quellenansicht, Korrektur, Duplikatprüfung und ausdrücklicher Übernahme.
- P07: Echte serverseitige Jev-Integration; nachvollziehbare Fehler und manueller Korrekturweg.
- P08: Dauerhafte lokale Speicherung, reproduzierbarer Start, echter Browsernachweis und fertiger Ersatzstand für die Vorführung.
- P09: Settings-Seite für eigene Firma, serverseitig gespeicherten Jev-Zugang und Verbindungstest.
- P10: Analyse-Seite für zeitlichen Verlauf, geplante Volumen, Kostenkategorien und Ergebnisse je Rechnung.
- P11: Zahlungstreue aus fiktiver Historie und belegte Termin-Vorschläge aus Kunden-E-Mails gemäss `DEMO_STORY.md`. Historie bleibt von künftigen Planbewegungen getrennt.

- P12: Lieferantenrechnungen als Ausgaben verarbeiten. Eine ausdrückliche Zahlungsrichtung in die Jev-Prüfung einbeziehen; Lieferant, Betrag, Termine und Kostenkategorie aus belegten Kandidaten vorschlagen. Originalwährung erhalten. CHF-Umrechnung für USD/EUR/GBP separat bestätigen; fehlende, veraltete oder geänderte Kurse sperren die Übernahme. Alte Entwürfe zur erneuten Prüfung markieren.

Der E-Mail-Umfang ist bewusst `.eml` und Text. Ein direkt verbundenes Postfach ist eine offene Erweiterung, keine bereits bestätigte Anforderung. Gmail, Microsoft 365, IMAP, Weiterleitungsadressen, Hintergrundsynchronisation und Mailversand gehören nicht zu Version 1. Wenn André direkten Abruf verlangt, zuerst Anbieter und Zugriff klären und den Zeitplan neu schätzen; nicht stillschweigend einen Connector auswählen.

Ebenfalls ausserhalb: Rechnungsfinanzierung, Bankanbindung, Zahlungsverkehr, Buchhaltung, wiederkehrende Buchungen, Mehrbenutzerbetrieb und Veröffentlichung. USD, EUR und GBP können nach ausdrücklicher Bestätigung eines datierten ECB-Referenzkurses als CHF-Planwert übernommen werden. Der Wert ist eine Planungsschätzung, kein Bankabrechnungskurs. Andere Fremdwährungen und Gutschriften bleiben gesperrt. Es gibt keine KI-Prognose zukünftiger Umsätze.

## 2. Was vor und während der Vorführung passiert

### Vorbereitung

Vor dem Vortrag fertigstellen: Paper-Design mit Revision, vollständige Anwendung, Imports, TypeSafe-Konfiguration, Datenbank, Abhängigkeiten, Fixtures, Tests, Browserstart und funktionierender Ersatzstand. Die Einrichtung ist sichtbar als Vorbereitung zu benennen.

Paper-Datei: **Cash-Lab-Demo-01**. `design/manifest.json` enthält die tatsächlich erzeugten Datei-/Frame-IDs, URL, Themes und Exportdateien. Das Manifest darf erst nach erfolgreichen Paper-Aufrufen erstellt werden. Dieses Startrepository enthält Screenshots und Design-Daten, aber keine JSX-Exporte oder fertigen UI-Komponenten. Neu erzeugte Exporte während des Laufs sind Layoutreferenzen, keine Funktionsabnahme.

### Empfohlener Live-Block: 10 bis 15 Minuten

1. Minute 0 bis 2: Paper öffnen, den Agenten einen Frame über MCP lesen lassen und eine kleine Änderung an einer ausdrücklich als Demo-Kopie markierten Variante zeigen. Der geprüfte Master bleibt erhalten.
2. Minute 2 bis 3: Zum fertigen Design wechseln und den begrenzten Live-Auftrag zeigen.
3. Minute 3 bis 10: Im vorbereiteten Startstand die Aktion "+14 Tage" mit ihren Zustandsänderungen implementieren. Der Agent prüft selbst im Browser.
4. Minute 10 bis 12: CHF-14'000-Rechnung verschieben, Lücke zeigen, zurücksetzen. Anschliessend den vorbereiteten Import an der fertigen Anwendung demonstrieren, wenn die Zeit reicht.
5. Spätestens Minute 12: Wenn der geprüfte Live-Stand fehlt, zum fertigen Ersatzstand wechseln. Bis Minute 15 das Ergebnis erklären und weitergehen.

Dieser Live-Block ist eine geprüfte Funktionsänderung aus einem vorbereiteten Startstand. Er behauptet keinen vollständigen Neubau in 15 Minuten. Der vollständige Neubau mit den oben genannten Importwegen wird separat vorab gemessen.

Live-Auftrag, wörtlich verwendbar:

> Lies AGENTS.md und docs/live-run.md. Nutze das geprüfte Paper-Design. Ergänze im vorbereiteten Startstand die Aktion "+14 Tage" für einen erwarteten Rechnungseingang. Sie verändert ausschliesslich das Szenario. Aktualisiere Kurve, Wochentabelle und Kennzahlen gemeinsam. Prüfe mit der Rechnung über CHF 14'000 vom 18. November: neuer Eingang 2. Dezember, erste negative Woche 16. November, Minimum CHF -5'000, Endsaldo CHF 2'000. Die Fälligkeit bleibt 18. November. Prüfe auch Zurücksetzen und Neuladen. Öffne den Browser und führe den Ablauf selbst aus. Ändere keine Abhängigkeiten und baue keine weiteren Funktionen.

### Zeitmessung statt Versprechen

Erfasse beim vollständigen Probelauf sowie bei drei Wiederholungen des Live-Auftrags Start, erstes sichtbares Ergebnis, bestandene Tests und bestandenes Browserergebnis. Verwende eine monotone Uhr für Laufzeiten und UTC für Zeitstempel. Dokumentiere Rechner, Modell, Agentenanzahl, Commit, Prompt-Version, warme/kalte Abhängigkeiten und Wartezeiten auf Menschen oder APIs.

Die Live-Variante gilt erst als vorführbereit, wenn alle drei Wiederholungen vom gleichen Startstand binnen 12 Minuten die vorgeschriebenen Tests und den Browserflow bestehen. Dokumentiere alle Versuche, auch Fehlschläge. Eine einzige schnelle Generierung ist keine belastbare Laufzeit. Falls das Ziel nicht erreicht wird, weiter reduzieren oder nur den fertigen Stand zeigen. Niemals Tests auslassen, um die Zeit einzuhalten.

Planungswerte vor dem ersten vollständigen Lauf: 1 bis 2 Stunden für die erste Demo-Ansicht. Für den inzwischen um Settings und Analysen erweiterten Prototyp etwa 12 bis 24 Arbeitsstunden. Das sind Schätzungen. Multi-Agent-Arbeit verkürzt nicht automatisch den kritischen Weg über Design, Integration und Prüfung. Der begrenzte Live-Auftrag bleibt bei 10 bis 15 Minuten.

## 3. Nutzerabläufe und UI-Zustände

### Dashboard

Die Anwendung hat drei echte Routen: `/` für den Plan, `/analytics` für Analysen und `/settings` für Einstellungen. Kopfbereich: "Cashflow Lab", Navigation zu Plan/Analysen, Settings-Zahnrad, Umschalter Demo/Eigene Daten, Theme-Icon und "Demo-Daten laden". Der Theme-Wechsel zeigt ausschliesslich ein Sonnen-/Mond-Icon, keine sichtbaren Wörter "Light" oder "Dark". Tooltip und zugänglicher Name benennen die Zielaktion, etwa "Dunkle Darstellung aktivieren". Keine Navigation ohne funktionierendes Ziel.

Im Dark Theme bleiben sämtliche Texte und Icons hell auf dunklem Grund, einschliesslich Platzhalter, deaktivierter Elemente und SVG-Pfade. Farben nicht ungeprüft über `currentColor` erben. Kontrast gegen den ungünstigsten Bereich des dunkelgrauen Verlaufs prüfen. Blaue Aktionsflächen erhalten eine jeweils gut lesbare Beschriftung.

Rechts befindet sich ein einklappbarer Dokumentbereich für Uploads, Rechnungen und den jeweiligen Importstatus. Im geöffneten Zustand bleibt der Plan nutzbar; geschlossen gewinnt er die Breite zurück. Ein sichtbares Dokument-/Panel-Icon öffnet den Bereich erneut. Eingeklappte Entwürfe bleiben erhalten, ein Statuspunkt zeigt laufende oder prüfbedürftige Imports. Auf schmalen Displays öffnet sich der Bereich als zugänglicher Drawer mit Fokusführung und Schliessen per Escape.

Planparameter: Firmenname des eigenen Plans, Anfangsbestand in CHF und Planbeginn. Planbeginn ist ein Montag; bei einer anderen Auswahl den folgenden oder vorherigen Montag nicht stillschweigend verwenden, sondern den Nutzer einen Montag wählen lassen. Demo-Zeitraum bleibt unabhängig vom heutigen Datum fest.

Drei Kennzahlen zeigen den aktuellen Szenario-Endsaldo, den niedrigsten Wochenschlussbestand und den Beginn der ersten negativen Woche. Bei keinem Engpass: "Keine negative Woche". Saldo null ist nicht negativ. Zusätzlich die Warnung: "Wochensalden können Engpässe innerhalb einer Woche verdecken."

Diagramm mit Basisplan, Szenario, Legende, CHF-Achse, Wochen und sichtbarer Nulllinie. Unterschiedliche Linienarten und Beschriftungen ergänzen Farben. Darunter eine jederzeit zugängliche Tabelle derselben sechs Zahlenpaare.

Rechnungsliste: Gegenpartei, offener Betrag, Fälligkeit, erwarteter Eingang, Quelle und "+14 Tage". Ausgabenliste: Bezeichnung/Gegenpartei, offener Betrag, erwarteter Abgang. Manuelle Einträge hinzufügen, bearbeiten und als bezahlt oder ausgeschlossen markieren. Bezahlt/ausgeschlossen zählt nicht in zukünftigen Bewegungen; dadurch wird der eingegebene Anfangsbestand nicht automatisch verändert.

"Szenario zurücksetzen" entfernt nur Szenario-Änderungen. Es löscht keine Daten, lädt keine Demo nach und verändert keine importierten Basiswerte. Basisänderungen sind über "Plan bearbeiten" separat erkennbar. Eine Basisänderung entfernt die veraltete Szenario-Änderung derselben Zeile; andere Zeilen bleiben unverändert.

Der Demo-Button wechselt in einen isolierten Demo-Plan. Er überschreibt nie eigene Daten. Wiederholtes Laden stellt ausschliesslich die Demo auf ihren definierten Ausgangsstand zurück. Im Demo-Modus erscheint dauerhaft "Fiktive Demo-Daten". Ein neuer eigener Plan startet leer, nicht mit Demo-Kunden.

### Import

1. Das Dokument-Icon öffnet den rechten Bereich mit Dateiablage oder Textfeld. Zeige erlaubte Formate und Grenzen vor der Auswahl. Drag-and-drop und ein zugänglicher Button "Dateien auswählen" lösen denselben Ablauf aus.
2. Datei lokal speichern und lesbaren Text gewinnen. Zeige Dateiname, Seitenzahl, Verarbeitungszustand und Fehler. Kein Netzwerkabruf aus eingebetteten Links oder E-Mail-HTML.
3. Vor "Mit KI auslesen" zeigen, dass der angezeigte Belegtext an TypeSafe gesendet wird. Der Nutzer kann abbrechen oder Werte manuell erfassen. Nur der ausgewählte Beleg und nötiger Kontext werden gesendet, kein Postfach und keine anderen Projektdateien.
4. Jev liefert Vorschläge. Quellenansicht und Formular nebeneinander; auf kleinen Displays nacheinander. Die Quelle ist PDF-Seite oder Textausschnitt, nicht eine frei erfundene Erklärung.
5. Nutzer prüft Ein-/Ausgang, Gegenpartei, offenen Betrag, Originalwährung, gegebenenfalls bestätigte CHF-Umrechnung, Rechnungsnummer, Fälligkeit und erwarteten Zahlungstermin. Fehlende oder widersprüchliche Pflichtwerte verhindern die Übernahme.
6. Nach "In Plan übernehmen" entsteht genau ein Eintrag pro bestätigter Rechnung. Der Plan, seine Tabelle und Kennzahlen aktualisieren sich. Quelle bleibt am Eintrag erreichbar. Doppelklick und Wiederholung dürfen keine zweite Buchung erzeugen.

Ein leerer Plan fordert Anfangsbestand und Planbeginn an. Der Anfangsbestand wird nicht aus Rechnungen abgeleitet. Ein Importdatum vor Planbeginn erscheint als "Termin vor Planbeginn; Zahlungsdatum prüfen" und verlangt einen bewussten erwarteten Termin. Ein Datum nach dem Horizont bleibt gespeichert und sichtbar als "Ausserhalb des Plans".

Pflichtzustände im Design und in der App: leer, lädt, Text wird gelesen, OCR läuft, KI wird geprüft, Vorschau vollständig, Angaben fehlen, widersprüchlicher Wert, Duplikat, API nicht erreichbar, Schlüssel fehlt, ungültiges Format, Datei zu gross, Übernahme erfolgreich. Fehler erhalten einen konkreten nächsten Schritt.

### Settings

Firmenname verpflichtend für den eigenen Plan; optionale Strasse, PLZ, Ort, Land und Kontakt-E-Mail. Die Firmenidentität dient der Unterscheidung eigener Ausgangsrechnungen von Eingangsrechnungen. Nur tatsächlich eingetragene Namen/Aliase verwenden; eine Änderung darf vorhandene Einträge nicht automatisch umklassifizieren. Demo-Firma bleibt unabhängig. Basiswährung CHF ist sichtbar und in Version 1 fest.

Jev-Bereich: Status "Nicht eingerichtet", "Eingerichtet", "Verbindung geprüft" oder konkreter Fehler; Feld für neuen API-Key; stabiles Modell; "Speichern" und "Verbindung prüfen". Das Eingabefeld zeigt nie den gespeicherten Schlüssel zurück. Ein leer gelassenes Feld bewahrt ihn. Kein Ein-/Ausblenden des vorhandenen Schlüssels; nur einen neu eingegebenen Wert kann der Nutzer bei Bedarf lokal sichtbar machen. Keine Schlüssel in URLs, Analytics oder Fehlermeldungen.

Schlüssel serverseitig aus einer ausdrücklich bereitgestellten Umgebung initialisieren. Für Änderungen aus der Settings-Seite einen eigenen ignorierten Secret-Store unter dem geschützten Datenverzeichnis verwenden, mit Dateirechten 0600 und atomarem Ersetzen. Der gespeicherte Override hat Vorrang vor der Umgebung. Das ist lokaler Einzelbenutzerbetrieb, keine Behauptung verschlüsselter Cloud-Speicherung. Der Server gibt nur Vorhandensein und Prüfergebnis zurück. Keine Secrets in der gewöhnlichen Settings-Tabelle oder im Browser-Storage.

"Verbindung prüfen" prüft den gerade eingegebenen oder gespeicherten Zugang serverseitig anhand der Modellliste und einer kleinen synthetischen Anfrage. Testen speichert einen neuen Schlüssel noch nicht. Erst erfolgreicher Speichervorgang meldet "Gespeichert". Ein fehlgeschlagener Ersatzversuch überschreibt keinen funktionierenden gespeicherten Zugang. Prüfstatus enthält Zeitpunkt und Modell; ein geänderter Key oder ein anderes Modell macht den alten Status ungültig. Fehler ohne Secret-Inhalt anzeigen.

### Analysen

Alle Ansichten verwenden denselben ausgewählten Plan, dieselben sechs Wochen und denselben Basis-/Szenario-Schalter. Demo und eigene Daten bleiben getrennt. Unbestätigte Importvorschläge fliessen in keine Summe ein. Diagrammwerte sind auch tabellarisch lesbar.

- **Verlauf/Forecast:** Wochenschlussbestände und Ein-/Auszahlungen über die Zeit, Nulllinie, Minimum und erste negative Woche. Das ist eine Projektion bestätigter geplanter Zahlungen. Keine erfundenen historischen Kontobewegungen, KI-Zahlungswahrscheinlichkeiten oder nicht belegten Konfidenzbänder.
- **Volumen:** Summe und Anzahl der geplanten Einträge je Woche, getrennt nach Einnahmen/Ausgaben. Für den Demo-Basisplan vier Eingänge mit CHF 33'000, sechs Ausgänge mit CHF 41'000 und Veränderung CHF -8'000. Der Anfangsbestand CHF 10'000 ist kein Umsatz. Verschieben ändert Wochenzuordnung, nicht den Gesamtbetrag, solange der Eintrag im Horizont bleibt.
- **Kostenkategorien:** Ausgaben innerhalb des gewählten Horizonts nach bestätigter Kategorie, Anzahl, CHF-Betrag und Anteil. Summe aller Kategorien einschliesslich "Nicht zugeordnet" muss exakt den geplanten Ausgaben entsprechen. Bei Summe null keine Division durch null; "Noch keine Ausgaben" anzeigen. Klick auf eine Kategorie filtert die zugehörigen Einträge.
- **Rechnungsprüfung:** Liste je Beleg mit Extraktionsstatus, vorgeschlagener/bestätigter Kategorie, fehlenden oder widersprüchlichen Feldern und Nutzerbestätigung. Öffnen zeigt die originalen Feldbelege und erlaubt Korrektur. "Übernommen" bedeutet vom Nutzer bestätigt, nicht von Jev als echt, bezahlt oder kreditwürdig zertifiziert.

Kostenkategorien in Version 1: Personal, Externe Leistungen, Büro, Software, Marketing, Steuern/Gebühren, Sonstiges und Nicht zugeordnet. Jev schlägt per begrenzter Choice eine Kategorie aus Beleginhalt vor, inklusive "Nicht zugeordnet". Der Nutzer bestätigt oder ändert. Kategorie ist getrennt von Richtung und Betrag. Manuelle Kategorien werden bei erneuter Analyse nicht überschrieben.

Der feste Demo-Datensatz verteilt CHF 41'000 auf Personal CHF 15'000, Externe Leistungen CHF 10'000, Büro CHF 6'000, Software CHF 5'000 und Marketing CHF 5'000. Diese Zuordnungen sind ausdrücklich synthetisch und liegen in der Fixture, nicht als fest verdrahtete Diagrammwerte im UI.

## 4. Datenmodell und Rechenregeln

Geld als ganze Rappen, niemals Gleitkomma-Franken. Zulässiger offener Betrag: 1 bis 99'999'999'999 Rappen. Anfangsbestand darf negativ oder null sein, Betrag absolut höchstens dieselbe Grenze. Validierung serverseitig; Änderungen dürfen den letzten gültigen Zustand bei Fehlern nicht zerstören.

Kalenderdaten im Format `YYYY-MM-DD`, ohne Uhrzeit. Audit-Zeitstempel dagegen UTC mit Zeitzone. Wochen sind Montag inklusive bis nächster Montag exklusive, sechs Wochen sind 42 Tage. Sommerzeit und Browserzeitzone dürfen keinen Beleg verschieben.

Minimaler gemeinsamer Vertrag, vor paralleler Implementierung in TypeScript/Zod festschreiben:

```typescript
type Plan = {
  id: string;
  kind: 'demo' | 'personal';
  name: string;
  organizationLabel: string;
  startDate: string;
  openingBalanceCents: number;
  revision: number;
};
type Entry = {
  id: string;
  planId: string;
  direction: 'in' | 'out';
  label: string;
  counterparty: string;
  invoiceNumber: string | null;
  amountCents: number; // Outstanding amount, strictly positive.
  currency: 'CHF';
  dueDate: string | null; // Required for an imported invoice.
  expectedPaymentDate: string;
  status: 'planned' | 'paid' | 'excluded';
  sourceKind: 'demo' | 'manual' | 'import';
  costCategory: 'personnel' | 'external' | 'office' | 'software'
    | 'marketing' | 'tax_fees' | 'other' | 'uncategorized' | null;
  revision: number;
};
type ScenarioOverride = {
  entryId: string;
  expectedPaymentDate: string;
  baseEntryRevision: number;
};
```

Persistiere ausserdem Quelldokumente, Importentwürfe und Eintrag-Quelle-Verknüpfungen. Quelldokument: ID, Plan-ID, Typ, Originalname, interner Dateipfad, SHA-256, Grösse, OCR/Text-Version und Erstellzeit. Quellenangabe je vorgeschlagenem Feld: Dokument-ID, Seite oder Textoffset, exakter Originalausschnitt, gewählter Kandidat, Prüfergebnis und spätere manuelle Änderung. Keine Absolutpfade oder Geheimnisse an den Browser liefern.

Eigene Firma in einer Settings-Struktur persistieren. Jev-Ergebnis je Entwurf speichert Status, Modell/Fragenversion, Feldprüfungen und Kategorie-Vorschlag getrennt von bestätigten Werten. Kategorien bei Eingängen sind `null`, bei Ausgängen ohne Bestätigung `uncategorized`. Eine Änderung am Quelltext oder an entscheidungsrelevanten Firmenangaben markiert das alte Modellergebnis als veraltet. Bestätigte Finanzwerte bleiben erhalten, bis der Nutzer sie selbst ändert.

Importstatus: `stored -> extracting -> awaiting_analysis -> analyzing -> review -> imported`. Von einem laufenden Schritt sind `failed` und erneuter Versuch möglich; ein Entwurf kann `rejected` werden. API-Timeout und Prozessneustart dürfen einen Import nicht dauerhaft als laufend zeigen. Ohne Warteschlange genügt ein synchroner begrenzter Auftrag; verwaiste laufende Zustände werden beim Start als unterbrochen und wiederholbar markiert.

Ein Eintrag wird erst nach bestätigter Vorschau innerhalb einer Datenbanktransaktion angelegt. Die Import-ID hat eine eindeutige Zuordnung zur übernommenen Rechnung. Eine E-Mail und ihr PDF dürfen auf denselben Eintrag verweisen. Quelle und Entwurf sind keine zusätzlichen Geldbewegungen.

Für jede Woche: `closing = opening + sum(in) - sum(out)`. Die nächste Woche beginnt mit dem vorherigen Schlussbestand. Basis nutzt die gespeicherten Termine; Szenario nutzt gültige Overrides. Nicht geplante Einträge werden ignoriert. Ausserhalb liegende Einträge bleiben sichtbar, zählen aber nicht im Intervall. Zeige vor dem Plan liegende offene Einträge gesondert, ohne sie automatisch dem Anfangsbestand zuzuschlagen.

"+14 Tage" addiert 14 Kalendertage zum aktuell im Szenario erwarteten Datum. Wiederholte Klicks addieren weitere 14 Tage. Die Fälligkeit, der Betrag und der Basisplan bleiben unverändert. Nach dem Reset gibt es keine Overrides. Speichere Änderungen und zeige Speicherfehler; ein UI-Zustand ohne erfolgreiche Speicherung darf nicht als gespeichert erscheinen.

### Verbindlicher Demo-Datensatz

`fixtures/demo-plan.json` ist die Eingabe, `fixtures/expected-demo.json` das unabhängige Soll. Start 9. November 2026, Anfangsbestand CHF 10'000. Fiktive Zahlungseingänge: CHF 4'000 am 11. November, CHF 14'000 am 18. November, CHF 6'000 am 25. November und CHF 9'000 am 9. Dezember. Die sechs Montagsausgaben betragen CHF 7'000, 8'000, 10'000, 6'000, 5'000 und 5'000.

| Woche ab | Basis CHF | Nach Verschiebung CHF |
| --- | ---: | ---: |
| 09.11.2026 | 7'000 | 7'000 |
| 16.11.2026 | 13'000 | -1'000 |
| 23.11.2026 | 9'000 | -5'000 |
| 30.11.2026 | 3'000 | 3'000 |
| 07.12.2026 | 7'000 | 7'000 |
| 14.12.2026 | 2'000 | 2'000 |

Verschobener Eintrag: `income-02`, CHF 14'000, 18. November auf 2. Dezember. Szenario-Minimum CHF -5'000, erste negative Woche 16. November, Endsaldo CHF 2'000. Basis-Minimum CHF 2'000, keine negative Woche. Das Minimum umfasst die sechs Schlussbestände; der Anfangsbestand ist eine separate Information.

## 5. PDF, E-Mail und Jev

### Eingangsgrenzen

- Pro Auswahl höchstens fünf Dateien; je Datei höchstens 10 MiB, zusammen höchstens 25 MiB. Nach MIME-Decodierung gelten dieselben Grenzen für Anhänge, zusammen höchstens zehn Anhänge.
- PDF höchstens zehn Seiten. Gedruckte Rechnungen auf Deutsch oder Englisch, mit Textschicht oder lesbarem Scan. Passwortgeschützte, beschädigte, handschriftliche oder nicht lesbare Dateien erhalten eine klare Meldung. Nicht schweigend nur die ersten Seiten verarbeiten.
- `.eml`: MIME korrekt decodieren, Klartext bevorzugen, HTML als bereinigten Text verarbeiten, PDF-Anhänge einzeln darstellen. Kein `.msg`-Versprechen, kein Laden von Trackingbildern und keine Ausführung von HTML.
- Ein Dokument entspricht im ersten Umfang einer Rechnung. Enthält es mehrere Rechnungen, Übernahme sperren und zum Aufteilen auffordern. Mehrere PDF-Anhänge dürfen jeweils separate Rechnungen ergeben. E-Mail-Text ergänzt den zugehörigen Beleg und erzeugt nicht automatisch einen zweiten Eintrag.
- Eingefügter Text höchstens 40.000 Zeichen. Bei Dokumenttext oberhalb des geprüften API-Budgets sichtbar begrenzen oder blockieren; niemals abgeschnittenen Text als vollständig geprüft ausgeben.

### Verarbeitung

1. Dateityp anhand des Inhalts prüfen, zufälligen internen Dateinamen verwenden, Pfadgrenzen und Ressourcenlimits durchsetzen.
2. PDF-Text seitenweise lokal extrahieren. Für Seiten ohne brauchbaren Text lokalen OCR-Weg für Deutsch/Englisch einsetzen. OCR-Pakete und Sprachdaten werden vor dem Vortrag installiert und gepinnt. Jev ersetzt keinen allgemeinen OCR-Parser.
3. Kandidaten für Beträge, Währungen, Termine, Rechnungsnummer und Gegenpartei mit Quellenposition erfassen. Schweizer Schreibweisen wie `14'000.50`, `14’000.50` und `14 000,50` berücksichtigen. Mehrdeutige Zahlen nicht raten.
4. Jev entscheidet in eng begrenzten Fragen, welcher belegte Kandidat das offene Rechnungstotal, Rechnungsdatum oder Fälligkeitsdatum bezeichnet und ob es sich um eine Rechnung handelt. Jede Auswahl enthält "Kein passender Wert". Gegenpartei ist ein ausgewählter Originaltext, kein generierter Firmenname.
5. Ein-/Ausgang relativ zur eingetragenen eigenen Firma vorschlagen. E-Mail-Empfang allein beweist keine Ausgabe. Ist die Rolle unklar, Nutzerwahl verlangen.
6. Code kopiert die ausgewählten Originalwerte und normalisiert sie. Kalenderberechnungen wie "30 Tage ab Rechnungsdatum" erfolgen nur bei eindeutiger Ausgangsangabe; Ableitung sichtbar machen. Fehlende Fälligkeit bleibt leer.
7. Der erwartete Zahlungstermin ist eine Annahme des Nutzers. Fälligkeit kann als sichtbarer Vorschlag übernommen werden, aber nie als bewiesener Zahlungseingang. Bei Teilzahlung muss der offene Betrag bestätigt werden; weder ursprüngliches Total noch ein bereits bezahlter Betrag darf ungeprüft zählen.
8. Nutzer prüft und bestätigt jede Rechnung. Es gibt in Version 1 keine automatische Buchung anhand eines KI-Scores.

Ein gültiges JSON beweist keine korrekte Extraktion. Prüfe Kandidatenabdeckung und Fundstelle zusätzlich. Speichere Modell-ID, Zeitpunkt, Fragenversion und Antwortmetadaten ohne Schlüssel. Nutzungsdaten dienen der Messung; keine vollständigen Belegtexte in Standardlogs.

### Konkreter TypeSafe-Vertrag

Ein serverseitiger Adapter kapselt TypeSafe. Verwende die aktuelle dokumentierte API oder das offizielle SDK. Vor Implementierung API- und SDK-Dokumentation lesen; Modell über die echte Modellliste prüfen und einen konkreten stabilen Namen in `TYPESAFE_MODEL` festhalten. Kein unbemerktes Wechseln auf Preview oder einen anderen Anbieter.

Konfiguration aus `.env.local` oder Prozessumgebung gemäss `.env.example`. Ein bereits bereitgestellter Schlüssel darf unter einem anderen bekannten Variablennamen liegen; nur nach Bestätigung der Zuordnung im Serveradapter verwenden. Falls keine Konfiguration im Projekt oder ein ausdrücklich genannter Secret-Pfad vorliegt, nach dem Pfad fragen. Keine ungezielte Suche nach Geheimnissen auf dem Rechner.

Unabhängige Fragen über denselben Text in einem Aufruf bündeln. Antworten gegeneinander prüfen, bevor daraus ein Vorschlag entsteht. Fehlende Confidence gilt als unbekannt; keine erfundene Sicherheit. Bis zur Auswertung der Fixtures bleibt jeder Vorschlag manuell zu bestätigen. Schwellenwerte niemals als Garantie behandeln.

TypeSafe-Timeout 30 Sekunden, höchstens ein Retry bei vorübergehendem Netzwerkfehler oder 429/5xx, sofern das Gesamtbudget reicht. 401/403 nicht automatisch wiederholen. Textgewinnung höchstens 60 Sekunden pro Dokument, Gesamtanalyse höchstens 90 Sekunden; Timeout liefert wiederholbaren Fehler mit erhaltenem Entwurf. Abbrechen verhindert eine spätere automatische Übernahme.

Bei fehlendem Schlüssel/API-Ausfall funktionieren Demo und Berechnung weiter. Importdaten bleiben als manuell bearbeitbarer Entwurf erhalten, klar mit "KI-Auslesen nicht verfügbar". Dieser Fallback erfüllt nicht den verlangten Live-API-Nachweis für die Gesamt-Abnahme.

### Duplikate und Widersprüche

Identische Datei per SHA-256 innerhalb desselben Plans wiedererkennen, unabhängig vom Dateinamen. Vor einer zweiten Übernahme denselben Import/Eintrag öffnen. Zusätzliche Prüfung anhand normalisierter Gegenpartei, Rechnungsnummer, Richtung, Währung und Betrag. Bei abweichendem Betrag zur gleichen Rechnungsnummer einen Konflikt anzeigen, nicht neue Einnahmen erzeugen.

Bei Dokumenten ohne Rechnungsnummer einen ähnlichen vorhandenen Beleg als möglichen Doppelimport anzeigen. Der Nutzer kann nach Sichtprüfung bewusst einen eigenständigen Beleg bestätigen; diese Entscheidung festhalten. Gleiche E-Mail mit eingebettetem und angehängtem Rechnungstext führt nicht zu einer Doppelzählung. Jev darf keine vorhandenen Einträge selbständig löschen oder überschreiben.

## 6. Technische Umsetzung

Für GitVM gilt zusätzlich `docs/gitvm-run.md`: vorgebautes Werkzeug-Template, getrennte `blank`-/`ready`-Pakete, gemessener vollständiger Ablauf und unveränderte Ersatzversion. Die erste GitVM-Vorbereitung ersetzt keine Live-Messung. Öffentlicher Studentenbetrieb benötigt das dort beschriebene zusätzliche Abnahmegate; der bestehende lokale Umfang bleibt separat prüfbar.

Neue Anwendung: Next.js App Router, React, TypeScript, Tailwind und passende vorhandene shadcn/ui-Bausteine. Drizzle mit eigener lokaler PostgreSQL-Datenbank. Server Components für Datenzugriff, Client Components für Interaktion, Server Actions für Mutationen und Route Handler für Uploads. Zod an Eingangsgrenzen. Bestehende passende Pakete wiederverwenden, Kandidaten vorab prüfen.

Vor der Versionswahl den `release-check`-Skill lesen, offizielle stabile und unterstützte Versionen prüfen und die getestete Kombination exakt festhalten. Keine pauschalen Versionszahlen aus alten KB-Seiten übernehmen. Bei einem unlösbaren Kompatibilitätskonflikt Entscheidung einholen. Lockfile und Runtime-Version gehören ins Repository.

Lokaler Einzelbenutzerbetrieb auf `127.0.0.1`. Eine eigene Datenbank bzw. ein eigener Container mit Loopback-Port und eigenem Volume; keine fremden Datenbanken, keine globalen Service-Neustarts. Passende lokale Runtime zuerst prüfen. Falls sie fehlt, den konkreten Installationsbedarf melden; kein bestehendes Produkt umkonfigurieren.

Die lokale Anwendung ist kein Mehrbenutzer-SaaS. Öffnen auf LAN/Tailscale/Internet ist ein separater Schritt mit Stack Auth, serverseitiger Autorisierung und frischem Release-Check. Auch lokal mutierende Requests gegen fremde Origins schützen. Keine CORS-Freigabe für beliebige Seiten, kein Dateizugriff anhand frei übergebener Pfade.

Uploads ausserhalb von `public/` und Git speichern; Zugriff über geprüfte IDs. Eigener Datenordner mit eingeschränkten Dateirechten. Datenbank speichert Metadaten/Beziehungen, keine grossen Binärdateien. Abgebrochene Uploads und temporäre OCR-Dateien im selben Vorgang entfernen. Ein verwaistes Original ohne DB-Verweis darf nicht als bestätigter Beleg erscheinen.

Alle Beziehungen über Fremdschlüssel, Mutationen transaktional, `revision` gegen veraltete parallele Schreibzugriffe prüfen. Import-ID eindeutig, Wiederholung idempotent. Szenarien gehören zum Plan. Theme lokal speichern; Light/Dark bieten dieselben Funktionen und berücksichtigen Tastaturfokus sowie ausreichenden Kontrast.

Kein zusätzlicher Worker, Redis, Vektorspeicher oder Chat nötig. Die begrenzten Imports laufen zunächst kontrolliert im lokalen Serverprozess. Produktdaten, Rechenfunktion, Importservice und TypeSafe-Adapter bleiben getrennte Module, ohne ein allgemeines Framework zu bauen.

Verbindliche Service-Operationen: `loadPlan`, `loadDemo`, `savePlanSettings`, `saveEntry`, `setScenarioDate`, `resetScenario`, `prepareImport`, `analyzeImport`, `confirmImport`, `rejectImport`, `loadAnalytics`, `loadSettings`, `saveCompanySettings`, `testJevConnection`, `saveJevConfiguration`. Rückgaben enthalten Erfolg mit aktuellen Revisionen oder typisierte Validierungs-/Konflikt-/Servicefehler. UI und Tests nutzen dieselben Verträge. Kein Erfolg nur deshalb, weil ein HTTP-Request gesendet wurde.

## 7. Gates und Agentenaufteilung

Gates sind Arbeitsnachweise, keine zusätzlichen menschlichen Genehmigungsrunden. Nach einem bestandenen Gate selbständig fortfahren.

### G0: Voraussetzungen und Verträge

Repository und Regeln lesen, vorhandene Änderungen schützen. Tatsächliche Paper-Tools/Datei, TypeSafe-Zugang mit synthetischem Beispiel, Runtime, Browserwerkzeug, freie feste Ports und eigene Datenbank prüfen. Ein GET auf eine MCP-URL allein ist kein MCP-Nachweis. Findings nach `docs/preflight-run.md`; Abhängigkeiten nach `docs/versions.md`.

Data-/Import-Verträge sowie Fixtures vor parallelem Coding festschreiben. Die Startkonfiguration muss ohne Secrets im Repo dokumentiert sein. Fehlende externe Voraussetzungen konkret melden und unabhängige Arbeiten fortsetzen. Ohne erfolgreichen API-Aufruf bleibt dessen Gate offen.

### G1: Fertiges Paper-Design prüfen

Den vorhandenen Entwurf in Cash-Lab-Demo-01 über MCP lesen. Erstelle keine zweite Variante, wenn der geprüfte Master bereits existiert. Lies Tokens, Struktur und exportierbare Styles; Screenshots dienen der Sichtprüfung. Prüfe die Pflichtzustände aus Abschnitt 3, beide Themes und eine schmale Ansicht.

Der Reviewer ordnet jede Anforderung P01 bis P11 einer sichtbaren UI-Stelle oder einem dokumentierten Verhalten zu. Er prüft Zahlen, Quellenansicht, Datumsunterscheidung, Demo-Trennung, Fehlermeldungen, Kontrast, Tastaturreihenfolge und responsive Anordnung auf Plan, Settings und Analysen. Dokumentiere fehlende Zustände und korrigiere sie vor UI-Implementierung. Ein Coding-/Vision-Modell prüft das Design; Jev ist hier nicht pauschal der visuelle Reviewer.

Ergebnis: `design/manifest.json`, Screenshots, genaue JSX-/Style-Exporte und `design/review.md` mit PASS/FAIL je Anforderung. Design-PASS bedeutet keine Funktionsabnahme.

### G2: Fachlogik und Speicherung

Rechenfunktion zuerst gegen beide Sollreihen testen. Schema und Migration auf eigener Scratch-Datenbank anwenden. Demo-Trennung, Szenariopersistenz, Revisionen und Importzustände prüfen. Start/Stop, Seed und Tests müssen reproduzierbar sein; Seed kann keine fremden Daten löschen.

### G3: Import und Oberfläche

Extraktion/OCR, MIME/Text, TypeSafe-Adapter, Quellenanzeige und Bestätigung vollständig implementieren. Oberfläche nach dem geprüften Design bauen. Alle sichtbaren Aktionen verbinden. Ein fertiger Screen ohne echten Import wird nicht als fertig gemeldet.

### G4: Integration und Fehlerkorrektur

Alle Abnahmekriterien aus Abschnitt 8 ausführen, insbesondere echte API und echte Browseraktionen. Konsolenfehler prüfen, Speicherzustand nach Reload und Serverneustart lesen. Findings beheben und betroffene Checks wiederholen. Screenshots nur mit synthetischen Daten ablegen. Exakte Befehle, Ergebnisse und Artefakt-IDs nach `docs/acceptance.md`.

### G5: Vortragsstand und Zeitprobe

Vollständigen lokalen Stand committen. Daraus separat `demo/ready` und `demo/start` erstellen. Der Startstand hat alle geprüften Funktionen ausser der bewusst begrenzten Live-Änderung; der betreffende Button ist sichtbar als noch zu ergänzen gekennzeichnet. Keine unbeabsichtigt kaputte Navigation. Der Integrator dokumentiert exakt, welche Dateien/Diffs die beiden Stände unterscheiden.

Start- und Ersatzstand in getrennten Worktrees halten. Ersatzstand bleibt während der Live-Arbeit unverändert. Feste getrennte Ports und eine eigene synthetische Demo-Datenbasis verhindern gegenseitiges Überschreiben. Keine Branches oder Daten löschen, um einen Test zurückzusetzen.

Drei Zeitproben durchführen und `docs/live-run.md` mit den gemessenen Zeiten, Startkommando, Prompt und Ersatzwechsel schreiben. Ports, Datenbanken und Config pro Stand fest dokumentieren. Ein 60- bis 90-sekündiger Ersatzfilm mit Demo-Daten kann ergänzt werden; er ersetzt keine zuvor bestandene Prüfung.

### Single-Agent oder Multi-Agent

Ein Agent führt dieselben Gates nacheinander aus. Bei ausdrücklich gestartetem Multi-Agent-Lauf:

- Integrator besitzt Architektur, Verträge, Migrationen, Runtime und endgültige Integration.
- Designer besitzt nur `design/` und die benannte Paper-Datei. Er greift keine Vortragsfolien an.
- Import-Entwickler besitzt Importservice, OCR/MIME, TypeSafe-Adapter und deren Tests.
- UI-Entwickler besitzt UI-Komponenten und Theme. Er startet nach G1 und nutzt die vereinbarten Verträge.
- Reviewer prüft das integrierte Ergebnis. Er zählt Teilberichte nicht als End-to-End-Pass.

Bei begrenzten Slots laufen Rollen nacheinander. Keine zwei Agenten ändern dieselben Dateien gleichzeitig. Handovers nennen Commit, Dateien, durchgeführte Checks und offene Abhängigkeiten. Gemeinsame Vertragsänderungen gehen über den Integrator. Die Verantwortung für Fertigstellung bleibt bei ihm.

## 8. Verbindliche Abnahme

Alle folgenden Checks sind Pflicht. Im Prüfbericht pro ID: PASS/FAIL/NOT RUN, Datum, Befehl oder Browseraktion und Belegpfad. Kein PASS aus blossen Screenshots oder Mock-Antworten ableiten.

| ID | Zu prüfendes Verhalten |
| --- | --- |
| A01 | Demo laden erzeugt exakt die sechs Basiswerte und Basis-Kennzahlen der Fixture. |
| A02 | +14 Tage auf income-02 ergibt exakt die Szenarioreihe, Minimum und erste negative Woche. Fälligkeit, Betrag und Basis bleiben erhalten. |
| A03 | Zweiter Klick addiert weitere 14 Tage. Reset entfernt nur Overrides. Reload und Serverneustart erhalten den gespeicherten Zustand. |
| A04 | Sonntag/Montag, erster Tag und Tag 42, Jahreswechsel, Schaltjahr, Rappen und negative Anfangsbestände korrekt. Nullsaldo ist kein Engpass. |
| A05 | Betrag/Datum ungültig, leeres Pflichtfeld und Überlauf werden serverseitig abgewiesen; gültiger Zustand bleibt erhalten. |
| A06 | Eigene Daten bleiben nach Demo-Laden und Demo-Reset unverändert. Leerer eigener Plan bleibt frei von Demo-Firmen. |
| A07 | Echte synthetische Text-PDF wird im Browser hochgeladen, belegt erkannt, korrigiert, bestätigt und korrekt genau einmal verrechnet. |
| A08 | Dasselbe für einen lesbaren Scan ohne Textschicht, mit real ausgeführtem OCR und Seitenbeleg. |
| A09 | `.eml` mit MIME/UTF-8 und zwei PDF-Anhängen liefert zwei getrennte Vorschauen. Wiederholter Rechnungsinhalt im Body wird nicht doppelt gebucht. |
| A10 | Eingefügter E-Mail-Text folgt demselben Review-/Bestätigungsweg und verändert vor Bestätigung keinen Saldo. |
| A11 | Netto/MwSt/Brutto, mehrere Beträge und mehrere Datumsangaben: korrekter offener Gesamtbetrag/Fälligkeit, kein blindes erstes Regex-Ergebnis. |
| A12 | Fehlende Fälligkeit, unklare Gegenpartei/Richtung oder Teilzahlung verlangt Korrektur. Keine erfundenen Werte oder Zahlungszusagen. |
| A13 | Identische Datei unter anderem Namen, E-Mail plus Anhang und Doppelklick auf Übernehmen erzeugen keine Doppelzählung. |
| A14 | Gleiche Rechnungsnummer mit abweichendem Betrag zeigt Konflikt; gleich hoher unabhängiger Beleg wird nicht pauschal verworfen. |
| A15 | Nicht-CHF, Gutschrift, bezahlter Beleg, mehrere Rechnungen pro PDF, beschädigtes/verschlüsseltes PDF und Grössenlimits werden verständlich behandelt. |
| A16 | Fehlender/falscher Schlüssel, Timeout, 429/5xx und Abbruch haben sichtbare Zustände; kein Dummy-Erfolg, keine automatische Übernahme. |
| A17 | Neustart während Analyse lässt einen wiederholbaren Entwurf zurück. Bestätigter Import bleibt dauerhaft mit Originalquelle verbunden. |
| A18 | Belegtext mit Anweisungen kann keine Tools, URLs oder Datenänderungen auslösen. E-Mail-HTML lädt keine externen Bilder/Skripte. |
| A19 | Importdaten vor/nach Horizont, bezahlte/ausgeschlossene Einträge und Änderungen der Basis haben die spezifizierte Wirkung. |
| A20 | Light und Dark: vollständiger Hauptflow bei 1440x900 und 1280x720; schmale Ansicht bei 390 px ohne abgeschnittene Aktionen. Theme-Icon ohne sichtbare Light/Dark-Wörter, dunkelgrauer Verlauf, rechter Dokumentbereich öffnet/schliesst ohne Datenverlust. |
| A21 | Tastatur, sichtbarer Fokus, Formularlabels, Kontrast, Fehlerzuordnung und lesbare Wochentabelle; keine reine Farbcodierung. |
| A22 | Browserkonsole ohne neue App-Fehler. Alle sichtbaren Buttons/Links funktionieren. Quellenansicht öffnet nur die zugehörige Datei. |
| A23 | Kein API-Schlüssel in Git, Client-Bundle, Netzwerkantworten oder Logs. Fremder Origin und unerlaubte Dateipfade werden zurückgewiesen. |
| A24 | Frischer Installations-/Migrations-/Startlauf aus README klappt. Tests räumen ausschliesslich eigene synthetische Daten im selben Prozess auf. |
| A25 | Live-Jev-Aufruf mit synthetischem Beleg erfolgt tatsächlich; dokumentierte Modell-ID, Ergebnis und Latenz. Servicefehler separat mit Stubs testbar. |
| A26 | Mindestens zwölf beschriftete synthetische Belegfälle, darunter A07 bis A15, gegen die echte Extraktionskette auswerten. Falsche Vorschläge und manuelle Korrekturen zählen und offen ausweisen. |
| A27 | Paper-Design stimmt mit der umgesetzten UI überein; Abweichungen sind begründet und beide Themes geprüft. |
| A28 | Drei Live-Wiederholungen erfüllen die Zeit- und Qualitätsbedingungen; Ersatzwechsel wird ebenfalls einmal tatsächlich ausgeführt. |
| A29 | Settings: Firmendaten speichern, neu laden und zur Rechnungserkennung verwenden; Demo-Firma unverändert. Alle drei Routen funktionieren in beiden Themes. |
| A30 | Key neu eingeben, testen, speichern, ersetzen und App neu starten. Bestehender Key wird nie zurückgegeben; leeres Feld bewahrt ihn, fehlgeschlagener Ersatz überschreibt ihn nicht. Datei- und Origin-Schutz prüfen. |
| A31 | Analytics: Fixture ergibt CHF 33'000 Eingänge, CHF 41'000 Ausgänge, Veränderung CHF -8'000 und Endsaldo CHF 2'000. Jede Wochenzahl stimmt mit dem Plan überein. |
| A32 | Kategorien ergeben zusammen exakt CHF 41'000; unbekannt, null Ausgaben, manuelle Umklassifizierung und Filter funktionieren ohne Doppelzählung. |
| A33 | Jev-Ergebnis je Rechnung zeigt Herkunft/fehlende Felder und Modellzeitpunkt. Ändern relevanter Eingaben markiert es veraltet; bestätigte Werte werden nicht ungefragt ersetzt. |

Die Anwendung muss nicht jede denkbare Rechnung automatisch verstehen. Für die klaren Text-/Scan-Standardfälle muss die automatische Auswahl richtig sein. Mehrdeutige Fälle müssen als prüfbedürftig sichtbar sein. Eine komplett manuelle Eingabe aller Fixtures erfüllt A26 nicht. Lege erwartete Feldwerte vor den Modelltests fest und ändere sie nicht nachträglich, um eine Antwort richtig erscheinen zu lassen.

## 9. Lieferumfang und Abschluss

Liefere funktionierenden Code mit Lockfile, Migrationen, `.env.example` ohne Schlüssel, README mit echten Befehlen, Paper-Master plus Exporte, synthetische Eingabefälle, Tests, Prüfbericht und gemessenen Live-Ablauf. Schreibe `memory/brief.md`, `memory/decisions.md`, `memory/state.md` und `memory/sources.md` so, dass ein neuer Agent den Stand gegen den Code prüfen kann.

Kennzeichne Gesamtstatus getrennt als `IMPLEMENTATION_VERIFIED`, `LIVE_DEMO_READY` oder `BLOCKED`. A01 bis A27, A29 bis A33 und H01 bis H06 aus `DEMO_STORY.md` sind Voraussetzung für `IMPLEMENTATION_VERIFIED`; zusätzlich A28 für `LIVE_DEMO_READY`. Bei BLOCKED konkrete fehlende Voraussetzung, bereits geprüfte Teile und nächste Aktion nennen. Ein Buildfehler, fehlender API-Nachweis oder nicht geprüfter Import verhindert die Vollabnahme.

Lokale Commits sind erlaubt, wenn der Bauauftrag ausgeführt wird. Push, Veröffentlichung, echte Postfachverbindung und Versand benötigen die Autorisierung der ausführenden Sitzung. Vor jeder autorisierten Bereitstellung die exakte Version erneut mit `release-check` prüfen. Dieses Dokument erteilt keine pauschale Produktionsfreigabe.

## Quellen und Wiederverwendung

Das TypeSafe-Muster wählt belegte Kandidaten und normalisiert sie anschliessend im Code. Die Dokumentation ist vor Implementierung erneut auf den aktuellen API-Vertrag zu prüfen: [Werteauswahl](https://docs.typesafe.ai/cookbooks/pre_parsed_value_extraction_cookbook), [API](https://docs.typesafe.ai/api), [Extraktionsprüfung](https://docs.typesafe.ai/cookbooks/sde_cascade). Hier festgelegte Limits und Nutzerbestätigungen sind Produktentscheidungen, keine behaupteten TypeSafe-Garantien.

Paper ermöglicht Lesen und Bearbeiten der Design-Datei über MCP. Nutze die tatsächlich verfügbaren Werkzeuge: [Paper MCP](https://paper.design/docs/mcp). Der fertige Entwurf wird vor dem Vortrag geprüft und exportiert.

Prüfe verfügbare wiederverwendbare Bibliotheken anhand ihrer Quellen, Lizenz, Grenzen und Tests. Interne Komponenten-Kataloge sind keine Voraussetzung für diesen öffentlichen Bauauftrag. Dokumentiere jede tatsächliche Übernahme.
