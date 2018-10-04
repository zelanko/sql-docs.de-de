---
title: Implizite Cursorkonvertierung (ODBC) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eebbfcefdf5c4c9e2d6ed1409e3c119f598a22d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600645"
---
# <a name="implicit-cursor-conversions-odbc"></a>Implizite Cursorkonvertierung (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Anwendungen können über einen anderer Cursortyp anfordern [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) und führen Sie dann auf eine SQL-Anweisung, die nicht von Servercursorn des angeforderten Typs unterstützt wird. Ein Aufruf von **SQLExecute** oder **SQLExecDirect** gibt SQL_SUCCESS_WITH_INFO zurück und **SQLGetDiagRec** zurückgibt:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Die Anwendung kann bestimmen, welche Art von Cursor jetzt durch den Aufruf verwendet wird **SQLGetStmtOption** auf SQL_CURSOR_TYPE gesetzt. Die Cursortypkonvertierung gilt nur für eine Anweisung. Die nächste **SQLExecDirect** oder **SQLExecute** erfolgt mit den ursprünglichen anweisungscursoreinstellungen.  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zur Programmierung von Cursor &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
