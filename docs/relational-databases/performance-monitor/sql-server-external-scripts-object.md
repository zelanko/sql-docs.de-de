---
title: SQL Server, Externes Skript-Objekt | Microsoft-Dokumentation
description: Hier lernen Sie das „SQLServer:Externes Skript“-Objekt kennen, das Leistungsindikatoren zum Überwachen der Aktionen in Verbindung mit der Ausführung externer Skripts bereitstellt.
ms.custom: ''
ms.date: 03/21/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: fb8ded658e80c3530b916ea81595ac5fa5c99f52
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457418"
---
# <a name="sql-server-external-scripts-object"></a>SQL Server, Externes Skript-Objekt
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Das **SQLServer:Externes Skript** -Objekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Leistungsindikatoren zum Überwachen der Aktionen in Verbindung mit der Ausführung externer Skripts bereit. Informationen zum Ausführen von externen Skripts finden Sie unter [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  
  
 In dieser Tabelle werden die **External Scripts**-Zähler in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beschrieben.  
  
|Leistungsindikatoren für externe SQL Server-Skripts|BESCHREIBUNG|  
|------------------------------------------|-----------------|  
|**Execution Errors**|Die Anzahl von Fehlern beim Ausführen externer Skripts.|  
|**Implied Auth. Anmeldungen**|Die Anzahl von Anmeldungen über Satellitenprozesse, die über die implizite Authentifizierung authentifiziert wurden.|  
|**Parallel Executions**|Die Anzahl externer Skripts, die mit @parallel = 1 ausgeführt wurden.|  
|**SQL CC Executions**|Die Anzahl externer Skripts, die mit SQL Compute Context ausgeführt wurden.|  
|**Streaming Executions**|Die Anzahl externer Skripts, die mit dem @r_rowsPerRead-Parameter ausgeführt wurden.|  
|**Total Execution Time (ms)**|Die Gesamtzeit für das Ausführen externer Skripts.|  
|**Total Executions**|Die Anzahl ausgeführter externer Skripts.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
