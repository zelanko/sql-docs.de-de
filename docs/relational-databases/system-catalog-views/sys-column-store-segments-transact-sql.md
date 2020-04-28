---
title: sys. column_store_segments (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b8d476e2f21693254eac5fc4712d53ac854e74ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68140001"
---
# <a name="syscolumn_store_segments-transact-sql"></a>sys.column_store_segments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Gibt eine Zeile für jedes Spalten Segment in einem columnstore--Index zurück. Pro Spalte pro Zeilen Gruppe ist ein Spalten Segment vorhanden. Beispielsweise gibt eine Tabelle mit 10 Zeilen Gruppen und 34 Spalten 340 Zeilen zurück. 
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.|  
|**hobt_id**|**bigint**|ID des Heaps oder B-Struktur-Indexes (hobt) für die Tabelle, die diesen columnstore-Index aufweist.|  
|**column_id**|**int**|ID der columnstore-Spalte.|  
|**segment_id**|**int**|ID der Zeilen Gruppe. Aus Gründen der Abwärtskompatibilität wird der Spaltenname weiterhin segment_id aufgerufen, obwohl dies die Zeilen Gruppen-ID ist. Sie können ein Segment mit \<hobt_id, partition_id column_id> <segment_id> eindeutig identifizieren.|  
|**version**|**int**|Die Version des Spaltensegmentformats.|  
|**encoding_type**|**int**|Codierungstyp, der für dieses Segment verwendet wird:<br /><br /> 1 = VALUE_BASED-nicht-Zeichenfolge/Binärdatei ohne Wörterbuch (sehr ähnlich wie 4 mit einigen internen Variationen)<br /><br /> 2 = VALUE_HASH_BASED-nicht-Zeichenfolge/binäre Spalte mit allgemeinen Werten im Wörterbuch<br /><br /> 3 = STRING_HASH_BASED Zeichenfolge/binäre Spalte mit allgemeinen Werten im Wörterbuch<br /><br /> 4 = STORE_BY_VALUE_BASED-keine Zeichenfolge/Binärdatei ohne Wörterbuch<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED Zeichenfolge/Binärdatei ohne Wörterbuch<br /><br /> Alle Codierungen nutzen, wenn möglich, die bitkomprimierung und die Codierung der Lauf Länge.|  
|**row_count**|**int**|Die Anzahl der Zeilen in der Zeilengruppe.|  
|**has_nulls**|**int**|1, wenn das Spaltensegment NULL-Werte enthält.|  
|**base_id**|**bigint**|Die Basiswert-ID, wenn Codierungstyp 1 verwendet wird.  Wenn Codierungstyp 1 nicht verwendet wird, wird base_id auf-1 festgelegt.|  
|**magnitude**|**float**|Größe, wenn Codierungstyp 1 verwendet wird.  Wenn Codierungstyp 1 nicht verwendet wird, wird die Größe auf-1 festgelegt.|  
|**primary_dictionary_id**|**int**|Der Wert 0 steht für das globale Wörterbuch. Der Wert-1 gibt an, dass für diese Spalte kein globales Wörterbuch erstellt wurde.|  
|**secondary_dictionary_id**|**int**|Ein Wert ungleich 0 (null) verweist auf das lokale Wörterbuch für diese Spalte im aktuellen Segment (d. h. die Zeilen Gruppe). Der Wert-1 gibt an, dass kein lokales Wörterbuch für dieses Segment vorhanden ist.|  
|**min_data_id**|**bigint**|Die minimale Daten-ID im Spaltensegment.|  
|**max_data_id**|**bigint**|Die maximale Daten-ID im Spaltensegment.|  
|**null_value**|**bigint**|Ein Wert, der zum Darstellen von NULL-Werten verwendet wird.|  
|**on_disk_size**|**bigint**|Die Größe des Segments in Byte.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die folgende Abfrage gibt Informationen zu Segmenten eines columnstore-Indexes zurück.  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>Berechtigungen  
 Alle Spalten erfordern mindestens die **View Definition** -Berechtigung für die Tabelle. Die folgenden Spalten geben NULL zurück, es sei denn, der Benutzer verfügt auch über die **Select** -Berechtigung: has_nulls, base_id, Magnitude, min_data_id, max_data_id und null_value.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys. Columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys. ALL_COLUMNS &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys. computed_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Leitfaden für columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

