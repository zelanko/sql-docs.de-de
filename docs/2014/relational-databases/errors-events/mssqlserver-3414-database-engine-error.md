---
title: MSSQLSERVER_3414 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3414 (Database Engine error)
ms.assetid: f25852f9-b91c-4356-b817-78bec9ec8db4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 890179c3f5a6bc7d3d627ce9cf2c51fc5d2e96ba
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868275"
---
# <a name="mssqlserver_3414"></a>MSSQLSERVER_3414
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3414|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|REC_GIVEUP|  
|Meldungstext|Fehler bei der Wiederherstellung. Die '%.*ls'-Datenbank (Datenbank-ID %d) kann daher nicht neu gestartet werden. Diagnostizieren und beheben Sie die Wiederherstellungsfehler, oder führen Sie eine Wiederherstellung von einer als fehlerfrei bekannten Sicherung aus. Falls die Fehler nicht behoben werden oder unerwartete Fehler auftreten, wenden Sie sich an den technischen Support.|  
  
## <a name="explanation"></a>Erklärung  
 Die angegebene Datenbank wurde wiederhergestellt, konnte jedoch nicht gestartet werden, da Fehler bei der Wiederherstellung auftraten. Durch diesen Fehler wurde die Datenbank in den SUSPECT-Status geschaltet. Die primäre Dateigruppe und möglicherweise weitere Dateigruppen sind fehlerverdächtig und u. U. beschädigt. Die Datenbank kann während Starts von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht wiederhergestellt werden und ist daher nicht verfügbar. Eine Aktion seitens des Benutzers ist erforderlich, um das Problem zu beheben.  
  
 Falls dieser Fehler für **tempdb**auftritt, wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz heruntergefahren.  
  
## <a name="user-action"></a>Benutzeraktion  
 Dieser Fehler kann auf vorübergehende Systemschwierigkeiten zurückzuführen sein, die beim Versuch, die Serverinstanz zu starten oder eine Datenbank wiederherzustellen, aufgetreten sind. Es kann jedoch auch ein dauerhafter Fehler vorliegen, der bei jedem Versuch auftritt, die Datenbank zu starten. Um Informationen zur Ursache zu erhalten, überprüfen Sie das Windows-Ereignisprotokoll auf einen vorangehenden Fehler, der Aufschluss über den aktuellen Fehler geben könnte.  
  
 Um Informationen zur Ursache dieses Auftretens von Fehler 3414 zu erhalten, überprüfen Sie das Windows-Ereignisprotokoll auf einen vorangehenden Fehler, der Aufschluss über den aktuellen Fehler geben könnte. Die entsprechende Benutzeraktion hängt davon ab, ob die Informationen im Windows-Ereignisprotokoll angeben, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehler durch eine vorübergehende Bedingung oder einen dauerhaften Fehler verursacht wurde. Informationen zu den Benutzeraktionen zum Beheben von Fehler 3414 finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [DBCC CHECKDB &#40;Transact-SQL-&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [Umfassende Daten Bank Wiederherstellungen &#40;einfaches Wiederherstellungs Modell&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md)   
 [MSSQLSERVER_824](mssqlserver-824-database-engine-error.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
