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
ms.openlocfilehash: 770d66941af9b42be3c7b26f7e04a60d2a95cac2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017150"
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
  
## <a name="remarks"></a>Bemerkungen  
 Die **AllMembers** -Funktion gibt eine Menge zurück, die alle Elemente enthält, die berechnete Elemente in der angegebenen Hierarchie oder Ebene enthalten. Die **AllMembers** -Funktion gibt die berechneten Elemente zurück, auch wenn die angegebene Hierarchie oder Ebene keine sichtbaren Elemente enthält.  
  
> [!IMPORTANT]  
>  Wenn eine Dimension nur eine einzige sichtbare Hierarchie enthält, kann auf die Hierarchie entweder mit dem Dimensionsnamen oder mit dem Hierarchienamen verwiesen werden, weil der Dimensionsname in diesem Fall in seine einzige sichtbare Hierarchie aufgelöst wird. `Measures.AllMembers` ist z. B. ein gültiger MDX-Ausdruck, weil er in die einzige vorhandene Hierarchie in der Measures-Dimension aufgelöst wird.  
  
> [!NOTE]  
>  Die **AllMembers** -Funktion ähnelt semantisch der [AddCalculatedMembers-Funktion (MDX)](../mdx/addcalculatedmembers-mdx.md) .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Elemente in der [`Date].[Calendar Year]` Attribut Hierarchie auf der Spalten Achse, einschließlich berechneter Elemente, sowie die Menge aller untergeordneten Elemente `[Product].[Model Name]` der Attribut Hierarchie auf der Zeilen Achse des **Adventure Works** -Cubes zurückgegeben.  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 Im folgenden Beispiel werden alle Elemente der **Measures** -Dimension auf der Spalten Achse zurückgegeben, einschließlich aller berechneten Elemente und der Menge aller untergeordneten Elemente der `[Product].[Model Name]` Attribut Hierarchie auf der Zeilen Achse aus dem **Adventure Works** -Cube.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [AddCalculatedMembers &#40;MDX-&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Untergeordnete &#40;MDX-&#41;](../mdx/children-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
