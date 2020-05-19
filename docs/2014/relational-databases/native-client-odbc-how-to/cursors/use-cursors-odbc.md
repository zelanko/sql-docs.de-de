---
title: Verwenden von Cursorn (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4be434e4d80a8146b58beb0ae0de07e62415a6ad
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701580"
---
# <a name="use-cursors-odbc"></a>Verwenden von Cursorn (ODBC)
    
### <a name="to-use-cursors"></a>So verwenden Sie Cursor  
  
1.  Rufen Sie [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) auf, um die gewünschten Cursorattribute festzulegen:  
  
     Legen Sie die Attribute SQL_ATTR_CURSOR_TYPE und SQL_ATTR_CONCURRENCY fest (dies ist die bevorzugte Option).  
  
     Oder  
  
     Legen Sie die Attribute SQL_CURSOR_SCROLLABLE und SQL_CURSOR_SENSITIVITY fest.  
  
2.  Rufen Sie [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) auf, um die Rowsetgröße mit dem SQL_ATTR_ROW_ARRAY_SIZE-Attribut festzulegen.  
  
3.  Sie können auch [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) aufrufen, um einen Cursornamen festzulegen, wenn positionierte Updates mit der WHERE CURRENT OF-Klausel durchgeführt werden.  
  
4.  Führen Sie die SQL-Anweisung aus.  
  
5.  Sie können optional auch [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) aufrufen, um den Cursornamen abzurufen, wenn positionierte Updates mit der WHERE CURRENT OF-Klausel durchgeführt werden und in Schritt 3 mit [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) kein Cursorname angegeben wurde.  
  
6.  Rufen Sie [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) auf, um die Anzahl von Spalten (C) im Rowset abzurufen.  
  
     Verwenden Sie spaltenbezogene Bindungen.  
  
     \- oder -  
  
     Verwenden Sie zeilenbezogene Bindungen.  
  
7.  Rufen Sie beliebige Rowsets vom Cursor ab.  
  
8.  Rufen [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) auf, um zu ermitteln, ob ein anderes Resultset verfügbar ist.  
  
    -   Wenn SQL_SUCCESS zurückgegeben wird, ist ein anderes Resultset verfügbar.  
  
    -   Wenn SQL_NO_DATA zurückgegeben wird, sind keine weiteren Resultsets verfügbar.  
  
    -   Wenn SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgegeben wird, rufen Sie [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) auf, um festzustellen, ob die Ausgabe von einer PRINT- oder RAISERROR-Anweisung verfügbar ist.  
  
     Wenn für Ausgabeparameter oder für den Rückgabewert einer gespeicherten Prozedur gebundene Anweisungsparameter verwendet werden, verwenden Sie die jetzt in den Puffern für gebundene Parameter verfügbaren Daten.  
  
     Wenn gebundene Parameter verwendet werden, hat jeder Aufruf von [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) oder [SQLExecDirect die SQL](https://go.microsoft.com/fwlink/?LinkId=58399)-Anweisung S mal ausgeführt, wobei S die Anzahl der Elemente im Array von gebundenen Parametern ist. Das bedeutet, dass S Ergebnismengen verarbeitet werden müssen, wobei jede Ergebnismenge sämtliche Resultsets, Ausgabeparameter und Rückgabecodes enthält, die in der Regel von einer einzelnen Ausführung der SQL-Anweisung zurückgegeben werden.  
  
     Wenn ein Resultset COMPUTE-Zeilen enthält, wird jede COMPUTE-Zeile als eigenes Resultset verfügbar gemacht. Diese COMPUTE-Resultsets werden in die normalen Zeilen eingefügt und teilen normale Zeilen in mehrere Resultsets.  
  
9. Sie können optional [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) mit SQL_UNBIND aufrufen, um Puffer mit gebundenen Spalten freizugeben.  
  
10. Wenn ein weiteres Resultset verfügbar ist, fahren Sie mit Schritt 6 fort.  
  
     Wenn in Schritt 9 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) für ein teilweise verarbeitetes Resultset aufgerufen wird, wird das restliche Resultset gelöscht. Eine andere Möglichkeit, ein teilweise verarbeitetes Resultset zu löschen, besteht darin, [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) aufzurufen.  
  
     Sie können den Typ des verwendeten Cursors entweder durch die Festlegung von SQL_ATTR_CURSOR_TYPE und SQL_ATTR_CONCURRENCY oder die Festlegung von SQL_ATTR_CURSOR_SENSITIVITY und SQL_ATTR_CURSOR_SCROLLABLE steuern. Sie sollten die zwei Methoden zur Angabe des Cursorverhaltens nicht kombinieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst-wie-Themen zur Verwendung von Cursorn &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)  
  
  
