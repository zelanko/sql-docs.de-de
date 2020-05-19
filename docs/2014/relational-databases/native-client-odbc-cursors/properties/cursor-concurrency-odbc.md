---
title: Cursor Parallelität (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7139ace2498ef2eeddb173950281ac4cf493efad
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705594"
---
# <a name="cursor-concurrency-odbc"></a>Cursorparallelität (ODBC)
  Cursorvorgänge werden, wie Cursortypen, von den von der Anwendung festgelegten Parallelitätsoptionen beeinflusst. Parallelitäts Optionen werden mithilfe der Option SQL_ATTR_CONCURRENCY von [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)festgelegt. Es gibt folgende Parallelitätstypen:  
  
-   Schreibgeschützt (SQL_CONCUR_READONLY)  
  
-   Werte (SQL_CONCUR_VALUES)  
  
-   Zeilenversion (SQL_CONCUR_ROWVER)  
  
-   Sperre (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursoreigenschaften](cursor-properties.md)  
  
  
