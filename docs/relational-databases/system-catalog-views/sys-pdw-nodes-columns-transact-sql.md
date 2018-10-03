---
title: Sys.pdw_nodes_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 268c77b7-1d71-4197-a2ed-5e2b2b8fc260
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7b811bb94039974faa8c145ef93df92949fbd702
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47714908"
---
# <a name="syspdwnodescolumns-transact-sql"></a>Sys.pdw_nodes_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Zeigt die Spalten für benutzerdefinierte Tabellen und benutzerdefinierten Ansichten.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|Die ID des Objekts, zu dem diese Spalte gehört.||  
|NAME|**sysname**|Der Name der Spalte. Eindeutig im-Objekt.||  
|column_id|**int**|ID der Spalte. Eindeutig im-Objekt.||  
|system_type_id|**tinyint**|Die ID des Systemtyps der Spalte.||  
|user_type_id|**int**|Die ID des vom Benutzer definierten Typs der Spalte.||  
|max_length|**smallint**|Maximale Länge (in Byte) für die Spalte.|Umfasst 1, die nicht unterstützten Spaltentypen (ungültig).|  
|precision|**tinyint**|Die Genauigkeit der Spalte, wenn sie auf numerischen Werten basiert; andernfalls 0.||  
|scale|**tinyint**|Die Skalierung der Spalte, wenn sie auf numerischen Werten basiert; andernfalls 0.||  
|collation_name|**sysname**|Der Name der Sortierung der Spalte, wenn Sie zeichenbasierte; andernfalls NULL.||  
|is_nullable|**bit**|1 = Spalte lässt NULL-Werte zu.||  
|is_ansi_padded|**bit**|1 = Spalte verwendet ANSI_PADDING ON-Verhalten, wenn es sich um Zeichen- oder Binärdaten bzw. Daten vom Typ Variant handelt.|Immer 0.|  
|is_rowguidcol|**bit**|1 = Spalte ist eine deklarierte ROWGUIDCOL.|Immer 0.|  
|is_identity|**bit**|1 = Spalte verfügt über Identitätswerte.|Immer 0.|  
|is_computed|**bit**|1 = Spalte ist eine berechnete Spalte.|Immer 0.|  
|is_filestream|**bit**|1 = Spalte ist eine FILESTREAM-Spalte.|Immer 0.|  
|is_replicated|**bit**|1 = Spalte wird repliziert.|Immer 0.|  
|is_non_sql_subscribed|**bit**|1 = Spalte weist einen nicht-SQL-Abonnenten.|Immer 0.|  
|is_merge_published|**bit**|1 = Spalte verwendet die Mergeveröffentlichung.|Immer 0.|  
|is_dts_replicated|**bit**|1 = Spalte werden mithilfe von SSIS repliziert.|Immer 0.|  
|is_xml_document|**bit**|1 = Der Inhalt ist ein vollständiges XML-Dokument.|Immer 0.|  
|xml_collection_id|**int**|0 = Keine XML-Schemaauflistung|Immer 0.|  
|default_object_id|**int**|Die ID des Standardobjekts; 0 = kein Standard.|Immer 0.|  
|rule_object_id|**int**|ID der eigenständigen Regel, die an die Spalte gebunden werden. <br />0 = Keine eigenständige Regel.|Immer 0.|  
|is_sparse|**bit**|1 = Spalte ist eine Sparsespalte.|Immer 0.|  
|is_column_set|**bit**|1 = Spalte ist ein Spaltensatz.|Immer 0.|  
|pdw_node_id|**int**|Der eindeutige Bezeichner des eine [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] Knoten.|NOT NULL|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)  
  
  
