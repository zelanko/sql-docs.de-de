---
title: Freigeben eines Anweisungshandles | Microsoft Docs
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
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7da2fec15303e9c2d50fb7aa2e6dc40266a380d9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148824"
---
# <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles
  Es ist effizienter, Anweisungshandles wieder zu verwenden, als sie zu löschen und neu zuzuordnen. Vor dem Ausführen einer neuen SQL-Anweisung für ein Anweisungshandle sollten Anwendungen überprüfen, ob die aktuellen Anweisungseinstellungen korrekt sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im allgemeinen Parameter und Resultsets legt fest, für die alte SQL-Anweisung durch den Aufruf ungebunden sein muss [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) mit dem SQL_RESET_PARAMS und SQL_UNBIND-Optionen, und klicken Sie dann erneut für die neue SQL-Anweisung gebunden.  
  
 Wenn die Anwendung mit der Anweisung abgeschlossen ist, ruft er [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) um die Anweisung freizugeben. Beachten Sie, dass **SQLDisconnect** alle Anweisungen für eine Verbindung automatisch freigibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  