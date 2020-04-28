---
title: Direkte Ausführung von ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], direct execution
- direct execution [ODBC]
- SQL statements [ODBC], executing
ms.assetid: dd00a535-b136-494f-913b-410838e3de7e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc5d942ac0c2af54168248d8e416ca233b2c69e6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305161"
---
# <a name="direct-execution-odbc"></a>Direkte Ausführung – ODBC
Die direkte Ausführung ist die einfachste Methode, um eine-Anweisung auszuführen. Wenn die Anweisung zur Ausführung übermittelt wird, kompiliert die Datenquelle Sie in einen Zugriffs Plan und führt dann diesen Zugriffs Plan aus.  
  
 Die direkte Ausführung wird häufig von generischen Anwendungen verwendet, die-Anweisungen zur Laufzeit erstellen und ausführen. Der folgende Code erstellt z. b. eine SQL-Anweisung und führt Sie ein einziges Mal aus:  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 Die direkte Ausführung funktioniert am besten für Anweisungen, die nur einmal ausgeführt werden. Der größte Nachteil besteht darin, dass die SQL-Anweisung bei jeder Ausführung analysiert wird. Darüber hinaus kann die Anwendung keine Informationen über das Resultset abrufen, das von der-Anweisung (sofern vorhanden) erstellt wurde, bis die-Anweisung ausgeführt wird. Dies ist möglich, wenn die-Anweisung in zwei separaten Schritten vorbereitet und ausgeführt wird.  
  
 Um eine Anweisung direkt auszuführen, führt die Anwendung die folgenden Aktionen aus:  
  
1.  Legt die Werte von Parametern fest. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
2.  Ruft **SQLExecDirect** auf und übergibt ihm eine Zeichenfolge, die die SQL-Anweisung enthält.  
  
3.  Wenn **SQLExecDirect** aufgerufen wird, führt der Treiber Folgendes aus:  
  
    -   Ändert die SQL-Anweisung so, dass die SQL-Grammatik der Datenquelle verwendet wird, ohne die Anweisung zu verwenden. Dies umfasst das Ersetzen der in Escapesequenzen [in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)beschriebenen Escapesequenzen. Die Anwendung kann das geänderte Formular einer SQL-Anweisung abrufen, indem **SQLNativeSql**aufgerufen wird. Escapesequenzen werden nicht ersetzt, wenn das SQL_ATTR_NOSCAN-Anweisungs Attribut festgelegt ist.  
  
    -   Ruft die aktuellen Parameterwerte ab und konvertiert sie nach Bedarf. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Sendet die-Anweisung und die konvertierten Parameterwerte zur Ausführung an die Datenquelle.  
  
    -   Gibt alle Fehler zurück. Hierzu gehören die Sequenzierung oder Zustandsdiagnose wie SQLSTATE 24000 (Ungültiger Cursor Zustand), syntaktische Fehler wie SQLSTATE 42000 (Syntax Fehler oder Zugriffsverletzung) sowie semantische Fehler wie SQLSTATE 42s02 (Basistabelle oder Sicht nicht gefunden).
