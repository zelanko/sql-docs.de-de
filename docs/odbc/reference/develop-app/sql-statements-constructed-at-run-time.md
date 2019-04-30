---
title: SQL-Anweisungen, die zur Laufzeit | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0573851ee93bda4aa33e8645148cf2ee66200bee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149131"
---
# <a name="sql-statements-constructed-at-run-time"></a>SQL-Anweisungen, die zur Laufzeit erstellt werden
Anwendungen, die ad-hoc-Analysen häufig ausführen werden SQL-Anweisungen zur Laufzeit erstellen. Eine Tabelle kann z. B. einen Benutzer die Auswahl von Spalten, aus denen zum Abrufen von Daten zulassen:  
  
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
  
 Eine andere Klasse von Anwendungen, die im Allgemeinen SQL-Anweisungen zur Laufzeit erstellt anwendungsentwicklungsumgebungen sind Allerdings sind die Anweisungen, die sie erstellen, in der Anwendung, die sie erstellen, in denen sie in der Regel optimiert und getestet werden können, die hartcodiert.  
  
 Anwendungen, die SQL-Anweisungen zur Laufzeit zu erstellen, können äußerst flexibel an den Benutzer bereitstellen. Wie aus dem vorherigen Beispiel, angesehen werden kann, wodurch die noch nicht über allgemeine Vorgänge wie unterstützte **, in denen** Klauseln **ORDER BY** -Klauseln oder Verknüpfungen durch, Erstellen von SQL-Anweisungen zur Laufzeit ist erheblich komplexer als Anweisungen fest zu programmieren. Darüber hinaus ist die Prüfung solcher Anwendungen problematisch, da sie eine beliebige Anzahl von SQL-Anweisungen erstellen können.  
  
 Erstellen von SQL-Anweisungen zur Laufzeit ein potenzieller Nachteil ist, dass das dauert wesentlich mehr Zeit, eine Anweisung zu erstellen, als eine hartcodierte-Anweisung verwenden. Glücklicherweise ist dies nur selten relevant. Solche Anwendungen sind tendenziell Benutzeroberfläche intensiv und die Uhrzeit, an die Anwendung, Erstellen von SQL-Anweisungen ist im Allgemeinen klein verglichen mit der Zeit, die der Benutzer Eingabe Kriterien benötigt.
