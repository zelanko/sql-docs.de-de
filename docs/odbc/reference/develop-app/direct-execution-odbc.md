---
title: Direkte Ausführung ODBC | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305161"
---
# <a name="direct-execution-odbc"></a>Direkte Ausführung – ODBC
Die direkte Ausführung ist die einfachste Möglichkeit, eine Anweisung auszuführen. Wenn die Anweisung zur Ausführung übermittelt wird, kompiliert die Datenquelle sie in einen Zugriffsplan und führt diesen Zugriffsplan dann aus.  
  
 Die direkte Ausführung wird häufig von generischen Anwendungen verwendet, die Anweisungen zur Laufzeit erstellen und ausführen. Der folgende Code erstellt z. B. eine SQL-Anweisung und führt sie ein einziges Mal aus:  
  
```  
SQLCHAR *SQLStatement;  
  
// Build an SQL statement.  
BuildStatement(SQLStatement);  
  
// Execute the statement.  
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);  
```  
  
 Die direkte Ausführung eignet sich am besten für Anweisungen, die ein einziges Mal ausgeführt werden. Sein Hauptnachteil besteht darin, dass die SQL-Anweisung jedes Mal analysiert wird, wenn sie ausgeführt wird. Darüber hinaus kann die Anwendung erst nach der Ausführung der Anweisung Informationen über das von der Anweisung erstellte Resultset (falls vorhanden) abrufen. Dies ist möglich, wenn die Anweisung in zwei separaten Schritten vorbereitet und ausgeführt wird.  
  
 Um eine Anweisung direkt auszuführen, führt die Anwendung die folgenden Aktionen aus:  
  
1.  Legt die Werte aller Parameter fest. Weitere Informationen finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
2.  Ruft **SQLExecDirect** auf und übergibt ihm eine Zeichenfolge, die die SQL-Anweisung enthält.  
  
3.  Wenn **SQLExecDirect** aufgerufen wird, lautet der Treiber:  
  
    -   Ändert die SQL-Anweisung, um die SQL-Grammatik der Datenquelle zu verwenden, ohne die Anweisung zu analysieren. Dazu gehört das Ersetzen der Escapesequenzen, die in [Escape Sequences in ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)beschrieben werden. Die Anwendung kann die geänderte Form einer SQL-Anweisung abrufen, indem sie **SQLNativeSql aufruft.** Escapesequenzen werden nicht ersetzt, wenn das SQL_ATTR_NOSCAN-Anweisungsattribut festgelegt ist.  
  
    -   Ruft die aktuellen Parameterwerte ab und konvertiert sie bei Bedarf. Weitere Informationen finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md)weiter unten in diesem Abschnitt.  
  
    -   Sendet die Anweisung und konvertierte Parameterwerte zur Ausführung an die Datenquelle.  
  
    -   Gibt alle Fehler zurück. Dazu gehören Sequenzierung oder Zustandsdiagnose wie SQLSTATE 24000 (Ungültiger Cursorstatus), syntaktische Fehler wie SQLSTATE 42000 (Syntaxfehler oder Zugriffsverletzung) und semantische Fehler wie SQLSTATE 42S02 (Basistabelle oder Ansicht nicht gefunden).
