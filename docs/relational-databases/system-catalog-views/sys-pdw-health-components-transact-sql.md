---
description: sys. pdw_health_components (Transact-SQL)
title: sys. pdw_health_components (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 74b741d94d5e9a10c4b657cfbe70ad69f9cbbfa1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88400766"
---
# <a name="syspdw_health_components-transact-sql"></a>sys. pdw_health_components (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Speichert Informationen zu allen Komponenten und Geräten, die im System vorhanden sind. Dazu zählen Hardware, Speichergeräte und Netzwerkgeräte.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|component_id|**int**|Eindeutiger Bezeichner einer Komponente oder eines Geräts.<br /><br /> Der Schlüssel für diese Ansicht.|NOT NULL|  
|group_id|**Int**|Die logische Komponentengruppe, zu der diese Komponente gehört. Weitere Informationen finden Sie unter [sys. pdw_health_components (Parallel Data Warehouse)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|component_name|**nvarchar(255)**|Der Name der Komponente.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
