---
title: Verwenden von Längen- und Indikatorwerten | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0c878c9038b26aa996ed206c6b8adfe8d6c21e5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306761"
---
# <a name="using-length-and-indicator-values"></a>Verwenden von Längen- und Indikatorwerten
Der Längen-Indikator-Puffer wird verwendet, um die Bytelänge der Daten im Datenpuffer oder einen speziellen Indikator wie SQL_NULL_DATA zu übergeben, der angibt, dass die Daten NULL sind. Je nach Funktion, in der er verwendet wird, wird ein Längen-Indikator-Puffer als SQLINTEGER oder SQLSMALLINT definiert. Daher ist ein einziges Argument erforderlich, um es zu beschreiben. Wenn es sich bei dem Datenpuffer um einen nicht verzögerten Eingabepuffer handelt, enthält dieses Argument die Bytelänge der Daten selbst oder einen Indikatorwert. Es wird oft *StrLen_or_Ind* oder einem ähnlichen Namen genannt. Der folgende Code ruft z. B. **SQLPutData** auf, um einen Puffer voller Daten zu übergeben. Die Bytelänge (*ValueLen*) wird direkt übergeben, da der Datenpuffer (*ValuePtr*) ein Eingabepuffer ist.  
  
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
  
 Wenn der Datenpuffer ein verzögerter Eingabepuffer, ein nicht verzögerter Ausgabepuffer oder ein Ausgabepuffer ist, enthält das Argument die Adresse des Längen-/Indikatorpuffers. Es wird oft *StrLen_or_IndPtr* oder einem ähnlichen Namen genannt. Der folgende Code ruft z. B. **SQLGetData** auf, um einen Puffer voller Daten abzurufen. Die Bytelänge wird im Längen-/Indikatorpuffer (*ValueLenOrInd*), dessen Adresse an **SQLGetData** übergeben wird, an die Anwendung zurückgegeben, da der entsprechende Datenpuffer (*ValuePtr*) ein nicht verzögerter Ausgabepuffer ist.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Sofern dies nicht ausdrücklich verboten ist, kann ein Längen-/Indikatorpufferargument 0 (wenn nicht verzögerte Eingabe) oder ein NULL-Zeiger (wenn Ausgabe oder verzögerte Eingabe) sein. Bei Eingabepuffern führt dies dazu, dass der Treiber die Bytelänge der Daten ignoriert. Dies gibt einen Fehler beim Übergeben von Daten variabler Länge zurück, ist jedoch häufig beim Übergeben von Daten mit nicht null, fester Länge, da weder eine Länge noch ein Indikatorwert erforderlich ist. Bei Ausgabepuffern führt dies dazu, dass der Treiber die Bytelänge der Daten oder einen Indikatorwert nicht zurückgibt. Dies ist ein Fehler, wenn die vom Treiber zurückgegebenen Daten NULL sind, aber beim Abrufen von Daten mit fester Länge und nicht NULL üblich ist, da weder eine Länge noch ein Indikatorwert erforderlich ist.  
  
 Wie beim Übergeben der Adresse eines verzögerten Datenpuffers an den Treiber muss die Adresse eines verzögerten Längen-/Indikatorpuffers gültig bleiben, bis der Puffer nicht gebunden ist.  
  
 Die folgenden Längen gelten als Längen-/Indikatorwerte:  
  
-   *,* wobei *n* > 0.  
  
-   0.  
  
-   SQL_NTS. Eine Zeichenfolge, die an den Treiber im entsprechenden Datenpuffer gesendet wird, wird null beendet. Dies ist eine bequeme Möglichkeit für C-Programmierer, Strings zu übergeben, ohne ihre Bytelänge berechnen zu müssen. Dieser Wert ist nur zulässig, wenn die Anwendung Daten an den Treiber sendet. Wenn der Treiber Daten an die Anwendung zurückgibt, gibt er immer die tatsächliche Bytelänge der Daten zurück.  
  
 Die folgenden Werte sind als Längen-/Indikatorwerte gültig. SQL_NULL_DATA wird im SQL_DESC_INDICATOR_PTR-Deskriptorfeld gespeichert. alle anderen Werte werden im SQL_DESC_OCTET_LENGTH_PTR-Deskriptorfeld gespeichert.  
  
-   SQL_NULL_DATA. Die Daten sind ein NULL-Datenwert, und der Wert im entsprechenden Datenpuffer wird ignoriert. Dieser Wert ist nur für SQL-Daten zulässig, die an den Treiber gesendet oder vom Treiber abgerufen werden.  
  
-   SQL_DATA_AT_EXEC. Der Datenpuffer enthält keine Daten. Stattdessen werden die Daten mit **SQLPutData** gesendet, wenn die Anweisung ausgeführt wird oder wenn **SQLBulkOperations** oder **SQLSetPos** aufgerufen wird. Dieser Wert ist nur für SQL-Daten zulässig, die an den Treiber gesendet werden. Weitere Informationen finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
-   Ergebnis des*SQL_LEN_DATA_AT_EXEC(Länge*) Makros. Dieser Wert ähnelt SQL_DATA_AT_EXEC. Weitere Informationen finden Sie unter [Senden langer Daten](../../../odbc/reference/develop-app/sending-long-data.md).  
  
-   SQL_NO_TOTAL. Der Treiber kann die Anzahl der Bytes langer Daten, die noch in einem Ausgabepuffer zurückgegeben werden können, nicht ermitteln. Dieser Wert ist nur für SQL-Daten zulässig, die vom Treiber abgerufen werden.  
  
-   SQL_DEFAULT_PARAM. Eine Prozedur besteht darin, den Standardwert eines Eingabeparameters in einer Prozedur anstelle des Werts im entsprechenden Datenpuffer zu verwenden.  
  
-   SQL_COLUMN_IGNORE. **SQLBulkOperations** oder **SQLSetPos** ignoriert den Wert im Datenpuffer. Beim Aktualisieren einer Datenzeile durch einen Aufruf von **SQLBulkOperations** oder **SQLSetPos** wird der Spaltenwert nicht geändert. Beim Einfügen einer neuen Datenzeile durch einen Aufruf von **SQLBulkOperations**wird der Spaltenwert auf den Standardwert oder, wenn die Spalte keinen Standard hat, auf NULL festgelegt.
