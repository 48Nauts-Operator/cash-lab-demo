# Voraussetzungen für den neuen Lauf

Stand 6. November 2026. Dieses Repository enthält noch keine Anwendung. Ergebnisse früherer Anwendungen gelten nicht als Abnahme dieses Neubaus.

- Ziel ist `https://github.com/48Nauts-Operator/cash-lab-demo.git`, Branch `main`.
- Der vorbereitete Paper-Master und vierzehn Screenshots stehen in `design/manifest.json`. Zugriff über tatsächliche Paper-MCP-Werkzeuge auf dem ausführenden Rechner prüfen. Eine bestehende Verbindung auf einem anderen Mac wird nicht vorausgesetzt.
- Den TypeSafe/Jev-Key stellt der Betreiber separat in privater serverseitiger Konfiguration bereit. Keine Schlüssel im Repository. Präsenz prüfen, ohne den Wert auszugeben; anschliessend einen echten synthetischen Test ausführen.
- Runtime, stabile kompatible Abhängigkeiten, PostgreSQL, PDF/OCR, Browserwerkzeug und freie Ports vor Beginn des Live-Laufs vorbereiten und prüfen. Wenn diese Vorbereitung zum gemessenen Lauf gehört, darf ihre Zeit nicht abgezogen werden.
- GitVM-Template und fertiger Fallback werden separat bereitgestellt. Der separate private GitVM-Fallback läuft im geprüften Text-Demo-Profil mit gesperrten Datei-Uploads. Diese Abnahme gilt für den Fallback, nicht als vorweggenommener Erfolg des Neubaus. Öffentliche Studentenroute und direkter MacBook-Test sind noch offen. Details im GitVM-Runbook.
- E-Mail-Umfang ist `.eml` mit PDF-Anhängen oder eingefügter Text. Keine direkte Postfachverbindung voraussetzen.
- Schreib frische Ergebnisse nach `docs/preflight-run.md`, gewählte Versionen nach `docs/versions.md` und den laufenden Stand nach `memory/state.md`.

Produkt- und API-Verträge stehen in [BUILD_SPEC.md](../BUILD_SPEC.md). Aktuelle offizielle [Paper-MCP-Dokumentation](https://paper.design/docs/mcp) und [TypeSafe-API-Dokumentation](https://docs.typesafe.ai/api) vor Integration lesen.
