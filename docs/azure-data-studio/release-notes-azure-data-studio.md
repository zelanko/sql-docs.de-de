---
title: Versionshinweise
titleSuffix: Azure Data Studio
description: Versionshinweise zu Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: 2b06e8476e10abc3a96ab6c6f2304ef81f225f02
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681613"
---
# <a name="release-notes-for-azure-data-studio"></a>Anmerkungen zu dieser Version für Azure Data Studio

**[Herunterladen Sie und installieren Sie die neueste Version.](download.md)**

## <a name="june-2019"></a>Juni 2019

6 Juni 2019 &nbsp;  /  &nbsp; Version: 1.8.0 

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Version des zentralen Management Server (CMS)-Erweiterung | Zentrale Verwaltungsserver speichern eine Liste mit Instanzen von SQL Server, die eine oder mehrere Gruppen zentraler Verwaltungsserver unterteilt ist. Benutzer können eine Verbindung mit ihren eigenen vorhandenen CMS-Servern herstellen und verwalten ihre Server wie das Hinzufügen und Entfernen von Servern. Weitere Informationen finden Sie [hier](https://docs.microsoft.com/sql/relational-databases/administer-multiple-servers-using-central-management-servers) |
| Version der Datenbank-Verwaltung-Tool-Erweiterungen für Windows | Diese Erweiterung wird gestartet, zwei der am häufigsten verwendeten Funktionen in SQL Server Management Studio aus Azure Data Studio. Benutzer können klicken Sie mit der rechten Maustaste auf viele verschiedene Objekte (z. B. Datenbanken, Tabellen, Spalten, Sichten usw.) und Eigenschaften auswählen, um das Dialogfeld Eigenschaften von SSMS für dieses Objekt anzeigen. Darüber hinaus können Benutzer klicken Sie mit der rechten Maustaste auf eine Datenbank und wählen Sie "Skripts generieren", um die bekannten SSMS Assistent zum Generieren Skripts zu starten. 
| Schema vergleichen-Verbesserungen | &bull; &nbsp; Optionen für die hinzugefügte einschließen/ausschließen <br/>&bull; &nbsp; Skriptgenerierung Skript öffnet nach generiert werden <br/>&bull; &nbsp; Entfernt doppelte Bildlaufleisten  <br/>&bull; &nbsp; Verbesserungen bei der Formatierung und layout <br/>&bull; &nbsp; Finden Sie umfassende Änderungen [hier](https://github.com/microsoft/azuredatastudio/issues?q=is%3Aissue+milestone%3A%22June+2019+Release%22+label%3A%22Area%3A+Schema+Compare%22+is%3Aclosed)|
| Verschobene Messages-Abschnitt zur Registerkarte "Eigene" | Als Benutzer mit SQL-Abfragen ausgeführt haben, wurden Ergebnisse und Meldungen für gestapelte Bereiche. Jetzt sind sie auf separaten Registerkarten in einem Bereich z. B. in SSMS. |
| SQL-Notebook-Verbesserungen | &bull; &nbsp; Benutzer können jetzt auch ihre eigenen Python 3 oder Anaconda-Installationen in Notizbüchern verwenden <br/>&bull; &nbsp; Mehrere Stabilität + anpassen/Ende Korrekturen &bull; &nbsp; zeigt die vollständige Liste der Verbesserungen [hier](https://github.com/microsoft/azuredatastudio/issues?q=is%3Aissue+milestone%3A%22June+2019+Release%22+is%3Aclosed+label%3A%22Area%3A+Notebooks%22)|
| Visual Studio-Code kann Merge 1.34 freizugeben. | Neueste Verbesserungen finden Sie [hier](https://code.visualstudio.com/updates/v1_34) |
| Behobene Fehler und Probleme. | Finden Sie unter [Fehlern und Problemen, die auf GitHub](https://github.com/microsoft/azuredatastudio/milestone/32?closed=1). |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme
- Datenbank-Verwaltung-Tools-Erweiterungen für Windows
    - Eigenschaften von Knoten für nicht verbundene Server kann nicht gestartet werden.
    - Eigenschaften für Azure-Server kann nicht gestartet werden.
    - Nicht alle Objekte verfügen Dialogfelder für Ereigniseigenschaften
    - Dialogfelder lange gestartet wird
    - Fehler, die Server für einige Typen von Verbindungen (wie z.B. AAD) starten
- Notebooks
    - [5838](https://github.com/microsoft/azuredatastudio/issues/5838) ermöglichen Benutzern die Verwendung von System Python Notebooks
- Schemavergleich
    - [5804](https://github.com/microsoft/azuredatastudio/issues/5804) Schemavergleich Tasks angezeigt werden standardmäßig "Abbrechen" im Kontextmenü nichts tut

## <a name="may-2019"></a>Mai 2019

8 Mai 2019 &nbsp;  /  &nbsp; Version: 1.7.0 

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Veröffentlichung der Schemavergleich-Erweiterung | Schemavergleich ist ein bekanntes Feature in SQL Server Data Tools (SSDT) und der primäre Anwendungsfall ist, um zu vergleichen und Visualisieren die Unterschiede zwischen Datenbanken und DACPAC-Dateien und zum Ausführen von Aktionen auf, damit sie identisch sind. |
| Aufgabenansicht in Fenster "Ausgabe" verschoben | Benutzer können nun den Status der lang ausgeführten Aufgaben z.B. Sicherung, Wiederherstellung und Schemavergleich in der Aufgabenansicht im Fenster "Ausgabe" anzeigen.
| Hinzugefügte Seite "Willkommen" | &bull; &nbsp; Links zu häufig verwendete Aktionen wie die neue Abfrage, die neue Datei, neues Notebook <br/>&bull; &nbsp; Links zu Dokumentationen und GitHub |
| SQL-Notebook-Verbesserungen | &bull; &nbsp; Markdown-Rendering-Verbesserungen, z. B. eine bessere Unterstützung für Anmerkungen zu dieser Version und Tabellen <br/>&bull; &nbsp; Verbesserungen der benutzerfreundlichkeit auf der Symbolleiste <br/>&bull; &nbsp; Markdownlinks nicht mehr vertrauenswürdigen Notebooks Cmd/STRG + klicken und direkt geklickt werden kann <br/>&bull; &nbsp; Verbesserungen an der Bereinigung der Jupyter-Prozesse nach dem Schließen von Notebooks, und verringert Fehler, wenn Sie mehrere Notizbücher gleichzeitig zu starten <br/>&bull; &nbsp; Verbesserungen bei der SQL-Notebook-Verbindungen, um sicherzustellen, dass Fehler treten nicht, wenn 2 Notebooks für dieselbe Datenbank ausgeführt wird. <br/>&bull; &nbsp; Verbesserungen an Notebook den automatischen Bildlauf der aktuell ausgeführten Zelle, wenn Sie die Zellen ausführen-Schaltfläche auf der Symbolleiste klicken <br/>&bull; &nbsp; Allgemeine Verbesserungen für Stabilität und Leistung |
| Behobene Fehler und Probleme. | Finden Sie unter [Fehlern und Problemen, die auf GitHub](https://github.com/microsoft/azuredatastudio/milestone/31?closed=1). |
| &nbsp; | &nbsp; |

## <a name="april-2019"></a>April 2019

18 April 2019 &nbsp;  /  &nbsp; Version: 1.6.0 

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Umbenannt **Server** TAB-Taste zum **Verbindungen** | |
| Azure-Ressourcen-Explorer als ein Azure Viewlet unter Verbindungen verschoben | Benutzer können jetzt ihre Azure SQL-Instanzen über Azure Viewlet anzeigen, in der Verbindungen und erweitern, um Objekte unter jedem Server oder die Datenbank anzuzeigen.|
| SQL-Notebook-Verbesserungen | &bull; &nbsp; Hinzugefügte Schaltfläche auf der Symbolleiste, um die Ausgabe für alle Zellen löschen <br/>&bull; &nbsp; Hinzugefügte Schaltfläche auf der Symbolleiste, um alle Zellen ausführen <br/>&bull; &nbsp; Feste Verbindung Server anstelle des Namens (falls festgelegt) an den Dropdownliste anhängen <br/>&bull; &nbsp; Korrektur für Images in Markdown nicht wiedergegeben werden, wenn Sie relative Image Pfade verwenden <br/>&bull; &nbsp; Verbesserte Funktionalität in der Notebook-Raster durch Hinzufügen von Doppelklicken Sie auf automatische Größenänderung Spaltengröße und eine verbesserte Mousewheel-Unterstützung <br/>&bull; &nbsp; Verbesserungen bei der Fehlerbehandlung und Python installieren resilienz bei der Installation von Python über notebooks <br/>&bull; &nbsp; Verbesserungen an der Funktionalität "Alles auswählen", bei der Auswahl der Notebook-Zellen <br/>&bull; &nbsp; Verbesserungen bei der Notebook-Verbindungen, um zu verhindern, schließen ein Notebook und Auswirkungen auf eine Objekt-Explorer-Verbindung <br/>&bull; &nbsp; Verbesserte Notebook-Erfahrung ermöglicht dem Benutzer eine Meldung angezeigt, wenn Notebook getrennt und eine Verbindung zum Ausführen von Zellen benötigt<br/>&bull; &nbsp; Verbesserte Unterstützung für nicht gespeicherte Notebooks, in Werbung zu aktivieren, wenn ADS erneut gestartet wird |
| Behobene Fehler und Probleme. | Finden Sie unter [Fehlern und Problemen, die auf GitHub](https://github.com/Microsoft/azuredatastudio/milestone/26?closed=1). |
| &nbsp; | &nbsp; |

## <a name="march-2019-hotfix"></a>März 2019 (Hotfix)

22 März 2019 &nbsp;  /  &nbsp; Version: 1.5.2 &nbsp;  /  &nbsp; Hotfix-Version

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Einige Probleme, die in den Wert "1.5.1" ermittelt wurden behoben. | Finden Sie unter [März Hotfix-Version auf GitHub](https://github.com/Microsoft/azuredatastudio/milestone/28).<br/> <br/>&bull; &nbsp; Problem behoben, in dem Benutzer nicht Notizbuch, die von der Aufgabe "Notizbuch öffnen" im Dashboard geöffnet schließen konnte <br/>&bull; &nbsp; Problem behoben wurde, in dem Notebook JSON zusätzliche} nach dem Speichern <br/>&bull; &nbsp; Problem behoben, wenn der Notebook-Raster nicht zu Designänderungen reagiert wurden <br/>&bull; &nbsp; Korrigiert: Problem, in denen vollständige Notebook-Pfad in der Registerkartenheader angezeigt wurde. Jetzt wird nur der Dateiname angezeigt. |
| &nbsp; | &nbsp; |

## <a name="march-2019"></a>März 2019

18 März 2019 &nbsp;  /  &nbsp; Version: 1.5.1

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Hinzugefügt [PostgreSQL-Erweiterung für Azure Data Studio](postgres-extension.md) | Unterstützte Funktionen: <br/>&bull; &nbsp; Dialogfeld "Verbindung" <br/>&bull; &nbsp; Objekt-Explorer <br/>&bull; &nbsp; Abfrage-Editor <br/>&bull; &nbsp; Diagrammerstellung <br/>&bull; &nbsp; Dashboards <br/>&bull; &nbsp; Codeausschnitte <br/>&bull; &nbsp; Bearbeiten von Daten <br/>&bull; &nbsp; Notebooks |
| Zusätzliche SQL-Notebooks | SQL-Kernel-Unterstützung für integrierte Notebook Anzeige hinzugefügt: <br/>&bull; &nbsp; Unterstützt die T-SQL <br/>&bull; &nbsp; Support PGSQL |
| Zusätzliche PowerShell-Erweiterung  | Bietet über die [PowerShell-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) von Visual Studio Code auftreten.  |
| Hinzugefügte SQL Server-Erweiterung DACPAC-Datei  | Entfernt Datenebenen-Anwendungs-Assistent von SQL Server-Import-Erweiterung in eine neue Erweiterung an.  |
| Hinzugefügte Community Extensions QueryPlan.show | Integration unterstützt, um Abfragepläne zu visualisieren.  |
| Aktualisierte 2019-Vorschau von SQL Server-Erweiterung | &bull; &nbsp; Unterstützung für Jupyter-Notebook, insbesondere Python3 und Spark-Kernel, wurden in der Core-Studio für Azure Data-Tool verschoben. <br/>&bull; &nbsp; Fehlerbehebungen für den Assistenten für externe Daten  |
| Behobene Fehler und Probleme. | Finden Sie unter [Fehlern und Problemen, die auf GitHub](https://github.com/Microsoft/azuredatastudio/milestone/25?closed=1). |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Bekannte Probleme
- [#4427](https://github.com/Microsoft/azuredatastudio/issues/4427): Klicken auf die Zelle vor der Kernel bereit ist für die Spark-Ergebnisse in Schwerwiegender Fehler **dieses Problem zu umgehen:** Warten Sie, bis der Kernel geladen werden, bis alle Zellen ausführen
- [#4493](https://github.com/Microsoft/azuredatastudio/issues/4493): ANZEIGEN, die aus SSMS mit der SQL-Auth - eingabeaufforderungen Benutzer das Kennwort gestartet **dieses Problem zu umgehen:** Verwenden Sie jetzt Windows-Authentifizierung. 
- [#4494](https://github.com/Microsoft/azuredatastudio/issues/4494): Kann nicht zum Installieren von SQL-Notebook-Funktion <br/>
**Problemumgehung:** Führen Sie die Schritte zur problemumgehung [hier](https://github.com/Microsoft/azuredatastudio/issues/4494#issuecomment-473043832). 
- [#4503](https://github.com/Microsoft/azuredatastudio/issues/4503): Azure Data Studio darf nicht direkt geöffnet, aus dem Ordner "Downloads" (Mac) sein. <br />
**Problemumgehung:** Starten Sie Computer nach dem Entpacken der app neu. Wird untersucht werden. 
- [#4539](https://github.com/Microsoft/azuredatastudio/issues/4539):  Verliert Notebooks speichern als Verbindungskontext <br />
**Problemumgehung:** Wird in der nächsten Version behoben werden. 
- [#4458](https://github.com/Microsoft/azuredatastudio/issues/4458): Extrahieren der DACPAC-Datei abstürzt SqlToolsService, wenn ungültige Version verwendet wird <br/>
**Problemumgehung:** Starten Sie Studio für Azure Data, und stellen Sie sicher, dass die richtige Version verwendet wird.
- Neue Symbole für Notebooks und Notizbuch öffnen verloren. <br/> 
**Problemumgehung:** Die legacy-Verbindungstyp ist veraltet. Es wird empfohlen, eine Verbindung mit der SQL Server-Endpunkt, und erhalten Sie alle Aktionen (neues Notizbuch, Spark-Auftrag) wie erwartet. 

## <a name="february-2019"></a>Februar 2019

13 Februar 2019 &nbsp;  /  &nbsp; Version: 1.4.5

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Hinzugefügt **Admin Pack für SQL Server** Erweiterungspaket. | Dies erleichtert es, SQL Server-Administratoraufgaben Erweiterungen zu installieren. Dies schließt Folgendes ein:<br/>&bull; &nbsp; [SQL Server-Agent](sql-server-agent-extension.md?view=sql-server-2017)<br/>&bull; &nbsp; [SQL Server Profiler](https://docs.microsoft.com/sql/azure-data-studio/sql-server-profiler-extension)<br/>&bull; &nbsp; [SQL Server-Import](sql-server-import-extension.md?view=sql-server-2017) |
| Hinzugefügte Filter erweitert ereignisunterstützung in Profiler-Erweiterung. | &nbsp; |
| Hinzugefügte speichern als XML-Funktion, die T-SQL-Ergebnisse als XML speichern können. | &nbsp; |
| Datenebenen-Anwendungs-Assistent-Verbesserungen hinzugefügt. | &bull; &nbsp; Hinzugefügte Skript Schaltfläche "generieren"<br/>&bull; &nbsp; Hinzugefügte Ansicht, die Warnungen eines möglichen Datenverlusts während der Bereitstellung zu erhalten. |
| Updates der SQL Server 2019 Preview-Erweiterung. | Finden Sie unter [vorschauerweiterung von SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| Führt streaming standardmäßig aktiviert, lange Ausführung von Abfragen. | &nbsp; |
| Behobene Fehler und Probleme. | Finden Sie unter [Fehlern und Problemen, die auf GitHub](https://github.com/Microsoft/azuredatastudio/milestone/23?closed=1). |
| &nbsp; | &nbsp; |

## <a name="january-2019-hotfix"></a>Januar 2019 (Hotfix)

16 Januar 2019 &nbsp;  /  &nbsp; Version: 1.3.9 &nbsp;  /  &nbsp; Hotfix-Version

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Einige Probleme, die in 1.3.8 ermittelt wurden behoben. | Finden Sie unter [Hotfix-Release von Januar auf GitHub](https://github.com/Microsoft/azuredatastudio/milestone/24?closed=1).<br/><br/>Ausführliche Informationen finden Sie unter:<br/>&bull; &nbsp; [Änderungsprotokoll auf GitHub](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md).<br/>&bull; &nbsp; [Releases auf GitHub](https://github.com/Microsoft/azuredatastudio/releases). |
| &nbsp; | &nbsp; |

## <a name="january-2019"></a>Januar 2019

09 Januar 2019 &nbsp;  /  &nbsp; Version: 1.3.8

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Einen neuen Benutzer Installer für Windows wird hinzugefügt. | Im Gegensatz zu den vorhandenen System-Webinstaller erfordert das Installationsprogramm für neue Benutzer keine Administratorrechte. Dies ermöglicht auch ein einfacher Upgradeverhalten für nicht-Administratoren. |
| Zusätzliche Unterstützung für Azure Active Directory-Authentifizierung. | &nbsp; |
| Hiermit kündigen wir Idera SQL DM Performance Insights (Vorschau). | &nbsp; |
| Datenebenen-Anwendungs-Assistent-Unterstützung in SQL Server-Import-Erweiterung. | &nbsp; |
| Aktualisieren Sie auf der SQL Server 2019 Preview-Erweiterung. | Finden Sie unter [vorschauerweiterung von SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| Verbesserungen für SQL Server Profiler. | &nbsp; |
| Führt das Streaming für große Abfragen (Vorschau). | &nbsp; |
| Community Extensions: Sp_executesql to Sql und die neue Datenbank. | &nbsp; |
| Behobene Fehler und Probleme. | Finden Sie unter [Fehlern und Problemen, die auf GitHub](https://github.com/Microsoft/azuredatastudio/milestone/19?closed=1). |
| &nbsp; | &nbsp; |

## <a name="november-2018"></a>November 2018

6 November 2018 &nbsp;  /  &nbsp; Version: 1.2.4

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Aktualisieren Sie auf der SQL Server 2019 Preview-Erweiterung. | Finden Sie unter [vorschauerweiterung von SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| Einführung in fügen Sie der Plans-Erweiterung. | &nbsp; |
| Einführung in High Color Abfragen-Erweiterungen, einschließlich SSMS-Editor-Design. | &nbsp; |
| Fehlerbehebungen in SQL Server-Agent, Profiler und Import-Erweiterungen. | &nbsp; |
| Beheben von.NET Core Socket KeepAlive Problem verursacht, inaktive Verbindungen auf MacOS gelöscht. | &nbsp; |
| Upgrade SQL Tools-Diensts zur.NET Core 2.2 Preview 3 (für AAD-Unterstützung für "Eventual"). | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-november-2018"></a>Aufgrund von Fehlerbehebungen, November 2018

- Beheben Sie [Problem #2933](https://github.com/Microsoft/azuredatastudio/issues/2933): Die Verbindung wurde getrennt, zur Azure SQL-Datenbank
- Beheben Sie [Problem #2914](https://github.com/Microsoft/azuredatastudio/issues/2914): "Ungültige Argument" Ausnahme erweiterbare OE-Datenbank-Knoten
- Beheben Sie [Problem #2935](https://github.com/Microsoft/azuredatastudio/pull/2935): Mehrzeilige Nachrichten richtig angezeigt, in den Abfrageergebnissen
- Beheben Sie [Problem #2906](https://github.com/Microsoft/azuredatastudio/pull/2906): Beheben Sie Dokumentname Daten bearbeiten, wenn Tabellennamen Sonderzeichen enthält.
- Beheben Sie [Problem #2929](https://github.com/Microsoft/azuredatastudio/issues/2929): Erstellt in der Erweiterung Änderungsprotokoll sagt, um den Anmerkungen zur Version von VSCode für die Änderungen zu überprüfen
- Beheben Sie [Problem #2719](https://github.com/Microsoft/azuredatastudio/issues/2719): Design "hoher Kontrast" Doubles/Tripeln Symbole
- Beheben Sie [Problem #3047](https://github.com/Microsoft/azuredatastudio/pull/3047): Fügen Sie eine Befehlszeilenschnittstelle für die Verbindung mit einer SQL Server
- Beheben Sie [Problem #3031](https://github.com/Microsoft/azuredatastudio/pull/3031): Abfrage-Plan-Design-Unterstützung hinzufügen

## <a name="october-2018"></a>Oktober 2018

29. Oktober 2018 &nbsp;  /  &nbsp; Version: 1.1.4

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Einführung in die Azure-Ressourcen-Explorer zum Durchsuchen von Azure SQL-Datenbanken. | &nbsp; |
| Verbessert die Stabilität von Objekt-Explorer und Abfrage-Editor-Konnektivität. | &nbsp; |
| Verbesserungen für SQL-Agent-Erweiterungen. | &nbsp; |
| Aktualisieren Sie auf der SQL Server 2019 Preview-Erweiterung. | Finden Sie unter [vorschauerweiterung von SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-october-2018"></a>Aufgrund von Fehlerbehebungen, Oktober 2018

- Beheben Sie [Problem #2717](https://github.com/Microsoft/azuredatastudio/issues/2717): Ergebnis der XML-Spalte, klicken Sie auf Formatierung
- Beheben Sie [Problem #2993](https://github.com/Microsoft/azuredatastudio/issues/2993): Die Breite des Ergebnisses Windows ist unvollständig
- Beheben Sie [Problem #2999](https://github.com/Microsoft/azuredatastudio/issues/2999): System.Diagnostics.Tracing-Datei auf dem Mac konnte nicht geladen werden, Herstellen der Verbindung mit Datenbank
- Beheben Sie [Problem #2851](https://github.com/Microsoft/azuredatastudio/issues/2851): Zeitreihen-Diagramm wird nicht ordnungsgemäß gerendert.
- Beheben Sie [Problem #2996](https://github.com/Microsoft/azuredatastudio/issues/2996): Temporäre Tabelle Datenverlust aufgrund von plötzlichen sitzungsänderung

Ausführliche Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), und [Versionen](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="september-2018-ga-release"></a>September 2018 (GA-Version)

24. September 2018 &nbsp;  /  &nbsp; Version: 1.0 &nbsp;  /  &nbsp; GA-Version

Allgemein verfügbare Version von Azure Data Studio (früher SQL Operations Studio).

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Fragen Sie Ergebnisraster Verbesserungen der Leistung und UX für große Anzahl von Resultsets. | &nbsp; |
| Visual Studio Code-Quellcode Aktualisieren von "1,23", um 1.26.1 mit Rasterlayout und verbesserte-Einstellungs-Editor (Vorschau). | &nbsp; |
| Verbesserungen der Barrierefreiheit für die Sprachausgabe und Tastaturnavigation hohen Kontrast. | &nbsp; |
| Hinzugefügt `Connection name` Option aus, um einen alternativen Anzeigenamen in der Ansicht-Let-Server angeben. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="announcing-the-sql-server-2019-preview-extension"></a>Ankündigung der Vorschau von SQL Server-2019-Erweiterung

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Unterstützung für SQL Server-2019 vorschaufeatures einschließlich [big Data-Cluster](../big-data-cluster/big-data-cluster-overview.md) unterstützen. | Verbinden Sie sich an das HDFS/Spark-Gateway, das im Lieferumfang von SQL Server-2019 Vorschau.<br/><br/>Durchsuchen von HDFS, Hochladen von Dateien, Dateien speichern und nützliche Aktionen wie das Analysieren im Notebook für CSV-Dateien zu starten.<br/><br/>Übermitteln von Spark-Aufträgen über das Dashboard, oder mit der rechten Maustaste auf eine HDFS/Spark-Verbindung im Objekt-Explorer. |
| Azure Data Studio Notebooks. | Erstellen oder Öffnen von Notebooks mit einem integrierten Notebook-Viewer. In dieser Version das Notebook unterstützt Viewer, die Verbindung mit lokalen Kernels und die SQL Server-2019 big Data-Cluster nur.<br/><br/>Verwenden Sie die PROSE Code Accelerator-Bibliotheken in Ihrem Notebook, um Dateitypen Format und die Daten für schnelle datenvorbereitung erfahren. |
| Azure-Ressourcen-Explorer. | Die Azure-Ressourcen-Explorer-Ansicht können Sie datenbezogene Endpunkte für Ihre Azure-Konten durchsuchen, und erstellen im Objekt-Explorer-Verbindungen für sie. In dieser Version werden die Azure SQL-Datenbanken und Servern unterstützt. |
| SQL Server-PolyBase Erstellen externer Tabellen-Assistenten. | Erstellen Sie eine externe Tabelle und die unterstützenden Systemmetadaten-Strukturen mit einer benutzerfreundlichen Assistenten an. In dieser Version werden die SQL Server- und Oracle-Remoteserver unterstützt. |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-september-2018"></a>Aufgrund von Fehlerbehebungen, September 2018

- Beheben Sie [Problem #2647](https://github.com/Microsoft/azuredatastudio/issues/143): Die Diagramme hat einen großen Schritt rückwärts.
- Beheben Sie [Problem #2648](https://github.com/Microsoft/azuredatastudio/issues/143): Wählen Sie, die eine JSON-links auf die gesamte Spalte zurückgibt.

Ausführliche Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), und [Versionen](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="august-2018"></a>August 2018

30. August 2018 &nbsp;  /  &nbsp; Version: 0.32.8 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *öffentliche Vorschau für August* Fehlerbehebungen, Produkt Stabilisierung und Auffüllen der Lücken in vorhandenen Szenarios im Mittelpunkt.

_0.32.8 bietet Korrekturen für einige Regressionen finden Sie im 0.32.7 ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971), [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372))_

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Hiermit kündigen wir die SQL Server-Import-Erweiterung. | &nbsp; |
| Verwaltung von SQL Server Profiler-Sitzung. | &nbsp; |
| Unterstützung von SQL Server Profiler-Sitzung Vorlagen. | &nbsp; |
| Verbesserungen für SQL Server-Agent. | &nbsp; |
| Neue Community-Erweiterung: Erste-Responder-Kit. | &nbsp; |
| Verbesserungen bei der Quality Of Life: Verbindungszeichenfolgen | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-august-2018"></a>Aufgrund von Fehlerbehebungen, August 2018

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

### <a name="known-issues-august-2018"></a>Bekannte Probleme "," August 2018

- [Problem #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) speichern als erste Zeile der Daten nur speichert Excel
- [Problem #2150](https://github.com/Microsoft/azuredatastudio/issues/2150): Es konnte keine Verbindung auf Ubuntu 16.04, um SQL-Code in einem container

## <a name="july-2018"></a>Juli 2018

Am 19. Juli 2018 &nbsp;  /  &nbsp; Version: 0.31.4 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *Public Preview von Juli* konzentriert sich auf die folgenden Elemente:

- Die erste Version der SQL Server-Agent-Konfiguration-Szenarien.
- SQL Server Profiler-Sitzung und Ansicht-Vorlage Erweiterungen.
- Fortgesetzte Fehlerbehebungen für Kunden gemeldete Probleme mit GitHub.

&nbsp;

| Ändern | Details |
| :----- | :------ |
| [SQL Server-Agent für SQL Operations Studio-Erweiterung](sql-server-agent-extension.md) Verbesserungen. | Anzeigen von Warnungen, Operatoren und Proxys und Symbole im linken Bereich hinzugefügt.<br/><br/>Hinzugefügte Dialogfelder für die neuen Auftrag, Neuer Auftragsschritt, neue Warnung und New-Operator.<br/><br/>Hinzugefügte Auftrag löschen, Warnungen löschen und Delete-Operator (Rechtsklick).<br/><br/>Bei vorherigen Ausführungen-Visualisierung hinzugefügt.<br/><br/>Zusätzliche Filter für jeden Spaltennamen. |
| [SQL Server Profiler für SQL Operations Studio-Erweiterung](sql-server-profiler-extension.md) Verbesserungen. | 5 Vorlagen, die zum Anzeigen von erweiterte Ereignisse die standardmäßig hinzugefügt.<br/><br/>Server-Datenbank-Verbindungsname ist hinzugefügt.<br/><br/>Unterstützung für Azure SQL-Datenbank-Instanzen hinzugefügt.<br/><br/>Hinzugefügte Vorschlag zu Profiler beenden, wenn die Registerkarte geschlossen wird, wenn der Profiler noch ausgeführt wird. |
| Die Version der Erweiterung für Skripts kombinieren. | &nbsp; |
| Assistent "und" Dialogfeld Erweiterungspunkte behandelt, die für Ersteller von Erweiterungen hinzugefügt werden. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-july-2018"></a>Aufgrund von Fehlerbehebungen, Juli 2018

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

## <a name="june-2018"></a>Juni 2018

20. Juni 2018 &nbsp;  /  &nbsp; Version: 0.30.6 &nbsp;  /  &nbsp; öffentliche Vorschau

&nbsp;

| Ändern | Details |
| :----- | :------ |
| **SQL Server Profiler für SQL Operations Studio _Vorschau_**  erste Version der Erweiterung. | &nbsp; |
| Die neue **SQL Data Warehouse** Erweiterung enthält umfangreiche anpassbar dashboardwidgets stellt Einblicke in Ihr Datawarehouse. | Dies hebt die Sperre wichtige Szenarien zu verwalten und optimieren Ihr Datawarehouse, um sicherzustellen, dass sie für eine gleichbleibende Leistung optimiert ist. |
| **Bearbeiten von Daten, die "Filtern und sortieren"** unterstützen. | &nbsp; |
| **SQL Server-Agent für SQL Operations Studio _Vorschau_**  Erweiterung Verbesserungen für die Aufträge und Auftragsverlauf Ansichten. | &nbsp; |
| Verbesserte **-Assistent & Dialogfeld-Framework für UI-Builder** Erweiterbarkeits-APIs. | &nbsp; |
| Aktualisieren Sie VS Code-Plattform-Quellcodes. | Integriert die folgenden Versionen:<br/>&bull; &nbsp; [März 2018 (Version 1.22)](https://code.visualstudio.com/updates/v1_22)<br/>&bull; &nbsp; [April 2018 ("1,23")](https://code.visualstudio.com/updates/v1_23) |
| &nbsp; | &nbsp; |

### <a name="github-issues-fixes-june-2018"></a>GitHub-Problemen, behebt, Juni 2018

- Die Anforderung zur ([ausgeben 1204](https://github.com/Microsoft/azuredatastudio/issues/1204)): Stellen Sie die Ergebnisse Breite des Rasters AutoAnpassen-Spalte auf Daten, und beachten Sie die manuelle Änderungen, wenn dieselbe Abfrage erneut ausgeführt wird.
- Beheben Sie [ausgeben 1398](https://github.com/Microsoft/azuredatastudio/issues/1398): Sollte anzeigen Nachricht hinzufügen, und fügen die Schaltfläche "Konto" hinzu, wenn verknüpftes Konto leer ist.
- Beheben Sie [ausgeben 1399](https://github.com/Microsoft/azuredatastudio/issues/1399): Registerkarte "verknüpfte Konto" ist unterbrochen, wenn die Ansicht reduziert wird.
- Beheben Sie [ausgeben 1374](https://github.com/Microsoft/azuredatastudio/issues/1374): SQL Tools-Dienst stürzt ab, wenn Sie SQL-Datei vom Datenträger zu öffnen.
- Beheben Sie [ausgeben 1372](https://github.com/Microsoft/azuredatastudio/issues/1372): SQL-Schlüsselwort "BETWEEN" fehlt.
- Beheben Sie [ausgeben 1395](https://github.com/Microsoft/azuredatastudio/issues/1395): "MATCH"-Schlüsselwort stürzt SQL Tools-Dienst ab.
- Beheben Sie [ausgeben 1496](https://github.com/Microsoft/azuredatastudio/issues/1496): "Neuer Profiler" Option für das Kontextmenü im Objekt-Explorer hat keine Auswirkungen.
- Beheben Sie [ausgeben 1495](https://github.com/Microsoft/azuredatastudio/issues/1495): Abfrage-Editor "Explain" Abfrageplan ist unterbrochen.

## <a name="may-2018"></a>Mai 2018

7\. Mai 2018 &nbsp;  /  &nbsp; Version: 0.29.3 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *Public Preview kann* konzentriert sich auf die Stabilität und Fehlerbehebungen.

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Jetzt Redgate SQL Search-Erweiterung, die im Erweiterungs-Manager verfügbar. | &nbsp; |
| Community-Lokalisierung für 10 Sprachen verfügbar. | Deutsch, Spanisch, Französisch, Italienisch, Japanisch, Koreanisch, Portugiesisch, Russisch, vereinfachtem Chinesisch und traditionelles Chinesisch. |
| Telemetrie-Auflistung geändert wird. | &bull; &nbsp; Reduzierte Telemetrie-Erfassung.<br/>&bull; &nbsp; Verbesserte Benutzeroberfläche für die Teilnahme an.<br/>&bull; &nbsp; Produktinterne Links zu Datenschutzbestimmungen. |
| Erweiterungs-Manager verfügt über verbesserte Marketplace auftreten. | Community Extensions leichter zu ermitteln. |
| SQL Agent-Erweiterung. | &bull; &nbsp; Aufträge.<br/>&bull; &nbsp; Zur Verbesserung der Auftragsverlauf-Ansicht. |
| Updates für Whoisactive und Erweiterungen von Server-Berichte. | &nbsp; |
| Verbesserte Bildlauf der Dashboardeigenschaften zu verwalten. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fix-github-issues"></a>GitHub-Probleme beheben

- Beheben Sie [ausgeben 703](https://github.com/Microsoft/azuredatastudio/issues/703): Ähnlich wie HTML-Text eingeben, in das Bearbeiten von Daten wird Wert nicht ordnungsgemäß angezeigt wurde, bis die Aktualisierung
- Beheben Sie [ausgeben 821](https://github.com/Microsoft/azuredatastudio/issues/821): azuredatastudio.deb paketabhängigkeit
- Beheben Sie [ausgeben 1260](https://github.com/Microsoft/azuredatastudio/issues/1260): Schlüsselwort 'distinct' nicht hervorgehoben.
- Beheben Sie [ausgeben 1332](https://github.com/Microsoft/azuredatastudio/issues/1332): Bearbeiten Sie Daten wiederherstellen Zeile funktioniert nicht
- Beheben Sie [ausgeben 1215](https://github.com/Microsoft/azuredatastudio/issues/1215): SQL Agent-Erweiterung und der Statusleiste
- Beheben Sie [ausgeben 1316](https://github.com/Microsoft/azuredatastudio/issues/1316): Größe der SQL-Agent nicht nach Windows-Größe ändern

## <a name="april-2018"></a>April 2018

25 April 2018 &nbsp;  /  &nbsp; Version: 0.28.6 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *Public Preview-Version April* enthält Fehlerbehebungen und Verbesserungen.

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Verbesserungen an der Vorschau von SQL-Agent-Erweiterung: | &nbsp; |
| &nbsp; &nbsp; &nbsp; Verbesserte Unterstützung für Dateien. | &bull; &nbsp; Große Dateien.<br/>&bull; &nbsp; Geschützter Dateien für das Speichern geschützter Administrator.<br/>&bull; &nbsp; Speichern von \>256 M-Dateien in SQL Operations Studio. |
| &nbsp; &nbsp; &nbsp; Integriertes Terminal aufteilen. | Arbeiten Sie mit mehreren open Terminals gleichzeitig an. |
| &nbsp; &nbsp; &nbsp; Schnellere Installationen und Startzeiten. | Reduzierte Installation der Datei auf dem Datenträger Anzahl Foot drucken. |
| &nbsp; | &nbsp; |

### <a name="fix-github-issues-april-2018"></a>Beheben Sie die GitHub-Probleme, April 2018

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

### <a name="visual-studio-code-121-platform"></a>Visual Studio Code 1.21-Plattform

Eine Markierung für die öffentliche Vorschau von April wird die Aktualisierung des Quellcodes für die Visual Studio Code 1.21-Plattform. Dies bringt mehrere Updates auf die Kern-Editor und die Workbench aus der vorherigen 1.19 verfügt über Synchronisierungspunkt. Die folgenden: Beispiele

&nbsp;

| Ändern | Details |
| :----- | :------ |
| [Neue Benachrichtigungen UI](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui). | Leichter zu verwalten Sie und überprüfen Sie SQL Operations Studio-Benachrichtigungen. |
| [Integrierte Terminal aufteilen](https://code.visualstudio.com/updates/v1_21#_split-terminals). | Arbeiten Sie mit mehreren open Terminals auf einmal an. |
| [Speichern von großen und geschützte Dateien](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges). | Geschützter Administrator speichern und \>256 M-Dateien in SQL Operations Studio. |
| [Verbesserte Unterstützung für große Datei](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements). | Text-Puffer-Optimierungen für große Dateien. |
| [Verbesserte Suche der Einstellungen](https://code.visualstudio.com/updates/v1_20#_settings-search). | Finden Sie problemlos die richtige Einstellung mit der Suche in natürlicher Sprache. |
| [Globale Codeausschnitte](https://code.visualstudio.com/updates/v1_20#_global-snippets). | Erstellen Sie Codeausschnitte, die Sie für alle Dateitypen verwenden können. |
| [Mehrfachauswahl Explorer](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer). | Führen Sie Aktionen für mehrere Dateien gleichzeitig. |
| [Fehler und Warnungen im Explorer](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer). | Navigieren Sie schnell zu Fehlern in Ihrer Codebasis. |
| [Ziehen und ablegen, kopieren und fügen Sie in Windows](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support). | Verschieben Sie Dateien über die geöffnete SQL Operations Studio-Fenster. |
| [Unterstützung für Git-submodul](https://code.visualstudio.com/updates/v1_20#_git-submodules). | Führen Sie die Git-Vorgänge für geschachtelte Git-Repositorys. |
| [Unterstützung für die Terminaldienste Sprachausgabe](https://code.visualstudio.com/updates/v1_20#_screen-reader-support). | Integriertes Terminal verfügt jetzt über **Bildschirm Reader optimiert** Modus. |
| [Zentriert Editor Layout](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout). | Maximieren Sie den Code, der Platz auf dem Bildschirm anzeigen. |
| [Horizontale Suchergebnisse (Vorschau)](https://code.visualstudio.com/updates/v1_21#_horizontal-search). | Sie können jetzt Ansicht in einem horizontalen Bereich angezeigt Suchergebnisse. |
| &nbsp; | &nbsp; |

Weitere Informationen: Auschecken der [Visual Studio Code Februar-Release Notes](https://code.visualstudio.com/updates/v1_21), und die [Visual Studio Code Januar – Versionsanmerkungen](https://code.visualstudio.com/updates/v1_20).

Weitere Informationen finden Sie unter den [Änderungsprotokoll](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md).

## <a name="march-2018"></a>März 2018

28. März 2018 &nbsp;  /  &nbsp; Version: 0.27.3 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *öffentliche Vorschau März* weiterhin die wichtigsten GitHub-Probleme zu beheben, und konzentriert sich auf die Verbesserung unserer Geschichte Erweiterbarkeit. Insbesondere Erweiterungs-Manager aktivieren, Verbessern der dashboardverwaltung und Bereitstellen von SQL-Agent "und" Insights-Erweiterungen. Dieses Release enthält die folgenden Verbesserungen:

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Erweitern Sie das Dashboard-Erweiterbarkeitsmodell Unterstützung im Registerkartenformat Einblicke und Bereiche der Konfiguration. | Erweiterungs-Manager ermöglicht die einfache Übernahme von Erweiterungen.<br/><br/>Erweiterungen für sp\_Whoisactive aus [whoisactive.com](http://www.whoisactive.com).<br/><br/>Weitere Informationen finden Sie unter [erweitern die Funktionalität von SQL Operations Studio](extensions.md). |
| Hinzufügen zusätzlicher [Erweiterbarkeits-APIs für die Verbindung und Objekt-Explorer](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API) Management. | &nbsp; |
| Beheben Sie wichtige Auswirkungen auf Kunden weiterhin [GitHub-Problemen](https://github.com/Microsoft/azuredatastudio/issues). | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="february-2018"></a>Februar 2018

15. Februar 2018 &nbsp;  /  &nbsp; Version: 0.26.7 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *Public Preview-Version vom Februar* enthält einige Vorschläge für Features und Fehlerkorrekturen hoher Priorität. Dieses Release enthält die folgenden Verbesserungen:

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Einführung in die automatische Update-Installation, die stellt eine Benachrichtigung bereit, wenn eine neue Version als download verfügbar ist. | &nbsp; |
| Das Dialogfeld "Verbindung" **Datenbank** Feld ist mittlerweile eine dynamisch aufgefüllt Dropdown-Liste, die eine Liste der Datenbanken aufgefüllt, die vom angegebenen Server enthält. | &nbsp; |
| Führen Sie die Verbindung Erweiterbarkeits-API. | &nbsp; |
| VS Code-Editor 1.19-Integration. | &nbsp; |
| Aktualisieren Sie JustinPealing/html-Abfrageplan Komponente einfachere Installation mehrere Verbesserungen der Abfrageplan-Viewer. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixed-issues-february-2018"></a>Behobene Probleme, Februar 2018

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

## <a name="january-2018"></a>Januar 2018

17 Januar 2018 &nbsp;  /  &nbsp; Version: 0.25.4 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *Public Preview Januar* enthält einige Vorschläge für Features und Fehlerkorrekturen hoher Priorität. Dieses Release enthält die folgenden Verbesserungen:

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Gespeicherten serververbindungen finden im Verbindungsdialogfeld. | &nbsp; |
| Aktivieren von "Hot" beenden. Beenden von "Hot" ist standardmäßig deaktiviert, finden Sie unter aktivieren ["Hot" Exit-Einstellung](settings.md#hot-exit). | &nbsp; |
| Registerkartenfärbung basierend auf Gruppe "Server". Registerkartenfärbung ist standardmäßig deaktiviert, finden Sie unter aktivieren [Registerkarte die Einstellung für die](settings.md#tab-color). | &nbsp; |
| Änderung *Servernamen* zu *Server* im Verbindungsdialogfeld. | &nbsp; |
| Korrektur unterteilt *aktuelle Abfrage ausführen* Befehl. | &nbsp; |
| Beheben Sie die Drag & Drop-wichtige Fehler Skripterstellung. | &nbsp; |
| Korrigieren Sie falsche angeheftete Menü "Start"-Symbol. | &nbsp; |
| Beheben Sie fehlende branding Symbol "Azure-Konto an. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="december-2017"></a>Dezember 2017

19. Dezember 2017 &nbsp;  /  &nbsp; Version: 0.24.1 &nbsp;  /  &nbsp; öffentliche Vorschau

Die *Public Preview-Version Dezember* umfasst verschiedene Fehlerkorrekturen für alle Featurebereiche sowie die folgenden Verbesserungen:

&nbsp;

| Ändern | Details |
| :----- | :------ |
| Erstellen Sie Dialogfeld Firewallregeln ist jetzt bei der verbindungsherstellung mit Azure SQL-Datenbank und Azure SQL Data Warehouse verfügbar. | &nbsp; |
| Zusätzliche Windows-Setup und Linux DEB und RPM-Pakete für die Installation. | &nbsp; |
| Verwalten Sie Dashboard visuelle Layout-Editor. | &nbsp; |
| *Alter-Skript als* und *Ausführen von Skripts als* Befehle. | &nbsp; |
| *Führen Sie die aktuelle Abfrage mit Istplan* Befehl. | &nbsp; |
| Integrieren Sie Visual Studio Code 1.18.1-Editor-Plattform. | &nbsp; |
| Aktivieren Sie Sideload-VSIX-Erweiterung-Dateien. | &nbsp; |
| "GO-N" Batch-Iterationssyntax zu unterstützen. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="november-2017"></a>November 2017

15. November 2017 &nbsp;  /  &nbsp; Version: 0.23.6

- Erste Version des [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="next-steps"></a>Nächste Schritte

Finden Sie in der folgenden schnellstartanleitungen für den Einstieg:

- [Verbinden und Abfragen von SQLServer](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
- [Verbinden und Abfragen von Azure Datawarehouse](quickstart-sql-dw.md)

Mitwirken an [!INCLUDE[name-sos](../includes/name-sos-short.md)]:

- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
