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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2082a97b24284afcc879048bb08e86a7b2bb3ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070112"
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
