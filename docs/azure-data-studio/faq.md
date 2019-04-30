---
title: HÄUFIG GESTELLTE FRAGEN
titleSuffix: Azure Data Studio
description: Häufig gestellte Fragen (FAQ) zu Azure Data Studio ein.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 129e7de66e896e1f452c5d68fc4891d9cc5eafa3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238297"
---
# <a name="includeazure-data-studioincludesname-sosmd-faq"></a>[!INCLUDE[Azure Data Studio](../includes/name-sos.md)] FAQ

## <a name="what-is-azure-data-studio"></a>Was ist Azure Data Studio?

Azure Data Studio ist eine neue Open-source-Cross-Platform-desktop-Umgebung für Data-Experten, die mit der Daten in Azure-Familie von lokalen und cloud-datenplattformen unter Windows, MacOS und Linux. Zuvor unter dem Namen Vorschau SQL Operations Studio veröffentlicht, extrem Studio für Azure Data-Angebote, die ein modernen Editor Erfahrung im Umgang mit schnellen IntelliSense, Codeausschnitte, Integration der quellcodeverwaltung und eine integrierte Terminal. Es wurde mit dem Data-Plattform Benutzer Denken Sie daran, konzipiert integriert die diagrammerstellung für Abfrageresultsets und anpassbaren Dashboards.

Untersuchung ergab, dass Benutzer bedeutend mehr Zeit, die abfragebearbeitung als für andere Aufgaben mit SQL Server Management Studio gearbeitet haben. Aus diesem Grund wurde Azure Data Studio entwickelt, um umfassend auf die Funktionalität konzentrieren, die am häufigsten mit zusätzlichen Funktionen, die als optionale Erweiterungen in das Produkt zur Verfügung gestellt werden. Dadurch kann jeder Benutzer ihrer Umgebung auf die Workflows anpassen, die sie am häufigsten verwenden.


## <a name="how-much-does-azure-data-studio-cost"></a>Wie viel kostet Azure Data Studio?

Azure Data Studio ist kostenlos für private oder gewerbliche Zwecke verwenden.

## <a name="who-should-use-azure-data-studio"></a>Wer sollte die Azure Data Studio verwenden

Jeder Benutzer kann Azure Data Studio verwenden. Es soll jedoch Entwickler, Datenbankadministratoren, Systemadministratoren und unabhängige Softwarehersteller ausgeführte Aufgaben zu vereinfachen.

## <a name="what-can-i-do-with-azure-data-studio"></a>Was kann ich mit Azure Data Studio tun?

Azure Data Studio basiert auf Visual Studio Code und bietet eine einfache, Tastaturfokus installationsworkflows modernen Code beim Arbeiten mit SQL Server, Azure SQL-Datenbank, Azure SQL Data Warehouse. Azure Data Studio macht die Core-Benutzeroberflächen, die Sie täglich, einfach und leicht mit integrierten Features wie Fenstern mit Registerkarten, einen umfangreichen SQL-Editor, IntelliSense, Vervollständigung von Schlüsselwörtern, Codeausschnitten und Navigation in Code und Integration der quellcodeverwaltung (Git nutzen und TFS). Sie können bedarfsgesteuerte Abfragen ausführen, anzeigen & Ergebnisse als Text, JSON oder Excel speichern, Bearbeiten von Daten, organisieren und verwalten Ihre bevorzugten Datenbankverbindungen und Datenbankobjekte in einer vertrauten Oberfläche durchsuchen.

Verwenden Sie Ihre bevorzugten Befehlszeilentools (beispielsweise Bash, PowerShell "," Sqlcmd "," Bcp "," Psql, per ssh) im integrierten Terminal-Fenster direkt in der Azure Data Studio-Benutzeroberfläche. Einfach zu generieren und Ausführen erstellen und Einfügen-Skripts für Datenbankobjekte, Kopien Ihrer Datenbank für Entwicklungs- oder Testzwecke zu erstellen. Steigern Sie Ihre Produktivität mit intelligenter Code Snippets und eine umfassende grafische Benutzeroberflächen, die neue Datenbanken und Datenbankobjekte (z. B. Tabellen, Sichten, gespeicherte Prozeduren, Benutzern, Anmeldungen, Rollen, usw.) zu erstellen oder vorhandene Datenbankobjekte zu aktualisieren. Verwendung umfangreiche anpassbare Dashboards überwachen und Leistungsengpässe in Ihrer lokalen Datenbanken, in Azure oder jede andere Cloud schnell zu beheben.

Azure Data Studio bietet eine konsistente Umgebung zum Sichern und Wiederherstellen Ihrer Datenbanken. Mit geplante Unterstützung für SQL Server Always On-Verfügbarkeitsgruppen können Sie ganz einfach konfigurieren, überwachen und Problembehandlung von Verfügbarkeitsgruppen für Ihre unternehmenskritischen SQL Server-Datenbanken und schnell ein Failover auf eine sekundäre Datenbank während eines Notfalls. Azure Data Studio wurde entwickelt, um in den DevOps-Lebenszyklus Ihrer Datenbanken Ihrer Wahl unter den Betriebssystemen Ihrer Wahl produktiver arbeiten können. Daher, Sie können jederzeit steuern, und Sie Risiken verringern, Probleme schneller zu lösen und liefern Sie fortlaufend Qualität, die Erwartungen der Kunden überschreiten können.

## <a name="is-azure-data-studio-open-source"></a>Ist Azure Data Studio Open-Source?

Der Quellcode für Azure Data Studio und der Datenanbieter ist auf GitHub verfügbar. Der Quellcode für das Front-End-Azure-Daten-Studio (die basierend auf Visual Studio Code) ist verfügbar unter ein Quellcode-Endbenutzer-Lizenzvertrag, die Rechte zum Ändern und verwenden Sie die Software, jedoch nicht zu verteilen oder hosten Sie es in einem Clouddienst bereitstellt. Der Quellcode für die Datenanbieter finden Sie unter MIT-Lizenz auf [ https://github.com/Microsoft/sqltoolsservice ](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-we-plan-to-open-source-ssms"></a>Möchten wir die open Source SSMS?

Nein. Allerdings sind der nächsten Generation betriebssystemübergreifenden-CLI und GUI-Tools mit open-Source. Beispielsweise sind die Mssql-Erweiterung für Visual Studio Code und Mssql-Skripter Msql-CLI für alle open Source auf GitHub. Der Quellcode für Azure Data Studio ist auf GitHub verfügbar.  

## <a name="now-that-there-is-azure-data-studio-does-microsoft-plan-to-deprecate-ssms-and-ssdt"></a>Nun, da Azure Data Studio, plant Microsoft, SSMS und SSDT als veraltet kennzeichnen? 

Nein. Zusätzlich zu die nächste Generation von betriebssystemübergreifenden und Multi-DB-CLI und GUI-Tools weiterhin Investitionen in die wichtigsten Windows-Tools (SSMS, SSDT, PowerShell). Ziel ist es, Kunden anbieten, verwenden Sie die gewünschten Tools für die Plattformen ihrer Wahl für ihre Szenarien. Azure Data Studio enger konzentriert sich auf die Erfahrungen mit abfragebearbeitung und Datenentwicklung, die Untersuchung zeigte ist die am meisten verwendeten-Funktion in SQL Server Management Studio durch eine Zehnerpotenz. Außerdem stehen zusätzliche hochwertige Verwaltungsfunktionen wie z. B. Sicherung, Wiederherstellung, Agent-auftragsverwaltung und erstellen als Erweiterungen in Azure Data Studio zur Verfügung. Azure Data Studio ist auch plattformübergreifende, sodass Benutzer auf der Plattform Ihrer Wahl arbeiten. SQL Server Management Studio wird allerdings weiterhin bietet die breiteste Palette an Verwaltungsfunktionen, und der bleibt das führende Tool für Verwaltungsaufgaben für die Plattform. 

## <a name="when-should-i-use-azure-data-studio-vs-sql-server-management-studio"></a>Wenn sollte ich mich mit Azure Data Studio und SQL Server Management Studio?

*Verwenden von Azure Data Studio, wenn Sie:*

- Verbringen Sie die meiste Zeit bearbeiten oder Ausführen von Abfragen.
- Benötigen Sie die Möglichkeit, schnell Diagramm- und Visualisieren von Resultsets.
- Können die meisten administrative Aufgaben über das integrierte Terminal mithilfe von Sqlcmd oder Powershell ausführen.
- Müssen Sie minimale Assistenten arbeiten.
- Müssen Sie sich nicht für umfassende administrative oder verwandte Plattformkonfiguration.
- Unter MacOS oder Linux ausgeführt werden müssen.

*SQL Server Management Studio verwenden, wenn Sie:*

- Verbringen Sie die meiste Zeit Aufgaben für die datenbankverwaltung.
- Komplexe Verwaltungs- oder Platform-Konfiguration durchführen.
- Sicherheitsverwaltung, einschließlich benutzerverwaltung, sicherheitsrisikobewertung und Konfiguration von Sicherheitsfunktionen durchführen.
- Müssen Sie Performance tuning Berater und Dashboards verwenden.
- Verwenden Sie Datenbankdiagramme und Tabellen-Designer.
- Import/Export von DACPAC-Dateien durchführen.
- Benötigen Sie Zugriff auf registrierte Server.
- Stellen Sie die Sqlcmd-Modus verwenden, live-Abfragestatistik oder Clientstatistiken.

## <a name="feature-comparison"></a>Funktionsvergleich zwischen "

### <a name="shell-features"></a>Shell-features

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Azure-Anmeldung|Ja|Ja|
|Dashboard|Ja| |
|Erweiterungen|Ja| |
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
|Assistent zum Generieren von Skripts||Ja
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
|T-SQL-Debugger||Ja|

### <a name="operating-system-support"></a>Betriebssystemunterstützung

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Windows|Ja|Ja|
|macOS|Ja||
|Linux|Ja||

### <a name="data-engineering"></a>Datentechnik

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Externe Daten-Assistenten|Vorschau||
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
|Datenbankdiagramme||Ja|
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


## <a name="azure-data-studio-is-missing-a-feature-that-is-in-ssmsssdt-will-you-add-it"></a>Azure Data Studio fehlt ein Feature, das in SSMS/SSDT ist. Fügen Sie sie hinzu?

Es hängt Szenario &/Geschäftsbetrieb des Kunden erforderlich. Zum priorisieren, melden Sie einen Vorschlag auf [GitHub](https://github.com/microsoft/azuredatastudio/issues).

## <a name="i-understand-azure-data-studio-and-the-mssql-extension-for-vs-code-are-powered-by-a-new-tools-service-that-uses-smo-apis-under-the-covers-is-smo-available-on-linux-and-macos"></a>Mir ist bewusst, dass es sich bei Studio für Azure Data und die Mssql-Erweiterung für Visual Studio Code durch einen neuen Dienst für die Tools basieren, die SMO-APIs im Hintergrund verwendet. Ist SMO wird unter Linux und MacOS verfügbar?

Die SMO-APIs sind noch nicht verfügbar unter Linux oder MacOS in einer Weise genutzt werden. Wir haben eine Teilmenge der .NET Core, die wir brauchten für Azure Data Studio, und wir erweitern möchten, als Teil der Roadmap für die SMO-APIs portiert. Der SQL-Tools-Dienst ist auf GitHub: [ https://github.com/Microsoft/sqltoolsservice ](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-you-plan-to-port-the-dacfx-apis-andor-sqlpackageexe-andor-ssdt-to-linux-and-macos"></a>Möchten Sie die DACFx-APIs und/oder sqlpackage.exe und/oder SSDT für Linux und MacOS-port?

Es ist für die langfristige Roadmap. Zum priorisieren, melden Sie einen Vorschlag auf [GitHub](https://github.com/microsoft/azuredatastudio/issues).

## <a name="will-sql-powershell-cmdlets-be-available-on-linux-and-macos"></a>Werden SQL PowerShell-Cmdlets werden unter Linux und MacOS verfügbar sein?

SQL PowerShell ist auf dem PowerShell-Katalog erhältlich und können Sie sie in Windows mit SQL Server auf einem beliebigen Standort, einschließlich SQL unter Linux funktioniert. Befindet sich Angebot SQL PowerShell-Cmdlets auf Linux und MacOS in der Roadmap enthalten. Zum priorisieren, melden Sie einen Vorschlag auf [GitHub](https://github.com/microsoft/azuredatastudio/issues).

## <a name="who-usually-uses-azure-data-studio"></a>Wer verwendet in der Regel Studio für Azure Data?

Entwickler und Datenbankadministratoren sind in der Regel die Benutzer von Azure Data Studio.

## <a name="does-azure-data-studio-integrate-with-azure-sql-data-warehouse"></a>Integrieren Azure Data Studio lässt sich mit Azure SQL Data Warehouse?

Ja. Azure Data Studio-Unterstützung für Azure SQL Data Warehouse befindet sich derzeit in der Vorschau, zusammen mit Azure SQL-Datenbank verwaltete Instanz und SQL Server 2019 Big Data.

## <a name="why-is-azure-data-studio-important-for-the-new-version-of-sql-server"></a>Warum ist Azure Data Studio wichtig, für die neue Version von SQL Server?

Wie SQL Server seine Funktionen in den Big Data-Bereich erweitert wird, benötigt es neuen Tools unterstützen die Anwendungsfälle. Aus diesem Grund wird Studio für Azure Data noch heute eine neue Benutzeroberfläche für die Vorschau der Unterstützung für SQL Server Big Data, einschließlich der ersten Auslieferung jemals Notebook-Benutzeroberfläche in das SQL Server-Toolset, und einen neuen Create External Table-Assistenten, die Zugriff auf Daten vom remote-SQL stellt Server- und Oracle-Instanzen schnell und einfach.
