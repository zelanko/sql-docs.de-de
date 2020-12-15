---
description: Implizite Cursorkonvertierung (ODBC)
title: Implizite Cursor Konvertierungen (ODBC) | Microsoft-Dokumentation
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b07b3bc1dd045b42e3e7a56f40f63504b0cf38f2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438567"
---
# <a name="implicit-cursor-conversions-odbc"></a>Implizite Cursorkonvertierung (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Anwendungen können mithilfe von [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) einen Cursortyp anfordern und dann eine SQL-Anweisung ausführen, die von Server Cursorn des angeforderten Typs nicht unterstützt wird. Ein-Befehl von **SQLExecute** oder **SQLExecDirect** gibt SQL_SUCCESS_WITH_INFO zurück, und **SQLGetDiagRec** gibt Folgendes zurück:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Die Anwendung kann ermitteln, welcher Cursortyp jetzt verwendet wird, indem **SQLGetStmtOption** auf SQL_CURSOR_TYPE festgelegt wird. Die Cursortypkonvertierung gilt nur für eine Anweisung. Der nächste **SQLExecDirect** -oder **SQLExecute** -Vorgang wird mit den ursprünglichen Anweisungs Cursor Einstellungen durchgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Details zur Cursor Programmierung &#40;ODBC-&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
