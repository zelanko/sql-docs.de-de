---
title: Zuordnen und Freigeben von Puffern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], allocating and freeing
- allocating buffers [ODBC]
- freeing buffers [ODBC]
ms.assetid: 886bc9ed-39d4-43d2-82ff-aebc35b14d39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 388147de8935d36180ba9845c8353bbf3dd6edc0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288074"
---
# <a name="allocating-and-freeing-buffers"></a>Zuweisen und Freigeben von Puffern
Alle Puffer werden zugeordnet und von der Anwendung freigegeben. Wenn Sie ein Puffer nicht verzögert wird, müssen sie nur für die Dauer des Aufrufs an eine Funktion vorhanden sein. Z. B. **SQLGetInfo** gibt den Wert mit einer bestimmten Option in den Puffer, der auf die *InfoValuePtr* Argument. Dieser Puffer kann freigegeben werden, sofort nach dem Aufruf von **SQLGetInfo**, wie im folgenden Codebeispiel gezeigt:  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 Da verzögerte Puffer sind eine Funktion nicht angegeben und in einem anderen verwendet, ist es ein Programmiermodell Fehler um eine verzögerte Puffer freizugeben, während der Treiber noch vorhanden sein, erwartet. Z. B. die Adresse der \* *ValuePtr* Puffer übergeben wird, um **SQLBindCol** zur späteren Verwendung mit **SQLFetch**. Dieser Puffer kann nicht freigegeben werden, bis die Spalte nicht gebundenen, z. B. mit einem Aufruf von **SQLBindCol** oder **SQLFreeStmt** wie im folgenden Codebeispiel gezeigt:  
  
```  
SQLRETURN    rc;  
SQLINTEGER   ValueLenOrInd;  
SQLHSTMT     hstmt;  
  
// Allocate ValuePtr  
SQLCHAR * ValuePtr = malloc(50);  
  
// Bind ValuePtr to column 1. It is an error to free ValuePtr here.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, 50, &ValueLenOrInd);  
  
// Fetch each row of data and place the value for column 1 in *ValuePtr.  
// Code to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO   
// not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // It is an error to free ValuePtr here.  
}  
  
// Unbind ValuePtr from column 1.  It is now OK to free ValuePtr.  
SQLFreeStmt(hstmt, SQL_UNBIND);  
free(ValuePtr);  
```  
  
 Solche Fehler erfolgt einfach durch den Puffer lokal in einer Funktion deklarieren; der Puffer wird freigegeben, wenn die Anwendung die Funktion lässt. Beispielsweise verursacht der folgende Code das Verhalten nicht definiert und möglicherweise schwerwiegender im Treiber:  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
BindAColumn(hstmt);  
  
// Fetch each row of data and try to place the value for column 1 in  
// *ValuePtr. Because ValuePtr has been freed, the behavior is undefined  
// and probably fatal. Code to check if rc equals SQL_ERROR or   
// SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {}  
  
   .  
   .  
   .  
  
void BindAColumn(SQLHSTMT hstmt)  // WARNING! This function won't work!  
{  
   // Declare ValuePtr locally.  
   SQLCHAR      ValuePtr[50];  
   SQLINTEGER   ValueLenOrInd;  
  
   // Bind rgbValue to column.  
   SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr),  
               &ValueLenOrInd);  
  
   // ValuePtr is freed when BindAColumn exits.  
}  
```
