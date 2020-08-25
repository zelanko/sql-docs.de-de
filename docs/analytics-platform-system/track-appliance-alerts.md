---
title: Nachverfolgen von Appliancewarnungen
description: Geräte Warnungen in Analytics Platform System nachverfolgen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 03568666367bf6273f197994f572bbbbd62bb42e
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "74399944"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Geräte Warnungen in Analytics Platform System nachverfolgen
In diesem Thema wird erläutert, wie Sie die-Verwaltungskonsole und-System Sichten verwenden, um Warnungen in einem SQL Server PDW Appliance zu verfolgen.  
  
## <a name="to-track-appliance-alerts"></a>So verfolgen Sie Geräte Warnungen  
SQL Server PDW erstellt Warnungen für Hardware-und Software Probleme, für die eine Aufmerksamkeit erforderlich ist. Jede Warnung enthält einen Titel und eine Beschreibung des Problems.  
  
SQL Server PDW protokolliert Warnungen in der [sys. dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) -DMV. Das System behält eine Beschränkung von 10.000 Warnungen bei und löscht die älteste Warnung zuerst, wenn der Grenzwert überschritten wird.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Anzeigen von Warnungen mithilfe der Verwaltungskonsole  
Es gibt eine Registerkarte **Warnungen** für den PDW-Bereich und für die Fabric-Region des Geräts. Nach dem Failover ist das failoverereignis in der Anzahl der Warnungen auf der Seite enthalten. Es gibt eine Seite für den PDW-Bereich und für die Fabric-Region des Geräts. Jede Integritäts Seite verfügt über eine Registerkarte. Wenn Sie weitere Informationen zu einer Warnung erhalten möchten, klicken Sie auf **die Seite Integrität, die Register** Karte **Warnungen** , und klicken Sie dann auf eine Warnung.  
  
![PDW-Verwaltungskonsole, Warnungen](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
Auf der Seite **Warnungen** :  
  
-   Um den Warnungs Verlauf anzuzeigen, klicken Sie auf den Link Warnungs **Verlauf überprüfen** .  
  
-   Um die Warnungs Komponente und die aktuellen Eigenschaftswerte anzuzeigen, klicken Sie auf die Zeile Warnung.  
  
-   Zum Anzeigen von Details zu dem Knoten, der die Warnung ausgelöst hat, klicken Sie auf den Knoten Namen.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Anzeigen von Warnungen mithilfe der System Sichten  
Fragen Sie zum Anzeigen von Warnungen mithilfe von System Sichten [sys. dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md)ab. Diese DMV zeigt Warnungen an, die nicht korrigiert wurden. Wenn Sie Hilfe bei der Selektierung von Warnungen und Fehlern benötigen, verwenden Sie die [sys. dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) -DMV.  
  
Das folgende Beispiel ist eine gängige Abfrage zum Anzeigen der aktuellen Warnungen.  
  
```sql  
SELECT   
    aa.[pdw_node_id],  
    n.[name] AS [node_name],  
    g.[group_name] ,  
    c.[component_name] ,  
    aa.[component_instance_id] ,   
    a.[alert_name] ,  
    a.[state] ,  
    a.[severity] ,  
    aa.[current_value] ,  
    aa.[previous_value] ,  
    aa.[create_time] ,  
    a.[description]   
FROM [sys].[dm_pdw_component_health_active_alerts] AS aa  
    INNER JOIN sys.dm_pdw_nodes AS n   
        ON aa.[pdw_node_id] = n.[pdw_node_id]  
    INNER JOIN [sys].[pdw_health_components] AS c   
        ON aa.[component_id] = c.[component_id]  
    INNER JOIN [sys].[pdw_health_component_groups] AS g   
        ON c.[group_id] = g.[group_id]  
    INNER JOIN [sys].[pdw_health_alerts] AS a   
        ON aa.[alert_id] = a.[alert_id] and aa.[component_id] = c.[component_id]  
ORDER BY  
    a.alert_id ,  
    aa.[pdw_node_id];  
```  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[Geräteüberwachung &#40;Analytics-Platt Form System&#41;](appliance-monitoring.md)  
  
