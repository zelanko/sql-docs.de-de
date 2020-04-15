---
title: SQLTransact-Zuordnung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6aaa056fca860a70f81ad7c3a4cd8539512bc25d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304881"
---
# <a name="sqltransact-mapping"></a>SQLTransact-Zuordnung
**SQLTransact** wird jetzt durch **SQLEndTran**ersetzt. Der Hauptunterschied zwischen den beiden Funktionen besteht darin, dass **SQLEndTran** ein Argument *HandleType*enthält, das den Umfang der zu erledigenden Arbeit angibt. Das *HandleType-Argument* kann die Umgebung oder das Verbindungshandle angeben. Der folgende Aufruf von **SQLTransact:**  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 wird zugeordnet, um  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 wenn *ConnectionHandle* nicht gleich SQL_NULL_HDBC ist. Das *ConnectionHandle-Argument* wird auf den Wert von *hdbc*festgelegt.  
  
 **SQL_Transact** wird  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 wenn *ConnectionHandle* gleich SQL_NULL_HDBC ist. Das *EnvironmentHandle-Argument* wird auf den Wert von *henv*festgelegt.  
  
 In beiden vorstehenden Fällen wird das *CompletionType-Argument* auf denselben Wert wie *fType*festgelegt.
