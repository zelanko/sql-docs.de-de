---
title: Überwachen der Geräte Integrität
description: Überwachen des Status einer Analytics-Platt Form System Appliance mithilfe der Verwaltungskonsole oder durch direktes Abfragen der parallelen Data Warehouse dynamischen Verwaltungs Sichten.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: b99123f81fcdddd74dc72d485d97e428ca59ed84
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400992"
---
# <a name="monitor-appliance-health-state"></a>Geräte Integritäts Status überwachen
In diesem Artikel wird erläutert, wie Sie den Status eines Analytics-plattformsystems mithilfe der Verwaltungskonsole oder durch direktes Abfragen der parallelen Data Warehouse dynamischen Verwaltungs Sichten überwachen können. 
  
## <a name="to-monitor-the-appliance-state"></a>So überwachen Sie den Gerätestatus  
Ein Systemadministrator kann die Verwaltungskonsole (Dynamic Management Views, DMVs) von SQL Server PDW verwenden, um die vollständige Hierarchie von Knoten, Komponenten und Software abzurufen. Das folgende Diagramm bietet ein allgemeines Verständnis der Komponenten, die von SQL Server PDW überwacht werden.  
  
![Monitoring overview (Überwachung (Übersicht))](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Überwachen des Komponenten Status mithilfe der Verwaltungskonsole  
So rufen Sie den Komponenten Status mithilfe der Verwaltungskonsole ab  
  
1.  Klicken Sie auf die Registerkarte **Appliance State** .  
  
2.  Klicken Sie auf der Seite Appliance State auf einen bestimmten Knoten, um die Knoten Details anzuzeigen.  
  
    ![PDW-Verwaltungskonsole, Status](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>Überwachen des Komponenten Status mithilfe von System Sichten  
Um den Komponenten Status mithilfe von System Sichten abzurufen, verwenden Sie [sys. dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Die folgende Abfrage ruft z. b. den Status für alle-Komponenten ab.  
  
```sql  
SELECT   
   s.[pdw_node_id],  
   n.[name] as [node_name],  
   n.[address] ,  
   g.[group_id] ,  
   g.[group_name] ,  
   c.[component_id] ,  
   c.[component_name] ,  
   s.[component_instance_id] ,   
   p.[property_name] ,  
   s.[property_value] ,  
   s.[update_time]  
FROM [sys].[dm_pdw_component_health_status] AS s  
JOIN sys.dm_pdw_nodes AS n   
   ON s.[pdw_node_id] = n.[pdw_node_id]  
JOIN [sys].[pdw_health_components] AS c   
   ON s.[component_id] = c.[component_id]  
JOIN [sys].[pdw_health_component_groups] AS g   
   ON c.[group_id] = g.[group_id]  
JOIN [sys].[pdw_health_component_properties] AS p   
   ON s.[property_id] = p.[property_id] AND s.[component_id] = p.[component_id]  
WHERE p.property_name = 'Status'  
ORDER BY  
   s.[pdw_node_id],  
   g.[group_name] ,   
   s.[component_instance_id] ,  
   c.[component_name] ,   
   p.[property_name];  
```  
  
Mögliche Werte, die für die Eigenschaft Status zurückgegeben werden, sind:  
  
-   OK,  
  
-   Nicht schwerwiegender  
  
-   Kritisch  
  
-   Unbekannt  
  
-   Nicht unterstützt  
  
-   Nicht erreichbar  
  
-   Nicht behebbar  
  
Um alle Eigenschaften für alle Komponenten anzuzeigen, entfernen Sie die- `WHERE  p.property_name = 'Status'` Klausel.  
  
In der Spalte **[update_time]** wird der Zeitpunkt angezeigt, zu dem die Komponente zuletzt von den SQL Server PDW Health-Agents abgerufen wurde.  
  
> [!CAUTION]  
> Stellen Sie sicher, dass Sie das Problem untersuchen, wenn eine Komponente mindestens 5 Minuten lang nicht abgerufen wurde. möglicherweise wird eine Warnung angezeigt, die auf ein Problem mit den Software Takten hinweist.  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Geräteüberwachung &#40;Analytics-Platt Form System&#41;](appliance-monitoring.md)  
  
