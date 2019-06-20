---
title: Hohe Verfügbarkeit in Analytics Platform System | Microsoft-Dokumentation
description: Erfahren Sie, wie Analytics Platform System (APS) für hochverfügbarkeit entworfen wird.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5c8a562ab105e1bc40b590916d0881757036aeff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63280358"
---
# <a name="analytics-platform-system-high-availability"></a>Hohe Verfügbarkeit für Analytics Platform System
Erfahren Sie, wie Analytics Platform System (APS) für hochverfügbarkeit entworfen wird.  
  
## <a name="high-availability-architecture"></a>Hochverfügbarkeitsarchitektur  
![Appliancearchitektur](media/appliance-architecture.png "Anwendungsarchitektur")  
  
## <a name="network"></a>Netzwerk  
Für die Verfügbarkeit des Netzwerks hat die APS-Appliance zwei InfiniBand-Netzwerken. Wenn die InfiniBand-Netzwerke ausfällt, ist der andere Controller weiterhin verfügbar. Darüber hinaus wurde Active Directory-Domänencontrollern, um eingehende Anforderungen mit dem richtigen InfiniBand-Netzwerk zu beheben repliziert.  
  
Weitere Informationen finden Sie unter [konfigurieren InfiniBand-Netzwerkadapter](configure-infiniband-network-adapters.md).  
  
## <a name="storage"></a>Speicherung  
Um Daten zu schützen, verwendet die APS RAID 1-Spiegelung, um zwei Kopien der Daten für alle Benutzer zu verwalten. Wenn ein Datenträger ausfällt, wird das Hardwaresystem die Daten auf ein Hotspare-Laufwerk erstellt und legt eine Warnung, dass ein Fehler auf dem Datenträger vorhanden ist.  
  
Um die verfügbaren Daten online zu halten, verwendet APS Windows-Speicherplätze "und" freigegebene Clustervolumes, um die Benutzer-Datenträger in den direkt angeschlossenen Speicher zu verwalten. Es gibt einen einzigen Speicherpool pro Daten Skalierungseinheit unterteilt Cluster Shared Volumes, die auf die Compute-Knoten-Hosts durch einbindungspunkte verfügbar sind.  
  
Um sicherzustellen, dass der Speicherpool online bleibt, hat jedem Host in der Data-Skalierungseinheit einen iSCSI-virtuellen Computer, der kein Failover durchgeführt wird. Diese Architektur ist wichtig, da ein Host ausfällt, die Daten weiterhin über den anderen Hosts in der Data-Skalierungseinheit verfügbar sind.  
  
## <a name="hosts"></a>Hosts  
Für die hostverfügbarkeit werden auf allen Hosts in einem Windows-Failovercluster konfiguriert. Jedes Rack verfügt über einen passiven Host. Das erste Rack, das SQL Server Parallel Data Warehouse (PDW) und der Appliance-Fabric gesteuert werden soll, kann optional einen zweiten passiven Host verfügen. Wenn ein Host ausfällt, virtuelle Computer, die für Failover konfiguriert sind wird ein Failover auf einen verfügbaren passiven Host.  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>PDW-Knoten und Appliance-fabric  
APS wird für hohe Verfügbarkeit der PDW-Knoten und der Appliance-Fabric Netzwerkvirtualisierung verwendet. Jede der PDW und Fabric-Komponenten, die auf einem virtuellen Computer ausführen.  
  
Jeder virtuelle Computer wird als eine Rolle in der Windows-Failovercluster definiert. Bei ein virtuellen Computer ein Fehler auftritt, startet Sie Cluster auf einem verfügbaren passiven-Host neu. Die virtuellen Computer werden mithilfe von System Center Virtual Machine Manager bereitgestellt. Wenn ein Failover auftritt, kann der virtuelle Computer auf dem passiven Host mit weiterhin Zugriff auf die Benutzerdaten über das InfiniBand-Netzwerk.  
  
Der steuerknoten und den Compute-Knoten virtuelle Computer werden jeweils als einen einzelnen Knoten-Cluster konfiguriert. Der einzelnen Knoten-Cluster verwaltet InfiniBand-Netzwerke als Clusterressource, um sicherzustellen, dass der Cluster immer das aktive InfiniBand IP verwendet. Die einzelnen Knoten-Cluster verwaltet die PDW-Prozesse, die innerhalb des virtuellen Computers ausgeführt. Beispielsweise hat die Einzelknotencluster SQL Server- und Windows-Verwaltungsinstrumentation (Data Movement Service, DMS) als Ressourcen, damit er in der richtigen Reihenfolge gestartet werden kann. Der steuerknoten VM steuert auch die Startreihenfolge für die anderen virtuellen Computer, die auf der orchestrierungshost ausgeführt.  
  
