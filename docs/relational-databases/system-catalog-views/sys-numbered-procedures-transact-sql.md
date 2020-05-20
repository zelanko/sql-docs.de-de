---
title: sys. numbered_procedures (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ec4ee023960c573ac48ff66886181c2f88b374bb
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825055"
---
# <a name="sysnumbered_procedures-transact-sql"></a>sys.numbered_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Enthält eine Zeile für jede gespeicherte Prozedur von SQL Server, die als nummerierte Prozedur erstellt wurde. Für die gespeicherte Basisprozedur (Nummer = 1) wird keine Zeile angezeigt. Einträge für die gespeicherten Basisprozeduren finden Sie in Sichten, wie z. B. **sys.objects** und **sys.procedures**.  
  
> [!IMPORTANT]  
>  Nummerierte Prozeduren sind als veraltet markiert. Von der Verwendung nummerierter Prozeduren wird abgeraten. Ein DEPRECATION_ANNOUNCEMENT-Ereignis wird ausgelöst, wenn eine Abfrage kompiliert wird, die diese Katalogsicht verwendet.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die ID des Objekts der gespeicherten Prozedur.|  
|**procedure_number**|**smallint**|Die Nummer dieser Prozedur innerhalb des Objekts, d. h. 2 oder größer.|  
|**Definition**|**nvarchar(max)**|Der SQL Server-Text, mit dem diese Prozedur definiert wird.<br /><br /> NULL = verschlüsselt.|  
  
> [!NOTE]  
>  XML- und CLR-Parameter werden für nummerierte Prozeduren nicht unterstützt.  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
