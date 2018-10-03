---
title: Direkte Ausführung ODBC | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73c061718dc326e43f72be369a28ad12726a3cab
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603048"
---
# <a name="direct-execution-odbc"></a>Direkte Ausführung – ODBC
Direkte Ausführung ist die einfachste Möglichkeit zum Ausführen einer Anweisung. Wenn die Anweisung zur Ausführung übermittelt wird, wird die Datenquelle kompiliert sie zu einem Zugriffsplan und führt dann diesen Zugriffsplan.  
  
 Direkte Ausführung wird häufig von generischen Anwendungen verwendet, das Erstellen und Ausführen von Anweisungen zur Laufzeit. Der folgende Code wird z. B. eine SQL-Anweisung erstellt und ein einziges Mal ausgeführt:  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 Direkte Ausführung funktioniert am besten für Anweisungen, die ein einziges Mal ausgeführt wird. Die wichtigsten Nachteil besteht darin, dass die SQL-Anweisung analysiert wird, jedes Mal, wenn er ausgeführt wird. Die Anwendung kann nicht darüber hinaus Informationen über das Resultset, die von der Anweisung erstellt (sofern vorhanden) erst nach der Ausführung der Anweisung abrufen; Dies ist möglich, wenn die Anweisung vorbereitet und in zwei separaten Schritte ausgeführt werden.  
  
 Zum Ausführen einer Anweisung direkt die Anwendung die folgenden Aktionen ausgeführt:  
  
1.  Legt die Werte aller Parameter. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
2.  Aufrufe **SQLExecDirect** und übergibt sie eine Zeichenfolge, die die SQL-Anweisung enthält.  
  
3.  Wenn **SQLExecDirect** aufgerufen wird, wird den Treiber:  
  
    -   Ändert die SQL-Anweisung, um SQL-Grammatik für die Datenquelle zu verwenden, ohne die Anweisung analysieren; Dies schließt das Ersetzen der Escape-Sequenzen, die in beschriebenen [Escapesequenzen in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md). Kann die Anwendung eine SQL-Anweisung geänderte Form durch den Aufruf abrufen **SQLNativeSql**. Escapesequenzen werden nicht ersetzt werden, wenn das SQL_ATTR_NOSCAN-Anweisungsattribut festgelegt ist.  
  
    -   Ruft die aktuellen Parameterwerte aus, und nach Bedarf konvertiert. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Sendet die Anweisung und die konvertierten Parameterwerte an die Datenquelle für die Ausführung an.  
  
    -   Gibt alle Fehler zurück. Dazu gehören Sequenzierung oder Status-Diagnose wie z. B. SQLSTATE 24000 (Ungültiger Cursorstatus), syntaktische Fehler wie z. B. SQLSTATE 42000 (Syntaxfehler oder zugriffsverletzung) und semantische Fehler, z. B. SQLSTATE 42S02 (Basis-Tabelle oder Sicht wurde nicht gefunden).
