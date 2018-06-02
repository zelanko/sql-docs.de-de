---
title: AllMembers (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a5720c3e82fdb341635c23d13a9c6bf4346a1cc0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577172"
---
# <a name="allmembers-mdx"></a>AllMembers (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Wertet entweder einen Hierarchie- oder einen Ebenenausdruck aus und gibt eine Menge zurück, die alle Elemente der angegebenen Hierarchie oder Ebene enthält. Hierzu zählen alle berechneten Elemente der Hierarchie oder Ebene.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>Argumente  
 *Hierarchy_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Hierarchie zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **AllMembers** -Funktion eine Menge, die alle Elemente enthält, einschließlich berechneter Elemente in der angegebenen Hierarchie oder Ebene zurück. Die **AllMembers** Funktion gibt die berechneten Elemente zurück, selbst wenn die angegebene Hierarchie oder Ebene keine sichtbaren Elemente enthält.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension nur eine einzige sichtbare Hierarchie enthält, kann auf die Hierarchie entweder mit dem Dimensionsnamen oder mit dem Hierarchienamen verwiesen werden, weil der Dimensionsname in diesem Fall in seine einzige sichtbare Hierarchie aufgelöst wird. `Measures.AllMembers` ist z. B. ein gültiger MDX-Ausdruck, weil er in die einzige vorhandene Hierarchie in der Measures-Dimension aufgelöst wird.  
  
> [!NOTE]  
>  Die **AllMembers** -Funktion ähnelt semantisch der [AddCalculatedMembers (MDX)](../mdx/addcalculatedmembers-mdx.md) Funktion.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt alle Elemente in der [`Date].[Calendar Year]` Attributhierarchie auf der Spaltenachse, dies schließt berechnete Elemente und die Menge aller untergeordneten Elemente von der `[Product].[Model Name]` -Attributhierarchie auf der Zeilenachse der **Adventure Works** Cube.  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 Das folgende Beispiel gibt alle Elemente in der **Measures** Dimension auf der Spaltenachse einschließlich aller berechneten Elemente sowie die Menge aller untergeordneten Elemente der der `[Product].[Model Name]` -Attributhierarchie auf der Zeilenachse der **Adventure Works** Cube.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Untergeordnete Elemente &#40;MDX&#41;](../mdx/children-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
