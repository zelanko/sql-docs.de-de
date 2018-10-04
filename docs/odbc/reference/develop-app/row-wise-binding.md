---
title: Zeilenweises binden | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c596f4924e9859b3ac61d38f68bacbc3ecd54a2e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855858"
---
# <a name="row-wise-binding"></a>Zeilenbezogenes Binden
Bei Verwendung zeilenweise Bindung wird eine Anwendung definiert eine Struktur mit einem oder zwei, oder in einigen Fällen werden drei Elemente für jede Spalte, die für die Daten zurückgegeben werden. Das erste Element enthält den Datenwert, und das zweite Element enthält der Längen-/Indikatorpuffer. Indikatoren und Längenwerte können in separaten Puffer gespeichert werden, durch die deskriptorfelder SQL_DESC_INDICATOR_PTR und SQL_DESC_OCTET_LENGTH_PTR auf unterschiedliche Werte festlegen; Wenn dies geschehen ist, enthält die Struktur ein drittes Element. Klicken Sie dann die Anwendung weist ein Array dieser Strukturen, die enthält so viele Elemente als Zeilen im Rowset vorhanden sind.  
  
 Die Anwendung die Größe der Struktur an den Treiber mit dem Attribut der SQL_ATTR_ROW_BIND_TYPE-Anweisung deklariert und bindet die Adresse für jedes Element im ersten Element des Arrays. Daher kann der Treiber die Adresse der Daten für eine bestimmte Zeile und Spalte als berechnen  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size)  
```  
  
 Zeilen werden, in denen auf die Größe des Rowsets von 1 nummeriert. (Eine wird von die Nummer der Zeile subtrahiert, da bei der Indizierung in C nullbasiert ist.) Die folgende Abbildung zeigt die Funktionsweise der zeilenbezogenen Bindung. Im Allgemeinen werden nur Spalten, die gebunden werden, in der Struktur enthalten. Die Struktur kann Felder enthalten, die nicht verbunden sind, um Spalten zu erhalten. Die Spalten in der Struktur in einer beliebigen Reihenfolge platziert werden können, jedoch werden in sequenzieller Reihenfolge aus Gründen der Übersichtlichkeit angezeigt.  
  
 ![Zeigt Zeile&#45;klug Bindung](../../../odbc/reference/develop-app/media/pr22.gif "pr22")  
  
 Der folgende Code erstellt z.B. eine Struktur mit Elementen in den Daten für die Spalten "OrderID", Vertriebsmitarbeiter und den Status und Länge/Indikatoren für die Spalten Vertriebsmitarbeiter und Status zurückgegeben. Es weist 10 dieser Strukturen und den Spalten "OrderID", Vertriebsmitarbeiter und den Status zu binden.  
  
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
