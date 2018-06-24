---
title: Implizite Cursorkonvertierung (ODBC) | Microsoft Docs
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
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b1f1880ea464949bd962bab002d1f1129261463c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058277"
---
# <a name="implicit-cursor-conversions-odbc"></a>Implizite Cursorkonvertierung (ODBC)
  Anwendungen können über einen Cursortyp anfordern [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) und führen Sie dann eine SQL-Anweisung, die von Servercursorn des angeforderten Typs nicht unterstützt wird. Ein Aufruf von **SQLExecute** oder **SQLExecDirect** SQL_SUCCESS_WITH_INFO zurückgegeben und **SQLGetDiagRec** zurückgibt:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Kann die Anwendung bestimmen, welche Art von Cursor jetzt durch den Aufruf verwendet wird **SQLGetStmtOption** auf SQL_CURSOR_TYPE gesetzt. Die Cursortypkonvertierung gilt nur für eine Anweisung. Das nächste **SQLExecDirect** oder **SQLExecute** erfolgt mithilfe der ursprünglichen anweisungscursoreinstellungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Details zum Programmieren von Cursorn &#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  