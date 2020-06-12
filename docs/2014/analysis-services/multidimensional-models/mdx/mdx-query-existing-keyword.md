---
title: Vorhandenes Schlüsselwort (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115444c832fe8fe9b258a0c23b97b97553f32e8e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546212"
---
# <a name="existing-keyword-mdx"></a>EXISTING-Schlüsselwort (MDX)
  Erzwingt die Auswertung einer angegebenen Menge im aktuellen Kontext.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Mengenausdruck (Multidimensional Expressions).  
  
## <a name="remarks"></a>Bemerkungen  
 Standardmäßig werden Mengen im Kontext des Cubes ausgewertet, der die Elemente der Menge enthält. Das `Existing`-Schlüsselwort erzwingt dagegen die Auswertung einer angegebenen Menge im aktuellen Kontext.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Anzahl der Wiederverkäufer, deren Umsätze im vergangenen Zeitraum zurückgegangen sind, basierend auf vom Benutzer ausgewählten State-Province-Elementwerten zurückgegeben, die mit der `Aggregate`-Funktion ausgewertet wurden. Das [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) und [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) werden zum Zurückgeben von Werten für zurückgegangene Umsätze in Produktkategorien der Product-Dimension verwendet. Das `Existing` -Schlüsselwort erzwingt die Auswertung der Menge in der `Filter` Funktion im aktuellen Kontext, d. h. für die Washington-und Oregon-Elemente der State-Province-Attribut Hierarchie.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzahl &#40;fest geleg&#41; &#40;MDX-&#41;](/sql/mdx/count-set-mdx)   
 [AddCalculatedMembers &#40;MDX-&#41;](/sql/mdx/addcalculatedmembers-mdx)   
 [&#40;MDX-&#41;aggregieren](/sql/mdx/aggregate-mdx)   
 [&#40;MDX-&#41;Filtern](/sql/mdx/filter-mdx)   
 [Eigenschaften &#40;MDX-&#41;](/sql/mdx/properties-mdx)   
 [DrilldownLevel-&#40;MDX-&#41;](/sql/mdx/drilldownlevel-mdx)   
 [Hierarchize &#40;MDX-&#41;](/sql/mdx/hierarchize-mdx)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx)  
  
  
