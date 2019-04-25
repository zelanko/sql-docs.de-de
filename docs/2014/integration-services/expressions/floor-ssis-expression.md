---
title: FLOOR (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9addd13deb4dcf3c81a4975e0ed33783799ae2a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62769166"
---
# <a name="floor-ssis-expression"></a>FLOOR (SSIS-Ausdruck)
  Gibt die größte ganze Zahl zurück, die kleiner oder gleich einem numerischen Ausdruck ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der numerische Datentyp des expression-Arguments. Das Ergebnis ist der ganzzahlige Teil des berechneten Werts mit dem gleichen Datentyp wie *numeric_expression*.  
  
## <a name="remarks"></a>Hinweise  
 FLOOR gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird die FLOOR-Funktion auf positive und negative Werte und auf Null angewendet.  
  
```  
FLOOR(123.45)  
```  
  
 Gibt 123.00 zurück.  
  
```  
FLOOR(-123.45)  
```  
  
 Gibt -124.00 zurück.  
  
```  
FLOOR(0.00)  
```  
  
 Gibt 0.00 zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [CEILING &#40;SSIS-Ausdruck&#41;](ceiling-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
