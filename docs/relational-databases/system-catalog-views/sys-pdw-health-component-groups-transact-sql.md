---
title: sys. pdw_health_component_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 5ba27432-7a29-4420-b73d-def621c0b3ac
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 36c931af24e7bd6ee3faa7dcd4aa2da31315b656
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87397139"
---
# <a name="syspdw_health_component_groups-transact-sql"></a>sys. pdw_health_component_groups (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Speichert Informationen über logische Gruppierungen von Komponenten und Geräten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|Eindeutiger Bezeichner für Komponenten und Geräte.<br /><br /> Der Schlüssel für diese Ansicht.|NOT NULL|  
|group_name|**nvarchar(255)**|Der Name der logischen Gruppe für die Komponenten und Geräte.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
