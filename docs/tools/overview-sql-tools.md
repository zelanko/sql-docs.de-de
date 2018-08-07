---
title: SQL-Tools und Hilfsprogramme für SQLServer, Azure SQL-Datenbank und Azure SQL Datawarehouse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/22/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: misc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a8f31d6479a0a2ba5e5f19f6a0739ab6322de92b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39458984"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>SQL-Tools und Hilfsprogramme für SQLServer, Azure SQL-Datenbank und Azure SQL Datawarehouse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Zum Verwalten ("Abfrage", "überwachen", "usw.") Ihrer Datenbank, die Sie benötigen ein Tool. Mehrere Datenbanktools stehen zur Verfügung. Während Ihre Datenbanken ausgeführt werden können, in der Cloud, die auf Windows oder auf [Linux](../linux/sql-server-linux-overview.md), Ihr Tool muss nicht auf derselben Plattform wie die Datenbank ausgeführt. 

Dieser Artikel enthält Informationen zu den verfügbaren Tools für die Arbeit mit Ihrer SQL-Datenbanken. 


## <a name="tools-to-run-queries-and-manage-databases"></a>Tools zum Ausführen von Abfragen und Verwalten von Datenbanken  

| Tool | und Beschreibung |
|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] ist eine kostenlose, leicht-Tool zum Verwalten von Datenbanken aus, wo sie ausgeführt werden. Diese Preview-Version stellt die Datenbank-Management-Funktionen, einschließlich einer erweiterten Transact-SQL-Editor und anpassbare Einblicke in den Betriebszustand der Datenbanken bereit. **[!INCLUDE[name-sos](../includes/name-sos-short.md)] unter Windows, MacOS und Linux ausgeführt wird**.|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Verwenden Sie SQL Server Management Studio (SSMS), um Abfragen, Entwerfen und Verwalten Ihrer SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse. **SSMS ausgeführt wird, auf Windows**.|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Verwandeln Sie Visual Studio in eine leistungsstarke Entwicklungsumgebung für SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse. **SSDT ausgeführt wird, auf Windows**.|
|[MSSQL-cli](mssql-cli.md)|MSSQL-Cli ist eine interaktive Befehlszeilen-Tool für die Abfragen von SQL Server. **MSSQL-Cli wird auf Windows, MacOS und Linux ausgeführt.**|
| [Visual Studio Code](https://code.visualstudio.com/)| Installieren Sie nach der Installation von Visual Studio Code, der [Mssql-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) für die Entwicklung von Microsoft SQL Server, Azure SQL-Datenbank und SQL Data Warehouse. **Visual Studio Code ausgeführt wird, unter Windows, MacOS und Linux**.|

## <a name="which-tool-should-i-choose"></a>Welches Tool soll ich auswählen?

- Möchten Sie eine SQL Server-Instanz oder Datenbank, in einem Lightweight-Editor unter Windows, Linux oder Mac zu verwalten? Verwenden Sie in diesem Fall [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md).
- Möchten Sie ein SQL Server-Instanz oder Datenbank auf Windows mit vollständiger GUI-Unterstützung verwalten? Verwenden Sie in diesem Fall [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md).
- Sie erstellen oder Verwalten von Datenbankcode, einschließlich Überprüfung kompilieren, refactoring und Designer-Unterstützung auf Windows? Verwenden Sie in diesem Fall [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md).
- Möchten Sie die Abfragen von SQL Server über ein Befehlszeilentool, das IntelliSense, Beleuchtung aus High-Syntax, Funktionen und vieles mehr? Wählen Sie [Mssql-Cli](mssql-cli.md)
- Möchten Sie die T-SQL-Skripts in einem Lightweight-Editor unter Windows, Linux oder Mac zu schreiben? Wählen Sie [Visual Studio Code](https://code.visualstudio.com/) und [Mssql-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="additional-tools"></a>Zusätzliche tools

| Tool | und Beschreibung |
|:--|:--|
| [Configuration Manager](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Verwenden Sie SQL Server Configuration Manager, SQL Server-Dienste konfigurieren, und konfigurieren die Netzwerkkonnektivität. Configuration Manager ausgeführt wird, auf Windows|
|[MSSQL-conf](../linux/sql-server-linux-configure-mssql-conf.md)|Verwenden Sie Mssql-Conf so konfigurieren Sie SQL Server unter Linux ausgeführt wird.|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | Verwenden Sie SQL Server Migration Assistant zur Automatisierung der Datenbankmigration von Microsoft Access, DB2, MySQL, Oracle und Sybase zu SQL Server.|
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | Verwenden Sie die Distributed Replay-Funktion können Sie das Bewerten der Auswirkungen zukünftiger Upgrades von SQL Server. Distributed Replay kann auch zum Bewerten der Auswirkungen von Hardware und Betriebssystem-Upgrades und Optimierung von SQL Server-Hilfe verwenden Sie werden. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Die Ssbdiagnose (Hilfsprogramm) meldet Probleme in Service Broker-Konversationen oder die Konfiguration von Service Broker-Dienste. |


## <a name="command-line-utilities"></a>Befehlszeilenhilfsprogramme

  Mit Befehlszeilen-Hilfsprogrammen können Sie für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Vorgänge ein Skript erstellen. Die folgende Tabelle enthält eine Liste der Eingabeaufforderung-Hilfsprogramme, die im Lieferumfang von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]enthalten sind.  
  
|**Hilfsprogramm**|**Beschreibung**|**Installiert in**|  
|-----------------|---------------------|----------------------|  
|[bcp (Hilfsprogramm)](../tools/bcp-utility.md)|Wird verwendet, um Daten in einem benutzerdefinierten Format zwischen einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz und einer Datendatei zu kopieren.|\<*Laufwerk*:>\Programme\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta (Hilfsprogramm)](../tools/dta/dta-utility.md)|Wird verwendet, um eine Arbeitsauslastung zu analysieren und Empfehlungen zu physischen Entwurfsstrukturen auszugeben, um die Serverleistung für diese Arbeitsauslastung zu optimieren.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[dtexec (Hilfsprogramm)](../integration-services/packages/dtexec-utility.md)|Wird verwendet, um ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket zu konfigurieren und auszuführen. Unter dem Namen **DTExecUI**steht eine Version dieses Hilfsprogramms mit Benutzeroberfläche zur Verfügung, über die das Paketausführungsprogramm aufgerufen wird.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[dtutil (Hilfsprogramm)](../integration-services/dtutil-utility.md)|Wird für die Verwaltung von SSIS-Paketen verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Bereitstellen von Modelllösungen mit dem Bereitstellungshilfsprogramm](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Wird verwendet, um [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekte für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanzen bereitzustellen.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[MSSQL-Skripter (öffentliche Vorschau)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|Zum Generieren von erstellen und Einfügen von T-SQL-Skripts für Datenbankobjekte in SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse verwendet.|Finden Sie in unserem [GitHub-Repository](https://github.com/Microsoft/sql-xplat-cli) Download und Verwendung von Informationen.| 
|[osql (Hilfsprogramm)](../tools/osql-utility.md)|Ermöglicht es Ihnen, [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, Systemprozeduren und Skriptdateien an der Eingabeaufforderung einzugeben.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Profiler-Hilfsprogramm](../tools/profiler-utility.md)|Wird verwendet, um [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] von der Eingabeaufforderung zu starten.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Hilfsprogramm RS.exe &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|Wird verwendet, um Skripts für die Verwaltung von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsservern auszuführen.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rsconfig-Hilfsprogramm &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|Wird zum Konfigurieren einer Berichtsserververbindung verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rskeymgmt-Hilfsprogramm &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Wird für die Verwaltung von Verschlüsselungsschlüsseln auf einem Berichtsserver verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlagent90 (Anwendung)](../tools/sqlagent90-application.md)|Wird verwendet, um den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent von der Eingabeaufforderung zu starten.|\<Laufwerk>:\Programme\Microsoft SQL Server\\<*Instanzname*>\MSSQL\Binn|  
|[sqlcmd Utility](../tools/sqlcmd-utility.md)|Ermöglicht es Ihnen, [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, Systemprozeduren und Skriptdateien an der Eingabeaufforderung einzugeben.|\<*Laufwerk*:>\Programme\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[SQLdiag (Hilfsprogramm)](../tools/sqldiag-utility.md)|Wird zum Sammeln von Diagnoseinformationen für den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Kundenservice und -support verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Anwendung sqllogship](../tools/sqllogship-application.md)|Wird von Anwendungen zum Ausführen von Sicherungs-, Kopier- und Wiederherstellungsvorgängen und zugeordneten Cleanups für eine Protokollversandkonfiguration verwendet, ohne Sicherungs-, Kopier- und Wiederherstellungsaufträge auszuführen.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[SqlLocalDB-Hilfsprogramm](../tools/sqllocaldb-utility.md)|Ein Ausführungsmodus von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , der speziell für Programmentwickler konzipiert wurde.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlmaint (Hilfsprogramm)](../tools/sqlmaint-utility.md)|Wird verwendet, um Datenbank-Wartungspläne auszuführen, die in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]erstellt wurden.|\<Laufwerk:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[sqlps (Hilfsprogramm)](../tools/sqlps-utility.md)|Wird zum Ausführen von PowerShell-Befehlen und -Skripts verwendet. Lädt und registriert den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Anbieter sowie cmdlets.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr](../tools/sqlservr-application.md)|Wird verwendet, um eine Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)] zur Problembehandlung von der Eingabeaufforderung aus zu starten und zu beenden.|\<Laufwerk:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn|  
|[Ssms-Hilfsprogramm](../tools/sql-server-management-studio/ssms-utility.md)|Wird verwendet, um [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] von der Eingabeaufforderung zu starten.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[tablediff (Hilfsprogramm)](../tools/tablediff-utility.md)|Wird verwendet, um Daten in zwei Tabellen im Hinblick auf Nichtkonvergenz zu vergleichen, was im Rahmen der Problembehandlung in einer Replikationstopologie hilfreich sein kann.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>Syntaxkonventionen für die SQL-Eingabeaufforderungs-Hilfsprogramme  
  
|**Konvention**|**Syntaxelemente**|  
|--------------------|------------------|  
|GROSSBUCHSTABEN|Anweisungen und Ausdrücke, die auf Betriebssystemebene verwendet werden.|  
|`monospace`|Beispielbefehle und Programmcode.|  
|*Kursiv*|Vom Benutzer angegebene Parameter.|  
|**Fett**|Befehle, Parameter und sonstige Syntaxelemente, die genau wie angezeigt eingegeben werden müssen.|  



