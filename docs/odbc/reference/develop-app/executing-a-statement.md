---
title: Ausführen einer Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], executing
ms.assetid: e5f0d2ee-0453-4faf-b007-12978dd300a1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5660cfe2f264e0971d30cd2eaf1aadf68581321e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63032811"
---
# <a name="executing-a-statement"></a>Ausführen einer Anweisung
Es gibt vier Möglichkeiten zum Ausführen einer Anweisung abhängig ist, wenn sie kompiliert werden (vorbereitet), indem Sie die Datenbank-Engine und, die sie definiert:  
  
-   **Direkte Ausführung** die Anwendung definiert, die SQL-Anweisung. Es wird vorbereitet und zur Laufzeit in einem einzigen Schritt ausgeführt.  
  
-   **Vorbereitete Ausführung** die Anwendung definiert, die SQL-Anweisung. Es wird vorbereitet und zur Laufzeit in getrennten Schritten ausgeführt. Die Anweisung einmal vorbereitet, und mehrere Male ausgeführt werden kann.  
  
-   **Prozeduren** kann die Anwendung zu definieren und kompilieren Sie eine oder mehrere SQL-Anweisungen auf die Entwicklung, Zeit, und speichern Sie diese Anweisungen für die Datenquelle als eine Prozedur. Die Prozedur wird einmal oder mehrmals zur Laufzeit ausgeführt. Die Anwendung kann die verfügbare gespeicherte Prozeduren verwenden von Katalogfunktionen auflisten.  
  
-   **Katalogfunktionen** der Treiber-Writer erstellt eine Funktion, die ein vordefiniertes Resultset zurückgibt. In der Regel wird diese Funktion übermittelt eine vordefinierte SQL­Anweisung, oder ruft eine Prozedur, die für diesen Zweck erstellt wurde. Die Funktion wird einmal oder mehrmals zur Laufzeit ausgeführt.  
  
 (Wie von seinem Anweisungshandle gekennzeichnet) kann eine bestimmte Anweisung werden oft ausgeführt. Die Anweisung mit einer Vielzahl von verschiedenen SQL-Anweisungen ausgeführt werden kann, oder sie können mit der gleichen SQL-Anweisung wiederholt ausgeführt werden. Der folgende Code verwendet beispielsweise dasselbe Anweisungshandle (*hstmt1*) abgerufen und in den Tabellen in der Sales-Datenbank angezeigt. Klicken Sie dann wiederverwendet dieses Handle zum Abrufen der Spalten in einer Tabelle, die vom Benutzer ausgewählten.  
  
```  
SQLHSTMT    hstmt1;  
SQLCHAR *   Table;  
  
// Create a result set of all tables in the Sales database.  
SQLTables(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, NULL, 0, NULL, 0);  
  
// Fetch and display the table names; then close the cursor.  
// Code not shown.  
  
// Have the user select a particular table.  
SelectTable(Table);  
  
// Reuse hstmt1 to create a result set of all columns in Table.  
SQLColumns(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, Table, SQL_NTS, NULL, 0);  
  
// Fetch and display the column names in Table; then close the cursor.  
// Code not shown.  
```  
  
 Und der folgende Code zeigt die Verwendung ein einzelnes Handles zur wiederholten Ausführung von der gleichen Anweisung zum Löschen von Zeilen aus einer Tabelle.  
  
```  
SQLHSTMT      hstmt1;  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
  
// Prepare a statement to delete orders from the Orders table.  
SQLPrepare(hstmt1, "DELETE FROM Orders WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter for the OrderID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &OrderID, 0, &OrderIDInd);  
  
// Repeatedly execute hstmt1 with different values of OrderID.  
while ((OrderID = GetOrderID()) != 0) {  
   SQLExecute(hstmt1);  
}  
```  
  
 Für viele Treiber ist Zuordnen von Anweisungen als teuer, daher Wiederverwenden der gleichen Anweisung auf diese Weise in der Regel effizienter als das Freigeben von vorhandenen Anweisungen sowie Zuweisen von neuen virtuellen Computern. Anwendungen, die Resultsets in einer Anweisung zu erstellen, müssen darauf achten, schließen Sie den Cursor über das Ergebnis festlegen, bevor Sie die Anweisung reexecuting sein; Weitere Informationen finden Sie unter [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 Wiederverwenden von Anweisungen erzwingt auch die Anwendung aus, um eine Einschränkung in einige Treiber, der die Anzahl von Anweisungen zu vermeiden, die gleichzeitig aktiv sein können. Die genaue Definition von "aktiv" ist treiberspezifisch, aber es bezieht sich häufig auf eine Anweisung, die vorbereitet oder ausgeführt wurde und noch immer zur Verfügung stehenden Ergebnisse. Z. B. nach einer **einfügen** Anweisung vorbereitet wurde, dies wird im Allgemeinen als aktiv ist, werden nach dem ein **wählen** Anweisung ausgeführt wurde und der Cursor noch geöffnet ist, wird in der Regel als betrachtet aktiv sein; Nachdem eine **CREATE TABLE** Anweisung ausgeführt wurde, wird nicht in der Regel als betrachtet aktiv sein.  
  
 Eine Anwendung bestimmt, wie viele SoHs auf eine einzelne Verbindung gleichzeitig aktiv sein können, durch den Aufruf **SQLGetInfo** mit der Option SQL_MAX_CONCURRENT_ACTIVITIES. Eine Anwendung kann mehr aktive Anweisungen über diesem Grenzwert verwenden, öffnen Sie mehrere Verbindungen mit der Datenquelle; Da Verbindungen teuer sein können, sollten jedoch die Auswirkungen auf die Leistung berücksichtigt werden.  
  
 Anwendungen können die Zeitspanne, die für eine Anweisung mit der SQL_ATTR_QUERY_TIMEOUT-Anweisungsattribut vorgesehene einschränken. Wenn das Timeout abläuft, bevor Sie die Datenquelle über das Resultset zurückgibt, gibt die Funktion, die die SQL-Anweisung ausführen SQLSTATE HYT00 zurück (das Timeout ist abgelaufen). Standardmäßig wird keine zeitliche Beschränkung.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [Vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [Vorgehensweisen](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [Ausführen von Katalogfunktionen](../../../odbc/reference/develop-app/executing-catalog-functions.md)
