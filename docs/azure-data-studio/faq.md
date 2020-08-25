---
title: FAQ zu Azure Data Studio
description: Hier finden Sie Antworten auf häufig gestellte Fragen zu Azure Data Studio, z. B. „Was ist Azure Data Studio?“, „Wer sollte Azure Data Studio verwenden?“ und „Wie viel kostet Azure Data Studio?“.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 1413903521019e9b2c95b11143d7e0039fc8e103
ms.sourcegitcommit: dc8a30a4a27e15fc6671ca2674da9b7c637ec255
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88745970"
---
# <a name="azure-data-studio-faq"></a>FAQ zu Azure Data Studio

## <a name="what-is-azure-data-studio"></a>Was ist Azure Data Studio?

Azure Data Studio ist eine neue plattformübergreifende Open-Source-Desktopumgebung für Datenexperten, die zu den Azure Data-Produkten lokaler und cloudbasierter Datenplattformen unter Windows, macOS und Linux gehören. Azure Data Studio wurde zuvor in einer Vorschauversion unter dem Namen SQL Operations Studio veröffentlicht und bietet eine moderne Editor-Funktion mit einem integrierten Terminal sowie einer schnellen Integration von IntelliSense, Codeausschnitten und der Quellcodeverwaltung. Das Tool wurde speziell für die Bedürfnisse der Benutzer von Datenplattformen konzipiert und bietet eine integrierte Diagrammdarstellung von Abfrageresultsets sowie anpassbare Dashboards.

Studien haben ergeben, dass die Benutzer von SQL Server Management Studio (SSMS) viel mehr Zeit mit der Bearbeitung von Abfragen verbringen als mit jeder anderen Aufgabe. Aus diesem Grund standen bei der Entwicklung von Azure Data Studio die Funktionen im Mittelpunkt, die am meisten verwendet werden. Zusätzliche Funktionen stehen als optionale Erweiterungen für das Produkt zur Verfügung. Dadurch kann jeder Benutzer seine Umgebung an die Workflows anpassen, die er am häufigsten verwendet.

## <a name="how-much-does-azure-data-studio-cost"></a>Wie viel kostet Azure Data Studio?

Azure Data Studio ist sowohl bei privater als auch bei kommerzieller Verwendung kostenlos.

## <a name="who-should-use-azure-data-studio"></a>Wer sollte Azure Data Studio verwenden?

Grundsätzlich kann jeder Azure Data Studio verwenden. Das Tool wurde jedoch in erster Linie dafür entwickelt, um Aufgaben zu vereinfachen, die von Datenbankentwicklern, Datenbankadministratoren, Systemadministratoren und unabhängigen Softwareanbietern durchgeführt werden.

## <a name="what-can-i-do-with-azure-data-studio"></a>Wofür kann ich Azure Data Studio verwenden?

Azure Data Studio basiert auf Visual Studio Code und bietet bei der Arbeit mit SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse einfache, moderne Funktionen für den Codeworkflow, bei denen der Fokus auf der Tastatur liegt. Azure Data Studio erleichtert die wichtigsten Funktionen, die Sie regelmäßig einsetzen, mithilfe von integrierten Features wie mehreren Registerkartenfenstern, einem umfangreichen SQL-Editor, IntelliSense, der Vervollständigung von Schlüsselwörtern, Codeausschnitten, Codenavigation und der Integration der Quellcodeverwaltung (Git und TFS). Sie können bedarfsgesteuerte Abfragen ausführen, Ergebnisse in Textformaten oder im JSON- oder Excel-Format abrufen und speichern, Daten bearbeiten, bevorzugte Datenbankverbindungen organisieren und verwalten sowie Datenbankobjekte auf einer vertrauten Benutzeroberfläche durchsuchen.

Sie können die von Ihnen bevorzugten Befehlszeilentools (z. B. Bash, PowerShell, sqlcmd, bcp, psql und ssh) auf der Azure Data Studio-Benutzeroberfläche direkt im Fenster „Integriertes Terminal“ verwenden. Sie können ganz einfach CREATE- und INSERT-Skripts für Ihr Datenbankobjekt erstellen und ausführen, um für die Entwicklung oder für Tests Kopien Ihrer Datenbank zu erstellen. Steigern Sie Ihre Produktivität durch intelligente Codeausschnitte und umfassende grafische Funktionen für die Erstellung neuer Datenbanken und Datenbankobjekte (z. B. Tabellen, Sichten, gespeicherte Prozeduren, Benutzer, Anmeldeinformationen, Rollen usw.) oder für das Aktualisieren von Datenbankobjekten. Sie können umfangreiche anpassbare Dashboards verwenden, um Leistungsengpässe in Ihren lokalen Datenbanken, in Azure oder in einer beliebigen Cloud zu überwachen und Probleme schnell zu beheben.

Azure Data Studio bietet einheitliche Funktionen zum Sichern und Wiederherstellen Ihrer Datenbanken. In Zukunft sollen auch für SQL Server Always On-Verfügbarkeitsgruppen unterstützt werden, damit Sie diese für Ihre unternehmenskritischen SQL Server-Datenbanken problemlos konfigurieren, überwachen und Probleme beheben können sowie im Falle eines Notfalls schnell ein Failover auf eine sekundäre Datenbank durchführen können. Azure Data Studio wurde entwickelt, damit der DevOps-Lebenszyklus aller Datenbanken auf sämtlichen Betriebssystemen produktiver gestaltet werden kann. So haben Sie immer die Kontrolle und können Risiken mindern, Probleme schneller lösen und kontinuierlich Ergebnisse liefern, die die Erwartungen der Kunden übertreffen.

## <a name="is-azure-data-studio-open-source"></a>Ist Azure Data Studio ein Open-Source-Produkt?

Der Quellcode für Azure Data Studio und die zugehörigen Datenanbieter sind auf GitHub verfügbar. Der Quellcode für das Front-End von Azure Data Studio (basiert auf Visual Studio Code) ist Gegenstand eines Lizenzvertrags für Quellcode, gemäß dem die Software zwar geändert und verwendet, aber nicht weitervertrieben oder auf einem Clouddienst gehostet werden darf. Den Quellcode für die Datenanbieter finden Sie in der MIT-Lizenz unter [https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-we-plan-to-open-source-ssms"></a>Soll es in Zukunft eine Open-Source-Version von SSMS geben?

Nein. Die CLI für mehrere Betriebssysteme und die GUI-Tools der nächsten Generation werden allerdings als Open-Source-Produkte angeboten. Beispielsweise sind für die MSSQL-Erweiterung für VS Code, den MSSQL-Scripter und die MSSQL-CLI in GitHub Open-Source-Versionen verfügbar. Der Quellcode für Azure Data Studio ist auf GitHub verfügbar.  

## <a name="now-that-there-is-azure-data-studio-does-microsoft-plan-to-deprecate-ssms-and-ssdt"></a>Plant Microsoft nun, da es Azure Data Studio gibt, SSMS und SSDT als veraltet zu kennzeichnen? 

Nein. Wir werden zusätzlich zur nächsten Generation der CLI für mehrere Betriebssysteme und mehrere Datenbanken und der GUI-Tools weiter in die Vorzeigetools von Windows (SSMS, SSDT, PowerShell) investieren. Ziel ist es, Kunden die Möglichkeit zu bieten, für alle Szenarios die Tools und Plattformen zu verwenden, mit denen sie gern arbeiten. Der Schwerpunkt von Azure Data Studio liegt in erster Linie auf den Funktionen für die Bearbeitung von Abfragen und die Datenentwicklung, da diese Studien zufolge die am häufigsten in SQL Server Management Studio verwendet werden. Zusätzlich sind weitere tolle administrative Funktionen wie die Sicherung, Wiederherstellung, Agent-Auftragsverwaltung und Serverprofilerstellung auch als Erweiterungen in Azure Data Studio verfügbar. Azure Data Studio kann plattformübergreifend verwendet werden und ermöglicht es Benutzern, mit der Plattform ihrer Wahl zu arbeiten. SQL Server Management Studio bietet jedoch weiterhin die meisten administrativen Funktionen und bleibt unser wichtigstes Tool für Aufgaben zur Plattformverwaltung. 

## <a name="when-should-i-use-azure-data-studio-vs-sql-server-management-studio"></a>Wann sollte ich Azure Data Studio und wann besser SQL Server Management Studio verwenden?

*Verwenden Sie Azure Data Studio in folgenden Fällen*:

- Sie verbringen einen Großteil Ihrer Zeit mit der Bearbeitung oder Ausführung von Abfragen.
- Sie benötigen eine Funktion, mit der Sie Resultsets schnell visualisieren und in Diagrammen darstellen können.
- Sie können die meisten administrativen Aufgaben mit sqlcmd oder PowerShell über das integrierte Terminal ausführen.
- Sie benötigen nur wenige Assistentenfunktionen.
- Sie müssen keine detaillierten administrativen oder plattformbezogenen Konfiguration durchführen.
- Sie verwenden macOS oder Linux.

*Verwenden Sie SQL Server Management Studio in folgenden Fällen*:

- Sie verbringen einen Großteil Ihrer Zeit mit Aufgaben für die Datenbankverwaltung.
- Sie führen komplexe administrative Konfigurationen oder Plattformkonfigurationen durch.
- Die Sicherheitsverwaltung, einschließlich der Benutzerverwaltung, der Sicherheitsrisikobewertung und der Konfiguration von Sicherheitsfeatures, gehört zu Ihren Aufgaben.
- Sie benötigen Ratgeber und Dashboards für die Leistungsoptimierung.
- Sie verwenden Datenbankdiagramme und Tabellen-Designer.
- Sie importieren bzw. exportieren DACPAC-Pakete.
- Sie benötigen Zugriff auf registrierte Server.
- Sie verwenden den sqlcmd-Modus, Liveabfragestatistiken oder Clientstatistiken.

## <a name="feature-comparison"></a>Featurevergleich

### <a name="shell-features"></a>Shellfeatures

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Azure-Anmeldung|Ja|Ja|
|Dashboard|Ja| |
|Erweiterungen|Ja| |
|Integriertes Terminal|Ja||
|Objekt-Explorer|Ja|Ja|
|Skripterstellung für Objekte|Ja|Ja|
|Projektsystem|Ja||
|Aus Tabelle auswählen|Ja|Ja|
|Quellcodeverwaltung|Ja||
|Aufgabenbereich|Ja||
|Designs|Ja||
|Dunkler Modus|Ja||
|Azure-Ressourcen-Explorer|Vorschau||
|Assistent zum Generieren von Skripts||Ja
|DACPACs importieren/exportieren||Ja|
|Objekteigenschaften||Ja|
|Tabellen-Designer||Ja|

### <a name="query-editor"></a>Abfrage-Editor

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Diagrammviewer|Ja||
|Ergebnisse im CSV-, JSON- oder XLSX-Format exportieren|Ja||
|IntelliSense|Ja|Ja|
|Codeausschnitte|Ja|Ja|
|Plan anzeigen|Vorschau|Ja|
|Clientstatistiken||Ja|
|Liveabfragestatistiken||Ja|
|Abfrageoptionen||Ja|
|Ergebnisse in Datei||Ja|
|Ergebnisse in Text||Ja|
|Räumlicher Viewer||Ja|
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
|External Data Wizard (Assistent für externe Daten)|Vorschau||
|HDFS-Integration|Vorschau||
|Notebooks|Vorschau||

### <a name="database-administration"></a>Datenbankverwaltung

|Funktion|Azure Data Studio|SSMS|
|:---|:---|:---|
|Sicherung/Wiederherstellung|Ja|Ja|
|Flatfile-Import|Vorschau|Ja|
|SQL-Agent|Vorschau|Ja|
|SQL Profiler|Vorschau|Ja|
|Always On||Ja|
|Always Encrypted||Ja|
|Assistent zum Kopieren von Daten||Ja|
|Ratgeber für die Datenoptimierung||Ja|
|Datenbankdiagramme||Ja|
|Fehlerprotokollanzeige||Ja|
|Wartungspläne||Ja|
|Abfrage mehrerer Server||Ja|
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


## <a name="azure-data-studio-is-missing-a-feature-that-is-in-ssmsssdt-will-you-add-it"></a>In Azure Data Studio fehlt eine Funktion, die in SSMS bzw. SQL Server Data Tools (SSDT) enthalten ist. Soll das in Zukunft geändert werden?

Dies ist vom Szenario und von den Anforderungen des Kunden bzw. des Unternehmens abhängig. Machen Sie einen Vorschlag auf [GitHub](https://github.com/microsoft/azuredatastudio/issues), damit wir die Anfragen besser priorisieren können.

## <a name="i-understand-azure-data-studio-and-the-mssql-extension-for-vs-code-are-powered-by-a-new-tools-service-that-uses-smo-apis-under-the-covers-is-smo-available-on-linux-and-macos"></a>Azure Data Studio und die MSSQL-Erweiterung für VS Code werden von einem neuen Tooldienst unterstützt, der im Hintergrund SQL Server Management Objects-APIs (SMO) verwendet. Ist SMO unter Linux und macOS verfügbar?

Die SMO-APIs können unter Linux oder macOS noch nicht verarbeitet werden. Wir haben einen Teil der SMO-APIs auf .NET Core übertragen, da diese für Azure Data Studio benötigt wurden, und haben in unserer Roadmap zusätzliche Erweiterungen angegeben. SQL Tools Service finden Sie auf GitHub unter [https://github.com/Microsoft/sqltoolsservice](https://github.com/Microsoft/sqltoolsservice).

## <a name="do-you-plan-to-port-the-dacfx-apis-andor-sqlpackageexe-andor-ssdt-to-linux-and-macos"></a>Ist es geplant, die APIs für Microsoft SQL Server Data-Tier Application Framework (DACFx) und/oder die Datei „sqlpackage.exe“ und/oder SSDT für Linux und macOS zu integrieren?

Langfristig ist dies geplant. Machen Sie einen Vorschlag auf [GitHub](https://github.com/microsoft/azuredatastudio/issues), damit wir die Anfragen besser priorisieren können.

## <a name="will-sql-powershell-cmdlets-be-available-on-linux-and-macos"></a>Werden in Zukunft SQL PowerShell-Cmdlets unter Linux und macOS zur Verfügung stehen?

SQL PowerShell ist derzeit über den PowerShell-Katalog verfügbar und kann unter Windows zusammen mit SQL Server-Instanzen verwendet werden. Dabei spielt es keine Rolle, wo diese Instanzen ausgeführt werden, auch die Ausführung unter Linux stellt kein Problem dar. Wir planen, die SQL PowerShell-Cmdlets unter Linux und macOS in Zukunft anzubieten. Machen Sie einen Vorschlag auf [GitHub](https://github.com/microsoft/azuredatastudio/issues), damit wir die Anfragen besser priorisieren können.

## <a name="who-usually-uses-azure-data-studio"></a>Wer verwendet in der Regel Azure Data Studio?

In der Regel wird Azure Data Studio von Entwicklern und Datenbankadministratoren verwendet.

## <a name="does-azure-data-studio-integrate-with-azure-sql-data-warehouse"></a>Kann Azure Data Studio in Azure SQL Data Warehouse integriert werden?

Ja. Die Unterstützung von Azure Data Studio für Azure SQL Data Warehouse befindet sich derzeit genauso wie Azure SQL Managed Instance und Big-Data-Cluster für SQL Server 2019 in der Vorschauphase.

## <a name="why-is-azure-data-studio-important-for-the-new-version-of-sql-server"></a>Warum ist Azure Data Studio wichtig für die neue Version von SQL Server?

Da die Funktionen von SQL Server auf den Big-Data-Bereich ausgeweitet werden sollen, werden neue Features benötigt. Aus diesem Grund gibt es ab heute eine neue Vorschauversion von Azure Data Studio, die Big-Data-Cluster für SQL Server unterstützt. Diese Version umfasst u. a. die erste Notebookfunktion aller SQL Server-Tools und einen neuen Assistenten für die Erstellung externer Tabellen, mit dem einfacher und schneller über Remoteinstanzen von SQL Server und Oracle auf Daten zugegriffen werden kann.
