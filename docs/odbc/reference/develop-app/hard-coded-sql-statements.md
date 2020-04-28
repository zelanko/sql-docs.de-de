---
title: Hart codierte SQL-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], hard-coded
- hard-coded SQL statements [ODBC]
- SQL statements [ODBC], constructing
ms.assetid: e355f5f1-4f1a-4933-8c74-ee73e90d2d19
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7a092742e5f0151b7b08f434b453645cbd804a5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300200"
---
# <a name="hard-coded-sql-statements"></a>Hartcodierte SQL-Anweisungen
Anwendungen, die eine feste Aufgabe ausführen, enthalten in der Regel hart codierte SQL-Anweisungen. Beispielsweise kann ein Bestell Eintrags System den folgenden-Befehl verwenden, um offene Verkaufsaufträge aufzulisten:  
  
```  
SQLExecDirect(hstmt, "SELECT OrderID FROM Orders WHERE Status = 'OPEN'", SQL_NTS);  
```  
  
 Hart codierte SQL-Anweisungen haben mehrere Vorteile: Sie können beim Schreiben der Anwendung getestet werden. Sie sind einfacher zu implementieren als Anweisungen, die zur Laufzeit erstellt werden. Außerdem vereinfachen Sie die Anwendung.  
  
 Die Verwendung von Anweisungs Parametern und Vorbereitungs Anweisungen bietet noch bessere Möglichkeiten, hart codierte SQL-Anweisungen zu verwenden. Angenommen, die parts-Tabelle enthält die Spalten partid, Description und Price. Eine Möglichkeit, eine neue Zeile in diese Tabelle einzufügen, besteht darin, eine **Insert** -Anweisung zu erstellen und auszuführen:  
  
```  
#define DESC_LEN 51  
#define STATEMENT_LEN 51  
  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN], Statement[STATEMENT_LEN];  
SQLREAL       Price;  
  
// Set part ID, description, and price.  
GetNewValues(&PartID, Desc, &Price);  
  
// Build INSERT statement.  
sprintf_s(Statement, 100, "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (%d, '%s', %f)", PartID, Desc, Price);  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
```  
  
 Eine noch bessere Möglichkeit besteht darin, eine hart codierte, parametrisierte-Anweisung zu verwenden. Dies hat zwei Vorteile gegenüber einer Anweisung mit hart codierten Datenwerten. Erstens ist es einfacher, eine parametrisierte-Anweisung zu erstellen, da die Datenwerte in ihren systemeigenen Typen, z. b. ganze Zahlen und Gleit Komma Zahlen, gesendet werden können, anstatt Sie in Zeichen folgen zu konvertiert. Zweitens kann eine solche Anweisung mehr als einmal verwendet werden, indem Sie die Parameterwerte ändern und Sie erneut ausführen. Es ist nicht erforderlich, Sie neu zu erstellen.  
  
```  
#define DESC_LEN 51  
  
SQLCHAR * Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (?, ?, ?)";  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Set part ID, description, and price.  
GetNewValues(&PartID, Desc, &Price);  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
```  
  
 Wenn Sie davon ausgehen, dass diese Anweisung mehrmals ausgeführt werden soll, kann Sie für noch mehr Effizienz vorbereitet werden:  
  
```  
#define DESC_LEN 51  
  
SQLCHAR *Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (?, ?, ?)";  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Prepare the INSERT statement.  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Loop to continually get new values and insert them.  
while (GetNewValues(&PartID, Desc, &Price))  
   SQLExecute(hstmt);  
```  
  
 Möglicherweise ist die Verwendung der-Anweisung die effizienteste Methode, um eine Prozedur zu erstellen, die die-Anweisung enthält, wie im folgenden Codebeispiel gezeigt. Da die Prozedur zur Entwicklungszeit erstellt und in der Datenquelle gespeichert wird, muss Sie zur Laufzeit nicht vorbereitet werden. Ein Nachteil dieser Methode besteht darin, dass die Syntax zum Erstellen von Prozeduren DBMS-spezifisch ist und Prozeduren für jedes DBMS, auf dem die Anwendung ausgeführt werden soll, separat erstellt werden müssen.  
  
```  
#define DESC_LEN 51  
  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Loop to continually get new values and insert them.  
while (GetNewValues(&PartID, Desc, &Price))  
   SQLExecDirect(hstmt, "{call InsertPart(?, ?, ?)}", SQL_NTS);  
```  
  
 Weitere Informationen zu Parametern, vorbereiteten Anweisungen und Prozeduren finden Sie unter [Ausführen einer Anweisung](../../../odbc/reference/develop-app/executing-a-statement.md).
