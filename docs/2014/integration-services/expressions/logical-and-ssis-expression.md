---
title: '&amp;&amp; (Logisches AND) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f0d51123d4ef5b17ad69dc8623a586058e27e212
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62897537"
---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp; (Logisches AND) (SSIS-Ausdruck)
  Führt eine logische AND-Operation aus. Der Ausdruck wird zu TRUE ausgewertet, falls alle Bedingungen TRUE sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression1, boolean_expression2*  
 Ein gültiger Ausdruck, der zu TRUE, FALSE oder NULL ausgewertet wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle wird das Ergebnis des &&-Operators dargestellt.  
  
|Ergebnis|expression|expression|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel werden die Spalten **StandardCost** und **ListPrice** verwendet. In diesem Beispiel wird zu TRUE ausgewertet, falls der Wert der **StandardCost** -Spalte kleiner als 300 und falls die **ListPrice** -Spalte größer als 500 ist.  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 In diesem Beispiel werden die Variablen **SPrice** und **LPrice** anstelle von Literalen verwendet.  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Siehe auch  
 [& &#40;Bitweises AND&#41; &#40;SSIS-Ausdruck&#41;](bitwise-and-ssis-expression.md)   
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
