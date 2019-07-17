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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c8d2d567f899c30dfe91cd35445956cd6214da9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125551"
---
# <a name="sqlsetparam-mapping"></a>SQLSetParam-Zuordnung
**SQLSetParam** weiterhin auf der Basis von zuzuordnenden **SQLBindParameter** wie ODBC 2. *X*. Obwohl sie konzeptionell ist **SQLBindParam**, des Treiber-Managers ordnet nicht **SQLSetParam** zu **SQLBindParam**. Grund hierfür ist, bestimmte vorhandene ODBC 2. *x* Treiber verwendet den Sonderwert *Pufferlänge* (SQL_SETPARAM_VALUE_MAX), die der Treiber-Manager generiert, wenn ordnet **SQLSetParam** auf der Basis von  **SQLBindParameter** um zu bestimmen, wenn sie von 1 aufgerufen wird. *X* ODBC-Anwendung.  
  
 Ein Aufruf von  
  
```  
SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)  
```  
  
 Das folgende Ergebnis:  
  
```  
SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)  
```
