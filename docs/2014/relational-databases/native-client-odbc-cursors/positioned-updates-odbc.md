---
title: Positionierte Updates (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2336944b583b6077d75bd5155bb4b52c66d9a852
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63200524"
---
# <a name="positioned-updates-odbc"></a>Positionierte Updates (ODBC)
  ODBC unterstützt zwei Methoden für das Ausführen von positionierten Updates in einem Cursor:  
  
-   **SQLSetPos**  
  
-   WHERE CURRENT OF-Klausel  
  
 Der gängigste Ansatz ist die Verwendung von **SQLSetPos**. Es bietet die folgenden Optionen.  
  
 SQL_POSITION  
 Positioniert den Cursor in einer bestimmten Zeile im aktuellen Rowset.  
  
 SQL_REFRESH  
 Aktualisiert die an die Resultsetspalten gebundenen Programmvariablen mit den Werten aus der Zeile, in der der Cursor zurzeit positioniert ist.  
  
 SQL_UPDATE  
 Aktualisiert die aktuelle Zeile im Cursor mit den Werten aus den an die Resultsetspalten gebundenen Programmvariablen.  
  
 SQL_DELETE  
 Löscht die aktuelle Zeile im Cursor.  
  
 **SQLSetPos** können mit jedem Anweisungs Ergebnissatz verwendet werden, wenn die Cursor Attribute des Anweisungs Handles für die Verwendung von Server Cursorn festgelegt sind. Die Resultsetspalten müssen an Programmvariablen gebunden sein. Sobald die Anwendung eine Zeile abgerufen hat, ruft Sie **SQLSetPos**(SQL_POSTION) auf, um den Cursor in der Zeile zu positionieren. Die Anwendung könnte dann SQLSetPos(SQL_DELETE) aufrufen, um die aktuelle Zeile zu löschen, oder neue Datenwerte in die gebundenen Programmvariablen verschieben und SQLSetPos(SQL_UPDATE) aufrufen, um die aktuelle Zeile zu aktualisieren.  
  
 Anwendungen können jede Zeile im Rowset mit **SQLSetPos**aktualisieren oder löschen. Das Aufrufen von **SQLSetPos** ist eine bequeme Alternative zum Erstellen und Ausführen einer SQL-Anweisung. **SQLSetPos** funktioniert auf dem aktuellen Rowset und kann nur nach einem [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)-Aufrufvorgang verwendet werden.  
  
 Die Rowsetgröße wird durch einen Aufrufen von [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) mit dem Attribut Argument SQL_ATTR_ROW_ARRAY_SIZE festgelegt. **SQLSetPos** verwendet eine neue Rowsetgröße, jedoch erst nach einem-Befehl von **SQLFetch** oder **SQLFetchScroll**. Wenn z. b. die Rowsetgröße geändert wird, wird **SQLSetPos** aufgerufen und dann **SQLFetch** oder **SQLFetchScroll** aufgerufen. Beim Aufrufen von **SQLSetPos** wird die alte Rowsetgröße verwendet, aber **SQLFetch** oder **SQLFetchScroll** verwendet die neue Rowsetgröße.  
  
 Die erste Zeile im Rowset ist die Zeile 1. Das RowNumber-Argument in **SQLSetPos** muss eine Zeile im Rowset identifizieren. Das heißt, der Wert muss im Bereich zwischen 1 und der Anzahl von Zeilen liegen, die zuletzt abgerufen wurden. Diese ist eventuell kleiner als die Rowsetgröße. Wenn RowNumber 0 ist, gilt der Vorgang für jede Zeile im Rowset.  
  
 Der DELETE-Vorgang von **SQLSetPos** bewirkt, dass die Datenquelle eine oder mehrere ausgewählte Zeilen einer Tabelle löscht. Zum Löschen von Zeilen mit **SQLSetPos**Ruft die Anwendung **SQLSetPos** auf, wobei Operation auf SQL_DELETE und RowNumber auf die Nummer der zu löschenden Zeile festgelegt ist. Wenn RowNumber 0 ist, werden alle Zeilen im Rowset gelöscht.  
  
 Nach dem zurückkehren von **SQLSetPos** ist die gelöschte Zeile die aktuelle Zeile, und Ihr Status ist SQL_ROW_DELETED. Die Zeile kann nicht in weiteren positionierten Vorgängen verwendet werden, z. b. bei Aufrufen von [SQLGetData](../native-client-odbc-api/sqlgetdata.md) oder **SQLSetPos**.  
  
 Wenn Sie alle Zeilen des Rowsets löschen (RowNumber ist gleich 0), kann die Anwendung verhindern, dass der Treiber bestimmte Zeilen löscht, indem er das Zeilen Vorgangs Array genau wie für den Aktualisierungs Vorgang von **SQLSetPos**verwendet.  
  
 Jede Zeile, die gelöscht wird, sollte eine Zeile sein, die im Resultset vorhanden ist. Wenn die Anwendungspuffer beim Abrufen gefüllt werden und ein Zeilenstatusarray beibehalten wurde, sollten die Werte an jeder Zeilenposition nicht SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW sein.  
  
 Positionierte Updates können auch mit der WHERE CURRENT OF-Klausel für UPDATE-, DELETE- und INSERT-Anweisungen durchgeführt werden. WHERE CURRENT of erfordert einen Cursor Namen, den ODBC generiert, wenn die [SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md) -Funktion aufgerufen wird, oder die Sie durch Aufrufen von **SQLSetCursorName**angeben können. Im Folgenden finden Sie allgemeine Schritte zum Durchführen eines WHERE CURRENT OF-Updates in einer ODBC-Anwendung:  
  
-   Aufrufen von **SQLSetCursorName** , um einen Cursor Namen für das Anweisungs Handle festzulegen.  
  
-   Erstellen Sie eine SELECT-Anweisung mit einer FOR UPDATE OF-Klausel, und führen Sie sie aus.  
  
-   Rufen Sie **SQLFetchScroll** auf, um ein Rowset oder **SQLFetch** zum Abrufen einer Zeile abzurufen.  
  
-   Aufrufen von **SQLSetPos** (SQL_POSITION), um den Cursor in der Zeile zu positionieren.  
  
-   Erstellen Sie eine Update-Anweisung mit einer WHERE CURRENT OF-Klausel, und führen Sie Sie mit dem mit **SQLSetCursorName**festgelegten Cursor Namen aus.  
  
 Alternativ könnten Sie **sqlgetcursor Name** auch aufrufen, nachdem Sie die SELECT-Anweisung ausgeführt haben, anstatt **sqlsetcursor Name** vor dem Ausführen der SELECT-Anweisung aufzurufen. **SQLGetCursorName** gibt einen von ODBC zugewiesenen standardmäßigen Cursor Namen zurück, wenn Sie keinen Cursor Namen mithilfe von **SQLSetCursorName**festlegen.  
  
 **SQLSetPos** wird von WHERE CURRENT of bevorzugt, wenn Sie Server Cursor verwenden. Wenn Sie einen statischen, aktualisierbaren Cursor mit der ODBC-Cursorbibliothek verwenden, implementiert die Cursorbibliothek die WHERE CURRENT OF-Updates, indem eine WHERE-Klausel mit den Schlüsselwerten für die zugrunde liegende Tabelle hinzugefügt wird. Dies kann zu nicht beabsichtigten Updates führen, wenn die Schlüssel in der Tabelle nicht eindeutig sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Cursorn &#40;ODBC-&#41;](using-cursors-odbc.md)  
  
  
