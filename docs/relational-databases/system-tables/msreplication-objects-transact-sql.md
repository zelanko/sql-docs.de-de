---
title: MSreplication_objects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 058e1948fa79ed2ba250a4f4d504f95201d1e254
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079082"
---
# <a name="msreplicationobjects-transact-sql"></a>MSreplication_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSreplication_objects** Tabelle enthält eine Zeile für jedes Objekt, das Replikation in der Abonnentendatenbank zugeordnet ist. Diese Tabelle wird in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**publication**|**sysname**|Der Name der Veröffentlichung.|  
|**object_name**|**sysname**|Der Name des Objekts.|  
|**object_type**|**char(2)**|Der Objekttyp:<br /><br /> **u** = Tabelle.<br /><br /> **t** = Trigger.<br /><br /> **p** = gespeicherte Prozedur.|  
|**article**|**sysname**|Der Name des Artikels, dem das Objekt zugeordnet ist|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
