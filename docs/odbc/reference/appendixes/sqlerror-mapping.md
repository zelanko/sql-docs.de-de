---
description: SQLError-Zuordnung
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
ms.openlocfilehash: 5d18d1b25acbbe56f29555274a7b8d995b7355d0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466022"
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
