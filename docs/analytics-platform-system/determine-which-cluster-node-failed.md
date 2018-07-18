---
title: Ermitteln von fehlgeschlagenen Clusterknoten - Analytics Platform System | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie den Namen des Knotens Analytics Platform System (APS) zu ermitteln, die Fehler, nachdem ein Clusterfailover aufgetreten ist und eine Cluster-Failover-Warnung ausgelöst wurde. Im Rahmen der Problembehandlung eines clusterfailovers durchgeführt werden müssen Sie den Namen des Knotens bestimmen, die nicht vor der Kontaktaufnahme mit Microsoft, um das Problem zu beheben.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4fd739e55725a3138a22539ef837088f86c8d8b9
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909500"
---
# <a name="determine-which-cluster-node-failed-for-analytics-platform-system"></a>Bestimmt, welcher Cluster Knoten konnte nicht für Analytics Platform System
Dieses Thema beschreibt, wie Sie den Namen des Knotens Analytics Platform System (APS) zu ermitteln, die Fehler, nachdem ein Clusterfailover aufgetreten ist und eine Cluster-Failover-Warnung ausgelöst wurde. Im Rahmen der Problembehandlung eines clusterfailovers durchgeführt werden müssen Sie den Namen des Knotens bestimmen, die nicht vor der Kontaktaufnahme mit Microsoft, um das Problem zu beheben.  
  
## <a name="Background"></a>Hintergrund  
Für hochverfügbarkeit in SQL Server PDW werden der steuerknoten und den Compute-Knoten als aktiv oder Passiv Komponenten der Windows-Failovercluster konfiguriert. Wenn ein aktiver Server nicht auf kritische Systeme-Anforderungen antwortet, wird der passive Server ein Failover und führt die Funktionen des Servers, der Fehler.  
  
Nach einem Clusterfailover beim Berichten von SQL Server PDW zum Knotenstatus, muss der passive Server ein über den Status. Allerdings ist es nicht offensichtlich Fehler bei der Server oder den Knoten, insbesondere dann, wenn der Server, die Fehler bei noch immer online ist. Um den Fehler zu beheben, müssen Sie den Namen des Knotens bestimmen, die ein Failover ausgeführt.  
  
## <a name="AdminConsoleSolution"></a>-Verwaltungskonsole-Lösung  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>Um den Namen des Knotens zu finden, die fehlgeschlagen  
  
1.  Öffnen Sie die Verwaltungskonsole. Weitere Informationen über die Verwaltungskonsole finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md). Nach dem Failover, das Failover im serverereignissatz enthalten ist die Anzahl der Warnungen auf der **INTEGRITÄT** Seite. Gibt es eine **INTEGRITÄT** Seite für die PDW-Region und für den Fabric-Bereich des Geräts. Jede Seite "Integrität" verfügt über eine **WARNUNGEN** Registerkarte. Weitere Informationen zu einer Warnung, klicken Sie auf der Seite "Integrität", Registerkarte "Warnungen", und klicken Sie dann auf eine Warnung aus.  
  
## <a name="SystemView"></a>Lösung der System-anzeigen  
Die folgende SQL-Anweisung zeigt, wie die [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md) Systemsicht, um den Namen des Servers zu finden, die nicht.  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
