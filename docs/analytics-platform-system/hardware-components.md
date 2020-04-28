---
title: Hardwarekomponenten
description: Analytics Platform System (APS) nutzt skalierbare Komponenten, sodass Sie die richtige Menge an Verarbeitung und Speicherung gemäß Ihren Geschäftsanforderungen erwerben können. Wenn Sie APS anordnen, benötigen Sie eine Kombination dieser kernhardware Komponenten.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: db9966315d60fd4de1de7ae6805620d3f2144e6f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401146"
---
# <a name="hardware-components-for-analytics-platform-system"></a>Hardware Komponenten für Analytics Platform System

Analytics Platform System (APS) nutzt skalierbare Komponenten, sodass Sie die richtige Menge an Verarbeitung und Speicherung gemäß Ihren Geschäftsanforderungen erwerben können. Wenn Sie APS anordnen, benötigen Sie eine Kombination dieser kernhardware Komponenten. Bestimmte Hardware Anbieter verwenden möglicherweise andere Benennungs Konventionen oder zusätzliche Komponenten.  
 
  
## <a name="rack-and-network"></a><a name="rackandnetwork"></a>Gestell und Netzwerk 
 
APS-Komponenten werden alle in einem oder mehreren Racks gespeichert, die in Ihr Rechenzentrum passt. Jedes Gestell verfügt über Stromverteiler Einheiten (PDUs), zwei InfiniBand-Switches und zwei Ethernet-Switches.  
  
![Gestell und Netzwerk](media/rack-and-network.png "APS-Rack und-Netzwerk")  
  
## <a name="data-scale-unit"></a><a name="datascaleunit"></a>Datenskalierungs Einheit
 
Eine datenskalierungs Einheit enthält die Daten Hosts und den direkt angeschlossenen Speicher (das) zum Verarbeiten und Speichern von Benutzerdaten. Um Kapazität hinzuzufügen, fügen Sie Daten Skalierungs Einheiten gemäß den Konfigurationen hinzu, die vom Hardwarehersteller unterstützt werden. Wenn die Anzahl der Daten Skalierungs Einheiten zunimmt, müssen Sie ggf. zusätzliche Rack & Netzwerkkomponenten hinzufügen, um eine höhere Stromversorgung, Netzwerk-und Gestell-Infrastruktur bereitzustellen.  
  
### <a name="data-host"></a>Datenhost  

Ein datenhost ist ein Server, der für die Verarbeitung von Benutzerdaten reserviert ist. Parallel Data Warehouse (PDW) führt einen Computeknoten auf den einzelnen Daten Hosts aus. Bei HPE-Geräten verfügt die Daten Skalierungs Einheit über zwei Daten Hosts. Bei Dell-und QUANTA-Geräten verfügt die datenskalierungs Einheit über drei Daten Hosts.  
  
### <a name="direct-attached-storage"></a>Direkt angeschlossener Speicher
 
Der Direct Attached Storage (das) ist ein Pool von Datenträgern, die mit den Daten Hosts verbunden sind. Alle Daten Hosts können auf alle Datenträger zugreifen. Als Teil der Shared Nothing-Architektur verwenden die auf den Daten Hosts verwendeten Computeknoten keine einzelnen Datenträger gemeinsam. Für hohe Verfügbarkeit wird der Speicherzugriff jedoch freigegeben, und jeder der Daten Hosts kann auf die Datenträger zugreifen.  
  
### <a name="data-scale-unit-architecture---dell-and-quanta"></a>Architektur der Data Scale Unit (Dell und QUANTA)
  
![Skalierbarkeits Einheit](media/scalability-unit-dell.png "Dell-Skalierbarkeits Einheit")  
  
### <a name="data-scale-unit-architecture---hpe"></a>Architektur der Data Scale Unit (HPE) 
 
![HPE-Skalierbarkeits Einheit](media/scalability-unit-hpe.png "HPE-Skalierbarkeits Einheit")  
  
### <a name="data-scale-unit-description"></a>Beschreibung der Daten Skalierungs Einheit

Eine datenskalierungs Einheit verfügt über einen Server (Host) für jeden Computeknoten und ein direkt angefügtes Datenträger Array, das mit Serial Attached SCSI (SAS) verbunden ist. Im Speicher Schrank ist das Datenträger Array in zwei Hälften unterteilt, die jeweils über redundante Stromversorgungen verfügen. Windows Server-Speicherplätze verwalten Benutzerdaten durch Duplizieren von Daten über RAID 1-gespiegelte Datenträger Paare. Die Datenträger in den einzelnen Datenträger Paaren werden in unterschiedlichen Hälften des Datenträger Arrays gespeichert.  
  
Das Datenträger Array enthält auch Hot-Spare-Laufwerke und einen System Datenträger. Wenn ein Datenträger ausfällt, verwendet Speicherplätze die gute Kopie der Daten auf dem funktionierenden Datenträger, um eine doppelte Kopie der Daten auf einem Hotspare wiederherzustellen. Dies ist eine wichtige Selbstreparatur Funktion, die den Schutz vor Datenverlusten erleichtert.  
  
Die Gesamtanzahl der Datenträger für die Computeknoten:  
  
-   Dell verfügt über 96 Disks = (3 Server) * (16 Datenträger pro \* Server) (2 für redundante Datenträger).  
  
-   HPE hat 64 Datenträger = (2 Server) * (16 Datenträger pro \* Server) (2 für redundante Datenträger).  
  
-   Außerdem verfügt jedes Datenträger Array über Hot-Spare-Datenträger und einen System Datenträger.  
  
Wenn **für hohe Verfügbarkeit**ein Failover eines computeknotens durchgeführt wird, kann es weiterhin funktionsfähig sein und auf seine Benutzerdaten über den anderen Host in der Daten Skalierungs Einheit zugreifen. Mindestens einer der direkt angeschlossenen physischen Hosts muss funktionieren, oder der Datenzugriff auf den Speicher geht verloren.  
  
**Für**Datenträger Größen kann der direkt angeschlossene Speicher über 1, 2 oder 3 Terabyte Festplattenlaufwerke verfügen. Alle datenskalierungseinheiten müssen Datenträger mit derselben Größe aufweisen.  
  
## <a name="base-scale-unit"></a><a name="basescaleunit"></a>Basis Skalierungs Einheit 
 
Die Basis Skalierungs Einheit enthält die Mindestanzahl von Brain-Power-Hosts, Daten Hosts und einem direkt angeschlossenen Speicher, der für das Gerät erforderlich ist. Sie enthält die folgenden Komponenten. 
  
### <a name="orchestration-host"></a>Orchestrierungs Host  
Dieser Server führt die Brains von PDW aus.
  
### <a name="passive-host"></a>Passiver Host  
Dieser Server bietet hohe Verfügbarkeit. Er ist online und bereit, Aufträge auszuführen, wenn ein Fehler bei der Orchestrierung oder dem datenhost auftritt. Der Orchestrierungs Host, der passive Host und die Daten Skalierungs Einheiten Server sind als Windows-Failovercluster konfiguriert. Für jedes Gestell in der Appliance ist ein passiver Host erforderlich.  
  
### <a name="optional-passive-host"></a>Optionaler passiver Host  
Zum Hinzufügen weiterer Redundanz haben Sie die Möglichkeit, der Basis Skalierungs Einheit einen zweiten passiven Host hinzuzufügen.  
  
### <a name="data-scale-unit"></a>Datenskalierungs Einheit  
Die Basis Skalierungs Einheit umfasst eine Daten Skalierungs Einheit, die sich am unteren Rand des Racks befindet.  
  
Dieses Diagramm zeigt die grundlegende Skalierungs Einheit sowie das Gestell und das Netzwerk. Dies ist die minimale Konfiguration für eine Analytics Platform System-Appliance.  
  
![Basis Skalierungs Einheit](media/base-scale-unit.png "Basis Skalierungs Einheit")  
 
