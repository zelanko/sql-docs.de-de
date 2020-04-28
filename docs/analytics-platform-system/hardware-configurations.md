---
title: Hardwarekonfigurationen
description: Die Hardware des Analytics-plattformsystems (APS) ist mit skalierbaren Einheiten aufgebaut, sodass Sie die richtige Menge an Verarbeitung und Speicherung gemäß Ihren Geschäftsanforderungen erwerben. Die Appliance skaliert Speicher für parallele Data Warehouse von einem Paar von Terabyte bis zu mehr als 6 Daten.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ee16045931da345f06c141597ccd25d19a36dea7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401133"
---
# <a name="hardware-configurations---analytics-platform-system"></a>Hardware Konfigurationen-Analytics Platform System
Die Hardware des Analytics Platform System (APS) wurde mit skalierbaren Einheiten entworfen, sodass Sie die richtige Menge an Verarbeitung und Speicherung gemäß Ihren Geschäftsanforderungen erwerben. Die Appliance skaliert Speicher für SQL Server parallele Data-wareouse (PDW) von einem Paar von Terabyte bis zu über 6 Peer tabytes von Daten.  
  
## <a name="contents"></a>Contents  
  
-   [One-Rack-Konfigurationen](#section1)  
  
-   [Konfigurationen mit mehreren Racks](#section2)  

  
## <a name="one-rack-configurations"></a><a name="section1"></a>One-Rack-Konfigurationen  
Das erste Gestell in der Appliance enthält die zum Ausführen von PDW erforderlichen Komponenten. Die minimale Gerätekonfiguration ist ein Gestell und Netzwerk sowie eine Basis Skalierungs Einheit. Diese Diagramme zeigen, wie das erste Gestell des Geräts konfiguriert werden kann. Abhängig vom Hardware Anbieter können Sie zwischen 2 und 9 Computeknoten im ersten Rack haben.  
  
### <a name="first-rack-configurations---dell"></a>Erste Rack-Konfigurationen (Dell)  
Die minimale Konfiguration für eine Dell-Appliance umfasst drei Computeknoten. Sie können dem ersten Gestell bis zu 2 datenskalierungs Einheiten für insgesamt 9 Computeknoten hinzufügen.  
  
![Dell First Rack-Konfigurationen](media/first-rack-configurations-dell.png "Dell First Rack-Konfigurationen")  
  
### <a name="first-rack-configurations---hpe"></a>Erste Rack-Konfigurationen-HPE  
Die Mindestkonfiguration für eine HPE-Appliance umfasst zwei Computeknoten. Sie können dem ersten Gestell bis zu 3 Daten Skalierungs Einheiten hinzufügen, um insgesamt acht Computeknoten zu erhalten.  
  
![HPE First Rack-Konfigurationen für HPE](media/first-rack-configurations-hpe.png "HPE-erste Rack-Konfigurationen")  
  
## <a name="multi-rack-configurations"></a><a name="section2"></a>Konfigurationen mit mehreren Racks  
Um PDW Kapazität hinzuzufügen, können Sie Daten Skalierungs Einheiten zusammen mit zusätzlichen Rack & Netzwerkkomponenten hinzufügen, um die richtige Stromversorgung, Netzwerk-und Rack-Infrastruktur bereitzustellen. Für jedes zusätzliche Rack & Netzwerk ist ein passiver Host erforderlich.  
  
Jeder Hardwarehersteller gibt die Anzahl der Daten Skalierungs Einheiten an, die Sie mit der Kapazität Ihres Geräts hinzufügen können. Es wird empfohlen, genügend Daten Skalierungs Einheiten hinzuzufügen, um mindestens eine Erhöhung der Leistung von 20 Prozent zu sehen. Beispielsweise kann das Hinzufügen einer Daten Skalierungs Einheit zu einem Gerät, das bereits 20 datenskalierungseinheiten aufweist, zu einem vernachlässigbaren Leistungsgewinn führen. Der Nettogewinn wäre nicht die Kosten und der Aufwand.  
  
### <a name="scale-out-example---hpe"></a>Beispiel für horizontales hochskalieren: HPE  
Dieses Diagramm zeigt ein 3-Rack-HP-Gerät, das 20 Computeknoten enthält.  
  
![HPE-Appliance mit 20 Computeknoten](media/scale-out-hpe.png "HPE-Appliance mit 20 Computeknoten")  
  
### <a name="scale-out-example---dell-quanta"></a>Scale Out Beispiel-Dell, QUANTA  
Dieses Diagramm zeigt ein 3-Rack-Dell oder ein QUANTA-Gerät, das 21 Computeknoten enthält.  
  
![Dell Appliance mit 21 Computeknoten](media/scale-out-dell.png "Dell Appliance mit 21 Computeknoten")  
 
