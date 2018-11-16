---
title: SchemaEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SchemaEnum
helpviewer_keywords:
- SchemaEnum enumeration [ADO]
ms.assetid: 21c97651-297f-469f-b5b5-c48af72b62a8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c95ec9525fe0890d241fd6a99a6c298f6ef7568e
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603662"
---
# <a name="schemaenum"></a>SchemaEnum
Gibt den Typ des Schemas **Recordset** , die die [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) Methode abgerufen.  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen über die Funktion und die Spalten zurückgegeben, für jede Konstante ADO Sie in Themen finden [Anhang B: Schemarowsets](https://msdn.microsoft.com/2b5fbf03-e50d-44ee-bc57-5a57666c55f1) von der OLE DB Programmer's Reference. Der Name jedes Themas ist in Klammern in den Abschnitt "Beschreibung" der folgenden Tabelle aufgeführt.  
  
 Weitere Informationen über die Funktion und die Spalten zurückgegeben, für jede ADO MD-Konstante Sie in Themen finden [OLE DB für OLAP-Objekten und Schemarowsets](https://msdn.microsoft.com/d20bb2a6-68bd-423f-9ec8-eb930cd0c144) in der OLE DB für Online Analytical Processing (OLAP)-Dokumentation. Der Name jedes Themas ist in Klammern in der Spalte "Beschreibung" in der folgenden Tabelle aufgeführt.  
  
 Sie können die Datentypen der Spalten in der OLE DB-Dokumentation, ADO-Datentypen finden Sie in der Spalte "Beschreibung" von der ADO übersetzen [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) Thema. Z. B. dem OLE DB-Datentyp **DBTYPE_WSTR** ist gleichbedeutend mit dem ADO-Datentyp **AdWChar**.  
  
 ADO-Schema-ähnliche-Ergebnisse für die Konstanten, generiert **AdSchemaDBInfoKeywords** und **AdSchemaDBInfoLiterals**. ADO erstellt eine **Recordset**, und füllt dann jede Zeile, mit der jeweils vom zurückgegebenen Werte den **IDBInfo:: GetKeywords** und **:: GetLiteralInfo** Methoden. Weitere Informationen zu diesen Methoden finden Sie der [IDBInfo](https://msdn.microsoft.com/3f5ad97f-3fc6-4f21-b691-f6911e4007f3) Teil der OLE DB Programmer's Reference.  
  
|Konstante|Wert|Description|Einschränkungsspalten|  
|--------------|-----------|-----------------|------------------------|  
|**adSchemaAsserts**|0|Gibt die im Katalog definierten Assertionen, die von einem bestimmten Benutzer gehören.<br /><br /> (ASSERTIONEN Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCatalogs**|1|Gibt die zugegriffen werden kann, aus dem DBMS Katalogen zugeordneten physischen Attribute zurück.<br /><br /> (Kataloge Rowset)|CATALOG_NAME|  
|**adSchemaCharacterSets**|2|Gibt zurück, die im Katalog definierten Zeichensätze, die für einen bestimmten Benutzer zugänglich sind.<br /><br /> (CHARACTER_SETS Rowset)|CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME|  
|**adSchemaCheckConstraints**|5|Gibt die Check-Einschränkungen im Katalog definierten, die von einem bestimmten Benutzer gehören.<br /><br /> (CHECK_CONSTRAINTS) Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaCollations**|3|Gibt zurück, die im Katalog definierten Zeichensortierreihenfolgen, die für einen bestimmten Benutzer zugänglich sind.<br /><br /> (SORTIERUNGEN Rowset)|COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME|  
|**adSchemaColumnPrivileges**|13|Gibt die Berechtigungen für Tabellenspalten im Katalog definierten, die zur oder von einem bestimmten Benutzer erteilt werden.<br /><br /> (COLUMN_PRIVILEGES Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|**adSchemaColumns**|4|Gibt zurück, die Spalten der Tabellen (einschließlich Sichten) im Katalog definierten, die für einen bestimmten Benutzer zugänglich sind.<br /><br /> (COLUMNS-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaColumnsDomainUsage**|11|Gibt zurück, die im Katalog definierten Spalten, die einer Domäne, die im Katalog definierten und Eigentümer ein angegebener Benutzer abhängig sind.<br /><br /> (COLUMN_DOMAIN_USAGE-Rowset)|DOMAIN_CATALOG DOMAIN_SCHEMA DOMAIN_NAME COLUMN_NAME|  
|**adSchemaConstraintColumnUsage**|6|Die Spalten, die von referenziellen Einschränkungen, unique-Einschränkungen, Check-Einschränkungen und Assertionen verwendet, die im Katalog definierten und Eigentümer ein angegebener Benutzer zurückgegeben.<br /><br /> (CONSTRAINT_COLUMN_USAGE-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaConstraintTableUsage**|7|Gibt zurück, die Tabellen, die von referenziellen Einschränkungen, unique-Einschränkungen, Check-Einschränkungen und Assertionen, die im Katalog definierten und Eigentümer ein angegebener Benutzer verwendet werden.<br /><br /> (CONSTRAINT_TABLE_USAGE-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaCubes**|32|Informationen zu den verfügbaren Cubes zurückgegeben in einem Schema (oder im Katalog, wenn der Anbieter keine Schemas unterstützt).<br /><br /> (CUBES Rowset *)|CATALOG_NAME SCHEMA_NAME CUBE_NAME|  
|**adSchemaDBInfoKeywords**|30|Gibt eine Liste mit anbieterspezifischen Schlüsselwörtern zurück.<br /><br /> (IDBInfo:: GetKeywords)|\<Keine >|  
|**adSchemaDBInfoLiterals**|31|Gibt eine Liste providerabhängiger Literale, die in Textbefehlen verwendet zurück.<br /><br /> (IDBInfo::GetLiteralInfo)|\<Keine >|  
|**adSchemaDimensions**|33|Gibt Informationen zu den Dimensionen in einem bestimmten Cube zurück. Es wurde eine Zeile für jede Dimension.<br /><br /> (DIMENSIONEN Rowset)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_NAME DIMENSION_UNIQUE_NAME|  
|**adSchemaForeignKeys**|27|Gibt die im Katalog von einem angegebenen Benutzer definierten Fremdschlüsselspalten zurück.<br /><br /> (FOREIGN_KEYS-Rowsets)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|**adSchemaHierarchies**|34|Gibt Informationen zu den Hierarchien, die in einer Dimension zurück.<br /><br /> (Rowset HIERARCHIEN)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHIENAME HIERARCHY_UNIQUE_NAME|  
|**adSchemaIndexes**|12|Gibt die im Katalog definierten Indizes, die von einem bestimmten Benutzer gehören.<br /><br /> (INDIZES Rowset)|TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TYP TABLE_NAME|  
|**adSchemaKeyColumnUsage**|8|Gibt zurück, die im Katalog definierten Spalten, die von einem bestimmten Benutzer als Schlüssel eingeschränkt werden.<br /><br /> (KEY_COLUMN_USAGE-Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adSchemaLevels**|35|Gibt Informationen über die Ebenen in einer Dimension zurück.<br /><br /> (Ebenen-Rowset)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_NAME LEVEL_UNIQUE_NAME|  
|**adSchemaMeasures**|36|Gibt Informationen zu den verfügbaren Measures zurück.<br /><br /> (MEASURES Rowset)|CATALOG_NAME SCHEMA_NAME CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME|  
|**adSchemaMembers**|38|Gibt Informationen über die verfügbaren Mitglieder zurück.<br /><br /> (Member Rowset)|Catalog_name SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME LEVEL_NUMBER MEMBER_NAME MEMBER_UNIQUE_NAME MEMBER_CAPTION MEMBER_TYPE Tree-Operator. Weitere Informationen finden Sie in der OLE DB für Online Analytical Processing (OLAP).|  
|**adSchemaPrimaryKeys**|28|Gibt die im Katalog von einem angegebenen Benutzer definierten Primärschlüsselspalten zurück.<br /><br /> (PRIMARY_KEYS-Rowset)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME|  
|**adSchemaProcedureColumns**|29|Gibt Informationen zu den Spalten von Rowsets zurück, die von Prozeduren zurückgegeben werden.<br /><br /> (PROCEDURE_COLUMNS Rowset)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME COLUMN_NAME|  
|**adSchemaProcedureParameters**|26|Gibt Informationen zu den Parametern und Rückgabecodes von Prozeduren zurück.<br /><br /> (PROCEDURE_PARAMETERS-Rowset)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|**adSchemaProcedures**|16|Gibt die im Katalog definierten Prozeduren, die von einem bestimmten Benutzer gehören.<br /><br /> (PROCEDURES-Rowset)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PROCEDURE_TYPE AUS|  
|**adSchemaProperties**|37|Gibt Informationen zu den verfügbaren Eigenschaften für jede Ebene der Dimension zurück.<br /><br /> (Eigenschaften Rowset)|CATALOG_NAME SCHEMA_NAME CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE PROPERTY_NAME|  
|**adSchemaProviderSpecific**|-1|Verwendet, wenn der Anbieter die eigene Schemaabfragen nicht dem Standard entsprechende definiert.|\<Anbieterspezifisch >|  
|**adSchemaProviderTypes**|22|Gibt zurück, die vom Datenanbieter unterstützten (Basis-) Datentypen.<br /><br /> (PROVIDER_TYPES-Rowset)|DATA_TYPE BEST_MATCH|  
|**AdSchemaReferentialConstraints**|9|Gibt zurück, die im Katalog definierten referenziellen Einschränkungen, die von einem bestimmten Benutzer gehören.<br /><br /> (REFERENTIAL_CONSTRAINTS Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME|  
|**adSchemaSchemata**|17|Gibt zurück, die Schemas (Datenbankobjekte), die von einem bestimmten Benutzer gehören.<br /><br /> (SCHEMAS Rowset)|CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|**adSchemaSQLLanguages**|18|Gibt zurück, die Übereinstimmungsebenen, Optionen und Dialekte, die von der SQL-Implementierung Verarbeitung von Daten im Katalog definierten unterstützt werden.<br /><br /> (SQL_LANGUAGES Rowset)|\<Keine >|  
|**adSchemaStatistics**|19|Gibt die im Katalog definierten Statistiken, die von einem bestimmten Benutzer gehören.<br /><br /> (Statistiken Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaTableConstraints**|10|Gibt zurück, die im Katalog definierten tabelleneinschränkungen, die von einem bestimmten Benutzer gehören.<br /><br /> (TABLE_CONSTRAINTS-Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|**adSchemaTablePrivileges**|14|Gibt die Berechtigungen für Tabellen, die im Katalog definierten, die zur oder von einem bestimmten Benutzer erteilt werden.<br /><br /> (TABLE_PRIVILEGES Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|**adSchemaTables**|20|Gibt zurück, die Tabellen (einschließlich Sichten) im Katalog definierten, die für einen bestimmten Benutzer zugänglich sind.<br /><br /> (TABLES-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|**adSchemaTranslations**|21|Gibt zurück, die im Katalog definierten Zeichenübersetzungen, die für einen bestimmten Benutzer zugänglich sind.<br /><br /> (ÜBERSETZUNGEN Rowset)|TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME|  
|**adSchemaTrustees**|39|Zur künftigen Verwendung reserviert.||  
|**adSchemaUsagePrivileges**|15|Gibt die USAGE-Berechtigungen für Objekte, die im Katalog definierten, die zur oder von einem bestimmten Benutzer erteilt werden.<br /><br /> (USAGE_PRIVILEGES Rowset)|OBJECT_CATALOG OBJECT_SCHEMA OBJECT_NAME OBJECT_TYPE GRANTOR EMPFÄNGER|  
|**adSchemaViewColumnUsage**|24|Gibt die Spalten für die Tabellen angezeigt, im Katalog definierten und einen bestimmten Benutzer gehören hängen.<br /><br /> (Rowset VIEW_COLUMN_USAGE-Sicht)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
|**adSchemaViews**|23|Gibt zurück, die im Katalog definierten Sichten, die für einen bestimmten Benutzer zugänglich sind.<br /><br /> (Ansichten Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adSchemaViewTableUsage**|25|Gibt zurück, die Tabellen auf dem angezeigten Tabellen im Katalog definierten und einen bestimmten Benutzer im Besitz, die abhängig sind.<br /><br /> (VIEW_TABLE_USAGE-Rowset)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.Schema.ASSERTS|  
|AdoEnums.Schema.CATALOGS|  
|AdoEnums.Schema.CHARACTERSETS|  
|AdoEnums.Schema.CHECKCONSTRAINTS|  
|AdoEnums.Schema.COLLATIONS|  
|AdoEnums.Schema.COLUMNPRIVILEGES|  
|AdoEnums.Schema.COLUMNS|  
|AdoEnums.Schema.COLUMNSDOMAINUSAGE|  
|AdoEnums.Schema.CONSTRAINTCOLUMNUSAGE|  
|AdoEnums.Schema.CONSTRAINTTABLEUSAGE|  
|AdoEnums.Schema.CUBES|  
|AdoEnums.Schema.DBINFOKEYWORDS|  
|AdoEnums.Schema.DBINFOLITERALS|  
|AdoEnums.Schema.DIMENSIONS|  
|AdoEnums.Schema.FOREIGNKEYS|  
|AdoEnums.Schema.HIERARCHIES|  
|AdoEnums.Schema.INDEXES|  
|AdoEnums.Schema.KEYCOLUMNUSAGE|  
|AdoEnums.Schema.LEVELS|  
|AdoEnums.Schema.MEASURES|  
|AdoEnums.Schema.MEMBERS|  
|AdoEnums.Schema.PRIMARYKEYS|  
|AdoEnums.Schema.PROCEDURECOLUMNS|  
|AdoEnums.Schema.PROCEDUREPARAMETERS|  
|AdoEnums.Schema.PROCEDURES|  
|AdoEnums.Schema.PROPERTIES|  
|AdoEnums.Schema.PROVIDERSPECIFIC|  
|AdoEnums.Schema.PROVIDERTYPES|  
|AdoEnums.Schema.REFERENTIALCONTRAINTS|  
|AdoEnums.Schema.SCHEMATA|  
|AdoEnums.Schema.SQLLANGUAGES|  
|AdoEnums.Schema.STATISTICS|  
|AdoEnums.Schema.TABLECONSTRAINTS|  
|AdoEnums.Schema.TABLEPRIVILEGES|  
|AdoEnums.Schema.TABLES|  
|AdoEnums.Schema.TRANSLATIONS|  
|AdoEnums.Schema.TRUSTEES|  
|AdoEnums.Schema.USAGEPRIVILEGES|  
|AdoEnums.Schema.VIEWCOLUMNUSAGE|  
|AdoEnums.Schema.VIEWS|  
|AdoEnums.Schema.VIEWTABLEUSAGE|  
  
## <a name="applies-to"></a>Gilt für  
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)
