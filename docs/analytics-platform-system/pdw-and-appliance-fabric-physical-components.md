---
title: Physische Komponenten von Appliance
description: Namen und Beschreibungen der physischen Komponenten des PDW-und Appliance Fabric.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 5cbed66f53189668518e04848002ae69adb8c614
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400923"
---
# <a name="appliance-physical-components---analytics-platform-system"></a>Physische Appliance von Appliance-Analytics Platform System
Namen und Beschreibungen der physischen Komponenten des PDW-und Appliance Fabric. 
  
<!-- MISSING LINKS See also [HDInsight Physical Components &#40;Analytics Platform System&#41;](hdinsight-physical-components.md).  -->  
  
## <a name="diagrams"></a>Komponenten Diagramme  
Dies zeigt die Namen der physischen Komponenten an, wo Sie sich im ersten Gestell einer 6-Compute-Knoten Appliance befinden.  
  
![Komponentennamen für die PDW-Region – HP](./media/pdw-and-appliance-fabric-physical-components/APS_HW_ComponentNames-HP.png "APS_HW_ComponentNames-HP")  
  
Der tatsächliche Name für PDW-Komponenten ist der Name der PDW-Region, gefolgt von einem Bindestrich und dem Komponentennamen. Wenn der Name des PDW-Regions beispielsweise PDW123 lautet, sind die tatsächlichen Namen **PDW123-CTL01**, **PDW123-CMP01**usw.  
  
Entsprechend ist der tatsächliche Name für Appliance Fabric Components die Appliance-Domäne, gefolgt von einem Bindestrich und dem Komponentennamen. Wenn die Anwendungsdomäne z. b. FSW123 lautet, sind die Appliance Fabric-VMS **FSW123-WDS**, **FSW123-ad01**, **FSW123-VMM**usw.  
  
Im folgenden finden Sie eine konsolidierte Ansicht eines PDW-Bereichs mit sechs Computeknoten.  
  
![PDW-Komponentennamen](./media/pdw-and-appliance-fabric-physical-components/APS_HW_Names.png "APS_HW_Names")  
  
## <a name="pdw"></a>PDW-Komponenten  
Die virtuellen Computer in PDW sind Teil der PDW-Region.  
  
*PDW_region*-CTL01  
Ein virtueller Computer, der den Steuer Knoten ausführt. Dies wird auf HST01 ausgeführt und kann ein Failover auf HST02 ausführen.  
  
> [!WARNING]  
> Die Erstellung einer Momentaufnahme des virtuellen Computers CTL01 mit dem Hyper-V-Manager wird von SQL Server PDW nicht unterstützt. Momentaufnahmen basieren auf lokalem Speicher, was zu Fehlern führt, wenn die virtuelle Maschine versucht, ein Failover auf die Sicherung durchführen. Das Erstellen einer Momentaufnahme kann auch zu Zuverlässigkeits Problemen mit dem anderen virtuellen Computer führen, bei dem ein Failover auf den passiven Server ausgeführt wird.  
  
*PDW_region*-CMP01 bis *PDW_Region*-CMP06  
Ein virtueller Computer, auf dem der Computeknoten ausgeführt wird. In diesem Knoten Diagramm mit 6 Computeknoten führen die Hosts HSA01 bis HSA06 virtuelle Computer mit Computeknoten CMP01 bis CMP06 aus.  
  
## <a name="fabric"></a>Appliance Fabric-Komponenten  
Diese Komponenten sind Bestandteil des Appliance-Fabrics.  
  
### <a name="virtual-machines"></a>Virtual Machines  
*appliance_domain*-WDS  
Dieser virtuelle Computer hostet die Windows-Bereitstellungs Dienste (Windows Deployment Services, WDS), von denen Analytics Platform System Windows-Betriebssysteme über das Geräte Netzwerk bereitstellt Außerdem hostet Sie den DHCP-Dienst, der es den Geräte Hosts ermöglicht, dem Geräte Netzwerk beizutreten, ohne eine vorkonfigurierte IP-Adresse zu haben.  
  
Der virtuelle *appliance_domain*-WDS-Computer wird auf HST01 ausgeführt und kann ein Failover auf HST02 ausführen. Der virtuelle WDS-Computer und der virtuelle VMM-Computer stellen Windows auf den physischen Hosts bereit, während das Gerät installiert wird. Während des Lebenszyklus der Appliance werden von WDS und VMM Vorgänge wie das Ersetzen eines Hosts durchgeführt.  
  
*appliance_domain*VMM  
Die Virtual Machine Manager (VMM) wird auf einem virtuellen Computer ausgeführt und kann ein Failover auf HST02 ausführen. VMM hostet System Center, um das Betriebs System auf den physischen Hosts bereitzustellen. VMM stellt außerdem Windows Server Update Services (WSUS) zum Anwenden oder Entfernen von Windows-Updates auf allen Hosts und virtuellen Maschinen bereit.  
  
*appliance_domain*-ad01, *appliance_domain*-ad02  
Active Directory Domain Services, das die Domain Name System (DNS) enthält, wird auf einem virtuellen Computer sowohl auf HST01 als auch auf HST02 ausgeführt. Für eine hohe Verfügbarkeit der Appliance sind ad01 und ad02 replizierte Domänen Controller und kein Failover. Wenn ein Fehler auftritt, ist der andere bereits mit den richtigen Daten verfügbar.  
  
*appliance_domain*-ISCSI01  
Ein virtueller iSCSI-Computer wird auf jedem der Hosts mit angefügtem Speicher (HSA01-HSA06) ausgeführt. Diese VM führt kein Failover durch.  
  
### <a name="hosts"></a>Host  
*appliance_domain*-HST01 bis *appliance_domain*-HST06  
Die Hosts für den PDW-Steuerungs Knoten und die Appliance Fabric Virtual Machines. HST03 ist ein optionaler passiver Host.  
  
*appliance_domain*-HSA01 bis *appliance_domain*-HSA08  
Die Hosts mit angefügtem Speicher (HSA). Jeder Host verfügt über einen virtuellen Computer mit einem Computeknoten und eine iSCSI-VM.  
  
### <a name="cluster-for-pdw"></a>Cluster für PDW  
*appliance_domain*-WFOHST01  
Der PDW-Cluster hat den Namen "WFOHST01". Alle physischen Hosts und virtuellen Computer, die zu PDW gehören, werden verwaltet.  
  
### <a name="direct-attached-storage"></a>Direkt angeschlossener Speicher  
*appliance_domain*-DAS01 bis *appliance_domain*-DAS03  
Dabei handelt es sich um den direkt angeschlossenen Speicher, der mit den Computeknoten verbunden ist. HP verfügt über ein das für jeden der beiden Computeknoten. Dell und QUANTA verfügen über ein das für jeden drei Computeknoten.  
  
## <a name="see-also"></a>Weitere Informationen  
<!-- MISSING LINKS [Hardware Configurations &#40;Analytics Platform System&#41;](../architecture/hardware-configurations.md)  -->  
[Gerätekonfiguration &#40;Analytics-Platt Form System&#41;](appliance-configuration.md)  
[Geräte Verwaltungsaufgaben &#40;Analytics-Platt Form System&#41;](appliance-management-tasks.md)  
  
