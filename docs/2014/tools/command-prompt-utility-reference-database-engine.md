---
title: Referenz zum Befehlszeilen-Hilfsprogramm (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server]
- command prompt utilities [SQL Server], about command prompt utilities
- command prompt [SQL Server]
- utilities [SQL Server], command prompt
- command prompt [SQL Server], utilities
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd1ea5dbf44a5db030abc666dc11e567f2f7fa3b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008591"
---
# <a name="command-prompt-utility-reference-database-engine"></a>Referenz zum Eingabeaufforderungs-Hilfsprogramm (Datenbank-Engine)
  Eingabeaufforderungs-Hilfsprogramme versetzen Sie in die Lage, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Vorgänge einem Skript hinzuzufügen. Die folgende Tabelle enthält eine Liste der Eingabeaufforderung-Hilfsprogramme, die im Lieferumfang von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]enthalten sind.  
  
|**Hilfsprogramm**|**Beschreibung**|**Installiert in**|  
|-----------------|---------------------|----------------------|  
|[bcp (Hilfsprogramm)](bcp-utility.md)|Wird verwendet, um Daten in einem benutzerdefinierten Format von einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz in eine Datendatei zu kopieren|\<*drive*:>\Programme \\ [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] \Client sdk\odbc\110\tools\binn|  
|[dta (Hilfsprogramm)](dta/dta-utility.md)|Wird verwendet, um eine Arbeitsauslastung zu analysieren und Empfehlungen zu physischen Entwurfsstrukturen auszugeben, um die Serverleistung für diese Arbeitsauslastung zu optimieren.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[dtexec (Hilfsprogramm)](../integration-services/packages/dtexec-utility.md)|Wird verwendet, um ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket zu konfigurieren und auszuführen. Unter dem Namen **DTExecUI**steht eine Version dieses Hilfsprogramms mit Benutzeroberfläche zur Verfügung, über die das Paketausführungsprogramm aufgerufen wird.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[dtutil (Hilfsprogramm)](../integration-services/dtutil-utility.md)|Wird für die Verwaltung von SSIS-Paketen verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Bereitstellen von Modelllösungen mit dem Bereitstellungsprogramm](https://docs.microsoft.com/analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility)|Wird verwendet, um [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekte für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanzen bereitzustellen.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[osql (Hilfsprogramm)](osql-utility.md)|Ermöglicht es Ihnen, [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, Systemprozeduren und Skriptdateien an der Eingabeaufforderung einzugeben.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Profiler-Hilfsprogramm](profiler-utility.md)|Wird verwendet, um [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] von der Eingabeaufforderung zu starten.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Hilfsprogramm RS.exe (SSRS)](../reporting-services/tools/rs-exe-utility-ssrs.md)|Wird verwendet, um Skripts für die Verwaltung von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichtsservern auszuführen.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rsconfig-Hilfsprogramm (SSRS)](../reporting-services/tools/rsconfig-utility-ssrs.md)|Wird zum Konfigurieren einer Berichtsserververbindung verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rskeymgmt-Hilfsprogramm &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Wird für die Verwaltung von Verschlüsselungsschlüsseln auf einem Berichtsserver verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlagent90 (Anwendung)](sqlagent90-application.md)|Wird verwendet, um den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent von der Eingabeaufforderung zu starten.|\<drive>: \Programme\Microsoft SQL Server \\ < *instance_name*> \MSSQL\Binn|  
|[SQLCMD-Hilfsprogramm](sqlcmd-utility.md)|Ermöglicht es Ihnen, [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, Systemprozeduren und Skriptdateien an der Eingabeaufforderung einzugeben.|\<*drive*:>\Programme \\ [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] \Client sdk\odbc\110\tools\binn|  
|[SQLdiag (Hilfsprogramm)](sqldiag-utility.md)|Wird zum Sammeln von Diagnoseinformationen für den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Kundenservice und -support verwendet.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Anwendung sqllogship](sqllogship-application.md)|Wird von Anwendungen zum Ausführen von Sicherungs-, Kopier- und Wiederherstellungsvorgängen und zugeordneten Cleanups für eine Protokollversandkonfiguration verwendet, ohne Sicherungs-, Kopier- und Wiederherstellungsaufträge auszuführen.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[SqlLocalDB-Hilfsprogramm](sqllocaldb-utility.md)|Ein Ausführungsmodus von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , der speziell für Programmentwickler konzipiert wurde.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlmaint (Hilfsprogramm)](sqlmaint-utility.md)|Wird verwendet, um Datenbank-Wartungspläne auszuführen, die in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]erstellt wurden.|\<drive>: \Programme\Microsoft SQL server\mssql12. MSSQLSERVER\MSSQL\binn|  
|[sqlps (Hilfsprogramm)](sqlps-utility.md)|Wird zum Ausführen von PowerShell-Befehlen und -Skripts verwendet. Lädt und registriert den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Anbieter sowie cmdlets.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr](sqlservr-application.md)|Wird verwendet, um eine Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)] zur Problembehandlung von der Eingabeaufforderung aus zu starten und zu beenden.|\<drive>: \Programme\Microsoft SQL server\mssql12. MSSQLSERVER\MSSQL\binn|  
|[Ssms-Hilfsprogramm](../ssms/ssms-utility.md)|Wird verwendet, um [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] von der Eingabeaufforderung zu starten.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[tablediff (Hilfsprogramm)](tablediff-utility.md)|Wird verwendet, um Daten in zwei Tabellen im Hinblick auf Nichtkonvergenz zu vergleichen, was im Rahmen der Problembehandlung in einer Replikationstopologie hilfreich sein kann.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  
  
 **So greifen Sie unter [!INCLUDE[win8](../includes/win8-md.md)]** auf den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager zu  
  
 Da der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für die [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager bei Verwendung von [!INCLUDE[win8](../includes/win8-md.md)]nicht als Anwendung angezeigt. Um [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager im Charm **Suchen** unter **apps**zu öffnen, geben Sie **SQLServerManager12. msc** (für [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] ) oder **SQLServerManager11. msc** für () ein [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , und drücken Sie dann die **Eingabe**Taste.  
  
## <a name="command-prompt-utilities-syntax-conventions"></a>Syntaxkonventionen für die Befehlszeilen-Hilfsprogramme  
  
|**Konvention**|**Verwendung**|  
|--------------------|------------------|  
|GROSSBUCHSTABEN|Anweisungen und Ausdrücke, die auf Betriebssystemebene verwendet werden.|  
|`monospace`|Beispielbefehle und Programmcode.|  
|*Kursiv*|Vom Benutzer angegebene Parameter.|  
|**Fett**|Befehle, Parameter und sonstige Syntaxelemente, die genau wie angezeigt eingegeben werden müssen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Verteilungs-Agent](../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Replikations Protokolllese-Agent](../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Replikations Merge-Agent](../relational-databases/replication/agents/replication-merge-agent.md)   
 [Replikations Warteschlangenlese-Agent](../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
