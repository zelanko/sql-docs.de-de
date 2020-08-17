---
description: SQLSetParam-Zuordnung
title: SQLSetParam-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetParam
- SQLSetParam function [ODBC], mapping
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2c16f942920b5fefff664cc647f4edfc9ab6d13
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339296"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam-Zuordnung
**SQLSetParam** wird weiterhin auf **SQLBindParameter** wie in ODBC 2 zugeordnet. *x*. Obwohl es konzeptionell mit **SQLBindParam**vergleichbar ist, ordnet der Treiber-Manager **SQLSetParam** nicht zu **SQLBindParam**zu. Dies liegt daran, dass bestimmte vorhandene ODBC 2-. *x* -Treiber verwenden den besonderen Wert von *BufferLength* (SQL_SETPARAM_VALUE_MAX), den der Treiber-Manager generiert, wenn er **SQLSetParam** Top von **SQLBindParameter** zuordnet, um zu bestimmen, wann er von 1 aufgerufen wird. *x* ODBC-Anwendung.  
  
 Ein-Rückruf  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 führt zu folgendem:  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
