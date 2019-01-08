---
title: – Hardwarekonfigurationen – Analytics Platform System | Microsoft-Dokumentation
description: Die Einheiten-Hardware des Analytics Platform System (APS) basiert, damit Sie die richtige Menge an Prozessor- und Speicherressourcen gemäß Ihren geschäftlichen Anforderungen erwerben mit skalierbaren Einheiten. Die Appliance Skalierung Speicher für Parallel Data Warehouse über einige Terabytes auf mehr als 6 Petabytes von Daten.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2a252e5f2aebd8d51b9b0eb1f353ded504155c2e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52507948"
---
# <a name="hardware-configurations---analytics-platform-system"></a>– Hardwarekonfigurationen – Analytics Platform System
Die Hardware des Analytics Platform System (APS) basiert, damit Sie die richtige Menge an Prozessor- und Speicherressourcen gemäß Ihren geschäftlichen Anforderungen erwerben mit skalierbaren Einheiten. Die Appliance skaliert Storage für SQL Server Parallel Data Wareouse (PDW) von ein paar Terabytes auf mehr als 6 Petabytes von Daten.  
  
## <a name="contents"></a>Inhalt  
  
-   [Ein-Rack-Konfigurationen](#section1)  
  
-   [Multi-Rack-Konfigurationen](#section2)  

  
## <a name="section1"></a>Ein-Rack-Konfigurationen  
Das erste Rack, in der Appliance enthält die erforderlichen Komponenten zum Ausführen von PDW. Die minimale Einheitenkonfiguration ist ein Rack und Netzwerk und eine Basis-Skalierungseinheit. Diese Diagramme zeigen die Möglichkeiten, das erste Rack des Geräts konfiguriert werden kann. Sie können zwischen 2 und 9 Compute-Knoten in das erste Rack, je nach Hardwarehersteller verwenden.  
  
### <a name="first-rack-configurations---dell"></a>Zuerst Rack-Konfigurationen - DELL  
Die Mindestanforderungen für die Konfiguration für ein Gerät DELL hat 3-Compute-Knoten. Sie können bis zu 2 Skalierungseinheiten für die Daten für das erste Rack für einen Zeitraum von 9 Compute-Knoten hinzufügen.  
  
![Dell erste Rack Konfigurationen](media/first-rack-configurations-dell.png "Dell erste Rack-Konfigurationen")  
  
### <a name="first-rack-configurations---hpe"></a>Zuerst Rack-Konfigurationen - HPE  
Die Mindestanforderungen für die Konfiguration für eine Einheit HPE hat 2 Computeknoten. Sie können bis zu 3 Skalierungseinheiten für die Daten für das erste Rack für einen Zeitraum von 8 Serverknoten hinzufügen.  
  
![HPE rack zuerst die Konfigurationen für HPE](media/first-rack-configurations-hpe.png "HPE zuerst rack-Konfigurationen")  
  
## <a name="section2"></a>Multi-Rack-Konfigurationen  
Sie können zum Hinzufügen von Kapazität in PDW Hinzufügen von Skalierungseinheiten für Daten, zusammen mit zusätzlichen Rack & Netzwerk-Komponenten wie erforderlich, um die richtige Stromversorgung, Netzwerk und rack-Infrastruktur. Jede zusätzliche Rack & Netzwerk ist ein passiven Host erforderlich.  
  
Jeder Hersteller gibt die Anzahl der Daten Skalierungseinheiten, die Sie hinzufügen können, erhalten die Kapazität Ihres Geräts an. Es wird empfohlen, genügend Daten Skalierungseinheiten dahingehend, dass mindestens eine 20-Prozent-Cloudangebote Leistung hinzufügen. Beispielsweise kann eine Daten-Skala hinzufügen Einheit in einer Anwendung, die bereits von 20 Skalierungseinheiten für die Daten in einem vernachlässigbaren Leistungsgewinn führen. Der Reingewinn wäre nicht zu den Kosten und Aufwand.  
  
### <a name="scale-out-example---hpe"></a>Beispiel: HPE skalieren  
Dieses Diagramm zeigt eine 3 Rack HP-Anwendung, die 20 Compute-Knoten enthält.  
  
![HPE Appliance mit 20 Serverknoten](media/scale-out-hpe.png "HPE Appliance mit 20 Serverknoten")  
  
### <a name="scale-out-example---dell-quanta"></a>Scale Out-Beispiel: DELL-Quanten  
Dieses Diagramm zeigt eine 3 Rack DELL oder Quanta Appliance, die 21 Compute-Knoten enthält.  
  
![Dell-Appliance mit 21 Computeknoten](media/scale-out-dell.png "Dell-Appliance mit 21 Compute-Knoten")  
 
