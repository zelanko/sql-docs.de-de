---
title: SQL-Anweisungen zur Laufzeit erstellt | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 795335be2a2a3aab1be6dac26bf6d213161fe42e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301971"
---
# <a name="sql-statements-constructed-at-run-time"></a>SQL-Anweisungen, die zur Laufzeit erstellt werden
Anwendungen, die Ad-hoc-Analysen durchführen, erstellen normalerweise SQL-Anweisungen zur Laufzeit. Eine Kalkulationstabelle kann es einem Benutzer beispielsweise ermöglichen, Spalten auszuwählen, aus denen Daten abgerufen werden sollen:  
  
```  
// SQL_Statements_Constructed_at_Run_Time.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <sqltypes.h>  
  
int main() {  
   SQLCHAR *Statement = 0, *TableName = 0;  
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;  
   BOOL *ColumnSelectedArray = 0;  
   BOOL  CommaNeeded;  
   SQLSMALLINT i = 0, NumColumns = 0;  
  
   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the  
   // user select a table and store the selected table in TableName.  
  
   // Use SQLColumns to build a list of the columns in the selected table  
   // (ColumnNamesArray). Set NumColumns to the number of columns in the  
   // table. Let the user select one or more columns and flag these columns  
   // in ColumnSelectedArray[].  
  
   // Build a SELECT statement from the selected columns.  
   CommaNeeded = FALSE;  
   Statement = (SQLCHAR*)malloc(8);  
   strcpy_s((char*)Statement, 8, "SELECT ");  
  
   for (i = 0 ; i = NumColumns ; i++) {  
      if (ColumnSelectedArray[i]) {  
         if (CommaNeeded)  
            strcat_s((char*)Statement, sizeof(Statement), ",");  
         else  
            CommaNeeded = TRUE;  
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);  
      }  
   }  
  
   strcat_s((char*)Statement, 15, " FROM ");  
   // strcat_s((char*)Statement, 100, (char*)TableName);  
  
   // Execute the statement . It will be executed once, do not prepare it.  
   // SQLExecDirect(hstmt, Statement, SQL_NTS);  
}  
```  
  
 Eine weitere Klasse von Anwendungen, die normalerweise SQL-Anweisungen zur Laufzeit erstellt, sind Anwendungsentwicklungsumgebungen. Die Anweisungen, die sie erstellen, sind jedoch in der Anwendung, die sie erstellen, hartcodiert, wo sie in der Regel optimiert und getestet werden können.  
  
 Anwendungen, die SQL-Anweisungen zur Laufzeit erstellen, können dem Benutzer enorme Flexibilität bieten. Wie aus dem vorherigen Beispiel zu sehen ist, das **WHERE** nicht einmal solche allgemeinen Vorgänge wie WHERE-Klauseln, **ORDER BY-Klauseln** oder Joins unterstützte, ist das Erstellen von SQL-Anweisungen zur Laufzeit wesentlich komplexer als hard-coding-Anweisungen. Darüber hinaus ist das Testen solcher Anwendungen problematisch, da sie eine beliebige Anzahl von SQL-Anweisungen erstellen können.  
  
 Ein potenzieller Nachteil beim Erstellen von SQL-Anweisungen zur Laufzeit besteht darin, dass das Erstellen einer Anweisung viel mehr Zeit in Anspruch nimmt als die Verwendung einer hartcodierten Anweisung. Glücklicherweise ist dies selten ein Problem. Solche Anwendungen sind in der Regel benutzeroberflächenintensiv, und die Zeit, die die Anwendung mit dem Erstellen von SQL-Anweisungen verbringt, ist im Allgemeinen gering im Vergleich zu der Zeit, die der Benutzer mit der Eingabe von Kriterien verbringt.
