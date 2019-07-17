---
title: Sys.dm_db_page_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_page_info
- sys.dm_db_page_info_TSQL
- dm_db_page_info
- dm_db_page_info_TSQL
- dbcc page
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_page_info dynamic management view
author: bluefooted
ms.author: pamela
manager: amitban
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 31b1a282e6d68bf9a31f26536926f9dccd4ff6de
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263825"
---
# <a name="sysdmdbpageinfo-transact-sql"></a>sys.dm_db_page_info (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssver15-asdb-xxxx-xxx.md)]

Gibt Informationen zu einer Seite in einer Datenbank zurück.  Die Funktion gibt eine Zeile mit den Headerinformationen auf der Seite, einschließlich der `object_id`, `index_id`, und `partition_id`.  Dank dieser Funktion ist die Verwendung von `DBCC PAGE` in den meisten Fällen nicht mehr erforderlich.

## <a name="syntax"></a>Syntax   
```  
sys.dm_db_page_info ( DatabaseId, FileId, PageId, Mode )  
``` 

## <a name="arguments"></a>Argumente  
*DatabaseId* | NULL | STANDARDWERT     
Ist die ID der Datenbank. *DatabaseId* ist **Smallint**. Gültige Eingabe ist die ID einer Datenbank. Der Standardwert ist NULL, senden jedoch, dass ein NULL-Wert für diesen Parameter zu einem Fehler führt.
 
*FileId* | NULL | STANDARDWERT   
Die ID der Datei. *FileId* ist **Int**.  Gültige Eingabe ist die ID einer Datei in der Datenbank durch *DatabaseId*. Der Standardwert ist NULL, senden jedoch, dass ein NULL-Wert für diesen Parameter zu einem Fehler führt.

*PageId* | NULL | STANDARDWERT   
Ist die ID der Seite.  *PageId* ist **Int**.  Gültige Eingabe ist die ID einer Seite in der angegebenen Datei *FileId*. Der Standardwert ist NULL, senden jedoch, dass ein NULL-Wert für diesen Parameter zu einem Fehler führt.

*Modus* | NULL | STANDARDWERT   
Bestimmt die Detailebene in der Ausgabe der Funktion. "Begrenzt" wird für alle Beschreibung Spalten NULL-Werte zurückgeben, "Detaillierte" füllt Beschreibung Spalten.  Der Standardwert ist "Eingeschränkt".

## <a name="table-returned"></a>Zurückgegebene Tabelle  

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|database_id |ssNoversion |Datenbank-ID |
|file_id |ssNoversion |Datei-ID |
|page_id |ssNoversion |Seiten-ID |
|page_type |ssNoversion |Seitentyp |
|page_type_desc |Nvarchar(64) |Beschreibung der Seitentyp |
|page_flag_bits |Nvarchar(64) |Flagbits im Seitenkopf |
|page_flag_bits_desc |nvarchar(256) |Beschreibung des Flags Bits im Seitenkopf |
|page_type_flag_bits |Nvarchar(64) |Geben Sie im Seitenkopf Flagbits |
|page_type_flag_bits_desc |Nvarchar(64) |Bits-Flag Beschreibung im Seitenkopf |
|object_id |ssNoversion |ID des Objekts, das die Seite besitzt |
|index_id |ssNoversion |Die ID des Indexes (0 für Heap von Datenseiten) |
|partition_id |BIGINT |ID der partition |
|alloc_unit_id |BIGINT |ID der Zuordnungseinheit |
|page_level |ssNoversion |Auf der Seite im Index (Blatt = 0) |
|slot_count |SMALLINT |Gesamte Anzahl von Einschubfächern (verwendeten und nicht verwendeten) <br> Für eine Datenseite entspricht diese Zahl die Anzahl der Zeilen. |
|ghost_rec_count |SMALLINT |Anzahl der Datensätze, die als inaktiv, auf der Seite markiert <br> Ein inaktiver Datensatz ist eine, die zum Löschen gekennzeichnet wurde, aber noch nicht entfernt werden soll. |
|torn_bits |ssNoversion |1 Bit pro Sektor für die Erkennung von zerrissenen Seiten schreibt. Auch verwendet, um die Prüfsumme zu speichern. <br> Dieser Wert wird verwendet, um datenbeschädigung zu erkennen. |
|is_iam_pg |bit |Bit, um anzugeben, und zwar unabhängig davon, ob die Seite einer IAM-Seite ist.  |
|is_mixed_ext |bit |Um anzugeben, wenn zugeordnete Bit, in einen gemischten Block |
|pfs_file_id |SMALLINT |Datei-ID der entsprechenden PFS-Seite |
|pfs_page_id |ssNoversion |Seiten-ID der entsprechenden PFS-Seite |
|pfs_alloc_percent |ssNoversion |PFS-Bytes durch Zuweisung in Prozent |
|pfs_status |Nvarchar(64) |PFS-Bytes |
|pfs_status_desc |Nvarchar(64) |Beschreibung der PFS-Bytes |
|gam_file_id |SMALLINT |Datei-ID der entsprechenden GAM-Seite |
|gam_page_id |ssNoversion |Seiten-ID der entsprechenden GAM-Seite |
|gam_status |bit |Bit um anzugeben, wenn in der GAM zugeordnet |
|gam_status_desc |Nvarchar(64) |Beschreibung für das GAM-Bit-status |
|sgam_file_id |SMALLINT |Datei-ID der entsprechenden SGAM-Seite |
|sgam_page_id |ssNoversion |Seiten-ID der entsprechenden SGAM-Seite |
|sgam_status |bit |Bit um anzugeben, wenn in der SGAM zugeordnet |
|sgam_status_desc |Nvarchar(64) |Beschreibung der SGAM-Bit-status |
|diff_map_file_id |SMALLINT |Datei-ID der entsprechenden differenzielles Bitmuster-Seite |
|diff_map_page_id |ssNoversion |Seiten-ID der entsprechenden differenzielles Bitmuster-Seite |
|diff_status |bit |Bit, um anzugeben, ob die Diff-Status geändert wird |
|diff_status_desc |Nvarchar(64) |Beschreibung des Diff-Status-Bits |
|ml_file_id |SMALLINT |Datei-ID der entsprechenden minimale Protokollierung Bitmap-Seite |
|ml_page_id |ssNoversion |Seiten-ID der entsprechenden minimale Protokollierung Bitmap-Seite |
|ml_status |bit |Bit, um anzugeben, ob die Seite minimal protokolliert wird |
|ml_status_desc |Nvarchar(64) |Beschreibung des Status die minimale Protokollierung bit |
|free_bytes |SMALLINT |Anzahl freier Bytes auf der Seite |
|free_data_offset |ssNoversion |Offset des freien Speicherplatzes am Ende des Datenbereich |
|reserved_bytes |SMALLINT |Anzahl freier Bytes, die durch alle Transaktionen reserviert (wenn Heap) <br> Anzahl der inaktive Zeilen (sofern es sich um eine Index Blattelemente) |
|reserved_xdes_id |SMALLINT |Speicherplatz von M_xdesID zu M_reservedCnt beigetragenen <br> Nur zu Debugzwecken |
|xdes_id |Nvarchar(64) |Aktuelle Transaction von M_reserved beigetragenen <br> Nur zu Debugzwecken |
|prev_page_file_id |SMALLINT |Vorherige Seite-Datei-ID |
|prev_page_page_id |ssNoversion |Vorherige Seite-Seiten-ID |
|next_page_file_id |SMALLINT |Nächste Seite von Datei-ID |
|next_page_page_id |ssNoversion |Nächste Seite der Seiten-ID |
|MIN_LEN |SMALLINT |Länge der Zeilen mit fester Größe |
|lsn |Nvarchar(64) |Log Sequence Number, / Zeitstempel |
|header_version |ssNoversion |Seite-Headerversion |

## <a name="remarks"></a>Hinweise
Die `sys.dm_db_page_info` dynamische Verwaltungsfunktion gibt Informationen wie `page_id`, `file_id`, `index_id`, `object_id` usw., die in einem Seitenkopf vorhanden sind. Diese Informationen sind hilfreich für die Problembehandlung und Debuggen von verschiedenen Leistung (Sperren und Latchwartevorgänge-Konflikt) und Probleme durch Beschädigungen behandelt.

`sys.dm_db_page_info` kann verwendet werden, anstelle von der `DBCC PAGE` -Anweisung in vielen Fällen, aber es gibt nur die Seite Headerinformationen, nicht den Text der Seite zurück. `DBCC PAGE` wird für Anwendungsfälle weiterhin benötigt, wenn der gesamte Inhalt der Seite erforderlich sind.

## <a name="using-in-conjunction-with-other-dmvs"></a>Verwendung in Verbindung mit anderen DMVs
Der wichtige Anwendungsfälle von `sys.dm_db_page_info` besteht darin, es mit anderen DMVs einzubinden, die Informationen verfügbar machen.  Um diesen Anwendungsfall zu ermöglichen, eine neue Spalte namens `page_resource` der Informationen in einem 8-Byte-hex-Format verfügbar macht hinzugefügt wurde. Diese Spalte wurde zu `sys.dm_exec_requests` und `sys.sysprocesses` und andere DMVs in der Zukunft nach Bedarf hinzugefügt.

Eine neue Funktion, `sys.fn_PageResCracker`, dauert die `page_resource` als Eingabe und gibt eine einzelne Zeile, die enthält `database_id`, `file_id` und `page_id`.  Diese Funktion kann dann verwendet werden, um die Joins zwischen zu vereinfachen `sys.dm_exec_requests` oder `sys.sysprocesses` und `sys.dm_db_page_info`.

## <a name="permissions"></a>Berechtigungen  
Erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-displaying-all-the-properties-of-a-page"></a>A. Alle Eigenschaften einer Seite anzeigen
Die folgende Abfrage gibt eine Zeile mit den Seiteninformationen für einen bestimmten `database_id`, `file_id`, `page_id` zusammen mit der Standardmodus ("begrenzt")

```sql
SELECT *  
FROM sys.dm_db_page_info (5, 1, 15, DEFAULT)
```

### <a name="b-using-sysdmdbpageinfo-with-other-dmvs"></a>B. Verwenden sys.dm_db_page_info mit anderen DMVs 

Die folgende Abfrage gibt eine Zeile pro `wait_resource` von verfügbar gemachten `sys.dm_exec_requests` Wenn die Zeile eine Wert ungleich Null enthält `page_resource`

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 'LIMITED') AS page_info
```

## <a name="see-also"></a>Siehe auch  
[Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)     
[sys.fn_PageResCracker](../../relational-databases/system-functions/sys-fn-pagerescracker-transact-sql.md)


