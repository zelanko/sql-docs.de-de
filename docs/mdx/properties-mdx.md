---
title: Eigenschaften (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e7d6e072cd47233b6cb76c09fb3bc0e9b9b42604
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020650"
---
# <a name="properties-mdx"></a>Properties (MDX)


  Gibt eine Zeichenfolge oder einen stark typisierten Wert zurück, der den Wert einer Elementeigenschaft enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.Properties(Property_Name [, TYPED])  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Property_name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen einer Elementeigenschaft enthält.  
  
## <a name="remarks"></a>Hinweise  
 Die **Eigenschaften** Funktion gibt den Wert des angegebenen Elements für die angegebene Elementeigenschaft zurück. Die Elementeigenschaft möglich die systeminternen Elementeigenschaften, wie z. B. **Namen**, **ID**, **Schlüssel**, oder **Beschriftung**, oder es kann ein eine benutzerdefinierte Elementeigenschaft. Weitere Informationen finden Sie unter [integrierte Elementeigenschaften &#40;MDX&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) und [benutzerdefinierte Elementeigenschaften &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
 Standardmäßig muss der Wert zwingend eine Zeichenfolge sein. Wenn **TYPISIERTE** angegeben ist, wird der Rückgabewert ist stark typisiert.  
  
-   Bei einer systeminternen Eigenschaft gibt die Funktion den ursprünglichen Typ des Elements zurück.  
  
-   Wenn der Eigenschaftentyp Benutzerdefiniert ist, der Typ des Rückgabewerts entspricht der Typ des Rückgabewerts der der **MemberValue** Funktion.  
  
> [!NOTE]  
>  Properties ('Key') gibt das gleiche Ergebnis wie Key0 zurück, außer für zusammengesetzte Schlüssel. Properties ('Key') gibt für zusammengesetzte Schlüssel den Wert NULL zurück. Verwenden Sie die Taste*x* -Syntax für zusammengesetzte Schlüssel, wie im Beispiel dargestellt. Properties ('Key0'), Properties('Key1'), Properties('Key2') usw. bilden zusammen den zusammengesetzten Schlüssel.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden sowohl systemeigene als auch benutzerdefinierte Elementeigenschaften zurückgegeben. Dabei wird das TYPED-Argument verwendet, um den stark typisierten Wert für die Day Name-Elementeigenschaft zurückzugeben.  
  
```  
WITH MEMBER Measures.MemberName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Name')  
MEMBER Measures.MemberVal AS   
   [Date].[Calendar].[July 1, 2003].Properties('Member_Value')  
MEMBER Measures.MemberKey AS   
   [Date].[Calendar].[July 1, 2003].Properties('Key')  
MEMBER Measures.MemberID AS   
   [Date].[Calendar].[July 1, 2003].Properties('ID')  
MEMBER Measures.MemberCaption AS   
   [Date].[Calendar].[July 1, 2003].Properties('Caption')  
MEMBER Measures.DayName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name', TYPED)  
MEMBER Measures.DayNameTyped AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name')  
MEMBER Measures.DayofWeek AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Week')  
MEMBER Measures.DayofMonth AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Month')  
MEMBER Measures.DayofYear AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Year')  
  
SELECT {Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  ON 0  
FROM [Adventure Works]  
```  
  
 Das folgende Beispiel zeigt die Verwendung des Schlüssels*x* Eigenschaft.  
  
```  
WITH   
MEMBER Measures.MemberKey AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key')  
MEMBER Measures.MemberKey0 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key0')  
MEMBER Measures.MemberKey1 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key1')  
  
SELECT {Measures.MemberKey  
   , Measures.MemberKey0  
   , Measures.MemberKey1     
   }  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Elementeigenschaften &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
