---
title: SQLBindParam-Zuordnung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c1df595722297c91dc75398470912188e109e278
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305440"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam-Zuordnung
**SQLBindParam** kann nicht wirklich als veraltet bezeichnet werden, da es in ODBC nie vorhanden war. Es stellt jedoch immer noch doppelte Funktionalität dar – der Treiber-Manager muss sie exportieren, da ISO- und Open Group-kompatible Anwendungen sie verwenden. Da **SQLBindParameter** alle Funktionen von **SQLBindParam**enthält, wird **SQLBindParam** zusätzlich zu **SQLBindParameter** zugeordnet (wenn der zugrunde liegende Treiber ein ODBC *3.x-Treiber* ist). Ein ODBC *3.x-Treiber* muss **SQLBindParam**nicht implementieren.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der folgende Aufruf von **SQLBindParam** erfolgt:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 Der Treiber-Manager ruft **SQLBindParameter** im Treiber wie folgt auf:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Siehe [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung veralteter Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
