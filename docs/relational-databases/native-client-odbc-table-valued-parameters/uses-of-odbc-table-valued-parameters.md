---
title: Verwendungen von ODBC-Tabellenwert Parametern | Microsoft-Dokumentation
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
ms.openlocfilehash: 5be9838e0c4e989c6b802d9c74e240a0d01c354b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715319"
---
# <a name="uses-of-odbc-table-valued-parameters"></a>Verwendungen von ODBC-Tabellenwertparametern
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  In diesem Thema werden die wichtigsten Benutzerszenarien für die Verwendung von Tabellenwertparametern mit ODBC erläutert:  
  
-   Tabellenwertparameter mit vollständig gebundenen mehrzeiligen Puffern (Senden von Daten als Tabellenwertparameter mit allen Werten im Arbeitsspeicher)  
  
-   Tabellenwertparameter mit Zeilenstreaming (Senden von Daten als Tabellenwertparameter mithilfe von Data-at-Execution)  
  
-   Abrufen von Tabellenwertparameter-Metadaten aus dem Systemkatalog  
  
-   Abrufen von Tabellenwertparameter-Metadaten für eine vorbereitete Anweisung  
  
## <a name="table-valued-parameter-with-fully-bound-multirow-buffers-send-data-as-a-tvp-with-all-values-in-memory"></a>Tabellenwertparameter mit vollständig gebundenen mehrzeiligen Puffern (Senden von Daten als Tabellenwertparameter mit allen Werten im Arbeitsspeicher)  
 Bei der Verwendung mit vollständig gebundenen mehrzeiligen Puffern sind alle Parameterwerte im Arbeitsspeicher verfügbar. Dies ist beispielsweise für eine OLTP-Transaktion typisch, bei der Tabellenwertparameter in eine einzeln gespeicherte Prozedur gepackt werden können. Ohne Tabellenwertparameter wären mehrere Serveraufrufe oder die dynamische Generierung eines komplexen Batches mit mehreren Anweisungen erforderlich.  
  
 Der Tabellenwert Parameter selbst wird mithilfe von [SQLBindParameter](https://go.microsoft.com/fwlink/?LinkId=59328) zusammen mit den anderen Parametern gebunden. Nachdem alle Parameter gebunden wurden, legt die Anwendung für jeden Tabellenwert Parameter das Parameter Fokus Attribut (SQL_SOPT_SS_PARAM_FOCUS) fest und ruft SQLBindParameter für die Spalten des Tabellenwert Parameters auf.  
  
 Der Servertyp für Tabellenwertparameter ist SQL_SS_TABLE, ein neuer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-spezifischer Typ. Der C-Bindungstyp für SQL_SS_TABLE muss stets SQL_C_DEFAULT sein. Für den gebundenen Parameter des Tabellenwertparameters werden keine Daten übertragen. Dieser wird zur Übergabe von Tabellenmetadaten und zur Steuerung der Datenübergabe in die einzelnen Spalten des Tabellenwertparameters verwendet.  
  
 Die Länge des Tabellenwertparameters ist auf die Anzahl der an den Server gesendeten Zeilen festgelegt. Der *ColumnSize* -Parameter von SQLBindParameter für einen Tabellenwert Parameter gibt die maximale Anzahl von Zeilen an, die gesendet werden können. Dies ist die Array Größe der Spalten Puffer. *ParameterValuePtr* ist der Parameter Puffer für einen Tabellenwert Parameter in SQLBindParameter. *ParameterValuePtr* und die zugehörige *BufferLength* werden verwendet, um bei Bedarf den Typnamen des Tabellenwert Parameters zu übergeben. Der Typname wird nicht für gespeicherte Prozeduraufrufe benötigt, er ist jedoch für SQL-Anweisungen erforderlich.  
  
 Wenn ein Tabellenwert Parameter-Typname für einen SQLBindParameter-Befehl angegeben wird, muss er immer als Unicode-Wert angegeben werden, auch in Anwendungen, die als ANSI-Anwendungen erstellt werden. Wenn Sie mithilfe von SQLSetDescField einen Typnamen für einen Tabellenwert Parameter angeben, können Sie einen Literalwert verwenden, der der Art und Weise entspricht, in der die Anwendung erstellt wird. Der ODBC-Treiber-Manager führt die eventuell erforderliche Unicode-Konvertierung aus.  
  
 Metadaten für Tabellenwert Parameter und Tabellenwert Parameter-Spalten können einzeln und explizit mithilfe von SQLGetDescRec, SQLSetDescRec, SQLGetDescField und SQLSetDescField bearbeitet werden. Das Überladen von SQLBindParameter ist jedoch in der Regel bequemer und erfordert in den meisten Fällen keinen expliziten deskriptorzugriff. Diese Vorgehensweise ist mit der Definition von SQLBindParameter für andere Datentypen konsistent, mit dem Unterschied, dass für einen Tabellenwert Parameter die betroffenen Deskriptorfelder leicht abweichen.  
  
 Manchmal verwendet eine Anwendung einen Tabellenwertparameter mit dynamischem SQL, und der Name des Tabellenwertparameters muss bereitgestellt werden. Wenn dies der Fall ist und der Tabellenwert Parameter nicht im aktuellen Standardschema für die Verbindung definiert ist, müssen SQL_CA_SS_TYPE_CATALOG_NAME und SQL_CA_SS_TYPE_SCHEMA_NAME mithilfe von SQLSetDescField festgelegt werden. Da Tabellentypdefinitionen und Tabellenwertparameter in derselben Datenbank vorliegen müssen, darf SQL_CA_SS_TYPE_CATALOG_NAME nicht festgelegt werden, wenn die Anwendung Tabellenwertparameter verwendet. Andernfalls meldet SQLSetDescField einen Fehler.  
  
 Beispielcode für dieses Szenario finden Sie unter `demo_fixed_TVP_binding` Verwenden von [Tabellenwert Parametern &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="table-valued-parameter-with-row-streaming-send-data-as-a-tvp-using-data-at-execution"></a>Tabellenwertparameter mit Zeilenstreaming (Senden von Daten als Tabellenwertparameter mithilfe von Data-at-Execution)  
 In diesem Szenario stellt die Anwendung dem Treiber Zeilen nach Anforderung bereit. Diese werden an den Server gestreamt. Hierdurch wird das Puffern aller Zeilen im Arbeitsspeicher vermieden. Dies ist für Masseneinfügungs-/-updateszenarien repräsentativ. Tabellenwertparameter bieten eine Leistungsfähigkeit, die zwischen Parameterarrays und Massenkopieren liegt. Tabellenwertparameter sind ebenso einfach zu programmieren wie Parameterarrays, sie bieten jedoch eine größere Flexibilität auf dem Server.  
  
 Das Binden des Tabellenwertparameters und der zugehörigen Spalten erfolgt wie im vorherigen Abschnitt "Tabellenwertparameter mit vollständig gebundenen mehrzeiligen Puffern" beschrieben, der Längenindikator des Tabellenwertparameters selbst wird jedoch auf SQL_DATA_AT_EXEC festgelegt. Der Treiber antwortet auf SQLExecute oder SQLExecuteDirect auf die übliche Weise bei Data-at-Execution-Parametern, d. h. durch Zurückgeben von SQL_NEED_DATA. Wenn der Treiber bereit ist, Daten für einen Tabellenwert Parameter zu akzeptieren, gibt SQLParamData den Wert von *ParameterValuePtr* in SQLBindParameter zurück.  
  
 Eine Anwendung verwendet SQLPutData für einen Tabellenwert Parameter, um die Verfügbarkeit von Daten für die einzelnen Tabellenwert Parameter-Spalten anzugeben. Wenn SQLPutData für einen Tabellenwert Parameter aufgerufen wird, muss *DataPtr* immer NULL sein, und *StrLen_Or_Ind* muss entweder 0 oder eine Zahl sein, die kleiner oder gleich der für Tabellenwert Parameter-Puffer angegebenen Array Größe ist (der *ColumnSize* -Parameter von SQLBindParameter). Der Wert 0 gibt an, dass keine weiteren Zeilen für den Tabellenwertparameter vorhanden sind, und der Treiber fährt mit der Verarbeitung des nächsten tatsächlichen Prozedurparameters fort. Wenn *StrLen_Or_Ind* nicht 0 ist, verarbeitet der Treiber die einzelnen Tabellenwert Parameter-Spalten auf dieselbe Weise wie Parameter gebundene Parameter, die nicht Tabellenwert Parameter sind: jede Tabellenwert Parameter-Spalte kann die tatsächliche Daten Länge angeben, SQL_NULL_DATA, oder Sie kann Daten bei der Ausführung über Ihren Längen-/Indikatorpuffer angeben. Tabellenwert Parameter-Spaltenwerte können von wiederholten Aufrufen von SQLPutData wie gewohnt übergeben werden, wenn ein Zeichen-oder Binärwert in Teile übergeben werden soll.  
  
 Nachdem alle Tabellenwertparameter-Spalten verarbeitet wurden, kehrt der Treiber zum Tabellenwertparameter zurück, um weitere Tabellenwertparameter-Datenzeilen zu verarbeiten. Bei Data-at-Execution-Tabellenwertparametern führt der Treiber daher nicht den üblichen sequenziellen Scan gebundener Parameter durch. Ein gebundener Tabellenwert Parameter wird abgerufen, bis SQLPutData mit *StrLen_Or_IndPtr* gleich 0 aufgerufen wird. zu diesem Zeitpunkt überspringt der Treiber Tabellenwert Parameter-Spalten und wechselt zum nächsten tatsächlichen Parameter der gespeicherten Prozedur.  Wenn SQLPutData einen Indikator Wert größer oder gleich 1 übergibt, verarbeitet der Treiber Tabellenwert Parameter-Spalten und-Zeilen sequenziell, bis er über Werte für alle gebundenen Zeilen und Spalten verfügt. Anschließend kehrt der Treiber zum Tabellenwertparameter zurück. Zwischen dem empfangen des Tokens für den Tabellenwert Parameter von SQLParamData und dem Aufruf von SQLPutData (hstmt, NULL, n) für einen Tabellenwert Parameter muss die Anwendung Tabellenwert Parameter-Spaltendaten und Indikator Puffer Inhalte für die nächste Zeile oder Zeilen festlegen, die an den Server übergeben werden.  
  
 Beispielcode für dieses Szenario finden Sie in der Routine `demo_variable_TVP_binding` unter [Verwenden von Tabellenwert Parametern &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-from-the-system-catalog"></a>Abrufen von Tabellenwertparameter-Metadaten aus dem Systemkatalog  
 Wenn eine Anwendung sqlprocedurecolenns für eine Prozedur mit Tabellenwert Parameter-Parametern aufruft, wird data_type als SQL_SS_TABLE zurückgegeben, und TYPE_NAME ist der Name des Tabellentyps für den Tabellenwert Parameter. Dem Resultset, das von sqlprocedurecolrens zurückgegeben wird, werden zwei weitere Spalten hinzugefügt: SS_TYPE_CATALOG_NAME gibt den Namen des Katalogs zurück, in dem der Tabellentyp des Tabellenwert Parameters definiert ist, und SS_TYPE_SCHEMA_NAME gibt den Namen des Schemas zurück, in dem der Tabellentyp des Tabellenwert Parameters definiert ist. In Übereinstimmung mit der ODBC-Spezifikation werden SS_TYPE_CATALOG_NAME und SS_TYPE_SCHEMA_NAME vor allen treiberspezifischen Spalten angezeigt, die in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hinzugefügt wurden sowie nach allen Spalten, die von ODBC selbst benötigt werden.  
  
 Die neuen Spalten werden nicht nur für Tabellenwertparameter, sondern auch für Parameter des CLR-benutzerdefinierten Typs aufgefüllt. Die vorhandenen Schema- und Katalogspalten von Parametern des benutzerdefinierten Typs werden noch aufgefüllt, in Zukunft wird die Anwendungsentwicklung jedoch durch gemeinsame Schema- und Katalogspalten für Datentypen, die diese erfordern, erleichtert. (Beachten Sie, dass XML-Schemaauflistungen einige Unterschiede aufweisen und nicht in dieser Änderung enthalten sind.)  
  
 Eine Anwendung verwendet SQLTables, um die Namen von Tabellentypen auf die gleiche Weise zu bestimmen wie für persistente Tabellen, Systemtabellen und Sichten. Die Einführung eines neuen Tabellentyps ? TABLE TYPE ? ermöglicht es einer Anwendung, Tabellentypen zu identifizieren, die mit Tabellenwertparametern verbunden sind. Tabellentypen und reguläre Tabellen verwenden unterschiedliche Namespaces. Daher können Sie den gleichen Namen für einen Tabellentyp und eine tatsächliche Tabelle verwenden. Für diesen Fall wurde ein neues Anweisungsattribut ? SQL_SOPT_SS_NAME_SCOPE ? eingeführt. Dieses Attribut gibt an, ob SQLTables und andere Katalog Funktionen, die einen Tabellennamen als Parameter annehmen, den Tabellennamen als den Namen einer tatsächlichen Tabelle oder den Namen eines Tabellentyps interpretieren sollen.  
  
 Eine Anwendung verwendet SQLColumns, um die Spalten für einen Tabellentyp auf die gleiche Weise zu bestimmen wie für persistente Tabellen, muss jedoch zuerst SQL_SOPT_SS_NAME_SCOPE festlegen, um anzugeben, dass Sie mit Tabellentypen anstelle tatsächlicher Tabellen arbeitet. SQLPrimaryKeys kann auch mit Tabellentypen verwendet werden, und zwar mithilfe von SQL_SOPT_SS_NAME_SCOPE.  
  
 Beispielcode für dieses Szenario finden Sie in der Routine `demo_metadata_from_catalog_APIs` unter [Verwenden von Tabellenwert Parametern &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="retrieving-table-valued-parameter-metadata-for-a-prepared-statement"></a>Abrufen von Tabellenwertparameter-Metadaten für eine vorbereitete Anweisung  
 In diesem Szenario verwendet eine Anwendung SQLNumParameters und SQLDescribeParam, um Metadaten für Tabellenwert Parameter abzurufen.  
  
 Das IPD-Feld SQL_CA_SS_TYPE_NAME wird verwendet, um den Typnamen für den Tabellenwertparameter abzurufen. Die IPD-Felder SQL_CA_SS_TYPE_SCHEMA_NAME und SQL_CA_SS_TYPE_CATALOG_NAME werden zum Abrufen seines Katalogs bzw. Schemas verwendet.  
  
 Tabellentypdefinitionen und Tabellenwertparameter müssen sich in der gleichen Datenbank befinden. SQLSetDescField meldet einen Fehler, wenn eine Anwendung SQL_CA_SS_TYPE_CATALOG_NAME festlegt, wenn Tabellenwert Parameter verwendet werden.  
  
 SQL_CA_SS_TYPE_CATALOG_NAME und SQL_CA_SS_TYPE_SCHEMA_NAME können auch verwendet werden, um den Katalog und das Schema abzurufen, die mit Parametern des CLR-benutzerdefinierten Typs verbunden sind. SQL_CA_SS_TYPE_CATALOG_NAME und SQL_CA_SS_TYPE_SCHEMA_NAME sind Alternativen zu den vorhandenen typspezifischen Katalogschemaattributen für CLR-benutzerdefinierte Typen.  
  
 Eine Anwendung verwendet SQLColumns auch zum Abrufen von Spalten Metadaten für einen Tabellenwert Parameter in diesem Szenario, da SQLDescribeParam keine Metadaten für die Spalten einer Tabellenwert Parameter-Spalte zurückgibt.  
  
 Der Beispielcode für diesen Anwendungsfall befindet sich in der Routine `demo_metadata_from_prepared_statement` in [Verwenden von Tabellenwert Parametern &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwert Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
