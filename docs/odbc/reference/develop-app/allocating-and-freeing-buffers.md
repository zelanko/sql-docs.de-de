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
ms.openlocfilehash: b783c2fc6766f0e2d2685724169894160c15ffc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077187"
---
# <a name="allocating-and-freeing-buffers"></a>Zuweisen und Freigeben von Puffern
Alle Puffer werden von der Anwendung zugeordnet und freigegeben. Wenn ein Puffer nicht verzögert wird, muss er nur für die Dauer des Aufrufes einer Funktion vorhanden sein. Beispielsweise gibt **SQLGetInfo** den Wert zurück, der einer bestimmten Option im Puffer zugeordnet ist, auf den das *infovalueptr* -Argument zeigt. Dieser Puffer kann direkt nach dem Aufrufen von **SQLGetInfo**freigegeben werden, wie im folgenden Codebeispiel gezeigt:  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 Da verzögerte Puffer in einer Funktion angegeben und in einer anderen Funktion verwendet werden, handelt es sich um einen Anwendungs Programmierfehler, der einen verzögerten Puffer freigibt, während der Treiber weiterhin erwartet, dass er vorhanden ist. Beispielsweise wird die Adresse des \* *ValuePtr* -Puffers zur späteren Verwendung durch **SQLFetch**an **SQLBindCol** weitergegeben. Dieser Puffer kann erst freigegeben werden, wenn die Bindung der Spalte aufgehoben wird, z. b. mit einem-Befehl von **SQLBindCol** oder **SQLFreeStmt** , wie im folgenden Codebeispiel gezeigt:  
  
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
  
 Ein solcher Fehler kann problemlos auftreten, indem der Puffer lokal in einer Funktion deklariert wird. der Puffer wird freigegeben, wenn die Anwendung die Funktion verlässt. Der folgende Code verursacht z. b. ein nicht definiertes und wahrscheinlich schwerwiegender Verhalten im Treiber:  
  
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
