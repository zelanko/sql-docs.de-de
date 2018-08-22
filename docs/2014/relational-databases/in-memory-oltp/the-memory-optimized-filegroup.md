---
title: Die speicheroptimierte Dateigruppe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
caps.latest.revision: 12
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 021bab292e56b9ead1164cd3933efa6c02eb7ee4
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395491"
---
# <a name="the-memory-optimized-filegroup"></a>Die speicheroptimierte Dateigruppe
  Um speicheroptimierte Tabellen zu erstellen, müssen Sie zuerst eine speicheroptimierte Dateigruppe erstellen. Die speicheroptimierte Dateigruppe enthält mindestens einen Container. Jeder Container enthält Datendateien oder Änderungsdateien oder sowohl als auch.  
  
 Obwohl Datenzeilen aus SCHEMA_ONLY-Tabellen nicht beibehalten werden und die Metadaten für speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren in herkömmlichen Katalogen gespeichert werden, ist für die [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Engine weiterhin eine speicheroptimierte Dateigruppe erforderlich, damit die Behandlung speicheroptimierter SCHEMA_ONLY-Tabellen für Datenbanken mit speicheroptimierten Tabellen konsistent ist.  
  
 Die speicheroptimierte Dateigruppe basiert auf Filestream-Dateigruppen, von denen sie sich in folgenden Punkten unterscheidet:  
  
-   Sie können nur eine speicheroptimierte Dateigruppe pro Datenbank erstellen. Sie müssen die Dateigruppe explizit als Container für aus memory_optimized_data markieren. Sie können die Dateigruppe erstellen, wenn Sie die Datenbank erstellen, oder Sie können sie später hinzufügen:  
  
    ```  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   Sie müssen der MEMORY_OPTIMIZED_DATA-Dateigruppe mindestens einen Container hinzufügen. Zum Beispiel:  
  
    ```  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   Es ist nicht erforderlich, Filestream zu aktivieren ([Aktivieren und Konfigurieren von FILESTREAM](../blob/enable-and-configure-filestream.md)), um eine speicheroptimierte Dateigruppe zu erstellen. Die Zuordnung zu Filestream wird über die [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Engine ausgeführt.  
  
-   Sie können einer speicheroptimierten Dateigruppe neue Container hinzufügen. Möglicherweise benötigen Sie einen neuen Container, um den Speicher zu erweitern, der für die dauerhafte speicheroptimierte Tabelle und die Weitergabe von E/A über mehrere Container hinweg benötigt wird.  
  
-   Die Datenverschiebung mit einer speicheroptimierten Dateigruppe ist in einer AlwaysOn-Verfügbarkeitsgruppenkonfiguration optimiert. Im Gegensatz zu Filestream-Dateien, die an sekundäre Replikate gesendet werden, werden die Prüfpunktdateien (Daten und Änderungen) in der speicheroptimierten Dateigruppe nicht an die sekundären Replikate gesendet. Die Daten- und Änderungsdateien werden mithilfe des Transaktionsprotokolls für das sekundäre Replikat erstellt.  
  
 Beachten Sie die folgenden Einschränkungen der speicheroptimierten Dateigruppe:  
  
-   Sobald Sie eine speicheroptimierte Dateigruppe erstellt haben, können Sie sie nur entfernen, indem Sie die Datenbank löschen. In einer Produktionsumgebung müssen Sie die speicheroptimierte Dateigruppe wahrscheinlich nicht entfernen.  
  
-   Sie können einen nicht leeren Container nicht löschen und Daten- und Änderungsdateipaare nicht in einen anderen Container in der speicheroptimierten Dateigruppe verschieben.  
  
-   Sie können MAXSIZE nicht für den Container angeben.  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>Konfigurieren einer speicheroptimierten Dateigruppe  
 Sie sollten mehrere Container in der speicheroptimierten Dateigruppe erstellen und auf unterschiedliche Laufwerke verteilen, um beim Streamen der Daten in den Arbeitsspeicher eine höhere Bandbreite zu erzielen.  
  
 Wenn Sie den Speicher konfigurieren, müssen Sie freien Speicherplatz bereitstellen, der viermal so groß wie die dauerhaften speicheroptimierten Tabellen ist. Stellen Sie auch sicher, dass das E/A-Subsystem die erforderlichen IOPS für die Arbeitsauslastung unterstützt. Wenn Daten- und Änderungsdateipaare bei bestimmten IOPS aufgefüllt werden, benötigen Sie dreimal so viel IOPS, um Speicher- und Zusammenführungsvorgänge zu berücksichtigen. Sie können Speicherkapazität und IOPS hinzufügen, indem Sie einen oder mehrere Container zur speicheroptimierten Dateigruppe hinzufügen.  
  
 In einem Szenario mit mehreren Containern und mehreren Laufwerken werden Daten- und Änderungsdateien im Round-Robin-Verfahren den Containern zugewiesen. Die erste Datendatei wird aus dem ersten Container zugewiesen, und die Änderungsdatei wird aus dem nächsten Container zugewiesen. Dieses Zuordnungsmuster wird wiederholt. Bei diesem Zuordnungsschema werden Daten- und Änderungsdateien gleichmäßig auf Container verteilt, wenn Sie über eine ungerade Zahl von Laufwerken verfügen, die jeweils einem Container zugeordnet sind. Wenn Sie jedoch über eine gerade Anzahl von Laufwerken verfügen, die jeweils einem Container zugeordnet sind, kann dies zu einer unausgeglichenen Speicherung führen, bei der Datendateien ungeraden Laufwerken und Änderungsdateien geraden Laufwerken zugeordnet werden. Um bei der Wiederherstellung einen ausgeglichenen E/A-Datenstrom zu erzielen, sollten Sie Paare von Daten- und Änderungsdateien auf den gleichen Spindeln bzw. im gleichen Speicher platzieren, wie im folgenden Beispiel beschrieben.  
  
 **Beispiel:** sollten Sie eine Speicheroptimierte Dateigruppe mit zwei Containern: Container 1 auf Laufwerk X und Container 2 auf Laufwerk Y. Da die Zuordnung von Daten-und Änderungsdateien im Round-Robin erfolgt, muss Container 1 nur Datendateien und Container 2 haben nur Änderungsdateien, dies führt zu einer unausgeglichenen Persistenz für Speicher als auch e/a-Vorgänge pro Sekunde, Datendateien im sind erheblich größer als Änderungsdateien. Um die Daten-und Änderungsdateien gleichmäßig auf die Laufwerke X und Y zu verteilen, erstellen Sie vier Container anstelle von zwei aus, und ordnen Sie die ersten beiden Container Laufwerk X und die beiden folgenden Container Laufwerk Y. Mit Round-Robin-Zuordnung werden die erste Datendatei und die erste Änderungsdatei aus Container-1 und Container-2 bzw. zugewiesen werden die Laufwerk X zugeordnet sind. Auf ähnliche Weise wird die nächste Datei von Daten- und Änderungsdateien aus Container-3 und Container-4 die Laufwerk Y zugeordnet sind zugeordnet. Dies ermöglicht die Verteilung von Daten-und Änderungsdateien gleichmäßig über zwei Laufwerken.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
