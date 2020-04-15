---
title: Ausführen einer Anweisung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305741"
---
# <a name="executing-a-statement"></a>Ausführen einer Anweisung
Es gibt vier Möglichkeiten, eine Anweisung auszuführen, je nachdem, wann sie vom Datenbankmodul kompiliert (vorbereitet) werden und wer sie definiert:  
  
-   **Direkte Ausführung** Die Anwendung definiert die SQL-Anweisung. Es wird zur Laufzeit in einem einzigen Schritt vorbereitet und ausgeführt.  
  
-   **Vorbereitete Ausführung** Die Anwendung definiert die SQL-Anweisung. Es wird zur Laufzeit in separaten Schritten vorbereitet und ausgeführt. Die Anweisung kann einmal vorbereitet und mehrmals ausgeführt werden.  
  
-   **Verfahren** Die Anwendung kann eine oder mehrere SQL-Anweisungen zur Entwicklungszeit definieren und kompilieren und diese Anweisungen als Prozedur in der Datenquelle speichern. Die Prozedur wird zur Laufzeit ein oder mehrere Male ausgeführt. Die Anwendung kann verfügbare gespeicherte Prozeduren mithilfe von Katalogfunktionen aufzählen.  
  
-   **Katalogfunktionen** Der Treiberschreiber erstellt eine Funktion, die ein vordefiniertes Resultset zurückgibt. Normalerweise sendet diese Funktion eine vordefinierte SQL-Anweisung oder ruft eine zu diesem Zweck erstellte Prozedur auf. Die Funktion wird zur Laufzeit ein oder mehrere Male ausgeführt.  
  
 Eine bestimmte Anweisung (wie durch ihr Anweisungshandle identifiziert) kann bemalungsvoll ausgeführt werden. Die Anweisung kann mit einer Vielzahl verschiedener SQL-Anweisungen oder wiederholt mit derselben SQL-Anweisung ausgeführt werden. Der folgende Code verwendet z. B. dasselbe Anweisungshandle (*hstmt1*), um die Tabellen in der Sales-Datenbank abzurufen und anzuzeigen. Anschließend wird dieses Handle wiederverwendet, um die Spalten in einer vom Benutzer ausgewählten Tabelle abzurufen.  
  
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
  
 Und der folgende Code zeigt, wie ein einzelnes Handle verwendet wird, um dieselbe Anweisung wiederholt auszuführen, um Zeilen aus einer Tabelle zu löschen.  
  
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
  
 Für viele Treiber ist das Zuweisen von Anweisungen eine kostspielige Aufgabe, daher ist die Wiederverwendung derselben Anweisung auf diese Weise in der Regel effizienter als das Freiwerden vorhandener Anweisungen und das Zuweisen neuer Anweisungen. Anwendungen, die Resultsets für eine Anweisung erstellen, müssen darauf achten, den Cursor über dem Resultset zu schließen, bevor die Anweisung erneut ausgeführt wird. Weitere Informationen finden Sie unter [Schließen des Cursors](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 Das Wiederverwenden von Anweisungen erzwingt auch, dass die Anwendung eine Einschränkung der Anzahl der Anweisungen, die gleichzeitig aktiv sein können, in einigen Treibern vermeidet. Die genaue Definition von "aktiv" ist treiberspezifisch, bezieht sich jedoch häufig auf jede Anweisung, die vorbereitet oder ausgeführt wurde und über die Ergebnisse noch verfügen. Wenn z. B. eine **INSERT-Anweisung** vorbereitet wurde, wird sie im Allgemeinen als aktiv betrachtet. nachdem eine **SELECT-Anweisung** ausgeführt wurde und der Cursor noch geöffnet ist, wird sie im Allgemeinen als aktiv betrachtet. Nachdem eine **CREATE TABLE-Anweisung** ausgeführt wurde, wird sie im Allgemeinen nicht als aktiv betrachtet.  
  
 Eine Anwendung bestimmt, wie viele Anweisungen gleichzeitig für eine einzelne Verbindung aktiv sein können, indem **SIE SQLGetInfo** mit der Option SQL_MAX_CONCURRENT_ACTIVITIES aufruft. Eine Anwendung kann mehr aktive Anweisungen als diesen Grenzwert verwenden, indem sie mehrere Verbindungen zur Datenquelle öffnet. Da Verbindungen jedoch teuer sein können, sollten die Auswirkungen auf die Leistung berücksichtigt werden.  
  
 Anwendungen können die Zeit begrenzen, die für die Ausführung einer Anweisung mit dem Attribut SQL_ATTR_QUERY_TIMEOUT-Anweisung vorgesehen ist. Wenn der Timeoutzeitraum abläuft, bevor die Datenquelle das Resultset zurückgibt, gibt die Funktion, die die SQL-Anweisung ausführt, SQLSTATE HYT00 (Timeout abgelaufen) zurück. Standardmäßig ist kein Timeout festgelegt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Direkte Ausführung](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [Vorbereitete Ausführung](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [Prozeduren](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [Batches von SQL-Anweisungen](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [Ausführen von Katalogfunktionen](../../../odbc/reference/develop-app/executing-catalog-functions.md)
