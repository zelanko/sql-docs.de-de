---
title: Verarbeitung und Speicherkapazität
description: Ihre geschäftlichen Anforderungen bestimmen die Anzahl der Daten Skalierungs Einheiten und die Größe der Datenträger für den Computeknoten, die Sie in Ihrem Analytics Platform System (APS)-Gerät benötigen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 143c37b6b55b96f8a0225c98db2212f07b2cd3a5
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400542"
---
# <a name="processing-and-storage-capacity-in-analytics-platform-system"></a>Verarbeitungs-und Speicherkapazität in Analytics Platform System
Ihre geschäftlichen Anforderungen bestimmen die Anzahl der Daten Skalierungs Einheiten und die Größe der Datenträger für den Computeknoten, die Sie in Ihrem Analytics Platform System (APS)-Gerät benötigen. Verwenden Sie diese Verarbeitungs-und Speicher Berechnungen, um Ihre Kapazitäts Kauf-und Planungsentscheidungen zu steuern.  
  
  
## <a name="planning-for-processing-capacity"></a><a name="section1"></a>Planen der Verarbeitungskapazität  
Die Abfrageleistung für SQL Server parallele Data Warehouse (PDW) hängt stark von der Anzahl der CPU-Kerne ab, die für Ihre Daten parallel funktionieren. Innerhalb von Grenzwerten verbessert die Parallelität die Leistung der MPP-Abfrage (massive Parallel Processing). Auch wenn die Datengröße relativ klein ist, wird die Leistungsfähigkeit der MPP-Abfrage-Engine durch eine größere Parallelität verbessert.  
  
Beispielsweise verfügt eine Appliance mit 12 Computeknoten über 192 CPU-Kerne, die Ihre Daten parallel verarbeiten. Das ist die 192-Wege-Parallelität! Eine Appliance mit 56 Computeknoten verfügt über 896 Kerne, die alle parallel funktionieren. Dieses Ausmaß an Parallelität kann ohne MPP-Computing nicht erreicht werden.  
  
Wenn die Anzahl der Computeknoten zunimmt, erfordert das horizontale hochskalieren der Appliance, dass mehrere Computeknoten gleichzeitig hinzugefügt werden, um einen spürbaren Vorteil zu erzielen. Hardware Anbieter unterstützen nur bestimmte Konfigurationen von datenskalierungseinheiten, um sicherzustellen, dass der Vorteil der Skalierung der Appliance die Kosten für die Neuverteilung der Daten auf mehr Computeknoten auswiegt.  
  
### <a name="data-scale-unit-configuration-examples---hpe"></a>Beispiele für die Konfiguration der Daten Skalierung (HPE)  
Dies sind Beispiele für die unterstützten HPE-Konfigurationen für datenskalierungsdateneinheiten. Sie können von den aktuellsten unterstützten Konfigurationen abweichen, werden jedoch als Beispiel dafür bereitgestellt, wie die Kapazität um etwa 20 Prozent erhöht werden kann.  
  
Uplift ist der prozentuale Kapazitäts Gewinn, indem die datenskalierungsdateneinheiten von einer Zeile zur nächsten erhöht werden. Beispielsweise ergibt eine Erhöhung der datenskalierungseinheiten von 6 auf 8 einen 33%-weltweite cloudangebote in CPU-Kernen und Arbeitsspeicher.  Außerdem vergrößert Sie den Speicherplatz, der in dieser Tabelle nicht angezeigt wird.  
  
|Datenskalierungs Einheiten|Serverknoten|CPU-Kerne|Arbeitsspeicher (GB)|Weltweite cloudangebote|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|2|32|512|-|  
|2|4|64|1024|100 %|  
|3|6|96|1536|50%|  
|4|8|128|2048|33 %|  
|5|10|160|2560|25%|  
|6|12|192|3072|20%|  
|8|16|256|4096|33 %|  
|10|20|320|5120|25%|  
|12|24|384|6.144|20%|  
|16|32|512|8192|33 %|  
|20|40|640|10.240|25%|  
|24|48|768|12288|20%|  
|28|56|896|14336|17 %|  
  
Erläuterung:  
  
-   **Datenskalierungs Einheiten** pro Gerät. Weitere Informationen zu datenskalierungseinheiten finden Sie unter [Analytics Platform System Hardware Components](hardware-components.md).  
  
-   **Compute-Knoten** pro Gerät.  
  
-   **CPU-Kerne** pro Gerät. Es gibt 16 Kerne pro Computeknoten, einen Kern pro gespiegeltes Datenträger Paar. Informationen zur Datenträger Struktur des computeknotens finden Sie unter [Analytics Platform System Hardware Components](hardware-components.md).  
  
-   Arbeits **Speicher** pro Gerät. Jeder Kern verfügt über 256 GB Arbeitsspeicher.  
  
### <a name="data-scale-unit-configuration-examples---dell-quanta"></a>Beispiele für die Konfiguration der Daten Skalierungs Einheit-Dell, QUANTA  
Dies sind Beispiele für die unterstützten Dell-und QUANTA-Konfigurationen für datenskalierungsdatenskalierungseinheiten. Sie können von den aktuellsten unterstützten Konfigurationen abweichen, werden jedoch als Beispiel dafür bereitgestellt, wie die Kapazität um etwa 20 Prozent erhöht werden kann.  
  
Uplift ist der prozentuale Kapazitäts Gewinn, indem die datenskalierungsdateneinheiten von einer Zeile zur nächsten erhöht werden. Beispielsweise ergibt eine Erhöhung der datenskalierungseinheiten von 6 auf 8 einen 33%-weltweite cloudangebote in CPU-Kernen und Arbeitsspeicher. Außerdem vergrößert Sie den Speicherplatz, der in dieser Tabelle nicht angezeigt wird.  
  
|Datenskalierungs Einheiten|Serverknoten|CPU-Kerne|Arbeitsspeicher (GB)|Weltweite cloudangebote|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|3|48|768|-|  
|2|6|96|1536|100 %|  
|3|9|144|2.304|50%|  
|4|12|192|3\.072|33 %|  
|5|15|240|3.840|25%|  
|6|18|288|4\.608|20%|  
|7|21|336|5.376|17 %|  
|8|24|384|6\.144|14 %|  
|9|27|432|6.912|13 %|  
|12|36|576|9\.216|33 %|  
|15|45|720|11.520|25%|  
|18|54|864|13.824|20%|  
  
## <a name="planning-for-storage-capacity"></a><a name="section2"></a>Planen der Speicherkapazität  
In dieser Tabelle wird geschätzt, dass Sie auf einem vollständig erstellten Analytics-Platt Form System Gerät bis zu 6 Daten in Form von nicht komprimierten Daten in einem beliebigen Bereich laden und speichern können. 
  
|Hersteller|Laufwerkgröße|Physischer Datenspeicher pro Computeknoten|Maximale Anzahl von Computeknoten pro Rack|Physischer maximaler Datenspeicher pro Rack|Geschätzter maximaler Benutzerdaten Speicher pro Rack|Maximale Racks|Geschätzter maximaler Benutzerdaten Speicher pro Appliance|  
|----------|--------------|------------------------------------------|----------------------------------|------------------------------------------|------------------------------------------------|-----------------|-----------------------------------------------------|  
|HPE|1 TB|16 TB|8|128 TB|320 TB|7|2.240 TB|  
|HPE|2 TB|32 TB|8|256 TB|640 TB|7|4.480 TB|  
|HPE|4 TB|64 TB|8|512 TB|1280 TB|7|8.960 TB|  
|DELL|1 TB|16 TB|9|144 TB|360 TB|6|2.160 TB|  
|DELL|2 TB|32 TB|9|288 TB|720 TB|6|4.320 TB|  
|DELL|4 TB|64 TB|9|576 TB|1440 TB|6|8.640 TB|   
  
Erläuterung:  
  
-   Die **Laufwerk Größe** beträgt 1, 2 oder 4 TB für jeden Hardware Anbieter.  
  
-   **Physischer Datenspeicher pro Computeknoten** = (Laufwerks Größe) * (16 Datenträger pro Computeknoten). Die gespiegelten Datenträger sind nicht enthalten, da Sie für Redundanz vorgesehen sind.  
  
-   Die **maximalen Computeknoten pro Rack** sind spezifisch für den Hardwarehersteller.  
  
-   **Physischer maximaler Datenspeicher pro Rack** = (physischer Datenspeicher pro Computeknoten) * (maximale Anzahl von Computeknoten pro Rack).  
  
-   **Geschätzter maximaler Benutzerdaten Speicher pro Rack** = (physischer maximaler Datenspeicher pro Rack) * (5 für ein 5:1-Komprimierungs Verhältnis) \* (50% für Protokolle und tempdb). Dies ist eine konservative Schätzung für die unkomprimierten Benutzerdaten, die geladen und auf dem Gerät gespeichert werden können. Dies ist eine Schätzung und wird von Software nicht erzwungen. Die tatsächliche Speicherung von Benutzerdaten hängt von Ihren Daten und der Konfiguration ab.  
  
-   **Maximale Racks** ist für jeden Hardware Anbieter spezifisch.  
  
-   **Geschätzter maximaler Datenspeicher pro Appliance** = (Geschätzter maximaler Datenspeicher pro Rack) * (maximale Anzahl von Racks). Dies ist eine konservative Schätzung der Gesamtgröße von Benutzerdaten, die Sie laden und auf einem vollständig erstellten Gerät speichern können.  
  
