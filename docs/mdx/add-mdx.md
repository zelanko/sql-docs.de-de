---
title: + Eren (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9cb5ddf37104c0de00e17bdec5946d9b39d60020
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68017213"
---
# <a name="-add-mdx"></a>+ (Addition) (MDX)


  Führt eine arithmetische Operation aus, die zwei Zahlen addiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric_Expression + Numeric_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *Numerischer Ausdruck*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Datentyp des Parameters, der in der Rangfolge höher eingestuft ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Beide Ausdrücke müssen denselben Datentyp haben, oder es muss möglich sein, einen Ausdruck implizit in den Datentyp des anderen Ausdrucks zu konvertieren. Hat ein Ausdruck als Ergebnis den Wert NULL, gibt der Operator das Ergebnis des anderen Ausdrucks zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
