---
title: Positionierte Updates (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52495f670986638cac02661240e349713424256e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305324"
---
# <a name="positioned-updates-odbc"></a>Positionierte Updates (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC unterstützt zwei Methoden für das Ausführen von positionierten Updates in einem Cursor:  
  
-   **SQLSetPos**  
  
-   WHERE CURRENT OF-Klausel  
  
 Der gebräuchlichere Ansatz ist die Verwendung von **SQLSetPos**. Es bietet die folgenden Optionen.  
  
 SQL_POSITION  
 Positioniert den Cursor in einer bestimmten Zeile im aktuellen Rowset.  
  
 SQL_REFRESH  
 Aktualisiert die an die Resultsetspalten gebundenen Programmvariablen mit den Werten aus der Zeile, in der der Cursor zurzeit positioniert ist.  
  
 SQL_UPDATE  
 Aktualisiert die aktuelle Zeile im Cursor mit den Werten aus den an die Resultsetspalten gebundenen Programmvariablen.  
  
 SQL_DELETE  
 Löscht die aktuelle Zeile im Cursor.  
  
 **SQLSetPos** kann mit jedem Anweisungsergebnissatz verwendet werden, wenn die Anweisungshandlecursorattribute so eingestellt sind, dass Servercursor verwendet werden. Die Resultsetspalten müssen an Programmvariablen gebunden sein. Sobald die Anwendung eine Zeile abgerufen hat, ruft sie **SQLSetPos**(SQL_POSTION) auf, um den Cursor in der Zeile zu positionieren. Die Anwendung könnte dann SQLSetPos(SQL_DELETE) aufrufen, um die aktuelle Zeile zu löschen, oder neue Datenwerte in die gebundenen Programmvariablen verschieben und SQLSetPos(SQL_UPDATE) aufrufen, um die aktuelle Zeile zu aktualisieren.  
  
 Anwendungen können jede Zeile im Rowset mit **SQLSetPos**aktualisieren oder löschen. Das Aufrufen von **SQLSetPos** ist eine praktische Alternative zum Erstellen und Ausführen einer SQL-Anweisung. **SQLSetPos** arbeitet mit dem aktuellen Rowset und kann nur nach einem Aufruf von [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)verwendet werden.  
  
 Die Rowsetgröße wird durch einen Aufruf von [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) mit dem Attributargument SQL_ATTR_ROW_ARRAY_SIZE festgelegt. **SQLSetPos** verwendet eine neue Rowsetgröße, jedoch erst nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**. Wenn z. B. die Rowsetgröße geändert wird, wird **SQLSetPos** aufgerufen, und dann wird **SQLFetch** oder **SQLFetchScroll** aufgerufen. Der Aufruf von **SQLSetPos** verwendet die alte Rowsetgröße, **aber SQLFetch** oder **SQLFetchScroll** verwendet die neue Rowsetgröße.  
  
 Die erste Zeile im Rowset ist die Zeile 1. Das RowNumber-Argument in **SQLSetPos** muss eine Zeile im Rowset identifizieren. Das heißt, sein Wert muss im Bereich zwischen 1 und der Anzahl der Zeilen liegen, die zuletzt abgerufen wurden. Diese ist eventuell kleiner als die Rowsetgröße. Wenn RowNumber 0 ist, gilt der Vorgang für jede Zeile im Rowset.  
  
 Durch den Löschvorgang von **SQLSetPos** wird die Datenquelle eine oder mehrere ausgewählte Zeilen einer Tabelle löschen. Um Zeilen mit **SQLSetPos**zu löschen, ruft die Anwendung **SQLSetPos** auf, wobei Operation auf SQL_DELETE festgelegt ist und RowNumber auf die Nummer der zu löschenden Zeile festgelegt ist. Wenn RowNumber 0 ist, werden alle Zeilen im Rowset gelöscht.  
  
 Nachdem **SQLSetPos** zurückgegeben wurde, ist die gelöschte Zeile die aktuelle Zeile, deren Status SQL_ROW_DELETED ist. Die Zeile kann nicht in weiteren positionierten Vorgängen verwendet werden, z. B. in Aufrufen von [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) oder **SQLSetPos**.  
  
 Wenn Sie alle Zeilen des Rowsets löschen (RowNumber ist gleich 0), kann die Anwendung verhindern, dass der Treiber bestimmte Zeilen löscht, indem sie das Zeilenoperationarray wie für den Aktualisierungsvorgang von **SQLSetPos**verwendet.  
  
 Jede Zeile, die gelöscht wird, sollte eine Zeile sein, die im Resultset vorhanden ist. Wenn die Anwendungspuffer beim Abrufen gefüllt werden und ein Zeilenstatusarray beibehalten wurde, sollten die Werte an jeder Zeilenposition nicht SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW sein.  
  
 Positionierte Updates können auch mit der WHERE CURRENT OF-Klausel für UPDATE-, DELETE- und INSERT-Anweisungen durchgeführt werden. WHERE CURRENT OF erfordert einen Cursornamen, den ODBC generiert, wenn die [SQLGetCursorName-Funktion](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) aufgerufen wird, oder den Sie durch Aufrufen von **SQLSetCursorName**angeben können. Im Folgenden finden Sie allgemeine Schritte zum Durchführen eines WHERE CURRENT OF-Updates in einer ODBC-Anwendung:  
  
-   Rufen Sie **SQLSetCursorName** auf, um einen Cursornamen für das Anweisungshandle einzurichten.  
  
-   Erstellen Sie eine SELECT-Anweisung mit einer FOR UPDATE OF-Klausel, und führen Sie sie aus.  
  
-   Rufen Sie **SQLFetchScroll** auf, um ein Rowset oder **SQLFetch** abzurufen, um eine Zeile abzurufen.  
  
-   Rufen Sie **SQLSetPos** (SQL_POSITION) auf, um den Cursor in der Zeile zu positionieren.  
  
-   Erstellen und führen Sie eine UPDATE-Anweisung mit einer WHERE CURRENT OF-Klausel mithilfe des Cursornamenssatzes mit **SQLSetCursorName**aus.  
  
 Alternativ können Sie **SQLGetCursorName** aufrufen, nachdem Sie die SELECT-Anweisung ausgeführt haben, anstatt **SQLSetCursorName** aufzurufen, bevor Sie die SELECT-Anweisung ausführen. **SQLGetCursorName** gibt einen von ODBC zugewiesenen Standardcursornamen zurück, wenn Sie keinen Cursornamen mit **SQLSetCursorName**festlegen.  
  
 **SQLSetPos** wird gegenüber WHERE CURRENT OF bevorzugt, wenn Sie Servercursor verwenden. Wenn Sie einen statischen, aktualisierbaren Cursor mit der ODBC-Cursorbibliothek verwenden, implementiert die Cursorbibliothek die WHERE CURRENT OF-Updates, indem eine WHERE-Klausel mit den Schlüsselwerten für die zugrunde liegende Tabelle hinzugefügt wird. Dies kann zu nicht beabsichtigten Updates führen, wenn die Schlüssel in der Tabelle nicht eindeutig sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
