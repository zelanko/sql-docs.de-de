---
title: Befreien eines Anweisungshandles | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7e954773f85afc434d1e5bd18f7ffb76e28a1438
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297894"
---
# <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Es ist effizienter, Anweisungshandles wieder zu verwenden, als sie zu löschen und neu zuzuordnen. Vor dem Ausführen einer neuen SQL-Anweisung für ein Anweisungshandle sollten Anwendungen überprüfen, ob die aktuellen Anweisungseinstellungen korrekt sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im Allgemeinen müssen Parameter und Resultsets für die alte SQL-Anweisung durch Aufrufen von [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) mit den Optionen SQL_RESET_PARAMS und SQL_UNBIND und dann für die neue SQL-Anweisung neu gebunden werden.  
  
 Wenn die Anwendung die Anweisung verwendet hat, ruft sie [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) auf, um die Anweisung freizugeben. Beachten Sie, dass **SQLDisconnect** automatisch alle Anweisungen für eine Verbindung freigibt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen von Abfragen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
