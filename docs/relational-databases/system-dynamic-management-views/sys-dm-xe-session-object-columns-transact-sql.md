---
description: sys.dm_xe_session_object_columns (Transact-SQL)
title: sys. dm_xe_session_object_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_session_object_columns_TSQL
- sys.dm_xe_session_object_columns_TSQL
- dm_xe_session_object_columns
- sys.dm_xe_session_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- xe
- sys.dm_xe_session_object_columns dynamic management view
ms.assetid: e97f3307-2da6-4c54-b818-a474faec752e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba65acaf8feb98a959e9ef37c7fdd26d1ce29121
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498257"
---
# <a name="sysdm_xe_session_object_columns-transact-sql"></a>sys.dm_xe_session_object_columns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Zeigt die Konfigurationswerte für Objekte an, die an eine Sitzung gebunden sind.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Die Speicheradresse der Ereignissitzung. Hat eine n:1-Beziehung mit sys.dm_xe_sessions.address. Lässt keine NULL-Werte zu.|  
|column_name|**nvarchar(256)**|Der Name des Konfigurationswerts. Lässt keine NULL-Werte zu.|  
|column_id|**int**|Die ID der Spalte. Ist eindeutig innerhalb des Objekts. Lässt keine NULL-Werte zu.|  
|column_value|**nvarchar (3072)**|Der konfigurierte Wert der Spalte. Lässt NULL-Werte zu.|  
|object_type|**nvarchar(60)**|Der Typ des Objekts. Lässt keine NULL-Werte zu. object_type ist einer der folgenden:<br /><br /> event<br /><br /> target|  
|object_name|**nvarchar(256)**|Der Name des Objekts, zu dem diese Spalte gehört. Lässt keine NULL-Werte zu.|  
|object_package_guid|**uniqueidentifier**|Die GUID des Pakets, das das Objekt enthält. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|An|Beziehung|  
|----------|--------|------------------|  
|dm_xe_session_object_columns. object_name<br /><br /> dm_xe_session_object_columns.object_package_guid|sys. dm_xe_objects. package_guid,<br /><br /> sys.dm_xe_objects.name|n:1|  
|dm_xe_session_object_columns. column_name<br /><br /> dm_xe_session_object_columns.column_id|sys. dm_xe_object_columns. Name,<br /><br /> sys.dm_xe_object_columns.column_id|n:1|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

