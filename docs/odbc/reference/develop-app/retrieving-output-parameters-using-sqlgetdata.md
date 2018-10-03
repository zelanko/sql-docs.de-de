---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ebb09b3118c2d16041d4ca60bf738d0fda561346
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837358"
---
# <a name="retrieving-output-parameters-using-sqlgetdata"></a>Abrufen von Ausgabeparametern mithilfe von SQLGetData
Bevor Sie ODBC 3.8 konnte eine Anwendung nur die Output-Parameter, der eine Abfrage mit einer gebundenen Ausgabepuffer abrufen. Allerdings ist es schwierig, die einen sehr großen Puffer zuzuweisen, wenn die Größe des Parameterwerts sehr groß ist (z. B. ein großes Bild). ODBC 3.8 bietet neue Möglichkeiten zum Abrufen von Ausgabeparametern in Teilen. Eine Anwendung kann jetzt Aufrufen **SQLGetData** mit einem kleinen Puffer mehrere Male auf, um einen großen Parameterwert abzurufen. Dies ist für das Abrufen von großen Spaltendaten vergleichbar.  
  
 Rufen Sie zum Binden einer Output-Parameter oder Eingabe-/Ausgabeparameter in Teilen abgerufen werden sollen **SQLBindParameter** mit der *InputOutputType* Argument festgelegt wird, um SQL_PARAM_OUTPUT_STREAM oder SQL_PARAM_INPUT_OUTPUT an _STREAM. Eine Anwendung kann mit SQL_PARAM_INPUT_OUTPUT_STREAM, verwenden **SQLPutData** Daten an den Parameter eingeben, und klicken Sie dann verwenden **SQLGetData** zum Abrufen des Output-Parameters. Die Eingabedaten muss in der Data-at-Execution-(. DAE) bilden, mit **SQLPutData** statt an einen vorab zugeordneten Puffer.  
  
 Dieses Feature von ODBC 3.8-Anwendungen verwendet werden können oder erneut kompiliert ODBC 3.x und ODBC 2.x-Anwendungen und diese Anwendungen benötigen einen ODBC 3.8-Treiber, unterstützt beim Abrufen von Ausgabeparametern mit **SQLGetData** und ODBC 3.8-Treiber -Manager. Informationen dazu, wie Sie eine ältere Anwendung neue ODBC-Funktionen verwenden kann, finden Sie unter [Matrix der Sperrenkompatibilität](../../../odbc/reference/develop-app/compatibility-matrix.md).  
  
## <a name="usage-example"></a>Verwendungsbeispiel  
 Betrachten Sie z. B. das Ausführen einer gespeicherten Prozedur, **{AUFRUF sp_f(?,?)}** , wobei beide Parameter werden als SQL_PARAM_OUTPUT_STREAM gebunden, und die gespeicherte Prozedur kein Resultset zurückgegeben (weiter unten in diesem Thema finden Sie ein komplexeres Szenario):  
  
1.  Rufen Sie für jeden Parameter **SQLBindParameter** mit *InputOutputType* SQL_PARAM_OUTPUT_STREAM festgelegt und *ParameterValuePtr* zu einem Token, z. B. ein Parameter mit der Nummer festlegen , ein Zeiger auf Daten oder ein Zeiger auf eine Struktur, die die Anwendung verwendet, um Parameter zu binden. In diesem Beispiel wird die Ordnungszahl des Parameters als das Token verwendet.  
  
2.  Führen Sie die Abfrage mit **SQLExecDirect** oder **SQLExecute**. SQL_PARAM_DATA_AVAILABLE wird zurückgegeben, der angibt, dass gestreamte Output-Parameter verfügbar sind für den Abruf.  
  
3.  Rufen Sie **SQLParamData** zum Abrufen des Parameters, der für den Abruf verfügbar ist. **SQLParamData** SQL_PARAM_DATA_AVAILABLE zurückgegeben wird, mit dem Token des ersten verfügbaren Parameters, der festgelegt wird, in **SQLBindParameter** (Schritt 1). Das Token wird im Puffer zurückgegeben, die die *ValuePtrPtr* verweist auf.  
  
4.  Rufen Sie **SQLGetData** mit dem Argument *Col*_or\_*Param_Num* an den Parameter zum Abrufen der Daten von den ersten verfügbaren Parameter Ordnungszahl festgelegt. Wenn **SQLGetData** gibt SQL_SUCCESS_WITH_INFO und SQLState 01004 (Daten wurden abgeschnitten), und der Typ eine Variable Länge auf dem Client und Server ist, weitere Daten aus dem ersten verfügbaren Parameter abgerufen werden sollen. Sie können weiterhin aufrufen **SQLGetData** bis durch ein anderes SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurückgegeben **SQLState**.  
  
5.  Wiederholen Sie Schritt 3 und 4, um den aktuellen Parameter abzurufen.  
  
6.  Rufen Sie **SQLParamData** erneut aus. Wenn nichts außer SQL_PARAM_DATA_AVAILABLE zurückgegeben wird, es gibt keine weiteren gestreamte Parameterdaten abgerufen werden sollen, und der Rückgabecode werden den Rückgabecode, der die nächste Anweisung, die ausgeführt wird.  
  
7.  Rufen Sie **SQLMoreResults** um den nächsten Satz von Parametern zu verarbeiten, bis SQL_NO_DATA zurückgegeben. **SQLMoreResults** gibt SQL_NO_DATA in diesem Beispiel zurück, wenn das Anweisungsattribut verweist SQL_ATTR_PARAMSET_SIZE auf 1 festgelegt wurde. Andernfalls **SQLMoreResults** gibt SQL_PARAM_DATA_AVAILABLE, um anzugeben, dass es gestreamte Output-Parameter für den nächsten Satz von Parametern zum Abrufen verfügbar sind.  
  
 Ähnlich wie ein DAE-Eingabeparameter, das Token im Argument verwendeten *ParameterValuePtr* in **SQLBindParameter** (Schritt 1) kann ein Zeiger auf eine Anwendung Daten-Struktur, NULL enthält die Ordnungszahl des Parameters und weitere anwendungsspezifische Informationen bei Bedarf.  
  
 Die Reihenfolge der zurückgegebenen gestreamte Ausgabe oder Eingabe-/Ausgabeparameter ist treiberspezifisch und u. u. nicht immer identisch mit der Reihenfolge, in der Abfrage angegeben.  
  
 Wenn die Anwendung nicht aufruft **SQLGetData** in Schritt 4 wird der Wert des Parameters wird verworfen. Auf ähnliche Weise, wenn die Anwendung ruft **SQLParamData** vor allen eines Parameters Wert gelesen wurde von **SQLGetData**, den Wert der Rest wird verworfen und die Anwendung das nächste verarbeiten kann der Parameter.  
  
 Wenn die Anwendung ruft **SQLMoreResults** vor allen gestreamte Ausgabe Parameter verarbeitet werden (**SQLParamData** SQL_PARAM_DATA_AVAILABLE gibt immer noch zurück), alle verbleibenden Parameter werden verworfen. Auf ähnliche Weise, wenn die Anwendung aufruft, **SQLMoreResults** vor allen eines Parameters Wert gelesen wurde von **SQLGetData**, der Rest des Werts und alle verbleibenden Parameter werden verworfen, und die Anwendung kann weiterhin den nächsten Parametersatz zu verarbeiten.  
  
 Beachten Sie, dass eine Anwendung die C-Datentyp in beiden angeben können **SQLBindParameter** und **SQLGetData**. Die C-Datentyp, der mit angegebenen **SQLGetData** überschreibt die C-Datentyp, der im angegebenen **SQLBindParameter**, es sei denn, in der C-Datentyp angegeben **SQLGetData** SQL_APD_TYPE ist.  
  
 Obwohl ein gestreamte Output-Parameter, wenn der Datentyp des Output-Parameters vom Typ BLOB ist noch nützlicher ist, kann diese Funktion auch eines beliebigen Datentyps verwendet werden. Die von gestreamte Ausgabeparameter unterstützten Datentypen werden in der Treiber angegeben.  
  
 Wenn SQL_PARAM_INPUT_OUTPUT_STREAM-Parameter verarbeitet werden, sind **SQLExecute** oder **SQLExecDirect** SQL_NEED_DATA werden zuerst zurückgegeben. Kann eine Anwendung aufrufen **SQLParamData** und **SQLPutData** DAE Parameterdaten senden. Wenn alle DAE Eingabeparameter verarbeitet werden, **SQLParamData** gibt SQL_PARAM_DATA_AVAILABLE, um anzugeben, gestreamte Output-Parameter sind verfügbar.  
  
 Wenn es Output-Parameter und gebundene Output-Parameter verarbeitet werden gestreamt werden, bestimmt der Treiber die Reihenfolge für die Verarbeitung von Output-Parameter. Wenn Output-Parameter auf einen Puffer gebunden ist (die **SQLBindParameter** Parameter *InputOutputType* auf SQL_PARAM_INPUT_OUTPUT oder SQL_PARAM_OUTPUT festgelegt ist), der Puffer kann nicht aufgefüllt werden, bis  **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück. Eine Anwendung sollte eine Grenze lesen erst nach Puffern **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO, die schließlich die Output-Parameter gestreamt werden, werden verarbeitet.  
  
 Eine Warnung und das Ergebnis außerdem in den Stream Ausgabeparameter festgelegt, kann die Datenquelle zurückgegeben. Im Allgemeinen Warnungen und Resultsets werden getrennt verarbeitet aus einem Stream befindlichen Output-Parameter durch den Aufruf **SQLMoreResults**. Verarbeiten von Warnungen und das Resultset, die vor der Verarbeitung des gestreamten Output-Parameters.  
  
 Die folgende Tabelle beschreibt die verschiedene Szenarien für einen einzelnen Befehl, der mit dem Server, und die Funktionsweise der Anwendungs gesendet.  
  
|Szenario|Rückgabewert von SQLExecute oder SQLExecDirect|Nächste Schritte|  
|--------------|---------------------------------------------------|---------------------|  
|Daten nur enthalten gestreamte Output-Parameter.|SQL_PARAM_DATA_AVAILABLE|Verwendung **SQLParamData** und **SQLGetData** gestreamte Ausgabeparameter abrufen.|  
|Enthält das Resultset und gestreamt Output-Parameter|SQL_SUCCESS|Rufen Sie das Resultset mit **SQLBindCol** und **SQLGetData**.<br /><br /> Rufen Sie **SQLMoreResults** , beginnt die Verarbeitung von gestreamte Output-Parameter. Sie sollte SQL_PARAM_DATA_AVAILABLE zurückgeben.<br /><br /> Verwendung **SQLParamData** und **SQLGetData** gestreamte Ausgabeparameter abrufen.|  
|Enthält eine Warnmeldung und gestreamt Output-Parameter|SQL_SUCCESS_WITH_INFO|Verwendung **SQLGetDiagRec** und **SQLGetDiagField** zum Verarbeiten der Warnung Nachrichten.<br /><br /> Rufen Sie **SQLMoreResults** , beginnt die Verarbeitung von gestreamte Output-Parameter. Sie sollte SQL_PARAM_DATA_AVAILABLE zurückgeben.<br /><br /> Verwendung **SQLParamData** und **SQLGetData** gestreamte Ausgabeparameter abrufen.|  
|Daten enthält, eine Warnmeldung, Resultsets und Ausgabeparameter gestreamt|SQL_SUCCESS_WITH_INFO|Verwendung **SQLGetDiagRec** und **SQLGetDiagField** zum Verarbeiten der Warnung Nachrichten. Rufen Sie anschließend **SQLMoreResults** , beginnt die Verarbeitung des Ergebnis festgelegt.<br /><br /> Rufen Sie ein Resultset mit **SQLBindCol** und **SQLGetData**.<br /><br /> Rufen Sie **SQLMoreResults** , beginnt die Verarbeitung von gestreamte Output-Parameter. **SQLMoreResults** SQL_PARAM_DATA_AVAILABLE sollte zurückgegeben werden.<br /><br /> Verwendung **SQLParamData** und **SQLGetData** gestreamte Ausgabeparameter abrufen.|  
|Abfrageparameter mit Eingabeparametern für DAE, z. B. eine gestreamte Eingabe/Ausgabe (. DAE)|SQL-NEED_DATA|Rufen Sie **SQLParamData** und **SQLPutData** Geben Sie zum Senden von DAE Parameterdaten.<br /><br /> Nachdem alle DAE Eingabeparameter verarbeitet werden, **SQLParamData** können Zurückgeben einer-Rückgabecode zurück, die **SQLExecute** und **SQLExecDirect** zurückgeben können. Die Fälle, in dieser Tabelle können dann angewendet werden.<br /><br /> Wenn der Rückgabecode SQL_PARAM_DATA_AVAILABLE ist, stehen gestreamte Output-Parameter. Eine Anwendung aufrufen muss **SQLParamData** erneut aus, um das Token für die gestreamten Output-Parameter abrufen, wie in der ersten Zeile dieser Tabelle beschrieben.<br /><br /> Ist der Rückgabecode SQL_SUCCESS zurück, es gibt ein Resultset verarbeitet, oder die Verarbeitung abgeschlossen ist.<br /><br /> Ist der Rückgabecode auf SQL_SUCCESS_WITH_INFO, sollten Sie die Warnung Nachrichten zum Verarbeiten vorhanden sind.|  
  
 Nach dem **SQLExecute**, **SQLExecDirect**, oder **SQLMoreResults** gibt SQL_PARAM_DATA_AVAILABLE, ein Fehler bei Funktionssequenz führt, wenn eine Anwendung ruft eine eine Funktion, die nicht in der folgenden Liste ist:  
  
-   **SQLAllocHandle** / **SQLAllocHandleStd**  
  
-   **SQLDataSources** / **SQLDrivers**  
  
-   **SQLGetInfo** / **SQLGetFunctions**  
  
-   **SQLGetConnectAttr** / **SQLGetEnvAttr** / **SQLGetDescField** / **SQLGetDescRec**  
  
-   **SQLNumParams**  
  
-   **SQLDescribeParam**  
  
-   **SQLNativeSql**  
  
-   **SQLParamData**  
  
-   **SQLMoreResults**  
  
-   **SQLGetDiagField** / **SQLGetDiagRec**  
  
-   **SQLCancel**  
  
-   **SQLCancelHandle** (mit Anweisungshandle)  
  
-   **SQLFreeStmt** (klicken Sie mit der Option = SQL_CLOSE, SQL_DROP oder SQL_UNBIND)  
  
-   **SQLCloseCursor**  
  
-   **SQLDisconnect**  
  
-   **SQLFreeHandle** (mit HandleType = SQL_HANDLE_STMT auf)  
  
-   **SQLGetStmtAttr**  
  
 Anwendungen können weiterhin **SQLSetDescField** oder **SQLSetDescRec** Bindungsinformationen über die festgelegt. Feld Zuordnung wird nicht geändert werden. Felder innerhalb der Deskriptor können jedoch neue Werte zurückgeben. SQL_DESC_PARAMETER_TYPE könnte es sich beispielsweise um SQL_PARAM_INPUT_OUTPUT_STREAM oder SQL_PARAM_OUTPUT_STREAM zurückgeben.  
  
## <a name="usage-scenario-retrieve-an-image-in-parts-from-a-result-set"></a>Verwendungsszenario: Abrufen eines Bilds in Teilen aus einem Resultset  
 **SQLGetData** können verwendet werden, um das Abrufen von Daten in Teilen, wenn eine gespeicherte Prozedur gibt ein Resultset, das eine Zeile mit Metadaten zu einem Bild enthält, und das Bild wird in einem großen Output-Parameter zurückgegeben.  
  
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
  
## <a name="usage-scenario-send-and-receive-a-large-object-as-a-streamed-inputoutput-parameter"></a>Verwendungsszenario: Senden und Empfangen von ein großes Objekt als eine gestreamte Eingabe-/Ausgabeparameter  
 **SQLGetData** abrufen und Senden von Daten in Teilen, wenn eine gespeicherte Prozedur ein großes Objekt bewegt wird als Eingabe/Ausgabe-Parameter, den Wert in und aus der Datenbank-streaming verwendet werden können. Sie müssen nicht alle Daten im Speicher gespeichert.  
  
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
