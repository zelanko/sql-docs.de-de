---
title: + (Verketten) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 292d671fb3b971c30b6e261e3b851aba1ead9b36
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150003"
---
# <a name="-string-concatenation-mdx"></a>+ (Verketten von Zeichenfolgen) (MDX)


  Führt eine Zeichenfolgenoperation aus, die mindestens zwei Zeichenfolgen, Tupel oder eine Kombination von Zeichenfolgen und Tupeln verkettet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
String_Expression + String_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *String_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen Zeichenfolgenwert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Datentyp des Parameters, der in der Rangfolge höher eingestuft ist.  
  
## <a name="remarks"></a>Hinweise  
 Beide Ausdrücke müssen denselben Datentyp haben, oder es muss möglich sein, einen Ausdruck implizit in den Datentyp des anderen Ausdrucks zu konvertieren. Hat ein Ausdruck als Ergebnis den Wert NULL, gibt der Operator das Ergebnis des anderen Ausdrucks zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
