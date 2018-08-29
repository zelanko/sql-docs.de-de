---
title: Freigeben eines Anweisungshandles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a82c5dca156d7f3c10f7854d2ea147890921ae01
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102707"
---
# <a name="freeing-a-statement-handle"></a>Freigeben eines Anweisungshandles
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Es ist effizienter, Anweisungshandles wieder zu verwenden, als sie zu löschen und neu zuzuordnen. Vor dem Ausführen einer neuen SQL-Anweisung für ein Anweisungshandle sollten Anwendungen überprüfen, ob die aktuellen Anweisungseinstellungen korrekt sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im allgemeinen Parameter und Resultsets legt fest, für die alte SQL-Anweisung aufgehoben werden muss, durch den Aufruf [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) mit dem SQL_RESET_PARAMS und SQL_UNBIND "Optionen", und klicken Sie dann die Bindung erneut für die neue SQL-Anweisung.  
  
 Wenn die Anwendung mithilfe der Anweisung abgeschlossen ist, ruft er [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) um die Anweisung freizugeben. Beachten Sie, dass **SQLDisconnect** alle Anweisungen für eine Verbindung automatisch freigibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
