---
title: IST (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 29d251c05639d928f3ea5a9925a4cc21935e0529
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62630877"
---
# <a name="is-mdx"></a>IS (MDX)


  Führt einen logischen Vergleich zweier Objektausdrücke aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>Parameter  
 *Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen MDX-Objektverweis zurückgibt.  
  
 *Expression2*  
 Ein gültiger MDX-Ausdruck, der einen MDX-Objektverweis zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der zurückgibt **"true"** , wenn beide Argumente für das gleiche Objekt verweisen, andernfalls **"false"** . Wenn die **NULL** Schlüsselwort angegeben ist, gibt der Operator **"true"** Wenn *Expression1* ist **null**ist, andernfalls **"false"** .  
  
## <a name="remarks"></a>Hinweise  
 Die **IS** -Operator wird häufig verwendet, um festzustellen, ob Tupeln und Elemente Idempotent sind, was bedeutet, dass sie genau gleich sind.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie Sie mit der **IS** Operator, um zu überprüfen, ob das aktuelle Element auf einer Abfrageachse ein spezifisches Element ist:  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
