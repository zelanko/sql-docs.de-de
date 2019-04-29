---
title: SQLColumns | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumns function
ms.assetid: 69d3af44-8196-43ab-8037-cdd06207b171
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5815e4f3a0cdd0defb16c613f3d6e9444fdfaac7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63067719"
---
# <a name="sqlcolumns"></a>SQLColumns
  `SQLColumns` Gibt SQL_SUCCESS zurück, unabhängig davon, ob Werte vorhanden sind, für die *CatalogName*, *TableName*, oder *ColumnName* Parameter. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
> [!NOTE]  
>  Für Datentypen für große Werte werden alle Längenparameter mit einem Wert von SQL_SS_LENGTH_UNLIMITED zurückgegeben.  
  
 `SQLColumns` kann in einem statischen Servercursor ausgeführt werden. Wenn `SQLColumns` in einem aktualisierbaren Cursor (dynamischer Cursor oder Keysetcursor) ausgeführt wird, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die *CatalogName* Parameter: *Linked_Server_Name.Catalog_Name*.  
  
 Für ODBC 2. *x* Anwendungen, die nicht mithilfe von Platzhaltern in *TableName*, `SQLColumns` gibt Informationen über alle Tabellen, deren Namen übereinstimmen *TableName* und von der aktuellen gehören der Benutzer. Wenn der aktuelle Benutzer keine Tabelle besitzt, dessen Name, der *TableName* Parameter `SQLColumns` gibt Informationen über alle Tabellen, deren Besitzer andere Benutzer entspricht, in dem der Tabellenname der *TableName* der Parameter. Für ODBC 2. *x* Anwendungen mithilfe von Platzhaltern, `SQLColumns` alle Tabellen, deren Namen Übereinstimmung zurück *TableName*. Für ODBC 3. *x* Anwendungen `SQLColumns` alle Tabellen, deren Namen Übereinstimmung zurück *TableName* unabhängig vom Besitzer oder gibt an, ob Platzhalter verwendet werden.  
  
 In der folgenden Tabelle werden die vom Resultset zurückgegebenen Spalten aufgeführt:  
  
|Spaltenname|Description|  
|-----------------|-----------------|  
|DATA_TYPE|Gibt SQL_VARCHAR, SQL_VARBINARY oder SQL_WVARCHAR für den **varchar(max)** -Datentypen.|  
|TYPE_NAME|Gibt "Varchar", "Varbinary" oder "Nvarchar" für die **varchar(max)**, **'varbinary(max)'**, und **nvarchar(max)** -Datentypen.|  
|COLUMN_SIZE|Gibt SQL_SS_LENGTH_UNLIMITED für **varchar(max)** -Datentyp zurück, die Größe der Spalte unbegrenzt ist.|  
|BUFFER_LENGTH|Gibt SQL_SS_LENGTH_UNLIMITED für **varchar(max)** -Datentyp zurück, die Größe des Puffers unbegrenzt ist.|  
|SQL_DATA_TYPE|Gibt SQL_VARCHAR, SQL_VARBINARY oder SQL_WVARCHAR für den **varchar(max)** -Datentypen.|  
|CHAR_OCTET_LENGTH|Gibt die maximale Länge einer char- oder binary-Spalte zurück. Gibt 0 zurück, um anzuzeigen, dass die Größe unbegrenzt ist.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|Gibt den Namen des Katalogs zurück, in dem ein XML-Schemaauflistungsname definiert ist. Wenn der Katalogname nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|Gibt den Namen des Schemas zurück, in dem ein XML-Schemaauflistungsname definiert ist. Wenn der Schemaname nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_NAME|Gibt den Namen einer XML-Schemaauflistung zurück. Wenn der Name nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_UDT_CATALOG_NAME|Der Name des Katalogs, der den benutzerdefinierten Typ (User-Defined Type, UDT) enthält.|  
|SS_UDT_SCHEMA_NAME|Der Name des Schemas, die den UDT enthält.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|Der qualifizierte Name der UDT-Assembly.|  
  
 Für UDTs wird die vorhandene TYPE_NAME-Spalte verwendet, um den Namen des UDTS anzugeben. aus diesem Grund dafür keine zusätzliche Spalte hinzugefügt werden sollen das Resultset der `SQLColumns` oder [SQLProcedureColumns](sqlprocedurecolumns.md). Der DATA_TYPE für eine UDT-Spalte oder einen UDT-Parameter ist SQL_SS_UDT.  
  
 Für den benutzerdefinierten Typ von Parametern können Sie die neuen, weiter oben in diesem Abschnitt definierten treiberspezifischen Deskriptoren verwenden, um die zusätzlichen Metadateneigenschaften eines UDT abzurufen oder festzulegen, falls der Server diese Informationen zurückgibt bzw. anfordert.  
  
 Wenn ein Client eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Aufrufen von SQLColumns, die mit NULL oder Platzhalter für ein als katalogeingabeparameter keine Informationen aus anderen Katalogen zurückgegeben wird. Stattdessen werden nur Informationen über den aktuellen Katalog zurückgegeben. Der Client kann zuerst aufrufen, SQLTables, um zu bestimmen, in welchem Katalog sich die gewünschte Tabelle befindet. Der Client kann dann diesen Katalogwert für den katalogeingabeparameter in seinem Aufruf von SQLColumns verwenden, zum Abrufen von Informationen zu den Spalten in dieser Tabelle.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns und Tabellenwertparameter  
 Von SQLColumns zurückgegebene Resultset hängt von der Einstellung von SQL_SOPT_SS_NAME_SCOPE ab. Weitere Informationen finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md). Die folgenden Spalten wurden für Tabellenwertparameter hinzugefügt:  
  
|Spaltenname|Datentyp|Inhalt|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Für eine Spalte vom Datentyp TABLE_TYPE ist dies SQL_TRUE, wenn es sich um eine berechnete Spalte handelt, andernfalls SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE, wenn die Spalte eine Identitätsspalte ist, andernfalls SQL_FALSE.|  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>SQLColumns-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Informationen über die zurückgegebenen Werte für Datum/Uhrzeit-Typen finden Sie unter [Katalogmetadaten](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>SQLColumns-Unterstützung für große CLR-UDTs  
 `SQLColumns` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>SQLColumns-Unterstützung für Spalten mit geringer Dichte  
 Zwei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bestimmte Spalten das Resultset für SQLColumns hinzugefügt wurden:  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|`Smallint`|SQL_TRUE, wenn die Spalte eine Sparsespalte ist, andernfalls SQL_FALSE.|  
|SS_IS_COLUMN_SET|`Smallint`|Wenn die Spalte die `column_set`-Spalte ist, SQL_TRUE, andernfalls SQL_FALSE.|  
  
 In Übereinstimmung mit der ODBC-Spezifikation werden SS_IS_SPARSE und SS_IS_COLUMN_SET vor alle treiberspezifischen Spalten, die hinzugefügt wurden, angezeigt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versionen älter als [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], und nach alle Spalten, die von ODBC selbst.  
  
 Von SQLColumns zurückgegebene Resultset hängt von der Einstellung von SQL_SOPT_SS_NAME_SCOPE ab. Weitere Informationen finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Weitere Informationen über sparsespalten in ODBC finden Sie unter [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLColumns-Funktion](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
