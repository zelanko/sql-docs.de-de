---
title: Schemarowset-Unterstützung (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- SQL Server Native Client OLE DB provider, schema rowsets
- rowsets [OLE DB], schema
ms.assetid: a75b4b69-b095-4690-9b31-a2b32a67489e
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 316bfd740f909321798cc2203af9577c5ef6e404
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73759555"
---
# <a name="schema-rowset-support-ole-db"></a>Schemarowset-Unterstützung (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt auch das Zurückgeben von Schema Informationen von [!INCLUDE[tsql](../../../includes/tsql-md.md)] einem Verbindungs Server bei der Verarbeitung verteilter Abfragen.  
  
> [!NOTE]  
>  Obwohl [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Synonyme unterstützt, werden Metadaten für Synonyme nicht von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zurückgegeben.  
  
 In der folgenden Tabelle sind die Schemarowsets und die Einschränkungs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Spalten aufgelistet, die vom Native Client-OLE DB Anbieter unterstützt werden  
  
|Schemarowset|Einschränkungsspalten|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|Alle Einschränkungen werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|Alle Einschränkungen werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> Die folgenden zusätzlichen Spalten gelten für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:<br /><br /> COLUMN_LCID, die Gebietsschema-ID der Sortierung. COLUMN_LCID ist der gleiche Wert wie eine Windows-LCID.<br /><br /> COLUMN_COMPFLAGS definiert, welche Vergleiche für die Sortierung unterstützt werden. Das Datenformat ist das Gleiche wie DBPROB_FINDCOMPAREOPS.<br /><br /> COLUMN_SORTID, das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sortierungsformat für die Sortierung.<br /><br /> COLUMN_TDSCOLLATION, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Sortierung für die Spalte.<br /><br /> IS_COMPUTED, mit dem Wert VARIANT_TRUE, wenn es sich um eine berechnete Spalte handelt, andernfalls VARIANT_FALSE.|  
|DBSCHEMA_FOREIGN_KEYS|Alle Einschränkungen werden unterstützt.<br /><br /> PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|DBSCHEMA_INDEXES|Einschränkungen 1, 2, 3 und 5 werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TABLE_NAME|  
|DBSCHEMA_PRIMARY_KEYS|Alle Einschränkungen werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_PROCEDURE_PARAMETERS|Alle Einschränkungen werden unterstützt.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|DBSCHEMA_PROCEDURES|Einschränkungen 1, 2 und 3 werden unterstützt.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME<br /><br /> DBSCHEMA_PROCEDURES gibt nur Prozeduren zurück, die vom aktuellen Benutzer ausgeführt werden können bzw. für die der Benutzer die VIEW DEFINITION-Berechtigung erhalten hat.|  
|DBSCHEMA_PROVIDER_TYPES|Alle Einschränkungen werden unterstützt.<br /><br /> DATA_TYPE BEST_MATCH|  
|DBSCHEMA_SCHEMATA|Alle Einschränkungen werden unterstützt.<br /><br /> CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|DBSCHEMA_STATISTICS|Alle Einschränkungen werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_TABLE_CONSTRAINTS|Alle Einschränkungen werden unterstützt.<br /><br /> CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|DBSCHEMA_TABLE_PRIVILEGES|Alle Einschränkungen werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|DBSCHEMA_TABLES|Alle Einschränkungen werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|DBSCHEMA_TABLES_INFO|Alle Einschränkungen werden unterstützt.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verteilte Abfrageunterstützung für Schemarowsets](../../../relational-databases/native-client/ole-db/schema-rowsets-distributed-query-support.md)  
  
 [LINKEDSERVERS-Rowset &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Verwenden von benutzerdefinierten Typen](../../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
