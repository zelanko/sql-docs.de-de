---
title: AllMembers (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92cde0acf07f62d0678da6dd96efa707dedc1a1f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63066248"
---
# <a name="allmembers-mdx"></a>AllMembers (MDX)


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
 Die **AllMembers** -Funktion eine Menge, die alle Elemente enthält und die berechneten Elemente, in der angegebenen Hierarchie oder Ebene enthält, zurück. Die **AllMembers** Funktion gibt die berechneten Elemente zurück, auch wenn die angegebene Hierarchie oder Ebene keine sichtbaren Elemente enthält.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension nur eine einzige sichtbare Hierarchie enthält, kann auf die Hierarchie entweder mit dem Dimensionsnamen oder mit dem Hierarchienamen verwiesen werden, weil der Dimensionsname in diesem Fall in seine einzige sichtbare Hierarchie aufgelöst wird. `Measures.AllMembers` ist z. B. ein gültiger MDX-Ausdruck, weil er in die einzige vorhandene Hierarchie in der Measures-Dimension aufgelöst wird.  
  
> [!NOTE]  
>  Die **AllMembers** -Funktion ähnelt semantisch der [AddCalculatedMembers (MDX)](../mdx/addcalculatedmembers-mdx.md) Funktion.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel gibt alle Elemente in der [`Date].[Calendar Year]` -Attributhierarchie auf der Spaltenachse Dies schließt berechnete Elemente, sowie die Menge aller untergeordneten Elemente des der `[Product].[Model Name]` -Attributhierarchie auf der Zeilenachse der **Adventure Works** Cube.  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 Das folgende Beispiel gibt alle Elemente in der **Measures** Dimension auf der Spaltenachse, dazu gehören alle berechneten Elemente, sowie die Menge aller untergeordneten Elemente des der `[Product].[Model Name]` -Attributhierarchie auf der Zeilenachse aus der **Adventure Works** Cube.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Children &#40;MDX&#41;](../mdx/children-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
