---
title: IHpublisherindexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherindexes
- IHpublisherindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherindexes system table
ms.assetid: 6008ef89-eeb9-46dc-93a2-f7623298cf0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 114ffee3ca13d7b5a42c3843957df0a2450b787f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67990245"
---
# <a name="ihpublisherindexes-transact-sql"></a>IHpublisherindexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **IHpublisherindexes** -Systemtabelle enthält eine Zeile für jeden Index, der von nicht - SQL Server-Verlegern mithilfe des aktuellen Verteilers repliziert. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisherindex_id**|**int**|Identifiziert einen veröffentlichten Index.|  
|**table_id**|**int**|Identifiziert die Tabelle aus [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) zu dem der Index gehört.|  
|**publisher_id**|**smallint**|Identifiziert den nicht - SQL Server-Verleger aus der der Index veröffentlicht wird.|  
|**name**|**sysname**|Der Name des veröffentlichten Indexes.|  
|**type**|**nvarchar(255)**|Ein unterstützter Indextyp aus der [IHindextypes](../../relational-databases/system-tables/ihindextypes-transact-sql.md) -Systemtabelle.|  
  
## <a name="see-also"></a>Siehe auch  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
