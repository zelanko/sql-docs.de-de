---
title: + (Addieren) (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b96a6e5c659925ea5eed876e1f7505997ea02b71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149486"
---
# <a name="-add-ssis"></a>+ (Addieren) (SSIS)
  Addiert zwei numerische Ausdrücke.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression1, numeric_ expression2*  
 Jeder gültige Ausdruck mit einem numerischen Datentyp.  
  
## <a name="result-types"></a>Ergebnistypen  
 Die Ergebnistypen werden von den Datentypen der beiden Argumente bestimmt. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="remarks"></a>Hinweise  
 Wenn einer der Operanden NULL ist, ist das Ergebnis NULL.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel werden numerische Literale addiert.  
  
```  
5 + 6.09 + 7.0  
```  
  
 In diesem Beispiel werden Werte in den Spalten **VacationHours** und **SickLeaveHours** addiert.  
  
```  
VacationHours + SickLeaveHours  
```  
  
 In diesem Beispiel wird ein berechneter Wert zur **StandardCost** -Spalte addiert. Die **Profit%** -Variable muss in eckige Klammern eingeschlossen werden, weil der Name das Zeichen % enthält. Weitere Informationen finden Sie unter [Bezeichner &#40;SSIS&#41;](identifiers-ssis.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge und Assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  