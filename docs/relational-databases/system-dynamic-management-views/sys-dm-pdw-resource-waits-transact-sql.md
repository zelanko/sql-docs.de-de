---
title: Sys.dm_pdw_resource_waits (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a43ce9a2-5261-41e3-97f0-555ba05ebed9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 704fcdc72f571485f10b76860a632c61233ed296
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000852"
---
# <a name="sysdmpdwresourcewaits-transact-sql"></a>Sys.dm_pdw_resource_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Warten Sie, zeigt Informationen für alle Ressourcentypen im [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Die Position der Anforderung in der Liste der wartenden.|0-basierte Ordnungszahl. Dies ist in allen Einträgen der Wartevorgang nicht eindeutig.|  
|session_id|**nvarchar(32)**|ID der Sitzung, in der der Wartezustand aufgetreten ist.|Finden Sie unter Sitzungs-ID in [dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Typ|**nvarchar(255)**|Der Typ des Wartevorgangs, den dieser Eintrag darstellt.|Mögliche Werte:<br /><br /> Verbindung<br /><br /> Parallelität für lokale Abfragen<br /><br /> Parallelität von verteilten Abfragen<br /><br /> DMS-Parallelität<br /><br /> Sicherung der Parallelität|  
|object_type|**nvarchar(255)**|Der Typ des Objekts, das den Wartevorgang betroffen ist.|Mögliche Werte:<br /><br /> **OBJEKT**<br /><br /> **DATABASE**<br /><br /> **SYSTEM**<br /><br /> **SCHEMA**<br /><br /> **ANWENDUNG**|  
|object_name|**nvarchar(386)**|Name oder die GUID des angegebenen Objekts, das von den Wartevorgang betroffen war.|Tabellen und Ansichten werden mit den dreiteiligen Namen angezeigt.<br /><br /> Indizes und Statistiken werden mit vierteiligen Namen angezeigt.<br /><br /> Namen, Prinzipale und Datenbanken sind die Zeichenfolgennamen.|  
|request_id|**nvarchar(32)**|Die ID der Anforderung auf der der Wartezustand aufgetreten ist.|QID Bezeichner der Anforderung.<br /><br /> GUID-Bezeichner für die Anforderungen zum Laden.|  
|request_time|**datetime**|Der Zeitpunkt, an dem die Sperre oder eine Ressource angefordert wurde.||  
|acquire_time|**datetime**|Der Zeitpunkt, an dem die Sperre oder die Ressource abgerufen wurde.||  
|state|**nvarchar(50)**|Status des den Wartezustand.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Die Priorität des Elements warten.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|concurrency_slots_used|**int**|Anzahl von parallelitätsslots (maximal 32) für diese Anforderung reserviert.|1 – für "smallrc"<br /><br /> 3 – für "mediumrc"<br /><br /> 7 für "largerc"<br /><br /> 22 – für "xlargerc"|  
|resource_class|**nvarchar(20)**|Die Ressourcenklasse für diese Anforderung.|"Smallrc"<br /><br /> "Mediumrc"<br /><br /> "Largerc"<br /><br /> "Xlargerc"|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
