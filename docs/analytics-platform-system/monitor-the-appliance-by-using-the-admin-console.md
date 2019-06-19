---
title: Monitor mit Admin Console - Analytics Platform System | Microsoft-Dokumentation
description: Für Analytics Platform System ist die Verwaltungskonsole für eine Anwendung, die die Appliance Zustand, Integrität und Leistung Informationen angezeigt. Herstellen einer Verbindung auf die Verwaltungskonsole über einen Internetbrowser.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d094f809052222238806e679e38c6578422fd9aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63027543"
---
# <a name="monitor-the-appliance-with-the-admin-console---analytics-platform-system"></a>Überwachen der Appliance mit der Admin Console - Analytics Platform System
Die Verwaltungskonsole ist eine SQL Server-PDW-Webanwendung, die die Appliance Zustand, Integrität und Leistung Informationen angezeigt. Herstellen einer Verbindung auf die Verwaltungskonsole über Internet Explorer.  
  
## <a name="About"></a>Informationen zur Verwaltungskonsole  
![Appliance Console Home](./media/monitor-the-appliance-by-using-the-admin-console/SQL_Server_PDW_AdminConsol_ApplHome.png "SQL_Server_PDW_AdminConsol_ApplHome")  
  
**Appliance**  
Home  
Bietet eine kurze Übersicht über den Anwendungszustand.  
  
Integrität  
Zeigt die appliancetopologie mit Indikatoren zeigt die Integrität der einzelnen überwachten Komponenten innerhalb eines jeden Knotens. Können Sie den aktuellen Status der einzelnen Knoten und die Eigenschaften der Komponenten des Knotens anzuzeigen.  
  
Zeigt Warnungen an Hardware und Software.  
  
Systemmonitor  
Zeigt Leistungsdiagramme für die Überwachung an.  
  
**Parallel Data Warehouse**  
Home  
Bietet eine kurze Übersicht über die PDW-Zustand.  
  
Sitzungen  
Zeigt aktive Sitzungen von PDW-Benutzer. Dies kann helfen, für die Überwachung der Ressourcenkonflikte.  
  
Abfragen  
Zeigt eine Liste der ausgeführten Abfragen und kürzlich abgeschlossenen Abfragen. Verwandte Fehler werden angezeigt, sofern vorhanden. Außerdem bietet die Möglichkeit zum Anzeigen von Details der Ausführungsinformationen für die Abfrage Ausführung planen und Knoten aus.  
  
Loads  
Zeigt geladen werden Plänen, die den aktuellen Zustand der PDW-Ladevorgänge sowie verknüpfte Fehler, falls vorhanden.  
  
Sicherung und Wiederherstellung  
Zeigt ein Protokoll mit PDW sicherungs- und Wiederherstellungsvorgänge.  
  
Integrität  
Zeigt die PDW-Topologie mit Indikatoren zeigt die Integrität der einzelnen überwachten Komponenten innerhalb eines jeden Knotens. Können Sie den aktuellen Status der einzelnen Knoten und die Eigenschaften der Komponenten des Knotens anzuzeigen.  
  
Zeigt Warnungen an Hardware und Software.  
  
Ressourcen  
Zeigt eine Liste von PDW-Ressourcensperren sowie deren aktuellen Status.  
  
Speicherung  
Fasst zusammen, die PDW-speichernutzung.  
  
Systemmonitor  
Zeigt die PDW-Monitor Leistungsdiagramme an.  
 
> [!NOTE]  
> Die Verwaltungskonsole verfügt über eine Auflösung von 1024 x 768 Bildschirm. Die Administratorkonsole zeigt die am besten mit einer Bildschirmauflösung von 1280 X 1024 oder höher.  
  
## <a name="Connect"></a>Verbinden Sie mit der Verwaltungskonsole  
Verbindung mit der Admin-Konsole erfordert:  
  
-   Mindestens Internet Explorer Version 10.  
  
-   Berechtigungen für die Verwaltungskonsole zugreifen. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Die IP-Adresse der Steuerelement-Knoten-Cluster.  Rufen Sie diese von Ihrem SQL Server-PDW-Administrator.  
  
Verwenden Sie zum Verbinden mit der Verwaltungskonsole Internet Explorer und Https, um die IP-Adresse der Steuerelement-Knoten-Cluster zu suchen. Wenn die IP-Adresse des Clusters Knoten Steuerelement beispielsweise `10.192.63.102`, geben Sie `https://10.192.63.102` in die Adressleiste Ihres Browsers. Der erste Bildschirm fordert Ihre **Anmeldung** und **Kennwort**. Geben Sie entweder eine SQL Server-authentifizierungsanmeldung und ein Kennwort oder eine Anmeldung mit Windows-Authentifizierung und Windows-Kennwort ein. Wenn Sie eine Anmeldung mit Windows-Authentifizierung zu verwenden, wird die Verwaltungskonsole Identitätswechsel verwendet werden.  
  
## <a name="RelatedTasks"></a>Admin-Konsolentasks  
Die Verwaltungskonsole bietet die Möglichkeit, folgende Aspekte überwachen:  
  
|||  
|-|-|  
|**Informationstyp**|**Wie Sie in der Verwaltungskonsole zuzugreifen.**|  
|Gesamtstatus des Geräts|Klicken Sie auf **Anwendungszustand** in der oberen Menüleiste oder **Startseite**.|  
|Benachrichtigungen|Klicken Sie auf **Warnungen**. Weitere Informationen finden Sie unter [Grundlegendes zu Admin-Konsole Warnungen &#40;Analytics Platform System&#41;](understanding-admin-console-alerts.md).|  
|Appliance-Komponenten und deren status|Klicken Sie auf **Anwendungszustand** in der oberen Menüleiste oder **Startseite**.|  
|Monitor-Anforderungen (einschließlich Abfragen, lädt, Sicherungen und Wiederherstellungen)|Klicken Sie auf **Sitzungen** derzeit aktive oder aktuelle Sitzungen angezeigt.<br /><br />Klicken Sie auf **Abfragen** derzeit aktive oder aktuelle Abfragen angezeigt. Für Abfragen angezeigte Informationen enthält, lädt, Sicherungen und Wiederherstellungen.<br /><br />Klicken Sie auf **Sperren** zu aktiven Sperren finden Sie unter.|  
|Überwachen Sie zusätzliche Informationen für Lasten, Sicherungen und Wiederherstellungen.|Klicken Sie auf **lädt** oder **Sicherung und Wiederherstellung**.|  
|Leistungsinformationen|Klicken Sie auf **Systemmonitor**.|  
  
## <a name="see-also"></a>Siehe auch  
[Applianceüberwachung &#40;Analytics Platform System&#41;](appliance-monitoring.md)  
  
