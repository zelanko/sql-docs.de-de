---
title: Freigeben eines Anweisungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d7a1e93d222e2b87058bc878f7eca85313b4108
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85018343"
---
# <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles
  Es ist effizienter, Anweisungshandles wieder zu verwenden, als sie zu löschen und neu zuzuordnen. Vor dem Ausführen einer neuen SQL-Anweisung für ein Anweisungshandle sollten Anwendungen überprüfen, ob die aktuellen Anweisungseinstellungen korrekt sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im Allgemeinen müssen die Bindung von Parametern und Resultsets für die alte SQL-Anweisung aufgehoben werden, indem [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) mit den Optionen SQL_RESET_PARAMS und SQL_UNBIND aufgerufen und dann für die neue SQL-Anweisung erneut gebunden wird.  
  
 Wenn die Anwendung die Verwendung der-Anweisung abgeschlossen hat, wird [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) aufgerufen, um die-Anweisung freizugeben. Beachten Sie, dass **SQLDisconnect** automatisch alle-Anweisungen für eine Verbindung freigibt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](executing-queries-odbc.md)  
  
  
