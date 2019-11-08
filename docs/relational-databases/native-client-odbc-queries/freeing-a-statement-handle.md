---
title: Freigeben eines Anweisungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 405e5fd13298892a2c6226015f575ef9b8373148
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73779421"
---
# <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Es ist effizienter, Anweisungshandles wieder zu verwenden, als sie zu löschen und neu zuzuordnen. Vor dem Ausführen einer neuen SQL-Anweisung für ein Anweisungshandle sollten Anwendungen überprüfen, ob die aktuellen Anweisungseinstellungen korrekt sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im Allgemeinen müssen die Bindung von Parametern und Resultsets für die alte SQL-Anweisung aufgehoben werden, indem [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) mit den Optionen SQL_RESET_PARAMS und SQL_UNBIND aufgerufen und dann für die neue SQL-Anweisung erneut gebunden wird.  
  
 Wenn die Anwendung die Verwendung der-Anweisung abgeschlossen hat, wird [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) aufgerufen, um die-Anweisung freizugeben. Beachten Sie, dass **SQLDisconnect** automatisch alle-Anweisungen für eine Verbindung freigibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von &#40;Abfragen (ODBC)&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
