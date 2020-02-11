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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
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
 Ein boolescher Wert, der **true** zurückgibt, wenn nur ein Argument als **true**ausgewertet wird. andernfalls **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Der **Xor** -Operator behandelt beide Parameter als boolesche Werte (null, 0, **false**, andernfalls **true**), bevor der Operator den logischen Ausschluss ausführt. In der folgenden Tabelle wird veranschaulicht, wie der **Xor** -Operator den logischen Ausschluss ausführt.  
  
|*Expression1*|*Expression2*|Rückgabewert|  
|-------------------|-------------------|------------------|  
|**Fall**|**Fall**|**Alarm**|  
|**Fall**|**Alarm**|**Fall**|  
|**Alarm**|**Fall**|**Fall**|  
|**Alarm**|**Alarm**|**Alarm**|  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
