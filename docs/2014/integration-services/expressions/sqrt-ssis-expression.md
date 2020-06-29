---
title: SQRT (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 06e899be27df88a628f8e45493452a66739f30a4
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428177"
---
# <a name="sqrt-ssis-expression"></a>SQRT (SSIS-Ausdruck)
  Gibt die Quadratwurzel eines numerischen Ausdrucks zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein numerischer Ausdruck mit einem beliebigen numerischen Datentyp. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_R8  
  
## <a name="remarks"></a>Bemerkungen  
 SQRT gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 SQRT schlägt fehl, wenn das Argument einen negativen Wert aufweist.  
  
 Das Argument wird in einen DT_R8-Datentyp umgewandelt, bevor die Quadratwurzel berechnet wird.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird die Quadratwurzel eines numerischen Literals zurückgegeben. Als Ergebnis wird 12 zurückgegeben.  
  
```  
SQRT(144)  
```  
  
 In diesem Beispiel wird die Quadratwurzel eines Ausdrucks zurückgegeben, die das Ergebnis der Subtraktion von Werten in den Spalten **Value1** und **Value2** ist.  
  
```  
SQRT(Value1 - Value2)  
```  
  
 In diesem Beispiel wird die Länge der dritten Seite eines rechtwinkligen Dreiecks zurückgegeben, indem die SQUARE-Funktion auf zwei Variablen angewendet und dann die Quadratwurzel der Summe berechnet wird. Falls **Side1** 3 und **Side2** 4 enthält, gibt die SQRT-Funktion 5 zurück.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  In Ausdrücken schließen Variablennamen immer das \@-Präfix ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
