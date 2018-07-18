---
title: Konfigurieren von Speicher für speicheroptimierte Tabellen | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
caps.latest.revision: 5
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 5c8b5a9f50c30cccb7a0e24799ca59105294aba0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236770"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a>Konfigurieren von Speicher für speicheroptimierte Tabellen
  Sie müssen die Speicherkapazität und die E/A-Vorgänge pro Sekunde (IOPS) konfigurieren.  
  
## <a name="storage-capacity"></a>Speicherkapazität  
 Verwenden Sie die Informationen unter [Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen](memory-optimized-tables.md) , um für die dauerhaften speicheroptimierten Tabellen der Datenbank deren Größe im Arbeitsspeicher zu schätzen. Da die Indizes der speicheroptimierten Tabellen nicht beibehalten werden, muss die Größe der Indizes nicht berücksichtigt werden. Wenn Sie die Größe ermittelt haben, müssen Sie Speicherplatz bereitstellen, der vier Mal der Größe der dauerhaften Tabellen im Arbeitsspeicher entspricht.  
  
## <a name="storage-performance"></a>Speicher-Performance  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] kann den Arbeitsauslastungsdurchsatz erheblich erhöhen. Daher ist es wichtig sicherzustellen, dass die E/A-Vorgänge keinen Engpass darstellen.  
  
-   Wenn Sie datenträgerbasierte Tabellen zu speicheroptimierten Tabellen migrieren, stellen Sie sicher, dass sich das Transaktionsprotokoll auf einem Speichermedium befindet, das die erhöhte Transaktionsprotokollaktivität verarbeiten kann. Wenn das Speichermedium z. B. Transaktionsprotokollvorgänge bei 100 MB/s unterstützt und durch speicheroptimierte Tabellen eine fünfmal höhere Leistung erzielt wird, muss das Speichermedium des Transaktionsprotokolls in der Lage sein, die fünfmal höhere Leistung auch zu unterstützen, damit die Transaktionsprotokollaktivitäten nicht zu einem Leistungsengpass führen.  
  
-   Speicheroptimierte Tabellen werden in Dateien beibehalten, die über einen oder mehrere Container verteilt sind. Jeder Container sollte in der Regel einer eigenen Spindel zugeordnet sein. Er wird sowohl für eine höhere Speicherkapazität als auch für eine verbesserte Leistung verwendet. Sie müssen sicherstellen, dass bei sequenziellen IOPS auf dem Speichermedium der dreifache Wert des Transaktionsprotokolldurchsatzes unterstützt wird.  
  
     Z. B. wenn Speicheroptimierte Tabellen Aktivitäten mit 500 MB/s im Transaktionsprotokoll generiert werden, muss der Speicher für Speicheroptimierte Tabellen 1,5 GB/s unterstützen. Die Notwendigkeit zur Unterstützung von einem 3 Mal Anstieg der transaktionsprotokolldurchsatzes ergibt sich daraus, dass die Daten- und Änderungsdateien zunächst mit den anfänglichen Daten geschrieben werden und anschließend Lese-/neu geschrieben werden müssen als Teil eines Zusammenführungsvorgangs.  
  
     Ein weiterer Faktor bei der Schätzung des Speicherdurchsatzes ist die Wiederherstellungszeit für speicheroptimierte Tabellen. Daten aus dauerhaften Tabellen müssen in den Speicher gelesen werden, bevor die Datenbank für Anwendungen zur Verfügung steht. Normalerweise können Daten mit dem maximalen IOPS-Wert in speicheroptimierte Tabellen geladen werden. Wenn der gesamte Speicherplatz für dauerhafte speicheroptimierte Tabellen 60 GB beträgt und Sie diese Daten innerhalb von 1 Minute laden möchten, muss der Speicher IOPS mit 1 GB/s unterstützen.  
  
-   Wenn eine gerade Anzahl an Spindeln vorliegt, erstellen Sie zweimal so viele Container, und ordnen Sie jeweils ein Paar derselben Spindel zu. Dies ist erforderlich, um die IOPS- und Speicherlast zu verteilen. Weitere Informationen finden Sie unter [die Speicheroptimierte Dateigruppe](the-memory-optimized-filegroup.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
