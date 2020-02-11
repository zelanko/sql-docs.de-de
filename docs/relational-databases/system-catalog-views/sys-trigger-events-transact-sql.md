---
title: sys. trigger_events (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trigger_events_TSQL
- trigger_events
- sys.trigger_events
- sys.trigger_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trigger_events catalog view
ms.assetid: 92540447-131c-491c-b033-c064c7d950e1
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cc2732797551317a392b0ab55d9ecbeb28d990a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091945"
---
# <a name="systrigger_events-transact-sql"></a>sys.trigger_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Ereignis, für das ein Trigger ausgelöst wird.  
  
> [!NOTE]  
>  **sys. trigger_events** gilt nicht für Ereignis Benachrichtigungen.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<Von sys. Events geerbte Spalten>**|Nicht verfügbar|Erbt die Spalten **object_id**, **type**, **type_desc** von [sys.events](../../relational-databases/system-catalog-views/sys-events-transact-sql.md).|  
|**is_first**|**bit**|Der Trigger ist als derjenige gekennzeichnet, der für dieses Ereignis als erster ausgelöst wird.|  
|**is_last**|**bit**|Der Trigger ist als derjenige gekennzeichnet, der für dieses Ereignis als letzter ausgelöst wird.|  
|**event_group_type**|**int**|Ereignisgruppe, für die der Trigger erstellt wurde, bzw. NULL, wenn sie nicht für eine Ereignisgruppe erstellt wurden.|  
|**event_group_type_desc**|**nvarchar (60)**|Beschreibung der Ereignisgruppe, für die der Trigger erstellt wurde, bzw. NULL, wenn sie nicht für eine Ereignisgruppe erstellt wurden.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
