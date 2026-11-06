# GitVM live-build runbook

Dieses Dokument beschreibt den vollständigen Neubau in einem vorbereiteten privaten GitVM-Gast. Es enthält keine Infrastrukturimplementierung oder Zugangsdaten. Der Betreiber stellt die tatsächlichen API-, SSH- und Template-Zugänge separat bereit.

## Vorbereitung vor der Vorführung

- Ein freigegebenes Template mit stabilen kompatiblen Werkzeugen, Browser, PDF/OCR und PostgreSQL bereitstellen. Exakte Versionen, Image-/Rootfs-Hashes, Gastkernel und Scanzeit dokumentieren. Kein Anwendungscode und keine Schlüssel im Template.
- Ein Dependency-Cache ist Vorbereitung und muss exakt zu den ausgewählten Manifesten passen. Bei Abweichung neu bauen und prüfen; keine ungeprüfte Laufzeitinstallation einschleusen.
- Den GitVM-Gast tatsächlich booten und Datenbank, Produktionsstart, Neustartverhalten, Browser und synthetischen Jev-Import prüfen. Containerprüfungen allein beweisen keinen Firecracker-Betrieb.
- Einen fertigen Fallback separat betreiben. Angeforderte maximale Dashboard-TTL: **604800 Sekunden, sieben Tage**. Tatsächlich eingestellte Ablaufzeit und verfügbaren Ressourcen prüfen; niemals eine unbegrenzte Laufzeit behaupten.
- Den Fallback vom MacBook aus direkt über den GitVM-Host erreichen, beispielsweise über einen privaten SSH-Tunnel. Der Mac Studio darf weder Anwendungshost noch notwendiger Proxy sein. Diese Verbindung vor der Präsentation vom MacBook testen.

## Aktuelle Freigabegrenze

Am 6. November 2026 ist die GitVM-Vorlage noch nicht freigegeben. Der Betreiber hat nur den bekannten Host-Kernel-Befund ausgenommen. Das ist keine Ausnahme für Pakete im Gast. Die PDF-Verarbeitung über Poppler/OpenJPEG hat offene anwendbare Befunde; ein verifiziert behobener stabiler Ersatz wurde noch nicht nachgewiesen. Eine neuere Wrapper-Version oder ein sauberer npm-Scan ersetzt keine Prüfung eingebauter Decoder.

Vor Deployment die exakten Artefakte erneut prüfen. Wenn Fix oder erforderliche Abdeckung fehlen, Deployment stoppen und den konkreten Blocker dokumentieren. Der Agent darf unabhängig davon lokale Implementierung und isolierte Tests durchführen. Dieses Repository verspricht keinen bereits laufenden GitVM-Fallback.

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
