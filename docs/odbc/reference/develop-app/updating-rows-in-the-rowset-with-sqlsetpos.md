---
title: Aktualisieren von Zeilen im Rowset mit SQLSetPos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating rows
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4851d4ba741379fc188b2b88c895a378ef3bb80d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298970"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Aktualisieren von Zeilen im Rowset mit SQLSetPos
Der Aktualisierungsvorgang von **SQLSetPos** macht die Datenquelle nmöglich, eine oder mehrere ausgewählte Zeilen einer Tabelle zu aktualisieren, wobei Daten in den Anwendungspuffern für jede gebundene Spalte verwendet werden (es sei denn, der Wert im Längen-/Indikatorpuffer ist SQL_COLUMN_IGNORE). Spalten, die nicht gebunden sind, werden nicht aktualisiert.  
  
 Um Zeilen mit **SQLSetPos**zu aktualisieren, führt die Anwendung die folgenden Schritte aus:  
  
1.  Platziert die neuen Datenwerte in den Rowsetpuffern. Informationen zum Senden langer Daten mit **SQLSetPos**finden Sie unter [Long Data und SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Legt den Wert im Längen-/Indikatorpuffer jeder Spalte nach Bedarf fest. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten, die an Zeichenfolgenpuffer gebunden sind, die Bytelänge der Daten für Spalten, die an Binärpuffer gebunden sind, und SQL_NULL_DATA für alle Spalten, die auf NULL festgelegt werden sollen.  
  
3.  Legt den Wert im Längen-/Indikatorpuffer der Spalten fest, die nicht auf SQL_COLUMN_IGNORE aktualisiert werden sollen. Obwohl die Anwendung diesen Schritt überspringen und vorhandene Daten erneut senden kann, ist dies ineffizient und besteht die Gefahr, dass Werte an die Datenquelle gesendet werden, die beim Lesen abgeschnitten wurden.  
  
4.  Ruft **SQLSetPos** *auf,* wobei Operation auf SQL_UPDATE festgelegt ist und *RowNumber* auf die Nummer der zu aktualisierenden Zeile festgelegt ist. Wenn *RowNumber* 0 ist, werden alle Zeilen im Rowset aktualisiert.  
  
 Nachdem **SQLSetPos** zurückgegeben wurde, wird die aktuelle Zeile auf die aktualisierte Zeile festgelegt.  
  
 Beim Aktualisieren aller Zeilen des Rowsets *(RowNumber* ist gleich 0) kann eine Anwendung die Aktualisierung bestimmter Zeilen deaktivieren, indem die entsprechenden Elemente des Zeilenoperationarrays (auf die durch das Attribut SQL_ATTR_ROW_OPERATION_PTR-Anweisung verwiesen wird) auf SQL_ROW_IGNORE. Das Zeilenoperationarray entspricht in Größe und Anzahl der Elemente dem Zeilenstatusarray (auf das durch das Attribut SQL_ATTR_ROW_STATUS_PTR Anweisung verwiesen wird). Um nur die Zeilen im Resultset zu aktualisieren, die erfolgreich abgerufen und nicht aus dem Rowset gelöscht wurden, verwendet die Anwendung das Zeilenstatusarray aus der Funktion, die das Rowset als Zeilenoperationarray nach **SQLSetPos**abgerufen hat.  
  
 Für jede Zeile, die als Aktualisierung an die Datenquelle gesendet wird, sollten die Anwendungspuffer über gültige Zeilendaten verfügen. Wenn die Anwendungspuffer durch Abrufen gefüllt wurden und ein Zeilenstatusarray beibehalten wurde, sollten seine Werte an jeder dieser Zeilenpositionen nicht SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW sein.  
  
 Der folgende Code ermöglicht es einem Benutzer beispielsweise, durch die Tabelle Customers zu scrollen und neue Zeilen zu aktualisieren, zu löschen oder hinzuzufügen. Die neuen Daten werden in den Rowsetpuffern platziert, bevor **SQLSetPos** aufgerufen wird, um neue Zeilen zu aktualisieren oder hinzuzufügen. Eine zusätzliche Zeile wird am Ende der Rowsetpuffer zugewiesen, um neue Zeilen zu halten. Dadurch wird verhindert, dass vorhandene Daten überschrieben werden, wenn Daten für eine neue Zeile in den Puffern platziert werden.  
  
```  
#define UPDATE_ROW   100  
#define DELETE_ROW   101  
#define ADD_ROW      102  
  
SQLUINTEGER    CustIDArray[11];  
SQLCHAR        NameArray[11][51], AddressArray[11][51],   
               PhoneArray[11][11];  
SQLINTEGER     CustIDIndArray[11], NameLenOrIndArray[11],   
               AddressLenOrIndArray[11],  
               PhoneLenOrIndArray[11];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]), NameLenOrIndArray);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
            AddressLenOrIndArray);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmt, "SELECT CustID, Name, Address, Phone FROM Customers", SQL_NTS);  
  
// Fetch and display the first 10 rows.  
rc = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
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
         SQLFetchScroll(hstmt, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray,  
                     NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray,  
                     PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case UPDATE_ROW:  
         // Place the new data in the rowset buffers and update the   
         // specified row.  
         GetNewData(&CustIDArray[RowNum - 1], &CustIDIndArray[RowNum - 1],  
                  NameArray[RowNum - 1], &NameLenOrIndArray[RowNum - 1],  
                  AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                  PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
         SQLSetPos(hstmt, RowNum, SQL_UPDATE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case DELETE_ROW:  
         // Delete the specified row.  
         SQLSetPos(hstmt, RowNum, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case ADD_ROW:  
         // Place the new data in the rowset buffers at index 10.   
         // This is an extra element for new rows so rowset data is   
         // not overwritten. Insert the new row. Row 11 corresponds   
         // to index 10.  
         GetNewData(&CustIDArray[10], &CustIDIndArray[10],  
                     NameArray[10], &NameLenOrIndArray[10],  
                     AddressArray[10], &AddressLenOrIndArray[10],  
                     PhoneArray[10], &PhoneLenOrIndArray[10]);  
         SQLSetPos(hstmt, 11, SQL_ADD, SQL_LOCK_NO_CHANGE);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
