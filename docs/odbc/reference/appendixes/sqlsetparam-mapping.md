---
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
ms.openlocfilehash: 4d8e632412965664e5cdd9c87dc1e26787dcdab2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300530"
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
