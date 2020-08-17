---
description: IS (MDX)
title: ist (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eab5fc86d89fccbe6ae56c4dba78ccde60e26d50
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387346"
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
 Ein boolescher Wert, der **true** zurückgibt, wenn beide Argumente auf das gleiche Objekt verweisen. andernfalls **false**. Wenn das **null** -Schlüsselwort angegeben ist, gibt der Operator **true** zurück, wenn *expression1* **null**ist. andernfalls **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Der **is** -Operator wird häufig verwendet, um zu bestimmen, ob Tupel und Member idempotent sind, was bedeutet, dass Sie exakt äquivalent sind.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie der **is** -Operator verwendet wird, um zu überprüfen, ob das aktuelle Element auf einer Achse ein bestimmtes Element ist:  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
