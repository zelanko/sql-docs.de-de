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
ms.openlocfilehash: 9a9aa2ab3fbfdbe10246e0dcf8758cfcf7732375
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893676"
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
  
 *Property_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen einer Elementeigenschaft enthält.  
  
## <a name="remarks"></a>Hinweise  
 Die **Properties** -Funktion gibt den Wert des angegebenen Members für die angegebene Element Eigenschaft zurück. Die Element Eigenschaft kann eine beliebige der systeminternen Element Eigenschaften sein, z. b. " **Name**", " **ID**", " **Key**" oder " **Caption**", oder es kann sich um eine benutzerdefinierte Element Eigenschaft handeln. Weitere Informationen finden Sie unter systeminterne Element [ &#40;Eigenschaften MDX&#41; ](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties) und [benutzerdefinierte Element Eigenschaften &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties).  
  
 Standardmäßig muss der Wert zwingend eine Zeichenfolge sein. Wenn **eingegeben** angegeben wird, ist der Rückgabewert stark typisiert.  
  
-   Bei einer systeminternen Eigenschaft gibt die Funktion den ursprünglichen Typ des Elements zurück.  
  
-   Wenn der Eigenschaftentyp Benutzer definiert ist, ist der Typ des Rückgabewerts mit dem Typ des Rückgabewerts der Mitgliedschafts Funktion identisch.  
  
> [!NOTE]  
>  Properties ('Key') gibt das gleiche Ergebnis wie Key0 zurück, außer für zusammengesetzte Schlüssel. Properties ('Key') gibt für zusammengesetzte Schlüssel den Wert NULL zurück. Verwenden Sie die Key*x* -Syntax für zusammengesetzte Schlüssel, wie im Beispiel veranschaulicht. Properties ('Key0'), Properties('Key1'), Properties('Key2') usw. bilden zusammen den zusammengesetzten Schlüssel.  
  
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
  
 Das folgende Beispiel zeigt die Verwendung der Key*x* -Eigenschaft.  
  
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
 [Verwenden von Elementeigenschaften &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-member-properties)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
