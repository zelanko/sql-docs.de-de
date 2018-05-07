---
title: Sys. filetable_system_defined_objects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.filetable_system_defined_objects_TSQL
- filetable_system_defined_objects
- filetable_system_defined_objects_TSQL
- sys.filetable_system_defined_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetable_system_defined_objects catalog view
ms.assetid: 62022e6b-46f6-495f-b14b-53f41e040361
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a9d4cdb95349c9af9416caca7ca8dcf8893c0b4d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="sysfiletablesystemdefinedobjects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt eine Liste mit systemdefinierten Objekten an, die sich auf FileTables beziehen. Enthält eine Zeile für jedes systemdefinierte Objekt.  
  
 Wenn Sie eine FileTable erstellen, werden verknüpfte Objekte, z. B. Einschränkungen und Indizes, zur gleichen Zeit erstellt. Sie können diese Objekte nicht ändern oder löschen; sie verschwinden nur, wenn die FileTable selbst gelöscht wird.  
  
 Weitere Informationen zu FileTables finden Sie unter [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
|Column|Datentyp|Description|  
|------------|---------------|-----------------|  
|**object_id**|**int**|Objekt-ID des systemdefinierten Objekts für eine FileTable.<br /><br /> Verweist auf das Objekt in **sys.objects**.|  
|**"parent_object_id"**|**int**|Objekt-ID der übergeordneten FileTable.<br /><br /> Verweist auf das Objekt in **sys.objects**.|  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen, Ändern und Löschen von FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md)  
  
  
