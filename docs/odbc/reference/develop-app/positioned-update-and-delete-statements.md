---
title: Positionierte UPDATE-und DELETE-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: 0eafba50-02c7-46ca-a439-ef3307b935dc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b37bdfae5f97a453477768aca39b801c06c0701
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023294"
---
# <a name="positioned-update-and-delete-statements"></a>Positionierte Aktualisierung und DELETE-Anweisungen
Anwendungen können die aktuelle Zeile in einem Resultset mit einer positionierten Update-oder DELETE-Anweisung aktualisieren oder löschen. Positionierte UPDATE-und DELETE-Anweisungen werden von einigen Datenquellen unterstützt, aber nicht für alle. Um zu ermitteln, ob eine Datenquelle positionierte UPDATE-und DELETE-Anweisungen unterstützt, ruft eine Anwendung **SQLGetInfo** mit dem SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 *InfoType* (abhängig vom Cursortyp) auf. Beachten Sie, dass die ODBC-Cursor Bibliothek positionierte UPDATE-und DELETE-Anweisungen simuliert.  
  
 Um eine positionierte UPDATE-oder DELETE-Anweisung zu verwenden, muss die Anwendung ein Resultset mit einer **Select for Update** -Anweisung erstellen. Die Syntax dieser Anweisung lautet wie folgt:  
  
 **Select** [**all** &#124; **verschieden**] *Select-List*  
  
 **From** *Table-Reference-List*  
  
 [**Where** *Such Bedingung*]  
  
 **Zum Aktualisieren von** [*Spaltenname* [**,** *Spaltenname*]...]  
  
 Die Anwendung positioniert dann den Cursor in der zu aktualisierenden oder zu löschenden Zeile. Dies kann durch Aufrufen von **SQLFetchScroll** zum Abrufen eines Rowsets, das die erforderliche Zeile enthält, und durch Aufrufen von **SQLSetPos** zum Positionieren des Rowsetcursors in dieser Zeile aufgerufen werden. Die Anwendung führt dann die positionierte UPDATE-oder DELETE-Anweisung für eine andere Anweisung aus als die Anweisung, die vom Resultset verwendet wird. Die Syntax dieser Anweisungen lautet wie folgt:  
  
 **** *Tabellennamen* aktualisieren  
  
 **Festlegen** des *Spalten Bezeichners* **=** {*Expression* &#124; **null**}  
  
 [**,** *Spalten Bezeichner* **=** {*Expression* &#124; **null**}]...  
  
 **WHERE CURRENT of** *Cursor-Name*  
  
 **Aus** *Tabellenname* löschen, **wobei Current of** *Cursor Name*  
  
 Beachten Sie, dass für diese Anweisungen ein Cursor Name erforderlich ist. Die Anwendung kann einen Cursor Namen mit **SQLSetCursorName** angeben, bevor die Anweisung ausgeführt wird, mit der das Resultset erstellt wird, oder die Datenquelle kann beim Erstellen des Cursors automatisch einen Cursor Namen generieren lassen. Im letzteren Fall ruft die Anwendung diesen Cursor Namen zur Verwendung in positionierten Update-und DELETE-Anweisungen durch Aufrufen von **SQLGetCursorName**ab.  
  
 Mit dem folgenden Code kann ein Benutzer beispielsweise durch die Customers-Tabelle scrollen und Kundendaten Sätze löschen oder seine Adressen und Telefonnummern aktualisieren. Sie ruft **SQLSetCursorName** auf, um einen Cursor Namen anzugeben, bevor das Resultset von Kunden erstellt wird, und verwendet drei Anweisungs Handles: *hstmtcust* für das Resultset, *hstmtupdate* für eine positionierte UPDATE-Anweisung und *hstmtdelete* für eine positionierte DELETE-Anweisung. Obwohl der Code separate Variablen an die Parameter in der positionierten Update-Anweisung binden könnte, aktualisiert er die rowsetpuffer und bindet die Elemente dieser Puffer. Dadurch werden die rowsetpuffer mit den aktualisierten Daten synchronisiert.  
  
```  
#define POSITIONED_UPDATE 100  
#define POSITIONED_DELETE 101  
  
SQLUINTEGER    CustIDArray[10];  
SQLCHAR        NameArray[10][51], AddressArray[10][51],   
               PhoneArray[10][11];  
SQLINTEGER     CustIDIndArray[10], NameLenOrIndArray[10],   
               AddressLenOrIndArray[10],  
               PhoneLenOrIndArray[10];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLHSTMT       hstmtCust, hstmtUpdate, hstmtDelete;  
  
// Set the SQL_ATTR_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmtCust, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmtCust, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]),  
            NameLenOrIndArray);  
SQLBindCol(hstmtCust, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
         AddressLenOrIndArray);  
SQLBindCol(hstmtCust, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Set the cursor name to Cust.  
SQLSetCursorName(hstmtCust, "Cust", SQL_NTS);  
  
// Prepare positioned update and delete statements.  
SQLPrepare(hstmtUpdate,  
   "UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust",  
   SQL_NTS);  
SQLPrepare(hstmtDelete, "DELETE FROM Customers WHERE CURRENT OF Cust", SQL_NTS);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmtCust,  
   "SELECT CustID, Name, Address, Phone FROM Customers FOR UPDATE OF Address, Phone",  
   SQL_NTS);  
  
// Fetch and display the first 10 rows.  
SQLFetchScroll(hstmtCust, SQL_FETCH_NEXT, 0);  
DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray, AddressArray,  
            AddressLenOrIndArray, PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
  
// Call GetAction to get an action and a row number from the user.  
while (GetAction(&Action, &RowNum)) {  
   switch (Action) {  
  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmtCust, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray, PhoneArray,  
                     PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case POSITIONED_UPDATE:  
         // Get the new data and place it in the rowset buffers.  
         GetNewData(AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                     PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Bind the elements of the arrays at position RowNum-1 to the   
         // parameters of the positioned update statement.  
         SQLBindParameter(hstmtUpdate, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           50, 0, AddressArray[RowNum - 1], sizeof(AddressArray[0]),  
                           &AddressLenOrIndArray[RowNum - 1]);  
         SQLBindParameter(hstmtUpdate, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           10, 0, PhoneArray[RowNum - 1], sizeof(PhoneArray[0]),  
                           &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned update statement to update the row.  
         SQLExecute(hstmtUpdate);  
         break;  
  
      case POSITIONED_DELETE:  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned delete statement to delete the row.  
         SQLExecute(hstmtDelete);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmtCust);  
```
