---
title: sys. dm_pdw_wait_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 2d5815783528b89716cc8bfb426ea7c1b274802e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088718"
---
# <a name="sysdm_pdw_wait_stats-transact-sql"></a>sys. dm_pdw_wait_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Enthält Informationen im Zusammenhang [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem Betriebssystem Status im Zusammenhang mit Instanzen, die auf verschiedenen Knoten ausgeführt werden. Eine Liste der Warte Typen und deren Beschreibung finden Sie unter [sys. dm_os_wait_stats](https://msdn.microsoft.com/library/ms179984\(v=sql.120\).aspx).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|ID des Knotens, auf den sich dieser Eintrag bezieht.||  
|**wait_name**|**nvarchar(255)**|Der Name des Wartetyps.||  
|**max_wait_time**|**bigint**|Maximale Wartezeit für diesen Wartetyp.||  
|**request_count**|**bigint**|Anzahl der Warte Vorgänge für diesen Wartetyp, der aussteht.||  
|**signal_time**|**bigint**|Differenz zwischen dem Zeitpunkt der Signalisierung des wartenden Threads und dem Beginn der Ausführung.||  
|**completed_count**|**bigint**|Die Gesamtanzahl der seit dem letzten Neustart des Servers abgeschlossenen warte Vorgänge dieses Typs.||  
|**wait_time**|**bigint**|Gesamt Wartezeit für diesen Wartetyp in Millisekunden. Einschließlich signal_time.||  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys. dm_pdw_waits &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
