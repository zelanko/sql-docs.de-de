---
description: sys.dm_xe_map_values (Transact-SQL)
title: sys. dm_xe_map_values (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_map_values
- dm_xe_map_values
- dm_xe_map_values_TSQL
- sys.dm_xe_map_values_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_map_values dynamic management view
- xe
ms.assetid: c0c5dd7e-9cee-47e2-b65a-88194c00aa1f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 46f94a90a63c64e8a2b841337b875256154e2e22
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498319"
---
# <a name="sysdm_xe_map_values-transact-sql"></a>sys.dm_xe_map_values (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Zuordnung von internen numerischen Schlüsseln auf für den Benutzer lesbaren Text zurück.  
 
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(256)**|Der Name der Zuordnung. der Name ist im gesamten lokalen System eindeutig. Lässt keine NULL-Werte zu.|  
|object_package_guid|**uniqueidentifier**|Die GUID des Pakets, das die Zuordnung enthält. Lässt keine NULL-Werte zu.|  
|map_key|**int**|Der interne Schlüsselwert. Lässt keine NULL-Werte zu.|  
|map_value|**nvarchar (3072)**|Eine Beschreibung des Schlüsselwerts. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
### <a name="relationship-cardinalities"></a>Kardinalität der Beziehungen  
  
|Von|An|Beziehung|  
|----------|--------|------------------|  
|dm_xe_map_values.object_package_guid<br /><br /> dm_xe_map_values.name|sys.dm_xe_objects.package_guid<br /><br /> sys.dm_xe_objects.name|n:1| 
  
## <a name="see-also"></a>Siehe auch  
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

