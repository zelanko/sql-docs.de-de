---
title: sys. pdw_diag_sessions (Transact-SQL) | Microsoft-Dokumentation
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
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fa06005679e31381f723b30b9f68e5ce0d89ae1e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127691"
---
# <a name="syspdw_diag_sessions-transact-sql"></a>sys. pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Enthält Informationen zu den verschiedenen Diagnose Sitzungen, die auf dem System erstellt wurden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Der Name der Diagnose Sitzung.<br /><br /> Der Schlüssel für diese Ansicht.||  
|**xml_data**|**nvarchar(4000)**|XML-Nutzlast, die die Sitzung beschreibt.||  
|**is_active**|**bit**|Flag zum angeben, ob das Flag aktiv ist.||  
|**host_address**|**nvarchar(255)**|Adresse des Computers, auf dem die Sitzungs Definition (Steuerungs Knoten) gehostet wird.||  
|**principal_id**|**int**|ID des Benutzers, der die Sitzung auf Datenbankebene erstellt hat.||  
|**database_id**|**int**|ID der Datenbank, die den Bereich der Diagnose Sitzung ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
