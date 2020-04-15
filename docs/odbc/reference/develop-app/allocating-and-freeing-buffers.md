---
title: Zuweisen und Befreien von Puffern | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6aab888d24fcbc987b3db921436f14812618519
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288400"
---
# <a name="allocating-and-freeing-buffers"></a>Zuweisen und Freigeben von Puffern
Alle Puffer werden von der Anwendung zugewiesen und freigegeben. Wenn ein Puffer nicht zurückgestellt wird, muss er nur für die Dauer des Aufrufs einer Funktion vorhanden sein. **SQLGetInfo** gibt z. B. den Wert zurück, der einer bestimmten Option im Puffer zugeordnet ist, auf den das *Argument InfoValuePtr* zeigt. Dieser Puffer kann unmittelbar nach dem Aufruf von **SQLGetInfo**freigegeben werden, wie im folgenden Codebeispiel gezeigt:  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 Da verzögerte Puffer in einer Funktion angegeben und in einer anderen verwendet werden, ist es ein Anwendungsprogrammierfehler, um einen verzögerten Puffer freizugeben, während der Treiber weiterhin erwartet, dass er vorhanden ist. Beispielsweise wird die Adresse \*des *ValuePtr-Puffers* zur späteren Verwendung durch **SQLFetch**an **SQLBindCol** übergeben. Dieser Puffer kann erst freigegeben werden, wenn die Spalte ungebunden ist, z. B. bei einem Aufruf von **SQLBindCol** oder **SQLFreeStmt,** wie im folgenden Codebeispiel gezeigt:  
  
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
  
 Ein solcher Fehler kann leicht gemacht werden, indem der Puffer lokal in einer Funktion deklariert wird. Der Puffer wird freigegeben, wenn die Anwendung die Funktion verlässt. Der folgende Code verursacht z. B. undefiniertes und wahrscheinlich fatales Verhalten im Treiber:  
  
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
