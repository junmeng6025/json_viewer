# JSON Viewer

**Visualisieren. Vergleichen. Bearbeiten. Originaldaten bewahren.**

JSON Viewer ist eine eigenständige HTML-Anwendung zur lokalen Betrachtung numerischer Daten in JSON-Dateien: 1D-Kennlinien, 2D-Matrizen, mehrdimensionale Array-Schnitte und Skalarwerte. Zwei Versionen lassen sich nebeneinander vergleichen. Bearbeitungen erfolgen in einer vollständigen **Arbeitskopie C**, nicht in der hochgeladenen Originaldatei.

![Vorschau mit synthetischen Beispieldaten](assets/preview.png)

Sprachen: [English](README.md) · [简体中文](README.zh-CN.md) · [Deutsch](README.de.md)

## Schnellstart

`index.html` herunterladen und in einem aktuellen Desktop-Browser (vorzugsweise Chrome oder Edge) öffnen. **Einzeldatei** zum Visualisieren eines JSON-Dokuments oder **Versionsvergleich** für zwei zusammengehörige Dateien wählen. Die Sprache oben rechts wechseln. JSON-Variablennamen, Pfade, Schlüssel und Werte werden nicht übersetzt.

## Funktionen

- Numerische Arrays, explizite X/Y-Kennlinien, X/Y/Z-Matrizen, mehrdimensionale Schnitte und Skalarwerte erkennen.
- 1D-Diagramme, Heatmaps und interaktive 3D-Oberflächen mit Achsen, Gitterpunkten und Z-Farbskala anzeigen.
- 3D-Bedienung: mit linker Taste drehen, mit mittlerer Taste verschieben, mit dem Rad zoomen, per Doppelklick zurücksetzen. Bei Hover auf einem Punkt X/Y/Z ablesen; über einer Profillinie einen Schnitt anzeigen und per Klick fixieren. Im Einzeldateimodus liegt die Schnitttabelle über dem Diagramm, beim Versionsvergleich **unterhalb** der jeweiligen 3D-Oberfläche.
- Versionen A und B mit gemeinsamen Skalen vergleichen; Änderungen, Ergänzungen und Löschungen markieren.
- Eine vollständige Arbeitskopie C aus dem Original oder aus A/B erstellen, Werte ändern, Unterschiede zum Original hervorheben, rückgängig machen, zurücksetzen und C vollständig exportieren.
- CSV- und PNG-Export, zusätzlich CSV für Skalarunterschiede.
- **PDF-Differenzbericht direkt und offline herunterladen:** Jede geänderte Kurve oder Matrix erhält eine eigene Seite mit A/B-Grafiken oben und vollständigen A/B-Parametertabellen unten. Abweichungen sind orange hervorgehoben. Mehrere Skalarwerte stehen auf einer Seite. Weißer Hintergrund; alle Schnitte einer mehrdimensionalen Variablen bleiben auf einer gegebenenfalls höheren Seite.

## Beispieldaten und Datenmodell

[`examples/demo.json`](examples/demo.json) enthält ausschließlich synthetische Zahlen. Eine X/Y-Kennlinie verwendet etwa `SpeedXAxis_F` und `ResponseYAxis_F` innerhalb desselben Objekts. Eine Matrix ergänzt `LoadYAxis_F` und `ResponseZAxis_F`; die Zeilen entsprechen Y, die Spalten X.

Automatische Zuordnungen anhand von Namen und Arraylängen sind heuristisch und keine verbindliche Schemaprüfung. Bitte Achsenzuordnung und Einheiten prüfen. Für den Vergleich und PDF-Export stehen die rein synthetischen Dateien [`version-a.json`](examples/version-a.json) und [`version-b.json`](examples/version-b.json) bereit.

![Schnitttabellen unter beiden 3D-Diagrammen (synthetische Daten)](assets/comparison-preview.png)

![PDF-Berichtsvorschau (synthetische Daten)](assets/pdf-report-preview.png)

## PDF-Differenzbericht

Im Modus **Vergleich** A und B laden und auf **PDF-Differenzbericht exportieren** klicken. Die Datei wird **direkt heruntergeladen**, ohne Druckdialog, Server oder externe Bibliothek. Grundlage sind ausschließlich die **Originale A/B**; ungesicherte Änderungen an der Arbeitskopie C werden nicht einbezogen. Jede veränderte Kurve bzw. Matrix hat eine eigene Seite: oben die Visualisierung, unten die vollständigen Parametertabellen. Skalarunterschiede werden seitenweise zusammengefasst. Alle Schnitte einer mehrdimensionalen Variablen erscheinen auf einer einzigen Seite, die höher als A4 quer sein kann. PDF-Seiten sind hochauflösende Rasterbilder (Text ist nicht auswählbar oder durchsuchbar).

## Datenschutz und Arbeitskopie

Ausgewählte JSON-Dateien werden ausschließlich im Browser verarbeitet; es werden keine Daten an einen Server gesendet. Beim ersten Bearbeiten entsteht eine vollständige Kopie C. Nur C wird geändert, andere Felder bleiben erhalten. Beim Wechsel von A zu B als Quelle ist eine Bestätigung nötig. Die Originaldatei wird nicht überschrieben; Änderungen werden erst durch den Export von C lokal gesichert.

## Einschränkungen

Die 3D-Oberfläche verbindet nur vorhandene Stützstellen zur Visualisierung; sie bildet keinen anwendungsspezifischen Interpolationsalgorithmus ab. Einheiten können aus Variablennamen geschätzt werden und sind dann mit `(?)` markiert. Die Anwendung prüft weder Monotonie der Stützstellen noch `_size_`-Felder, domänenspezifische Vorgaben oder Sicherheitsgrenzen. Absolute lokale Ordnerpfade sind über den normalen Browser-Dateidialog nicht verfügbar; bei gleichen Dateinamen kann ein Ordnerlabel eingegeben werden.

## Auf GitHub veröffentlichen

Den Ordnerinhalt in ein Repository übertragen. `index.html` funktioniert direkt offline oder über GitHub Pages. Für Issues und Beispiele nur bereinigte bzw. synthetische Daten verwenden.

Einheitliche Begriffe: Arbeitskopie C / Working copy C / 工作副本 C; Stützstelle / Breakpoint / 断点; Profillinie / Ridge / 脊线; Schnitt / Slice / 切片.

**Lizenz:** Bitte vor der Veröffentlichung eine vom Repository-Inhaber gewählte `LICENSE`-Datei hinzufügen (z. B. nach Prüfung MIT oder Apache-2.0). Dieses Paket trifft keine Lizenzentscheidung.
