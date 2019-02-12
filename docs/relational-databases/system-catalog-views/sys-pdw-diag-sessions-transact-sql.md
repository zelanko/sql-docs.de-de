---
title: pdw_diag_sessions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bd48648719e04ca1eec15c4594b08cc1d40505b9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028631"
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu den verschiedenen diagnosesitzungen, die auf dem System erstellt wurden.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Der Name der diagnosesitzung.<br /><br /> Der Schlüssel für diese Sicht.||  
|**xml_data**|**nvarchar(4000)**|XML-Nutzlast, die Beschreibung der Sitzung.||  
|**is_active**|**bit**|Flag zur Angabe, ob das Flag aktiv ist.||  
|**host_address**|**nvarchar(255)**|Die Adresse des Computers die Sitzungsdefinition (steuerknoten) hosten.||  
|**principal_id**|**int**|Die ID des Benutzers, der die Sitzung auf der Datenbankebene erstellt.||  
|**database_id**|**int**|Die ID der Datenbank, die den Bereich der diagnosesitzung.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
