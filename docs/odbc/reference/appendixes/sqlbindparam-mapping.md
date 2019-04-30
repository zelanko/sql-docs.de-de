---
title: SQLBindParam-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57e0fe66d76f91c8cea35710e9d0245db7619628
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199714"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam-Zuordnung
**SQLBindParam** nicht wirklich aufgerufen werden als veraltet markierte, da sie noch nie war es in ODBC; allerdings es steht noch immer duplizierte Funktionalität – der Treiber-Manager benötigt, es zu exportieren, da ISO "und" Open Group-kompatible Anwendungen verwendet werden werden. Da **SQLBindParameter** enthält die gesamte Funktionalität der **SQLBindParam**, **SQLBindParam** wird zugeordnet werden, auf der Basis von **SQLBindParameter** (wenn der zugrunde liegenden Treiber ist ein ODBC 3.*.x* Treiber). Eine ODBC 3.*.x* Treiber muss nicht implementiert **SQLBindParam**.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der folgende Aufruf von **SQLBindParam** erfolgt:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 der Treiber-Manager ruft **SQLBindParameter** im Treiber wie folgt:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnung veralteter Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
