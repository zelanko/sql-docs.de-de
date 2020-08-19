---
description: SchemaEnum
title: Schemaaufumum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a4356ad974c45e16cec32d45fa2ed6aeb42209f5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442172"
---
# <a name="schemaenum"></a>SchemaEnum
Gibt den Typ des Schema- **Recordsets** an, das von der [OpenSchema](../../../ado/reference/ado-api/openschema-method.md) -Methode abgerufen wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen über die Funktion und die Spalten, die für jede ADO-Konstante zurückgegeben werden, finden Sie in den Themen in [Anhang B: Schemarowsets](https://msdn.microsoft.com/2b5fbf03-e50d-44ee-bc57-5a57666c55f1) der OLE DB Programmierer-Referenz. Der Name jedes Themas wird in Klammern im Abschnitt Beschreibung der folgenden Tabelle aufgeführt.  
  
 Weitere Informationen über die Funktion und die Spalten, die für die einzelnen ADO MD Konstanten zurückgegeben werden, finden Sie in den Themen in [OLE DB für OLAP-Objekte und Schemarowsets](https://msdn.microsoft.com/d20bb2a6-68bd-423f-9ec8-eb930cd0c144) im OLE DB für die Online Analytical Processing (OLAP)-Dokumentation. Der Name jedes Themas wird in Klammern in der Spalte Beschreibung der folgenden Tabelle aufgeführt.  
  
 Sie können die Datentypen von Spalten in der OLE DB-Dokumentation in ADO-Datentypen übersetzen, indem Sie auf die Spalte Beschreibung des Themas ADO [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) verweisen. Beispielsweise entspricht ein OLE DB Datentyp **DBTYPE_WSTR** dem ADO-Datentyp **adwchar**.  
  
 ADO generiert Schema ähnliche Ergebnisse für die Konstanten **adSchemaDBInfoKeywords** und **adSchemaDBInfoLiterals**. ADO erstellt ein **Recordset**und füllt dann jede Zeile mit den Werten aus, die von den **IDBInfo:: GetKeywords** -und **IDBInfo:: GetLiteralInfo** -Methoden zurückgegeben werden. Weitere Informationen zu diesen Methoden finden Sie im Abschnitt [IDBInfo](https://msdn.microsoft.com/3f5ad97f-3fc6-4f21-b691-f6911e4007f3) der OLE DB Programmierer-Referenz.  
  
|Konstant|Wert|Beschreibung|Einschränkungs Spalten|  
|--------------|-----------|-----------------|------------------------|  
|**adschemaassert**|0|Gibt die im Katalog definierten Assertionen zurück, deren Besitzer ein angegebener Benutzer ist.<br /><br /> (Assertionen-Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA constraint_name|  
|**adschemacatalogs**|1|Gibt die physischen Attribute zurück, die Katalogen zugeordnet sind, auf die über das DBMS zugegriffen werden<br /><br /> (Katalogen-Rowset)|CATALOG_NAME|  
|**adschemacharakterisets**|2|Gibt die im Katalog definierten Zeichensätze zurück, auf die ein bestimmter Benutzer zugreifen kann.<br /><br /> (CHARACTER_SETS-Rowset)|CHARACTER_SET_CATALOG CHARACTER_SET_SCHEMA CHARACTER_SET_NAME|  
|**adschemacheckeinschränkungen**|5|Gibt die im Katalog definierten CHECK-Einschränkungen zurück, die sich im Besitz eines bestimmten Benutzers befinden.<br /><br /> (CHECK_CONSTRAINTS) Rowset|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA constraint_name|  
|**adschemacollations**|3|Gibt die im Katalog definierten Zeichen Sortierungen zurück, auf die ein bestimmter Benutzer zugreifen kann.<br /><br /> (COLLATIONS-Rowset)|COLLATION_CATALOG COLLATION_SCHEMA COLLATION_NAME|  
|**adschemacolenumnprivileges**|13|Gibt die Berechtigungen für Spalten von Tabellen zurück, die im Katalog definiert sind oder von einem bestimmten Benutzer erteilt wurden.<br /><br /> (COLUMN_PRIVILEGES-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|**adschemacolin**|4|Gibt die Spalten der im Katalog definierten Tabellen (einschließlich Sichten) zurück, auf die ein bestimmter Benutzer zugreifen kann.<br /><br /> (COLUMNS-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**"adschemacolumschlag nsdomainusage"**|11|Gibt die im Katalog definierten Spalten zurück, die von einer im Katalog definierten Domäne abhängig sind und deren Eigentümer ein angegebener Benutzer ist.<br /><br /> (COLUMN_DOMAIN_USAGE-Rowset)|DOMAIN_CATALOG DOMAIN_SCHEMA DOMAIN_NAME column_name|  
|**adschemaconstraintcolumnusage**|6|Gibt die im Katalog definierten Spalten zurück, die von referenziellen Einschränkungen, UNIQUE-Einschränkungen, CHECK-Einschränkungen und Assertionen verwendet werden und deren Eigentümer ein angegebener Benutzer ist.<br /><br /> (CONSTRAINT_COLUMN_USAGE-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME|  
|**adschemaconstrainttableusage**|7|Gibt die im Katalog definierten Tabellen zurück, die von referenziellen Einschränkungen, UNIQUE-Einschränkungen, CHECK-Einschränkungen und Assertionen verwendet werden und deren Eigentümer ein angegebener Benutzer ist.<br /><br /> (Constraint_Table_Usage-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adschemacubes**|32|Gibt Informationen zu den verfügbaren Cubes in einem Schema (oder dem Katalog zurück, wenn der Anbieter keine Schemas unterstützt).<br /><br /> (Cubes-Rowset *)|Catalog_Name schema_name CUBE_NAME|  
|**adSchemaDBInfoKeywords**|30|Gibt eine Liste mit anbieterspezifischen Schlüsselwörtern zurück.<br /><br /> (IDBInfo:: GetKeywords)|\<None>|  
|**adSchemaDBInfoLiterals**|31|Gibt eine Liste providerabhängiger Literale zurück, die in Textbefehlen verwendet werden.<br /><br /> (IDBInfo:: GetLiteralInfo)|\<None>|  
|**adschemadimensions**|33|Gibt Informationen zu den Dimensionen in einem angegebenen Cube zurück. Sie enthält eine Zeile für jede Dimension.<br /><br /> (Dimensions-Rowset)|Catalog_Name schema_name CUBE_NAME Dimension_Name DIMENSION_UNIQUE_NAME|  
|**adschemafremnkeys**|27|Gibt die im Katalog von einem angegebenen Benutzer definierten Fremdschlüsselspalten zurück.<br /><br /> (FOREIGN_KEYS-Rowset)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|**adschemahierarchien**|34|Gibt Informationen zu den Hierarchien zurück, die in einer Dimension verfügbar sind.<br /><br /> (Hierarchien-Rowset)|Catalog_Name schema_name CUBE_NAME DIMENSION_UNIQUE_NAME Hierarchy_Name HIERARCHY_UNIQUE_NAME|  
|**adSchemaIndexes**|12|Gibt die im Katalog definierten Indizes zurück, deren Besitzer ein angegebener Benutzer ist.<br /><br /> (Indexen-Rowset)|TABLE_CATALOG TABLE_SCHEMA index_name Typ table_name|  
|**adschemakeycolumnusage**|8|Gibt die im Katalog definierten Spalten zurück, die von einem angegebenen Benutzer als Schlüssel eingeschränkt werden.<br /><br /> (KEY_COLUMN_USAGE-Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA constraint_name TABLE_CATALOG TABLE_SCHEMA table_name column_name|  
|**adschemalevels**|35|Gibt Informationen zu den in einer Dimension verfügbaren Ebenen zurück.<br /><br /> (Levels-Rowset)|Catalog_Name schema_name CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME level_name LEVEL_UNIQUE_NAME|  
|**adschemameasures**|36|Gibt Informationen zu den verfügbaren Measures zurück.<br /><br /> (Measures-Rowset)|Catalog_Name schema_name CUBE_NAME MEASURE_NAME MEASURE_UNIQUE_NAME|  
|**"adschemamembers"**|38|Gibt Informationen zu den verfügbaren Membern zurück.<br /><br /> (Members-Rowset)|Catalog_Name schema_name CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME LEVEL_NUMBER MEMBER_NAME MEMBER_UNIQUE_NAME MEMBER_CAPTION MEMBER_TYPE Tree-Operators. Weitere Informationen finden Sie unter OLE DB für die analytische Online Verarbeitung (Online Analytical Processing, OLAP).|  
|**adSchemaPrimaryKeys**|28|Gibt die im Katalog von einem angegebenen Benutzer definierten Primärschlüsselspalten zurück.<br /><br /> (PRIMARY_KEYS-Rowset)|PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME|  
|**adschemaprocedurecolumschlag**|29|Gibt Informationen zu den Spalten von Rowsets zurück, die von Prozeduren zurückgegeben werden.<br /><br /> (Procedure_Columns-Rowset)|PROCEDURE_CATALOG PROCEDURE_SCHEMA procedure_name column_name|  
|**adschemaprocedureparameters**|26|Gibt Informationen zu den Parametern und Rückgabecodes von Prozeduren zurück.<br /><br /> (PROCEDURE_PARAMETERS-Rowset)|PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|**adschemaprozeduren**|16|Gibt die im Katalog definierten Prozeduren zurück, die sich im Besitz eines bestimmten Benutzers befinden.<br /><br /> (Prozeduren-Rowset)|PROCEDURE_CATALOG PROCEDURE_SCHEMA procedure_name PROCEDURE_TYPE|  
|**adschemaproperties**|37|Gibt Informationen zu den verfügbaren Eigenschaften für die einzelnen Dimensions Ebenen zurück.<br /><br /> (Properties-Rowset)|Catalog_Name schema_name CUBE_NAME DIMENSION_UNIQUE_NAME HIERARCHY_UNIQUE_NAME LEVEL_UNIQUE_NAME MEMBER_UNIQUE_NAME PROPERTY_TYPE property_name|  
|**adSchemaProviderSpecific**|-1|Wird verwendet, wenn der Anbieter seine eigenen nicht standardmäßigen Schema Abfragen definiert.|\<Provider specific>|  
|**adschemaprovidertypes**|22|Gibt die vom Datenanbieter unterstützten (Basis-) Datentypen zurück.<br /><br /> (PROVIDER_TYPES-Rowset)|DATA_TYPE BEST_MATCH|  
|**Adschemareferentialeinschränkungen**|9|Gibt die referenziellen Einschränkungen zurück, die im Katalog definiert sind, dessen Besitzer ein angegebener Benutzer ist.<br /><br /> (REFERENTIAL_CONSTRAINTS-Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA constraint_name|  
|**adschemaschemata**|17|Gibt die Schemas (Datenbankobjekte) zurück, die sich im Besitz eines bestimmten Benutzers befinden.<br /><br /> (Schemata-Rowset)|CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|**adschemasqllanguages**|18|Gibt die definierten Übereinstimmungsebenen, Optionen und Dialekte zurück, die von der SQL-Implementierung, die die im Katalog definierten Daten verarbeitet, unterstützt werden.<br /><br /> (SQL_LANGUAGES-Rowset)|\<None>|  
|**adschemastatistics**|19|Gibt die im Katalog definierten Statistiken zurück, deren Besitzer ein angegebener Benutzer ist.<br /><br /> (Statistik-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adschematableeinschränkungen**|10|Gibt die im Katalog definierten Tabellen Einschränkungen zurück, die sich im Besitz eines bestimmten Benutzers befinden.<br /><br /> (TABLE_CONSTRAINTS-Rowset)|CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|**adschematableprivileges**|14|Gibt die im Katalog definierten Berechtigungen für Tabellen zurück, die für einen angegebenen Benutzer verfügbar sind oder von diesem erteilt wurden.<br /><br /> (TABLE_PRIVILEGES-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|**adSchemaTables**|20|Gibt die im Katalog definierten Tabellen (einschließlich Sichten) zurück, auf die ein angegebener Benutzer zugreifen kann.<br /><br /> (TABLES-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|**adschematranslations**|21|Gibt die im Katalog definierten Zeichen Übersetzungen zurück, auf die ein bestimmter Benutzer zugreifen kann.<br /><br /> (Translations-Rowset)|TRANSLATION_CATALOG TRANSLATION_SCHEMA TRANSLATION_NAME|  
|**adschematrustees**|39|Für zukünftige Verwendung reserviert.||  
|**adschemausageprivileges**|15|Gibt die Verwendungs Berechtigungen für Objekte zurück, die im Katalog definiert sind oder von einem bestimmten Benutzer erteilt werden.<br /><br /> (Usage_Privileges-Rowset)|OBJECT_CATALOG OBJECT_SCHEMA object_name OBJECT_TYPE Berechtigungs Empfänger|  
|**adschemaviewcolumnusage**|24|Gibt die Spalten zurück, für die angezeigte Tabellen, die im Katalog definiert sind und deren Besitzer ein angegebener Benutzer ist, abhängig sind.<br /><br /> (VIEW_COLUMN_USAGE-Rowset)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
|**adschemaviews**|23|Gibt die im Katalog definierten Sichten zurück, auf die ein bestimmter Benutzer zugreifen kann.<br /><br /> (Views-Rowset)|TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|**adschemaviewtableusage**|25|Gibt die Tabellen zurück, von denen im Katalog definierte Tabellen in Sichten, deren Eigentümer ein angegebener Benutzer ist, abhängig sind.<br /><br /> (View_Table_Usage-Rowset)|VIEW_CATALOG VIEW_SCHEMA VIEW_NAME|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|AdoEnums. Schema. Assert|  
|AdoEnums. Schema. Kataloge|  
|AdoEnums. Schema. Merkmal Sets|  
|AdoEnums. Schema. Check-Einschränkungen|  
|AdoEnums. Schema. Sortierungen|  
|AdoEnums. Schema. columnprivileges|  
|AdoEnums. Schema. Columns|  
|AdoEnums. Schema. columnsdomainusage|  
|AdoEnums. Schema. einschränintcolumnusage|  
|AdoEnums. Schema. einschräninttableusage|  
|AdoEnums. Schema. Cubes|  
|AdoEnums. Schema. DbInfoKeywords|  
|AdoEnums. Schema. DbInfoLiterals|  
|AdoEnums. Schema. Dimensions|  
|AdoEnums. Schema. Fremdschlüssel|  
|AdoEnums. Schema. Hierarchien|  
|AdoEnums. Schema. Indexes|  
|AdoEnums. Schema. keycolumnusage|  
|AdoEnums. Schema. Levels|  
|AdoEnums. Schema. Measures|  
|AdoEnums. Schema. Members|  
|AdoEnums. Schema. primarykeys|  
|AdoEnums. Schema. ProcedureColumns|  
|AdoEnums. Schema. ProcedureParameters|  
|AdoEnums. Schema. Prozeduren|  
|AdoEnums. Schema. Properties|  
|AdoEnums. Schema. ProviderSpecific|  
|AdoEnums. Schema. providertypes|  
|AdoEnums. Schema. referentialconfiguration|  
|AdoEnums. Schema. Schemata|  
|AdoEnums. Schema. sqllanguages|  
|AdoEnums. Schema. Statistics|  
|AdoEnums. Schema. tablecolumns|  
|AdoEnums. Schema. TablePrivileges|  
|AdoEnums. Schema. Tables|  
|AdoEnums. Schema. translations|  
|AdoEnums. Schema. Treuhänder|  
|AdoEnums. Schema. usageprivileges|  
|AdoEnums. Schema. viewcolumnusage|  
|AdoEnums. Schema. views|  
|AdoEnums. Schema. viewtableusage|  
  
## <a name="applies-to"></a>Gilt für  
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)
