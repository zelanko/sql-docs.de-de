---
description: sys. dm_db_log_info (Transact-SQL)
title: sys. dm_db_log_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_log_info
- sys.dm_db_log_info_TSQL
- dm_db_log_info
- dm_db_log_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_log_info dynamic management view
ms.assetid: f6b40060-c17d-472f-b0a3-3b350275d487
author: savjani
ms.author: pariks
manager: ajayj
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: aba965d4a0289db9ef7def58b90f15a1479cb485
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447662"
---
# <a name="sysdm_db_log_info-transact-sql"></a>sys. dm_db_log_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-2016sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2016sp2-asdb-xxxx-xxx-md.md)]

Gibt Informationen zu [virtuellen Protokolldateien (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) des Transaktions Protokolls zurück. Beachten Sie, dass alle Transaktionsprotokoll Dateien in der Tabellenausgabe kombiniert werden. Jede Zeile in der Ausgabe stellt eine VLF im Transaktionsprotokoll dar und enthält Informationen, die für diese VLF im Protokoll relevant sind.

## <a name="syntax"></a>Syntax  
  
```  
sys.dm_db_log_info ( database_id )  
``` 

## <a name="arguments"></a>Argumente  
 *database_id* | NULL | Vorgegebene  
 Die ID der Datenbank. *database_id* ist vom Datentyp **int**. Gültige Eingaben sind die ID einer Datenbank, NULL oder default. Die Standardeinstellung ist NULL. NULL und Default sind äquivalente Werte im Kontext der aktuellen Datenbank.
 
 Geben Sie NULL an, um VLF-Informationen der aktuellen Datenbank zurückzugeben.

 Die integrierte [DB_ID](../../t-sql/functions/db-id-transact-sql.md)-Funktion kann angegeben werden. Wenn Sie `DB_ID` ohne Angabe eines Daten Banknamens verwenden, muss der Kompatibilitäts Grad der aktuellen Datenbank 90 oder größer sein.  

## <a name="table-returned"></a>Zurückgegebene Tabelle  

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|database_id|**int**|Datenbank-ID|
|file_id|**smallint**|Die Datei-ID des Transaktions Protokolls.|  
|vlf_begin_offset|**bigint** |Der Offset Speicherort der [virtuellen Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) ab dem Anfang der Transaktionsprotokoll Datei.|
|vlf_size_mb |**float** |Größe der [virtuellen Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) in MB, auf 2 Dezimalstellen gerundet.|     
|vlf_sequence_number|**bigint** |die Sequenznummer der [virtuellen Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) in der erstellten Reihenfolge. Wird verwendet, um VLFs in der Protokolldatei eindeutig zu identifizieren.|
|vlf_active|**bit** |Gibt an, ob die [virtuelle Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) verwendet wird oder nicht. <br />0-VLF wird nicht verwendet.<br />1-VLF ist aktiv.|
|vlf_status|**int** |Status der [virtuellen Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Folgende Werte sind möglich. <br />0-VLF ist inaktiv. <br />1-VLF ist initialisiert, wird aber nicht verwendet. <br /> 2-VLF ist aktiv.|
|vlf_parity|**tinyint** |Parität der [virtuellen Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch). Wird intern verwendet, um das Ende des Protokolls innerhalb eines VLF zu bestimmen.|
|vlf_first_lsn|**nvarchar (48)** |[Protokoll Sequenznummer (Log Sequence Number, LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) des ersten Protokolldaten Satzes in der [virtuellen Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch).|
|vlf_create_lsn|**nvarchar (48)** |[Protokoll Sequenznummer (Log Sequence Number, LSN)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#Logical_Arch) des Protokolldaten Satzes, von dem die [virtuelle Protokolldatei (VLF)](../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch)erstellt wurde.|
|vlf_encryptor_thumbprint|**varbinary(20)**| **Gilt für:** [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] <br><br> Zeigt den Fingerabdruck der Verschlüsselung der VLF an, wenn die VLF mit [transparent Data Encryption](../../relational-databases/security/encryption/transparent-data-encryption.md)verschlüsselt ist, andernfalls NULL. |

## <a name="remarks"></a>Bemerkungen
Die `sys.dm_db_log_info` dynamische Verwaltungsfunktion ersetzt die- `DBCC LOGINFO` Anweisung.    
 
## <a name="permissions"></a>Berechtigungen  
Erfordert die- `VIEW DATABASE STATE` Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-determing-databases-in-a-sql-server-instance-with-high-number-of-vlfs"></a>A. Determinierung von Datenbanken in einer SQL Server-Instanz mit einer hohen Anzahl von VLFs
Die folgende Abfrage bestimmt die Datenbanken mit mehr als 100 VLFs in den Protokolldateien, die sich auf den Start-, Wiederherstellungs-und Wiederherstellungs Zeitpunkt der Datenbank auswirken können.

```sql
SELECT [name], COUNT(l.database_id) AS 'vlf_count' 
FROM sys.databases s
CROSS APPLY sys.dm_db_log_info(s.database_id) l
GROUP BY [name]
HAVING COUNT(l.database_id) > 100
```

### <a name="b-determing-the-position-of-the-last-vlf-in-transaction-log-before-shrinking-the-log-file"></a>B. Determinierung der Position des letzten `VLF` im Transaktionsprotokoll vor dem Verkleinern der Protokolldatei

Die folgende Abfrage kann verwendet werden, um die Position der letzten aktiven VLF zu ermitteln, bevor SHRINKFILE im Transaktionsprotokoll ausgeführt wird, um zu bestimmen, ob das Transaktionsprotokoll verkleinert werden kann.

```sql
USE AdventureWorks2016
GO

;WITH cte_vlf AS (
SELECT ROW_NUMBER() OVER(ORDER BY vlf_begin_offset) AS vlfid, DB_NAME(database_id) AS [Database Name], vlf_sequence_number, vlf_active, vlf_begin_offset, vlf_size_mb
    FROM sys.dm_db_log_info(DEFAULT)),
cte_vlf_cnt AS (SELECT [Database Name], COUNT(vlf_sequence_number) AS vlf_count,
    (SELECT COUNT(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 0) AS vlf_count_inactive,
    (SELECT COUNT(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS vlf_count_active,
    (SELECT MIN(vlfid) FROM cte_vlf WHERE vlf_active = 1) AS ordinal_min_vlf_active,
    (SELECT MIN(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS min_vlf_active,
    (SELECT MAX(vlfid) FROM cte_vlf WHERE vlf_active = 1) AS ordinal_max_vlf_active,
    (SELECT MAX(vlf_sequence_number) FROM cte_vlf WHERE vlf_active = 1) AS max_vlf_active
    FROM cte_vlf
    GROUP BY [Database Name])
SELECT [Database Name], vlf_count, min_vlf_active, ordinal_min_vlf_active, max_vlf_active, ordinal_max_vlf_active,
((ordinal_min_vlf_active-1)*100.00/vlf_count) AS free_log_pct_before_active_log,
((ordinal_max_vlf_active-(ordinal_min_vlf_active-1))*100.00/vlf_count) AS active_log_pct,
((vlf_count-ordinal_max_vlf_active)*100.00/vlf_count) AS free_log_pct_after_active_log
FROM cte_vlf_cnt
GO
```

## <a name="see-also"></a>Weitere Informationen  
[Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Dynamische Verwaltungs Sichten im Zusammenhang mit der Datenbank &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_db_log_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-space-usage-transact-sql.md)   
[sys.dm_db_log_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-log-stats-transact-sql.md)

