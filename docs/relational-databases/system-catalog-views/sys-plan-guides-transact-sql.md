---
title: Sys. plan_guides (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.planguides_TSQL
- plan_guides
- sys.planguides
- plan_guides_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.plan_guides catalog view
ms.assetid: 3dde0397-ef6f-4b3f-8250-3f25584eb62b
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 19b78ff53b5640d74b49d2e5956c39aa1df2e230
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68068068"
---
# <a name="sysplanguides-transact-sql"></a>sys.plan_guides (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Planhinweisliste in der Datenbank.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**plan_guide_id**|**int**|Eindeutiger Bezeichner für die Planhinweisliste in der Datenbank.|  
|**name**|**sysname**|Name der Planhinweisliste.|  
|**create_date**|**datetime**|Datum und Uhrzeit der Erstellung der Planhinweisliste.|  
|**modify_date**|**Datetime**|Datum, an dem die Planhinweisliste zuletzt geändert wurde.|  
|**is_disabled**|**bit**|1 = Planhinweisliste ist deaktiviert.<br /><br /> 0 = Planhinweisliste ist aktiviert.|  
|**query_text**|**nvarchar(max)**|Text der Abfrage, anhand derer die Planhinweisliste erstellt wird.|  
|**scope_type**|**tinyint**|Identifiziert den Bereich der Planhinweisliste.<br /><br /> 1 = OBJECT<br /><br /> 2 = SQL<br /><br /> 3 = TEMPLATE|  
|**scope_type_desc**|**nvarchar(60)**|Beschreibung des Bereichs der Planhinweisliste.<br /><br /> OBJECT<br /><br /> SQL<br /><br /> TEMPLATE|  
|**scope_object_id**|**Int**|object_id des Objekts, das den Bereich der Planhinweisliste definiert, wenn der Bereich OBJECT ist.<br /><br /> NULL, wenn der Bereich der Planhinweisliste nicht OBJECT ist.|  
|**scope_batch**|**nvarchar(max)**|Batchtext, wenn **Scope_type** SQL ist.<br /><br /> NULL, wenn der Batchtyp nicht SQL ist.<br /><br /> Wenn der Wert NULL und **Scope_type** SQL ist, den Wert der **Query_text** gilt.|  
|**parameters**|**nvarchar(max)**|Die Zeichenfolge zur Definition der Liste der Parameter, die mit der Planhinweisliste verknüpft sind.<br /><br /> NULL = Mit der Planhinweisliste ist keine Parameterliste verknüpft.|  
|**Hinweise**|**nvarchar(max)**|Die Hinweise der OPTION-Klausel, die mit der Planhinweisliste verknüpft sind.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
