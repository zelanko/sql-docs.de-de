---
title: SQLtransact-Zuordnung | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304881"
---
# <a name="sqltransact-mapping"></a>SQLTransact-Zuordnung
**SQLTransact** wird jetzt durch **SQLEndTran**ersetzt. Der Hauptunterschied zwischen den beiden Funktionen besteht darin, dass **SQLEndTran** einen Argument- *Typ*enthält, der den Gültigkeitsbereich der zu erledenden Arbeit angibt. Mit dem " *Lenker Type* "-Argument kann die Umgebung oder das Verbindungs Handle angegeben werden. Der folgende **SQLTransact**-Befehl:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 ist zugeordnet  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 , wenn *connectionHandle* nicht gleich SQL_NULL_HDBC ist. Das *connectionHandle* -Argument wird auf den Wert von *hdbc*festgelegt.  
  
 **SQL_Transact** ist zugeordnet  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 , wenn *connectionHandle* gleich SQL_NULL_HDBC ist. Das *environmenthandle* -Argument ist auf den Wert von " *HENV*" festgelegt.  
  
 In beiden vorangehenden Fällen wird das *CompletionType* -Argument auf denselben Wert wie *ftype*festgelegt.
