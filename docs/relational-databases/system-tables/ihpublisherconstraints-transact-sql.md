---
title: Ihpublishereinschränkungs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublisherconstraints
- IHpublisherconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublisherconstraints system table
ms.assetid: 537b1e1a-7228-4680-aa27-5ad7072ea01e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 44987e1b610483e6ce3cbca26c1efb8a1ef4c241
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990259"
---
# <a name="ihpublisherconstraints-transact-sql"></a>IHpublisherconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **ihpublishereinschränkungs** -Systemtabelle enthält eine Zeile für jede Einschränkung, die von nicht-SQL Server-Verlegern mithilfe des aktuellen Verteilers repliziert wurde. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisherconstraint_id**|**int**|Identifiziert eine veröffentlichte Einschränkung.|  
|**table_id**|**int**|Identifiziert die Tabelle aus [IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md) , zu der die Einschränkung gehört.|  
|**publisher_id**|**smallint**|Identifiziert den Nicht-SQL Server-Verleger, von dem die Spalte veröffentlicht wird.|  
|**Name**|**Vom Datentyp sysname**|Der Name der veröffentlichten Einschränkung.|  
|**Typ**|**nvarchar(255)**|Ein unterstützter Einschränkungstyp aus der [iheinschräninttypes](../../relational-databases/system-tables/ihconstrainttypes-transact-sql.md) -Systemtabelle.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Replikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
