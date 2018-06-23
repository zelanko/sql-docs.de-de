---
title: Verwenden von Cursorn (ODBC) | Microsoft Docs
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
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 240910c0c6be92537a15a0560ebde1236a3a6593
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158969"
---
# <a name="using-cursors-odbc"></a>Verwenden von Cursorn (ODBC)
  ODBC unterstützt ein Cursormodell, das Folgendes zulässt:  
  
-   Mehrere Typen von Cursorn  
  
-   Das Durchführen eines Bildlaufs und Positionieren innerhalb eines Cursors  
  
-   Mehrere Parallelitätsoptionen  
  
-   Positionierte Updates.  
  
 ODBC-Anwendungen deklarieren und öffnen Cursor oder verwenden cursorspezifische [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen nur selten. ODBC öffnet automatisch einen Cursor für jedes Resultset, das von einer SQL-Anweisung zurückgegeben wird. Die Charakteristika der Cursor werden von Anweisungsattribute festlegen mit gesteuert [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) vor der SQL-Anweisung ausgeführt wird. Die ODBC-API-Funktionen zum Verarbeiten der Resultsets unterstützen sämtliche Cursorfunktionalitäten einschließlich Abrufen, Durchführen eines Bildlaufs und positionierte Updates.  
  
 Dies ist ein Vergleich der Funktionsweise von Cursorn in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skripts und ODBC-Anwendungen.  
  
|Aktion|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|Definieren des Cursorverhaltens|Angeben durch DECLARE CURSOR-Parameter|Festlegen der Cursorattribute mithilfe [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)|  
|Öffnen eines Cursors|DECLARE CURSOR OPEN *Cursorname*|**SQLExecDirect** oder **SQLExecute**|  
|Abrufen von Zeilen|FETCH|**SQLFetch** oder [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)|  
|Positioniertes Update|WHERE CURRENT OF-Klausel mit UPDATE oder DELETE|**SQLSetPos**|  
|Schließen eines Cursors|Schließen *Cursor_name* DEALLOCATE|[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)|  
  
 Die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implementierten Servercursor unterstützen die Funktionalität des ODBC-Cursormodells. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Treiber verwendet Servercursor, um die Cursorfunktionalität der ODBC-API zu unterstützen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Implementieren von Cursorn](implementation/how-cursors-are-implemented.md)  
  
-   [Cursortypen](cursor-types.md)  
  
-   [Cursorverhalten](cursor-behaviors.md)  
  
-   [Cursoreigenschaften](properties/cursor-properties.md)  
  
-   [Details zum Programmieren von Cursorn &#40;ODBC&#41;](programming/cursor-programming-details-odbc.md)  
  
-   [Scrollen und Fetchen von Zeilen](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Positionierte Updates &#40;ODBC&#41;](positioned-updates-odbc.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [CLOSE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/close-transact-sql)   
 [Cursor](../../relational-databases/cursors.md)   
 [DEALLOCATE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/deallocate-transact-sql)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql)   
 [OPEN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/open-transact-sql)  
  
  
