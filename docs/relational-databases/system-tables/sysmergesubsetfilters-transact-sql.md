---
title: Sysmergesubsetfilters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergesubsetfilters
- sysmergesubsetfilters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubsetfilters system table
ms.assetid: f91d1c6c-3132-47f6-926c-88f56848cafe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6c5eee7cef00d05e2a296fccd527c3df7a119d6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802692"
---
# <a name="sysmergesubsetfilters-transact-sql"></a>sysmergesubsetfilters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen zu Joinfiltern für partitionierte Artikel. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Filtername**|**sysname**|Der Name des Filters, der zum Erstellen des Artikels verwendet wurde.|  
|**join_filterid**|**int**|Die ID des Objekts, das den Joinfilter darstellt.|  
|**pubid**|**uniqueidentifier**|Die ID der Veröffentlichung.|  
|**artid**|**uniqueidentifier**|Die ID des Artikels.|  
|**art_nickname**|**int**|Der Spitzname des Artikels.|  
|**join_articlename**|**sysname**|Der Name der zu verknüpfenden Tabelle, um zu bestimmen, ob die Zeile dazugehört.|  
|**join_nickname**|**int**|Der Spitzname der zu verknüpfenden Tabelle, um zu bestimmen, ob die Zeile dazugehört.|  
|**join_unique_key**|**int**|Zeigt einen Join mit einem eindeutigen Schlüssel von **Join_tablename**:<br /><br /> 0 = Nicht eindeutiger Schlüssel.<br /><br /> 1 = Eindeutiger Schlüssel.|  
|**expand_proc**|**sysname**|Der Name der gespeicherten Prozedur, mit der der Merge-Agent die Zeilen identifiziert, die von einem Abonnenten gesendet oder entfernt werden müssen.|  
|**join_filterclause**|**nvarchar(1000)**|Die für den Join verwendete Filterklausel.|  
|**filter_type**|**tinyint**|Gibt den Filtertyp an. Folgende Werte sind möglich:<br /><br /> 1 = Joinfilter.<br /><br /> 2 = Logischer Datensatzlink.<br /><br /> 3 = Sowohl Joinfilter als auch logischer Datensatzlink.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
