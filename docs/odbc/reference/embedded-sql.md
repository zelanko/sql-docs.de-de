---
description: Embedded SQL
title: Eingebettetes SQL | Microsoft-Dokumentation
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
ms.openlocfilehash: 7b52c5a87d1df03460a833a27fcb5523b80cd1f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487413"
---
# <a name="embedded-sql"></a>Embedded SQL
Die erste Methode zum Senden von SQL-Anweisungen an das DBMS ist eingebettetes SQL. Da SQL keine Variablen und Anweisungen zur Ablauf Steuerung verwendet, wird es häufig als Daten Bank Untersprache verwendet, die zu einem in einer herkömmlichen Programmiersprache geschriebenen Programm, wie z. b. C oder COBOL, hinzugefügt werden kann. Dies ist eine zentrale Idee für eingebettetes SQL: Platzieren von SQL-Anweisungen in einem Programm, das in einer Host Programmiersprache geschrieben ist. Zum Einbetten von SQL-Anweisungen in eine Host Sprache werden die folgenden Techniken verwendet:  
  
-   Eingebettete SQL-Anweisungen werden von einem speziellen SQL-präcompiler verarbeitet. Alle SQL-Anweisungen beginnen mit einem Einführungs und enden mit einem Abschluss Zeichen, das beide die SQL-Anweisung für den Precompiler markieren. Der Introduction und das Abschluss Zeichen unterscheiden sich von der Host Sprache. Beispielsweise ist der Introduction "Exec SQL" in C und "&SQL (" in Mumps, und das Abschluss Zeichen ist ein Semikolon (;) in C und eine schließende Klammer in Mumps.  
  
-   Variablen aus dem Anwendungsprogramm, so genannte Host Variablen, können in eingebetteten SQL-Anweisungen immer dann verwendet werden, wenn Konstanten zulässig sind. Diese können für Eingaben verwendet werden, um eine SQL-Anweisung an eine bestimmte Situation und die Ausgabe anzupassen, um die Ergebnisse einer Abfrage zu erhalten.  
  
-   Abfragen, die eine einzelne Daten Zeile zurückgeben, werden mit einer SELECT-Anweisung in Singleton behandelt. Diese Anweisung gibt sowohl die Abfrage als auch die Host Variablen an, in die Daten zurückgegeben werden sollen.  
  
-   Abfragen, die mehrere Daten Zeilen zurückgeben, werden mit Cursorn verarbeitet. Ein Cursor verfolgt die aktuelle Zeile in einem Resultset. Die DECLARE CURSOR-Anweisung definiert die Abfrage, die Open-Anweisung beginnt mit der Verarbeitung der Abfrage, die FETCH-Anweisung ruft aufeinander folgende Daten Zeilen ab, und die Close-Anweisung beendet die Verarbeitung der Abfrage.  
  
-   Während ein Cursor geöffnet ist, können positionierte UPDATE-und positionierte DELETE-Anweisungen verwendet werden, um die Zeile zu aktualisieren oder zu löschen, die derzeit vom Cursor ausgewählt wird.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Embedded SQL – Beispiel](../../odbc/reference/embedded-sql-example.md)  
  
-   [Kompilieren eines eingebetteten SQL-Programms](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [Statische SQL-Anweisungen](../../odbc/reference/static-sql.md)  
  
-   [Dynamischer SQL-Code](../../odbc/reference/dynamic-sql.md)
