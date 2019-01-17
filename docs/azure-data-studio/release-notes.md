---
title: Anmerkungen zu dieser Version und das Änderungsprotokoll
titleSuffix: Azure Data Studio
description: Versionshinweise zu Azure Data Studio
ms.custom: seodec18
ms.date: 01/17/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 163f5740626b0f4cb927272d46acddc79495e4c1
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361680"
---
# <a name="azure-data-studio-latest-release-notes-and-changelog"></a>Azure Data Studio neuesten Anmerkungen zu dieser Version und das Änderungsprotokoll

**[Herunterladen Sie und installieren Sie die neueste Version.](download.md)**


## <a name="january-hotfix-2019-january-hotfix-release"></a>Hotfix für Januar 2019 (Januar-Hotfix-Version)

Veröffentlichungsdatum: 16 Januar 2019  
version: 1.3.9

Version 1.3.9 behebt einige Probleme, die in 1.3.8 ermittelt wurden. Weitere Informationen finden Sie unter [Hotfix-Release aus Januar](https://github.com/Microsoft/azuredatastudio/milestone/24?closed=1).

Ausführliche Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), und [Versionen](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="january-2019-january-release"></a>Januar 2019 (Januar-Version)

Veröffentlichungsdatum: 09 Januar 2019  
version: 1.3.8

- Einen neuen Benutzer Installer für Windows wird hinzugefügt. Im Gegensatz zu den vorhandenen System-Webinstaller erfordert das Installationsprogramm für neue Benutzer keine Administratorrechte. Dies ermöglicht auch ein einfacher Upgradeverhalten für nicht-Administratoren.
- Unterstützung für Azure Active Directory-Authentifizierung.
- Hiermit kündigen wir Idera SQL DM Performance Insights (Vorschau).
- Datenebenen-Anwendungs-Assistent-Unterstützung in SQL Server-Import-Erweiterung.
- Aktualisieren Sie auf die [2019-Vorschau von SQL Server-Erweiterung](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)
- Verbesserungen für SQL Server Profiler.
- Führt das Streaming für große Abfragen (Vorschau).
- Community Extensions: Sp_executesql to Sql und die neue Datenbank.
- Aufgelöst [Fehler und Probleme](https://github.com/Microsoft/azuredatastudio/milestone/19?closed=1).

## <a name="november-2018-november-release"></a>November 2018 (Version November)

Veröffentlichungsdatum: 6 November 2018  
version: 1.2.4

- Aktualisieren Sie auf die [2019-Vorschau von SQL Server-Erweiterung](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)
- Einführung in fügen Sie der Plans-Erweiterung
- Einführung in High Color Abfragen Erweiterungen, einschließlich SSMS-Editor-Design
- Fehlerbehebungen in SQL Server-Agent, Profiler und Import-Erweiterungen
- Beheben von.NET Core Socket KeepAlive Problem verursacht, inaktive Verbindungen auf MacOS gelöscht
- Upgrade SQL Tools-Diensts zur.NET Core-2.2-Preview 3 (für "Eventual" AAD-Unterstützung)

### <a name="bug-fixes"></a>Fehlerbehebungen

- Beheben Sie [Problem #2933](https://github.com/Microsoft/azuredatastudio/issues/2933): Die Verbindung wurde getrennt, zur Azure SQL-Datenbank
- Beheben Sie [Problem #2914](https://github.com/Microsoft/azuredatastudio/issues/2914): "Ungültige Argument" Ausnahme erweiterbare OE-Datenbank-Knoten
- Beheben Sie [Problem #2935](https://github.com/Microsoft/azuredatastudio/pull/2935): Mehrzeilige Nachrichten richtig angezeigt, in den Abfrageergebnissen
- Beheben Sie [Problem #2906](https://github.com/Microsoft/azuredatastudio/pull/2906): Beheben Sie Dokumentname Daten bearbeiten, wenn Tabellennamen Sonderzeichen enthält.
- Beheben Sie [Problem #2929](https://github.com/Microsoft/azuredatastudio/issues/2929): Erstellt in der Erweiterung Änderungsprotokoll sagt, um den Anmerkungen zur Version von VSCode für die Änderungen zu überprüfen
- Beheben Sie [Problem #2719](https://github.com/Microsoft/azuredatastudio/issues/2719): Design "hoher Kontrast" Doubles/Tripeln Symbole
- Beheben Sie [Problem #3047](https://github.com/Microsoft/azuredatastudio/pull/3047): Fügen Sie eine Befehlszeilenschnittstelle für die Verbindung mit einer SQL Server
- Beheben Sie [Problem #3031](https://github.com/Microsoft/azuredatastudio/pull/3031): Abfrage-Plan-Design-Unterstützung hinzufügen
- ...

## <a name="october-2018-october-release"></a>Oktober 2018 (Oktober-Version)

Veröffentlichungsdatum: 29. Oktober 2018  
version: 1.1.4

- Einführung in die Azure-Ressourcen-Explorer zum Durchsuchen von Azure SQL-Datenbanken
- Die Objekt-Explorer und Abfrage-Editor-Konnektivität Robustheit
- Verbesserungen für SQL-Agent-Erweiterungen
- Aktualisieren Sie auf die [2019-Vorschau von SQL Server-Erweiterung](https://docs.microsoft.com/sql/azure-data-studio/sql-server-2019-extension?view=sql-server-ver15)

### <a name="bug-fixes"></a>Fehlerbehebungen
- Beheben Sie [Problem #2717](https://github.com/Microsoft/azuredatastudio/issues/2717): Ergebnis der XML-Spalte, klicken Sie auf Formatierung
- Beheben Sie [Problem #2993](https://github.com/Microsoft/azuredatastudio/issues/2993): Die Breite des Ergebnisses Windows ist unvollständig
- Beheben Sie [Problem #2999](https://github.com/Microsoft/azuredatastudio/issues/2999): System.Diagnostics.Tracing-Datei auf dem Mac konnte nicht geladen werden, Herstellen der Verbindung mit Datenbank
- Beheben Sie [Problem #2851](https://github.com/Microsoft/azuredatastudio/issues/2851): Zeitreihen-Diagramm wird nicht ordnungsgemäß gerendert.
- Beheben Sie [Problem #2996](https://github.com/Microsoft/azuredatastudio/issues/2996): Temporäre Tabelle Datenverlust aufgrund von plötzlichen sitzungsänderung
- ...

Ausführliche Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), und [Versionen](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="september-2018-september-ga-release"></a>September 2018 (September GA-Version)

Veröffentlichungsdatum: 24. September 2018  
version: 1,0

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
  - SQL Server-PolyBase Erstellen externer Tabellen-Assistent
    - Erstellen Sie eine externe Tabelle und die unterstützenden Systemmetadaten-Strukturen mit einer benutzerfreundlichen Assistenten an. In dieser Version werden die SQL Server- und Oracle-Remoteserver unterstützt.
- Fragen Sie Ergebnisraster Verbesserungen der Leistung und UX für große Anzahl von Resultsets.
- Visual Studio Code-Quellcode Aktualisieren von "1,23", um 1.26.1 mit Rasterlayout und verbesserte-Einstellungs-Editor (Vorschau).
- Verbesserungen der Barrierefreiheit für die Sprachausgabe und Tastaturnavigation mit hohem Kontrast.
- Hinzugefügt `Connection name` Option aus, um einen alternativen Anzeigenamen in der Ansicht-Let-Server angeben.

### <a name="bug-fixes"></a>Fehlerbehebungen

- Beheben Sie [Problem #2647](https://github.com/Microsoft/azuredatastudio/issues/143): Die Diagramme hat einen großen Schritt rückwärts.
- Beheben Sie [Problem #2648](https://github.com/Microsoft/azuredatastudio/issues/143): Wählen Sie, die eine JSON-links auf die gesamte Spalte zurückgibt.
- ...

Ausführliche Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), und [Versionen](https://github.com/Microsoft/azuredatastudio/releases).


## <a name="august-2018-august-public-preview"></a>August 2018 (öffentliche Vorschau für August)

Veröffentlichungsdatum: 30. August 2018  
version: 0.32.8

*0.32.8 bietet Korrekturen für einige Regressionen finden Sie im 0.32.7 ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971), [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372)*)

Die *öffentliche Vorschau für August* Fehlerbehebungen, Produkt Stabilisierung und Auffüllen der Lücken in vorhandenen Szenarios im Mittelpunkt.  

- Ankündigung der SQL Server-Import-Erweiterungs
- SQL Server Profiler-sitzungsverwaltung
- Unterstützung für die Vorlage von SQL Server Profiler-Sitzungen
- SQL Server-Agent-Verbesserungen
- Neue Community-Erweiterung: Erste-Responder-kit
- Verbesserungen bei der Quality Of Life: Verbindungszeichenfolgen

### <a name="bug-fixes"></a>Fehlerbehebungen

- Analysieren von SQL-Code in einem Abfrage-Editor-Fenster mit den `Parse Syntax` Befehl.
- Beheben Sie [Problem #143](https://github.com/Microsoft/azuredatastudio/issues/143): Doppelklicken Sie auf keine Variable-Name auswählen.
- Beheben Sie [Problem #387](https://github.com/Microsoft/azuredatastudio/issues/387): SQL DB Registerkartensymbol ist rot.
- Beheben Sie [Problem #825](https://github.com/Microsoft/azuredatastudio/issues/825): Anforderung: Automatisch verbinden, aktuellen Server nach dem Skript für Objekttyp als... 
- Beheben Sie [Problem #1278](https://github.com/Microsoft/azuredatastudio/issues/1278): sqlops.desktop [Desktop Entry -] redundante Wert für Name der & Kommentar.
- Beheben Sie [Problem #1285](https://github.com/Microsoft/azuredatastudio/issues/1285): Bewirkt, dass Anwendungssymbol sollen entfernt/ersetzt in Windows wird aktualisiert.
- Beheben Sie [Problem #1317](https://github.com/Microsoft/azuredatastudio/issues/1317): Beheben Sie das Dezimaltrennzeichen.
- Beheben Sie [Problem #1474](https://github.com/Microsoft/azuredatastudio/issues/1474): Verbindung von "Abbrechen" ändern trennt die aktuellen Verbindung.
- Beheben Sie [Problem #1497](https://github.com/Microsoft/azuredatastudio/issues/1497): Zeigen Sie als Diagramm Optionen unten abgeschnitten werden.
- Beheben Sie [Problem #1524](https://github.com/Microsoft/azuredatastudio/issues/1524): Shell/Dashboard: Main Viewlet Symbole sind ziehbare und können die app abstürzt.
- Beheben Sie [Problem #1578](https://github.com/Microsoft/azuredatastudio/issues/1578): Kann nicht zum Erweitern/Remotedatei Browserordner reduzieren, indem Sie Sie auf den Namen.
- Beheben Sie [Problem #1620](https://github.com/Microsoft/azuredatastudio/issues/1620): Vorschlag für eine Funktion: Rufen Sie Verbindungszeichenfolge für die vorhandene Verbindung aus.
- Beheben Sie [Problem #1624](https://github.com/Microsoft/azuredatastudio/issues/1624): Farbe wenn deaktiviert nicht zu verwendenden ändern.
- Beheben Sie [Problem #1728](https://github.com/Microsoft/azuredatastudio/issues/1728): Speichern Sie als JSON/EXCEL/CSV-Datei funktioniert nicht.
- Beheben Sie [Problem #1744](https://github.com/Microsoft/azuredatastudio/issues/1744): Bereich "Ergebnisse" die Bildlauf Positionen gehen verloren, beim Wechseln zwischen Registerkarten.
- Beheben Sie [Problem #1748](https://github.com/Microsoft/azuredatastudio/issues/1748): Fehlermeldung beim Speichern des Zeitpunkts der Excel-Datei, die zweite (und alle nachfolgenden).
- Beheben Sie [Problem #1782](https://github.com/Microsoft/azuredatastudio/issues/1782): Bearbeiten von Daten: Zelle nicht auf den ursprünglichen Wert auf das Drücken der ESC-Taste zurückgesetzt.
- Beheben Sie [Problem #1836](https://github.com/Microsoft/azuredatastudio/issues/1836): SQL-Dateien, die nicht mit SQL Operations Studio verknüpft sind.
- Beheben Sie [Problem #1850](https://github.com/Microsoft/azuredatastudio/issues/1850): Eingabe N'' automatisch vervollständigt, n '''.
- Beheben Sie [Problem #1985](https://github.com/Microsoft/azuredatastudio/issues/1985): Kopieren aus dem Raster mit Abfrageergebnissen ist deaktiviert, indem 1 Spalte.
- Beheben Sie [Problem #1998](htpts://github.com/Microsoft/azuredatastudio/pull/1998): Visual Studio Code-Version um zum Dialogfeld hinzufügen.
- Beheben Sie [Problem #2042](https://github.com/Microsoft/azuredatastudio/pull/2042): -Agent: Aktiviert die Schaltfläche, um Abfragen von Sql-Dateien importieren.
- Beheben Sie [Problem #2091](https://github.com/Microsoft/azuredatastudio/issues/2091): STRG + C-Verknüpfung kann nicht verwenden werden, um aus den Ergebnisbereich zu kopieren.
- Beheben Sie [Problem #2099](https://github.com/Microsoft/azuredatastudio/pull/2099): Weitere SaveAsCsv-Optionen hinzugefügt.
- Beheben Sie [Problem #2107](https://github.com/Microsoft/azuredatastudio/issues/2107): Symbol "Dokument" für Dashboards und der Profiler-Dokumente zu aktualisieren.
- Beheben Sie [Problem #2129](https://github.com/Microsoft/azuredatastudio/pull/2129): Speichern Sie beim Wechseln von Registerkarten bearbeiten Daten Bildlaufposition.
- Beheben Sie [Problem #2152](https://github.com/Microsoft/azuredatastudio/issues/2152): Ergebnisse Zeile des Datenblatts Indikator 0 (null) basiert.

### <a name="known-issues"></a>Bekannte Probleme

- [Problem #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) speichern als erste Zeile der Daten nur speichert Excel
- [Problem #2150](https://github.com/Microsoft/azuredatastudio/issues/2150): Es konnte keine Verbindung auf Ubuntu 16.04, um SQL-Code in einem container


## <a name="july-2018-july-public-preview"></a>Juli 2018 (Juli öffentliche Vorschau)

Veröffentlichungsdatum: Am 19. Juli 2018  
version: 0.31.4

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
 - Beheben Sie [ausgeben 728](https://github.com/Microsoft/azuredatastudio/issues/728): Keine Antwort auf Verbindung hinzufügen unter macOS
 - Beheben Sie [ausgeben 1612](https://github.com/Microsoft/azuredatastudio/issues/1612): Ergebnisse-Raster Textanzeige wird durch internationale Zeichen abgelegte.
 - Beheben Sie [ausgeben 1693](https://github.com/Microsoft/azuredatastudio/issues/1693): Dialogfeld "Sicherung": Dateibrowser UI ist fehlerhaft
 - Beheben Sie [ausgeben 1713](https://github.com/Microsoft/azuredatastudio/issues/1713): Anzahl der betroffenen Zeilen
 - Beheben Sie [ausgeben 1718](https://github.com/Microsoft/azuredatastudio/issues/1718): Es konnte keine Verbindung mit jeder Datenquelle
 - Beheben Sie [ausgeben 1719](https://github.com/Microsoft/azuredatastudio/issues/1719): TypeError Herstellen der Verbindung mit Server
 - Beheben Sie [ausgeben 1724](https://github.com/Microsoft/azuredatastudio/issues/1724): Erweiterung Dialogfelder beendet haben
 - Beheben Sie [ausgeben 1749](https://github.com/Microsoft/azuredatastudio/issues/1749): BUG: HTML-Daten in einer Spalte ruft interpretiert.
 - Beheben Sie [ausgeben 1789](https://github.com/Microsoft/azuredatastudio/issues/1789): Erweiterbarkeit: Wenn Sie über einen Verbindungsanbieter hinzufügen wird deinstallieren nie es aus der Liste entfernen
 - Beheben Sie [ausgeben 1791](https://github.com/Microsoft/azuredatastudio/issues/1791): Sqlops Erweiterungen: queryeditor.connect() verbinden, in die Zieldatenbank jedoch Benutzeroberfläche wird nicht angezeigt, ob der Editor verbunden ist.
 - Beheben Sie [ausgeben 1799](https://github.com/Microsoft/azuredatastudio/issues/1799): Diagramm der obersten 10 DB funktioniert nicht auf Instanzen von Groß-/Kleinschreibung beachten
 - Beheben Sie [ausgeben 1814](https://github.com/Microsoft/azuredatastudio/issues/1814): sqlops.d.ts Tippfehler verursacht implizite 'any'-Typdefinition
 - Beheben Sie [ausgeben 1817](https://github.com/Microsoft/azuredatastudio/issues/1817): Fehler beim de Ortografia
 - Beheben Sie [ausgeben 1830](https://github.com/Microsoft/azuredatastudio/issues/1830): IconPath in ButtonComponent festlegen, nach dem Aufruf von component() ändert nicht das Symbol
 - Beheben Sie [ausgeben 1843](https://github.com/Microsoft/azuredatastudio/issues/1843): Eine bessere Organisation von Tabellen


## <a name="june-2018-june-public-preview"></a>Juni 2018 (Juni-öffentliche Vorschau)

Veröffentlichungsdatum: 20. Juni 2018  
version: 0.30.6

Die *öffentliche Vorschauversion von Juni* enthält die folgenden Highlights:  

- **SQL Server Profiler für SQL Operations Studio *Vorschau***  erste Version der Erweiterung.
- Die neue **SQL Data Warehouse** Erweiterung enthält umfangreiche anpassbar dashboardwidgets stellt Einblicke in Ihr Datawarehouse. Dies hebt die Sperre wichtige Szenarien zu verwalten und optimieren Ihr Datawarehouse, um sicherzustellen, dass sie für eine gleichbleibende Leistung optimiert ist.
- **Bearbeiten von Daten, die "Filtern und sortieren"** unterstützen.
- **SQL Server-Agent für SQL Operations Studio *Vorschau***  Erweiterung Verbesserungen für die Aufträge und Auftragsverlauf Ansichten.
- Verbesserte **-Assistent & Dialogfeld-Framework für UI-Builder** Erweiterbarkeits-APIs.
- Aktualisieren Sie die Integration von VS Code-Plattform Source Code [März 2018 (Version 1.22)](https://code.visualstudio.com/updates/v1_22) und [April 2018 (1,23)](https://code.visualstudio.com/updates/v1_23) frei.
- Beheben Sie die GitHub-Probleme:
  - Die Anforderung zur ([ausgeben 1204](https://github.com/Microsoft/azuredatastudio/issues/1204)): Bitte nehmen Sie die Ergebnisse AutoAnpassen-Spalte Rasterbreite an Daten und/oder speichern Sie manuelle Änderungen, wenn dieselbe Abfrage erneut ausgeführt wird.
  - Beheben Sie [ausgeben 1398](https://github.com/Microsoft/azuredatastudio/issues/1398): Sollte anzeigen Nachricht hinzufügen, und fügen Sie der Schaltfläche "Konto-Konto" hinzu, wenn verknüpftes Konto leer ist.
  - Beheben Sie [ausgeben 1399](https://github.com/Microsoft/azuredatastudio/issues/1399): Registerkarte "verknüpfte Konto" ist unterbrochen, wenn die Ansicht reduziert wird.
  - Beheben Sie [ausgeben 1374](https://github.com/Microsoft/azuredatastudio/issues/1374): SQL Tools-Dienst stürzt ab, wenn Sie SQL-Datei vom Datenträger zu öffnen.
  - Beheben Sie [ausgeben 1372](https://github.com/Microsoft/azuredatastudio/issues/1372): SQL-Schlüsselwort "BETWEEN" fehlt.
  - Beheben Sie [ausgeben 1395](https://github.com/Microsoft/azuredatastudio/issues/1395): "MATCH"-Schlüsselwort stürzt SQL Tools-Dienst ab.
  - Beheben Sie [ausgeben 1496](https://github.com/Microsoft/azuredatastudio/issues/1496): "Neuer Profiler" Option für das Kontextmenü im Objekt-Explorer hat keine Auswirkungen.
  - Beheben Sie [ausgeben 1495](https://github.com/Microsoft/azuredatastudio/issues/1495): Abfrage-Editor "Explain" Abfrageplan ist unterbrochen.


## <a name="may-2018-may-public-preview"></a>Mai 2018 (öffentlichen Vorschau Mai)

Veröffentlichungsdatum: 7. Mai 2018  
version: 0.29.3

Die *Public Preview kann* konzentriert sich auf die Stabilität und Fehlerbehebungen. Dieser Build enthält die folgenden Highlights:  

- Jetzt Redgate SQL Search-Erweiterung, die im Erweiterungs-Manager verfügbar.
- Community-Lokalisierung für 10 Sprachen verfügbar: Deutsch, Spanisch, Französisch, Italienisch, Japanisch, Koreanisch, Portugiesisch, Russisch, vereinfachtes Chinesisch und traditionelles Chinesisch.
- Reduzierte Telemetrie-Erfassung, verbesserter teilnehmen und produktinterne Links zu Datenschutzbestimmungen.
- Erweiterungs-Manager verfügt über verbesserte Marketplace benutzerumgebung zur Community Extensions leicht zu erkennen.
- SQL Agent-Erweiterung Aufträge und Auftragsverlauf anzeigen, zur Verbesserung der.
- Updates für Whoisactive und Erweiterungen von Server-Berichte.
- Verbessern Sie die Dashboardeigenschaften verwalten scrollen.
- Beheben Sie die GitHub-Probleme:
   - Beheben Sie [ausgeben 703](https://github.com/Microsoft/azuredatastudio/issues/703): Ähnlich wie HTML-Text eingeben, in das Bearbeiten von Daten wird Wert nicht ordnungsgemäß angezeigt wurde, bis die Aktualisierung
   - Beheben Sie [ausgeben 821](https://github.com/Microsoft/azuredatastudio/issues/821): azuredatastudio.deb paketabhängigkeit
   - Beheben Sie [ausgeben 1260](https://github.com/Microsoft/azuredatastudio/issues/1260): Schlüsselwort 'distinct' nicht hervorgehoben.
   - Beheben Sie [ausgeben 1332](https://github.com/Microsoft/azuredatastudio/issues/1332): Bearbeiten Sie Daten wiederherstellen Zeile funktioniert nicht
   - Beheben Sie [ausgeben 1215](https://github.com/Microsoft/azuredatastudio/issues/1215): SQL Agent-Erweiterung und der Statusleiste
   - Beheben Sie [ausgeben 1316](https://github.com/Microsoft/azuredatastudio/issues/1316): Größe der SQL-Agent nicht nach Windows-Größe ändern




## <a name="april-2018-april-public-preview"></a>April 2018 (April-öffentliche Vorschau)

Veröffentlichungsdatum: 25 April 2018  
version: 0.28.6

Die *Public Preview-Version April* enthält Fehlerbehebungen und Verbesserungen. 

- Verbesserungen an der Vorschau von SQL-Agent-Erweiterung.
- Verbesserte dateiunterstützung für große und geschützte für das Speichern geschützter Administrator und > 256M-Dateien in SQL Operations Studio.
- Integriertes Terminal aufteilen, um mit mehreren open Terminals auf einmal zu arbeiten.
- Reduzierte Installation Datei auf dem Datenträger Anzahl Foot für schnellere Installationen und Startzeiten drucken.
- Weiter mit GitHub-Probleme zu beheben:
   - Beheben Sie [ausgeben 37](https://github.com/Microsoft/azuredatastudio/issues/37): Wenn der Viewer Diagramm einen Fehler verursacht, tritt ein, unerwartetes Verhalten.
   - Beheben Sie [ausgeben 462](https://github.com/Microsoft/azuredatastudio/issues/462): Featureanforderung: Option für Server-Gruppen werden standardmäßig erweitert werden.
   - Beheben Sie [ausgeben 606](https://github.com/Microsoft/azuredatastudio/issues/606): Intellisense - ungültige Vorschlag für Befehl 'update'.
   - Beheben Sie [ausgeben 967](https://github.com/Microsoft/azuredatastudio/issues/967): Abfrageplan erwarten, dass wenn XML-Showplan im Ergebnisraster auswählen.
   - Beheben Sie [ausgeben 1023](https://github.com/Microsoft/azuredatastudio/issues/1023): Fügen Sie eckige Klammern für Ms_foreachdb Aufruf aus Flyfishingdba hinzu.
   - Beheben Sie [ausgeben 1048](https://github.com/Microsoft/azuredatastudio/issues/1048): Vor der Anmeldung SSL/TLS-Handshake-Fehler.
   - Beheben Sie [ausgeben 1050](https://github.com/Microsoft/azuredatastudio/issues/1050): Klare Einblicke vor dem Fehler anzeigen.
   - Beheben Sie [ausgeben 1057](https://github.com/Microsoft/azuredatastudio/issues/1057): Wiederherstellung und neue Abfrageaktionen in der Explorer-Widget werden unterbrochen.
   - Beheben Sie [1068 ausgegeben](https://github.com/Microsoft/azuredatastudio/issues/1068): Dashboard Ausgabe Windows Pops oben mit Fehlermeldung zur Azure SQL-Datenbank.
   - Beheben Sie [ausgeben 1069](https://github.com/Microsoft/azuredatastudio/issues/1069): Dialogfeld "Verbindung" zeigt Server erforderlich, Fehler bei der ersten Anzeige.
   - Beheben Sie [ausgeben 1070](https://github.com/Microsoft/azuredatastudio/issues/1070): Server-Gruppen erfordern jetzt ein Doppelklick zu erweitern.
   - Beheben Sie [ausgeben 1072](https://github.com/Microsoft/azuredatastudio/issues/1072): SELECT-Steuerelement im Hintergrund ist teilweise transparent.
   - Beheben Sie [ausgeben 1115](https://github.com/Microsoft/azuredatastudio/issues/1115): Beheben Sie alle hohen Kontrast Probleme mit der Barrierefreiheit in SQL Operations Studio.
   - Beheben Sie [ausgeben 1101](https://github.com/Microsoft/azuredatastudio/issues/1101): Erweiterung ein Fehler auftritt, Upgrade "herunterladen Manually" Link wird am falschen Ort.
   - Beheben Sie [ausgeben 1103](https://github.com/Microsoft/azuredatastudio/issues/1103): Scrollen Sie V funktioniert nicht auf der Registerkarte Home.
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
version: 0.27.3

Die *öffentliche Vorschau März* weiterhin die wichtigsten GitHub-Probleme zu beheben und konzentriert sich auf die Verbesserung unserer Geschichte Erweiterbarkeit. Insbesondere Erweiterungs-Manager aktivieren, Verbessern der dashboardverwaltung und Bereitstellen von SQL-Agent "und" Insights-Erweiterungen. Dieses Release enthält die folgenden Verbesserungen:

- Erweitern Sie das Dashboard-Erweiterbarkeitsmodell Unterstützung im Registerkartenformat Einblicke und Bereiche der Konfiguration.
   - Erweiterungs-Manager ermöglicht die einfache Übernahme von Erweiterungen.
   - Dashboard-Erweiterungen für Sp_whoisactive aus [whoisactive.com](http://www.whoisactive.com).
   - Weitere Informationen finden Sie unter [erweitern die Funktionalität von SQL Operations Studio](extensions.md).
- Hinzufügen zusätzlicher [Erweiterbarkeits-APIs für die Verbindung und Objekt-Explorer](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API) Management.
- Beheben Sie wichtige Auswirkungen auf Kunden weiterhin [GitHub-Problemen](https://github.com/Microsoft/azuredatastudio/issues).


## <a name="february-2018-february-public-preview"></a>Februar 2018 (Februar öffentliche Vorschau)

Veröffentlichungsdatum: 15. Februar 2018  
version: 0.26.7

Die *Public Preview-Version vom Februar* enthält einige Vorschläge für Features und Fehlerkorrekturen hoher Priorität. Dieses Release enthält die folgenden Verbesserungen:

- Einführung in die automatische Update-Installation, die stellt eine Benachrichtigung bereit, wenn eine neue Version als download verfügbar ist. 
- Das Dialogfeld "Verbindung" 'Datenbank'-Feld ist jetzt eine dynamisch aufgefüllt Dropdown-Liste, die eine Liste der Datenbanken aufgefüllt, die vom angegebenen Server enthält.
- Beheben Sie [Problem 6](https://github.com/Microsoft/azuredatastudio/issues/6): Beim Öffnen von Registerkarten der Abfrage neue behalten Sie Verbindung und der ausgewählten Datenbank werden soll bei.
- Beheben Sie [ausgeben 22](https://github.com/Microsoft/azuredatastudio/issues/22): "Servername" und "Database Name" – können diese Dropdownlisten anstelle von Textfeldern werden?
- Beheben Sie [ausgeben 549](https://github.com/Microsoft/azuredatastudio/issues/549): Silent/sehr automatische Installation führt Anwendung nach der Installation öffnen.
- Beheben Sie [ausgeben 481](https://github.com/Microsoft/azuredatastudio/issues/481): Fügen Sie die Option "Nach Updates suchen" hinzu.
- Farbliche Kennzeichnung von SQL-Editor und automatische Vervollständigung Fixes:
   - Beheben Sie [ausgeben 584](https://github.com/Microsoft/azuredatastudio/issues/584): Schlüsselwort "Vollständige" nicht von IntelliSense hervorgehoben.
   - Beheben Sie [ausgeben 345](https://github.com/Microsoft/azuredatastudio/issues/345): Farbigen Anzeigen von SQL-Funktionen im Editor.
   - Beheben Sie [ausgeben 300](https://github.com/Microsoft/azuredatastudio/issues/300): [#tempData] letzte "]" wird grün angezeigt.
   - Beheben Sie [ausgeben 225](https://github.com/Microsoft/azuredatastudio/issues/225): Nichtübereinstimmung der Schlüsselwort-Farbe.
   - Beheben Sie [ausgeben 60](https://github.com/Microsoft/azuredatastudio/issues/60): Ungültiger Sql Farbe syntaxhervorhebung bei Verwendung der temporären Tabelle in from-Klausel.
- Führen Sie die Verbindung Erweiterbarkeits-API.
- VS Code-Editor 1.19-Integration.
- Aktualisieren Sie JustinPealing/html-Abfrageplan Komponente einfachere Installation mehrere Verbesserungen der Abfrageplan-Viewer.


## <a name="january-2018-january-public-preview"></a>Januar 2018 (Januar öffentliche Vorschau)

Veröffentlichungsdatum: 17 Januar 2018  
version: 0.25.4

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
version: 0.24.1

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
version: 0.23.6

- Erste Version des [!INCLUDE[name-sos](../includes/name-sos-short.md)].


## <a name="next-steps"></a>Nächste Schritte

Finden Sie in der folgenden schnellstartanleitungen für den Einstieg:
- [Verbinden und Abfragen von SQLServer](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verbinden und Abfragen von Azure Datawarehouse](quickstart-sql-dw.md)

Mitwirken an [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
