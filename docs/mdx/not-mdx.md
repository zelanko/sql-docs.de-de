---
title: KEINE (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4031b887eb0a42580d6ae8debf6c9177ff67efc3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088234"
---
# <a name="not-mdx"></a>NOT (MDX)


  Führt eine logische Negation für einen numerischen Ausdruck aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Parameter  
 *Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der zurückgibt **"false"** ergibt das Argument **"true"** ist, andernfalls **"true"** .  
  
## <a name="remarks"></a>Hinweise  
 Die **nicht** -Operator behandelt den Ausdruck als booleschen Wert (null, 0 (null) als **"false"** ist, andernfalls **"true"** ), bevor der Operator die logische Negation ausführt. In der folgende Tabelle wird veranschaulicht, wie die **nicht** Operator die logische Negation ausführt.  
  
|*Expression1*|Rückgabewert|  
|-------------------|------------------|  
|**true**|**false**|  
|**false**|**true**|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
