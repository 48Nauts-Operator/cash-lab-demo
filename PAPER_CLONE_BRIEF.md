# Cashflow Lab: exact Paper reconstruction

Version 1, 6 November 2026. This is the complete design task for a fresh agent. Create a new Paper file named **Cash-Lab-Demo-02** and reconstruct the fourteen desktop views described below. The target is the reviewed Cash-Lab-Demo-01 design, not a new visual interpretation.

This task creates editable Paper design nodes. Application implementation, live API calls and mobile artboards are separate tasks. Every company, invoice and result shown here is fictional.

## Inputs, ownership and timing

- Repository: `https://github.com/48Nauts-Operator/cash-lab-demo.git`.
- Work in a fresh checkout of the repository above. This optional Paper reconstruction task is timed separately from the application build.
- Read this document, `design/clone-kit/icons.json`, `design/clone-kit/copy.json` and the fourteen reference screenshots listed in `design/manifest.json`.
- The icon file contains the exact source SVGs. The copy file contains the exact German text and text-size/weight/leading records in reading order for each Light view. Dark uses the same copy. Use these records to resolve wording and typography without guessing.
- Reference priority: exact copy/icon kit for wording and text styling, explicit numeric layout rules here, then screenshots for placement. If two inputs disagree, record the disagreement and make the smallest correction that preserves the pictured result.
- Build into a new empty Paper file. Do not clone/duplicate the existing file or replay complete source JSX/HTML. Do not read `design/exports/` or previous generation scripts during this timed run. Freshly authored reusable components within this run are allowed. Deriving a Dark counterpart from your own new Light frame is allowed.
- Never change Cash-Lab-Demo-01, its existing exports, or the presentation file. Only write `design/runs/clone-02/**` and the new Paper file. Coordinate ownership if application work runs concurrently.
- Start the timer before reading the task inputs. Record UTC and `time.monotonic_ns()` on this machine. Include instruction reading, MCP connection, file creation, construction, review, corrections and exports. Stop only after all fourteen final frames and checks are complete. Record parent review separately if it occurs after the worker finish.
- Record milestones for first reviewed dashboard, all Light views, all Dark views, final export and review. Keep elapsed seconds and all failed attempts. Report connection/API waiting separately. Do not reduce the scope to meet a target time.

## Paper execution

Use actual Paper MCP tools. Read `get_guide` with topic `paper-mcp-instructions`, discover current schemas, create the empty file, read its basic information, and check the Inter font with `get_font_family_info`. Pass explicit file/page IDs throughout. Follow the Paper guide's incremental section-writing and screenshot-review workflow.

Use the available native Paper MCP connector or the official Paper CLI transport. Discover tool schemas in the current session. No machine-specific helper is required or included. Do not infer tool arguments from names.

Use editable text, layout containers, borders and vector charts. Screenshots are comparison references, not full-frame image layers. SVG charts and icons are acceptable vectors. Release working indicators with `finish_working_on_nodes` at completion.

## Required frames

Every artboard is exactly **1440 × 900 px**. Name frames exactly as below. Put each Light/Dark pair side by side, with enough canvas space between pairs.

| Pair | Light | Dark | Reference screenshot prefix |
| --- | --- | --- | --- |
| Main plan | dashboard-light | dashboard-dark | `design/dashboard-` |
| Docked document queue | upload-docked-light | upload-docked-dark | `design/upload-docked-` |
| Document review | import-review-light | import-review-dark | `design/import-review-` |
| Company and Jev settings | settings-light | settings-dark | `design/settings-` |
| Analytics overview | analytics-light | analytics-dark | `design/analytics-` |
| Payment history and message | payment-history-light | payment-history-dark | `design/payment-history-` |
| Reusable states | states-light | states-dark | `design/states-` |

Each prefix is followed by `light.jpg` or `dark.jpg`. The original screenshots are JPEG, not PNG.

## Exact palette

Apply these values explicitly to every text and SVG. Dark text must never appear on a dark surface. Dark text is allowed on the light-blue filled primary button.

| Semantic role | Light | Dark |
| --- | --- | --- |
| Main background / solid control surface | `#FFFFFF` | `#17191F` |
| Main text and outline icons | `#17212B` | `#F2F5FC` |
| Secondary text, axes, baseline | `#5B6573` | `#B9C1CF` |
| Borders, dividers, grid, inactive bar track | `#DDE2E8` | `#414752` |
| Soft panel/card | `#F4F7FB` | `#22252D` |
| Blue action, selected text and scenario | `#2455E6` | `#83AEFF` |
| Blue selection/notice background | `#EDF2FF` | `#20365B` |
| Negative value/error text | `#B42332` | `#FF9BA5` |
| Negative chart area | `#FFF1F3` | `#3B2831` |
| Primary button foreground | `#FFFFFF` | `#17191F` |
| Review backdrop | `#17212B1A` | `#0000002E` |

All Dark artboards have the neutral grey root gradient `linear-gradient(135deg, #111318 0%, #292D35 100%)`. Paper may serialize its colour interpolation as `in oklab`; preserve the same direction and stops. The wide Dark review pane has a solid `#191C22` surface and its document preview is `#252932`. Light equivalents are white and the soft panel colour. Do not turn the entire Dark surface navy. Blue is an accent only.

Charts use no green success series, purple category palette or extra colours. Success states use the same blue accent. Borders are 1 px. No decorative shadows, glass blur, photographs or illustrations.

## Typography and controls

Font is **Inter** everywhere, including SVG labels. Check the installed font before writing. Use regular 400, medium 500, semibold 600, variable 650 and bold 700 where specified. Use the actual per-label values in `copy.json`; the generic token stylesheet from the old export is not the typography authority for this reconstruction.

| Element | Font size / line height | Weight and tracking |
| --- | --- | --- |
| Brand | 20 / 24 px | 700, `-0.03em` |
| Dashboard title | 30 / 36 px | 700, `-0.04em` |
| Settings title | 32 / 38 px | 600 |
| Analytics title | 30 / 36 px | 650 |
| History/state-board title | 28 / 34 px | 650 |
| Docked plan title | 26 / 32 px | 650 |
| Wide import title | 24 / 30 px | 650 |
| Main dashboard KPIs | 34 / 40 px | 700, `-0.04em` |
| Docked KPIs | 28 / 34 px | 650 |
| Analytics KPIs | 30 / 36 px | 600 |
| Section headings | 18 / 24 px | 600 |
| Settings section / queue title / state title | 20 / 26 px | 600 |
| Main body/navigation | 14 / 20 px | 400; actions 500 or 600 |
| Compact rows/subtitles | 13 / 19 px | 400 |
| Helper, axis, table headings, badges | 12 / 18 px | 400; badges 500 or 600 |
| Small source/help notes | 11 / 17 px | 400 |

Some header elements use 14/18 and badges 12/16 exactly as in the copy kit. Do not enlarge every item to a uniform body size. Keep German text and Swiss apostrophe grouping, e.g. `CHF 14'000`, and Unicode minus for negative chart values.

Use 8 px radii for normal controls and cards, 5 or 6 px for compact inputs/buttons, 4 px for DEMO badge, and 9 px for the 32 px logo tile. Input borders use the line colour. Primary buttons use blue fill and the theme-specific primary foreground. Secondary buttons use a surface fill and 1 px line border. Disabled controls keep readable muted text and a soft fill; do not fade all content into illegibility.

## Icons and common header

Use the eight exact SVG definitions in `icons.json`. They specify logo, theme, settings and right-chevron variants for each theme. Keep their dimensions, paths and stroke widths. Do not substitute emoji or an unrelated icon set.

- Logo: blue 32 × 32 px tile; white upward zigzag, SVG 22 × 20 px, stroke 2.4 px.
- Light theme button: outlined moon, 20 × 20 px in a 40 × 40 px outline control.
- Dark theme button: outlined sun, same control. There are no visible Light/Dark words. Intended accessible names are `Dunkles Design` and `Helles Design`.
- Settings: outlined gear, SVG 20 × 20 px, 40 × 40 px control. Intended accessible name `Einstellungen`.
- Queue/review close: right chevron, 32 or 36 px control as shown. Intended accessible name `Dokumentbereich einklappen`.
- Import button has the literal leading `+`. Source links use `Quelle →`; target selector uses a small downward triangle. Preserve these text glyphs.

All frames except states have the same 72 px tall header with a bottom divider and 40 px horizontal padding. Left group: logo, 12 px gap, `Cashflow Lab`, DEMO badge, then Plan/Analysen navigation with 20 px separation and 28 px leading space. Right group: segmented Demo-Daten/Eigene Daten selector, theme icon, `+ Dokument importieren`, settings icon, with 12 px gaps. Demo-Daten is selected. The active Plan/Analysen item is blue and semibold. Settings preserves the reference header and adds `Zurück zum Plan` in its page header.

## Shared fixed financial data

Plan period is 09.11.2026 through 20.12.2026, six Monday-based weeks. Opening balance CHF 10'000. The pictured scenario moves Studio Nord by fourteen calendar days while preserving its contractual due date.

| Week starting | Base closing CHF | Scenario closing CHF | Base receipts CHF | Payments CHF |
| --- | ---: | ---: | ---: | ---: |
| 09.11.2026 | 7'000 | 7'000 | 4'000 | 7'000 |
| 16.11.2026 | 13'000 | −1'000 | 14'000 | 8'000 |
| 23.11.2026 | 9'000 | −5'000 | 6'000 | 10'000 |
| 30.11.2026 | 3'000 | 3'000 | 0 | 6'000 |
| 07.12.2026 | 7'000 | 7'000 | 9'000 | 5'000 |
| 14.12.2026 | 2'000 | 2'000 | 0 | 5'000 |

Invoices: Atelier West CHF 4'000 due/expected 11.11.2026; Studio Nord CHF 14'000 due 18.11.2026 and scenario expected 02.12.2026; Berg & Tal CHF 6'000 due/expected 25.11.2026; Werkraum CHF 9'000 due/expected 09.12.2026. All four have a `+14 Tage` action. Highlight Studio Nord with the blue-soft row, blue customer and expected-date text, and semibold amount.

The end balance is CHF 2'000; lowest scenario week closing CHF −5'000 in week starting 23 November; first negative week begins 16 November. Planned incoming total is CHF 33'000 over four invoices; outgoing CHF 41'000 over six payments; net cashflow CHF −8'000. Opening balance is not revenue.

## 1. Dashboard pair

Body starts below header with 40 px horizontal padding, 26 px top padding and 18 px vertical section gaps; content width 1360 px. Title/subtitle on left, period and opening-balance bordered controls on right. Title `Deine nächsten sechs Wochen.`; subtitle `Was passiert, wenn dein Kunde später zahlt?`.

Three horizontally arranged KPIs occupy about y196 to y282. Use vertical dividers, not separate cards: widths 31%, 36%, 33%, 30 px inset after dividers. Labels and explanations come from the copy kit. A horizontal divider ends the section around y302.

Chart title row: `Liquidität im Vergleich`, blue-soft scenario badge, dashed Basisplan legend, solid Szenario legend, and reset action at right. Native SVG is 1360 × 184 px. Plot x from 68 to 1330; sample centres x=90,330,570,810,1050,1290. Map CHF 15'000 to y10 and CHF −5'000 to y160, hence zero y122.5. Grey horizontal grid, zero line, pale-red area below zero. Baseline dashed 6/6 and 2 px; scenario solid blue 3 px with radius-4 blue markers and 2 px background-coloured outline. X labels at y181. Baseline points are `(90,70),(330,25),(570,55),(810,100),(1050,70),(1290,107.5)`; scenario differs at second `(330,130)` and third `(570,160)`.

Below the chart show two complete rows labelled Basis and Szenario, aligned with six dates. Negative values are red and scenario values semibold. Show no smoothing, fake confidence band or extra forecast series.

Bottom split is 896 px invoice table, 32 px gap, 432 px outgoing list. Invoice columns are customer, amount, due date, expected receipt, scenario action; four rows. Outgoing list has six Monday amounts. Footer shows the fictional-data/intraweek warning on the left and `Letzte Speicherung gerade eben` at right.

## 2. Docked queue pair

Keep the full common header. Below it split left 1064 px and right 376 px, no backdrop/scrim. Left padding is 24 px; right padding 20 px, soft fill and left divider. The left plan remains fully legible.

Left title/period/opening balance, compact KPIs, then chart section and invoice table. Use the same six values and a simplified 1016 px-wide vector chart; map identical values linearly and include zero, −5k and 15k labels. Keep all six dates and both full numeric rows. Compact invoice rows are 13 px. Below them show `Geplante Auszahlungen · CHF 41'000 über sechs Wochen` with `Auszahlungen bearbeiten`, then fictional-data note.

Queue: title `Dokumente` and chevron; target label and full-width `Eigene Daten ▾` selector; note `Die Demo bleibt unverändert.`. Dashed dropzone with `Dateien hier ablegen`, `PDF, Scan oder .eml`, and `Datei auswählen`. Then `3 Dokumente · Beispiel-Warteschlange` and three bordered cards, separated by 20 px:

1. `01-text-invoice.pdf`, `Bereit zur Prüfung`, `Prüfen`.
2. `02-scan-invoice.pdf`, `OCR · Text wird erkannt`, `Abbrechen`.
3. `studio-nord-zusage.eml`, `Wartet auf Bestätigung`, `Inhalt prüfen`.

Finish with a blue-soft notice explaining confirmation before TypeSafe transmission. No invented percentage progress.

## 3. Import review pair

Start from your newly created complete dashboard. Overlay the full-frame theme backdrop and a right-aligned 720 × 900 px review pane, 28 px padding, 20 px main gaps. The dashboard remains visible behind the left half. This wide review is distinct from the docked queue.

Top title `Dokumente importieren`, chevron, explicit target `Eigene Daten` and demo-preservation note. Tabs `PDF oder E-Mail-Datei` active with blue underline and `E-Mail-Text einfügen`. Dropzone across pane. Selected document row: PDF badge, `03-multiple-amounts.pdf`, `1 Seite · Fiktive Rechnung für die Demo`, `Erkannt · bitte prüfen`.

Middle columns: 276 px source preview and approximately 340 px form, 24 px gap. Preview contains Cashflow Demo Agentur AG, recipient Atelier Seefeld, Zürich, invoice TEST-003, issued 26.11.2026, due 10.12.2026, service `Konzept und Gestaltung`, CHF 4'000.00 net, MWST 8.1% CHF 324.00, highlighted total CHF 4'324.00. Add the provenance/help note below the preview.

Form: Eingang/Ausgang segment, Eingang selected; customer Atelier Seefeld; outstanding CHF 4'324.00; invoice due 10.12.2026; expected payment 10.12.2026. Keep field labels and explanatory text. At bottom an unchecked confirmation checkbox in a blue-soft strip and `Abbrechen` plus disabled `Übernehmen`. The footer says only confirmed values enter the plan. No checkbox can appear already checked.

## 4. Settings pair

Common header; page body 80 px side margins, 40 px top padding, 1280 px total width. Title `Einstellungen`, subtitle `Dein Unternehmen und die Dokumentprüfung.`, right `Zurück zum Plan`.

Two columns separated by vertical line around x688. Left starts x80, width536: `Unternehmen`, explanation, company name `Cashflow Demo Agentur AG`, optional address `Musterstrasse 12, 8000 Zürich`, optional email `demo@example.com`, fictional-data note. Inputs approximately 46 px high with 6 px radius.

Right starts x729 and ends x1360: `Jev / TypeSafe`, `Nicht verbunden` badge, explanation; `Gespeicherter API-Key: keiner`; empty new-key input with `API-Key eingeben`; note that stored keys are never displayed; model field `Nach erfolgreicher Verbindung auswählen`; outlined `Verbindung prüfen`, `Noch kein Verbindungstest ausgeführt.`; blue-soft data-transmission notice. Never draw a real key or a fake successful connection.

Horizontal divider around y721; changes apply to own data note at left; `Abbrechen` and blue `Speichern` at right. Same colour/typography rules as other views.

## 5. Analytics pair

Common header with Analysen active. Body x40 to1400, title `Dein Plan in Zahlen.`, period/fictional-data/weekly-balances subtitle. Upper-right subtabs Übersicht active and Zahlungsverhalten. Four KPI columns: incoming CHF33'000/4 Rechnungen, outgoing CHF41'000/6 Auszahlungen, red net CHF−8'000, final CHF2'000 with opening balance note. Vertical dividers and bottom separator.

Middle row has two columns, each approximately 656 px, separated by48 px. Left `Prognose über Zeit` with baseline/scenario chart using exactly the shared balances, zero line and red below-zero area. Use 15k,0k,−5k ticks and all six dates. Right `Wöchentliches Volumen · Basisplan` with **grouped vertical bars**: blue receipts and grey payments for every week, values 4/7,14/8,6/10,0/6,9/5,0/5 thousand CHF. Bars have value labels above and dates below; zero amounts are labelled0k. Do not substitute a pie chart.

Bottom row begins around y568 after divider. Left width400: `Kostenkategorien`, CHF41'000 planned payment total, five **horizontal blue bars**. Personal15'000, Externe Leistungen10'000, Büro6'000, Software5'000, Marketing5'000. Bar widths relative to maximum15'000 are100%,66.667%,40%,33.333%,33.333%; thin soft track behind. Each row has name left and CHF amount right.

Right x488 to1400: `Jev-Prüfung je Rechnung`, badge `Fiktive Prüfergebnisse`, four ruled rows and source links. Atelier West/Geprüft/Betrag und Fälligkeit belegt; Studio Nord/Vorschlag/Erwarteten Eingang bestätigen; Berg & Tal/Angaben fehlen/Zahlungsstatus nicht im Beleg; Werkraum/Nicht geprüft/Prüfung noch nicht gestartet. Footer explains user confirmation. No credit score or actual-payment certification.

## 6. Payment history pair

Common header with Analysen active. Body x40 to1400. Title `Was sagt die Zahlungshistorie?`, subtitle `48 bezahlte Demo-Rechnungen · Fälligkeiten Mai bis Oktober 2026 · Stichtag 06.11.2026`, `Synthetische Historie` badge. Below, Übersicht and active underlined Zahlungsverhalten.

Upper split: left width760, right width560, gap40. Left `Pünktlich bezahlt`, legend explaining blue on-time and grey late, twelve records each. Four ruled rows: customer width170, 300 px horizontal on-time bar over grey track, count, median. Values Atelier West9/12 median0; Studio Nord1/12 median14; Berg & Tal1/12 median7; Werkraum11/12 median0. Highlight Studio Nord's row.

Right with left divider and28 px inset: `Studio Nord im Detail`, large blue `14 Tage`, `mediane Verspätung`, sample count12 and one on time. Twelve compact day chips in order `14,14,7,21,14,28,0,14,7,21,14,14`. Notes show zero open overdue invoices at cutoff and explicitly state that history is not a future-payment probability.

Lower split begins around y500 after a divider: two660 px columns,40 px gap. Left `Eine Nachricht verändert den Plan`, outlined `Mit Jev prüfen`, sender/date/invoice line. Soft bordered message card contains these exact paragraphs:

> Hallo, wir können die Rechnung DEMO-2026-002 über CHF 14'000 nicht wie vorgesehen am 18. November bezahlen.
>
> Wir werden am 2. Dezember 2026 zahlen.
>
> Der Rechnungsbetrag bleibt unverändert. Grüsse, Studio Nord.

Highlight only the middle promise with blue-soft fill and a3 px blue left border. Include additional demo cases note below.

Right: `Vorschlag zu DEMO-2026-002 · CHF 14'000`, visibly fictional/unstarted-result note. Three separated rows: contractual due18.11.2026, history suggestion02.12.2026 with median+14days/12records, message promise02.12.2026 with source-reference note. Bottom red `Nach Übernahme: Tiefpunkt CHF −5'000`, unchanged due/final-balance helper, blue `Als Szenario übernehmen` button. Distinguish factual due date, inference and stated promise.

## 7. Reusable states pair

No app header. Full artboard with32 px padding and24 px vertical gaps. Title `Zustände und Rückmeldungen`, subtitle `Wiederverwendbare Zustände für Import und Prüfung · Fiktive Beispiele`. Three columns of432 px cards,40 px horizontal gaps; three rows of224 px cards,24 px vertical gaps. Cards use soft fill,1 px border,8 px radius,20 px padding. Small status label,20 px title,13 px body and bottom action row. Exact text is in the copy kit.

| Position | Status / heading | Required actions |
| --- | --- | --- |
| Row1 col1 | Leerer Plan / Noch keine eigenen Daten | Dokument importieren; Demo-Daten laden |
| Row1 col2 | OCR läuft / Text wird erkannt | Abbrechen |
| Row1 col3 | Jev-Prüfung läuft / Angaben werden geprüft | Abbrechen |
| Row2 col1 | Einrichtung erforderlich / API-Zugang fehlt | Einstellungen öffnen |
| Row2 col2 | Prüfung fehlgeschlagen / TypeSafe nicht erreichbar | Erneut versuchen; Manuell prüfen |
| Row2 col3 | Mögliches Duplikat / Rechnung bereits vorhanden | Vorhandene Rechnung öffnen; Import verwerfen |
| Row3 col1 | Übernahme gesperrt / Bitte Angaben ergänzen | Angaben bearbeiten |
| Row3 col2 | Deine Bestätigung / An TypeSafe senden? | unchecked consent checkbox; disabled Prüfung starten; Inhalte ansehen |
| Row3 col3 | Erfolgreich gespeichert / Rechnung übernommen | Zum eigenen Plan |

Error/warning status labels are red; other status labels blue. Titles are normal foreground. Preserve filenames, invoice IDs, target-plan notes and saved-draft explanations from the copy kit.

## Intended interaction and responsive contract

These are design specifications for the implementation handoff. Do not claim clicking Paper drawings runs APIs.

- Navigation opens Plan, Analysen or Einstellungen. Analytics subtabs switch overview/history.
- Theme button changes appearance and persists preference. Icon gives the target action; no visible theme words.
- Queue chevron closes the panel and preserves drafts. Import button reopens it. Prüfen enters wide review, Abbrechen returns to queue.
- Own-data target remains explicit; loading demo never overwrites own data.
- User reviews transmission contents before Jev, then confirms financial values separately before importing.
- +14 Tage and confirmed message proposal change only expected scenario date. Reset restores base dates without deleting sources or entries.
- At1280px+ docked queue stays376px; at1024–1279px use320px. Below1024px it becomes an overlay. Below768px use full width, stack preview/form and KPIs, and preserve table scroll. No squeezed tiny text.
- Icon controls need accessible labels and at least44×44px hit areas in the app, even when a32–40px drawn control remains inside that hit area. Modal review needs Escape, focus capture and return. Docked queue is non-modal.

## Acceptance and output

Review every full-size screenshot. Check all fourteen views against their matching references, with particular attention to text wrap, header widths, form labels, dark icon visibility, chart scales and clipped bottom content. Correct differences before finishing.

Acceptance requires:

1. New file named Cash-Lab-Demo-02; original file unchanged; fourteen1440×900 frames, correct names, editable text and vector charts.
2. Exact semantic colours, neutral-grey gradient, Inter, specified icons and icon-only theme control.
3. All required charts and all six-week data points match; every displayed total/date/customer/status is correct.
4. Matching hierarchy and proportions. Key container positions and widths should be within4px of the reference; typography uses copy-kit sizes. If this is not achieved, report the deviation instead of calling it pixel-identical.
5. Both upload modes, all nine states, all settings fields, all history evidence and all fictional-data labels are present.
6. No clipped labels, missing values, inaccessible dark-on-dark content, fake API success or rasterized full screens.
7. Export final screenshots with correct extension for returned MIME type, exact native JSX and style exports, and a manifest with file/page/frame IDs and SHA256 hashes.
8. Save `design/runs/clone-02/timing.json`, `review.md`, `manifest.json`, `exports/`, screenshots and newly authored generation script if used. Review lists PASS/FAIL and deviations; timing distinguishes worker completion from independent parent review.

End with the new Paper URL, actual elapsed time, first-dashboard time, passed/failed checks, and any difference from the reference. The coordinator will independently inspect the results and compare elapsed time with the first two design runs.
