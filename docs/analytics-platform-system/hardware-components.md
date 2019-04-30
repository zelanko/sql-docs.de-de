---
title: Hardware-Komponenten - Analytics Platform System | Microsoft-Dokumentation
description: Analytics Platform System (APS) verwendet skalierbare Komponenten, sodass Sie die richtige Menge an Prozessor- und Speicherressourcen gemäß Ihren geschäftlichen Anforderungen erwerben können. Wenn Sie APS bestellen, benötigen Sie eine Kombination aus diesen Hardware-Kernkomponenten.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8cf7fd100f72e14b09ea086a1ebff5140a9068a4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63157400"
---
# <a name="hardware-components-for-analytics-platform-system"></a>Hardware-Komponenten für Analytics Platform System

Analytics Platform System (APS) verwendet skalierbare Komponenten, sodass Sie die richtige Menge an Prozessor- und Speicherressourcen gemäß Ihren geschäftlichen Anforderungen erwerben können. Wenn Sie APS bestellen, benötigen Sie eine Kombination aus diesen Hardware-Kernkomponenten. Konkrete Hardwarehersteller können verschiedene Benennungskonventionen oder bei zusätzlichen Komponenten.  
 
  
## <a name="rackandnetwork"></a>Rack und Netzwerk 
 
APS-Komponenten werden alle in eine oder mehrere Racks gespeichert, die in Ihr Rechenzentrum passt. Jedes Rack im Lieferumfang von Stromverteilereinheiten (PDUs), zwei InfiniBand-Switches und zwei Ethernet-Switches.  
  
![Rack und Netzwerk](media/rack-and-network.png "APS-rack und Netzwerk")  
  
## <a name="datascaleunit"></a>Daten-Skalierungseinheit
 
Eine Skalierungseinheit mit Daten enthält, die Daten von Hosts und die direkt angeschlossenem Speicher (DAS) zum Verarbeiten und Speichern von Benutzerdaten. Fügen Sie Daten Mengen-Einheiten, entsprechend den Konfigurationen, die von Ihrem Hardwarehersteller unterstützt werden hinzu, um Kapazität hinzuzufügen. Mit steigender Anzahl der Skalierungseinheiten für Daten, müssen Sie zusätzliche Rack hinzufügen und Netzwerkkomponenten, nach Bedarf, um mehr zu bieten, Netzwerk sowie die rack-Infrastruktur.  
  
### <a name="data-host"></a>Daten-host  

Ein Host Daten ist es sich um einen Server für die Verarbeitung von Daten des Benutzers festgelegt. Parallel Data Warehouse (PDW) führt eine Compute-Knoten auf jedem Host Daten an. Für HPE Appliances hat die Data-Skalierungseinheit zwei Data-Hosts. Für Dell und Quanten Appliances hat die Data-Skalierungseinheit drei Data-Hosts.  
  
### <a name="direct-attached-storage"></a>Direkt angeschlossener Speicher
 
Der direkte angeschlossene Speicher (DAS) ist ein Pool von Datenträgern, die mit den Daten Hosts verbunden sind. Alle Daten Hosts können die Datenträger zugreifen. Als Teil der shared-Nothing-Architektur, die Compute-Knoten, die auf den Hosts für die Daten, weisen nicht die einzelnen Datenträger. Für hohe Verfügbarkeit, jedoch ist der Speicherzugriff freigegeben und kann einzelnen Hosts Daten zugreifen, der Datenträger.  
  
### <a name="data-scale-unit-architecture---dell-and-quanta"></a>Scale Unit Datenarchitektur - DELL und Quanten
  
![Skalierbarkeitseinheit](media/scalability-unit-dell.png "Dell skalierbarkeitseinheit")  
  
### <a name="data-scale-unit-architecture---hpe"></a>Data-Architektur Einheit skalieren - HPE 
 
![HPE skalierbarkeitseinheit](media/scalability-unit-hpe.png "HPE skalierbarkeitseinheit")  
  
### <a name="data-scale-unit-description"></a>Beschreibung zu Einheit skalieren

Eine Daten-Skalierungseinheit ist ein Server (Host) für jeden Compute-Knoten und einen direkt angeschlossenen Datenträger-Array, das mit Serial Attached SCSI (SAS) angeschlossen ist. In der CAB-Speicher ist dem Datenträgerarray in zwei Hälften unterteilt, von denen jeder redundanten Stromversorgungen. Windows Server-Speicherplätzen werden Daten des Benutzers durch Duplizieren von Daten über RAID 1-Spiegelsatz datenträgerpaaren verwaltet. Die Datenträger in jedem Paar Datenträger werden in Hälften des Datenträgerarrays gespeichert.  
  
Der Datenträgerarray enthält auch hot-spare-Laufwerke und einen Systemdatenträger. Wenn ein Datenträger ausfällt, verwendet Speicherplätze die intakten Kopie der Daten auf dem funktionsfähigen Datenträger, um eine doppelte Kopie der Daten auf einen hot-Spare neu zu erstellen. Dies ist eine wichtige Selbstreparatur-Funktion, die Ihnen hilft, um vor Datenverlusten zu schützen.  
  
Die Gesamtzahl von Datenträgern für die Compute-Knoten:  
  
-   DELL hat 96 Festplatten = (3-Server) * (16 Datenträger pro Server) \* (2 für redundante Datenträger).  
  
-   HPE sind 64 Datenträger = (2-Server) * (16 Datenträger pro Server) \* (2 für redundante Datenträger).  
  
-   Darüber hinaus verfügt jeder Datenträgerarray hot-spare-Laufwerke und einen Systemdatenträger.  
  
**Für hohe Verfügbarkeit**, Compute-Knoten, beim Failover können sie funktionieren weiterhin und Zugriff auf die Benutzerdaten über den anderen Host in der Data-Skalierungseinheit. Mindestens eines direkt angeschlossenen physischen Hosts ausgeführt werden muss, oder Datenzugriff auf den Speicher geht verloren.  
  
**Für Datenträgergrößen**, den direkte angeschlossene Speicher verfügen kann, 1, 2 oder 3 TB-Festplatten. Alle Daten Skalierungseinheiten müssen die Datenträger mit derselben Größe.  
  
## <a name="basescaleunit"></a>Grundlegende Skalierungseinheit 
 
Die Basis-Skalierungseinheit enthält die minimale Anzahl von Brain-Power-Hosts, Daten von Hosts und direkt angeschlossener Speicher, der für die Anwendung erforderlich ist. Es umfasst die folgenden Komponenten. 
  
### <a name="orchestration-host"></a>Orchestrierungshost  
Dieser Server führt die Gehirne von PDW.
  
### <a name="passive-host"></a>Passive host  
Dieser Server bietet eine hohe Verfügbarkeit. Es ist online und zum Ausführen von Aufträgen im Fall ein Ausfalls auf die Orchestrierung oder Daten hosten kann. Der orchestrierungshost, passive Host und Daten Scale Unit Server werden als Windows-Failovercluster konfiguriert. Jedes Rack, in der Appliance ist eine passive Host erforderlich.  
  
### <a name="optional-passive-host"></a>Optionale passiven host  
Um Redundanz Weitere hinzufügen zu können, müssen Sie die Option zum Hinzufügen eines zweiten passiven Hosts auf der Basis-Skalierungseinheit.  
  
### <a name="data-scale-unit"></a>Daten-Skalierungseinheit  
Die Basis-Mengen-Einheit umfasst eine Daten-Skalierungseinheit die am unteren Rand im Rack platziert wird.  
  
Dieses Diagramm zeigt die Basis-Skalierungseinheit sowie das Rack und das Netzwerk. Dies ist der Mindestkonfiguration für Analytics Platform System Appliance.  
  
![Grundlegende Skalierungseinheit](media/base-scale-unit.png "Basis-Skalierungseinheit")  
 
