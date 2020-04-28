---
title: SQLError-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLError
- SQLError function [ODBC], mapping
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1aa3b66b29af755099cb273f3a19ca4e8230cd0b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302075"
---
# <a name="sqlerror-mapping"></a>SQLError-Zuordnung
Wenn eine Anwendung **SQLError** über einen ODBC *3. x* -Treiber aufruft, wird der Aufruf von  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 ist zugeordnet  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 Wenn das " *Lenker Type* "-Argument auf den Wert SQL_HANDLE_ENV, SQL_HANDLE_DBC oder SQL_HANDLE_STMT festgelegt ist, und das *handle* -Argument entsprechend auf den Wert in " *HENV*", " *hdbc*" oder " *hstmt*" festgelegt ist. Das Argument " *RecNumber* " wird vom Treiber-Manager festgelegt.
