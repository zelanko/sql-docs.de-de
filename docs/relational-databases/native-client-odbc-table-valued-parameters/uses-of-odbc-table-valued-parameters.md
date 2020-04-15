---
title: Verwendung von ODBC-Tabellenwertparametern | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), scenarios
- ODBC, table-valued parameters
ms.assetid: f1b73932-4570-4a8a-baa0-0f229d9c32ee
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e88092c6566d9e5838f8a2cb59cd7c23564af9b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297736"
---
# <a name="uses-of-odbc-table-valued-parameters"></a>Verwendungen von ODBC-Tabellenwertparametern
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema werden die wichtigsten Benutzerszenarien für die Verwendung von Tabellenwertparametern mit ODBC erläutert:  
  
-   Tabellenwertparameter mit vollständig gebundenen mehrzeiligen Puffern (Senden von Daten als Tabellenwertparameter mit allen Werten im Arbeitsspeicher)  
  
-   Tabellenwertparameter mit Zeilenstreaming (Senden von Daten als Tabellenwertparameter mithilfe von Data-at-Execution)  
  
-   Abrufen von Tabellenwertparameter-Metadaten aus dem Systemkatalog  
  
-   Abrufen von Tabellenwertparameter-Metadaten für eine vorbereitete Anweisung  
  
## <a name="table-valued-parameter-with-fully-bound-multirow-buffers-send-data-as-a-tvp-with-all-values-in-memory"></a>Tabellenwertparameter mit vollständig gebundenen mehrzeiligen Puffern (Senden von Daten als Tabellenwertparameter mit allen Werten im Arbeitsspeicher)  
 Bei der Verwendung mit vollständig gebundenen mehrzeiligen Puffern sind alle Parameterwerte im Arbeitsspeicher verfügbar. Dies ist beispielsweise für eine OLTP-Transaktion typisch, bei der Tabellenwertparameter in eine einzeln gespeicherte Prozedur gepackt werden können. Ohne Tabellenwertparameter wären mehrere Serveraufrufe oder die dynamische Generierung eines komplexen Batches mit mehreren Anweisungen erforderlich.  
  
 Der Tabellenwertparameter selbst wird durch die Verwendung von [SQLBindParameter](https://go.microsoft.com/fwlink/?LinkId=59328) zusammen mit den anderen Parametern gebunden. Nachdem alle Parameter gebunden wurden, legt die Anwendung das Parameterfokusattribut SQL_SOPT_SS_PARAM_FOCUS für jeden Tabellenwertparameter fest und ruft SQLBindParameter für die Spalten des Tabellenwertparameters auf.  
  
 Der Servertyp für Tabellenwertparameter ist SQL_SS_TABLE, ein neuer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischer Typ. Der C-Bindungstyp für SQL_SS_TABLE muss stets SQL_C_DEFAULT sein. Für den gebundenen Parameter des Tabellenwertparameters werden keine Daten übertragen. Dieser wird zur Übergabe von Tabellenmetadaten und zur Steuerung der Datenübergabe in die einzelnen Spalten des Tabellenwertparameters verwendet.  
  
 Die Länge des Tabellenwertparameters ist auf die Anzahl der an den Server gesendeten Zeilen festgelegt. Der *ColumnSize-Parameter* von SQLBindParameter für einen Tabellenwertparameter gibt die maximale Anzahl von Zeilen an, die gesendet werden können. Dies ist die Arraygröße der Spaltenpuffer. *ParameterValuePtr* ist der Parameterpuffer für einen Tabellenwertparameter in SQLBindParameter. *ParameterValuePtr* und die zugehörige *BufferLength* werden verwendet, um den Typnamen des Parameters "Tabellenwert" bei Bedarf zu übergeben. Der Typname wird nicht für gespeicherte Prozeduraufrufe benötigt, er ist jedoch für SQL-Anweisungen erforderlich.  
  
 Wenn ein Tabellenwertparametertypname für einen Aufruf von SQLBindParameter angegeben wird, muss er immer als Unicode-Wert angegeben werden, auch in Anwendungen, die als ANSI-Anwendungen erstellt werden. Wenn Sie einen Parametertypnamen mit Tabellenwert mithilfe von SQLSetDescField angeben, können Sie ein Literal verwenden, das der Art und Weise entspricht, wie die Anwendung erstellt wird. Der ODBC-Treiber-Manager führt die eventuell erforderliche Unicode-Konvertierung aus.  
  
 Metadaten für Tabellenparameter und Parameterspalten mit Tabellenwert können mithilfe von SQLGetDescRec, SQLSetDescRec, SQLGetDescField und SQLSetDescField einzeln und explizit bearbeitet werden. Das Überladen von SQLBindParameter ist jedoch in der Regel bequemer und erfordert in den meisten Fällen keinen expliziten Deskriptorzugriff. Dieser Ansatz stimmt mit der Definition von SQLBindParameter für andere Datentypen überein, mit der Ausnahme, dass bei einem Parameter mit Tabellenwert die betroffenen Deskriptorfelder etwas unterschiedlich sind.  
  
 Manchmal verwendet eine Anwendung einen Tabellenwertparameter mit dynamischem SQL, und der Name des Tabellenwertparameters muss bereitgestellt werden. Wenn dies der Fall ist und der Parameter "Tabellenwert" nicht im aktuellen Standardschema für die Verbindung definiert ist, müssen SQL_CA_SS_TYPE_CATALOG_NAME und SQL_CA_SS_TYPE_SCHEMA_NAME mithilfe von SQLSetDescField festgelegt werden. Da Tabellentypdefinitionen und Tabellenwertparameter in derselben Datenbank vorliegen müssen, darf SQL_CA_SS_TYPE_CATALOG_NAME nicht festgelegt werden, wenn die Anwendung Tabellenwertparameter verwendet. Andernfalls meldet SQLSetDescField einen Fehler.  
  
 Beispielcode für dieses Szenario `demo_fixed_TVP_binding` befindet sich in der Prozedur unter Verwenden von [Tabellenwertparametern &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="table-valued-parameter-with-row-streaming-send-data-as-a-tvp-using-data-at-execution"></a>Tabellenwertparameter mit Zeilenstreaming (Senden von Daten als Tabellenwertparameter mithilfe von Data-at-Execution)  
 In diesem Szenario stellt die Anwendung dem Treiber Zeilen nach Anforderung bereit. Diese werden an den Server gestreamt. Hierdurch wird das Puffern aller Zeilen im Arbeitsspeicher vermieden. Dies ist für Masseneinfügungs-/-updateszenarien repräsentativ. Tabellenwertparameter bieten eine Leistungsfähigkeit, die zwischen Parameterarrays und Massenkopieren liegt. Tabellenwertparameter sind ebenso einfach zu programmieren wie Parameterarrays, sie bieten jedoch eine größere Flexibilität auf dem Server.  
  
 Das Binden des Tabellenwertparameters und der zugehörigen Spalten erfolgt wie im vorherigen Abschnitt "Tabellenwertparameter mit vollständig gebundenen mehrzeiligen Puffern" beschrieben, der Längenindikator des Tabellenwertparameters selbst wird jedoch auf SQL_DATA_AT_EXEC festgelegt. Der Treiber reagiert auf SQLExecute oder SQLExecuteDirect auf die übliche Weise für Daten-at-Ausführungsparameter, d. h. durch Rückgabe SQL_NEED_DATA. Wenn der Treiber bereit ist, Daten für einen Tabellenwertparameter zu akzeptieren, gibt SQLParamData den Wert von *ParameterValuePtr* in SQLBindParameter zurück.  
  
 Eine Anwendung verwendet SQLPutData für einen Parameter mit Tabellenwert, um die Verfügbarkeit von Daten für Tabellenwert-Parameterkonstituierende Spalten anzugeben. Wenn SQLPutData für einen Tabellenwertparameter aufgerufen wird, muss *DataPtr* immer null sein, und *StrLen_or_Ind* muss entweder 0 oder eine Zahl kleiner oder gleich der Arraygröße sein, die für Tabellenwertparameterpuffer angegeben ist (der *ColumnSize-Parameter* von SQLBindParameter). Der Wert 0 gibt an, dass keine weiteren Zeilen für den Tabellenwertparameter vorhanden sind, und der Treiber fährt mit der Verarbeitung des nächsten tatsächlichen Prozedurparameters fort. Wenn *StrLen_or_Ind* nicht 0 ist, verarbeitet der Treiber die Tabellenwertparameter-Komponentenspalten auf die gleiche Weise wie parametergebundene Parameter mit nicht Tabellenwert: Jede Parameterspalte mit Tabellenwert kann ihre tatsächliche Datenlänge angeben, SQL_NULL_DATA, oder sie kann Daten bei der Ausführung über ihren Längen-/Indikatorpuffer angeben. Tabellenwert-Parameterspaltenwerte können wie üblich durch wiederholte Aufrufe von SQLPutData übergeben werden, wenn ein Zeichen- oder Binärwert in Teilen übergeben werden soll.  
  
 Nachdem alle Tabellenwertparameter-Spalten verarbeitet wurden, kehrt der Treiber zum Tabellenwertparameter zurück, um weitere Tabellenwertparameter-Datenzeilen zu verarbeiten. Bei Data-at-Execution-Tabellenwertparametern führt der Treiber daher nicht den üblichen sequenziellen Scan gebundener Parameter durch. Ein gebundener Tabellenwertparameter wird abgefragt, bis SQLPutData mit *StrLen_Or_IndPtr* gleich 0 aufgerufen wird.  Wenn SQLPutData einen Indikatorwert größer oder gleich 1 übergibt, verarbeitet der Treiber Parameterspalten und Zeilen mit Tabellenwert sequenziell, bis er Werte für alle gebundenen Zeilen und Spalten enthält. Anschließend kehrt der Treiber zum Tabellenwertparameter zurück. Zwischen dem Empfang des Tokens für den Tabellenwertparameter von SQLParamData und dem Aufrufen von SQLPutData(hstmt, NULL, n) für einen Tabellenwertparameter muss die Anwendung Tabellenwertparameterkonstituierende Spaltendaten und Indikatorpufferinhalte für die nächste Zeile oder Zeilen festlegen, die an den Server übergeben werden sollen.  
  
 Beispielcode für dieses Szenario `demo_variable_TVP_binding` befindet sich in der Routine unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-from-the-system-catalog"></a>Abrufen von Tabellenwertparameter-Metadaten aus dem Systemkatalog  
 Wenn eine Anwendung SQLProcedureColumns für eine Prozedur aufruft, die Parameterparameter mit Tabellenwert enthält, wird DATA_TYPE als SQL_SS_TABLE zurückgegeben, und TYPE_NAME ist der Name des Tabellentyps für den Parameter "Tabellenwert". Zwei zusätzliche Spalten werden dem von SQLProcedureColumns zurückgegebenen Resultset hinzugefügt: SS_TYPE_CATALOG_NAME gibt den Namen des Katalogs zurück, in dem der Tabellentyp des Tabellenwertparameters definiert ist, und SS_TYPE_SCHEMA_NAME gibt den Namen des Schemas zurück, in dem der Tabellentyp des Tabellenwertparameters definiert ist. In Übereinstimmung mit der ODBC-Spezifikation werden SS_TYPE_CATALOG_NAME und SS_TYPE_SCHEMA_NAME vor allen treiberspezifischen Spalten angezeigt, die in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hinzugefügt wurden sowie nach allen Spalten, die von ODBC selbst benötigt werden.  
  
 Die neuen Spalten werden nicht nur für Tabellenwertparameter, sondern auch für Parameter des CLR-benutzerdefinierten Typs aufgefüllt. Die vorhandenen Schema- und Katalogspalten von Parametern des benutzerdefinierten Typs werden noch aufgefüllt, in Zukunft wird die Anwendungsentwicklung jedoch durch gemeinsame Schema- und Katalogspalten für Datentypen, die diese erfordern, erleichtert. (Beachten Sie, dass XML-Schemaauflistungen einige Unterschiede aufweisen und nicht in dieser Änderung enthalten sind.)  
  
 Eine Anwendung verwendet SQLTables, um die Namen von Tabellentypen auf die gleiche Weise zu bestimmen wie bei persistenten Tabellen, Systemtabellen und Ansichten. Die Einführung eines neuen Tabellentyps ? TABLE TYPE ? ermöglicht es einer Anwendung, Tabellentypen zu identifizieren, die mit Tabellenwertparametern verbunden sind. Tabellentypen und reguläre Tabellen verwenden unterschiedliche Namespaces. Daher können Sie den gleichen Namen für einen Tabellentyp und eine tatsächliche Tabelle verwenden. Für diesen Fall wurde ein neues Anweisungsattribut ? SQL_SOPT_SS_NAME_SCOPE ? eingeführt. Dieses Attribut gibt an, ob SQLTables und andere Katalogfunktionen, die einen Tabellennamen als Parameter annehmen, den Tabellennamen als Namen einer tatsächlichen Tabelle oder den Namen eines Tabellentyps interpretieren sollen.  
  
 Eine Anwendung verwendet SQLColumns, um die Spalten für einen Tabellentyp auf die gleiche Weise zu bestimmen wie für persistente Tabellen, muss jedoch zunächst SQL_SOPT_SS_NAME_SCOPE festlegen, um anzugeben, dass sie mit Tabellentypen und nicht mit tatsächlichen Tabellen arbeitet. SQLPrimaryKeys kann auch mit Tabellentypen verwendet werden, wiederum mit SQL_SOPT_SS_NAME_SCOPE.  
  
 Beispielcode für dieses Szenario `demo_metadata_from_catalog_APIs` befindet sich in der Routine unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-for-a-prepared-statement"></a>Abrufen von Tabellenwertparameter-Metadaten für eine vorbereitete Anweisung  
 In diesem Szenario verwendet eine Anwendung SQLNumParameters und SQLDescribeParam, um Metadaten für Tabellenwertparameter abzurufen.  
  
 Das IPD-Feld SQL_CA_SS_TYPE_NAME wird verwendet, um den Typnamen für den Tabellenwertparameter abzurufen. Die IPD-Felder SQL_CA_SS_TYPE_SCHEMA_NAME und SQL_CA_SS_TYPE_CATALOG_NAME werden zum Abrufen seines Katalogs bzw. Schemas verwendet.  
  
 Tabellentypdefinitionen und Tabellenwertparameter müssen sich in der gleichen Datenbank befinden. SQLSetDescField meldet einen Fehler, wenn eine Anwendung SQL_CA_SS_TYPE_CATALOG_NAME festlegt, wenn Tabellenwertparameter verwendet werden.  
  
 SQL_CA_SS_TYPE_CATALOG_NAME und SQL_CA_SS_TYPE_SCHEMA_NAME können auch verwendet werden, um den Katalog und das Schema abzurufen, die mit Parametern des CLR-benutzerdefinierten Typs verbunden sind. SQL_CA_SS_TYPE_CATALOG_NAME und SQL_CA_SS_TYPE_SCHEMA_NAME sind Alternativen zu den vorhandenen typspezifischen Katalogschemaattributen für CLR-benutzerdefinierte Typen.  
  
 Eine Anwendung verwendet SQLColumns, um Spaltenmetadaten für einen Tabellenwertparameter auch in diesem Szenario abzurufen, da SQLDescribeParam keine Metadaten für die Spalten einer Tabellenwertparameterspalte zurückgibt.  
  
 Beispielcode für diesen Anwendungsfall `demo_metadata_from_prepared_statement` befindet sich in der Routine unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenbewertete Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
