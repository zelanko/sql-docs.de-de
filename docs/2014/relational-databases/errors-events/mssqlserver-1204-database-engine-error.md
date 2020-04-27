---
title: MSSQLSERVER_1204 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee0544c14bbf3e05fcb59e16a9bb3e0d8e61e33b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62916101"
---
# <a name="mssqlserver_1204"></a>MSSQLSERVER_1204
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1204|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LK_OUTOF|  
|Meldungstext|Die Instanz der SQL Server-Datenbank-Engine kann derzeit keine LOCK-Ressource erhalten. Führen Sie die Anweisung erneut aus, wenn die Zahl der aktiven Benutzer kleiner ist. Bitten Sie den Datenbankadministrator, die Konfiguration der Sperren und des Arbeitsspeichers für diese Instanz zu überprüfen oder nach lange andauernden Transaktionen zu suchen.|  
  
## <a name="explanation"></a>Erklärung  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann keine Sperrenressource erhalten. Dies kann eine der beiden folgenden Ursachen haben:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann keinen zusätzlichen Arbeitsspeicher vom Betriebssystem zuordnen, weil der Arbeitsspeicher von anderen Prozessen verwendet wird oder weil der Server mit der konfigurierten Option **Max. Serverarbeitsspeicher** ausgeführt wird.  
  
-   Der Sperren-Manager verwendet nicht mehr als 60 Prozent des für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbaren Arbeitsspeichers.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenn Sie vermuten, dass SQL Server nicht genügend Arbeitsspeicher zuordnen kann, können Sie folgende Maßnahmen durchführen:  
  
-   Wenn andere Anwendungen als SQL Server Ressourcen verbrauchen, versuchen Sie, diese Anwendungen zu beenden, oder führen Sie sie auf einem separaten Server aus. Dadurch wird Arbeitsspeicher von anderen Prozessen für SQL Server freigegeben.  
  
-   Wenn Sie die Option Max. Serverarbeitsspeicher konfiguriert haben, erhöhen Sie die Einstellung für diese Option.  
  
 Wenn Sie vermuten, dass der Sperren-Manager die maximale Menge an verfügbarem Arbeitsspeicher verwendet hat, identifizieren Sie die Transaktion, die die meisten Sperren aufrechterhält, und beenden Sie sie. Das folgende Skript identifiziert die Transaktion mit den meisten Sperren:  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
 Nehmen Sie die höchste Sitzungs-ID, und beenden Sie sie mithilfe des KILL-Befehls.  
  
  
