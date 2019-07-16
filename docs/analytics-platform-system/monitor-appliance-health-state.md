---
title: Überwachen der Integrität der Appliance – Analytics Platform System
description: Informationen zum Überwachen des Zustands einer Analytics Platform System Appliance mithilfe der Verwaltungskonsole oder durch direkte Abfrage der dynamischen Verwaltungssichten von Parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c69e46ad6a37a17a12c37f83625b5c7f6eaf8078
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960615"
---
# <a name="monitor-appliance-health-state"></a>Integritätsstatus des Monitors Appliance
In diesem Artikel wird erläutert, wie den Status des Analytics Platform System Appliance mithilfe der Verwaltungskonsole oder durch direkte Abfrage der dynamischen Verwaltungssichten von Parallel Data Warehouse überwacht wird. 
  
## <a name="to-monitor-the-appliance-state"></a>Zum Überwachen des Status des Geräts  
Ein Systemadministrator kann die-Verwaltungskonsole oder der SQL Server PDW Dynamic Management Views (DMVs) verwenden, um die vollständige Hierarchie von Knoten, die Komponenten und die Software zu abzurufen. Das folgende Diagramm bietet auf hoher Ebenen einen Überblick über die Komponenten, die SQL Server PDW überwacht.  
  
![Übersicht über den](./media/monitor-appliance-health-state/SQL_Server_PDW_Monitoring_Overview.png "SQL_Server_PDW_Monitoring_Overview")  
  
### <a name="monitor-component-status-by-using-the-admin-console"></a>Überwachungsstatus von Komponente mithilfe der Verwaltungskonsole  
Komponentenstatus abrufen, indem Sie mit der Verwaltungskonsole:  
  
1.  Klicken Sie auf die **Anwendungszustand** Registerkarte.  
  
2.  Klicken Sie auf auf einem bestimmten Knoten zum Anzeigen der knotendetails, auf der Seite Status des Geräts.  
  
    ![PDW-Verwaltungskonsole, Status](./media/monitor-appliance-health-state/SQL_Server_PDW_AdminConsol_State.png "SQL_Server_PDW_AdminConsol_State")  
  
### <a name="monitor-component-status-by-using-system-views"></a>Überwachungsstatus von Komponenten mithilfe von Systemansichten  
Verwenden Sie zum Abrufen mithilfe von Systemansichten Komponentenstatus [sys.dm_pdw_component_health_status](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md). Die folgende Abfrage ruft z. B. den Status für alle Komponenten ab.  
  
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
  
Mögliche Werte für die Status-Eigenschaft zurückgegeben werden:  
  
-   Okay  
  
-   NonCritical  
  
-   Kritisch  
  
-   Unbekannt  
  
-   Nicht unterstützt  
  
-   Nicht erreichbar.  
  
-   Nicht behebbarer  
  
Zum Anzeigen aller Eigenschaften für alle Komponenten entfernen der `WHERE  p.property_name = 'Status'` Klausel.  
  
Die **[Update_time]** zeigt der Spalte der letzten Ausführung die Komponente wurde von der SQL Server-PDW-Health-Agents abgerufen.  
  
> [!CAUTION]  
> Achten Sie darauf, dass Sie das Problem zu untersuchen, wenn eine Komponente nicht 5 Minuten oder länger abgerufen wurde. Es kann eine Warnung aus, die ein Problem mit der Software-Takte angibt.  
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Applianceüberwachung &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
