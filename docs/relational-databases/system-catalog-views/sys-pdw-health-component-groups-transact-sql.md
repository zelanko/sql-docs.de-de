---
description: sys.pdw_health_component_groups (Transact-SQL)
title: sys.pdw_health_component_groups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 5ba27432-7a29-4420-b73d-def621c0b3ac
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 552a4b28187687c21312c5918788eaf85e799597
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464631"
---
# <a name="syspdw_health_component_groups-transact-sql"></a>sys.pdw_health_component_groups (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Speichert Informationen über logische Gruppierungen von Komponenten und Geräten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Range|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|Eindeutiger Bezeichner für Komponenten und Geräte.<br /><br /> Der Schlüssel für diese Ansicht.|NOT NULL|  
|group_name|**nvarchar(255)**|Der Name der logischen Gruppe für die Komponenten und Geräte.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten von Azure Synapse Analytics und Parallel Data Warehouse Catalog](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
