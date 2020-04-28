---
title: oder (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 45063e9f2aca6a924289d4d52434535d16c9a08e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68055710"
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
 Ein boolescher Wert, der **true** zurückgibt, wenn eines oder beide Argumente als **true**ausgewertet werden. andernfalls **false**.  
  
## <a name="remarks"></a>Bemerkungen  
 Der **or** -Operator behandelt beide Argumente als boolesche Werte (null, 0, **false**, andernfalls **true**), bevor der Operator die logische Disjunktion ausführt. In der folgenden Tabelle wird veranschaulicht, wie der **or** -Operator die logische Disjunktion ausführt.  
  
|*Expression1*|*Expression2*|Rückgabewert|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**true**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage enthält ein berechnetes Measure, das die Zeichenfolge "Married or männlich" zurückgibt, wenn das aktuelle Element in der Geschlechts Hierarchie der Customer-Dimension männlich ist oder das aktuelle Element in der Familien Status-Hierarchie der Customer-Dimension verheiratet ist. Andernfalls wird die Zeichenfolge "unverheiratet oder weiblich" zurückgegeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Operator Verweis &#40;MDX-&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
