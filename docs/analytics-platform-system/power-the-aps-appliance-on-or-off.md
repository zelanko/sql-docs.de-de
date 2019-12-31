---
title: Einschalten oder Deaktivieren der Appliance
description: Einschalten oder Deaktivieren der Appliance für das Analytics-Platt Form System
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ee70338b5a46ec60d808e489d982fd80692c5d1d
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400623"
---
# <a name="power-the-appliance-on-or-off-for-analytics-platform-system"></a>Einschalten oder Deaktivieren der Appliance für das Analytics-Platt Form System
In diesem Thema wird beschrieben, wie Sie Ihre Analytics Platform systemappliance einschalten oder ausschalten, die parallel Data Warehouse ausgeführt wird. Verwenden Sie dieses Thema, wenn eine Analyseplattform-System Gerät verschoben wird, oder wenn ein Gerät nach einem schwerwiegenden Stromausfall eingeschaltet werden soll.  
  
Das Einschalten und Deaktivieren der Appliance ist nicht mit dem Starten und Beenden der Geräte Dienste identisch. Weitere Informationen zu diesem Betreff finden Sie unter [PDW-Dienst Status &#40;Analytics Platform System&#41;](pdw-services-status.md). Informationen zum Einschalten oder Deaktivieren eines SQL Server 2008-parallelen Data Warehouse finden Sie in der Hilfedatei SQL Server 2008 parallel Data Warehouse. Informationen zum Einschalten oder Deaktivieren einer SQL Server 2012 AU1-oder AU2 parallel Data Warehouse finden Sie in der Hilfedatei für diese Versionen.  
  
Wenn diese Anweisungen das Herstellen einer Verbindung mit einem SQL Server PDW Knoten angeben, kann die Verbindung lokal mithilfe von angefügten Geräten (KVM) oder Remote mithilfe Remotedesktop erfolgen. Einige Aktionen müssen physisch sein (Einschalten eines Stromschalters), und einige (z. b. Herunterfahren) können physisch oder mithilfe von Windows-Befehlen erfolgen.  
  
Verbindungen mit SQL Server PDW Knoten können mithilfe der IP-Adressen hergestellt werden, die den Knoten zugewiesen sind, oder vom **HST01** -Computer mithilfe der Anwendungen **Failovercluster-Manager** (**Cluadmin. msc**) oder **Hyper-V-Manager** (**virtmgmt. msc**), und klicken Sie mit der rechten Maustaste auf den Knoten Namen.  
  
## <a name="PowerOff"></a>Ausschalten der Appliance  
  
### <a name="before-you-begin"></a>Voraussetzungen  
Bevor Sie das Gerät ausschalten, sollten Sie alle Aktivitäten auf dem Gerät beenden. So beenden Sie alle Aktivitäten:  
  
-   Verwenden Sie die Seite **Sitzungen** der Verwaltungskonsole, um die aktuellen Benutzer zu identifizieren. Kontaktieren Sie Sie, und bitten Sie Sie, sich abzumelden.  
  
-   Bei Bedarf können Sie die **Kill** -Anweisung verwenden, um die Beendigung einer Client Verbindung zu erzwingen. Gehen Sie beim Beenden von Verbindungen mit Bedacht vor. Bei einer unterbrochenen Transaktion müssen einige Transaktionsprozesse, z. b. ein Update mit langer Ausführungszeit, eine Aktivität zurücksetzen, bevor SQL Server die Wiederherstellung der Datenbank beenden können. Das Rollback eines teilweise abgeschlossenen Updates oder Löschvorgangs kann zeitaufwändig sein.  
  
### <a name="to-power-off-the-appliance"></a>So schalten Sie das Gerät aus  
  
> [!WARNING]  
> Alle Schritte müssen genau in der angegebenen Reihenfolge ausgeführt werden, und jeder Schritt muss vor der Ausführung des nächsten Schritts vollständig ausgeführt werden, sofern nicht anders angegeben. Das Ausführen von Schritten, die nicht in der richtigen Reihenfolge ausgeführt werden, oder das warten auf den Abschluss eines Schritts kann zu Fehlern führen, wenn die Appliance zu einem späteren Zeitpunkt eingeschaltet wird.  
  
1.  Stellen Sie eine Verbindung mit dem PDW-Steuerungs Knoten (**_PDW_region_-CTL01** ) her, und melden Sie sich mit dem Domänen Administrator Konto der Analytics Platform System Appliance  
  
2.  Führen `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` Sie aus, um die **Configuration Manager**zu öffnen.  
  
3.  Klicken Sie im Configuration Manager im Menü **parallele Data Warehouse Topologie** auf die Registerkarte **Dienst Status** , und klicken Sie dann auf **Region Abbrechen** , um die PDW-Dienste anzuhalten.   
  
4.  Stellen Sie eine Verbindung mit ** _appliance_domain_-HST01** her, und melden Sie sich mit dem Appliance Domain Administrator  
  
5.  Verwenden Sie die **Failovercluster-Manager** stellen Sie eine Verbindung mit dem Cluster ** _appliance_domain_-WFOHST01** her, falls diese nicht automatisch verbunden ist, und klicken Sie dann im Navigationsbereich auf **Rollen**. Im Bereich " **Rollen** ":  
  
    1.  Wählen Sie alle virtuellen Computer aus. Klicken Sie mit der rechten Maustaste darauf, und wählen Sie **herunter**fahren aus.  
  
    2.  Warten Sie, bis alle ausgewählten VMS heruntergefahren sind.  
  
6.  Schließen Sie die **Failovercluster-Manager** Anwendung.  
  
7. Fahren Sie alle Server außer ** _appliance_domain_-HST01**herunter.  
  
8. Fahren Sie den ** _appliance_domain_-HST01-** Server herunter.  
  
9. Fahren Sie die Stromverteiler Einheiten (PDUs) herunter.  
  
## <a name="PowerOn"></a>Einschalten des Geräts  
  
### <a name="to-power-on-the-appliance"></a>So schalten Sie das Gerät ein  
  
> [!WARNING]  
> Alle Schritte müssen genau in der angegebenen Reihenfolge ausgeführt werden, und jeder Schritt muss vor der Ausführung des nächsten Schritts vollständig ausgeführt werden, sofern nicht anders angegeben. Das Ausführen von Schritten außerhalb der Reihenfolge oder das warten auf den Abschluss der einzelnen Schritte kann zu Start Fehlern führen.  
  
1.  Schalten Sie die Stromverteiler Einheiten (PDU) ein, und warten Sie, bis die Switches automatisch gestartet werden.  
  
2.  Schalten Sie den ** _appliance_domain_-HST01-** Server ein.  
  
3.  Melden Sie sich bei ** _appliance_domain_-HST01** als Anwendungs Domänen Administrator an.  
  
4.  Starten Sie das **Hyper-V-Manager** -Programm (**virtmgmt. msc**), und stellen Sie eine Verbindung mit ** _appliance_domain_-HST01** , sofern nicht standardmäßig verbunden.  
  
    1.  Wenn Sie keine Verbindung über den Namen herstellen können, weil die ** _PDW_region_-ad01** nicht ausgeführt wird, versuchen Sie, eine Verbindung mit der IP-Adresse herzustellen.  
  
    2.  Suchen Sie im **Virtual Machines** Bereich nach ** _PDW_region_-ad01** , und vergewissern Sie sich, dass er ausgeführt wird. Wenn dies nicht der Fall ist, starten Sie diese VM, und warten Sie, bis Sie vollständig gestartet ist  
  
5.  Schalten Sie den Rest der Server in der Appliance ein.  
  
6.  Während **HST01** als Anwendungs Domänen Administrator angemeldet ist, über **Hyper-V-Manager**:  
  
    1.  Stellen Sie eine Verbindung mit ** _appliance_domain_-HST02**her.  
  
    2.  Suchen Sie im **Virtual Machines** Bereich nach ** _PDW_region_-ad02** , und vergewissern Sie sich, dass er ausgeführt wird.  Wenn dies nicht der Fall ist, starten Sie diese VM, und warten Sie, bis Sie vollständig gestartet ist  
  
7.  Verwenden Sie die **Failovercluster-Manager** stellen Sie eine Verbindung mit dem Cluster ** _appliance_domain_-WFOHST01** her, falls diese nicht automatisch verbunden ist, und klicken Sie dann im **Navigations** Bereich auf **Rollen**. Im Bereich " **Rollen** ":  
  
    1.  Wählen Sie alle virtuellen Computer aus, klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **starten**.  
  
    2.  Warten Sie, bis alle ausgewählten VMS gestartet wurden, bevor Sie mit dem nächsten Schritt fortfahren.  
  
    3.  Wenn dies für die virtuellen Computer erforderlich ist, für die ein Failover ausgeführt wurde, fahren Sie Sie herunter, verschieben Sie Sie, und starten Sie Sie auf dem richtigen primären  
  
8. Trennen Sie die Verbindung mit **HST01** , wenn Sie möchten.  
  
9. Stellen Sie eine Verbindung mit ** _PDW_region_-CTL01** unter Verwendung des Anwendungs Domänen Administrator Kontos her.  
  
10. Führen `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` Sie aus, um die **Configuration Manager**zu starten.  
  
11. Klicken Sie im **Configuration Manager**im Menü **parallele Data Warehouse Topologie** auf die Registerkarte **Dienst Status** , und klicken Sie dann auf **Region starten** , um die PDW-Dienste zu starten.  
  
### <a name="to-verify-the-appliance-health"></a>So überprüfen Sie die Geräte Integrität  
Nachdem das Gerät gestartet wurde, öffnen Sie die **Verwaltungskonsole** , und überprüfen Sie die Seite Integrität auf Warnungen, die möglicherweise auf Fehlerbedingungen hindeuten. Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Geräte Verwaltungsaufgaben &#40;Analytics-Platt Form System&#41;](appliance-management-tasks.md)  
  
