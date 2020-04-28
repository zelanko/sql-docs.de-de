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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3ce09809c896a4d1d9333da00367f972655f96b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305741"
---
# <a name="executing-a-statement"></a>Ausführen einer Anweisung
Es gibt vier Möglichkeiten, eine Anweisung auszuführen, je nachdem, wann Sie von der Datenbank-Engine kompiliert (vorbereitet) werden und wer Sie definiert:  
  
-   **Direkte Ausführung** Die Anwendung definiert die SQL-Anweisung. Sie wird zur Laufzeit in einem einzigen Schritt vorbereitet und ausgeführt.  
  
-   **Vorbereitete Ausführung** Die Anwendung definiert die SQL-Anweisung. Sie wird zur Laufzeit in separaten Schritten vorbereitet und ausgeführt. Die Anweisung kann einmal vorbereitet und mehrmals ausgeführt werden.  
  
-   **Prozeduren** Die Anwendung kann während der Entwicklungszeit eine oder mehrere SQL-Anweisungen definieren und kompilieren und diese Anweisungen als Prozedur in der Datenquelle speichern. Die Prozedur wird zur Laufzeit einmal oder mehrmals ausgeführt. Die Anwendung kann verfügbare gespeicherte Prozeduren mithilfe von Katalog Funktionen aufzählen.  
  
-   **Katalog Funktionen** Der treiberwriter erstellt eine Funktion, die ein vordefiniertes Resultset zurückgibt. Normalerweise wird von dieser Funktion eine vordefinierte SQL-Anweisung übermittelt oder eine für diesen Zweck erstellte Prozedur aufgerufen. Die Funktion wird einmal oder mehrmals zur Laufzeit ausgeführt.  
  
 Eine bestimmte Anweisung (wie von Ihrem Anweisungs Handle identifiziert) kann beliebig oft ausgeführt werden. Die Anweisung kann mit einer Vielzahl von SQL-Anweisungen ausgeführt werden, oder Sie kann mit derselben SQL-Anweisung wiederholt ausgeführt werden. Im folgenden Code wird z. b. das gleiche Anweisungs Handle (*hstmt1*) verwendet, um die Tabellen in der Sales-Datenbank abzurufen und anzuzeigen. Anschließend wird dieses Handle erneut verwendet, um die Spalten in einer vom Benutzer ausgewählten Tabelle abzurufen.  
  
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
  
 Der folgende Code zeigt, wie ein einzelnes Handle zum wiederholten Ausführen derselben Anweisung verwendet wird, um Zeilen aus einer Tabelle zu löschen.  
  
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
  
 Bei vielen Treibern ist das Zuordnen von Anweisungen eine aufwändige Aufgabe. Daher ist die Wiederverwendung derselben Anweisung in der Regel effizienter als die Freigabe vorhandener Anweisungen und die Zuordnung neuer Anweisungen. Anwendungen, die Resultsets für eine-Anweisung erstellen, müssen darauf achten, den Cursor vor dem erneuten Ausführen der Anweisung über das Resultset zu schließen. Weitere Informationen finden Sie unter [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 Durch die Wiederverwendung von Anweisungen wird auch die Anwendung gezwungen, eine Einschränkung in einigen Treibern der Anzahl von Anweisungen zu vermeiden, die gleichzeitig aktiv sein können. Die genaue Definition von "Active" ist Treiber spezifisch, bezieht sich jedoch häufig auf jede Anweisung, die vorbereitet oder ausgeführt wurde und weiterhin Ergebnisse liefert. Nachdem eine **Insert** -Anweisung vorbereitet wurde, wird Sie z. b. in der Regel als aktiv betrachtet. Nachdem eine **Select** -Anweisung ausgeführt wurde und der Cursor weiterhin geöffnet ist, wird Sie im Allgemeinen als aktiv betrachtet. Nachdem eine **CREATE TABLE** -Anweisung ausgeführt wurde, gilt Sie im Allgemeinen nicht als aktiv.  
  
 Eine Anwendung bestimmt, wie viele Anweisungen gleichzeitig in einer einzelnen Verbindung aktiv sein können, indem **SQLGetInfo** mit der Option SQL_MAX_CONCURRENT_ACTIVITIES aufgerufen wird. Eine Anwendung kann durch das Öffnen mehrerer Verbindungen mit der Datenquelle mehr aktive Anweisungen als dieses Limit verwenden. Da Verbindungen teuer sein können, sollten die Auswirkungen auf die Leistung berücksichtigt werden.  
  
 Anwendungen können den Zeitraum begrenzen, der für die Ausführung einer-Anweisung mit dem SQL_ATTR_QUERY_TIMEOUT Statement-Attribut zugewiesen ist. Wenn das Timeout abläuft, bevor die Datenquelle das Resultset zurückgibt, gibt die Funktion, die die SQL-Anweisung ausführt, SQLSTATE HYT00 (Timeout abgelaufen) zurück. Standardmäßig ist kein Timeout festgelegt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [Vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [Ausführen von Katalogfunktionen](../../../odbc/reference/develop-app/executing-catalog-functions.md)
