---
title: Die speicheroptimierte Dateigruppe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/19/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 64402f73fdf43c0ebcbeff338ed72d56d55227be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63155575"
---
# <a name="the-memory-optimized-filegroup"></a>Die speicheroptimierte Dateigruppe
  Um speicheroptimierte Tabellen zu erstellen, müssen Sie zuerst eine speicheroptimierte Dateigruppe erstellen. Die speicheroptimierte Dateigruppe enthält mindestens einen Container. Jeder Container enthält Datendateien oder Änderungsdateien oder sowohl als auch.  
  
 Obwohl Datenzeilen aus `SCHEMA_ONLY`-Tabellen nicht beibehalten werden und die Metadaten für speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren in herkömmlichen Katalogen gespeichert werden, ist für die [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Engine weiterhin eine speicheroptimierte Dateigruppe erforderlich, damit die Behandlung speicheroptimierter `SCHEMA_ONLY`-Tabellen für Datenbanken mit speicheroptimierten Tabellen konsistent ist.  
  
 Die speicheroptimierte Dateigruppe basiert auf Filestream-Dateigruppen, von denen sie sich in folgenden Punkten unterscheidet:  
  
-   Sie können nur eine speicheroptimierte Dateigruppe pro Datenbank erstellen. Sie müssen die Dateigruppe explizit als Container für aus memory_optimized_data markieren. Sie können die Dateigruppe erstellen, wenn Sie die Datenbank erstellen, oder Sie können sie später hinzufügen:  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   Sie müssen der MEMORY_OPTIMIZED_DATA-Dateigruppe mindestens einen Container hinzufügen. Beispiel:  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   Es ist nicht erforderlich, Filestream zu aktivieren ([Aktivieren und Konfigurieren von FILESTREAM](../blob/enable-and-configure-filestream.md)), um eine speicheroptimierte Dateigruppe zu erstellen. Die Zuordnung zu Filestream wird über die [!INCLUDE[hek_2](../../includes/hek-2-md.md)]-Engine ausgeführt.  
  
-   Sie können einer speicheroptimierten Dateigruppe neue Container hinzufügen. Möglicherweise benötigen Sie einen neuen Container, um den Speicher zu erweitern, der für die dauerhafte Speicher optimierte Tabelle benötigt wird, sowie für die Verteilung von e/a über mehrere Container.  
  
-   Die Datenverschiebung mit einer speicheroptimierten Dateigruppe ist in einer AlwaysOn-Verfügbarkeitsgruppenkonfiguration optimiert. Im Gegensatz zu Filestream-Dateien, die an sekundäre Replikate gesendet werden, werden die Prüfpunktdateien (Daten und Änderungen) in der speicheroptimierten Dateigruppe nicht an die sekundären Replikate gesendet. Die Daten- und Änderungsdateien werden mithilfe des Transaktionsprotokolls für das sekundäre Replikat erstellt.  
  
Beachten Sie die folgenden Einschränkungen der speicheroptimierten Dateigruppe:  
  
-   Sobald Sie eine speicheroptimierte Dateigruppe erstellt haben, können Sie sie nur entfernen, indem Sie die Datenbank löschen. In einer Produktionsumgebung müssen Sie die speicheroptimierte Dateigruppe wahrscheinlich nicht entfernen.  
  
-   Sie können einen nicht leeren Container nicht löschen und Daten- und Änderungsdateipaare nicht in einen anderen Container in der speicheroptimierten Dateigruppe verschieben.  
  
## <a name="configuring-a-memory-optimized-filegroup"></a>Konfigurieren einer speicheroptimierten Dateigruppe  
Erwägen Sie, mehrere Container in der speicheroptimierten Dateigruppe zu erstellen und auf unterschiedliche Laufwerke zu verteilen, um beim Streamen der Daten in den Arbeitsspeicher eine höhere Bandbreite zu erzielen.  
  
Wenn Sie den Speicher konfigurieren, müssen Sie freien Speicherplatz bereitstellen, der viermal so groß wie die dauerhaften speicheroptimierten Tabellen ist. Stellen Sie sicher, dass das e/a-Subsystem die erforderlichen IOPS für die Arbeitsauslastung unterstützt. Wenn Daten- und Änderungsdateipaare bei bestimmten IOPS aufgefüllt werden, benötigen Sie dreimal so viel IOPS, um Speicher- und Zusammenführungsvorgänge zu berücksichtigen. Sie können Speicherkapazität und IOPS hinzufügen, indem Sie einen oder mehrere Container zur speicheroptimierten Dateigruppe hinzufügen.  
  
In einem Szenario mit mehreren Containern und mehreren Laufwerken werden Daten- und Änderungsdateien im Round-Robin-Verfahren den Containern zugewiesen. Die erste Datendatei wird aus dem ersten Container zugewiesen, und die Änderungsdatei wird aus dem nächsten Container zugewiesen. Dieses Zuordnungsmuster wird wiederholt. Bei diesem Zuordnungsschema werden Daten- und Änderungsdateien gleichmäßig auf Container verteilt, wenn Sie über eine ungerade Zahl von Laufwerken verfügen, die jeweils einem Container zugeordnet sind. Wenn Sie jedoch über eine gerade Anzahl von Laufwerken verfügen, die jeweils einem Container zugeordnet sind, kann dies zu einer unausgeglichenen Speicherung führen, bei der Datendateien ungeraden Laufwerken und Änderungsdateien geraden Laufwerken zugeordnet werden. Um bei der Wiederherstellung einen ausgeglichenen e/a-Datenstrom zu erhalten, sollten Sie in Erwägung ziehen, Paare von Daten-und Änderungs Dateien in denselben Spindeln/Speicher zu platzieren, wie im folgenden Beispiel beschrieben.  

> [!CAUTION]
> Wenn ein `MAXSIZE`-Wert für die speicheroptimierte Dateigruppe festgelegt wird und Prüfpunktdateien die maximale Größe des Containers überschreiten, ändert sich der Zustand der Datenbank in SUSPECT.   
> Versuchen Sie in diesem Fall nicht, die Datenbank OFFLINE und ONLINE zu schalten, damit die Datenbank im Zustand RECOVERY_PENDING bleibt.
  
### <a name="example"></a>Beispiel 
Angenommen, Sie verfügen über eine speicheroptimierte Dateigruppe mit den beiden Containern Container 1 auf Laufwerk X und Container 2 auf Laufwerk Y.  
Da die Zuordnung von Daten- und Änderungsdateien im Round-Robin-Verfahren erfolgt, enthält Container 1 nur Datendateien und Container 2 nur Änderungsdateien. Dies führt zu einer unausgeglichenen Persistenz sowie zu unausgeglichenen Eingabe/Ausgabe-Vorgängen pro Sekunde, da Datendateien deutlich größer als Änderungsdateien sind.    
Wenn Sie Daten-und Änderungs Dateien gleichmäßig auf die Laufwerke X und Y verteilen möchten, erstellen Sie vier Container anstelle von zwei, und ordnen Sie die ersten beiden Container dem Laufwerk x und den nächsten zwei Containern zu, um Y zu verwenden.  
Bei der Roundrobin-Zuordnung werden die ersten Daten und die erste Delta Datei aus Container-1 bzw. Container-2 zugeordnet, die Laufwerk X zugeordnet sind.   
Ebenso werden die nächste Daten-und Änderungsdatei aus Container-3 und Container-4 zugeordnet, die Laufwerk Y zugeordnet sind. Dadurch können Daten und Delta Dateien gleichmäßig auf zwei Laufwerke verteilt werden.  
 
  
## <a name="see-also"></a>Weitere Informationen  
[Erstellen und Verwalten von Speicher für Speicher optimierte Objekte](creating-and-managing-storage-for-memory-optimized-objects.md)     
[Datenbankdateien und Dateigruppen](../../relational-databases/databases/database-files-and-filegroups.md)    
  
