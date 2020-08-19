---
description: SQLColumns
title: SQLColumns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1cfa5203d9be4b89d94173abc000c6fdb1d76d07
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428312"
---
# <a name="sqlcolumns"></a>SQLColumns
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SQLColumns** gibt SQL_SUCCESS zurück, ob Werte für die Parameter *CatalogName*, *TableName*oder *ColumnName* vorhanden sind. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
> [!NOTE]  
>  Für Datentypen für große Werte werden alle Längenparameter mit einem Wert von SQL_SS_LENGTH_UNLIMITED zurückgegeben.  
  
 **SQLColumns** kann in einem statischen Server Cursor ausgeführt werden. Der Versuch, **SQLColumns** für einen aktualisierbaren (dynamischen oder Keyset-) Cursor auszuführen, gibt SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für den *CatalogName* -Parameter akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
 Für ODBC 2. *x* -Anwendungen, die keine Platzhalter in *TableName*verwenden, gibt **SQLColumns** Informationen über alle Tabellen zurück, deren Namen *TableName* entsprechen und deren Besitzer der aktuelle Benutzer ist. Wenn der aktuelle Benutzer keine Tabelle besitzt, deren Name mit dem *TableName* -Parameter übereinstimmt, gibt **SQLColumns** Informationen über alle Tabellen zurück, die sich im Besitz anderer Benutzer befinden, wobei der Tabellenname dem *TableName* -Parameter entspricht. Für ODBC 2. *x* -Anwendungen, die Platzhalter verwenden, gibt **SQLColumns** alle Tabellen zurück, deren Namen *TableName*entsprechen. Für ODBC 3. *x* -Anwendungen **SQLColumns** gibt alle Tabellen zurück, deren Namen *TableName* entsprechen, unabhängig vom Besitzer oder, wenn Platzhalter verwendet werden.  
  
 In der folgenden Tabelle werden die vom Resultset zurückgegebenen Spalten aufgeführt:  
  
|Spaltenname|Beschreibung|  
|-----------------|-----------------|  
|DATA_TYPE|Gibt SQL_VARCHAR, SQL_VARBINARY oder SQL_WVARCHAR für die **varchar (max)** -Datentypen zurück.|  
|TYPE_NAME|Gibt "varchar", "varbinary" oder "nvarchar" für die Datentypen **varchar (max)**, **varbinary (max)** und **nvarchar (max)** zurück.|  
|COLUMN_SIZE|Gibt SQL_SS_LENGTH_UNLIMITED für **varchar (max)** -Datentypen zurück, die angeben, dass die Spaltengröße unbegrenzt ist.|  
|BUFFER_LENGTH|Gibt SQL_SS_LENGTH_UNLIMITED für **varchar (max)** -Datentypen zurück, die angeben, dass die Größe des Puffers unbegrenzt ist.|  
|SQL_DATA_TYPE|Gibt SQL_VARCHAR, SQL_VARBINARY oder SQL_WVARCHAR für die **varchar (max)** -Datentypen zurück.|  
|CHAR_OCTET_LENGTH|Gibt die maximale Länge einer char- oder binary-Spalte zurück. Gibt 0 zurück, um anzuzeigen, dass die Größe unbegrenzt ist.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Gibt den Namen des Katalogs zurück, in dem ein XML-Schemaauflistungsname definiert ist. Wenn der Katalogname nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Gibt den Namen des Schemas zurück, in dem ein XML-Schemaauflistungsname definiert ist. Wenn der Schemaname nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_NAME|Gibt den Namen einer XML-Schemaauflistung zurück. Wenn der Name nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_UDT_CATALOG_NAME|Der Name des Katalogs, der den benutzerdefinierten Typ (User-Defined Type, UDT) enthält.|  
|SS_UDT_SCHEMA_NAME|Der Name des Schemas, das den UDT enthält.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Der qualifizierte Name der UDT-Assembly.|  
  
 Für UDTs wird die vorhandene TYPE_NAME Spalte verwendet, um den Namen des UDT anzugeben. Daher sollte dem Resultset von **SQLColumns** oder [sqlprocedurecolumschlag](../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md)keine zusätzliche Spalte hinzugefügt werden. Der DATA_TYPE für eine UDT-Spalte oder einen UDT-Parameter ist SQL_SS_UDT.  
  
 Für den benutzerdefinierten Typ von Parametern können Sie die neuen, weiter oben in diesem Abschnitt definierten treiberspezifischen Deskriptoren verwenden, um die zusätzlichen Metadateneigenschaften eines UDT abzurufen oder festzulegen, falls der Server diese Informationen zurückgibt bzw. anfordert.  
  
 Wenn ein Client eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLColumns herstellt und diese aufruft, werden bei Verwendung von NULL-oder Platzhalterwerten für den Catalog-Eingabeparameter keine Informationen aus anderen Katalogen zurückgegeben. Stattdessen werden nur Informationen über den aktuellen Katalog zurückgegeben. Der Client kann zuerst SQLTables aufzurufen, um zu bestimmen, in welchem Katalog sich die gewünschte Tabelle befindet. Der Client kann dann diesen Katalogwert für den Catalog-Eingabeparameter im Befehl SQLColumns verwenden, um Informationen über die Spalten in dieser Tabelle abzurufen.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns und Tabellenwertparameter  
 Das Resultset, das von SQLColumns zurückgegeben wird, hängt von der Einstellung SQL_SOPT_SS_NAME_SCOPE ab. Weitere Informationen finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Die folgenden Spalten wurden für Tabellenwertparameter hinzugefügt:  
  
|Spaltenname|Datentyp|Inhalte|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Für eine Spalte vom Datentyp TABLE_TYPE ist dies SQL_TRUE, wenn es sich um eine berechnete Spalte handelt, andernfalls SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE, wenn die Spalte eine Identitätsspalte ist, andernfalls SQL_FALSE.|  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>SQLColumns-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Informationen zu den für Datums-/Uhrzeittypen zurückgegebenen Werten finden Sie unter [catalog Metadata](../../relational-databases/native-client-odbc-date-time/metadata-catalog.md).  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>SQLColumns-Unterstützung für große CLR-UDTs  
 **SQLColumns** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>SQLColumns-Unterstützung für Spalten mit geringer Dichte  
 Zwei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spezifische Spalten wurden dem Resultset für SQLColumns hinzugefügt:  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|**Smallint**|SQL_TRUE, wenn die Spalte eine Sparsespalte ist, andernfalls SQL_FALSE.|  
|SS_IS_COLUMN_SET|**Smallint**|Wenn es sich bei der Spalte um die **column_set** Spalte handelt, ist dies SQL_TRUE. andernfalls SQL_FALSE.|  
  
 In Übereinstimmung mit der ODBC-Spezifikation werden SS_IS_SPARSE und SS_IS_COLUMN_SET vor allen treiberspezifischen Spalten angezeigt, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] früheren Versionen als hinzugefügt wurden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , und nach allen Spalten, die von ODBC selbst vorgeschrieben wurden.  
  
 Das Resultset, das von SQLColumns zurückgegeben wird, hängt von der Einstellung SQL_SOPT_SS_NAME_SCOPE ab. Weitere Informationen finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Weitere Informationen zu sparsespalten in ODBC finden Sie [unter Unterstützung für sparsespalten &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLColumns-Funktion](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
