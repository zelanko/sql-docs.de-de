---
title: Verarbeitung und Speicherkapazität - Analytics Platform System | Microsoft-Dokumentation
description: Ihre geschäftlichen Anforderungen bestimmen die Anzahl der Skalierungseinheiten für die Daten und die Größe der Compute-Knoten Datenträger, die in Ihrer Appliance Analytics Platform System (APS) erforderlich.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f20de8ebc4e3b2970e439dbc413e588aa08b5324
ms.sourcegitcommit: 9c99f992abd5f1c174b3d1e978774dffb99ff218
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361570"
---
# <a name="processing-and-storage-capacity-in-analytics-platform-system"></a>Verarbeitung und Speicherkapazität in Analytics Platform System
Ihre geschäftlichen Anforderungen bestimmen die Anzahl der Skalierungseinheiten für die Daten und die Größe der Compute-Knoten Datenträger, die in Ihrer Appliance Analytics Platform System (APS) erforderlich. Verwenden Sie diese Berechnungen Prozessor- und Speicherressourcen, um Ihre Kapazität erwerben und planungsentscheidungen geführt.  
  
  
## <a name="section1"></a>Planung für die Verarbeitung von Kapazität  
Abfrageleistung für SQL Server Parallel Data Warehouse (PDW) hängt stark auf die Anzahl der CPU-Kerne, die Ihre Daten parallel ausgeführt werden. Mit Einschränkungen verbessert Erhöhen der Parallelität die abfrageleistung parallel Processing (MPP) aus. Selbst wenn Ihre Datengröße relativ klein ist, wird die Leistung der Abfrage MPP-Engine, dass mehr Parallelität verbessert.  
  
Beispielsweise hat eine Einheit mit 12 Serverknoten 192 CPU-Kerne, die Ihre Daten parallel verarbeiten. Das ist die 192-Wege-Parallelität. Ein Gerät mit 56 Compute-Knoten hat 896 Kerne arbeiten parallel. Dieses Ausmaß an Parallelität ist ohne MPP computing nicht erreichbar.  
  
Mit zunehmender Anzahl von Compute-Knoten, erfordert horizontales hochskalieren der Appliances und Hinzufügen von mehr als eine Compute-Knoten zu einem Zeitpunkt, um einen spürbaren Vorteil zu erhalten. Hardwarehersteller unterstützt nur bestimmte Konfigurationen für Skalierungseinheiten Daten, um sicherzustellen, dass der Vorteil der Skalierung der Appliances die Kosten der neuverteilung der Daten über mehrere Compute-Knoten von überwiegt.  
  
### <a name="data-scale-unit-configuration-examples---hpe"></a>Beispiele für Daten Skalierungseinheit-Konfiguration – HPE  
Dies sind Beispiele für die unterstützten HPE-Konfigurationen für die Skalierung Uunits Daten. Sie können von der aktuellen unterstützten Konfigurationen variieren, sondern dienen als Beispiel für das Erhöhen der Kapazität um ca. 20 Prozent.  
  
Cloudangebote ist der Gewinn Prozent Kapazität durch das Erhöhen der Uunits Skalierung Daten aus einer Zeile zur nächsten. Erhöhen die Daten Skalierungseinheiten von 6 bis 8 gibt beispielsweise eine Cloudangebote 33 % CPU-Kerne und Arbeitsspeicher.  Außerdem steigt auch den Speicherplatz, der in dieser Tabelle nicht angezeigt.  
  
|Daten-Skalierungseinheiten|Compute-Knoten|CPU-Kerne|Arbeitsspeicher (GB)|Cloudangebote|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|2|32|512|-|  
|2|4|64|1024|100%|  
|3|6|96|1536|50%|  
|4|8|128|2048|33%|  
|5|10|160|2560|25%|  
|6|12|192|3072|20%|  
|8|16|256|4096|33%|  
|10|20|320|5120|25%|  
|12|24|384|6144|20%|  
|16|32|512|8192|33%|  
|20|40|640|10240|25%|  
|24|48|768|12288|20%|  
|28|56|896|14336|17%|  
  
Erklärung:  
  
-   **Daten-Skalierungseinheiten** pro Anwendung. Informationen über Skalierungseinheiten Daten finden Sie [Hardwarekomponenten für Analytics Platform System](hardware-components.md).  
  
-   **Compute-Knoten** pro Anwendung.  
  
-   **CPU-Kerne** pro Anwendung. Es gibt 16 Kerne pro Compute-Knoten, ein Kern pro jedes gespiegelte Datenträger-Paar. Für dem Datenträgerstruktur für Compute-Knoten, finden Sie unter [Hardwarekomponenten für Analytics Platform System](hardware-components.md).  
  
-   **Arbeitsspeicher** pro Anwendung. Jeder Kern über 256 GB Arbeitsspeicher verfügt.  
  
### <a name="data-scale-unit-configuration-examples---dell-quanta"></a>Scale Unit Konfiguration Datenbeispiele - Dell, Quanten  
Dies sind Beispiele für die unterstützten Dell und Quanten-Konfigurationen für die Skalierung Uunits Daten. Sie können von der aktuellen unterstützten Konfigurationen variieren, sondern dienen als Beispiel für das Erhöhen der Kapazität um ca. 20 Prozent.  
  
Cloudangebote ist der Gewinn Prozent Kapazität durch das Erhöhen der Uunits Skalierung Daten aus einer Zeile zur nächsten. Erhöhen die Daten Skalierungseinheiten von 6 bis 8 gibt beispielsweise eine Cloudangebote 33 % CPU-Kerne und Arbeitsspeicher. Außerdem steigt auch den Speicherplatz, der in dieser Tabelle nicht angezeigt.  
  
|Daten-Skalierungseinheiten|Compute-Knoten|CPU-Kerne|Arbeitsspeicher (GB)|Cloudangebote|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|3|48|768|-|  
|2|6|96|1536|100%|  
|3|9|144|2,304|50%|  
|4|12|192|3,072|33%|  
|5|15|240|3,840|25%|  
|6|18|288|4,608|20%|  
|7|21|336|5,376|17%|  
|8|24|384|6,144|14%|  
|9|27|432|6,912|13%|  
|12|36|576|9,216|33%|  
|15|45|720|11,520|25%|  
|18|54|864|13,824|20%|  
  
## <a name="section2"></a>Planen der Speicherkapazität  
In dieser Tabelle schätzt, dass Sie laden und nicht komprimierten Daten auf eine vollständig integrierte Analytics Platform System Appliance bis zu 6 im petabytebereich speichern können. 
  
|Hersteller|Laufwerkgröße|Physischer Daten-Speicher pro Compute-Knoten|Maximale Compute-Knoten pro rack|Physische, maximale Datenspeicherkapazität pro rack|Geschätzte maximale Benutzerdatenspeicher pro rack|Maximale racks|Geschätzte maximale Benutzerdatenspeicher pro Einheit|  
|----------|--------------|------------------------------------------|----------------------------------|------------------------------------------|------------------------------------------------|-----------------|-----------------------------------------------------|  
|HPE|1 TB|16 TB|8|128 TB|320 TB|7|2,240 TB|  
|HPE|2 TB|32 TB|8|256 TB|640 TB|7|4,480 TB|  
|HPE|4 TB|64 TB|8|512 TB|1280 TB|7|8,960 TB|  
|DELL|1 TB|16 TB|9|144 TB|360 TB|6|2,160 TB|  
|DELL|2 TB|32 TB|9|288 TB|720 TB|6|4.320 TB|  
|DELL|4 TB|64 TB|9|576 TB|1440 TB|6|8,640 TB|   
  
Erklärung:  
  
-   **Laufwerkgröße** ist 1, 2 oder 4 TB für jeden Lieferanten für Hardware.  
  
-   **Physische Datenspeicher pro Compute-Knoten** = (Laufwerkgröße) * (16 Datenträger pro Compute-Knoten). Die gespiegelte Datenträger sind nicht enthalten, da sie für die Redundanz sind.  
  
-   **Max. Anzahl von Compute-Knoten pro Rack** bezieht sich auf die Hardwarehersteller.  
  
-   **Physische, maximale Datenspeicherkapazität pro Rack** = (physischen Datenspeicher pro Compute-Knoten) * (maximale Compute-Knoten pro Rack).  
  
-   **Geschätzte maximale Benutzerdatenspeicher pro Rack** = (physische maximale Datenspeicherkapazität pro Rack) * (für ein Komprimierungsverhältnis von 5:1-5) \* (50 % für Protokolle und TempDB). Dies ist eine konservative Schätzung für die unkomprimierten Benutzerdaten, die geladen und auf dem Gerät gespeichert werden können. Dies ist eine Schätzung und wird von der Software nicht erzwungen. Die tatsächliche Speicherung hängt davon ab, Ihre Daten und Ihrer Konfiguration.  
  
-   **Maximale Racks** ist spezifisch für jeden Lieferanten für Hardware.  
  
-   **Geschätzte maximale Datenspeicherkapazität pro Appliance** = (geschätzte maximale Datenspeicherkapazität pro Rack) * (maximale racks). Dies ist eine konservative Schätzung der Gesamtsumme Gesamtgröße von Benutzerdaten, die Sie laden und speichern in einem vollständig integrierten Gerät konnte.  
  
