---
title: Was ist Azure Data Studio
titleSuffix: Azure Data Studio
description: Azure Data Studio ist ein Tool mit der kostenlose, leicht, die auf Windows, MacOS und Linux ausgeführt wird, für die Verwaltung von SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: overview
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.openlocfilehash: 00c8a5aeba30d16e2ae2f5c98290797765c9a357
ms.sourcegitcommit: 553ecea0427e4d2118ea1ee810f4a73275b40741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65620187"
---
# <a name="what-is-azure-data-studio"></a>Was ist Azure Data Studio?

Azure Data Studio ist ein plattformübergreifendes Tool für datenexperten mithilfe der Microsoft-Familie der lokalen Datenbank und cloud-datenplattformen unter Windows, MacOS und Linux.

Zuvor unter dem Namen Vorschau SQL Operations Studio veröffentlicht, bietet Studio für Azure Data eine moderne-Editor mit Intellisense, Codeausschnitte, Integration der quellcodeverwaltung und eine integrierte Terminal. Es wurde mit dem Data-Plattform Benutzer Denken Sie daran, konzipiert integriert die diagrammerstellung für Abfrageresultsets und anpassbaren Dashboards.

**[Herunterladen und installieren [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)**


## <a name="sql-code-editor-with-intellisense"></a>SQL-Code-Editor mit IntelliSense

[!INCLUDE[name-sos](../includes/name-sos-short.md)] bietet eine moderne, per Tastatur bedienbare SQL, codierumgebung, die Ihre alltäglichen Aufgaben mit integrierten Features wie Fenstern mit Registerkarten, einen umfangreichen SQL-Editor, IntelliSense, Vervollständigung von Schlüsselwörtern, Codeausschnitten, codenavigation und Datenquellen-Steuerelement erleichtert Integration (Git). Führen Sie bei Bedarf SQL-Abfragen, zeigen Sie an und speichern Sie die Ergebnisse als Text, JSON oder Excel. Bearbeiten von Daten, Ihre bevorzugten Datenbankverbindungen organisieren und Datenbankobjekte in einer vertrauten Oberfläche durchsuchen. Gewusst wie: Verwenden Sie den SQL-Editor finden Sie unter [verwenden Sie den SQL-Editor zum Erstellen von Datenbankobjekten](tutorial-sql-editor.md).

## <a name="smart-sql-code-snippets"></a>Intelligente SQL-Codeausschnitte

SQL-Codeausschnitte generieren, die richtige SQL-Syntax zum Erstellen von Datenbanken, Tabellen, Sichten, gespeicherte Prozeduren, Benutzern, Anmeldungen, Rollen, usw., und klicken Sie zum Aktualisieren vorhandener Datenbankobjekte. Intelligente Codeausschnitte verwenden, um Kopien der Datenbank für Entwicklungs- oder Testzwecke, schnell zu erstellen und zu generieren und Ausführen erstellen, und fügen die Skripts.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] stellt auch Funktionen zum Erstellen von benutzerdefinierter SQL-Codeausschnitten bereit. Weitere Informationen finden Sie unter [erstellen und Verwenden von Codeausschnitten](code-snippets.md).


## <a name="customizable-server-and-database-dashboards"></a>Anpassbare Server und Datenbank-Dashboards

Erstellen Sie umfangreiche, anpassbare Dashboards zum Überwachen und schnell beheben von Leistungsengpässen in Ihren Datenbanken. Einblicke, Dashboards und Gadgets-Datenbank (und Server), finden Sie unter [Verwalten von Servern und Datenbanken mit einblickwidgets](insight-widgets.md).

## <a name="connection-management-server-groups"></a>Verbindungsverwaltung (Servergruppen)

Servergruppen bieten eine Möglichkeit zum Organisieren von Verbindungsinformationen für die Server und Datenbanken, mit denen Sie zusammenarbeiten. Weitere Informationen finden Sie unter [Servergruppen](server-groups.md).

## <a name="integrated-terminal"></a>Integriertes Terminal

Verwenden Sie Ihre bevorzugten Befehlszeilentools (beispielsweise Bash, PowerShell, Sqlcmd und Bcp, per ssh) im integrierten Terminal-Fenster innerhalb der [!INCLUDE[name-sos](../includes/name-sos-short.md)] -Benutzeroberfläche. Weitere Informationen zu integrierten Terminal finden Sie unter [integriertes Terminal](integrated-terminal.md).

## <a name="extensibility-and-extension-authoring"></a>Erweiterbarkeit und der Erweiterung erstellen

Verbessern der [!INCLUDE[name-sos](../includes/name-sos-short.md)] durch Erweitern der Funktionalität der Basisinstallation auftreten. [!INCLUDE[name-sos](../includes/name-sos-short.md)] stellt Erweiterungspunkte für Aktivitäten zur datenverwaltung sowie Unterstützung für das Erstellen von Erweiterung bereit.

Informationen über die Erweiterbarkeit in [!INCLUDE[name-sos](../includes/name-sos-short.md)], finden Sie unter [Erweiterbarkeit](extensibility.md).
Informationen zum Erstellen von Erweiterungen finden Sie unter [Extension authoring](extension-authoring.md).

## <a name="feature-comparison-with-sql-server-management-studio-ssms"></a>Vergleich der Features mit SQL Server Management Studio (SSMS)

**Verwenden von Azure Data Studio, wenn Sie:**
- Unter MacOS oder Linux ausgeführt werden müssen
- Eine Verbindung mit einem SQL Server-2019 big Data-cluster
- Verbringen Sie die meiste Zeit bearbeiten oder Ausführen von Abfragen
- Benötigen Sie die Möglichkeit, schnell Diagramm- und Visualisieren von Resultsets
- Die meisten administrative Aufgaben über das integrierte Terminal mithilfe von Sqlcmd oder Powershell können ausgeführt werden.
- Müssen Sie minimale für die Assistenten-Umgebungen
- Müssen Sie nicht tief administrative Konfiguration übernehmen

**SQL Server Management Studio verwenden, wenn Sie:**
- Aufgaben für die datenbankverwaltung verbringen Sie die meiste Zeit
- Eine umfassende administrative Konfiguration durchführen
- Machen die sicherheitsverwaltung, einschließlich benutzerverwaltung, sicherheitsrisikobewertung und Konfiguration von Sicherheitsfunktionen
- Die Berichte für SQL Server Query Store verwenden
- Müssen Sie Performance tuning Berater und Dashboards verwenden
- Import/Export von DACPAC-Dateien durchführen
- Benötigen Sie Zugriff auf registrierte Server, und steuern möchten, SQL Server-Dienste auf Windows

### <a name="shell"></a>Shell

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Azure-Anmeldung|Ja|Ja|
|Dashboard|Ja||
|Erweiterungen|Ja||
|Integriertes Terminal|Ja||
|Objekt-Explorer|Ja|Ja|
|Skripterstellung für Objekte|Ja|Ja|
|Projektsystem|Ja||
|Wählen Sie aus der Tabelle|Ja|Ja|
|Quellcodeverwaltung|Ja||
|Aufgabenbereich|Ja||
|Design|Ja||
|Dunkel-Modus|Ja||
|Azure-Ressourcen-Explorer|Vorschau||
|Assistent zum Generieren von Skripts||Ja|
|Importieren/Exportieren DACPAC-Datei||Ja|
|Objekt – Eigenschaften||Ja|
|Tabellen-Designer||Ja|


### <a name="query-editor"></a>Abfrage-Editor

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Diagramm-Viewer|Ja||
|Exportieren Sie Ergebnisse in CSV, JSON, XLSX|Ja||
|IntelliSense|Ja|Ja|
|Codeausschnitte|Ja|Ja|
|Plan angezeigt werden|Vorschau|Ja|
|Clientstatistiken||Ja|
|Live-Abfragestatistik||Ja|
|Abfrageoptionen||Ja|
|Ergebnisse in Datei||Ja|
|Ergebnisse in Text||Ja|
|Räumliche Viewer||Ja|
|SQLCMD||Ja|

### <a name="operating-system-support"></a>Betriebssystemunterstützung

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Linux|Ja||
|macOS|Ja||
|Windows|Ja|Ja|

### <a name="data-engineering"></a>Datentechnik

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Erstellen externer Tabellen-Assistent|Vorschau||
|HDFS-Integration|Vorschau||
|Notebooks|Vorschau||

### <a name="database-administration"></a>Datenbankverwaltung

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Sicherung / Wiederherstellung|Ja|Ja|
|Flatfile-Datei importieren|Vorschau|Ja|
|SQL-Agent|Vorschau|Ja|
|SQL Profiler|Vorschau|Ja|
|Always On||Ja|
|Always Encrypted||Ja|
|Assistent zum Kopieren von Daten||Ja|
|Daten-Datenbankoptimierungsratgeber||Ja|
|Fehler-Protokoll-Viewer||Ja|
|Wartungspläne||Ja|
|Multi-Server-Abfrage||Ja|
|Richtlinienbasierte Verwaltung||Ja|
|PolyBase||Ja|
|Abfragespeicher||Ja|
|Registrierte Server||Ja|
|Replikation||Ja|
|Sicherheitsverwaltung||Ja|
|Service Broker||Ja|
|SQL Mail||Ja|
|Template Explorer||Ja|
|Sicherheitsrisikobewertung||Ja|
|XEvent-Verwaltung||Ja|

## <a name="next-steps"></a>Nächste Schritte

- [Herunterladen und installieren [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)
- [Verbinden und Abfragen von SQL Server](quickstart-sql-server.md)
- [Verbinden und Abfragen von Azure SQL-Datenbank](quickstart-sql-database.md)
