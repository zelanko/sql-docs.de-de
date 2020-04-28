---
title: Eingebettetes SQL-Beispiel | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294171"
---
# <a name="embedded-sql-example"></a>Embedded SQL – Beispiel
Der folgende Code ist ein einfaches eingebettetes SQL-Programm, das in C geschrieben wurde. Das Programm veranschaulicht viele, aber nicht alle eingebetteten SQL-Techniken. Das Programm fordert den Benutzer auf, eine Bestellnummer einzugeben, ruft die Kundennummer, den Vertriebsmitarbeiter und den Status des Auftrags ab und zeigt die abgerufenen Informationen auf dem Bildschirm an.  
  
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
  
-   **Host Variablen** Die Host Variablen werden in einem Abschnitt deklariert, der in den Schlüsselwörtern " **BEGIN DECLARE SECTION** " und " **End DECLARE SECTION** " enthalten ist. Jedem Host Variablennamen wird ein Doppelpunkt vorangestellt (:) Wenn Sie in einer eingebetteten SQL-Anweisung angezeigt wird. Mit dem Doppelpunkt kann der vorkompilierten zwischen Host Variablen und Datenbankobjekten, z. b. Tabellen und Spalten, unterscheiden, die denselben Namen aufweisen.  
  
-   **Datentypen** Die von einem DBMS und einer Host Sprache unterstützten Datentypen können sich erheblich unterscheiden. Dies wirkt sich auf Host Variablen aus, da Sie eine duale Rolle spielen. Auf der einen Seite handelt es sich bei Host Variablen um Programmvariablen, die von Host Sprachanweisungen deklariert und manipuliert werden. Auf der anderen Seite werden Sie in eingebetteten SQL-Anweisungen verwendet, um Datenbankdaten abzurufen. Wenn kein Host Sprachtyp vorhanden ist, der einem DBMS-Datentyp entspricht, konvertiert das DBMS die Daten automatisch. Da jedem DBMS jedoch eigene Regeln und idiosyncraasen zugeordnet sind, müssen die Host Variablen Typen sorgfältig ausgewählt werden.  
  
-   **Fehlerbehandlung** Das DBMS meldet Laufzeitfehler an das Anwendungsprogramm über einen SQL-Kommunikationsbereich oder über SQLCA. Im vorangehenden Codebeispiel enthält die erste eingebettete SQL-Anweisung SQLCA. Dies weist den vorkompilierten an, die SQLCA-Struktur in das Programm einzubeziehen. Dies ist immer dann erforderlich, wenn das Programm vom DBMS zurückgegebene Fehler verarbeitet. Das-Mal, wenn... Die GoTo-Anweisung weist den vorkompilierten an, Fehler Behandlungs Code zu generieren, der bei Auftreten eines Fehlers zu einer bestimmten Bezeichnung verzweigt.  
  
-   **Singleton-Auswahl** Die Anweisung, mit der die Daten zurückgegeben werden, ist eine SELECT-Anweisung in Singleton. Das heißt, dass nur eine einzelne Daten Zeile zurückgegeben wird. Daher deklariert oder verwendet das Codebeispiel keine Cursor.
