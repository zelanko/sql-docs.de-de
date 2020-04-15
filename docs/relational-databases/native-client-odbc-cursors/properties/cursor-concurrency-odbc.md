---
title: Cursor-Parallelität (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 309bfb0313adeeb0002910975c0a484461ea608c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298370"
---
# <a name="cursor-concurrency-odbc"></a>Cursorparallelität (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cursorvorgänge werden, wie Cursortypen, von den von der Anwendung festgelegten Parallelitätsoptionen beeinflusst. Parallelitätsoptionen werden mit der SQL_ATTR_CONCURRENCY-Option von [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)festgelegt. Es gibt folgende Parallelitätstypen:  
  
-   Schreibgeschützt (SQL_CONCUR_READONLY)  
  
-   Werte (SQL_CONCUR_VALUES)  
  
-   Zeilenversion (SQL_CONCUR_ROWVER)  
  
-   Sperre (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Cursoreigenschaften](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
