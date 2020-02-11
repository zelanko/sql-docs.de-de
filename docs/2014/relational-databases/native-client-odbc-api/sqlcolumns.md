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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067719"
---
# <a name="sqlcolumns"></a>SQLColumns
  `SQLColumns`gibt SQL_SUCCESS zurück, ob Werte für die Parameter *CatalogName*, *TableName*oder *ColumnName* vorhanden sind. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
> [!NOTE]  
>  Für Datentypen für große Werte werden alle Längenparameter mit einem Wert von SQL_SS_LENGTH_UNLIMITED zurückgegeben.  
  
 
  `SQLColumns` kann in einem statischen Servercursor ausgeführt werden. Wenn `SQLColumns` in einem aktualisierbaren Cursor (dynamischer Cursor oder Keysetcursor) ausgeführt wird, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für den *CatalogName* -Parameter akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
 Für ODBC 2. *x* -Anwendungen, die keine Platzhalter in *TableName*verwenden, gibt Informationen zu allen Tabellen zurück, `SQLColumns` deren Namen *TableName* entsprechen und deren Besitzer der aktuelle Benutzer ist. Wenn der aktuelle Benutzer keine Tabelle besitzt, deren Name mit dem *TableName* - `SQLColumns` Parameter übereinstimmt, gibt Informationen zu allen Tabellen zurück, die sich im Besitz anderer Benutzer befinden, wobei der Tabellenname dem *TableName* -Parameter entspricht. Für ODBC 2. *x* -Anwendungen, die Platz `SQLColumns` Halter verwenden, gibt alle Tabellen zurück, deren Namen *TableName*entsprechen. Für ODBC 3. *x* - `SQLColumns` Anwendungen gibt alle Tabellen zurück, deren Namen *TableName* entsprechen, unabhängig vom Besitzer oder, wenn Platzhalter verwendet werden.  
  
 In der folgenden Tabelle werden die vom Resultset zurückgegebenen Spalten aufgeführt:  
  
|Spaltenname|BESCHREIBUNG|  
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
  
 Für UDTs wird die vorhandene TYPE_NAME Spalte verwendet, um den Namen des UDT anzugeben. Daher sollte dem Resultset von `SQLColumns` oder [sqlprocedurecolrens](sqlprocedurecolumns.md)keine zusätzliche Spalte hinzugefügt werden. Der DATA_TYPE für eine UDT-Spalte oder einen UDT-Parameter ist SQL_SS_UDT.  
  
 Für den benutzerdefinierten Typ von Parametern können Sie die neuen, weiter oben in diesem Abschnitt definierten treiberspezifischen Deskriptoren verwenden, um die zusätzlichen Metadateneigenschaften eines UDT abzurufen oder festzulegen, falls der Server diese Informationen zurückgibt bzw. anfordert.  
  
 Wenn ein Client eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit SQLColumns herstellt und diese aufruft, werden bei Verwendung von NULL-oder Platzhalterwerten für den Catalog-Eingabeparameter keine Informationen aus anderen Katalogen zurückgegeben. Stattdessen werden nur Informationen über den aktuellen Katalog zurückgegeben. Der Client kann zuerst SQLTables aufzurufen, um zu bestimmen, in welchem Katalog sich die gewünschte Tabelle befindet. Der Client kann dann diesen Katalogwert für den Catalog-Eingabeparameter im Befehl SQLColumns verwenden, um Informationen über die Spalten in dieser Tabelle abzurufen.  
  
## <a name="sqlcolumns-and-table-valued-parameters"></a>SQLColumns und Tabellenwertparameter  
 Das Resultset, das von SQLColumns zurückgegeben wird, hängt von der Einstellung SQL_SOPT_SS_NAME_SCOPE ab. Weitere Informationen finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md). Die folgenden Spalten wurden für Tabellenwertparameter hinzugefügt:  
  
|Spaltenname|Datentyp|Contents|  
|-----------------|---------------|--------------|  
|SS_IS_COMPUTED|Smallint|Für eine Spalte vom Datentyp TABLE_TYPE ist dies SQL_TRUE, wenn es sich um eine berechnete Spalte handelt, andernfalls SQL_FALSE.|  
|SS_IS_IDENTITY|Smallint|SQL_TRUE, wenn die Spalte eine Identitätsspalte ist, andernfalls SQL_FALSE.|  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlcolumns-support-for-enhanced-date-and-time-features"></a>SQLColumns-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Informationen zu den für Datums-/Uhrzeittypen zurückgegebenen Werten finden Sie unter [catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlcolumns-support-for-large-clr-udts"></a>SQLColumns-Unterstützung für große CLR-UDTs  
 
  `SQLColumns` unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlcolumns-support-for-sparse-columns"></a>SQLColumns-Unterstützung für Spalten mit geringer Dichte  
 Zwei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spezifische Spalten wurden dem Resultset für SQLColumns hinzugefügt:  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|SS_IS_SPARSE|`Smallint`|SQL_TRUE, wenn die Spalte eine Sparsespalte ist, andernfalls SQL_FALSE.|  
|SS_IS_COLUMN_SET|`Smallint`|Wenn die Spalte die `column_set`-Spalte ist, SQL_TRUE, andernfalls SQL_FALSE.|  
  
 In Übereinstimmung mit der ODBC-Spezifikation werden SS_IS_SPARSE und SS_IS_COLUMN_SET vor allen treiberspezifischen Spalten angezeigt, die früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Versionen als [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]hinzugefügt wurden, und nach allen Spalten, die von ODBC selbst vorgeschrieben wurden.  
  
 Das Resultset, das von SQLColumns zurückgegeben wird, hängt von der Einstellung SQL_SOPT_SS_NAME_SCOPE ab. Weitere Informationen finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Weitere Informationen zu sparsespalten in ODBC finden Sie [unter Unterstützung für sparsespalten &#40;ODBC-&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLColumns-Funktion](https://go.microsoft.com/fwlink/?LinkId=59336)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
