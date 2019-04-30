---
title: Nachverfolgen von appliancewarnungen - Analytics Platform System | Microsoft-Dokumentation
description: Nachverfolgen von appliancewarnungen in Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f38f76975290538a35203ddbbed84b9354285edc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156983"
---
# <a name="track-appliance-alerts-in-analytics-platform-system"></a>Nachverfolgen von appliancewarnungen in Analytics Platform System
In diesem Thema wird erläutert, wie Sie mit der Verwaltungskonsole und Systemsichten zum Nachverfolgen von Warnungen in einer SQL Server-PDW-Appliance.  
  
## <a name="to-track-appliance-alerts"></a>Zum Nachverfolgen von Appliancewarnungen  
SQL Server PDW erstellt Warnungen für Hardware und Software-Probleme, die Ihre Aufmerksamkeit erfordern. Jede Warnung enthält einen Titel und eine Beschreibung des Problems.  
  
SQL Server PDW protokolliert Warnungen in der [sys.dm_pdw_component_health_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md) DMV. Das System behält maximal 10.000 Benachrichtigungen und löscht zuerst die älteste Warnung, wenn das Limit überschritten wird.  
  
### <a name="view-alerts-by-using-the-admin-console"></a>Anzeigen von Warnungen mithilfe der Verwaltungskonsole  
Es gibt eine **Warnungen** Registerkarte für die PDW-Region und für den Fabric-Bereich des Geräts. Nach dem Failover auftritt, ist das failoverereignis in die Anzahl der Warnungen auf der Seite enthalten. Eine Seite, die für die PDW-Region und für den Fabric-Bereich des Geräts ist vorhanden. Jede Seite "Integrität" verfügt über eine Registerkarte. Weitere Informationen zu einer Warnung, klicken Sie auf die **Integrität** Seite die **Warnungen** Registerkarte, und klicken Sie dann auf eine Warnung.  
  
![PDW Admin Console Alerts](./media/track-appliance-alerts/SQL_Server_PDW_AdminConsole_AlertsV2.png "SQL_Server_PDW_AdminConsole_AlertsV2")  
  
Auf der **Warnungen** Seite:  
  
-   Um der Warnung dem Verlauf anzuzeigen, klicken Sie auf die **Warnung Überprüfungsverlauf** Link.  
  
-   Um die Warnung Komponente und die aktuellen Eigenschaftswerte anzuzeigen, klicken Sie auf die Warnung Zeile.  
  
-   Zum Anzeigen von Details über den Knoten, der die Warnung ausgelöst hat, klicken Sie auf den Knotennamen.  
  
### <a name="view-alerts-by-using-the-system-views"></a>Anzeigen von Warnungen mithilfe von Systemsichten  
Zum Anzeigen von Warnungen mithilfe von Systemsichten Abfragen [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md). Diese dynamische Verwaltungssicht zeigt die Warnungen, die nicht behoben wurden. Verwenden Sie für Hilfe beim Selektieren von Warnungen und Fehler, die [sys.dm_pdw_errors](../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md) DMV.  
  
Im folgende Beispiel wird eine allgemeine Abfrage für die aktuellen Warnungen anzeigen.  
  
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
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->
[Applianceüberwachung &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
