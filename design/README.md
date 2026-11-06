# Designreferenzen

Der geprüfte Master heisst Cash-Lab-Demo-01. [manifest.json](manifest.json) enthält Paper-Datei, Frame-IDs und die vierzehn Screenshots. Der Zugriff auf die Paper-Datei kann eine separate Berechtigung benötigen.

[PAPER_CLONE_BRIEF.md](../PAPER_CLONE_BRIEF.md) legt Farben, Inter-Schrift, Abstände, Icons, Diagramme und Zustände fest. [copy.json](clone-kit/copy.json) enthält die deutschen Texte und Typografie, [icons.json](clone-kit/icons.json) die Vektor-Icon-Assets. Das sind Designvorgaben, keine fertigen App-Komponenten.

Light und Dark zeigen dieselben Funktionen. Theme-Wechsel ist ein Icon; Dark verwendet dunkelgrauen Verlauf und helle Texte/Icons. Plan, Analysen, Settings, Dokumentbereich und Importprüfung gehören zum Pflichtumfang. Die neueren Lieferantenrechnungs- und FX-Anforderungen aus BUILD_SPEC.md ergänzen die ursprünglichen Screenshots und müssen in die Prüfung aufgenommen werden.

Dieses Repository enthält bewusst keine JSX-Exporte oder Generatorskripte. Die Anwendung wird während des Live-Laufs neu geschrieben. Ein optionaler Paper-Klon erhält eine neue Datei und eine eigene Zeitmessung; den Master nicht ändern.
