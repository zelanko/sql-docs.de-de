---
title: Hartcodierte SQL-Anweisungen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 383a81aea121882b334bbfdab806408ac0513893
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746238"
---
# <a name="hard-coded-sql-statements"></a>Hartcodierte SQL-Anweisungen
Anwendungen, die feste Aufgabe in der Regel enthalten hartcodierte SQL-Anweisungen. Beispielsweise kann ein Liste der offenen Aufträge den folgenden Aufruf verwenden:  
  
```  
SQLExecDirect(hstmt, "SELECT OrderID FROM Orders WHERE Status = 'OPEN'", SQL_NTS);  
```  
  
 Es gibt mehrere Vorteile in hartcodierten SQL-Anweisungen: sie können getestet werden, wenn die Anwendung geschrieben wird; Sie sind einfacher zu implementieren als Anweisungen, die zur Laufzeit erstellt. und sie die Anwendung vereinfachen.  
  
 Verwenden von Anweisungsparametern und Vorbereiten von Anweisungen bieten bessere Möglichkeiten, hartcodierte SQL-Anweisungen zu verwenden. Nehmen wir beispielsweise an, dass die Parts-Tabelle die Spalten PartID, Beschreibung und Preis enthält. Eine Möglichkeit, eine neue Zeile in dieser Tabelle einfügen wäre das Erstellen und führen eine **einfügen** Anweisung:  
  
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
  
 Eine noch bessere Möglichkeit ist eine hartcodierte, parametrisierte Anweisung verwenden. Dies hat zwei Vorteile gegenüber einer Anweisung mit hartcodierten Datenwerte. Zunächst ist es einfacher, die eine parametrisierte Anweisung erstellt werden, da die Datenwerte in deren systemeigenen Typen, z. B. ganze Zahlen und Gleitkommazahlen anstelle der Konvertierung in Zeichenfolgen gesendet werden können. Andererseits kann eine solche Anweisung mehr als einmal verwendet werden, indem Sie einfach die Parameterwerte ändern, und es reexecuting; Es ist nicht erforderlich, ihn neu zu erstellen.  
  
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
  
 Wenn, dass diese Anweisung ist mehr als einmal ausgeführt werden, können sie für noch größeren Effizienz vorbereitet werden:  
  
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
  
 Möglicherweise ist die effizienteste Methode mithilfe die Anweisung um eine Prozedur mit der Anweisung zu erstellen, wie im folgenden Codebeispiel wird gezeigt ein. Da die Prozedur, die zum Zeitpunkt der Entwicklung erstellt und in der Datenquelle gespeichert, muss es nicht zur Laufzeit vorbereitet werden. Ein Nachteil dieser Methode ist, dass die Syntax zum Erstellen von Prozeduren DBMS-spezifische und Prozeduren separat werden, für die jeweiligen Datenbankverwaltungssystem, die auf dem die Anwendung ausgeführt werden erstellt müssen soll.  
  
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
  
 Weitere Informationen zu Parametern, vorbereitete Anweisungen und Verfahren finden Sie unter [Ausführen einer Anweisung](../../../odbc/reference/develop-app/executing-a-statement.md).
