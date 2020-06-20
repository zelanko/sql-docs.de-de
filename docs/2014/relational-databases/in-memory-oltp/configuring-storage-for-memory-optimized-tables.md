---
title: Konfigurieren von Speicher für speicheroptimierte Tabellen | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5d2a487354f9cebf8f957f49d065a8d32ce109a0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050264"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a>Konfigurieren von Speicher für speicheroptimierte Tabellen
  Sie müssen die Speicherkapazität und die E/A-Vorgänge pro Sekunde (IOPS) konfigurieren.  
  
## <a name="storage-capacity"></a>Speicherkapazität  
 Verwenden Sie die Informationen unter [Schätzen der Arbeitsspeicheranforderungen speicheroptimierter Tabellen](memory-optimized-tables.md) , um für die dauerhaften speicheroptimierten Tabellen der Datenbank deren Größe im Arbeitsspeicher zu schätzen. Da die Indizes der speicheroptimierten Tabellen nicht beibehalten werden, muss die Größe der Indizes nicht berücksichtigt werden. Wenn Sie die Größe ermittelt haben, müssen Sie Speicherplatz bereitstellen, der vier Mal der Größe der dauerhaften Tabellen im Arbeitsspeicher entspricht.  
  
## <a name="storage-performance"></a>Speicher-Performance  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] kann den Arbeitsauslastungsdurchsatz erheblich erhöhen. Daher ist es wichtig sicherzustellen, dass die E/A-Vorgänge keinen Engpass darstellen.  
  
-   Wenn Sie datenträgerbasierte Tabellen zu speicheroptimierten Tabellen migrieren, stellen Sie sicher, dass sich das Transaktionsprotokoll auf einem Speichermedium befindet, das die erhöhte Transaktionsprotokollaktivität verarbeiten kann. Wenn das Speichermedium z. B. Transaktionsprotokollvorgänge bei 100 MB/s unterstützt und durch speicheroptimierte Tabellen eine fünfmal höhere Leistung erzielt wird, muss das Speichermedium des Transaktionsprotokolls in der Lage sein, die fünfmal höhere Leistung auch zu unterstützen, damit die Transaktionsprotokollaktivitäten nicht zu einem Leistungsengpass führen.  
  
-   Speicheroptimierte Tabellen werden in Dateien beibehalten, die über einen oder mehrere Container verteilt sind. Jeder Container sollte in der Regel einer eigenen Spindel zugeordnet sein. Er wird sowohl für eine höhere Speicherkapazität als auch für eine verbesserte Leistung verwendet. Sie müssen sicherstellen, dass die sequenziellen IOPS der Speichermedien eine dreifache Zunahme des Transaktionsprotokoll Durchsatzes unterstützen können.  
  
     Wenn Speicher optimierte Tabellen z. b. eine Aktivität von 500 MB/s im Transaktionsprotokoll generieren, muss der Speicher für Speicher optimierte Tabellen 1,5 GB/s unterstützen. Die Notwendigkeit, einen dreifachen Anstieg des Transaktionsprotokoll Durchsatzes zu unterstützen, ergibt sich aus der Beobachtung, dass die Daten-und Änderungsdatei Paare zuerst mit den anfänglichen Daten geschrieben und dann als Teil eines Mergevorgangs gelesen und erneut geschrieben werden müssen.  
  
     Ein weiterer Faktor bei der Schätzung des Speicherdurchsatzes ist die Wiederherstellungszeit für speicheroptimierte Tabellen. Daten aus dauerhaften Tabellen müssen in den Speicher gelesen werden, bevor die Datenbank für Anwendungen zur Verfügung steht. Normalerweise können Daten mit dem maximalen IOPS-Wert in speicheroptimierte Tabellen geladen werden. Wenn der gesamte Speicherplatz für dauerhafte speicheroptimierte Tabellen 60 GB beträgt und Sie diese Daten innerhalb von 1 Minute laden möchten, muss der Speicher IOPS mit 1 GB/s unterstützen.  
  
-   Wenn eine gerade Anzahl an Spindeln vorliegt, erstellen Sie zweimal so viele Container, und ordnen Sie jeweils ein Paar derselben Spindel zu. Dies ist erforderlich, um die IOPS- und Speicherlast zu verteilen. Weitere Informationen finden Sie [unter Speicher optimierte Datei Gruppe](the-memory-optimized-filegroup.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
