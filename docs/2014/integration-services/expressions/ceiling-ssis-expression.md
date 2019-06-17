---
title: CEILING (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a8306fa98194fbf314796b199fea98ddd53cb1fb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62769426"
---
# <a name="ceiling-ssis-expression"></a>CEILING (SSIS-Ausdruck)
  Gibt die kleinste ganze Zahl zurück, die größer oder gleich einem numerischen Ausdruck ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Datentyp des numerischen Ausdrucks, der an die Funktion übergeben wird.  
  
## <a name="remarks"></a>Hinweise  
 CEILING gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesen Beispielen wird die CEILING-Funktion auf positive und negative Werte und auf Null angewendet.  
  
```  
CEILING(123.74)  
```  
  
 Gibt 124,00 zurück.  
  
```  
CEILING(-124.27)  
```  
  
 Gibt -124.00 zurück.  
  
```  
CEILING(0.00)  
```  
  
 Gibt 0.00 zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [FLOOR &#40;SSIS-Ausdruck&#41;](floor-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
