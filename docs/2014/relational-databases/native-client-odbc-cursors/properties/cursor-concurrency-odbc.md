---
title: Cursorparallelität (ODBC) | Microsoft Docs
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
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: da4b99f4ea20ce7c8540f45a4324321413b18183
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149665"
---
# <a name="cursor-concurrency-odbc"></a>Cursorparallelität (ODBC)
  Cursorvorgänge werden, wie Cursortypen, von den von der Anwendung festgelegten Parallelitätsoptionen beeinflusst. Parallelitätsoptionen werden festgelegt, mit der SQL_ATTR_CONCURRENCY-Option von [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md). Es gibt folgende Parallelitätstypen:  
  
-   Schreibgeschützt (SQL_CONCUR_READONLY)  
  
-   Werte (SQL_CONCUR_VALUES)  
  
-   Zeilenversion (SQL_CONCUR_ROWVER)  
  
-   Sperre (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Siehe auch  
 [Cursoreigenschaften](cursor-properties.md)  
  
  