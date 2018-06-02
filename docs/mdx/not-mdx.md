---
title: KEINE (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5020f461d2576bbac7d0292ca0bf75bd8033e173
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580502"
---
# <a name="not-mdx"></a>NOT (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt eine logische Negation für einen numerischen Ausdruck aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Parameter  
 *Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der zurückgibt **"false"** , wenn das Argument ergibt **"true"** ist, andernfalls **"true"**.  
  
## <a name="remarks"></a>Hinweise  
 Die **nicht** -Operator behandelt den Ausdruck als booleschen Wert (null, 0, als **"false"** ist, andernfalls **"true"**), bevor der Operator die logische Negation ausführt. Die folgende Tabelle verdeutlicht, wie die **nicht** Operator die logische Negation ausführt.  
  
|*Expression1*|Rückgabewert|  
|-------------------|------------------|  
|**true**|**false**|  
|**false**|**true**|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
