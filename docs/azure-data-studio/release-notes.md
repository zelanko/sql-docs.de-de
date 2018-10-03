---
title: Versionshinweise zu Azure Data Studio | Microsoft-Dokumentation
description: Versionshinweise zu Azure Data Studio
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6b1328b1d0a0832e9d412d1fcd908f3cdb0d349
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038461"
---
# <a name="azure-data-studio-release-notes"></a>Versionshinweise zu Azure Data Studio

**[Herunterladen der September *allgemeiner Verfügbarkeit* (GA-Version).](download.md)**

## <a name="september-2018-september-ga-release"></a>September 2018 (September GA-Version)

Veröffentlichungsdatum: 24. September 2018  
Version: 1.0

Allgemein verfügbare Version von Azure Data Studio (früher SQL Operations Studio).

- Ankündigung der Vorschau von SQL Server-2019-Erweiterung.
  - Unterstützung für SQL Server-2019 vorschaufeatures einschließlich [big Data-Cluster](../big-data-cluster/big-data-cluster-overview.md) unterstützen.
    - Verbinden Sie sich an das HDFS/Spark-Gateway, das im Lieferumfang von SQL Server-2019 Vorschau.
    - Durchsuchen von HDFS, Hochladen von Dateien, Dateien speichern und nützliche Aktionen wie das Analysieren im Notebook für CSV-Dateien zu starten.
    - Übermitteln von Spark-Aufträgen über das Dashboard, oder mit der rechten Maustaste auf eine HDFS/Spark-Verbindung im Objekt-Explorer.
  - Azure Data Studio Notebooks
    - Erstellen oder Öffnen von Notebooks mit einem integrierten Notebook-Viewer. In dieser Version das Notebook unterstützt Viewer, die Verbindung mit lokalen Kernels und die SQL Server-2019 big Data-Cluster nur.
    - Verwenden Sie die PROSE Code Accelerator-Bibliotheken in Ihrem Notebook, um Dateitypen Format und die Daten für schnelle datenvorbereitung erfahren.
  - Azure-Ressourcen-Explorer
    - Die Azure-Ressourcen-Explorer-Ansicht können Sie datenbezogene Endpunkte für Ihre Azure-Konten durchsuchen, und erstellen im Objekt-Explorer-Verbindungen für sie. In dieser Version werden die Azure SQL-Datenbanken und Servern unterstützt.
  - SQL Server-Polybase Erstellen externer Tabellen-Assistent
    - Erstellen Sie eine externe Tabelle und die unterstützenden Systemmetadaten-Strukturen mit einer benutzerfreundlichen Assistenten an. In dieser Version werden die SQL Server- und Oracle-Remoteserver unterstützt.
- Fragen Sie Ergebnisraster Verbesserungen der Leistung und UX für große Anzahl von Resultsets.
- Visual Studio Code-Quellcode Aktualisieren von "1,23", um 1.26.1 mit Rasterlayout und verbesserte-Einstellungs-Editor (Vorschau).
- Verbesserungen der Barrierefreiheit für die Sprachausgabe und Tastaturnavigation mit hohem Kontrast.
- Hinzugefügt `Connection name` Option aus, um einen alternativen Anzeigenamen in der Ansicht-Let-Server angeben.

### <a name="bug-fixes"></a>Fehlerbehebungen

- Beheben Sie [Problem #2647](https://github.com/Microsoft/azuredatastudio/issues/143): die Diagramme hat einen großen Schritt rückwärts.
- Beheben Sie [Problem #2648](https://github.com/Microsoft/azuredatastudio/issues/143): auswählen, die eine JSON-links auf die gesamte Spalte zurückgibt.
- ...

Ausführliche Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), und [Versionen](https://github.com/Microsoft/azuredatastudio/releases).


## <a name="august-2018-august-public-preview"></a>August 2018 (öffentliche Vorschau für August)

Veröffentlichungsdatum: 30. August 2018  
Version: 0.32.8

*0.32.8 bietet Korrekturen für einige Regressionen finden Sie im 0.32.7 ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971), [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372)*)

Die *öffentliche Vorschau für August* Fehlerbehebungen, Produkt, Stabilisierung und Auffüllen der Lücken in vorhandenen Szenarios im Mittelpunkt.  

- Ankündigung der SQL Server-Import-Erweiterungs
- SQL Server Profiler-sitzungsverwaltung
- Unterstützung für die Vorlage von SQL Server Profiler-Sitzungen
- SQL Server-Agent-Verbesserungen
- Neue Community-Erweiterung: erste Beantworter Kit
- Lebenszyklusverbesserungen:-Verbindungszeichenfolgen

### <a name="bug-fixes"></a>Fehlerbehebungen

- Analysieren von SQL-Code in einem Abfrage-Editor-Fenster mit den `Parse Syntax` Befehl.
- Beheben Sie [Problem #143](https://github.com/Microsoft/azuredatastudio/issues/143): Doppelklicken Sie auf keine Variable-Name auswählen.
- Beheben Sie [Problem #387](https://github.com/Microsoft/azuredatastudio/issues/387): SQL-DB Registerkartensymbol ist rot.
- Beheben Sie [Problem #825](https://github.com/Microsoft/azuredatastudio/issues/825): anfordern: automatische Ablaufsteuerungsverbindung zum aktuellen Server nach dem Skript für Objekttyp als... 
- Beheben Sie [Problem #1278](https://github.com/Microsoft/azuredatastudio/issues/1278): sqlops.desktop [Desktop Entry -] redundante Wert für Name der & Kommentar.
- Beheben Sie [Problem #1285](https://github.com/Microsoft/azuredatastudio/issues/1285): Aktualisieren bewirkt, dass Anwendungssymbol entfernt/ersetzt in Windows sein.
- Beheben Sie [Problem #1317](https://github.com/Microsoft/azuredatastudio/issues/1317): Beheben Sie das Dezimaltrennzeichen.
- Beheben Sie [Problem #1474](https://github.com/Microsoft/azuredatastudio/issues/1474): Verbindung von "Abbrechen" ändern trennt die aktuelle Verbindung.
- Beheben Sie [Problem #1497](https://github.com/Microsoft/azuredatastudio/issues/1497): als Diagramm anzeigen Optionen sind am unteren Rand abgeschnitten.
- Beheben Sie [Problem #1524](https://github.com/Microsoft/azuredatastudio/issues/1524): Shell/Dashboard: Main Viewlet Symbole sind ziehbare und können die app abstürzt.
- Beheben Sie [Problem #1578](https://github.com/Microsoft/azuredatastudio/issues/1578): / Remotedatei Browserordner ExpandCollapse durch Klicken auf die Namen nicht möglich.
- Beheben Sie [Problem #1620](https://github.com/Microsoft/azuredatastudio/issues/1620): Feature Vorschlag: Abrufen der Verbindungszeichenfolge für die vorhandene Verbindung.
- Beheben Sie [Problem #1624](https://github.com/Microsoft/azuredatastudio/issues/1624): keine zu verwendenden Farbe wenn deaktiviert ändern.
- Beheben Sie [Problem #1728](https://github.com/Microsoft/azuredatastudio/issues/1728): als JSON/EXCEL/CSV-Datei nicht die Arbeit zu speichern.
- Beheben Sie [Problem #1744](https://github.com/Microsoft/azuredatastudio/issues/1744): Bereich "Ergebnisse" verliert die Bildlauf Positionen aus, wenn zwischen Registerkarten wechseln.
- Beheben Sie [Problem #1748](https://github.com/Microsoft/azuredatastudio/issues/1748): Fehlermeldung beim Speichern des Zeitpunkts der Excel-Datei, die zweite (und alle nachfolgenden).
- Beheben Sie [Problem #1782](https://github.com/Microsoft/azuredatastudio/issues/1782): Bearbeiten von Daten: Zelle nicht auf den ursprünglichen Wert auf das Drücken der ESC-Taste zurückgesetzt.
- Beheben Sie [Problem #1836](https://github.com/Microsoft/azuredatastudio/issues/1836): SQL-Dateien, die nicht mit SQL Operations Studio verknüpft sind.
- Beheben [Problem #1850](https://github.com/Microsoft/azuredatastudio/issues/1850): Eingabe N'' vervollständigt n '''.
- Beheben Sie [Problem #1985](https://github.com/Microsoft/azuredatastudio/issues/1985): Kopieren aus dem Raster mit Abfrageergebnissen ist deaktiviert, indem 1 Spalte.
- Beheben Sie [Problem #1998](htpts://github.com/Microsoft/azuredatastudio/pull/1998): Hinzufügen von VS Code-Version auf Info-Dialogfeld.
- Beheben Sie [Problem #2042](https://github.com/Microsoft/azuredatastudio/pull/2042): Agent: aktiviert die Schaltfläche zum Abfragen von Sql-Dateien importieren.
- Beheben Sie [Problem #2091](https://github.com/Microsoft/azuredatastudio/issues/2091): Verwenden Sie STRG + C-Verknüpfung kann nicht zum Kopieren aus dem Ergebnisbereich.
- Beheben Sie [Problem #2099](https://github.com/Microsoft/azuredatastudio/pull/2099): Weitere SaveAsCsv Optionen hinzugefügt.
- Beheben Sie [Problem #2107](https://github.com/Microsoft/azuredatastudio/issues/2107): Update Dokumentsymbol für Dashboards und der Profiler-Dokumente.
- Beheben Sie [Problem #2129](https://github.com/Microsoft/azuredatastudio/pull/2129): Bearbeiten von Daten speichern Bildlaufposition, die beim Wechseln von Registerkarten.
- Beheben Sie [Problem #2152](https://github.com/Microsoft/azuredatastudio/issues/2152): Ergebnisse Raster Zeile Indikator 0 (null) basieren.

## <a name="known-issues"></a>Bekannte Probleme

- [Problem #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) speichern als erste Zeile der Daten nur speichert Excel
- [Problem #2150](https://github.com/Microsoft/azuredatastudio/issues/2150): kann nicht für die Verbindung auf Ubuntu 16.04, um SQL-Code in einem Container


## <a name="july-2018-july-public-preview"></a>Juli 2018 (Juli öffentliche Vorschau)

Veröffentlichungsdatum: 19. Juli 2018  
Version: 0.31.4

Die *Public Preview von Juli* liegt der Schwerpunkt auf dem ersten Release der Konfigurationsszenarien für den SQL Server-Agent, SQL Server Profiler-Sitzung und Ansicht-Vorlage Erweiterungen und weiteren Fehlerbehebungen für Kunden mit GitHub-Probleme gemeldet. Diese Version enthält die folgenden Highlights:  

- [SQL Server-Agent für SQL Operations Studio-Erweiterung](sql-server-agent-extension.md) Verbesserungen
 - Hinzugefügte Anzeigen von Warnungen, Operatoren und Proxys und Symbole auf der linken Seite
 - Hinzugefügte Dialogfelder zum neuen Auftrag, Neuer Auftragsschritt, neue Warnung und New-Operator
 - Hinzugefügte Auftrag löschen, Warnungen löschen und Delete-Operator (Rechtsklick)
 - Hinzugefügte vorherigen Ausführungen-Visualisierung
 - Zusätzliche Filter für jeden Spaltennamen
- [SQL Server Profiler für SQL Operations Studio-Erweiterung](sql-server-profiler-extension.md) Verbesserungen
 - Hinzugefügte Hotkeys schnell starten und Starten/Beenden von Profiler
 - 5 Standard Vorlagen zum Anzeigen von erweiterten Ereignissen hinzugefügt
 - Name der hinzugefügten Server-Datenbank-Verbindung
 - Unterstützung für Azure SQL-Datenbank-Instanzen
 - Hinzugefügte Vorschlag zu Profiler beenden, wenn die Registerkarte geschlossen wird, wenn der Profiler noch ausgeführt wird
- Version der Erweiterung für Skripts kombinieren
- Assistent "und" Dialogfeld-Erweiterungspunkte behandelt, die für Ersteller von Erweiterungen hinzugefügt
- Beheben Sie die GitHub-Probleme:
 - Beheben Sie [ausgeben 728](https://github.com/Microsoft/azuredatastudio/issues/728): keine Antwort auf Verbindung hinzufügen unter MacOS
 - Beheben Sie [ausgeben 1612](https://github.com/Microsoft/azuredatastudio/issues/1612): Ergebnisse-Raster Textanzeige bemerke ist, durch internationale Zeichen
 - Beheben Sie [1693 ausgeben](https://github.com/Microsoft/azuredatastudio/issues/1693): Backup-Dialogfeld: Benutzeroberfläche Dateibrowsers ist fehlerhaft
 - Beheben Sie [ausgeben 1713](https://github.com/Microsoft/azuredatastudio/issues/1713): Anzahl der betroffenen Zeilen
 - Beheben Sie [1718 ausgeben](https://github.com/Microsoft/azuredatastudio/issues/1718): Es konnte keine Verbindung mit jeder Datenquelle
 - Beheben Sie [ausgeben 1719](https://github.com/Microsoft/azuredatastudio/issues/1719): TypeError Herstellen der Verbindung mit Server
 - Beheben Sie [ausgeben 1724](https://github.com/Microsoft/azuredatastudio/issues/1724): Erweiterung Dialogfelder beendet haben
 - Beheben Sie [ausgeben 1749](https://github.com/Microsoft/azuredatastudio/issues/1749): Fehler: HTML-Daten in einer Spalte ruft interpretiert.
 - Beheben Sie [ausgeben 1789](https://github.com/Microsoft/azuredatastudio/issues/1789): Erweiterbarkeit: Wenn Sie über einen Verbindungsanbieter hinzufügen deinstallieren niemals entfernt sie aus der Liste
 - Beheben Sie [ausgeben 1791](https://github.com/Microsoft/azuredatastudio/issues/1791): Sqlops Extensions: queryeditor.connect() stellt eine Verbindung her in die Zieldatenbank, aber die Benutzeroberfläche zeigt keine Editor verbunden ist
 - Beheben Sie [1799 ausgeben](https://github.com/Microsoft/azuredatastudio/issues/1799): Diagramm der Datenbankgröße für Top-10 funktioniert nicht auf Groß-/ Kleinschreibung-Instanzen
 - Beheben Sie [ausgeben 1814](https://github.com/Microsoft/azuredatastudio/issues/1814): sqlops.d.ts Tippfehler verursacht implizite 'any'-Typdefinition
 - Beheben Sie [ausgeben 1817](https://github.com/Microsoft/azuredatastudio/issues/1817): Fehler de Ortografia
 - Beheben Sie [ausgeben 1830](https://github.com/Microsoft/azuredatastudio/issues/1830): IconPath in ButtonComponent festlegen, wenn component() aufgerufen wurde, ändert sich nicht auf das Symbol
 - Beheben Sie [ausgeben 1843](https://github.com/Microsoft/azuredatastudio/issues/1843): bessere tabellenorganisation


## <a name="june-2018-june-public-preview"></a>Juni 2018 (Juni-öffentliche Vorschau)

Veröffentlichungsdatum: 20. Juni 2018  
Version: 0.30.6

Die *öffentliche Vorschauversion von Juni* enthält die folgenden Highlights:  

- **SQL Server Profiler für SQL Operations Studio *Vorschau***  erste Version der Erweiterung.
- Die neue **SQL Data Warehouse** Erweiterung enthält umfangreiche anpassbar dashboardwidgets stellt Einblicke in Ihr Datawarehouse. Dies hebt die Sperre wichtige Szenarien zu verwalten und optimieren Ihr Datawarehouse, um sicherzustellen, dass sie für eine gleichbleibende Leistung optimiert ist.
- **Bearbeiten von Daten, die "Filtern und sortieren"** unterstützen.
- **SQL Server-Agent für SQL Operations Studio *Vorschau***  Erweiterung Verbesserungen für die Aufträge und Auftragsverlauf Ansichten.
- Verbesserte **-Assistent & Dialogfeld-Framework für UI-Builder** Erweiterbarkeits-APIs.
- Aktualisieren Sie die Integration von VS Code-Plattform Source Code [März 2018 (Version 1.22)](https://code.visualstudio.com/updates/v1_22) und [April 2018 (1,23)](https://code.visualstudio.com/updates/v1_23) frei.
- Beheben Sie die GitHub-Probleme:
  - Die Anforderung zur ([ausgeben 1204](https://github.com/Microsoft/azuredatastudio/issues/1204)): Bitte stellen Sie die Ergebnisse Breite des Rasters AutoAnpassen-Spalte mit Daten, und/oder manuelle Änderungen speichern, wenn dieselbe Abfrage erneut ausgeführt wird.
  - Beheben Sie [ausgeben 1398](https://github.com/Microsoft/azuredatastudio/issues/1398): sollten anzeigen hinzufügen, Nachricht, und fügen Sie der Schaltfläche "Konto-Konto" hinzu, wenn verknüpftes Konto leer ist.
  - Beheben Sie [ausgeben 1399](https://github.com/Microsoft/azuredatastudio/issues/1399): Registerkarte "verknüpfte Konto" wird unterbrochen, wenn die Ansicht reduziert wird.
  - Beheben Sie [ausgeben 1374](https://github.com/Microsoft/azuredatastudio/issues/1374): SQL Tools-Dienst stürzt ab, wenn Sie SQL-Datei vom Datenträger zu öffnen.
  - Beheben Sie [ausgeben 1372](https://github.com/Microsoft/azuredatastudio/issues/1372): fehlende SQL-Schlüsselwort "BETWEEN".
  - Beheben Sie [ausgeben 1395](https://github.com/Microsoft/azuredatastudio/issues/1395): "MATCH"-Schlüsselwort stürzt ab, SQL-Tools-Dienst.
  - Beheben Sie [ausgeben 1496](https://github.com/Microsoft/azuredatastudio/issues/1496): "Neuer Profiler" Kontextmenüoption im Objekt-Explorer hat keine Auswirkungen.
  - Beheben Sie [ausgeben 1495](https://github.com/Microsoft/azuredatastudio/issues/1495): Abfrage-Editor "Explain" Abfrageplan ist fehlerhaft.


## <a name="may-2018-may-public-preview"></a>Mai 2018 (öffentlichen Vorschau Mai)

Veröffentlichungsdatum: 7. Mai 2018  
Version: 0.29.3

Die *Public Preview kann* konzentriert sich auf die Stabilität und Fehlerbehebungen. Dieser Build enthält die folgenden Highlights:  

- Jetzt Redgate SQL Search-Erweiterung, die im Erweiterungs-Manager verfügbar.
- Community-Lokalisierung für 10 Sprachen verfügbar: Deutsch, Spanisch, Französisch, Italienisch, Japanisch, Koreanisch, Portugiesisch, Russisch, Chinesisch (vereinfacht) und Chinesisch (traditionell).
- Reduzierte Telemetrie-Erfassung, verbesserter teilnehmen und produktinterne Links zu Datenschutzbestimmungen.
- Erweiterungs-Manager verfügt über verbesserte Marketplace benutzerumgebung zur Community Extensions leicht zu erkennen.
- SQL Agent-Erweiterung Aufträge und Auftragsverlauf anzeigen, zur Verbesserung der.
- Updates für Whoisactive und Erweiterungen von Server-Berichte.
- Verbessern Sie die Dashboardeigenschaften verwalten scrollen.
- Beheben Sie die GitHub-Probleme:
   - Beheben Sie [ausgeben 703](https://github.com/Microsoft/azuredatastudio/issues/703): ähnlich wie HTML-Text eingeben, in das Bearbeiten von Daten wird Wert nicht ordnungsgemäß angezeigt wurde, bis die Aktualisierung
   - Beheben Sie [ausgeben 821](https://github.com/Microsoft/azuredatastudio/issues/821): azuredatastudio.deb paketabhängigkeit
   - Beheben Sie [ausgeben 1260](https://github.com/Microsoft/azuredatastudio/issues/1260): Schlüsselwort nicht 'distinct' hervorgehoben
   - Beheben Sie [ausgeben 1332](https://github.com/Microsoft/azuredatastudio/issues/1332): Bearbeiten von Daten wiederherstellen Zeile funktioniert nicht
   - Beheben Sie [ausgeben 1215](https://github.com/Microsoft/azuredatastudio/issues/1215): SQL-Agent-Erweiterung und der Statusleiste
   - Beheben Sie [ausgeben 1316](https://github.com/Microsoft/azuredatastudio/issues/1316): SQL-Agent nicht ändern der Größe nach Windows-Größe ändern




## <a name="april-2018-april-public-preview"></a>April 2018 (April-öffentliche Vorschau)

Veröffentlichungsdatum: 25 April 2018  
Version: 0.28.6

Die *Public Preview-Version April* enthält Fehlerbehebungen und Verbesserungen. 

- Verbesserungen an der Vorschau von SQL-Agent-Erweiterung.
- Verbesserte dateiunterstützung für große und geschützte für das Speichern geschützter Administrator und > 256M-Dateien in SQL Operations Studio.
- Integriertes Terminal aufteilen, um mit mehreren open Terminals auf einmal zu arbeiten.
- Reduzierte Installation Datei auf dem Datenträger Anzahl Foot für schnellere Installationen und Startzeiten drucken.
- Weiter mit GitHub-Probleme zu beheben:
   - Beheben [ausgeben 37](https://github.com/Microsoft/azuredatastudio/issues/37): bei der Diagramm-Viewer auf einen Fehler ausgibt, unerwartetes Verhalten auftritt.
   - Beheben Sie [ausgeben 462](https://github.com/Microsoft/azuredatastudio/issues/462): Feature wünschen: Option für Server-Gruppen werden standardmäßig erweitert werden.
   - Beheben Sie [ausgeben 606](https://github.com/Microsoft/azuredatastudio/issues/606): Intellisense - ungültige Vorschlag für Befehl 'update'.
   - Beheben Sie [ausgeben 967](https://github.com/Microsoft/azuredatastudio/issues/967): erwarten, dass der Abfrageplan Wenn XML-Showplan im Ergebnisraster auswählen.
   - Beheben Sie [ausgeben 1023](https://github.com/Microsoft/azuredatastudio/issues/1023): Hinzufügen von eckigen Klammern für Ms_foreachdb Aufruf aus Flyfishingdba.
   - Beheben Sie [ausgeben 1048](https://github.com/Microsoft/azuredatastudio/issues/1048): vor der Anmeldung SSL/TLS-Handshake-Fehler.
   - Beheben Sie [ausgeben 1050](https://github.com/Microsoft/azuredatastudio/issues/1050): klar Einblicke vor dem Fehler anzeigen.
   - Beheben Sie [1057 ausgeben](https://github.com/Microsoft/azuredatastudio/issues/1057): Restore "und" neue Abfrageaktionen in der Explorer-Widget werden unterbrochen.
   - Beheben Sie [1068 ausgegeben](https://github.com/Microsoft/azuredatastudio/issues/1068): Dashboard Ausgabe Windows Pops oben mit Fehlermeldung zur Azure SQL-Datenbank.
   - Beheben Sie [ausgeben 1069](https://github.com/Microsoft/azuredatastudio/issues/1069): Dialogfeld "Verbindung" zeigt Server erforderlich, Fehler bei der ersten Anzeige.
   - Beheben Sie [ausgeben 1070](https://github.com/Microsoft/azuredatastudio/issues/1070): Server-Gruppen erfordern jetzt ein Doppelklick zu erweitern.
   - Beheben Sie [ausgeben 1072](https://github.com/Microsoft/azuredatastudio/issues/1072): Auswahlsteuerelement Hintergrund ist teilweise transparent.
   - Beheben Sie [ausgeben 1115](https://github.com/Microsoft/azuredatastudio/issues/1115): Beheben von Probleme mit der Barrierefreiheit in SQL Operations Studio für alle hohen Kontrast.
   - Beheben Sie [ausgeben 1101](https://github.com/Microsoft/azuredatastudio/issues/1101): Erweiterung ein Fehler auftritt, Upgrade "herunterladen Manually" Link wird am falschen Ort.
   - Beheben Sie [ausgeben 1103](https://github.com/Microsoft/azuredatastudio/issues/1103): V Scrollen funktioniert nicht auf der Registerkarte Home.
   - Beheben Sie [ausgeben 1104](https://github.com/Microsoft/azuredatastudio/issues/1104): Registerkarten für die Erweiterung von SQL nicht mehr funktioniert.


Eine erhebliche Hervorhebung für die öffentliche Vorschau von April ist der Visual Studio Code 1.21 Plattform Quelle Code aktualisieren. Dadurch erhalten Sie mehrere Updates für die Kern-Editor und die Workbench aus der vorherigen 1.19 verfügt über Synchronisierungspunkt. Die folgenden: Beispiele

- [Benutzeroberfläche für neue Benachrichtigungen](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui) – leicht zu verwalten und überprüfen Sie SQL Operations Studio-Benachrichtigungen.
- [Integrierte Terminal aufteilen](https://code.visualstudio.com/updates/v1_21#_split-terminals) -arbeiten mit mehreren open Terminals gleichzeitig.
- [Speichern von großen und geschützte Dateien](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges) – speichert Admin geschützt und > 256 M-Dateien in SQL Operations Studio.
- [Verbesserte Unterstützung für große Datei](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements) -Text-Puffer-Optimierungen für große Dateien.
- [Verbesserte Suche der Einstellungen](https://code.visualstudio.com/updates/v1_20#_settings-search) - leichter finden Sie die richtige Einstellung mit der Suche in natürlicher Sprache.
- [Globale Codeausschnitte](https://code.visualstudio.com/updates/v1_20#_global-snippets) -Ausschnitte, die für alle Dateitypen können erstellen.
- [Mehrfachauswahl Explorer](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer) -Aktionen für mehrere Dateien gleichzeitig ausführen.
- [Fehler und Warnungen im Explorer](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer) – schnell zu Fehlern in Ihrer Codebasis navigieren.
- [Ziehen und ablegen, kopieren und fügen Sie in Windows](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support) : Verschieben von Dateien zwischen geöffneten SQL Operations Studio-Fenster.
- [Unterstützung für Git-submodul](https://code.visualstudio.com/updates/v1_20#_git-submodules) -Ausführen von Git-Vorgänge für geschachtelte Git-Repositorys.
- [Unterstützung für die Terminaldienste Sprachausgabe](https://code.visualstudio.com/updates/v1_20#_screen-reader-support) -integriertes Terminal verfügt jetzt über Modus "Bildschirm Reader optimiert".
- [Zentriert Editor Layout](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout) – codeänderungen anzeigen Bildschirmfläche zu maximieren.
- [Horizontale Suchergebnisse (Vorschau)](https://code.visualstudio.com/updates/v1_21#_horizontal-search) – Sie können jetzt Anzeigen der Suchergebnisse in einem horizontalen Bereich angezeigt.

Weitere Informationen: Auschecken der [Visual Studio Code Februar-Release Notes](https://code.visualstudio.com/updates/v1_21), und die [Visual Studio Code Januar – Versionsanmerkungen](https://code.visualstudio.com/updates/v1_20).

Weitere Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md).

## <a name="march-2018-march-public-preview"></a>März 2018 (März öffentliche Vorschau)

Veröffentlichungsdatum: 28. März 2018  
Version: 0.27.3

Die *öffentliche Vorschau März* weiterhin die wichtigsten GitHub-Probleme zu beheben und konzentriert sich auf die Verbesserung unserer Geschichte Erweiterbarkeit. Insbesondere Erweiterungs-Manager aktivieren, Verbessern der dashboardverwaltung und Bereitstellen von SQL-Agent "und" Insights-Erweiterungen. Dieses Release enthält die folgenden Verbesserungen:

- Erweitern Sie das Dashboard-Erweiterbarkeitsmodell Unterstützung im Registerkartenformat Einblicke und Bereiche der Konfiguration.
   - Erweiterungs-Manager ermöglicht die einfache Übernahme von Erweiterungen.
   - Dashboard-Erweiterungen für Sp_whoisactive aus [whoisactive.com](http://www.whoisactive.com).
   - Weitere Informationen finden Sie unter [erweitern die Funktionalität von SQL Operations Studio](extensions.md).
- Hinzufügen zusätzlicher [Erweiterbarkeits-APIs für die Verbindung und Objekt-Explorer](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API) Management.
- Beheben Sie wichtige Auswirkungen auf Kunden weiterhin [GitHub-Problemen](https://github.com/Microsoft/azuredatastudio/issues).


## <a name="february-2018-february-public-preview"></a>Februar 2018 (Februar öffentliche Vorschau)

Veröffentlichungsdatum: 15. Februar 2018  
Version: 0.26.7

Die *Public Preview-Version vom Februar* enthält einige Vorschläge für Features und Fehlerkorrekturen hoher Priorität. Dieses Release enthält die folgenden Verbesserungen:

- Einführung in die automatische Update-Installation, die stellt eine Benachrichtigung bereit, wenn eine neue Version als download verfügbar ist. 
- Das Dialogfeld "Verbindung" 'Datenbank'-Feld ist jetzt eine dynamisch aufgefüllt Dropdown-Liste, die eine Liste der Datenbanken aufgefüllt, die vom angegebenen Server enthält.
- Beheben Sie [Problem 6](https://github.com/Microsoft/azuredatastudio/issues/6): Verbindung und der ausgewählten Datenbank beibehalten, wenn Sie neue Registerkarten der Abfrage zu öffnen.
- Beheben Sie [ausgeben 22](https://github.com/Microsoft/azuredatastudio/issues/22): "Server Name" und "Database Name" – können Sie diese Dropdownlisten anstelle von Textfeldern werden?
- Beheben Sie [ausgeben 549](https://github.com/Microsoft/azuredatastudio/issues/549): Silent/sehr automatische Installation führt Anwendung nach der Installation öffnen.
- Beheben Sie [ausgeben 481](https://github.com/Microsoft/azuredatastudio/issues/481): Fügen Sie die Option "Nach Updates suchen".
- Farbliche Kennzeichnung von SQL-Editor und automatische Vervollständigung Fixes:
   - Beheben Sie [ausgeben 584](https://github.com/Microsoft/azuredatastudio/issues/584): Schlüsselwort "FULL", nicht hervorgehoben von IntelliSense.
   - Beheben Sie [ausgeben 345](https://github.com/Microsoft/azuredatastudio/issues/345): farbigen Anzeigen von SQL-Funktionen im Editor.
   - Beheben Sie [ausgeben 300](https://github.com/Microsoft/azuredatastudio/issues/300): [#tempData] letzte "]" wird grün angezeigt.
   - Beheben Sie [ausgeben 225](https://github.com/Microsoft/azuredatastudio/issues/225): Schlüsselwort Farben stimmen nicht überein.
   - Beheben Sie [ausgeben 60](https://github.com/Microsoft/azuredatastudio/issues/60): Ungültige Sql Farbe syntaxhervorhebung bei Verwendung der temporären Tabelle in from-Klausel.
- Führen Sie die Verbindung Erweiterbarkeits-API.
- VS Code-Editor 1.19-Integration.
- Aktualisieren Sie JustinPealing/html-Abfrageplan Komponente einfachere Installation mehrere Verbesserungen der Abfrageplan-Viewer.


## <a name="january-2018-january-public-preview"></a>Januar 2018 (Januar öffentliche Vorschau)

Veröffentlichungsdatum: 17 Januar 2018  
Version: 0.25.4

Die *Public Preview Januar* enthält einige Vorschläge für Features und Fehlerkorrekturen hoher Priorität. Dieses Release enthält die folgenden Verbesserungen:

- Gespeicherten serververbindungen finden im Verbindungsdialogfeld.
- Aktivieren von "Hot" beenden. Beenden von "Hot" ist standardmäßig deaktiviert, finden Sie unter aktivieren ["Hot" Exit-Einstellung](settings.md#hot-exit).
- Registerkartenfärbung basierend auf Gruppe "Server". Registerkartenfärbung ist standardmäßig deaktiviert, finden Sie unter aktivieren [Registerkarte die Einstellung für die](settings.md#tab-color).
- Änderung *Servernamen* zu *Server* im Verbindungsdialogfeld.
- Korrektur unterteilt *aktuelle Abfrage ausführen* Befehl.
- Beheben Sie die Drag & Drop-wichtige Fehler Skripterstellung.
- Korrigieren Sie falsche angeheftete Menü "Start"-Symbol.
- Beheben Sie fehlende branding Symbol "Azure-Konto an.


## <a name="december-2017-december-public-preview"></a>Dezember 2017 (Dezember öffentliche Vorschau)

Veröffentlichungsdatum: 19. Dezember 2017  
Version: 0.24.1

Die *Public Preview-Version Dezember* umfasst verschiedene Fehlerkorrekturen für alle Featurebereiche sowie die folgenden Verbesserungen:

- Erstellen Sie Dialogfeld Firewallregeln ist jetzt bei der verbindungsherstellung mit Azure SQL-Datenbank und Azure SQL Data Warehouse verfügbar.
- Zusätzliche Windows-Setup und Linux DEB und RPM-Pakete für die Installation.
- Verwalten Sie Dashboard visuelle Layout-Editor.
- *Alter-Skript als* und *Ausführen von Skripts als* Befehle.
- *Führen Sie die aktuelle Abfrage mit Istplan* Befehl.
- Integrieren Sie Visual Studio Code 1.18.1-Editor-Plattform.
- Aktivieren Sie Sideload-VSIX-Erweiterung-Dateien.
- "GO-N" Batch-Iterationssyntax zu unterstützen.


## <a name="november-2017"></a>November 2017

Veröffentlichungsdatum: 15. November 2017  
Version: 0.23.6

- Erste Version des [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Nächste Schritte

Finden Sie in der folgenden schnellstartanleitungen für den Einstieg:
- [Verbinden und Abfragen von SQLServer](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verbinden und Abfragen von Azure Datawarehouse](quickstart-sql-dw.md)

Mitwirken an [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
