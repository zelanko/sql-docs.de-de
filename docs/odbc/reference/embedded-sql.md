---
title: Embedded SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47936b5c085514fca4ecc1c81057ef78a19f05c5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62628463"
---
# <a name="embedded-sql"></a>Embedded SQL
Das erste Verfahren für das Senden von SQL-Anweisungen für das DBMS eingebettet ist SQL. Da SQL keine Variablen und die ablaufsteuerung von Anweisungen verwendet werden, wird er häufig als eine untergeordnete Datenbanksprache verwendet, die ein in einer herkömmlichen Programmiersprache, z. B. C oder COBOL geschriebenes Programm hinzugefügt werden können. Dies ist eine zentralen Überblick über die eingebettete SQL: Platzieren von SQL-Anweisungen in einem Programm auf einem Host Programmiersprache geschrieben. Kurz gesagt, werden die folgenden Verfahren zum Einbetten von SQL-Anweisungen in einer Hostsprache verwendet:  
  
-   Eingebettete SQL-Anweisungen werden von einem speziellen SQL vorkompilierten verarbeitet. Alle SQL-Anweisungen mit einer Introducer beginnen und enden mit einem Abschlusszeichen, mit die SQL-Anweisung für den vorkompilierten flag. Die Introducer und Abschlusszeichen variieren je nach der Hostsprache. Die Introducer ist z. B. "EXEC-SQL" in C# und "& SQL (" in MUMPS, und das Abschlusszeichen ist ein Semikolon (;) in C und eine schließende Klammer in MUMPS.  
  
-   Variablen aus der Anwendungsprogramm mit dem Namen von Hostvariablen können in eingebettete SQL-Anweisungen verwendet werden, wo Konstanten zulässig sind. Diese können bei der Eingabe verwendet werden, um eine SQL-Anweisung, um eine bestimmte Situation und bei der Ausgabe auf die Ergebnisse einer Abfrage anzupassen.  
  
-   Abfragen, die eine einzelne Zeile mit Daten zurückgeben, werden mit einer Singleton-SELECT-Anweisung behandelt; Diese Anweisung gibt an, die Abfrage und die Hostvariablen in den Daten zurückgegeben werden sollen.  
  
-   Abfragen, die mehrere Datenzeilen zurückgeben werden mit Cursorn vom Typ behandelt. Ein Cursor verfolgt des die aktuelle Zeile in einem Resultset. DECLARE CURSOR-Anweisung definiert die Abfrage, die OPEN-Anweisung beginnt die Verarbeitung von Abfragen, die FETCH-Anweisung ruft aufeinander folgenden Zeilen mit Daten und die CLOSE-Anweisung beendet die Verarbeitung von Abfragen.  
  
-   Während ein Cursor geöffnet ist, können das Aktualisieren oder löschen die Zeile, die aktuell vom Cursor ausgewählt positionierten Aktualisierung und positionierte Delete-Anweisungen verwendet werden.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Embedded SQL – Beispiel](../../odbc/reference/embedded-sql-example.md)  
  
-   [Kompilieren eines eingebetteten SQL-Programms](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [Statische SQL-Anweisungen](../../odbc/reference/static-sql.md)  
  
-   [Dynamisches SQL](../../odbc/reference/dynamic-sql.md)
