---
title: Sys.pdw_diag_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fa98b2980f226b515c5ae202eea0972326d998bc
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
ms.locfileid: "33698233"
---
# <a name="syspdwdiagsessions-transact-sql"></a>Sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu den verschiedenen diagnosesitzungen, die auf dem System erstellt wurden.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Name des Diagnostics-Sitzung.<br /><br /> Der Schlüssel für diese Ansicht.||  
|**xml_data**|**nvarchar(4000)**|XML-Nutzlast, die Beschreibung der Sitzung.||  
|**is_active**|**bit**|Flag, das angibt, ob das Flag aktiv ist.||  
|**host_address**|**nvarchar(255)**|Die Adresse des Computers die Sitzungsdefinition (Steuerungsknoten) hosten.||  
|**principal_id**|**int**|Die ID des Benutzers, der die Sitzung auf der Datenbankebene erstellt.||  
|**database_id**|**int**|Die ID der Datenbank, die Bestandteil der diagnosesitzung ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
