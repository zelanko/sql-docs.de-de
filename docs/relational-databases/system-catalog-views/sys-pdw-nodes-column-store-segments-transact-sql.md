---
title: sys. pdw_nodes_column_store_segments (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 03/28/2018
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
author: julieMSFT
ms.author: jrasnick
manager: jrj
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: bea8e0d51b2918d7280f4afdb8b9d02f6b757827
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401669"
---
# <a name="syspdw_nodes_column_store_segments-transact-sql"></a>sys. pdw_nodes_column_store_segments (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Enthält eine Zeile für jede Spalte in einem columnstore-Index.

| Spaltenname                 | Datentyp  | BESCHREIBUNG                                                  |
| :-------------------------- | :--------- | :----------------------------------------------------------- |
| **partition_id**            | **bigint** | Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.     |
| **hobt_id**                 | **bigint** | ID des Heaps oder B-Struktur-Indexes (hobt) für die Tabelle, die diesen columnstore-Index aufweist. |
| **column_id**               | **int**    | ID der columnstore-Spalte.                                |
| **segment_id**              | **int**    | Die ID des Spaltensegments. Aus Gründen der Abwärtskompatibilität wird der Spaltenname weiterhin segment_id aufgerufen, obwohl dies die Zeilen Gruppen-ID ist. Sie können ein Segment mithilfe <hobt_id, partition_id, column_id>, <segment_id> eindeutig identifizieren. |
| **version**                 | **int**    | Die Version des Spaltensegmentformats.                        |
| **encoding_type**           | **int**    | Codierungstyp, der für dieses Segment verwendet wird:<br /><br /> 1 = VALUE_BASED-keine Zeichenfolge/Binärdatei ohne Wörterbuch (ähnlich wie 4 mit einigen internen Variationen)<br /><br /> 2 = VALUE_HASH_BASED-nicht-Zeichenfolge/binäre Spalte mit allgemeinen Werten im Wörterbuch<br /><br /> 3 = STRING_HASH_BASED Zeichenfolge/binäre Spalte mit allgemeinen Werten im Wörterbuch<br /><br /> 4 = STORE_BY_VALUE_BASED-keine Zeichenfolge/Binärdatei ohne Wörterbuch<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED Zeichenfolge/Binärdatei ohne Wörterbuch<br /><br /> Alle Codierungen nutzen, wenn möglich, die bitkomprimierung und die Codierung der Lauf Länge. |
| **row_count**               | **int**    | Die Anzahl der Zeilen in der Zeilengruppe.                             |
| **has_nulls**               | **int**    | 1, wenn das Spaltensegment NULL-Werte enthält.                     |
| **base_id**                 | **bigint** | Die Basiswert-ID, wenn Codierungstyp 1 verwendet wird.  Wenn Codierungstyp 1 nicht verwendet wird, wird base_id auf 1 festgelegt. |
| **magnitude**               | **float**  | Größe, wenn Codierungstyp 1 verwendet wird.  Wenn Codierungstyp 1 nicht verwendet wird, wird die Größe auf 1 festgelegt. |
| **primary__dictionary_id**  | **int**    | ID des primären Wörterbuchs. Ein Wert ungleich 0 (null) verweist auf das lokale Wörterbuch für diese Spalte im aktuellen Segment (d. h. die Zeilen Gruppe). Der Wert-1 gibt an, dass kein lokales Wörterbuch für dieses Segment vorhanden ist. |
| **secondary_dictionary_id** | **int**    | ID des sekundären Wörterbuchs. Ein Wert ungleich 0 (null) verweist auf das lokale Wörterbuch für diese Spalte im aktuellen Segment (d. h. die Zeilen Gruppe). Der Wert-1 gibt an, dass kein lokales Wörterbuch für dieses Segment vorhanden ist. |
| **min_data_id**             | **bigint** | Die minimale Daten-ID im Spalten Segment.                       |
| **max_data_id**             | **bigint** | Maximale Daten-ID im Spalten Segment.                       |
| **null_value**              | **bigint** | Ein Wert, der zum Darstellen von NULL-Werten verwendet wird.                               |
| **on_disk_size**            | **bigint** | Die Größe des Segments in Byte.                                    |
| **pdw_node_id**             | **int**    | Eindeutiger Bezeichner [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] eines Knotens. |
| &nbsp; | &nbsp; | &nbsp; |

## <a name="examples-sssdwfull-and-sspdw"></a>Beispiele: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] und [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]

Verknüpfen Sie sys. pdw_nodes_column_store_segments mit anderen Systemtabellen, um die Anzahl der columnstore--Segmente pro logischer Tabelle zu ermitteln.

```sql
SELECT  sm.name           as schema_nm
,       tb.name           as table_nm
,       nc.name           as col_nm
,       nc.column_id
,       COUNT(*)          as segment_count
FROM    sys.[schemas] sm
JOIN    sys.[tables] tb                   ON  sm.[schema_id]          = tb.[schema_id]
JOIN    sys.[pdw_table_mappings] mp       ON  tb.[object_id]          = mp.[object_id]
JOIN    sys.[pdw_nodes_tables] nt         ON  nt.[name]               = mp.[physical_name]
JOIN    sys.[pdw_nodes_partitions] np     ON  np.[object_id]          = nt.[object_id]
                                          AND np.[pdw_node_id]        = nt.[pdw_node_id]
                                          AND np.[distribution_id]    = nt.[distribution_id]
JOIN    sys.[pdw_nodes_columns] nc        ON  np.[object_id]          = nc.[object_id]
                                          AND np.[pdw_node_id]        = nc.[pdw_node_id]
                                          AND np.[distribution_id]    = nc.[distribution_id]
JOIN    sys.[pdw_nodes_column_store_segments] rg  ON  rg.[partition_id]         = np.[partition_id]
                                                      AND rg.[pdw_node_id]      = np.[pdw_node_id]
                                                      AND rg.[distribution_id]  = np.[distribution_id]
                                                      AND rg.[column_id]        = nc.[column_id]
GROUP BY    sm.name
,           tb.name
,           nc.name
,           nc.column_id  
ORDER BY    table_nm
,           nc.column_id
,           sm.name ;
```

## <a name="permissions"></a>Berechtigungen

Erfordert die **VIEW SERVER STATE**-Berechtigung.

## <a name="see-also"></a>Weitere Informationen

[SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)  
[sys. pdw_nodes_column_store_row_groups &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
[sys. pdw_nodes_column_store_dictionaries &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)
