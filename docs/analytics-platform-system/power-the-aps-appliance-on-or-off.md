---
title: Schalten Sie das Gerät ein- oder ausschalten - Analytics Platform System | Microsoft-Dokumentation
description: Schalten Sie das Gerät aktiviert oder deaktiviert für Analytics Platform System
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: a8be7ec364a257752576fa150434a67a92c28d9c
ms.sourcegitcommit: 731c5aed039607a8df34c63e780d23a8fac937e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909510"
---
# <a name="power-the-appliance-on-or-off-for-analytics-platform-system"></a>Schalten Sie das Gerät aktiviert oder deaktiviert für Analytics Platform System
In diesem Thema wird beschrieben, wie mit ein- und Ausschalten der Analytics-Plattform Systemappliance, Parallel Data Warehouse ausgeführt wird. Verwenden Sie in diesem Thema eine Analytics Platform System Appliance bewegt wird und wie auf einer Appliance nach einem schwerwiegenden Stromausfall.  
  
Verbessern der Leistung der Appliances / ist nicht identisch mit der Appliance-Dienste starten und beenden. Weitere Informationen zu diesem Thema finden Sie unter [PDW-Dienststatus &#40;Analytics Platform System&#41;](pdw-services-status.md). Informationen zum Verbessern der Leistung aktivieren oder Deaktivieren einer SQL Server 2008 Parallel Data Warehouse finden Sie die Datei mit SQL Server 2008 Parallel Data Warehouse. Informationen zum Verbessern der Leistung aktivieren oder Deaktivieren einer SQL Server 2012 AU1 oder AU2 Parallel Data Warehouse finden Sie die Hilfedatei für diesen Versionen.  
  
Wenn diese Anweisungen angeben, Herstellen einer Verbindung mit einem SQL Server-PDW-Knoten, kann die Verbindung lokal über angeschlossene Geräte (KVM) sein oder Remote mithilfe von Remotedesktop. Einige Aktionen muss physisch (Netzschalter aktivieren) und andere (z. B. Herunterfahren) kann physische oder mithilfe von Windows-Befehle.  
  
Verbindungen mit SQL Server-PDW-Knoten können vorgenommen werden, verwenden die IP-Adressen zugewiesen, und die Knoten, oder von der **HST01** Computer, indem Sie entweder die **Failovercluster-Manager** (**cluadmin.msc**) oder **Hyper-V-Manager** (**virtmgmt.msc**)-Anwendungen und der rechten Maustaste auf den Knotennamen.  
  
## <a name="PowerOff"></a>Schalten Sie das Gerät  
  
### <a name="before-you-begin"></a>Vorbereitungen  
Vor dem Ausschalten auf der Appliances, sollten Sie alle Aktivitäten auf dem Gerät beenden. Um alle Aktivitäten zu beenden:  
  
-   Verwenden der **Sitzungen** auf der Seite der Verwaltungskonsole, um die aktuellen Benutzer zu identifizieren. Kontakt mit aufnehmen Sie ihnen, und bitten Sie ihn, um sich abzumelden.  
  
-   Wenn notwendig können Sie die **KILL** Anweisung, um die Beendigung einer Client-Verbindung erzwingen. Seien Sie vorsichtig beim Beenden Verbindungen. Wenn einige transaktionalen Prozessen, z. B. eine lang ausgeführte Update unterbrochen muss zurücksetzungsaktivität vor SQL Server die Wiederherstellung der Datenbank abgeschlossen werden kann. Rollback einem teilweise abgeschlossenen aktualisieren oder löschen, kann zeitaufwendig sein.  
  
### <a name="to-power-off-the-appliance"></a>So schalten Sie das Gerät  
  
> [!WARNING]  
> Alle Schritte müssen ausgeführt werden, in der exakten Reihenfolge aufgeführt, und jeder Schritt muss abschließen, bevor der nächste Schritt ausgeführt wird, sofern nicht anders angegeben. Ausführen der Schritte außerhalb der Reihenfolge oder ohne zu warten, für die einzelnen Schritte zum Abschließen kann zu Fehlern führen, wenn das Gerät zu einem späteren Zeitpunkt eingeschaltet ist.  
  
1.  Verbinden mit dem Steuerungsknoten mit PDW (***PDW_region *-CTL01** ), und melden Sie sich mit dem Analytics Platform System Appliance-Domänenadministratorkonto.  
  
2.  Führen Sie `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` zum Öffnen der **Configuration Manager**.  
  
3.  In der Configuration Manager unter der **Parallel Data Warehouse-Topologie** Menü klicken Sie auf die **Dienststatus** Registerkarte, und klicken Sie auf **Region beenden** PDW-Dienste zu beenden.   
  
4.  Herstellen einer Verbindung mit ***Appliance_domain *-HST01** und melden Sie sich mit dem Domänenadministratorkonto für die Appliance.  
  
5.  Mithilfe der **Failovercluster-Manager** Herstellen einer Verbindung mit dem ***Appliance_domain *-WFOHST01** als Clusterressource konfigurieren, wenn nicht automatisch verbunden, und klicken Sie dann im Navigationsbereich auf **Rollen**. In der **Rollen** Bereich:  
  
    1.  Per Mehrfachauswahl ausgewählten alle virtuellen Computer. Mit der rechten Maustaste sie aus, und wählen **Herunterfahren**.  
  
    2.  Warten Sie, bis alle ausgewählten virtuellen Computer, um den Vorgang abzuschließen, wird heruntergefahren.  
  
6.  Schließen der **Failovercluster-Manager** Anwendung.  
  
7. Beenden Sie alle Server außer ***Appliance_domain *-HST01**.  
  
8. Beenden Sie die ***Appliance_domain *-HST01** Server.  
  
9. Beenden Sie die Stromverteilereinheiten (PDUs).  
  
## <a name="PowerOn"></a>Schalten Sie das Gerät  
  
### <a name="to-power-on-the-appliance"></a>So schalten Sie das Gerät  
  
> [!WARNING]  
> Alle Schritte müssen ausgeführt werden, in der exakten Reihenfolge aufgeführt, und jeder Schritt muss abschließen, bevor der nächste Schritt ausgeführt wird, sofern nicht anders angegeben. Schritten außerhalb der Reihenfolge oder ohne zu warten, für die einzelnen Schritte ausführen, kann dies zu Startfehlern führen.  
  
1.  Schalten Sie die Stromverteilereinheiten (PDUS), und warten Sie die Schalter für den automatischen start.  
  
2.  Einschalten der ***Appliance_domain *-HST01** Server.  
  
3.  Melden Sie sich bei ***Appliance_domain *-HST01** als Domänenadministrator Appliance.  
  
4.  Starten Sie den **Hyper-V-Manager** Programm (**virtmgmt.msc**) und Herstellen einer Verbindung mit ***Appliance_domain *-HST01** ist standardmäßig nicht verbunden.  
  
    1.  Wenn Sie anhand des Namens verbinden können, da die ***PDW_region *-AD01** wird nicht ausgeführt wird, versuchen Sie es mithilfe der IP-Adresse.  
  
    2.  In der **VMs** Bereich Suchen ***PDW_region *-AD01** und vergewissern Sie sich, dass er ausgeführt wird. Wenn dies nicht der Fall ist, starten Sie diesen virtuellen Computer aus, und warten Sie, bis er vollständig gestartet wird.  
  
5.  Schalten Sie die übrigen Server in der Appliance.  
  
6.  Während auf **HST01** aus als der Appliance-Domänenadministrator angemeldet **Hyper-V-Manager**:  
  
    1.  Herstellen einer Verbindung mit ***Appliance_domain *-HST02**.  
  
    2.  In der **VMs** Bereich Suchen ***PDW_region *-AD02** und vergewissern Sie sich, dass er ausgeführt wird.  Wenn dies nicht der Fall ist, starten Sie diesen virtuellen Computer aus, und warten Sie, bis er vollständig gestartet wird.  
  
7.  Mit der **Failovercluster-Manager** Herstellen einer Verbindung mit der ***Appliance_domain *-WFOHST01** Clustern, wenn nicht automatisch verbunden, und klicken Sie dann in der **Navigation** Bereich, klicken Sie auf **Rollen**. In der **Rollen** Bereich:  
  
    1.  Mehrfachauswahl aller virtuellen Maschinen, die mit der rechten Maustaste sie, und klicken Sie dann auf **starten**.  
  
    2.  Warten Sie, bis alle ausgewählten virtuellen Computer, um den Vorgang abzuschließen, starten vor dem Fortfahren mit dem nächsten Schritt.  
  
    3.  Bei Bedarf für die virtuellen Computer, die ein Failover ausgeführt werden soll, abschalten, verschieben und auf dem richtigen primären Host neu gestartet.  
  
8. Trennen von **HST01** Falls gewünscht.  
  
9. Herstellen einer Verbindung mit ***PDW_region *-CTL01** mithilfe der Appliance-Domänenadministratorkonto.  
  
10. Führen Sie `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` zum Starten der **Configuration Manager**.  
  
11. In der **Configuration Manager**in die **Parallel Data Warehouse-Topologie** Menü klicken Sie auf die **Dienststatus** Registerkarte, und klicken Sie auf **starten Region**PDW-Dienste zu starten.  
  
### <a name="to-verify-the-appliance-health"></a>So überprüfen die Appliance-Integrität  
Nachdem das Gerät gestartet wurde, öffnen Sie die **Verwaltungskonsole** und überprüfen Sie die Seite "Integrität" für Warnungen, die fehlerbedingung hinweisen. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
## <a name="see-also"></a>Siehe auch  
[Tasks zur applianceverwaltung &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
