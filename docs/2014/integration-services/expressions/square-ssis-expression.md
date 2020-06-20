---
title: SQUARE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 60c5fdc74e68970f7c62d83f9eeb65ce6db7d41c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966570"
---
# <a name="square-ssis-expression"></a>SQUARE (SSIS-Ausdruck)
  Gibt das Quadrat eines numerischen Ausdrucks zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein numerischer Ausdruck mit einem beliebigen numerischen Datentyp. Weitere Informationen finden Sie unter [Integration Services Datentypen](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_R8  
  
## <a name="remarks"></a>Bemerkungen  
 SQUARE gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
 Das Argument wird in einen DT_R8-Datentyp umgewandelt, bevor das Quadrat berechnet wird.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird das Quadrat von 12 zurückgegeben. Als Ergebnis wird 144 zurückgegeben.  
  
```  
SQUARE(12)  
```  
  
 In diesem Beispiel wird das Quadrat des Ergebnisses aus der Subtraktion von Werten in zwei Spalten zurückgegeben. Falls **Value1** 12 und **Value2** 4 enthält, gibt die SQUARE-Funktion 64 zurück.  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 In diesem Beispiel wird die Länge der dritten Seite eines rechtwinkligen Dreiecks zurückgegeben, indem die SQUARE-Funktion auf zwei Variablen angewendet und dann die Quadratwurzel der Summe berechnet wird. Falls **Side1** 3 und **Side2** 4 enthält, gibt die SQRT-Funktion 5 zurück.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  In Ausdrücken schließen Variablennamen immer das \@-Präfix ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](functions-ssis-expression.md)  
  
  
