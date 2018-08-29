---
title: Sys. server_triggers (Transact-SQL) | Microsoft-Dokumentation
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
- server_triggers
- sys.server_triggers_TSQL
- server_triggers_TSQL
- sys.server_triggers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_triggers catalog view
ms.assetid: 25926ff4-9271-45bf-bc32-d5d3344bd47a
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: caed89727f8fe6670db1b2531c0c2641ed92b38b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43024589"
---
# <a name="sysservertriggers-transact-sql"></a>sys.server_triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Umfasst die Gruppe aller DDL-Trigger auf Serverebene, für die für object_type entweder TR oder TA festgelegt ist. Im Falle von CLR-Triggern muss die Assembly in die **master** -Datenbank geladen werden. Alle Namen von DDL-Triggern auf Serverebene sind in einem globalen Bereich vorhanden.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Name des Triggers.|  
|**object_id**|**int**|ID des Objekts.|  
|**parent_class**|**tinyint**|Klasse des übergeordneten Objekts. Ist immer:<br /><br /> 100 = Server|  
|**parent_class_desc**|**nvarchar(60)**|Die Beschreibung der Klasse des übergeordneten Objekts. Ist immer:<br /><br /> SERVER.|  
|**Parent_ID**|**int**|Ist immer 0 für Trigger auf dem SERVER.|  
|**type**|**char(2)**|Objekttyp:<br /><br /> TA = Assembly (CLR) Trigger<br /><br /> TR = SQL-Trigger|  
|**type_desc**|**nvarchar(60)**|Beschreibung der Klasse des Objekttyps.<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|Das Datum, an dem der Trigger erstellt wurde.|  
|**modify_date**|**datetime**|Das Datum, an dem der Trigger zuletzt mit einer ALTER-Anweisung geändert wurde.|  
|**is_ms_shipped**|**bit**|Trigger im Auftrag des Benutzers, der von einer internen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponente.|  
|**is_disabled**|**bit**|1 = Trigger ist deaktiviert.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
