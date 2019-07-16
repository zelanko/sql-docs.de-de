---
title: XOR (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1657d9e58a0ae729a67e179602cd9a886ae923b1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125791"
---
# <a name="xor-mdx"></a>XOR (MDX)


  Führt eine logische Exklusion zweier numerischer Ausdrücke aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>Parameter  
 *Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen numerischen Wert zurückgibt.  
  
 *Expression2*  
 Ein gültiger MDX-Ausdruck, der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der zurückgibt **"true"** ergibt nur ein Argument **"true"** ist, andernfalls **"false"** .  
  
## <a name="remarks"></a>Hinweise  
 Die **XOR** -Operator behandelt beide Parameter als boolesche Werte (null, 0 (null) als **"false"** ist, andernfalls **"true"** ), bevor der Operator die logische Exklusion ausführt. In der folgende Tabelle wird veranschaulicht, wie die **XOR** -Operator führt die logische Exklusion.  
  
|*Expression1*|*Expression2*|Rückgabewert|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
