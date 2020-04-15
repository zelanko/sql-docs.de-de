---
title: Implizite Cursorkonvertierungen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ced726893b0f287db6b1fec7c8d16c6b844eea2b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298380"
---
# <a name="implicit-cursor-conversions-odbc"></a>Implizite Cursorkonvertierung (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Anwendungen können einen Cursortyp über [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) anfordern und dann eine SQL-Anweisung ausführen, die von Servercursorn des angeforderten Typs nicht unterstützt wird. Ein Aufruf von **SQLExecute** oder **SQLExecDirect** gibt SQL_SUCCESS_WITH_INFO zurück, und **SQLGetDiagRec** gibt zurück:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Die Anwendung kann bestimmen, welcher Cursortyp jetzt verwendet wird, indem **SQLGetStmtOption** auf SQL_CURSOR_TYPE festgelegt wird. Die Cursortypkonvertierung gilt nur für eine Anweisung. Die nächste **SQLExecDirect** oder **SQLExecute** erfolgt mit den ursprünglichen Anweisungscursoreinstellungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur Cursorprogrammierung &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
