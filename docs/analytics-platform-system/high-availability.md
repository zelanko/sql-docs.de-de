---
title: Hochverfügbarkeit
description: Erfahren Sie, wie das Analytics Platform System (APS) für Hochverfügbarkeit entworfen wird.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6246ed25909a2e366d8bbafcd912a4fd923cc84a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401100"
---
# <a name="analytics-platform-system-high-availability"></a>Hochverfügbarkeit von Analytics Platform System
Erfahren Sie, wie das Analytics Platform System (APS) für Hochverfügbarkeit entworfen wird.  
  
## <a name="high-availability-architecture"></a>Hochverfügbarkeitsarchitektur  
![Geräte Architektur](media/appliance-architecture.png "Geräte Architektur")  
  
## <a name="network"></a>Netzwerk  
Zur Netzwerkverfügbarkeit verfügt das APS-Gerät über zwei InfiniBand-Netzwerke. Wenn eines der InfiniBand-Netzwerke ausfällt, ist das andere noch verfügbar. Außerdem verfügt Active Directory über replizierte Domänen Controller, um eingehende Anforderungen an das richtige InfiniBand-Netzwerk aufzulösen.  
  
Weitere Informationen finden Sie unter [Konfigurieren von InfiniBand-Netzwerkadaptern](configure-infiniband-network-adapters.md).  
  
## <a name="storage"></a>Storage  
Um die Sicherheit der Daten zu gewährleisten, verwendet APS die RAID 1-Spiegelung, um zwei Kopien aller Benutzerdaten zu verwalten. Wenn ein Datenträger ausfällt, erstellt das Hardwaresystem die Daten auf einem freien Datenträger neu und legt eine Warnung fest, dass ein Datenträger Fehler vorliegt.  
  
Damit die Daten online verfügbar bleiben, verwendet APS Windows-Speicherplätze und freigegebene Clustervolumes, um die Benutzerdaten-Datenträger im direkt angeschlossenen Speicher zu verwalten. Es gibt einen Speicherpool pro datenskalierungs Einheit, der in freigegebenen Clustervolumes organisiert ist, die für die Computeknoten-Hosts über Einstellungs Punkte verfügbar sind.  
  
Um sicherzustellen, dass der Speicherpool online bleibt, verfügt jeder Host in der Daten Skalierungs Einheit über einen virtuellen iSCSI-Computer, für den kein Failover ausgeführt wird. Diese Architektur ist wichtig, denn wenn bei einem Host ein Fehler auftritt, kann auf die Daten immer noch über die anderen Hosts in der datenskalierungseinheit zugegriffen werden.  
  
## <a name="hosts"></a>Host  
Bei der Host Verfügbarkeit werden alle Hosts in einem Windows-Failovercluster konfiguriert. Jedes Gestell verfügt über einen passiven Host. Optional kann das erste Gestell, das SQL Server parallele Data Warehouse (PDW) und das gerätefabric steuert, über einen zweiten passiven Host verfügen. Wenn bei einem Host ein Fehler auftritt, wird für virtuelle Computer, die für ein Failover konfiguriert sind, ein Failover auf einen verfügbaren passiven Host ausgeführt.  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>PDW-Knoten und Appliance-Fabric  
Für hohe Verfügbarkeit der PDW-Knoten und des Appliance-Fabrics verwendet APS Virtualisierung. Jede PDW-und Appliance Fabric-Komponente wird auf einem virtuellen Computer ausgeführt.  
  
Jeder virtuelle Computer wird als Rolle im Windows-Failovercluster definiert. Wenn bei einem virtuellen Computer ein Fehler auftritt, wird der Cluster auf einem verfügbaren passiven Host neu gestartet. Die virtuellen Maschinen werden mithilfe von System Center Virtual Machine Manager bereitgestellt. Wenn ein Failover auftritt, kann der virtuelle Computer, der auf dem passiven Host ausgeführt wird, weiterhin über das InfiniBand-Netzwerk auf seine Benutzerdaten zugreifen.  
  
Die virtuellen Maschinen "Steuerungs Knoten" und "Computeknoten" sind jeweils als Einzelknoten Cluster konfiguriert. Der Cluster mit einem einzelnen Knoten verwaltet die InfiniBand-Netzwerke als Cluster Ressource, um sicherzustellen, dass der Cluster immer die aktive InfiniBand-IP-Adresse verwendet. Der Einzelknoten Cluster verwaltet die PDW-Prozesse, die auf dem virtuellen Computer ausgeführt werden. Beispielsweise verfügt der Cluster mit einem einzelnen Knoten über SQL Server und den Daten Verschiebungs Dienst (Data Movement Service, DMS) als Ressourcen, sodass er Sie in der richtigen Reihenfolge starten kann. Der VM-Steuerungs Knoten steuert auch die Start Reihenfolge für die anderen VMS, die auf dem Orchestrierungs Host ausgeführt werden.  
  
