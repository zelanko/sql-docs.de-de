---
description: Verwenden von Längen- und Indikatorwerten
title: Verwenden von Längen-und Indikator Werten | Microsoft-Dokumentation
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
ms.openlocfilehash: 7e9c7feb463b2a92d716be24c76d00b64c69a860
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424402"
---
# <a name="using-length-and-indicator-values"></a>Verwenden von Längen- und Indikatorwerten
Der Längen-/Indikatorpuffer wird verwendet, um die Byte Länge der Daten im Datenpuffer oder einen speziellen Indikator wie SQL_NULL_DATA zu übergeben, der angibt, dass die Daten NULL sind. Abhängig von der Funktion, in der Sie verwendet wird, wird ein Längen-/Indikatorpuffer als SQLINTEGER oder SQLSMALLINT definiert. Daher ist ein einzelnes Argument erforderlich, um es zu beschreiben. Wenn der Datenpuffer ein nicht verzögerter Eingabepuffer ist, enthält dieses Argument die Byte Länge der Daten selbst oder einen Indikator Wert. Sie wird häufig *StrLen_Or_Ind* oder ein ähnlicher Name genannt. Der folgende Code ruft z. b. **SQLPutData** auf, um einen Puffer mit vollen Daten zu übergeben. die Byte Länge (*valuelen*) wird direkt übermittelt, da der Datenpuffer (*ValuePtr*) ein Eingabepuffer ist.  
  
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
  
 Wenn der Datenpuffer ein verzögerter Eingabepuffer, ein nicht verzögerter Ausgabepuffer oder ein Ausgabepuffer ist, enthält das-Argument die Adresse des Längen-/indikatorenpuffers. Sie wird häufig *StrLen_or_IndPtr* oder ein ähnlicher Name genannt. Der folgende Code ruft z. b. **SQLGetData** auf, um einen Puffer in voller Größe abzurufen. die Byte Länge wird an die Anwendung im Längen-/Indikatorpuffer (*valuelenorind*) zurückgegeben, deren Adresse an **SQLGetData** weitergegeben wird, da der zugehörige Datenpuffer (*ValuePtr*) ein nicht verzögerter Ausgabepuffer ist.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Wenn Sie nicht ausdrücklich zulässig ist, kann ein Längen-/Indikator-pufferargument 0 (bei nicht verzögerter Eingabe) oder ein NULL-Zeiger (bei Ausgabe oder verzögerter Eingabe) sein. Bei Eingabe Puffern bewirkt dies, dass der Treiber die Byte Länge der Daten ignoriert. Dadurch wird ein Fehler zurückgegeben, wenn Daten variabler Länge übergeben werden, dies ist jedoch beim Übergeben von Daten mit fester Länge ungleich NULL üblich, weil weder eine Länge noch ein Indikator Wert benötigt wird. Bei Ausgabe Puffern bewirkt dies, dass der Treiber nicht die Byte Länge der Daten oder einen Indikator Wert zurückgibt. Dies ist ein Fehler, wenn die vom Treiber zurückgegebenen Daten NULL sind, beim Abrufen von Daten mit fester Länge, die keine NULL-Werte zulassen, aber üblich ist, weil weder eine Länge noch ein Indikator Wert benötigt wird.  
  
 Wenn die Adresse eines verzögerten Daten Puffers an den Treiber weitergeleitet wird, muss die Adresse eines verzögerten Längen-/indikatorenpuffers gültig bleiben, bis der Puffer nicht gebunden ist.  
  
 Die folgenden Längen sind als Längen-/Indikatorwerte gültig:  
  
-   *n*, wobei *n* > 0.  
  
-   0.  
  
-   SQL_NTS. Eine Zeichenfolge, die im entsprechenden Datenpuffer an den Treiber gesendet wurde, wird mit Null beendet. Dies ist eine bequeme Möglichkeit für C-Programmierer, Zeichen folgen zu übergeben, ohne die Byte Länge berechnen zu müssen. Dieser Wert ist nur zulässig, wenn die Anwendung Daten an den Treiber sendet. Wenn der Treiber Daten an die Anwendung zurückgibt, wird immer die tatsächliche Byte Länge der Daten zurückgegeben.  
  
 Die folgenden Werte sind als Längen-/Indikatorwerte gültig. SQL_NULL_DATA wird im SQL_DESC_INDICATOR_PTR Deskriptorfeld gespeichert. alle anderen Werte werden im Feld SQL_DESC_OCTET_LENGTH_PTR Deskriptor gespeichert.  
  
-   SQL_NULL_DATA. Bei den Daten handelt es sich um einen NULL-Datenwert, und der Wert im entsprechenden Datenpuffer wird ignoriert. Dieser Wert ist nur für SQL-Daten zulässig, die an den Treiber gesendet oder von diesem abgerufen werden.  
  
-   SQL_DATA_AT_EXEC. Der Datenpuffer enthält keine Daten. Stattdessen werden die Daten mit **SQLPutData** gesendet, wenn die-Anweisung ausgeführt wird oder wenn **SQLBulkOperations** oder **SQLSetPos** aufgerufen wird. Dieser Wert ist nur für SQL-Daten zulässig, die an den Treiber gesendet werden. Weitere Informationen finden Sie unter [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)und [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
-   Ergebnis des SQL_LEN_DATA_AT_EXEC (*length*)-Makros. Dieser Wert ähnelt SQL_DATA_AT_EXEC. Weitere Informationen finden Sie unter [Senden von Long-Daten](../../../odbc/reference/develop-app/sending-long-data.md).  
  
-   SQL_NO_TOTAL. Der Treiber kann nicht bestimmen, wie viele Bytes lange Daten in einem Ausgabepuffer zurückgeben können. Dieser Wert ist nur für SQL-Daten zulässig, die vom Treiber abgerufen werden.  
  
-   SQL_DEFAULT_PARAM. Eine Prozedur ist die Verwendung des Standardwerts eines Eingabe Parameters in einer Prozedur anstelle des Werts im entsprechenden Datenpuffer.  
  
-   SQL_COLUMN_IGNORE. **SQLBulkOperations** oder **SQLSetPos** dient zum Ignorieren des Werts im Datenpuffer. Wenn Sie eine Daten Zeile durch einen-Befehl von **SQLBulkOperations** oder **SQLSetPos aktualisieren,** wird der Spaltenwert nicht geändert. Beim Einfügen einer neuen Daten Zeile durch einen-Befehl von **SQLBulkOperations**wird der Wert der-Spalte auf den Standardwert festgelegt oder, wenn die Spalte keinen Standardwert hat, auf NULL festgelegt.
