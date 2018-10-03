---
title: Verwenden von Längen- und Indikatorwerten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- length/indicator buffers [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 849792f1-cb1e-4bc2-b568-c0aff0b66199
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 442d0865ede4819ea3413d662411295daa5b48bd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646018"
---
# <a name="using-length-and-indicator-values"></a>Verwenden von Längen- und Indikatorwerten
Die Längen-/Indikatorpuffer dient zum Übergeben von der Bytelänge der Daten in den Datenpuffer oder eine spezielle Indikator wie z. B. SQL_NULL_DATA gibt an, dass die Daten NULL sind. Abhängig von der Funktion, in der es verwendet wird, wird ein Längen-/Indikatorpuffer definiert eine SQLINTEGER oder ein SQLSMALLINT sein. Aus diesem Grund wird ein einzelnes Argument benötigt, um es zu beschreiben. Wenn im Datenpuffer eine nondeferred Eingabepuffer ist, enthält dieses Argument die Bytelänge der Daten selbst oder einem Indikatorwert. Es ist häufig mit dem Namen *StrLen_or_Ind* oder einem ähnlichen Namen. Beispielsweise der folgende code ruft **SQLPutData** auf einen Puffer übergeben voller Daten; -die Bytelänge (*ValueLen*) direkt übergeben wird, da im Datenpuffer (*ValuePtr*) ist ein Eingabepuffer.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLen;  
  
// Call local function to place data in ValuePtr. In ValueLen, return the  
// number of bytes of data placed in ValuePtr. If there is not enough  
// data, this will be less than 50.  
FillBuffer(ValuePtr, sizeof(ValuePtr), &ValueLen);  
  
// Call SQLPutData to send the data to the driver.  
SQLPutData(hstmt, ValuePtr, ValueLen);  
```  
  
 Ist der Datenpuffer eine verzögerte Eingabepuffer, einen nondeferred Ausgabepuffer oder einem Ausgabepuffer, enthält das Argument die Adresse des Längen-/Indikatorpuffers auf. Es ist häufig mit dem Namen *StrLen_or_IndPtr* oder einem ähnlichen Namen. Beispielsweise der folgende code ruft **SQLGetData** zum Abrufen eines Puffers mit Daten Länge in Byte an die Anwendung in den Längen-/Indikatorpuffer zurückgegeben wird (*ValueLenOrInd*), mit der Adresse ist übergeben **SQLGetData** da der entsprechende Datenpuffer (*ValuePtr*) ist ein nondeferred Ausgabepuffer.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Es sei denn, sie insbesondere nicht zulässig ist, ein Längenindikator / pufferargument "0" sein (wenn nondeferred Eingabe) oder ein null-Zeiger (wenn Ausgabe- oder verzögerte Eingabe). Für den Eingabepuffer bewirkt, dass dies den Treiber, um die Bytelänge der Daten zu ignorieren. Dies gibt einen Fehler zurück, wenn Daten mit variabler Länge übergeben jedoch häufig beim Übergeben von Daten fester Länge ungleich Null ist, da weder eine Länge noch einem Indikatorwert erforderlich ist. Für den Ausgabepuffer bewirkt, dass dies den Treiber nicht die Bytelänge der Daten oder einem Indikatorwert zurückgegeben. Dies ist ein Fehler, wenn die Daten, die vom Treiber zurückgegebene NULL ist, jedoch werden häufig beim Abrufen von Daten fester Länge, die NULL-Werte zulässt, da weder eine Länge noch einem Indikatorwert erforderlich ist.  
  
 Als wenn die Adresse eines Puffers verzögerten Daten an den Treiber übergeben wird muss die Adresse von einer verzögerten Längen-/Indikatorpuffer gültig bleiben, bis der Puffer aufgehoben wird.  
  
 Die folgenden Längen sind als Längenindikator/Werte gültig:  
  
-   *n*, wobei *n* > 0.  
  
-   0.  
  
-   SQL_NTS. Eine Zeichenfolge, die der Treiber in den entsprechenden Datenpuffer gesendet wird, Null-terminierte; Dies ist eine praktische Methode für C-Programmierer Zeichenfolgen übergeben werden, ohne die Bytelänge zu berechnen. Dieser Wert ist zulässig, nur, wenn die Anwendung Daten an den Treiber sendet. Wenn der Treiber die Daten an die Anwendung zurückgibt, wird immer die tatsächlichen Bytelänge der Daten zurückgegeben.  
  
 Die folgenden Werte sind als Längenindikator/Werte gültig. SQL_NULL_DATA wird in das Deskriptorfeld SQL_DESC_INDICATOR_PTR gespeichert. Alle anderen Werte werden in das Deskriptorfeld SQL_DESC_OCTET_LENGTH_PTR gespeichert.  
  
-   SQL_NULL_DATA. Die Daten ist ein NULL-Daten-Wert, und der Wert im entsprechenden Datenpuffer wird ignoriert. Dieser Wert ist nur für SQL-Daten gesendet oder abgerufen, die vom Treiber zulässig.  
  
-   SQL_DATA_AT_EXEC. Der Datenpuffer enthält keine Daten. Stattdessen werden die Daten gesendet werden, mit **SQLPutData** , wenn die Anweisung ausgeführt wird oder wenn **SQLBulkOperations** oder **SQLSetPos** aufgerufen wird. Dieser Wert ist zulässig, nur für SQL-Daten, die an den Treiber gesendet. Weitere Informationen finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
-   Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*) Makro. Dieser Wert ähnelt SQL_DATA_AT_EXEC. Weitere Informationen finden Sie unter [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md).  
  
-   SQL_NO_TOTAL. Der Treiber kann nicht die Anzahl der Bytes von long-Daten weiterhin verfügbar, die in einem Ausgabepuffer zurückgegeben bestimmen. Dieser Wert ist nur für SQL-Daten abgerufen, die vom Treiber zulässig.  
  
-   SQL_DEFAULT_PARAM. Eine Prozedur ist den Standardwert eines Eingabeparameters in einer Prozedur anstelle des Werts in den entsprechenden Datenpuffer verwenden.  
  
-   SQL_COLUMN_IGNORE. **SQLBulkOperations** oder **SQLSetPos** besteht darin, den Wert im Datenpuffer ignoriert. Bei der Aktualisierung einer Zeile mit Daten durch einen Aufruf von **SQLBulkOperations** oder **SQLSetPos** der Spaltenwert nicht geändert wird. Wenn Sie eine neue Zeile mit Daten durch einen Aufruf von einfügen **SQLBulkOperations**, der Wert der Spalte auf den Standardwert festgelegt ist oder, wenn die Spalte keinen standardmäßig auf NULL.
