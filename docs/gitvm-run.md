# GitVM live-build runbook

Dieses Dokument beschreibt den vollständigen Neubau in einem vorbereiteten privaten GitVM-Gast. Es enthält keine Infrastrukturimplementierung oder Zugangsdaten. Der Betreiber stellt die tatsächlichen API-, SSH- und Template-Zugänge separat bereit.

## Vorbereitung vor der Vorführung

- Ein freigegebenes Template mit stabilen kompatiblen Werkzeugen, Browser, Text-Demo und PostgreSQL bereitstellen. Exakte Versionen, Image-/Rootfs-Hashes, Gastkernel und Scanzeit dokumentieren. Kein Anwendungscode und keine Schlüssel im Template.
- Ein Dependency-Cache ist Vorbereitung und muss exakt zu den ausgewählten Manifesten passen. Bei Abweichung neu bauen und prüfen; keine ungeprüfte Laufzeitinstallation einschleusen.
- Den GitVM-Gast tatsächlich booten und Datenbank, Produktionsstart, Neustartverhalten, Browser und synthetischen Jev-Import prüfen. Containerprüfungen allein beweisen keinen Firecracker-Betrieb.
- Einen fertigen Fallback separat betreiben. Angeforderte maximale Dashboard-TTL: **604800 Sekunden, sieben Tage**. Tatsächlich eingestellte Ablaufzeit und verfügbaren Ressourcen prüfen; niemals eine unbegrenzte Laufzeit behaupten.
- Den Fallback vom MacBook aus direkt über den GitVM-Host erreichen, beispielsweise über einen privaten SSH-Tunnel. Der Mac Studio darf weder Anwendungshost noch notwendiger Proxy sein. Diese Verbindung vor der Präsentation vom MacBook testen.

## Aktuelle Freigabegrenze

Der Betreiber hat Datei-Uploads für die GitVM-Vorführung ausdrücklich aus dem Umfang genommen. Der Demo-Gast verwendet `CASHFLOW_DEMO_TEXT_ONLY=1`, zeigt den Upload-Button ausgegraut und weist auf die lokale Version hin. Direkte Datei-Requests und gespeicherte PDF-Quellen sind serverseitig gesperrt. Demo-Daten, eingefügter Text und echte Jev-Aufrufe bleiben verfügbar. PDF-/OCR-Pakete gehören nicht in dieses Template.

Das neue Image und die Begrenzung der Eingabewege müssen geprüft werden. Die früheren PDF-Befunde gelten nicht automatisch für ein Image ohne diese Verarbeitung. Andere Befunde anhand der tatsächlichen Laufzeit prüfen und nicht pauschal ausblenden. Die Host-Ausnahme bleibt bestehen. Das überarbeitete Text-Demo-Template hat inzwischen die private native GitVM-Abnahme bestanden; ein separater privater Fallback läuft mit sieben Tagen TTL. Konkrete private Zugangsdaten stellt der Betreiber separat bereit. Direkter MacBook-Test und öffentliche Studentenroute bleiben offen.

## Vollständiger Neubau

1. Timer vor der VM-Anforderung starten. UTC, monotone Zeit, Source-Commit und Template-Identität festhalten.
2. Einen frischen Build-Gast anlegen. Als Planungswert vier vCPUs, 8 GiB RAM und sechs Stunden TTL verwenden, sofern die reale Kapazität ausreicht. Fallback separat dimensionieren und unverändert lassen.
3. Dieses Repository als Eingabepaket verwenden. Es entspricht dem Modus `blank`: Dokumentation, Design und synthetische Fixtures. Keine Anwendung aus dem separaten Modus `ready` übernehmen.
4. Private Konfiguration nur in diesem Gast bereitstellen. Keine Schlüssel in Logs, Git, Screenshots oder Templates.
5. `START_PROMPT.md` ausführen. Die vorbereitete Paper-Datei lesen, Anforderungen prüfen, Anwendung schreiben und G0 bis G5 abarbeiten. Ausführung im Gast über den autorisierten GitVM-Zugang; Paper MCP kann auf dem steuernden Mac bleiben.
6. Tatsächliche Start-, Stopp- und Wiederherstellungsbefehle dokumentieren. Runtime-Kommandos müssen zum geprüften Template passen. Bei einem Template ohne npm kann `node --run` vorhandene package.json-Skripte ausführen; keine nicht vorhandenen Befehle voraussetzen.
7. Echte Browserabläufe, Jev, Reload und Neustart prüfen. Timer erst nach der vollständigen Abnahme stoppen. Fehler und Wartezeiten behalten.

## Zeitgrenze und Fallback

Nach fünfzehn Minuten verbleibende Prüfungen melden. Ist nach zwanzig Minuten die vollständige Abnahme nicht bestanden, das Ziel als verfehlt protokollieren und den zuvor geprüften Fallback zeigen. Den Timer nicht durch weniger Funktionen, simulierte Antworten oder ausgeblendete Fehler kürzen.

Template-Vorbereitung, optionaler Paper-Neubau, vollständiger App-Bau und Wiederherstellung eines fertigen Standes sind vier getrennte Messungen. Das Starten einer fertigen Anwendung zählt nicht als Neubau.

## Öffentlicher Studentenzugang

Eine private Tunnel-URL ist keine öffentliche FQDN. Vor öffentlicher Freigabe getrennte Nutzersitzungen und Daten, geschützte Betreiber-/Jev-Einstellungen, Nutzungsgrenzen, HTTPS sowie konkrete Host-/Origin-Regeln implementieren und testen. Zwei unabhängige Browsersitzungen und einen echten synthetischen Jev-Import über die öffentliche Adresse prüfen. Nur die tatsächlich verifizierte Adresse als erreichbar melden.
