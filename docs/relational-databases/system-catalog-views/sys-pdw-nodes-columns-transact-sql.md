---
title: sys. pdw_nodes_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 268c77b7-1d71-4197-a2ed-5e2b2b8fc260
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 201af9001703bb8f1dfbdaf2c41151697b945df3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68059401"
---
# <a name="syspdw_nodes_columns-transact-sql"></a>sys. pdw_nodes_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Zeigt Spalten für benutzerdefinierte Tabellen und benutzerdefinierte Sichten an.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Die ID des Objekts, zu dem diese Spalte gehört.||  
|Name|**sysname**|Name der Spalte. Eindeutig im Objekt.||  
|column_id|**int**|ID der Spalte. Eindeutig im Objekt.||  
|system_type_id|**tinyint**|ID des System Typs der Spalte.||  
|user_type_id|**int**|Die ID des vom Benutzer definierten Typs der Spalte.||  
|max_length|**smallint**|Maximale Länge (in Byte) für die Spalte.|Enthält-1 (ungültig) für nicht unterstützte Spaltentypen.|  
|precision|**tinyint**|Die Genauigkeit der Spalte, wenn sie auf numerischen Werten basiert; andernfalls 0.||  
|Skalierung|**tinyint**|Die Skalierung der Spalte, wenn sie auf numerischen Werten basiert; andernfalls 0.||  
|collation_name|**sysname**|Name der Sortierung der Spalte, wenn diese zeichenbasiert ist, andernfalls NULL.||  
|is_nullable|**bit**|1 = Spalte lässt NULL-Werte zu.||  
|is_ansi_padded|**bit**|1 = Spalte verwendet ANSI_PADDING ON-Verhalten, wenn es sich um Zeichen- oder Binärdaten bzw. Daten vom Typ Variant handelt.|Immer 0.|  
|is_rowguidcol|**bit**|1 = Spalte ist eine deklarierte ROWGUIDCOL.|Immer 0.|  
|is_identity|**bit**|1 = Spalte verfügt über Identitätswerte.|Immer 0.|  
|is_computed|**bit**|1 = Spalte ist eine berechnete Spalte.|Immer 0.|  
|is_filestream|**bit**|1 = Spalte ist eine FILESTREAM-Spalte.|Immer 0.|  
|is_replicated|**bit**|1 = Spalte wird repliziert.|Immer 0.|  
|is_non_sql_subscribed|**bit**|1 = die Spalte hat einen nicht-SQL-Abonnenten.|Immer 0.|  
|is_merge_published|**bit**|1 = Spalte verwendet die Mergeveröffentlichung.|Immer 0.|  
|is_dts_replicated|**bit**|1 = die Spalte wird mithilfe von SSIS repliziert.|Immer 0.|  
|is_xml_document|**bit**|1 = Der Inhalt ist ein vollständiges XML-Dokument.|Immer 0.|  
|xml_collection_id|**int**|0 = Keine XML-Schemaauflistung|Immer 0.|  
|default_object_id|**int**|ID des Standard Objekts. 0 = kein Standardwert.|Immer 0.|  
|rule_object_id|**int**|ID der eigenständigen Regel, die an die Spalte gebunden ist. <br />0 = Keine eigenständige Regel.|Immer 0.|  
|is_sparse|**bit**|1 = Spalte ist eine Sparsespalte.|Immer 0.|  
|is_column_set|**bit**|1 = Spalte ist ein Spaltensatz.|Immer 0.|  
|pdw_node_id|**int**|Eindeutiger Bezeichner [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] eines Knotens.|NOT NULL|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse- und Parallel Data Warehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys. ALL_COLUMNS &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)  
  
  
