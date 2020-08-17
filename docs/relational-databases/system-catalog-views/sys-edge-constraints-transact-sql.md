---
description: sys. edge_constraints (Transact-SQL)
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
ms.openlocfilehash: 7ceea1b9ad0c7995240187518522633de4ace1c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88377836"
---
# <a name="sysedge_constraints-transact-sql"></a>sys. edge_constraints (Transact-SQL)
[!INCLUDE[sqlserver2019](../../includes/applies-to-version/sqlserver2019.md)]

Enthält eine Zeile für jedes Objekt, bei dem es sich um eine Edge-Einschränkung handelt. 
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**\<Columns inherited from sys.objects>**||Eine Liste der Spalten, die diese Sicht erbt, finden Sie unter [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_disabled**|**bit**|1 = die Edge-Einschränkung ist disgerenselt.<br /><br /> 0 = die Edge-Einschränkung ist aktiviert.|  
|**is_not_trusted**|**bit**|1 = Edge-Einschränkung wurde nicht vom System überprüft.<br /><br /> 0 = Edge-Einschränkung wurde vom System überprüft.|  
|**delete_referential_action**|**tinyint**|Referenzielle Aktion, die für diese Edge-Einschränkung definiert wurde.<br /><br />0 = keine Aktion.|  
|**delete_referential_action_desc**|**nvarchar(60)**|Beschreibung der referenziellen Aktion, die für diese Edge-Einschränkung definiert wurde.<br /><br />NO_ACTION|  
|**is_system_named**|**bit**|1 = der Name der Edge-Einschränkung wurde vom System generiert.<br /><br />0 = der Name der Edge-Einschränkung wurde vom Benutzer angegeben.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
