---
title: sys. filetable_system_defined_objects (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd05f24ab90844065b708230ee016ce9ce78bfbd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005152"
---
# <a name="sysfiletable_system_defined_objects-transact-sql"></a>sys.filetable_system_defined_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Zeigt eine Liste mit systemdefinierten Objekten an, die sich auf FileTables beziehen. Enthält eine Zeile für jedes systemdefinierte Objekt.  
  
 Wenn Sie eine FileTable erstellen, werden verknüpfte Objekte, z. B. Einschränkungen und Indizes, zur gleichen Zeit erstellt. Sie können diese Objekte nicht ändern oder löschen; sie verschwinden nur, wenn die FileTable selbst gelöscht wird.  
  
 Weitere Informationen zu FileTables finden Sie unter [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md).  
  
|Column|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|**object_id**|**int**|Objekt-ID des systemdefinierten Objekts für eine FileTable.<br /><br /> Verweist auf das Objekt in **sys.objects**.|  
|**parent_object_id**|**int**|Objekt-ID der übergeordneten FileTable.<br /><br /> Verweist auf das Objekt in **sys.objects**.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen, ändern und Löschen von filetables](../../relational-databases/blob/create-alter-and-drop-filetables.md)   
 [Verwalten von FileTables](../../relational-databases/blob/manage-filetables.md)  
  
  
