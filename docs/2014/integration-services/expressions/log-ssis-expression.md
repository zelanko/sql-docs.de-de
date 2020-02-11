---
title: LOG (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- base-10 logarithms
- LOG function
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fde9e5cdaea245fd0b99820a89a4466e2d669fdf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62769066"
---
# <a name="log-ssis-expression"></a>LOG (SSIS-Ausdruck)
  Gibt den Logarithmus eines numerischen Ausdrucks zur Basis 10 zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LOG(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein gültiger numerischer Ausdruck, der ungleich 0 oder nicht negativ ist.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_R8  
  
## <a name="remarks"></a>Bemerkungen  
 Der *numerische Ausdruck* wird in den DT_R8-Datentyp umgewandelt, bevor der Logarithmus berechnet wird. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
 Falls *numeric_expression* zu 0 (null) oder einem negativen Wert ausgewertet wird, wird als Ergebnis NULL zurückgegeben.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein numerisches Literal verwendet. Die Funktion gibt den Wert 1.988291341907488 zurück.  
  
```  
LOG(97.34)  
```  
  
 In diesem Beispiel wird die **Length**-Spalte verwendet. Falls der Spaltenwert 101.24 ist, gibt die Funktion 2.005352136486217 zurück.  
  
```  
LOG(Length)   
```  
  
 In diesem Beispiel wird die **Length**-Variable verwendet. Die Variable muss einen numerischen Datentyp aufweisen, oder der Ausdruck muss eine explizite Umwandlung in einen numerischen [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Datentyp einschließen. Falls **Length** gleich 234.567 ist, gibt die Funktion 2.370266913465859 zurück.  
  
```  
LOG(@Length)   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [EXP &#40;SSIS-Ausdruck&#41;](exp-ssis-expression.md)   
 [LN &#40;SSIS-Ausdruck&#41;](ln-ssis-expression.md)   
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
