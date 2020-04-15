---
title: Positionierte Aktualisierungs- und Löschanweisungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6e5316bee7057b30eace326b3ca82b30b75741fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282361"
---
# <a name="positioned-update-and-delete-statements"></a>Positionierte Aktualisierung und DELETE-Anweisungen
Anwendungen können die aktuelle Zeile in einem Resultset mit einer positionierten Aktualisierungs- oder Löschanweisung aktualisieren oder löschen. Positionierte Aktualisierungs- und Löschanweisungen werden von einigen Datenquellen unterstützt, jedoch nicht von allen. Um zu bestimmen, ob eine Datenquelle positionierte Aktualisierungs- und Löschanweisungen unterstützt, ruft eine Anwendung **SQLGetInfo** mit den SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 *InfoType* auf (je nach Typ des Cursors). Beachten Sie, dass die ODBC-Cursorbibliothek positionierte Aktualisierungs- und Löschanweisungen simuliert.  
  
 Um eine positionierte Aktualisierungs- oder Löschanweisung zu verwenden, muss die Anwendung ein Resultset mit einer **SELECT FOR UPDATE-Anweisung** erstellen. Die Syntax dieser Anweisung lautet:  
  
 **SELECT** [**ALLE** &#124; **DISTINCT**] *Auswahlliste*  
  
 **Aus** *Tabellen-Referenzliste*  
  
 [**WHERE** *Suchbedingung*]  
  
 **FÜR DIE AKTUALISIERUNG von** [*Spaltenname* [**,** *Spaltenname*]...]  
  
 Die Anwendung positioniert dann den Cursor in der zu aktualisierenden oder zu löschenden Zeile. Dies kann geschehen, indem **SQLFetchScroll** aufgerufen wird, um ein Rowset mit der erforderlichen Zeile abzurufen, und **SQLSetPos** aufruft, um den Rowset-Cursor in dieser Zeile zu positionieren. Die Anwendung führt dann die positionierte Aktualisierungs- oder Löschanweisung in einer anderen Anweisung als der Anweisung aus, die vom Resultset verwendet wird. Die Syntax dieser Anweisungen lautet:  
  
 **UPDATE** *UPDATE-Tabellenname*  
  
 **SET** SET-Spaltenbezeichner *column-identifier* **=** -*Ausdruck* &#124; **NULL**  
  
 [**,** *Spaltenbezeichner* **=** -*Ausdruck* &#124; **NULL**]...  
  
 **WO STROM VON** *Cursor-NAME*  
  
 **AUS** *TABELLENNAME* **LÖSCHEN, WOBEI DER AKTUELLE** *CURSORNAME*  
  
 Beachten Sie, dass für diese Anweisungen ein Cursorname erforderlich ist. Die Anwendung kann entweder einen Cursornamen mit **SQLSetCursorName** angeben, bevor sie die Anweisung ausführt, die das Resultset erstellt, oder die Datenquelle kann automatisch einen Cursornamen generieren, wenn der Cursor erstellt wird. Im letzteren Fall ruft die Anwendung diesen Cursornamen für die Verwendung in positionierten Aktualisierungs- und Löschanweisungen ab, indem **sie SQLGetCursorName aufruft.**  
  
 Der folgende Code ermöglicht es einem Benutzer beispielsweise, durch die Tabelle "Customers" zu scrollen und Kundendatensätze zu löschen oder seine Adressen und Telefonnummern zu aktualisieren. Es ruft **SQLSetCursorName** auf, um einen Cursornamen anzugeben, bevor er die Resultmenge von Kunden erstellt und drei Anweisungshandles verwendet: *hstmtCust* für das Resultset, *hstmtUpdate* für eine positionierte Update-Anweisung und *hstmtDelete* für eine positionierte löschanweisung. Obwohl der Code separate Variablen an die Parameter in der positionierten Update-Anweisung binden kann, aktualisiert er die Rowsetpuffer und bindet die Elemente dieser Puffer. Dadurch werden die Rowsetpuffer mit den aktualisierten Daten synchronisiert.  
  
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
