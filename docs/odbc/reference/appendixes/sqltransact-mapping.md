---
description: SQLTransact-Zuordnung
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
ms.openlocfilehash: cf1298c9881a207c21074e03e8b0597ab8f11448
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429501"
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
