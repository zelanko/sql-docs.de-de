---
title: Applianceüberwachung
description: In diesem Handbuch zur Geräteüberwachung werden die Tools und Aufgaben zum Überwachen der Analytics Platform System Appliance beschrieben.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: cec604ff1a93213fc6308455cadda90e6efa2d61
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401425"
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Geräteüberwachung für Analytics Platform System
In diesem Handbuch zur Geräteüberwachung werden die Tools und Aufgaben zum Überwachen der Analytics Platform System Appliance beschrieben.  
  
## <a name="Basics"></a>Überwachen von Grundlagen und Tools  
Die Werte und Informationen, die auf der SQL Server PDW Appliance überwacht werden können, sind umfangreich. Im folgenden finden Sie beispielsweise typische Überwachungs Tasks.  
  
-   Überprüfen Sie, ob eine Warnung von SQL Server PDW ausgegeben wurde.  
  
-   Überwachen Sie Hardwarefehler.  
  
-   Überwachen Sie Probleme mit der Netzwerk Konnektivität.  
  
-   Überprüfen Sie, ob während der Abfrage Verarbeitung Fehler an Benutzer zurückgegeben wurden  
  
-   Zeigt die Anzahl der derzeit aktiven Sitzungen und Abfragen an.  
  
-   Überprüfen Sie den Status von Ladungen, Sicherungen und Wiederherstellungen.  
  
### <a name="appliance-monitoring-tools"></a>Tools zur Geräteüberwachung  
Zum Überwachen der Appliance sind mehrere Tools verfügbar.  
  
Verwaltungskonsole  
SQL Server PDW verfügt über eine Verwaltungskonsole. Hierbei handelt es sich um ein webbasiertes Tool, das Informationen zu Abfragen, Ladungen, Sicherungen und Wiederherstellungen, sperren, Sitzungen, Warnungen und Gerätestatus anzeigt. Die Verwaltungskonsole wird auf dem Gerät ausgeführt. Benutzer stellen über Internet Explorer eine Verbindung mit der Verwaltungskonsole her. Weitere Informationen finden Sie unter:  
  
-   [Überwachen Sie die Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![PDW-Verwaltungskonsole, Warnungen](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
Systemsichten  
SQL Server PDW umfasst umfassende System Sichten, mit denen Sie detaillierte Informationen zur Integrität, zum Zustand und zur Leistung des Geräts abrufen können. Eine Liste der System Sichten für die Überwachung von Tasks finden Sie unter:  
  
-   [Überwachen der Appliance mithilfe von System Sichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW verfügt über eine umfassende Integration in System Center Operations Manager. Die Management Packs für SQL Server PDW stehen als kostenloser Download zur Verfügung. Weitere Informationen zur Verwendung von System Center zum Überwachen von SQL Server PDW finden Sie in den folgenden Bereichen:  
  
-   [Überwachen Sie die Appliance mithilfe System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
Benutzerdefinierte Lösungen  
In Situationen, in denen System Center in ihren Rechenzentrums Überwachungstools nicht verfügbar ist, können Sie die Appliance mithilfe einer Überwachungslösung eines Drittanbieters überwachen. Die Installation externer Software-Agents wird derzeit in PDW nicht unterstützt, aber die meisten Überwachungslösungen\-unterstützen die Transact-SQL-Integration, sodass der\-Systemadministrator direkte Transact-SQL-Abfragen für Ihre PDW-Appliance implementieren kann.  
  
Wenn Ihre Überwachungslösung keine direkten Transact\--SQL-Abfragen unterstützt, oder Sie über kein Überwachungs Tool verfügen, können Sie mithilfe von Skripts Überwachungsaufgaben ausführen, z. b. das Senden von e-Mails, wenn eine Warnung auftritt.  Das TechNet-wiki enthält ein Beispiel für eine Lösung zur Überwachung der Skripterstellung.  
  
-   [Beispiel für die PowerShell-Überwachung für SQL Server PDW](https://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>Verwandte Überwachungsaufgaben  
  
|Überwachungs Task|Beschreibung|  
|-------------------|---------------|  
|Überwachen Sie die Appliance mithilfe der Verwaltungskonsole.|[Überwachen Sie die Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|Überwachen Sie die Appliance mithilfe von System Sichten.|[Überwachen der Appliance mithilfe von System Sichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|Überwachen der Appliance mithilfe von System Center|[Überwachen Sie die Appliance mithilfe System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|Überwachen Sie den Status des Geräts.|[Monitor für den Geräte Integritäts Status &#40;Analytics-Platt Form System&#41;](monitor-appliance-health-state.md)|  
|Takt Überwachung.|[Senden Sie telemetriefeedback an Microsoft &#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|Geräte Warnungen nachverfolgen.|[Geräte Warnungen &#40;Analytics-Platt Form System&#41;nachverfolgen](track-appliance-alerts.md)|  
|Bestimmen Sie, wie viel Kapazität verwendet wird.|[Anzeigen der Kapazitätsauslastung &#40;Analytics Platform System&#41;](view-capacity-utilization.md)|  
|Bestimmen Sie, wie oft das Gerät abgefragt werden soll.|[Ermitteln der Abruf Häufigkeit &#40;Analytics Platform System&#41;](determine-polling-frequency.md)|  
|Wenn ein Cluster Fehler auftritt, ermitteln Sie, welcher Cluster Knoten ausgefallen ist.|[Ermitteln, welcher Cluster Knoten Fehler &#40;Analytics-Platt Form System&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[Geräte Verwaltungsaufgaben &#40;Analytics-Platt Form System&#41;](appliance-management-tasks.md)  
  
