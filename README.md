# Cashflow Lab live build

Dieses Repository ist der Startpunkt für den Live-Bau. Es enthält den Bauauftrag, Designreferenzen und synthetische Testdaten. Die Anwendung ist noch nicht implementiert.

## Auftrag für den Agenten

> Lies AGENTS.md und START_PROMPT.md. Baue Cashflow Lab in diesem Repository gemäss BUILD_SPEC.md und DEMO_STORY.md. Nutze das vorbereitete Design und die synthetischen Fixtures. Führe echte Jev- und Browserprüfungen aus, miss den gesamten Lauf und dokumentiere Fehler sowie verbleibende Blocker. Kopiere keine fertige Anwendung aus einem anderen Repository.

## Unterlagen

- [Startprompt](START_PROMPT.md): vollständiger Ausführungsauftrag.
- [Bauspezifikation](BUILD_SPEC.md): Funktionen, Verträge und Abnahmekriterien.
- [Designvorgaben](PAPER_CLONE_BRIEF.md): Farben, Schrift, Icons, Abstände, Diagramme und vierzehn Ansichten.
- [Designreferenzen](design/README.md): Screenshots, Paper-Datei und Text-/Icon-Vorgaben.
- [Demo-Geschichte](DEMO_STORY.md): Zahlungstreue und Jev-Zahlungsnachrichten.
- [Synthetische Eingaben](fixtures/README.md): Plan, Historie, PDF-, Scan- und E-Mail-Fälle mit Sollwerten.
- [Voraussetzungen](docs/preflight.md): Zugänge und aktuelle Prüfgrenzen.
- [GitVM-Ablauf](docs/gitvm-run.md): Vorbereitung, Zeitmessung, sieben Tage Fallback-TTL und MacBook-Zugriff.

Die optionale Paper-Neukonstruktion und der vollständige App-Bau sind getrennte Messungen. Zwanzig Minuten sind ein Ziel, kein zugesagtes Ergebnis. Der separate fertige Fallback ist nicht Teil dieses Repositories.

Es gibt hier keinen Anwendungscode, keine JSX-Exporte, Installationsskripte, Dependency-Manifeste oder Zugangsdaten. `.env.local`, Datenbank und Laufzeit werden erst im autorisierten Bauauftrag eingerichtet. Das Bereitstellen dieser Unterlagen ist kein erfolgreicher App-Test oder Deployment.

## Hosted showcase and local version

Die GitVM-Vorführung ist ein Playground mit Demo-Daten und echter Jev-Analyse von eingefügtem Text. Datei-Upload ist sichtbar ausgegraut und serverseitig gesperrt. Die vollständige lokale Version enthält PDF-/OCR- und EML-Import. Beide Profile und ihre getrennten Abnahmen sind in BUILD_SPEC.md festgelegt.
