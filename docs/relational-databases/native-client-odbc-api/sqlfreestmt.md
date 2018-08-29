---
title: SQLFreeStmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f1685b30fb3ed4a0e8d22c97327eb0142f7acf7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43084693"
---
# <a name="sqlfreestmt"></a>'SQLFreeStmt'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In der Regel   
      **SQLFreeStmt** ODBC 3.0 und höher wird nicht empfohlen. Wenn die Anwendung die Anweisung erneut verwenden muss Sie jedoch weiterhin verwenden sollten **SQLFreeStmt** mit der **SQL_RESET_PARAMS** und **SQL_UNBIND** Optionen). Sie können auch [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), und [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) ersetzen oder duplizieren die Funktion der **SQLFreeStmt** und sollte stattdessen diese verwendet werden.  
  
 Im Allgemeinen ist es effizienter, Wiederverwenden von Anweisungen als zum Löschen und neu zuzuordnen. Jedoch muss in einigen Situationen, z. B. die Wiederverwendung von Anweisungen, SQLFreeStmt weiterhin verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLFreeStmt-Funktion](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
