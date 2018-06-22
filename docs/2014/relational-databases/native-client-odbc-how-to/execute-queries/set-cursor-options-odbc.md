---
title: Festlegen von Cursoroptionen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d4694337517f51c08273a988e105ae49fa9bb15a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058052"
---
# <a name="set-cursor-options-odbc"></a>Festlegen von Cursoroptionen (ODBC)
  Zum Festlegen von Cursoroptionen rufen [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) festlegen oder [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) um die Anweisungsoptionen abzurufen, das Cursorverhalten gesteuert.  
  
|*Attribut*|Gibt an|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|Cursortyp, der einen Vorwärtscursor, einen statischen, dynamischen oder keyset-gesteuerten Cursor bezeichnen kann|  
|SQL_ATTR_CONCURRENCY|Option zur Steuerung der gleichzeitigen Ausführung, die Schreibschutz, Sperren, vollständige Parallelität mit Timestamps oder vollständige Parallelität mit Werten angeben kann|  
|SQL_ATTR_ROW_ARRAY_SIZE|Anzahl der Zeilen, die mit jedem Abrufvorgang abgerufen werden|  
|SQL_ATTR_CURSOR_SENSITIVITY|Cursor, der Cursorupdates, die von anderen Verbindungen an Cursorzeilen vorgenommen wurden, anzeigt oder nicht anzeigt|  
|SQL_ATTR_CURSOR_SCROLLABLE|Cursor, mit denen sowohl ein Vorwärts- als auch ein Rückwärtsbildlauf ausgeführt werden kann|  
  
 Bei Verwendung der Standardwerte dieser Attribute (forward-only, read-only, Rowsetgröße von 1) werden keine Servercursor verwendet. Die Verwendung von Servercursorn setzt voraus, dass mindestens eines dieser Attribute auf einen anderen Wert als den Standardwert festgelegt wird und dass es sich bei der auszuführenden Anweisungen um eine einzelne SELECT-Anweisung oder eine gespeicherte Prozedur handelt, die eine einzelne SELECT-Anweisung enthält. Beim Einsatz von Servercursorn können in SELECT-Anweisungen keine Klauseln angegeben werden, die von den Servercursorn nicht unterstützt werden: COMPUTE, COMPUTE BY, FOR BROWSE und INTO.  
  
 Sie können den Typ des Cursors entweder von SQL_ATTR_CURSOR_TYPE und SQL_ATTR_CONCURRENCY oder SQL_ATTR_CURSOR_SENSITIVITY und SQL_ATTR_CURSOR_SCROLLABLE steuern. Sie sollten die zwei Methoden zur Angabe des Cursorverhaltens nicht kombinieren.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden ein Anweisungshandle zugeordnet, ein dynamischer Cursortyp mit vollständiger Parallelität mit Zeilenversionsverwaltung festgelegt und anschließend eine SELECT-Anweisung ausgeführt.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden ein Anweisungshandle zugeordnet, ein bildlauffähiger Sensitivcursor festgelegt und anschließend eine SELECT-Anweisung ausgeführt.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen: Themen zur Vorgehensweise &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  