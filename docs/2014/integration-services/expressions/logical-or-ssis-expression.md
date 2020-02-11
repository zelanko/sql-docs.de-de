---
title: '|| (Logisches OR) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OR operator
- logical OR (||)
- '|| (logical OR)'
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e4be7f70d568fd705847d3529fadd28181a71352
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62897596"
---
# <a name="-logical-or-ssis-expression"></a>|| (Logisches OR) (SSIS-Ausdruck)
  Führt eine logische OR-Operation aus. Der Ausdruck wird zu TRUE ausgewertet, falls mindestens eine Bedingung TRUE ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression1, boolean_expression2*  
 Ein gültiger Ausdruck, der zu TRUE, FALSE oder NULL ausgewertet wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle wird das Ergebnis des ||-Operators dargestellt.  
  
|Ergebnis|Ausdruck|Ausdruck|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## <a name="ssis-expression-examples"></a>Beispiele für SSIS-Ausdrücke  
 In diesem Beispiel werden die Spalten **StandardCost** und **ListPrice** verwendet. In diesem Beispiel wird zu TRUE ausgewertet, falls der Wert der **StandardCost** -Spalte kleiner als 300 oder falls die **ListPrice** -Spalte größer als 500 ist.  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 In diesem Beispiel werden die Variablen **SPrice** und **LPrice** anstelle numerischer Literale verwendet.  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [&#124; &#40;Bitweises inklusives OR&#41; &#40;SSIS-Ausdruck&#41;](bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40;Bitweises exklusives OR&#41; &#40;SSIS-Ausdruck&#41;](bitwise-exclusive-or-ssis-expression.md)   
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
