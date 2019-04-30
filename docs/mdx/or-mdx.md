---
title: ODER (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae6b6602d7968bb444dcf4838537bb000b97dd53
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63278261"
---
# <a name="or-mdx"></a>OR (MDX)


  Führt eine logische Disjunktion mit zwei numerischen Ausdrücken aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Expression1 OR Expression2   
```  
  
#### <a name="parameters"></a>Parameter  
 Expression1  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der einen numerischen Wert zurückgibt.  
  
 Expression2  
 Ein gültiger MDX-Ausdruck, der einen numerischen Wert zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein boolescher Wert, der zurückgibt **"true"** Wenn eine oder beide Argumente ausgewertet **"true"** ist, andernfalls **"false"**.  
  
## <a name="remarks"></a>Hinweise  
 Die **oder** -Operator behandelt beide Argumente als boolesche Werte (null, 0 (null) als **"false"** ist, andernfalls **"true"**), bevor der Operator die logische Disjunktion ausführt. In der folgende Tabelle wird veranschaulicht, wie die **oder** Operator die logische Disjunktion ausführt.  
  
|*Expression1*|*Expression2*|Rückgabewert|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage enthält ein berechnetes Measure, das die Zeichenfolge zurückgibt, die "MARRIED OR MALE" ist das aktuelle Element auf der geschlechtshierarchie der Customer-Dimension männlich oder das aktuelle Element auf der ehestatushierarchy der Customer-Dimension verheiratet ist; Andernfalls wird die Zeichenfolge "UNMARRIED oder FEMALE" zurückgegeben.  
  
```  
WITH  
MEMBER MEASURES.ORDEMO AS  
IIF(  
([Customer].[Gender].CURRENTMEMBER IS [Customer].[Gender].&[M])  
OR  
([Customer].[Marital Status].CURRENTMEMBER IS [Customer].[Marital Status].&[M]),  
"MARRIED OR MALE",  
"UNMARRIED OR FEMALE")  
SELECT [Customer].[Gender].[Gender].MEMBERS ON 0,  
[Customer].[Marital Status].[Marital Status].MEMBERS ON 1  
FROM [Adventure Works]  
WHERE(MEASURES.ORDEMO)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
