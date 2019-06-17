---
title: Physische Komponenten der Appliance - Analytics Platform System | Microsoft-Dokumentation
description: Namen und Beschreibungen für die PDW und, physischen Fabric-Komponenten.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0adbd92d1a29a98a80de65268c53ea63e3941d07
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639912"
---
# <a name="appliance-physical-components---analytics-platform-system"></a>Physische Komponenten der Appliance - Analytics Platform System
Namen und Beschreibungen für die PDW und, physischen Fabric-Komponenten. 
  
<!-- MISSING LINKS See also [HDInsight Physical Components &#40;Analytics Platform System&#41;](hdinsight-physical-components.md).  -->  
  
## <a name="diagrams"></a>Komponentendiagramme  
Dies zeigt die Namen der physischen Komponenten und, in denen sie in das erste Rack von einem 6-Compute-Knoten-Gerät befinden.  
  
![Komponentennamen für PDW-Region – HP](./media/pdw-and-appliance-fabric-physical-components/APS_HW_ComponentNames-HP.png "APS_HW_ComponentNames-HP")  
  
Der tatsächliche Name für die Komponenten von PDW heißt PDW-Region, gefolgt von einem Bindestrich gefolgt von den Namen der Komponente. Beispielsweise ist der Name der PDW-Region PDW123, sind die tatsächlichen Namen **PDW123-CTL01**, **PDW123 CMP01**usw.  
  
Auf ähnliche Weise ist der tatsächliche Name für die Appliance Fabric-Komponenten der Domäne der Anwendung, gefolgt von einem Bindestrich gefolgt von den Namen der Komponente. Beispielsweise ist die Domäne der Anwendung FSW123, das Fabric Appliance VMs sind **FSW123-WDS**, **FSW123-AD01**, **FSW123 VMM**usw.  
  
Hier ist eine konsolidierte Ansicht von einer PDW-Region mit 6 Compute-Knoten.  
  
![PDW-Komponentennamen](./media/pdw-and-appliance-fabric-physical-components/APS_HW_Names.png "APS_HW_Names")  
  
## <a name="pdw"></a>PDW-Komponenten  
Die PDW-VMs sind Teil der PDW-Region.  
  
*PDW_region*-CTL01  
Ein virtueller Computer, der den Steuerelementknoten aus ausgeführt wird. Dies wird auf HST01 ausgeführt und kann ein Failover zu HST02.  
  
> [!WARNING]  
> SQL Server PDW unterstützt die Erstellung einer Momentaufnahme des virtuellen Computers CTL01 nicht mit dem Hyper-V-Manager. Momentaufnahmen basieren auf den lokalen Speicher, der zu Fehlern führen wird, wenn der virtuelle Computer für das Failover der Sicherung versucht. Erstellen einer Momentaufnahme kann auch Behebung von Zuverlässigkeitsproblemen mit den anderen virtuellen Computern zu, dass das Failover zum passiven Server führen.  
  
*PDW_region*-CMP01 über *PDW_Region*-CMP06  
Ein virtueller Computer, der den Compute-Knoten ausgeführt wird. In diesem Diagramm 6-Compute-Knoten Computeknoten Hosts HSA01 über HSA06 ausführen VMs CMP01 über CMP06 bzw.  
  
## <a name="fabric"></a>Appliance-Fabric-Komponenten  
Diese Komponenten sind Bestandteil des Fabrics Appliance.  
  
### <a name="virtual-machines"></a>Virtuelle Computer  
*appliance_domain*-WDS  
Dieses Hosts für virtuelle Maschinen Windows Deployment Services (WDS), Analytics Platform System verwendet werden Windows-Betriebssysteme über das Anwendungsnetzwerk bereitstellen. Er hostet außerdem den DHCP-Dienst, wodurch die Appliance-Hosts im Netzwerk Appliance zu verknüpfen, ohne eine vorkonfiguriert, dass IP-Adresse.  
  
Die *Appliance_domain*- WDS-VM auf HST01 ausgeführt wird, und kann ein Failover zu HST02. Die VM "WDS" und "der VMM-VM Bereitstellen von Windows auf den physischen Hosts während der Installation der Anwendung. Führen Sie während des Lebenszyklus Appliance WDS und VMM Vorgänge wie das Ersetzen eines Hosts.  
  
*appliance_domain*-VMM  
Mit dem Virtual Machine Manager (VMM) auf einem virtuellen Computer ausgeführt wird, und es kann ein Failover zu HST02. VMM hostet System Center, um das Betriebssystem auf den physischen Hosts bereitzustellen. VMM bietet auch Windows Server Update Services (WSUS), um anzuwenden, oder Entfernen von Windows-Updates auf allen Hosts und virtuellen Computern.  
  
*appliance_domain*-AD01, *appliance_domain*-AD02  
Active Directory-Domänendienste, die das Domain Name System (DNS) enthält, wird auf einem virtuellen Computer auf HST01 und HST02 ausgeführt. Für hohe Verfügbarkeit des Geräts AD01 und AD02 sind replizierten Domänencontroller und dazu, dass kein Failover aus. Wenn ein fehlschlägt, ist der andere Controller bereits durch die richtigen Daten verfügbar.  
  
*appliance_domain*-ISCSI01  
Ein iSCSI-virtueller Computer wird auf jedem Host mit dem Speicher verbunden ist (HSA01-HSA06) ausgeführt. Dieser virtuelle Computer führt kein Failover.  
  
### <a name="hosts"></a>Hosts  
*Appliance_domain*-HST01 über *Appliance_domain*-HST06  
Die Hosts für die PDW-Knoten und Appliance Fabric von virtuellen Maschinen. HST03 handelt es sich um eine optionale passiven-Host.  
  
*appliance_domain*-HSA01 through *appliance_domain*-HSA08  
Die Hosts mit Speicher verbunden ist (HSA). Jeder HAS Host führt eine Compute-Knoten virtuelle Computer und eine ISCSI-VM.  
  
### <a name="cluster-for-pdw"></a>Cluster für PDW  
*appliance_domain*-WFOHST01  
Der PDW-Cluster wird WFOHST01 benannt. Er verwaltet alle physischen Hosts und virtuellen Computern, die PDW angehören.  
  
### <a name="direct-attached-storage"></a>Direkt angeschlossener Speicher  
*appliance_domain*-DAS01 through *appliance_domain*-DAS03  
Dies ist das direkt angeschlossenen Speicher, der auf den Computeknoten verbunden ist. HP hat eine DAS für jede zwei Computeknoten. Dell und Quanten haben eine DAS für alle drei Compute-Knoten.  
  
## <a name="see-also"></a>Siehe auch  
<!-- MISSING LINKS [Hardware Configurations &#40;Analytics Platform System&#41;](../architecture/hardware-configurations.md)  -->  
[Konfiguration von Sicherheitsgeräten &#40;Analytics Platform System&#41;](appliance-configuration.md)  
[Tasks zur applianceverwaltung &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
