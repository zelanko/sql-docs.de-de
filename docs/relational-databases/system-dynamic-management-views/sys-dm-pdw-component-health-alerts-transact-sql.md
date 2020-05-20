---
title: sys. dm_pdw_component_health_alerts (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 88f05392-1e97-4693-ba60-a4910af3c000
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 25b9274946c5890e5ff688663a0cd3d37cb3850e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82811390"
---
# <a name="sysdm_pdw_component_health_alerts-transact-sql"></a>sys. dm_pdw_component_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Speichert zuvor ausgegebene Warnungen auf Appliance-Komponenten.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Eindeutiger Bezeichner eines [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] Knotens.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|component_id|**int**|Die ID der Komponente. Weitere Informationen finden Sie unter [sys. pdw_health_components &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|alert_id|**int**|Die ID für den Warnungstyp. Weitere Informationen finden Sie unter [sys. pdw_health_alerts &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|alert_instance_id|**nvarchar (36)**|Identifiziert eine Instanz einer bestimmten Warnung.<br /><br /> pdw_node_id, component_id, component_instance_id, alert_id und alert_instance_id bilden den Schlüssel für diese Sicht.|NOT NULL|  
|previous_value|**nvarchar(255)**|Wird verwendet, wenn die Warnung vom Typ Status schange ist. Dies ist der vorherige Komponenten Status. Der Wert ist für Warnungen vom Typ Schwellenwert NULL. Eine Liste der Warnungs Typen finden Sie unter [sys. pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) .|NULL|  
|current_value|**nvarchar(255)**|Wird verwendet, wenn die Warnung vom Typ Status schange ist. Dies ist der aktuelle Komponenten Status. Der Wert ist für Warnungen vom Typ Schwellenwert NULL. Eine Liste der Warnungs Typen finden Sie unter [sys. pdw_health_alerts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) .|NULL|  
|create_time|**datetime**|Uhrzeit und Datum, zu der die Warnung generiert wurde.|NOT NULL|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
