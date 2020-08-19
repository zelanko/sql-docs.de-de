---
description: EXP (SSIS-Ausdruck)
title: EXP (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 09848aaee36990b8fd56e1f73cb4ba0f5c934095
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425482"
---
# <a name="exp-ssis-expression"></a>EXP (SSIS-Ausdruck)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Gibt den Exponenten für die Basis e eines numerischen Ausdrucks zurück. Die EXP-Funktion ergänzt die Aktion der LN-Funktion und wird auch als Antilogarithmus bezeichnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EXP(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_R8  
  
## <a name="remarks"></a>Hinweise  
 Der numerische Ausdruck wird in den DT_R8-Datentyp umgewandelt, bevor der Exponent berechnet wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Als Ergebnis wird immer eine positive Zahl zurückgegeben.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Diese Beispiele wenden die EXP-Funktion auf positive und negative Werte und auf Null an.  
  
```  
EXP(74)  
```  
  
 Gibt 1.373382979540176E+32 zurück.  
  
```  
EXP(-27)  
```  
  
 Gibt 1.879528816539083E-12 zurück.  
  
```  
EXP(0)  
```  
  
 Gibt 1 zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [LOG &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/log-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
