---
title: sys. edge_constraints (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.edge_constraints
- edge_constraints
- SQL Graph
- edge_constraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.edge_constraints catalog view
ms.assetid: 0f782d2f-7126-46ab-85b7-bcba44862231
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5dc2e47c49dc9d639489426fceab0b848c9def3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079317"
---
# <a name="sysedge_constraints-transact-sql"></a>sys. edge_constraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Enthält eine Zeile für jedes Objekt, bei dem es sich um eine Edge-Einschränkung handelt. 
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<Von sys. Objects geerbte Spalten>**||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_disabled**|**bit**|1 = die Edge-Einschränkung ist disgerenselt.<br /><br /> 0 = die Edge-Einschränkung ist aktiviert.|  
|**is_not_trusted**|**bit**|1 = Edge-Einschränkung wurde nicht vom System überprüft.<br /><br /> 0 = Edge-Einschränkung wurde vom System überprüft.|  
|**delete_referential_action**|**tinyint**|Referenzielle Aktion, die für diese Edge-Einschränkung definiert wurde.<br /><br />0 = keine Aktion.|  
|**delete_referential_action_desc**|**nvarchar (60)**|Beschreibung der referenziellen Aktion, die für diese Edge-Einschränkung definiert wurde.<br /><br />NO_ACTION|  
|**is_system_named**|**bit**|1 = der Name der Edge-Einschränkung wurde vom System generiert.<br /><br />0 = der Name der Edge-Einschränkung wurde vom Benutzer angegeben.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
