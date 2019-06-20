---
title: Applianceüberwachung - Analytics Platform System | Microsoft-Dokumentation
description: Dieses monitoring Appliance-Handbuch beschreibt die Tools und Aufgaben für die Überwachung der Analytics Platform System Appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 100a587814e62a6455d25e78a3defca973f39bf6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63276138"
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Applianceüberwachung für Analytics Platform System
Dieses monitoring Appliance-Handbuch beschreibt die Tools und Aufgaben für die Überwachung der Analytics Platform System Appliance.  
  
## <a name="Basics"></a>Grundlagen der Überwachung und Tools  
Die Werte und die Informationen, die überwacht werden, kann auf der SQL Server-PDW-Appliance sind umfangreiche. Beispielsweise sind die folgenden Überwachungsaufgaben typische.  
  
-   Überprüfen Sie für jede Warnung, die von SQL Server PDW ausgestellt.  
  
-   Monitor für fehlerhafte Hardware.  
  
-   Monitor für Probleme bei der Netzwerkkonnektivität.  
  
-   Suchen Sie nach Fehlern, die an Benutzer zurückgegeben wird, während der abfrageverarbeitung.  
  
-   Zeigen Sie die Anzahl der aktuell aktiven Sitzungen und Abfragen.  
  
-   Überprüfen Sie den Status der lädt, Sicherungen und Wiederherstellungen.  
  
### <a name="appliance-monitoring-tools"></a>Appliance-Überwachungstools  
Es gibt mehrere Tools, die zum Überwachen der Appliance zur Verfügung.  
  
Verwaltungskonsole  
SQL Server PDW ist eine Verwaltungskonsole. Dies ist ein webbasiertes Tool, das Informationen zu Abfragen, lädt, Sicherung und Wiederherstellung, sperren, Sitzungen, Warnungen und Anwendungszustand in angezeigt. Die Verwaltungskonsole wird auf dem Gerät. Herstellen einer Verbindung auf die Verwaltungskonsole über Internet Explorer. Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![PDW-Verwaltungskonsole, Warnungen](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Systemsichten  
SQL Server PDW enthält umfassende Systemsichten, die Ihnen ermöglichen, die ausführliche Informationen über die Integrität der Appliance, Status und Leistung zu erhalten. Eine Liste von Systemsichten für Überwachungsaufgaben finden Sie unter:  
  
-   [Überwachen der Appliance mithilfe von Systemansichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operationsmanager (SCOM)  
SQL Server PDW verfügt über umfassende Integration in Systems Center Operations Manager. Die Management Packs für SQL Server PDW sind als kostenloser Download verfügbar. Weitere Informationen zur Verwendung von System Center zum Überwachen von SQL Server PDW finden Sie hier:  
  
-   [Überwachen der Appliance mithilfe von System Center Operationsmanager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Benutzerdefinierte Lösungen  
Für Situationen können Sie bei der System Center mit Ihrem Datencenter, die Tools für die Überwachung nicht verfügbar ist das Gerät überwachen, von einer Drittanbieter-überwachungslösung. Installation von Agents für externe Software wird in PDW derzeit nicht unterstützt, aber die meisten überwachungslösungen unterstützt Transact\-SQL-Integration, damit der Systemadministrator, direkte Transact implementieren kann\-SQL-Abfragen für Ihr PDW Appliance.  
  
Wenn Ihre Lösung für die keine direkte Transact unterstützt\-SQL-Abfragen, oder Sie verfügen nicht über die Überwachungstool, und dann können Sie Skripts zum Ausführen von Überwachungsaufgaben wie e-Mail senden, wenn eine Warnung auftritt.  TechNet-Wiki enthält ein Beispiel für skriptgesteuerte Überwachung Lösung.  
  
-   [Beispiel für SQLServer PDW Überwachung PowerShell](https://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Beziehen die Überwachungsaufgaben  
  
|Überwachungstask|Description|  
|-------------------|---------------|  
|Überwachen der Appliance mithilfe der Verwaltungskonsole.|[Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Überwachen der Appliance mithilfe von Systemsichten.|[Überwachen der Appliance mithilfe von Systemansichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Überwachen der Appliance mithilfe von System Center|[Überwachen der Appliance mithilfe von System Center Operationsmanager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Überwachen Sie den Status des Geräts.|[Integritätsstatus des Monitors Appliance &#40;Analytics Platform System&#41;](monitor-appliance-health-state.md)|  
|Taktüberwachung.|[Senden von Telemetriefeedback an Microsoft &#40;SQLServer PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Nachverfolgen von appliancewarnungen.|[Nachverfolgen von Appliancewarnungen &#40;Analytics Platform System&#41;](track-appliance-alerts.md)|  
|Bestimmen Sie, wie viel Kapazität verwendet wird.|[Anzeigen der Kapazitätsauslastung &#40;Analytics Platform System&#41;](view-capacity-utilization.md)|  
|Bestimmt, wie oft das Gerät abrufen.|[Bestimmen der Abrufhäufigkeit &#40;Analytics Platform System&#41;](determine-polling-frequency.md)|  
|Bestimmt, welcher Cluster tritt ein Fehler auf, der Knoten konnte.|[Bestimmen, welche Clusterknoten fehlerhaft &#40;Analytics Platform System&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Tasks zur applianceverwaltung &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
