---
title: sys. pdw_health_components (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5205c1ac6248f5aadee01410b4ba5e8f00332a73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68127486"
---
# <a name="syspdw_health_components-transact-sql"></a>sys. pdw_health_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Speichert Informationen zu allen Komponenten und Geräten, die im System vorhanden sind. Dazu zählen Hardware, Speichergeräte und Netzwerkgeräte.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|component_id|**int**|Eindeutiger Bezeichner einer Komponente oder eines Geräts.<br /><br /> Der Schlüssel für diese Ansicht.|NOT NULL|  
|group_id|**Wartenden**|Die logische Komponentengruppe, zu der diese Komponente gehört. Weitere Informationen finden Sie unter [sys. pdw_health_components (Parallel Data Warehouse)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|component_name|**nvarchar(255)**|Der Name der Komponente.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
