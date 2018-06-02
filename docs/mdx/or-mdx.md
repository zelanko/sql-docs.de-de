---
title: ODER (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 215ed38ef7887d9815c6cf4ac79321b95a367707
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580622"
---
# <a name="or-mdx"></a>OR (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 Ein boolescher Wert, der zurückgibt **"true"** Wenn eines oder beide Argumente ausgewertet **"true"** ist, andernfalls **"false"**.  
  
## <a name="remarks"></a>Hinweise  
 Die **oder** -Operator behandelt beide Argumente als boolesche Werte (null, 0, als **"false"** ist, andernfalls **"true"**), bevor der Operator die logische Disjunktion ausführt. Die folgende Tabelle verdeutlicht, wie die **oder** Operator die logische Disjunktion ausführt.  
  
|*Expression1*|*Expression2*|Rückgabewert|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage enthält ein berechnetes Measure, das die Zeichenfolge "MARRIED OR MALE" zurückgibt, wenn das aktuelle Element auf der Geschlechtshierarchie der Customer-Dimension Männlich oder das aktuelle Element auf der Ehestatushierarchy der Customer-Dimension "Married" ist. Andernfalls wird die Zeichenfolge "UNMARRIED OR FEMALE" zurückgegeben.  
  
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
  
  
