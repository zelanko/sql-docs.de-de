---
title: SQL-Tools und Hilfsprogramme für SQLServer, Azure SQL-Datenbank und Azure SQL Datawarehouse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/19/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 84cebceddc18ee3d288226ebd00bc86ea25ac926
ms.sourcegitcommit: eb1f3a2f5bc296f74545f17d20c6075003aa4c42
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190990"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>SQL-Tools und Hilfsprogramme für SQLServer, Azure SQL-Datenbank und Azure SQL Datawarehouse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Zum Verwalten ("Abfrage", "überwachen", "usw.") Ihrer Datenbank, die Sie benötigen ein Tool. Während Ihre Datenbanken ausgeführt werden können, in der Cloud, die auf Windows oder auf [Linux](../linux/sql-server-linux-overview.md), Ihr Tool muss nicht auf derselben Plattform wie die Datenbank ausgeführt. 

Stehen viele Datenbanktools zur Verfügung, damit dieser Artikel Beschreibungen und Verweise auf einige der verfügbaren Tools enthält, für die Arbeit mit Ihrer SQL-Datenbanken. Informationen dazu, welches Tool Sie benötigen, finden Sie unter [welches Tool soll ich verwenden?](#which-tool-should-i-choose).


## <a name="gui-tools-to-manage-databases"></a>GUI-Tools zum Verwalten von Datenbanken  

Im folgenden sind die wichtigsten grafische Benutzeroberfläche (GUI) Tools:

| Tool | Beschreibung | Ausgeführt wird |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] ist eine kostenlose, leicht-Tool zum Verwalten von Datenbanken aus, wo sie ausgeführt werden. Diese Preview-Version stellt die Datenbank-Management-Funktionen, einschließlich einer erweiterten Transact-SQL-Editor und anpassbare Einblicke in den Betriebszustand der Datenbanken bereit. | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] unter Windows, MacOS und Linux ausgeführt wird**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Verwenden Sie SQL Server Management Studio (SSMS), um Abfragen, Entwerfen und Verwalten Ihrer SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse. | **SSMS wird unter Windows ausgeführt**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Verwandeln Sie Visual Studio in eine leistungsstarke Entwicklungsumgebung für SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse.| **SSDT wird unter Windows ausgeführt**.|
| [Visual Studio Code](https://code.visualstudio.com/)| Installieren Sie nach der Installation von Visual Studio Code, der [Mssql-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) für die Entwicklung von Microsoft SQL Server, Azure SQL-Datenbank und SQL Data Warehouse.| **Visual Studio Code ausgeführt wird, unter Windows, MacOS und Linux**.|


## <a name="command-line-tools-to-manage-databases"></a>Befehlszeilentools zum Verwalten von Datenbanken

Im folgenden sind die wichtigsten Befehlszeilentools:

| Tool | Beschreibung | Ausgeführt wird |
|:--|:--|:--|
|[**mssql-cli (Vorschauversion)**](mssql-cli.md)|**MSSQL-Cli** ist ein interaktives Befehlszeilentools-Tool zum Abfragen von SQL Server. | Windows, MacOS und Linux|
| [**sqlpackage**](sqlpackage.md) |**"Sqlpackage"** ist ein Befehlszeilenprogramm, das mehrere Aufgaben der Datenbankentwicklung automatisiert. MacOS und Linux-Versionen von "Sqlpackage" befinden sich derzeit in der Vorschauphase. | Windows, MacOS und Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** stellt Cmdlets bereit, für die Arbeit mit SQL| Windows, MacOS und Linux|
| [**sqlcmd**](sqlcmd-utility.md) |**Sqlcmd** Dienstprogramm können Sie die Transact-SQL-Anweisungen, Systemprozeduren und Skriptdateien an der Eingabeaufforderung eingeben. | Windows, MacOS und Linux|
|[**bcp**](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-2014)|Mit dem Hilfsprogramm **bcp**(**B**ulk **C**opy **P**rogram) werden Daten per Massenvorgang zwischen einer Instanz von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und einer Datendatei in einem benutzerdefinierten Format kopiert.|Windows, MacOS und Linux|
|[**MSSQL-Skripter (Vorschau)**](https://github.com/Microsoft/mssql-scripter)|**MSSQL-Skripter** ist eine plattformübergreifende Befehlszeile-Umgebung für die Skripterstellung von SQL Server-Datenbanken|Windows, MacOS und Linux|
|[**MSSQL-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**MSSQL-Conf** konfiguriert SQL Server unter Linux ausgeführt wird.|Linux|



## <a name="which-tool-should-i-choose"></a>Welches Tool soll ich auswählen?

- Möchten Sie eine SQL Server-Instanz oder Datenbank, in einem Lightweight-Editor unter Windows, Linux oder Mac zu verwalten? Verwenden Sie in diesem Fall [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md).
- Möchten Sie ein SQL Server-Instanz oder Datenbank auf Windows mit vollständiger GUI-Unterstützung verwalten? Verwenden Sie in diesem Fall [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).
- Sie erstellen oder Verwalten von Datenbankcode, einschließlich Überprüfung kompilieren, refactoring und Designer-Unterstützung auf Windows? Verwenden Sie in diesem Fall [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).
- Möchten Sie die Abfragen von SQL Server über ein Befehlszeilentool, das IntelliSense, Beleuchtung aus High-Syntax, Funktionen und vieles mehr? Wählen Sie [Mssql-Cli](mssql-cli.md)
- Möchten Sie die T-SQL-Skripts in einem Lightweight-Editor unter Windows, Linux oder Mac zu schreiben? Wählen Sie [Visual Studio Code](https://code.visualstudio.com/) und [Mssql-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)



## <a name="additional-tools"></a>Zusätzliche tools

| Tool | Beschreibung |
|:--|:--|
| [Configuration Manager](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Verwenden Sie SQL Server Configuration Manager, SQL Server-Dienste konfigurieren, und konfigurieren die Netzwerkkonnektivität. Configuration Manager ausgeführt wird, auf Windows|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | Verwenden Sie SQL Server Migration Assistant zur Automatisierung der Datenbankmigration von Microsoft Access, DB2, MySQL, Oracle und Sybase zu SQL Server.|
| [Assistent für Datenbankexperimente](../dea/database-experimentation-assistant-overview.md) | Verwenden Sie Datenbank-experimentieren-Assistenten, um eine Zielversion von SQL für eine bestimmte arbeitsauslastung auszuwerten. |
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | Verwenden Sie die Distributed Replay-Funktion können Sie das Bewerten der Auswirkungen zukünftiger Upgrades von SQL Server. Distributed Replay kann auch zum Bewerten der Auswirkungen von Hardware und Betriebssystem-Upgrades und Optimierung von SQL Server-Hilfe verwenden Sie werden. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Die Ssbdiagnose (Hilfsprogramm) meldet Probleme in Service Broker-Konversationen oder die Konfiguration von Service Broker-Dienste. |

Wenn Sie für weitere Tools suchen, die auf dieser Seite nicht erwähnt werden, finden Sie unter [SQL-Eingabeaufforderungs-Hilfsprogrammen](command-prompt-utility-reference-database-engine.md).

