---
title: sys. dm_xtp_gc_queue_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_gc_stats
- dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_gc_stats dynamic management view
ms.assetid: addef774-318d-46a7-85df-f93168a800cb
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = azuresqldb-mi-current || >= sql-server-2016 || >= sql-server-linux-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 76acad96bb43b23487490cab79072311906f7e8e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85648112"
---
# <a name="sysdm_xtp_gc_queue_stats-transact-sql"></a>sys.dm_xtp_gc_queue_stats (Transact-SQL)

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Gibt Informationen über jede Garbage Collection-Arbeitsthreadwarteschlange auf dem Server sowie verschiedene Statistiken zu diesen Warteschlangen aus. Pro logische CPU ist eine Warteschlange vorhanden.  
  
 Der Garbage Collection-Hauptthread (Leerlaufthread) verfolgt aktualisierte, gelöschte und eingefügte Zeilen für alle Transaktionen nach, die seit dem letzten Aufruf des Garbage Collection-Hauptthreads abgeschlossen wurden. Sobald er aktiviert wird, überprüft der Garbage Collection-Thread, ob der Zeitstempel der ältesten aktiven Transaktion geändert wurde. Wenn die älteste aktive Transaktion geändert wurde, reiht der Leerlaufthread Arbeitselemente für Transaktionen, deren Schreibmengen nicht mehr benötigt werden, (in Segmenten von 16 Zeilen) in die Warteschlange ein. Wenn Sie z. B. 1.024 Zeilen löschen, enthält die Warteschlange schließlich 64 Garbage Collection-Arbeitselemente mit jeweils 16 gelöschten Zeilen.  Nachdem für eine Benutzertransaktion ein Commit ausgeführt wurde, werden alle im zugehörigen Zeitplanungsmodul in die Warteschlange eingereihten Arbeitsaufgaben ausgewählt. Wenn die Warteschlange im Zeitplanungsmodul keine Arbeitsaufgaben enthält, werden von der Benutzertransaktion alle Warteschlangen im aktuellen NUMA-Knoten durchsucht.  
  
 Sie können feststellen, ob Arbeitsspeicher für gelöschte Zeilen durch die Garbage Collection freigegeben wird, indem Sie sys.dm_xtp_gc_queue_stats ausführen und überprüfen, ob die Arbeitsaufgaben in der Warteschlange verarbeitet werden. Wenn Einträge im current_queue_depth nicht verarbeitet werden oder der current_queue_depth keine neuen Arbeitsaufgaben hinzugefügt werden, ist dies ein Hinweis darauf, dass Garbage Collection keinen Arbeitsspeicher freigibt. Beispielsweise kann Garbage Collection nicht ausgeführt werden, wenn eine Transaktion mit langer Laufzeit ausgeführt wird.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  

|Spaltenname|Typ|BESCHREIBUNG|  
|-----------------|----------|-----------------|  
|queue_id|**int**|Der eindeutige Bezeichner der Warteschlange.|  
|total_enqueues|**bigint**|Die Gesamtanzahl von Arbeitselementen der Garbage Collection, die seit dem Start des Servers in die Warteschlange eingereiht wurden.|  
|total_dequeues|**bigint**|Die Gesamtanzahl von Arbeitselementen der Garbage Collection, die seit dem Start des Servers aus der Warteschlange entfernt wurden.|  
|current_queue_depth|**bigint**|Die aktuelle Anzahl von Arbeitselementen der Garbage Collection, die in dieser Warteschlange vorhanden sind. Dieses Element bedeutet möglicherweise, dass eine oder mehrere Garbage Collections durchgeführt werden sollen.|  
|maximum_queue_depth|**bigint**|Die maximale Tiefe, die diese Warteschlange aufgewiesen hat.|  
|last_service_ticks|**bigint**|CPU-Takte zu dem Zeitpunkt, als die Warteschlange zuletzt aktiv war.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung.  
  
## <a name="user-scenario"></a>Benutzerszenario  
 Diese Ausgabe veranschaulicht, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entweder auf vier Kernen ausgeführt wird oder dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz vier Kernen zugeordnet wurde:  
  
 Diese Ausgabe veranschaulicht, dass in den Warteschlangen keine zu verarbeitenden Arbeitselemente enthalten sind. Für Warteschlange 0 wurden seit dem SQL-Start insgesamt 15.625 Arbeitselemente aus der Warteschlange entfernt, und die maximale Warteschlangentiefe betrug 215.625.  
  
```  
queue_id total_enqueues total_dequeues current_queue_depth  maximum_queue_depth  last_service_ticks  
----------------------------------------------------------------------------------------------------  
0        15625                15625    0                    15625                1233573168347  
1        15625                15625    0                    15625                1234123295566  
2        15625                15625    0                    15625                1233569418146  
3        15625                15625    0                    15625                1233571605761  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten für speicheroptimierte Tabellen (Transact-SQL)](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
