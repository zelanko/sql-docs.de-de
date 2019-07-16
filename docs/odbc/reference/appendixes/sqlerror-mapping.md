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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f24a305c2f22ef4cfacbbe4bcbcf498eab648f1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064473"
---
# <a name="sqlerror-mapping"></a>SQLError-Zuordnung
Wenn eine Anwendung ruft **SQLError** über einen ODBC *3.x* Treiber, den Aufruf von  
  
```  
SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)   
```  
  
 wird zugeordnet  
  
```  
SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)  
```  
  
 mit der *HandleType* -Argument auf den Wert nach Bedarf SQL_HANDLE_ENV auf SQL_HANDLE_DBC auf oder SQL_HANDLE_STMT auf, und die *behandeln* Argument festgelegt wird, mit dem Wert im *Henv*, *Hdbc*, oder *Befehls beschäftigt*je nach Bedarf. Die *RecNumber* -Argument wird vom Treiber-Manager bestimmt.
