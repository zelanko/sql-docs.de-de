---
description: Abrufen von Ausgabeparametern mithilfe von SQLGetData
title: Abrufen von Ausgabeparametern mit SQLGetData | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], retrieving output parameters
- output parameters [ODBC]
- retrieving output parameters [ODBC]
ms.assetid: 7a8c298a-2160-491d-a300-d36f45568d9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a31cb6baa015e2a90977d0112e770ce66fa8e62f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461382"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Abrufen von Ausgabeparametern mithilfe von SQLGetData
Vor ODBC 3,8 konnte eine Anwendung nur die Ausgabeparameter einer Abfrage mit einem gebundenen Ausgabepuffer abrufen. Es ist jedoch schwierig, einen sehr großen Puffer zuzuordnen, wenn die Größe des Parameter Werts sehr groß ist (z. b. ein großes Bild). Mit ODBC 3,8 wird eine neue Methode eingeführt, um Ausgabeparameter in Teilen abzurufen. Eine Anwendung kann nun **SQLGetData** mit einem kleinen Puffer mehrmals aufrufen, um einen großen Parameterwert abzurufen. Dies ähnelt dem Abrufen großer Spaltendaten.  
  
 Um einen Ausgabeparameter oder einen Eingabe-/Ausgabeparameter zu binden, der in Teilen abgerufen werden soll, nennen Sie **SQLBindParameter** , wobei das Argument *inputoutputtype* auf SQL_PARAM_OUTPUT_STREAM oder SQL_PARAM_INPUT_OUTPUT_STREAM festgelegt ist. Mit SQL_PARAM_INPUT_OUTPUT_STREAM kann eine Anwendung **SQLPutData** verwenden, um Daten in den-Parameter einzugeben, und dann **SQLGetData** zum Abrufen des Output-Parameters verwenden. Die Eingabedaten müssen sich im Formular Data-at-Execution (DAE) befinden, wobei **SQLPutData** anstelle der Bindung an einen vorab zugeordneten Puffer verwendet wird.  
  
 Diese Funktion kann von ODBC 3,8-Anwendungen oder neu kompilierten ODBC 3. x-und ODBC 2. x-Anwendungen verwendet werden. diese Anwendungen müssen über einen ODBC 3,8-Treiber verfügen, der das Abrufen von Ausgabeparametern mithilfe von **SQLGetData** und dem ODBC 3,8-Treiber-Manager unterstützt. Informationen dazu, wie Sie eine ältere Anwendung für die Verwendung neuer ODBC-Funktionen aktivieren, finden Sie unter [Kompatibilitäts Matrix](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Verwendungsbeispiel  
 Nehmen Sie beispielsweise an, Sie können eine gespeicherte Prozedur ausführen, **{callsp_f (?,?)}**, wobei beide Parameter als SQL_PARAM_OUTPUT_STREAM gebunden sind und die gespeicherte Prozedur kein Resultset zurückgibt (später in diesem Thema finden Sie ein komplexeres Szenario):  
  
1.  Zum Aufrufen von **SQLBindParameter** mit *inputoutputtype* auf SQL_PARAM_OUTPUT_STREAM und *ParameterValuePtr* auf ein Token festgelegt, z. b. eine Parameter Nummer, einen Zeiger auf Daten oder einen Zeiger auf eine-Struktur, die die Anwendung verwendet, um Eingabeparameter zu binden. In diesem Beispiel wird die Ordinalzahl des Parameters als Token verwendet.  
  
2.  Führen Sie die Abfrage mit **SQLExecDirect** oder **SQLExecute**aus. SQL_PARAM_DATA_AVAILABLE wird zurückgegeben und gibt an, dass Streaming-Ausgabeparameter für den Abruf verfügbar sind.  
  
3.  Aufrufen von **SQLParamData** zum Abrufen des Parameters, der zum Abrufen verfügbar ist. **SQLParamData** gibt SQL_PARAM_DATA_AVAILABLE mit dem Token des ersten verfügbaren Parameters zurück, der in **SQLBindParameter** (Schritt 1) festgelegt ist. Das Token wird im Puffer zurückgegeben, auf den " *ValuePtrPtr* " verweist.  
  
4.  Rufen Sie **SQLGetData** mit dem Argument *Col*_or \_ *Param_Num* auf die Ordnungszahl des Parameters festzulegen, um die Daten des ersten verfügbaren Parameters abzurufen. Gibt **SQLGetData** SQL_SUCCESS_WITH_INFO und SQLSTATE 01004 (Daten abgeschnitten) zurück, und der Typ ist eine Variable Länge sowohl auf dem Client als auch auf dem Server, gibt es weitere Daten, die aus dem ersten verfügbaren Parameter abgerufen werden müssen. Sie können **SQLGetData** weiterhin aufrufen, bis SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO mit einem anderen **SQLSTATE**-Wert zurückgegeben wird.  
  
5.  Wiederholen Sie Schritt 3 und Schritt 4, um den aktuellen Parameter abzurufen.  
  
6.  **SQLParamData** erneut aufzurufen. Wenn Sie nur SQL_PARAM_DATA_AVAILABLE zurückgibt, gibt es keine weiteren streamingparameterdaten, die abgerufen werden können, und der Rückgabecode ist der Rückgabecode der nächsten Anweisung, die ausgeführt wird.  
  
7.  Ruft **SQLMoreResults** auf, um den nächsten Satz von Parametern zu verarbeiten, bis SQL_NO_DATA zurückgegeben wird. **SQLMoreResults** gibt SQL_NO_DATA in diesem Beispiel zurück, wenn das Anweisungs Attribut SQL_ATTR_PARAMSET_SIZE auf 1 festgelegt wurde. Andernfalls gibt **SQLMoreResults** SQL_PARAM_DATA_AVAILABLE zurück, um anzugeben, dass streamingausgabeparameter für die nächste Gruppe von Parametern verfügbar sind, die abgerufen werden sollen.  
  
 Ähnlich wie bei einem DAE-Eingabeparameter kann das Token, das im Argument *ParameterValuePtr* in **SQLBindParameter** (Schritt 1) verwendet wird, ein Zeiger sein, der auf eine Anwendungsdaten Struktur zeigt, die die Ordinalzahl des Parameters und ggf. weitere anwendungsspezifische Informationen enthält.  
  
 Die Reihenfolge der zurückgegebenen Stream-Ausgabe-oder Eingabe-/Ausgabeparameter ist Treiber spezifisch und nicht immer identisch mit der in der Abfrage angegebenen Reihenfolge.  
  
 Wenn die Anwendung **SQLGetData** in Schritt 4 nicht aufruft, wird der Parameterwert verworfen. Ebenso gilt: Wenn die Anwendung **SQLParamData** aufruft, bevor der gesamte Parameterwert von **SQLGetData**gelesen wurde, wird der Rest des Werts verworfen, und die Anwendung kann den nächsten Parameter verarbeiten.  
  
 Wenn die Anwendung **SQLMoreResults** aufruft, bevor alle gestreuten Ausgabeparameter verarbeitet werden (**SQLParamData** gibt immer noch SQL_PARAM_DATA_AVAILABLE zurück), werden alle verbleibenden Parameter verworfen. Ebenso gilt: Wenn die Anwendung **SQLMoreResults** aufruft, bevor der gesamte Parameterwert von **SQLGetData**gelesen wurde, werden der restliche Wert und alle verbleibenden Parameter verworfen, und die Anwendung kann den nächsten Parametersatz weiterhin verarbeiten.  
  
 Beachten Sie, dass eine Anwendung den C-Datentyp sowohl in **SQLBindParameter** als auch in **SQLGetData**angeben kann. Der mit **SQLGetData** angegebene c-Datentyp überschreibt den in **SQLBindParameter**angegebenen c-Datentyp, es sei denn, der in **SQLGetData** angegebene c-Datentyp ist SQL_APD_TYPE.  
  
 Obwohl ein Stream-Ausgabeparameter nützlicher ist, wenn der Datentyp des Output-Parameters vom Typ BLOB ist, kann diese Funktion auch mit jedem Datentyp verwendet werden. Die von gestreuten Ausgabeparametern unterstützten Datentypen werden im Treiber angegeben.  
  
 Wenn SQL_PARAM_INPUT_OUTPUT_STREAM zu verarbeitende Parameter vorhanden sind, werden **SQLExecute** oder **SQLExecDirect** zuerst SQL_NEED_DATA zurückgegeben. Eine Anwendung kann **SQLParamData** und **SQLPutData** aufrufen, um die DAE-Parameterdaten zu senden. Wenn alle DAE-Eingabeparameter verarbeitet werden, gibt **SQLParamData** SQL_PARAM_DATA_AVAILABLE zurück, um anzugeben, dass gestreamte Ausgabeparameter verfügbar sind.  
  
 Wenn übertragene Ausgabeparameter und gebundene Ausgabeparameter verarbeitet werden, bestimmt der Treiber die Reihenfolge für die Verarbeitung von Ausgabeparametern. Wenn ein Ausgabeparameter an einen Puffer gebunden ist (der **SQLBindParameter** -Parameter *inputoutputtype* ist auf SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT festgelegt), wird der Puffer möglicherweise erst aufgefüllt, wenn **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgibt. Eine Anwendung sollte einen gebundenen Puffer nur lesen, nachdem **SQLParamData** SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben hat, nachdem alle gestreuten Ausgabeparameter verarbeitet wurden.  
  
 Die Datenquelle kann zusätzlich zum gestreuten Ausgabeparameter eine Warnung und ein Resultset zurückgeben. Im Allgemeinen werden Warnungen und Resultsets getrennt von einem gestreamt-Ausgabeparameter durch Aufrufen von **SQLMoreResults**verarbeitet. Prozess Warnungen und das Resultset vor der Verarbeitung des gestreuten Ausgabe Parameters.  
  
 In der folgenden Tabelle werden die verschiedenen Szenarien eines einzelnen Befehls, der an den Server gesendet wird, und die Funktionsweise der Anwendung beschrieben.  
  
|Szenario|Rückgabewert von SQLExecute oder SQLExecDirect|Nächste Schritte|  
|--------------|---------------------------------------------------|---------------------|  
|Daten enthalten nur gestreamt Ausgabeparameter.|SQL_PARAM_DATA_AVAILABLE|Verwenden Sie **SQLParamData** und **SQLGetData** , um gestreute Ausgabeparameter abzurufen.|  
|Daten enthalten ein Resultset und per Streaming übertragene Ausgabeparameter.|SQL_SUCCESS|Rufen Sie das Resultset mit **SQLBindCol** und **SQLGetData**ab.<br /><br /> Öffnen Sie **SQLMoreResults** , um die Verarbeitung von gestreuten Ausgabeparametern zu starten. SQL_PARAM_DATA_AVAILABLE sollte zurückgegeben werden.<br /><br /> Verwenden Sie **SQLParamData** und **SQLGetData** , um gestreute Ausgabeparameter abzurufen.|  
|Die Daten enthalten eine Warnmeldung und per Streaming übertragene Ausgabeparameter.|SQL_SUCCESS_WITH_INFO|Verwenden Sie **SQLGetDiagRec** und **SQLGetDiagField** , um Warnmeldungen zu verarbeiten.<br /><br /> Öffnen Sie **SQLMoreResults** , um die Verarbeitung von gestreuten Ausgabeparametern zu starten. SQL_PARAM_DATA_AVAILABLE sollte zurückgegeben werden.<br /><br /> Verwenden Sie **SQLParamData** und **SQLGetData** , um gestreute Ausgabeparameter abzurufen.|  
|Zu den Daten gehören eine Warnmeldung, ein Resultset und übertragene Ausgabeparameter.|SQL_SUCCESS_WITH_INFO|Verwenden Sie **SQLGetDiagRec** und **SQLGetDiagField** , um Warnmeldungen zu verarbeiten. Anschließend wird **SQLMoreResults** aufgerufen, um mit der Verarbeitung des Resultsets zu beginnen.<br /><br /> Rufen Sie ein Resultset mit **SQLBindCol** und **SQLGetData**ab.<br /><br /> Öffnen Sie **SQLMoreResults** , um die Verarbeitung von gestreuten Ausgabeparametern zu starten. **SQLMoreResults** sollte SQL_PARAM_DATA_AVAILABLE zurückgeben.<br /><br /> Verwenden Sie **SQLParamData** und **SQLGetData** , um gestreute Ausgabeparameter abzurufen.|  
|Abfragen mit DAE-Eingabe Parametern, z. b. ein gestreamter Eingabe-/Ausgabeparameter (DAE)|SQL-NEED_DATA|Aufrufen von **SQLParamData** und **SQLPutData** zum Senden von DAE-Eingabeparameter Daten.<br /><br /> Nachdem alle DAE-Eingabeparameter verarbeitet wurden, können von **SQLParamData** alle Rückgabecodes zurückgegeben werden, die von **SQLExecute** und **SQLExecDirect** zurückgegeben werden können. Die Fälle in dieser Tabelle können dann angewendet werden.<br /><br /> Wenn der Rückgabecode SQL_PARAM_DATA_AVAILABLE ist, sind gestreamt-Ausgabeparameter verfügbar. Eine Anwendung muss **SQLParamData** erneut aufrufen, um das Token für den gestreuten Ausgabeparameter abzurufen, wie in der ersten Zeile dieser Tabelle beschrieben.<br /><br /> Wenn der Rückgabecode SQL_SUCCESS ist, muss entweder ein Resultset verarbeitet werden, oder die Verarbeitung ist fertiggestellt.<br /><br /> Wenn der Rückgabecode SQL_SUCCESS_WITH_INFO ist, werden Warnmeldungen verarbeitet.|  
  
 Nachdem **SQLExecute**, **SQLExecDirect**oder **SQLMoreResults** SQL_PARAM_DATA_AVAILABLE zurückgegeben hat, führt dies zu einem Funktions Sequenz Fehler, wenn eine Anwendung eine Funktion aufruft, die nicht in der folgenden Liste enthalten ist:  
  
-   **Sqlzuweisung**  /  **Sqlzuweisung**  
  
-   **SQLDataSources**  /  **SQLDrivers**  
  
-   **SQLGetInfo**  /  **SQLGetFunctions**  
  
-   **SQLGetConnectAttr**  /  **SQLGetEnvAttr**  /  **SQLGetDescField**  /  **Sqlgetdebug**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField**  /  **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **Sqlcancelhandle** (mit Anweisungs Handle)  
  
-   **SQLFreeStmt** (with Option = SQL_CLOSE, SQL_DROP oder SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (mit dem Typ "Lenker" = SQL_HANDLE_STMT)  
  
-   **'SQLGetStmtAttr'**  
  
 Anwendungen können weiterhin **SQLSetDescField** oder **SQLSetDescRec** verwenden, um die Bindungs Informationen festzulegen. Die Feld Zuordnung wird nicht geändert. Allerdings können Felder innerhalb des Deskriptors neue Werte zurückgeben. Beispielsweise können SQL_DESC_PARAMETER_TYPE SQL_PARAM_INPUT_OUTPUT_STREAM oder SQL_PARAM_OUTPUT_STREAM zurückgeben.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Verwendungs Szenario: Abrufen eines Bilds in Teilen aus einem Resultset  
 **SQLGetData** kann verwendet werden, um Daten in Teilen zu erhalten, wenn eine gespeicherte Prozedur ein Resultset zurückgibt, das eine Zeile mit Metadaten zu einem Bild enthält, und das Bild in einem großen Ausgabeparameter zurückgegeben wird.  
  
```  
// CREATE PROCEDURE SP_TestOutputPara  
//      @ID_of_picture   as int,  
//      @Picture         as varbinary(max) out  
// AS  
//     output the image data through streamed output parameter  
// GO  
BOOL displayPicture(SQLUINTEGER idOfPicture, SQLHSTMT hstmt) {  
   SQLLEN      lengthOfPicture;    // The actual length of the picture.  
   BYTE        smallBuffer[100];   // A very small buffer.  
   SQLRETURN   retcode, retcode2;  
  
   // Bind the first parameter (input parameter)  
   SQLBindParameter(  
         hstmt,  
         1,                         // The first parameter.   
         SQL_PARAM_INPUT,           // Input parameter: The ID_of_picture.  
         SQL_C_ULONG,               // The C Data Type.  
         SQL_INTEGER,               // The SQL Data Type.  
         0,                         // ColumnSize is ignored for integer.  
         0,                         // DecimalDigits is ignored for integer.  
         &idOfPicture,              // The Address of the buffer for the input parameter.  
         0,                         // BufferLength is ignored for integer.  
         NULL);                     // This is ignored for integer.  
  
   // Bind the streamed output parameter.  
   SQLBindParameter(  
         hstmt,   
         2,                         // The second parameter.  
         SQL_PARAM_OUTPUT_STREAM,   // A streamed output parameter.   
         SQL_C_BINARY,              // The C Data Type.    
         SQL_VARBINARY,             // The SQL Data Type.  
         0,                         // ColumnSize: The maximum size of varbinary(max).  
         0,                         // DecimalDigits is ignored for binary type.  
         (SQLPOINTER)2,             // ParameterValuePtr: An application-defined  
                                    // token (this will be returned from SQLParamData).  
                                    // In this example, we used the ordinal   
                                    // of the parameter.  
         0,                         // BufferLength is ignored for streamed output parameters.  
         &lengthOfPicture);         // StrLen_or_IndPtr: The status variable returned.   
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestOutputPara(?, ?)}", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Assume that the retrieved picture exists.  Use SQLBindCol or SQLGetData to retrieve the result-set.  
  
   // Process the result set and move to the streamed output parameters.  
   retcode = SQLMoreResults( hstmt );  
  
   // SQLGetData retrieves and displays the picture in parts.  
   // The streamed output parameter is available.  
   while (retcode == SQL_PARAM_DATA_AVAILABLE) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;      // #bytes remained  
      retcode = SQLParamData(hstmt, &token);   // returned token is 2 (according to the binding)  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         // A do-while loop retrieves the picture in parts.  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }  
  
   return TRUE;  
}  
```  
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Verwendungs Szenario: senden und Empfangen einer Large Object als per Streaming übertragenes Eingabe-/Ausgabeparameter  
 **SQLGetData** kann verwendet werden, um Daten in Teilen zu erhalten und zu senden, wenn eine gespeicherte Prozedur ein großes Objekt als Eingabe-/Ausgabeparameter übergibt und den Wert auf die und aus der Datenbank übergibt. Sie müssen nicht alle Daten im Arbeitsspeicher speichern.  
  
```  
// CREATE PROCEDURE SP_TestInOut  
//       @picture as varbinary(max) out  
// AS  
//    output the image data through output parameter   
// go  
  
BOOL displaySimilarPicture(BYTE* image, ULONG lengthOfImage, SQLHSTMT hstmt) {  
   BYTE smallBuffer[100];   // A very small buffer.  
   SQLRETURN retcode, retcode2;  
   SQLLEN statusOfPicture;  
  
   // First bind the parameters, before preparing the statement that binds the output streamed parameter.  
   SQLBindParameter(  
      hstmt,   
      1,                                 // The first parameter.  
      SQL_PARAM_INPUT_OUTPUT_STREAM,     // I/O-streamed parameter: The Picture.  
      SQL_C_BINARY,                      // The C Data Type.  
      SQL_VARBINARY,                     // The SQL Data Type.  
      0,                                 // ColumnSize: The maximum size of varbinary(max).  
      0,                                 // DecimalDigits is ignored.   
      (SQLPOINTER)1,                     // An application defined token.   
      0,                                 // BufferLength is ignored for streamed I/O parameters.  
      &statusOfPicture);                 // The status variable.  
  
   statusOfPicture = SQL_DATA_AT_EXEC;   // Input data in parts (DAE parameter at input).  
  
   retcode = SQLPrepare(hstmt, L"{call SP_TestInOut(?) }", SQL_NTS);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   // Execute the statement.  
   retcode = SQLExecute(hstmt);  
   if ( retcode == SQL_ERROR )  
      return FALSE;  
  
   if ( retcode == SQL_NEED_DATA ) {  
      // Use SQLParamData to loop through DAE input parameters.  For  
      // each, use SQLPutData to send the data to database in parts.  
  
      // This example uses an I/O parameter with streamed output.  
      // Therefore, the last call to SQLParamData should return  
      // SQL_PARAM_DATA_AVAILABLE to indicate the end of the input phrase   
      // and report that a streamed output parameter is available.  
  
      // Assume retcode is set to the return value of the last call to  
      // SQLParamData, which is equal to SQL_PARAM_DATA_AVAILABLE.  
   }  
  
   // Start processing the streamed output parameters.  
   while ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
      SQLPOINTER token;   // Output by SQLParamData.  
      SQLLEN cbLeft;     // #bytes remained  
      retcode = SQLParamData(hstmt, &token);  
      if ( retcode == SQL_PARAM_DATA_AVAILABLE ) {  
         do {  
            retcode2 = SQLGetData(   
               hstmt,   
               (UWORD) token,          // the value of the token is the ordinal.   
               SQL_C_BINARY,           // The C-type.  
               smallBuffer,            // A small buffer.   
               sizeof(smallBuffer),    // The size of the buffer.  
               &cbLeft);               // How much data we can get.  
         }  
         while ( retcode2 == SQL_SUCCESS_WITH_INFO );  
      }  
   }   
  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md)
