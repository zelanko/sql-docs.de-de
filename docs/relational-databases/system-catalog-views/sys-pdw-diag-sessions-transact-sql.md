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
ms.openlocfilehash: 6ae00a9b691deac38ebe3ea3ad4ed67ca3fd4dbe
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396072"
---
# <a name="syspdw_diag_sessions-transact-sql"></a>sys. pdw_diag_sessions (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Enthält Informationen zu den verschiedenen Diagnose Sitzungen, die auf dem System erstellt wurden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Der Name der Diagnose Sitzung.<br /><br /> Der Schlüssel für diese Ansicht.||  
|**xml_data**|**nvarchar(4000)**|XML-Nutzlast, die die Sitzung beschreibt.||  
|**is_active**|**bit**|Flag zum angeben, ob das Flag aktiv ist.||  
|**host_address**|**nvarchar(255)**|Adresse des Computers, auf dem die Sitzungs Definition (Steuerungs Knoten) gehostet wird.||  
|**principal_id**|**int**|ID des Benutzers, der die Sitzung auf Datenbankebene erstellt hat.||  
|**database_id**|**int**|ID der Datenbank, die den Bereich der Diagnose Sitzung ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
