---
title: Eingebettetes SQL-Beispiel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39ec504c423817c6a3e11bc954555b201b8b09c6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294171"
---
# <a name="embedded-sql-example"></a>Embedded SQL – Beispiel
Der folgende Code ist ein einfaches eingebettetes SQL-Programm, geschrieben in C. Das Programm veranschaulicht viele, aber nicht alle eingebetteten SQL-Techniken. Die Anwendung fordert den Benutzer zur Eingabe einer Auftragsnummer auf, ruft die Debitorennummer, den Verkäufer und den Status des Auftrags ab und zeigt die abgerufenen Informationen auf dem Bildschirm an.  
  
```cpp  
int main() {  
   EXEC SQL INCLUDE SQLCA;  
   EXEC SQL BEGIN DECLARE SECTION;  
      int OrderID;         /* Employee ID (from user)         */  
      int CustID;            /* Retrieved customer ID         */  
      char SalesPerson[10]   /* Retrieved salesperson name      */  
      char Status[6]         /* Retrieved order status        */  
   EXEC SQL END DECLARE SECTION;  
  
   /* Set up error processing */  
   EXEC SQL WHENEVER SQLERROR GOTO query_error;  
   EXEC SQL WHENEVER NOT FOUND GOTO bad_number;  
  
   /* Prompt the user for order number */  
   printf ("Enter order number: ");  
   scanf_s("%d", &OrderID);  
  
   /* Execute the SQL query */  
   EXEC SQL SELECT CustID, SalesPerson, Status  
      FROM Orders  
      WHERE OrderID = :OrderID  
      INTO :CustID, :SalesPerson, :Status;  
  
   /* Display the results */  
   printf ("Customer number:  %d\n", CustID);  
   printf ("Salesperson: %s\n", SalesPerson);  
   printf ("Status: %s\n", Status);  
   exit();  
  
query_error:  
   printf ("SQL error: %ld\n", sqlca->sqlcode);  
   exit();  
  
bad_number:  
   printf ("Invalid order number.\n");  
   exit();  
}  
```  
  
 Beachten Sie Folgendes zu diesem Programm:  
  
-   **Hostvariablen** Die Hostvariablen werden in einem Abschnitt **deklariert,** der von den Schlüsselwörtern BEGIN DECLARE SECTION und **END DECLARE SECTION** eingeschlossen wird. Jedem Hostvariablennamen wird ein Doppelpunkt vorangestellt (:) wenn sie in einer eingebetteten SQL-Anweisung angezeigt wird. Der Doppelpunkt ermöglicht es dem Vorkompilatierer, zwischen Hostvariablen und Datenbankobjekten wie Tabellen und Spalten mit demselben Namen zu unterscheiden.  
  
-   **Datentypen** Die von einem DBMS und einer Hostsprache unterstützten Datentypen können sehr unterschiedlich sein. Dies wirkt sich auf Hostvariablen aus, da sie eine doppelte Rolle spielen. Auf der einen Seite sind Hostvariablen Programmvariablen, die durch Host-Sprachanweisungen deklariert und manipuliert werden. Andererseits werden sie in eingebetteten SQL-Anweisungen zum Abrufen von Datenbankdaten verwendet. Wenn kein Hostsprachentyp vorhanden ist, der einem DBMS-Datentyp entspricht, konvertiert das DBMS die Daten automatisch. Da jedoch jedes DBMS über eigene Regeln und Eigenheiten verfügt, die mit dem Konvertierungsprozess verknüpft sind, müssen die Hostvariablentypen sorgfältig ausgewählt werden.  
  
-   **Fehlerbehandlung** Das DBMS meldet Laufzeitfehler über einen SQL Communications Area oder SQLCA an das Anwendungsprogramm. Im vorherigen Codebeispiel ist die erste eingebettete SQL-Anweisung INCLUDE SQLCA. Dadurch wird der Vorkompilierer angewiesen, die SQLCA-Struktur in das Programm aufzunehmen. Dies ist immer dann erforderlich, wenn das Programm vom DBMS zurückgegebene Fehler verarbeitet. Die WHENEVER... Die GOTO-Anweisung weist den Vorkompilen an, Fehlerbehandlungscode zu generieren, der zu einer bestimmten Bezeichnung verzweigt, wenn ein Fehler auftritt.  
  
-   **Singleton SELECT** Die Anweisung, die zum Zurückgeben der Daten verwendet wird, ist eine singleton SELECT-Anweisung; Das heißt, es gibt nur eine einzelne Datenzeile zurück. Daher deklariert oder verwendet das Codebeispiel keine Cursor.
