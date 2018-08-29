---
title: Sys. numbered_procedures (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.numbered_procedures_TSQL
- numbered_procedures
- sys.numbered_procedures
- numbered_procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.numbered_procedures catalog view
ms.assetid: 5b6d6498-bac6-4266-94b9-d16ef5089cf0
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3101b0049fbe52527271ba308244effd95e88d9
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43079161"
---
# <a name="sysnumberedprocedures-transact-sql"></a>sys.numbered_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jede gespeicherte Prozedur von SQL Server, die als nummerierte Prozedur erstellt wurde. Für die gespeicherte Basisprozedur (Nummer = 1) wird keine Zeile angezeigt. Einträge für die gespeicherten Basisprozeduren finden Sie in Sichten, wie z. B. **sys.objects** und **sys.procedures**.  
  
> [!IMPORTANT]  
>  Nummerierte Prozeduren sind als veraltet markiert. Von der Verwendung nummerierter Prozeduren wird abgeraten. Ein DEPRECATION_ANNOUNCEMENT-Ereignis wird ausgelöst, wenn eine Abfrage kompiliert wird, die diese Katalogsicht verwendet.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID des Objekts der gespeicherten Prozedur.|  
|**procedure_number**|**smallint**|Die Nummer dieser Prozedur innerhalb des Objekts, d. h. 2 oder größer.|  
|**definition**|**nvarchar(max)**|Der SQL Server-Text, mit dem diese Prozedur definiert wird.<br /><br /> NULL = verschlüsselt.|  
  
> [!NOTE]  
>  XML- und CLR-Parameter werden für nummerierte Prozeduren nicht unterstützt.  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
