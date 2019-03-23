---
title: ABS (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7fafc0ba09a8345e0639016aadfdef185900589d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58375262"
---
# <a name="abs-ssis-expression"></a>ABS (SSIS-Ausdruck)
  Gibt den absoluten, positiven Wert eines numerischen Ausdrucks zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein numerischer Ausdruck mit oder ohne Vorzeichen.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Datentyp des numerischen Ausdrucks, der an die Funktion übergeben wird.  
  
## <a name="remarks"></a>Hinweise  
 ABS gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird die ABS-Funktion auf eine positive und eine negative Zahl angewendet. In beiden Fällen wird 1.23 zurückgegeben.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 In diesem Beispiel wird die ABS-Funktion auf einen Ausdruck angewendet, der Werte in den Variablen **HighTemperature** und **LowTempature**subtrahiert.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
