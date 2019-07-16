---
title: dm_xe_object_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_object_columns
- sys.dm_xe_object_columns_TSQL
- dm_xe_object_columns_TSQL
- dm_xe_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_object_columns dynamic management view
- extended events [SQL Server], views
ms.assetid: d96a14f3-4284-45ff-b1fe-4858e540a013
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b44824310637b279388ea367cd4ab1d07401d1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090284"
---
# <a name="sysdmxeobjectcolumns-transact-sql"></a>sys.dm_xe_object_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Schemainformationen für alle Objekte zurück.  
  
> [!NOTE]  
>  Ereignisobjekte machen feste Schemas sowohl für schreibgeschützte Daten als auch für Daten mit Schreib-Lese-Zugriff verfügbar.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|NAME|**nvarchar(256)**|Name der Spalte. Name ist eindeutig innerhalb des Objekts. Lässt keine NULL-Werte zu.|  
|column_id|**int**|Der Bezeichner der Spalte. Column_id ist eindeutig innerhalb des Objekts, wenn Sie mit Spaltentyp verwendet. Lässt keine NULL-Werte zu.|  
|object_name|**nvarchar(256)**|Der Name des Objekts, zu dem diese Spalte gehört. Es ist eine viele-zu-eins-Beziehung mit sys.dm_xe_objects.id. Lässt keine NULL-Werte zu.|  
|object_package_guid|**uniqueidentifier**|Die GUID des Pakets, das das Objekt enthält. Lässt keine NULL-Werte zu.|  
|type_name|**nvarchar(256)**|Der Name des Typs für diese Spalte. Lässt keine NULL-Werte zu.|  
|type_package_guid|**uniqueidentifier**|Die GUID des Pakets, das den Spaltendatentyp enthält. Lässt keine NULL-Werte zu.|  
|column_type|**nvarchar(60)**|Gibt an, wie diese Spalte verwendet wird. Lässt keine NULL-Werte zu. COLUMN_TYPE kann einen der folgenden sein:<br /><br /> readonly. Die Spalte enthält einen statischen Wert, der nicht geändert werden kann.<br /><br /> data. Die Spalte enthält vom Objekt verfügbar gemachte Laufzeitdaten.<br /><br /> customizable. Die Spalte enthält einen Wert, der geändert werden kann.<br /><br /> Hinweis: Durch Ändern dieses Werts können Sie das Verhalten des Objekts ändern.|  
|column_value|**nvarchar(256)**|Zeigt statische Werte an, die der Objektspalte zugeordnet sind. Lässt NULL-Werte zu.|  
|capabilities|**int**|Eine Bitmap, die die Fähigkeiten der Spalte beschreibt. Lässt NULL-Werte zu.|  
|capabilities_desc|**nvarchar(256)**|Eine Beschreibung der Fähigkeiten dieser Objektspalte. Die folgenden Werte sind möglich:<br /><br /> Mandatory. Der Wert muss festgelegt werden, wenn das übergeordnete Objekt an eine Ereignissitzung gebunden wird.<br /><br /> Lässt NULL-Werte zu.|  
|description|**nvarchar(3072)**|Die Beschreibung dieser Objektspalte. Lässt NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|Beschreibung|Beziehung|  
|----------|--------|------------------|  
|sys.dm_xe_object_columns.object_name, sys.dm_xe_object_columns.object_package_guid|sys.dm_xe_objects.name,<br /><br /> sys.dm_xe_objects.package_guid|n:1|  
|sys.dm_xe_object_columns.type_name<br /><br /> sys.dm_xe_object_columns.type_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|n:1|  
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

