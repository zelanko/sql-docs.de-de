---
title: SQLFreeStmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b985db3cb58a7029a3b5ec489d2e23b0c1292919
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73786731"
---
# <a name="sqlfreestmt"></a>'SQLFreeStmt'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Meist   
      **SQLFreeStmt** wird in ODBC 3,0 und höher nicht empfohlen. Wenn die Anwendung jedoch die-Anweisung wieder verwenden muss, sollte **SQLFreeStmt** weiterhin mit den Optionen **SQL_RESET_PARAMS** und **SQL_UNBIND** ) verwendet werden. Sie können auch [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)und [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) verwenden, um die Funktion von **SQLFreeStmt** zu ersetzen oder zu duplizieren. Sie sollten Sie stattdessen verwenden.  
  
 Im Allgemeinen ist es effizienter,-Anweisungen wiederzuverwenden, als Sie zu löschen und neue zuzuweisen. In einigen Situationen, wie z. b. der Wiederverwendung von-Anweisungen, muss jedoch auch SQLFreeStmt verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLFreeStmt-Funktion](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
