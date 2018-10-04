---
title: Sichern einer Datenbank mit speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 83d47694-e56d-4dae-b54e-14945bf8ba31
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4b791f83342d02fb003a14f48861ae992ddc37df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190290"
---
# <a name="backing-up-a-database-with-memory-optimized-tables"></a>Sichern einer Datenbank mit speicheroptimierten Tabellen
  Speicheroptimierte Tabellen werden im Rahmen regelmäßiger Datenbanksicherungen gesichert. Wie bei datenträgerbasierten Tabellen wird die CHECKSUM von Daten-/Änderungsdateipaaren als Teil der Datenbanksicherung überprüft, um Speicherbeschädigungen zu erkennen.  
  
> [!NOTE]  
>  Wenn während einer Sicherung in einer oder mehreren Dateien einer speicheroptimierten Dateigruppe ein CHECKSUM-Fehler auftritt, sind Sie nicht in der Lage, die Datenbank wiederherzustellen und neu zu starten. In diesem Fall müssen Sie die Datenbank mit der letzten als fehlerfrei bekannten Sicherung wiederherstellen. Wenn keine Sicherung verfügbar ist, können Sie die Daten aus den speicheroptimierten und datenträgerbasierten Tabellen exportieren und erneut laden, nachdem Sie die Datenbank gelöscht und neu erstellt haben.  
  
 Eine vollständige Sicherung einer Datenbank mit mindestens einer speicheroptimierten Tabelle besteht aus dem zugeordneten Speicher für datenträgerbasierte Tabellen (falls vorhanden), dem aktiven Transaktionsprotokoll und den Daten-/Änderungsdateipaaren (auch als Prüfpunktdateipaare bezeichnet) für speicheroptimierte Tabellen. Allerdings kann der unter [Dauerhaftigkeit für speicheroptimierte Tabellen](memory-optimized-tables.md)beschriebene, von speicheroptimierten Tabellen genutzte Speicher wesentlich größer als die belegte Arbeitsspeicherkapazität sein, was sich auf die Größe der Datenbanksicherung auswirkt.  
  
## <a name="full-database-backup"></a>Vollständige Datenbanksicherung  
 Diese Erläuterung bezieht sich auf Datenbanksicherungen für Datenbanken, die ausschließlich über dauerhafte speicheroptimierte Tabellen verfügen, da die Sicherung für datenträgerbasierte Tabellen identisch ist. Die Prüfpunktdateipaare in der speicheroptimierten Dateigruppe können unterschiedliche Statusphasen aufweisen. In der folgenden Tabelle wird beschrieben, welcher Teil der Dateien gesichert wird.  
  
|Status des Prüfpunktdateipaars|Sichern|  
|--------------------------------|------------|  
|PRECREATED|Nur Dateimetadaten|  
|UNDER CONSTRUCTION|Nur Dateimetadaten|  
|Active|Dateimetadaten plus verwendete Bytes|  
|Merge source|Dateimetadaten plus verwendete Bytes|  
|Merge target|Nur Dateimetadaten|  
|REQUIRED FOR BACKUP/HA|Dateimetadaten plus verwendete Bytes|  
|IN TRANSITION TO TOMBSTONE|Nur Dateimetadaten|  
|TOMBSTONE|Nur Dateimetadaten|  
  
 Die Größe von Datenbanksicherungen mit einer oder mehreren speicheroptimierten Tabellen liegt in der Regel über deren Größe im Arbeitsspeicher jedoch unter dem auf dem Datenträger belegten Speicherplatz. Die zusätzliche Größe richtet sich nach der Anzahl gelöschter Zeilen und der Anzahl von Prüfpunktdateipaaren mit dem Status Merge sourceund REQUIRED FOR BACKUP/HA, die indirekt von der Arbeitsauslastung abhängt. Beschreibungen der Statusphasen für prüfpunktdateipaare finden Sie [Sys. dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql).  
  
### <a name="estimating-size-of-full-database-backup"></a>Schätzen der Größe einer vollständigen Datenbanksicherung  
  
> [!IMPORTANT]  
>  Es wird empfohlen, den BackupSizeInBytes-Wert nicht zu verwenden, um die Sicherungsgröße für In-Memory OLTP zu schätzen.  
  
 Das erste Arbeitsauslastungsszenario bezieht sich (hauptsächlich) auf Einfügevorgänge. In diesem Szenario weisen die meisten Datendateien den Status ACTIVE und einige wenige gelöschte Zeilen auf und wurden vollständig geladen. Die Größe der Datenbanksicherung entspricht in etwa der Größe der Daten im Arbeitsspeicher.  
  
 Das zweite Arbeitsauslastungsszenario bezieht sich auf häufige Einfüge-, Lösch- und Updatevorgänge: Im ungünstigsten Fall wurde jedes Prüfpunktdateipaar nach Berücksichtigung der gelöschten Zeilen zu 50 % geladen. Daher ist die Datenbanksicherung mindestens zweimal so groß wie die Daten im Arbeitsspeicher. Zusätzlich wächst die Größe der Datenbanksicherung durch einige Prüfpunktdateipaare mit dem Status „Quelle zusammenführen“ und „Für Backup/HA erforderlich“ weiter an.  
  
## <a name="differential-backups-of-databases-with-memory-optimized-tables"></a>Differenzielle Sicherungen von Datenbanken mit speicheroptimierten Tabellen  
 Der Speicher für speicheroptimierte Tabellen setzt sich zusammen aus Daten- und Änderungsdateien, wie in [Dauerhaftigkeit für speicheroptimierte Tabellen](memory-optimized-tables.md)beschrieben. Eine differenzielle Sicherung einer Datenbank mit speicheroptimierten Tabellen enthält die folgenden Daten:  
  
-   Die differenzielle Sicherung für Dateigruppen, in denen datenträgerbasierte Tabellen gespeichert sind, wird durch das Vorhandensein von speicheroptimierten Tabellen nicht beeinflusst.  
  
-   Das aktive Transaktionsprotokoll ist dasselbe wie bei einer vollständigen Datenbanksicherung.  
  
-   Für eine speicheroptimierte Datendateigruppe verwendet die differenzielle Sicherung den gleichen Algorithmus wie bei einer vollständigen Datenbanksicherung, um die Daten- und Änderungsdateien für die Sicherung identifizieren. Anschließend wird wie folgt eine Teilmenge dieser Dateien herausgefiltert:  
  
    -   Eine Datendatei, die neu eingefügte Zeilen enthält und voll ist, wird geschlossen und als schreibgeschützt gekennzeichnet. Eine Datendatei wird nur gesichert, wenn sie nach der letzten vollständigen Datenbanksicherung geschlossen wurde. Die differenzielle Sicherung sichert nur Datendateien, die seit der letzten vollständigen Datenbanksicherung eingefügte Zeilen enthalten, mit Ausnahme von zusammenhängenden Update- und Löschvorgängen, bei denen einige der eingefügten Zeilen möglicherweise schon für die Garbage Collection gekennzeichnet bzw. bereits durch diese gelöscht wurden.  
  
    -   Eine Änderungsdatei speichert Verweise auf die gelöschten Datenzeilen. Da jede zukünftige Transaktion eine Zeile löschen kann, kann eine Änderungsdatei zu jedem Zeitpunkt innerhalb ihrer Lebensdauer geändert werden. Sie wird daher nie geschlossen. Eine Änderungsdatei wird immer gesichert. Änderungsdateien belegen normalerweise weniger als 10 % des Speichers, sodass Änderungsdateien nur eine minimale Auswirkung auf der Größe der differenziellen Sicherung haben.  
  
 Wenn speicheroptimierte Tabellen einen großen Teil der Datenbank ausmachen, kann die Größe der Datenbanksicherung durch die differenzielle Sicherung erheblich reduziert werden.  
  
 Bei typischen OLTP-Arbeitsauslastungen fallen differenzielle Sicherungen wesentlich kleiner als vollständige Datenbanksicherungen aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern und Wiederherstellen speicheroptimierter Tabellen](restore-and-recovery-of-memory-optimized-tables.md)  
  
  
