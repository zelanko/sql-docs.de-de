---
title: Sys.Columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.columns_TSQL
- sys.columns
- columns_TSQL
- columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.columns catalog view
ms.assetid: 323ac9ea-fc52-4b8c-8a7e-e0e44f8ed86c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c028fe9a09ad1f0f0da06a75f8ac7e0cc02b8095
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62668968"
---
# <a name="syscolumns-transact-sql"></a>sys.columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jede Spalte eines Objekts zurück, das Spalten besitzt, z. B. Sichten oder Tabellen. Im Folgenden finden Sie eine Liste der Objekttypen mit Spalten:  
  
-   Assembly-Tabellenwertfunktionen (FT)  
  
-   Inline-SQL-Tabellenwertfunktionen (IF)  
  
-   Interne Tabellen (IT)  
  
-   Systemtabellen (S)  
  
-   SQL-Tabellenwertfunktionen (TF)  
  
-   Benutzertabellen (U)  
  
-   Sichten (V)  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|Die ID des Objekts, zu dem diese Spalte gehört.|  
|NAME|**sysname**|Der Name der Spalte. Ist eindeutig innerhalb des Objekts.|  
|column_id|**int**|ID der Spalte. Ist eindeutig innerhalb des Objekts.<br /><br /> Spalten-IDs sind möglicherweise nicht sequenziell.|  
|system_type_id|**tinyint**|Die ID des Systemtyps der Spalte.|  
|user_type_id|**int**|Die ID des vom Benutzer definierten Typs der Spalte.<br /><br /> Stellen Sie einen Join mit der [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) -Katalogsicht für diese Spalte her, um den Namen des Typs zurückzugeben.|  
|max_length|**smallint**|Maximale Länge (in Byte) für die Spalte.<br /><br /> -1 = Spaltendatentyp ist **varchar(max)** , **nvarchar(max)** , **'varbinary(max)'** , oder **Xml**.<br /><br /> Für **Text** Spalten 16 oder dem durch Sp_tableoption 'Text in Row' festgelegten Wert, wird der Max_length-Wert sein.|  
|precision|**tinyint**|Die Genauigkeit der Spalte, wenn sie auf numerischen Werten basiert; andernfalls 0.|  
|scale|**tinyint**|Die Skalierung der Spalte, wenn sie auf numerischen Werten basiert; andernfalls 0.|  
|collation_name|**sysname**|Der Name der Sortierung der Spalte, wenn Sie zeichenbasierte; andernfalls NULL.|  
|is_nullable|**bit**|1 = Spalte lässt NULL-Werte zu.|  
|is_ansi_padded|**bit**|1 = Spalte verwendet ANSI_PADDING ON-Verhalten, wenn es sich um Zeichen- oder Binärdaten bzw. Daten vom Typ Variant handelt.<br /><br /> 0 = Bei der Spalte handelt es sich um Zeichen- oder Binärdaten bzw. Daten vom Typ Variant.|  
|is_rowguidcol|**bit**|1 = Spalte ist eine deklarierte ROWGUIDCOL.|  
|is_identity|**bit**|1 = Die Spalte verfügt über Identitätswerte.|  
|is_computed|**bit**|1 = Spalte ist eine berechnete Spalte.|  
|is_filestream|**bit**|1 = Spalte ist eine FILESTREAM-Spalte.|  
|is_replicated|**bit**|1 = Spalte wird repliziert.|  
|is_non_sql_subscribed|**bit**|1 = Die Spalte hat einen Nicht-SQL Server-Abonnenten.|  
|is_merge_published|**bit**|1 = Spalte verwendet die Mergeveröffentlichung.|  
|is_dts_replicated|**bit**|1 = Die Spalte wird mithilfe von [!INCLUDE[ssIS](../../includes/ssis-md.md)] repliziert.|  
|is_xml_document|**bit**|1 = Der Inhalt ist ein vollständiges XML-Dokument.<br /><br /> 0 = Inhalt ist ein Dokumentfragment, oder der Spaltendatentyp ist nicht **Xml**.|  
|xml_collection_id|**int**|Ungleich NULL, wenn der Datentyp der Spalte **Xml** und XML typisiert ist. Der Wert entspricht der ID der Auflistung, die den prüfenden XML-Schemanamespace der Spalte enthält.<br /><br /> 0 = Keine XML-Schemaauflistung|  
|default_object_id|**int**|ID des Standardobjekts, unabhängig davon, ob es ein eingeständiges Objekt [Sys. sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md), oder eine Inline, DEFAULT-Einschränkung auf Spaltenebene. Die parent_object_id-Spalte eines DEFAULT-Inlineobjekts ist ein Verweis auf die Tabelle selbst.<br /><br /> 0 = Kein Standard.|  
|rule_object_id|**int**|ID der eigenständigen Regel, die mithilfe von sys.sp_bindrule gebunden wird.<br /><br /> 0 = Keine eigenständige Regel. CHECK-Einschränkungen auf Spaltenebene finden Sie unter [Sys. check_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md).|  
|is_sparse|**bit**|1 = Spalte ist eine Sparsespalte. Weitere Informationen finden Sie unter [Verwenden von Spalten mit geringer Dichte](../../relational-databases/tables/use-sparse-columns.md).|  
|is_column_set|**bit**|1 = Spalte ist ein Spaltensatz. Weitere Informationen finden Sie unter [Verwenden von Spalten mit geringer Dichte](../../relational-databases/tables/use-sparse-columns.md).|  
|generated_always_type|**tinyint**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Gibt an, wann der Spaltenwert generiert wird (werden immer 0 für-Spalten in Systemtabellen):<br /><br /> 0 = NOT_APPLICABLE<br /><br /> 1 = AS_ROW_START<br /><br /> 2 = AS_ROW_END<br /><br /> Weitere Informationen finden Sie unter [temporale Tabellen &#40;relationale Datenbanken&#41;](../../relational-databases/tables/temporal-tables.md).|  
|generated_always_type_desc|**nvarchar(60)**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Textbeschreibung des `generated_always_type`Wert (immer NOT_APPLICABLE für Spalten in Systemtabellen) <br /><br /> NOT_APPLICABLE<br /><br /> AS_ROW_START<br /><br /> AS_ROW_END|  
|encryption_type|**int**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Verschlüsselungstyp:<br /><br /> 1 = die deterministische Verschlüsselung<br /><br /> 2 = zufällige Verschlüsselung|  
|encryption_type_desc|**nvarchar(64)**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Beschreibung des Verschlüsselung:<br /><br /> ZUFÄLLIGE<br /><br /> DETERMINISTIC|  
|encryption_algorithm_name|**sysname**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Der Name des Verschlüsselungsalgorithmus.<br /><br /> Nur AEAD_AES_256_CBC_HMAC_SHA_512 wird unterstützt.|  
|column_encryption_key_id|**int**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Die ID des CEK.|  
|column_encryption_key_database_name|**sysname**|**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDW_md](../../includes/sssds-md.md)].<br /><br /> Der Name der Datenbank, in dem der spaltenverschlüsselungsschlüssel, wenn sich die Datenbank der Spalte vorhanden ist. NULL, wenn der Schlüssel in der gleichen Datenbank wie die Spalte vorhanden ist.|  
|is_hidden|**bit**|**Gilt für**: [!INCLUDE[ssCurrentLong](../../includes/sscurrent-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Gibt an, wenn die Spalte ausgeblendet ist:<br /><br /> 0 = reguläre, nicht ausgeblendeten, sichtbare Spalte<br /><br /> 1 = die ausgeblendete Spalte|  
|is_masked|**bit**|**Gilt für**: [!INCLUDE[ssCurrentLong](../../includes/sscurrent-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].<br /><br /> Gibt an, ob durch eine dynamische datenmaskierung für die Spalte maskiert ist:<br /><br /> 0 = reguläre, nicht maskiert Spalte<br /><br /> 1 = Spalte ist maskiert.|  


 
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Systemsichten &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)  
  
  
