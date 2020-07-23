---
title: '! (Logisches NOT) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bb3d9bc9fb9ff483e86f1ddd4a451f440bac2824
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914487"
---
# <a name="-logical-not-ssis-expression"></a>! (Logisches NOT) (SSIS-Ausdruck)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Negiert einen booleschen Operanden.  
  
> [!NOTE]  
>  Der !-Operator kann nicht zusammen mit anderen Operatoren verwendet werden. Beispielsweise können nicht den !-Operator und den >-Operator zum !>-Operator zusammenfassen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression*  
 Ein gültiger Ausdruck, der zu einem booleschen Wert ausgewertet wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_BOOL  
  
## <a name="remarks"></a>Bemerkungen  
 In der folgenden Tabelle wird das Ergebnis des ausgeführt werden müssen.  
  
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
  
 In diesem Beispiel wird zu TRUE ausgewertet, falls der Wert der **MonthNumber** -Variablen mit der ganzen Zahl identisch ist, die den aktuellen Monat darstellt. Weitere Informationen finden Sie unter [MONTH &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/month-ssis-expression.md) und [GETDATE &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/getdate-ssis-expression.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Operatorenrangfolge und -assoziativität](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
