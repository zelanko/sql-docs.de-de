---
title: '! (Logisches NOT) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9856f1ecb67a00f73782de1a23c361ca35ea83f4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779082"
---
# <a name="-logical-not-ssis-expression"></a>! (Logisches NOT) (SSIS-Ausdruck)
  Negiert einen booleschen Operanden.  
  
> [!NOTE]  
>  Der !-Operator kann nicht zusammen mit anderen Operatoren verwendet werden. Beispielsweise können nicht den !-Operator und den >-Operator zum !>-Operator zusammenfassen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression*  
 Ein gültiger Ausdruck, der zu einem booleschen Wert ausgewertet wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="remarks"></a>Hinweise  
 In der folgenden Tabelle wird das Ergebnis des Operation.  
  
|Ursprünglicher boolescher Ausdruck|Nach dem Anwenden des !- Operator|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird zu FALSE ausgewertet, falls der Wert in der **Color** -Spalte "red" ist.  
  
```  
!(Color == "red")  
```  
  
 In diesem Beispiel wird zu TRUE ausgewertet, falls der Wert der **MonthNumber** -Variablen mit der ganzen Zahl identisch ist, die den aktuellen Monat darstellt. Weitere Informationen finden Sie unter [MONTH &#40;SSIS-Ausdruck&#41;](month-ssis-expression.md) und [GETDATE &#40;SSIS-Ausdruck&#41;](getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
