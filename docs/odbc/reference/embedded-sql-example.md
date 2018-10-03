---
title: Eingebettete SQL-Beispiel | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eef8c87a152795d4756d05ba8a279a0d12cbc38c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750480"
---
# <a name="embedded-sql-example"></a>Embedded SQL – Beispiel
Der folgende Code ist eine einfache eingebettete SQL-Programms, in c geschriebenen Das Programm veranschaulicht viele, aber nicht alle, die eingebettete SQL-Techniken. Das Programm fordert den Benutzer für eine Bestellnummer, ruft die Anzahl der Kunden, Vertriebsmitarbeiter und Status des Auftrags ab und zeigt die abgerufene Informationen auf dem Bildschirm.  
  
```  
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
  
-   **Hosten von Variablen** die Hostvariablen werden in einem Abschnitt eingeschlossene deklariert die **Abschnitt beginnen, deklarieren Sie** und **ENDABSCHNITT deklarieren** Schlüsselwörter. Jeder Variablenname Host wird durch einen Doppelpunkt (:).) vorangestellt, wenn es in eine eingebettete SQL­Anweisung angezeigt wird. Der Doppelpunkt ermöglicht die vorkompilierten zwischen Hostvariablen und Datenbankobjekte, z. B. Tabellen und Spalten, mit dem gleichen Namen zu unterscheiden.  
  
-   **Datentypen** der von einem DBMS und einer Hostsprache unterstützten Datentypen können sehr unterschiedlich sein. Dies wirkt sich auf Hostvariablen aus, da sie eine Doppelrolle spielen. Einerseits sind Hostvariablen Programmvariablen, deklariert und vom Host-sprachanweisungen bearbeitet. Auf der anderen Seite werden sie in eingebetteten SQL-Anweisungen verwendet, um Daten abzurufen. Ist keine Host-Sprachtyps an, die einen DBMS-Datentyp entspricht, konvertiert das DBMS automatisch die Daten. Aber da jede DBMS einen eigenen Regeln und eigenheiten des Konvertierungsvorgangs zugeordnet hat, müssen die Host-Variablentypen sorgfältig ausgewählt werden.  
  
-   **Fehlerbehandlung** der DBMS-Berichte zu Laufzeitfehlern an das Programm Anwendungen über eine SQL Communications Area oder SQLCA. Im vorherigen Codebeispiel ist die erste embedded SQL-Anweisung SQLCA enthalten. Dadurch wird die vorkompilierten SQLCA-Struktur in das Programm eingeschlossen werden sollen. Dies ist erforderlich, wenn die Anwendung von DBMS zurückgegebenen Fehler verarbeitet werden. Die WHENEVER... GOTO-Anweisung teilt dem vorkompilierten Fehlerbehandlungscode, der Verzweigungen einer bestimmten Bezeichnung, wenn ein Fehler auftritt, generiert.  
  
-   **Singleton-SELECT** die Anweisung die Daten zurückgeben, wird eine Singleton-SELECT-Anweisung, also gibt, sondern nur eine einzelne Zeile mit Daten. Aus diesem Grund im Codebeispiel nicht deklariert oder Cursor.
