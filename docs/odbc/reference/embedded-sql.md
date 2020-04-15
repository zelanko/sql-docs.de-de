---
title: Eingebettete SQL | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ad6fd2753d026f026d72a7aa8f68d5d48ce03cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306673"
---
# <a name="embedded-sql"></a>Embedded SQL
Die erste Technik zum Senden von SQL-Anweisungen an das DBMS ist Embedded SQL. Da SQL keine Variablen und "Control-of-Flow"-Anweisungen verwendet, wird es häufig als Datenbankuntersprache verwendet, die einem Programm hinzugefügt werden kann, das in einer herkömmlichen Programmiersprache wie C oder COBOL geschrieben ist. Dies ist eine zentrale Idee von Embedded SQL: Platzieren von SQL-Anweisungen in einem Programm, das in einer Host-Programmiersprache geschrieben ist. Kurz gesagt, die folgenden Techniken werden verwendet, um SQL-Anweisungen in eine Hostsprache einzubetten:  
  
-   Eingebettete SQL-Anweisungen werden von einem speziellen SQL-Vorcompiler verarbeitet. Alle SQL-Anweisungen beginnen mit einem Introducer und enden mit einem Terminator, die beide die SQL-Anweisung für den Vorkompilierer kennzeichnen. Der Einführungs- und Terminator wird je nach Hostsprache variiert. Der Einfrichter ist z. B. "EXEC SQL" in C und "&SQL(" in MUMPS, und der Terminator ist ein Semikolon (;) in C und einer rechten Klammer in MUMPS.  
  
-   Variablen aus dem Anwendungsprogramm, so genannte Hostvariablen, können in eingebetteten SQL-Anweisungen überall dort verwendet werden, wo Konstanten zulässig sind. Diese können bei der Eingabe verwendet werden, um eine SQL-Anweisung an eine bestimmte Situation anzupassen, und für die Ausgabe, um die Ergebnisse einer Abfrage zu erhalten.  
  
-   Abfragen, die eine einzelne Datenzeile zurückgeben, werden mit einer singleton SELECT-Anweisung behandelt. Diese Anweisung gibt sowohl die Abfrage als auch die Hostvariablen an, in denen Daten zurückgegeben werden sollen.  
  
-   Abfragen, die mehrere Datenzeilen zurückgeben, werden mit Cursorn behandelt. Ein Cursor verfolgt die aktuelle Zeile innerhalb eines Resultsets. Die DECLARE CURSOR-Anweisung definiert die Abfrage, die OPEN-Anweisung beginnt die Abfrageverarbeitung, die FETCH-Anweisung ruft aufeinanderfolgende Datenzeilen ab, und die CLOSE-Anweisung beendet die Abfrageverarbeitung.  
  
-   Während ein Cursor geöffnet ist, können positionierte Aktualisierungs- und Positionierte Löschanweisungen verwendet werden, um die aktuell vom Cursor ausgewählte Zeile zu aktualisieren oder zu löschen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Embedded SQL – Beispiel](../../odbc/reference/embedded-sql-example.md)  
  
-   [Kompilieren eines eingebetteten SQL-Programms](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [Statische SQL-Anweisungen](../../odbc/reference/static-sql.md)  
  
-   [Dynamische SQL-Anweisungen](../../odbc/reference/dynamic-sql.md)
