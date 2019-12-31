---
title: sys. dm_pdw_component_health_active_alerts (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 90531889d3e510d342ff39abdf069f75f3c371aa
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401712"
---
# <a name="sysdm_pdw_component_health_active_alerts-transact-sql"></a>sys. dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Speichert aktive Warnungen für [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] -Komponenten.  
  
|Spaltenname|Datentyp|Beschreibung|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**wartenden**|Eindeutiger Bezeichner [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] eines Knotens.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|component_id|**wartenden**|Die ID der Komponente. Weitere Informationen finden Sie unter [sys. pdw_health_components &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|alert_id|**wartenden**|Die ID für den Warnungstyp. Weitere Informationen finden Sie unter [sys. pdw_health_alerts &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|alert_instance_id|**nvarchar (36)**|Identifiziert eine Instanz einer bestimmten Warnung.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|current_value|**nvarchar(255)**|Wird verwendet, wenn die Warnung vom Typ Status schange ist. Dies ist der aktuelle Komponenten Status. Der Wert ist für Warnungen vom Typ Schwellenwert NULL. Eine Liste der Warnungs Typen finden Sie unter [sys. pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) .|NULL|  
|previous_value|**nvarchar(255)**|Wird verwendet, wenn die Warnung vom Typ Status schange ist. Dies ist der vorherige Komponenten Status. Der Wert ist für Warnungen vom Typ Schwellenwert NULL. Eine Liste der Warnungs Typen finden Sie unter [sys. pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) .|NULL|  
|create_time|**DateTime**|Uhrzeit und Datum, zu der die Warnung generiert wurde.|NOT NULL|  
  
 Informationen über die maximale Anzahl von Zeilen, die in dieser Sicht beibehalten werden, finden Sie unter "Mindest [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]-und Höchstwerte" in der.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
