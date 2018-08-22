---
title: Überwachung und Problembehandlung der Mergereplikation für die Daten- und Änderungsdateien Änderungsdateipaare | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b0bacc-4d2c-42e4-84bf-1a97e0bd385b
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6ab50676145c7a7e68976448c6a89b2dceadb45
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394469"
---
# <a name="monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs"></a>Überwachung und Problembehandlung beim Zusammenführen von Daten-/Änderungsdateipaaren
  In-Memory OLTP verwendet eine Mergerichtlinie, um angrenzende Daten-/Änderungsdateipaare automatisch zusammenzuführen. Sie können die Mergeaktivität nicht deaktivieren.  
  
 Sie können Daten-/Änderungsdateipaare wie folgt überwachen:  
  
-   Vergleichen Sie die speicherintern genutzte Menge mit der Gesamtgröße des Arbeitsspeichers. Wenn die Speichermenge unverhältnismäßig groß ist, ist es wahrscheinlich, dass die Zusammenführung nicht ausgelöst wird. Weitere Informationen  
  
-   Sehen Sie sich den verwendeten Speicherplatz in Daten-und Änderungsdateien [Sys. dm_db_xtp_checkpoint_files &#40;Transact-SQL&#41; ](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql) um festzustellen, ob die Zusammenführung nicht ausgelöst wird, obwohl er es sollte.  
  
## <a name="performing-a-manual-merge"></a>Ausführen einer manuellen Zusammenführung  
 Sie können [sp_xtp_merge_checkpoint_files &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-merge-checkpoint-files-transact-sql) , eine manuelle Zusammenführung auszuführen.  
  
 Verwenden Sie die folgende Abfrage, um Informationen zu den Daten- und Änderungsdateien abzurufen.  
  
```tsql  
select checkpoint_file_id, file_type_desc, internal_storage_slot, file_size_in_bytes, file_size_used_in_bytes,   
inserted_row_count, deleted_row_count, lower_bound_tsn, upper_bound_tsn   
from sys.dm_db_xtp_checkpoint_files  
where state = 1  
order by file_type_desc, upper_bound_tsn  
```  
  
 Wird davon ausgegangen Sie, dass Sie über drei Datendateien gefunden, die nicht zusammengeführt wurden. Mithilfe der `lower_bound_tsn` Wert der ersten Datendatei und die `upper_bound_tsn` von der letzten Datendatei können Sie den folgenden Befehl ausgeben:  
  
```tsql  
exec sys.sp_xtp_merge_checkpoint_files 'H_DB',  12345, 67890  
```  
  
 Angenommen, die drei Daten-/Änderungsdateipaare enthielten jeweils 15.836 Zeilen und 5.279 gelöschte Zeilen. Nach der Zusammenführung enthält die neue Datendatei 31.872 Zeilen und 0 gelöschte Zeilen. Die Größe der neuen Datendatei kann deutlich oberhalb der ursprünglich zugeordneten Größe von 128 MB liegen. Dies liegt daran, dass die Mergerichtlinie durch die manuelle Zusammenführung überschrieben und die Zusammenführung der angeforderten Dateien erzwungen wird.  
  
 Im Blog [Zustand Statusübergang von Prüfpunktdateien in Datenbanken mit speicheroptimierten Tabellen](http://blogs.technet.com/b/dataplatforminsider/archive/2014/01/23/state-transition-of-checkpoint-files-in-databases-with-memory-optimized-tables.aspx) Statusübergang von Daten- / änderungsdateipaaren vom Beginn bis zur Garbagecollection beschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
