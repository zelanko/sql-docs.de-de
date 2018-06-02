---
title: = (Gleich) (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bb609b1a3bcfe08d0720aef70e584049080be148
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578172"
---
# <a name="-equal-to-mdx"></a>= (Ist gleich) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt eine Vergleichsoperation aus, die bestimmt, ob der Wert eines MDX-Ausdrucks (Multidimensional Expressions) gleich dem Wert eines anderen MDX-Ausdrucks ist.  
  
> [!NOTE]  
>  Um Objekte zu vergleichen, verwenden Sie die [IS &#40;MDX&#41; ](../mdx/is-mdx.md) Operator. Verwenden Sie z. B. den IS-Operator, um zu prüfen, ob das aktuelle Element auf einer Abfrageachse ein spezifisches Element ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
MDX_Expression = MDX_Expression   
```  
  
#### <a name="parameters"></a>Parameter  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der auf den folgenden Bedingungen basiert:  
  
-   **"true"** , wenn der Wert des ersten Parameters gleich dem Wert des zweiten Parameters ist.  
  
-   **"false"** , wenn der Wert des ersten Parameters ungleich dem Wert des zweiten Parameters ist.  
  
-   **"true"** Wenn beide Parameter null sind oder einen Parameter null ist, und der andere Parameter 0 ist gleich.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
