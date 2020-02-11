---
title: Ermitteln des fehlerhaften Cluster Knotens
description: In diesem Artikel wird beschrieben, wie Sie den Namen des Knotens "Analytics Platform System (APS)" ermitteln, bei dem nach einem Cluster Failover ein Fehler aufgetreten ist und eine Cluster Failover-Warnung ausgelöst wurde. Im Rahmen der Problembehandlung eines Cluster Failovers müssen Sie den Namen des Knotens ermitteln, bei dem ein Fehler aufgetreten ist, bevor Sie sich an Microsoft wenden, um das Problem zu beheben.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 68ebdb7f17ddee311644e11c48eaa4b586beac74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401198"
---
# <a name="determine-which-cluster-node-failed-for-analytics-platform-system"></a>Ermitteln des fehlerhaften Cluster Knotens für das Analytics-Platt Form System
In diesem Thema wird beschrieben, wie Sie den Namen des Knotens "Analytics Platform System (APS)" ermitteln, bei dem nach einem Cluster Failover ein Fehler aufgetreten ist und eine Cluster Failover-Warnung ausgelöst wurde. Im Rahmen der Problembehandlung eines Cluster Failovers müssen Sie den Namen des Knotens ermitteln, bei dem ein Fehler aufgetreten ist, bevor Sie sich an Microsoft wenden, um das Problem zu beheben.  
  
## <a name="Background"></a>Kulisse  
Für hohe Verfügbarkeit in SQL Server PDW sind der Steuerungs Knoten und die Computeknoten als aktive oder passive Komponenten von Windows-Failoverclustern konfiguriert. Wenn ein aktiver Server nicht auf kritische Systemanforderungen reagiert, führt der passive Server ein Failover durch und führt die Funktionen des Servers aus, bei dem ein Fehler aufgetreten ist.  
  
Wenn nach einem Cluster Failover SQL Server PDW Berichte zum Knoten Status ausgeführt wird, hat der passive Server einen Failover-Status. Es ist jedoch nicht offensichtlich, bei welchem Server oder Knoten ein Fehler aufgetreten ist, insbesondere, wenn der fehlerhafte Server weiterhin online ist. Zum Beheben des Cluster Fehlers müssen Sie den Namen des Knotens ermitteln, für den ein Failover ausgeführt wurde.  
  
## <a name="AdminConsoleSolution"></a>Verwaltungs Konsolen Lösung  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>So ermitteln Sie den Namen des fehlgeschlagenen Knotens  
  
1.  Öffnen Sie die Verwaltungskonsole. Weitere Informationen zur Verwaltungskonsole finden [Sie unter Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Nach dem Failover ist das failoverereignis in der Anzahl der Warnungen auf **der Seite "** Integrität" enthalten. Es gibt eine **Integritäts Seite für** die PDW-Region und die Fabric-Region des Geräts. Jede Integritäts Seite verfügt über eine Registerkarte **Warnungen** . Wenn Sie weitere Informationen zu einer Warnung erhalten möchten, klicken Sie auf die Seite Integrität, die Registerkarte Warnungen, und klicken Sie dann auf eine Warnung.  
  
## <a name="SystemView"></a>System Ansichts Lösung  
Die folgende SQL-Anweisung zeigt, wie Sie die Systemsicht [sys. dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md) verwenden, um den Namen des Servers zu ermitteln, bei dem ein Fehler aufgetreten ist.  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
