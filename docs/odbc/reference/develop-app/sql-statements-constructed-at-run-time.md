---
description: SQL-Anweisungen, die zur Laufzeit erstellt werden
title: Zur Laufzeit erstellte SQL-Anweisungen | Microsoft-Dokumentation
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
ms.openlocfilehash: fff9f7a4e579ce4e1d1177b8f5fa67f7d13a4fdc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424552"
---
# <a name="sql-statements-constructed-at-run-time"></a>SQL-Anweisungen, die zur Laufzeit erstellt werden
Anwendungen, die Ad-hoc-Analysen ausführen, erstellen häufig SQL-Anweisungen zur Laufzeit. Beispielsweise kann ein Benutzer mithilfe einer Kalkulations Tabelle Spalten auswählen, aus denen Daten abgerufen werden sollen:  
  
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
  
 Eine andere Klasse von Anwendungen, die häufig SQL-Anweisungen zur Laufzeit erstellt, sind Anwendungsentwicklungsumgebungen. Die von Ihnen konstruierenden Anweisungen sind jedoch in der Anwendung hart codiert, in der Sie normalerweise optimiert und getestet werden können.  
  
 Anwendungen, die SQL-Anweisungen zur Laufzeit erstellen, können dem Benutzer enorme Flexibilität verleihen. Wie aus dem vorherigen Beispiel ersichtlich ist, das nicht einmal solche gängigen Vorgänge als **Where** -Klauseln, **Order by** -Klauseln oder Joins unterstützt, ist das Erstellen von SQL-Anweisungen zur Laufzeit weitaus komplexer als hart codierungsanweisungen. Außerdem ist das Testen solcher Anwendungen problematisch, da Sie eine beliebige Anzahl von SQL-Anweisungen erstellen können.  
  
 Ein potenzieller Nachteil der Erstellung von SQL-Anweisungen zur Laufzeit besteht darin, dass es viel länger dauert, eine-Anweisung zu erstellen, als eine hart codierte Anweisung zu verwenden. Glücklicherweise ist dies selten ein Problem. Solche Anwendungen sind tendenziell Benutzeroberflächen intensiv, und der Zeitpunkt, zu dem die Anwendung das Erstellen von SQL-Anweisungen verbringt, ist im Vergleich zu dem Zeitpunkt, zu dem der Benutzer die Eingabe von Kriterien verbringt
