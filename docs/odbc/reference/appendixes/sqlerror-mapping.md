---
title: SQLError-Zuordnung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302075"
---
# <a name="sqlerror-mapping"></a>SQLError-Zuordnung
Wenn eine Anwendung **SQLError** über einen ODBC *3.x-Treiber* aufruft,  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 wird zugeordnet, um  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 wenn das *HandleType-Argument* auf den Wert SQL_HANDLE_ENV, SQL_HANDLE_DBC oder SQL_HANDLE_STMT festgelegt ist, und das *Handle-Argument* auf den Wert in *henv*, *hdbc*oder *hstmt*, entsprechend festgelegt ist. Das *RecNumber-Argument* wird vom Treiber-Manager bestimmt.
