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
ms.openlocfilehash: ecec6116ee16f4affa615518a690d2c665648464
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68091240"
---
# <a name="sqlbindparam-mapping"></a>SQLBindParam-Zuordnung
**SQLBindParam** kann nicht wirklich als veraltet markiert werden, da es in ODBC nie vorhanden war. Sie stellt jedoch weiterhin duplizierte Funktionen dar. der Treiber-Manager muss Sie exportieren, da Sie von ISO und geöffneten Gruppen kompatiblen Anwendungen verwendet werden. Da **SQLBindParameter** die gesamte Funktionalität von **SQLBindParam**enthält, wird **SQLBindParam** oberhalb von **SQLBindParameter** zugeordnet (wenn es sich beim zugrunde liegenden Treiber um einen ODBC *3. x* -Treiber handelt). Ein ODBC *3. x* -Treiber muss **SQLBindParam**nicht implementieren.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn der folgende **SQLBindParam** -Befehl durchgeführt wird:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 der Treiber-Manager ruft **SQLBindParameter** im Treiber wie folgt auf:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Weitere Informationen finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung unter einem 64-Bit-Betriebssystem ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnen veralteter Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
