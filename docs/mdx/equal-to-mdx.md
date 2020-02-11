---
title: = (Gleich) (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 189facb54de244ff220b41ec08c8b02faf5a2c27
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139316"
---
# <a name="-equal-to-mdx"></a>= (Ist gleich) (MDX)


  Führt eine Vergleichsoperation aus, die bestimmt, ob der Wert eines MDX-Ausdrucks (Multidimensional Expressions) gleich dem Wert eines anderen MDX-Ausdrucks ist.  
  
> [!NOTE]  
>  Um-Objekte zu vergleichen, verwenden Sie den [is &#40;MDX-&#41;](../mdx/is-mdx.md) Operator. Verwenden Sie z. B. den IS-Operator, um zu prüfen, ob das aktuelle Element auf einer Abfrageachse ein spezifisches Element ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MDX_Expression = MDX_Expression   
```  
  
#### <a name="parameters"></a>Parameter  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der auf den folgenden Bedingungen basiert:  
  
-   **true** , wenn der Wert des ersten Parameters gleich dem Wert des zweiten Parameters ist.  
  
-   **false** , wenn der Wert des ersten Parameters nicht gleich dem Wert des zweiten Parameters ist.  
  
-   **true** , wenn beide Parameter NULL sind oder ein Parameter NULL ist und der andere Parameter den Wert 0 hat.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage enthält Beispiele für diese Bedingungen:  
  
 `With`  
  
 `--Returns true`  
  
 `Member [Measures].bool1 as 1=1`  
  
 `--Returns false`  
  
 `Member [Measures].bool2 as 1=0`  
  
 `--Returns true`  
  
 `Member [Measures].bool3 as null=null`  
  
 `--Returns true`  
  
 `Member [Measures].bool4 as 0=null`  
  
 `--Returns false`  
  
 `Member [Measures].bool5 as 1=null`  
  
 `Select {[Measures].bool1,[Measures].bool2,[Measures].bool3,[Measures].bool4,[Measures].bool5}`  
  
 `On 0`  
  
 `From [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
