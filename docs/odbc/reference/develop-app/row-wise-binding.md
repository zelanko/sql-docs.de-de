---
description: Zeilenbezogenes Binden
title: Zeilen weises binden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4f622cf4-0603-47a1-a48b-944c4ef46364
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b30d2426a8fb2a2bd0f0cb89c2de5bc326b67dfa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465620"
---
# <a name="row-wise-binding"></a>Zeilenbezogenes Binden
Wenn die zeilenweise Bindung verwendet wird, definiert eine Anwendung eine Struktur, die ein oder zwei oder in einigen Fällen drei Elemente für jede Spalte enthält, für die Daten zurückgegeben werden sollen. Das erste Element enthält den Datenwert, und das zweite Element enthält den Längen-/indikatorenpuffer. Indikatoren und Längenwerte können in separaten Puffern gespeichert werden, indem die SQL_DESC_INDICATOR_PTR-und SQL_DESC_OCTET_LENGTH_PTR Deskriptorfelder auf verschiedene Werte festgelegt werden. Wenn dies der Fall ist, enthält die-Struktur ein drittes-Element. Die Anwendung ordnet dann ein Array dieser Strukturen zu, das so viele Elemente enthält, wie Zeilen im Rowset vorhanden sind.  
  
 Die Anwendung deklariert die Größe der Struktur für den Treiber mit dem SQL_ATTR_ROW_BIND_TYPE Statement-Attribut und bindet die Adresse der einzelnen Member im ersten Element des Arrays. Daher kann der Treiber die Adresse der Daten für eine bestimmte Zeile und Spalte als  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size)  
```  
  
 , wobei Zeilen von 1 bis zur Größe des Rowsets nummeriert werden. (Eine wird von der Zeilennummer subtrahiert, da die Array Indizierung in C Null basiert ist.) In der folgenden Abbildung wird gezeigt, wie die zeilenweise Bindung funktioniert. Im Allgemeinen sind nur Spalten, die gebunden werden, in der Struktur enthalten. Die Struktur kann Felder enthalten, die nicht mit Resultsetspalten verknüpft sind. Die Spalten können in beliebiger Reihenfolge in der Struktur platziert werden, werden jedoch in sequenzieller Reihenfolge zur Verdeutlichung angezeigt.  
  
 ![Zeigt die Zeilen&#45;Weise Bindung an.](../../../odbc/reference/develop-app/media/pr22.gif "pr22")  
  
 Der folgende Code erstellt z. b. eine-Struktur mit Elementen, in denen Daten für die Spalten OrderID, SalesPerson und Status und Länge/Indikatoren für die Spalten SalesPerson und Status zurückgegeben werden. Er ordnet 10 dieser Strukturen zu und bindet Sie an die Spalten OrderID, SalesPerson und Status.  
  
```  
#define ROW_ARRAY_SIZE 10  
  
// Define the ORDERINFO struct and allocate an array of 10 structs.  
typedef struct {  
   SQLUINTEGER   OrderID;  
   SQLINTEGER    OrderIDInd;  
   SQLCHAR       SalesPerson[11];  
   SQLINTEGER    SalesPersonLenOrInd;  
   SQLCHAR       Status[7];  
   SQLINTEGER    StatusLenOrInd;  
} ORDERINFO;  
ORDERINFO OrderInfoArray[ROW_ARRAY_SIZE];  
  
SQLULEN    NumRowsFetched;  
SQLUSMALLINT   RowStatusArray[ROW_ARRAY_SIZE], i;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Specify the size of the structure with the SQL_ATTR_ROW_BIND_TYPE  
// statement attribute. This also declares that row-wise binding will  
// be used. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE  
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement  
// attribute to point to the row status array. Set the  
// SQL_ATTR_ROWS_FETCHED_PTR statement attribute to point to  
// NumRowsFetched.  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, sizeof(ORDERINFO), 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, ROW_ARRAY_SIZE, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROWS_FETCHED_PTR, &NumRowsFetched, 0);  
  
// Bind elements of the first structure in the array to the OrderID,  
// SalesPerson, and Status columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &OrderInfoArray[0].OrderID, 0, &OrderInfoArray[0].OrderIDInd);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, OrderInfoArray[0].SalesPerson,  
            sizeof(OrderInfoArray[0].SalesPerson),  
            &OrderInfoArray[0].SalesPersonLenOrInd);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, OrderInfoArray[0].Status,  
            sizeof(OrderInfoArray[0].Status), &OrderInfoArray[0].StatusLenOrInd);  
  
// Execute a statement to retrieve rows from the Orders table.  
SQLExecDirect(hstmt, "SELECT OrderID, SalesPerson, Status FROM Orders", SQL_NTS);  
  
// Fetch up to the rowset size number of rows at a time. Print the actual  
// number of rows fetched; this number is returned in NumRowsFetched.  
// Check the row status array to print only those rows successfully  
// fetched. Code to check if rc equals SQL_SUCCESS_WITH_INFO or  
// SQL_ERRORnot shown.  
while ((rc = SQLFetchScroll(hstmt,SQL_FETCH_NEXT,0)) != SQL_NO_DATA) {  
   for (i = 0; i < NumRowsFetched; i++) {  
      if (RowStatusArray[i] == SQL_ROW_SUCCESS|| RowStatusArray[i] ==   
         SQL_ROW_SUCCESS_WITH_INFO) {  
         if (OrderInfoArray[i].OrderIDInd == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%d\t", OrderInfoArray[i].OrderID);  
         if (OrderInfoArray[i].SalesPersonLenOrInd == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%s\t", OrderInfoArray[i].SalesPerson);  
         if (OrderInfoArray[i].StatusLenOrInd == SQL_NULL_DATA)  
            printf(" NULL\n");  
         else  
            printf("%s\n", OrderInfoArray[i].Status);  
      }  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
