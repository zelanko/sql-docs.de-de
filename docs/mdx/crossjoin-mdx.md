---
title: Crossjoin (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b68dafa89f8285f532fc6e92e80f9741be239f65
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248250"
---
# <a name="crossjoin-mdx"></a>Crossjoin (MDX)


  Gibt das Kreuzprodukt mindestens einer Menge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Standard syntax  
Crossjoin(Set_Expression1 ,Set_Expression2 [,...n] )  
  
Alternate syntax  
Set_Expression1 * Set_Expression2 [* ...n]  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression1*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Set_Expression2*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Die **Crossjoin** Funktionsergebnis ist das Kreuzprodukt von zwei oder mehr angegebenen Mengen. Die Reihenfolge der Tupel in der sich ergebenden Menge hängt von der Reihenfolge der zu verknüpfenden Mengen und von der Reihenfolge ihrer Elemente ab. Z. B. wenn die erste Menge besteht aus {X1, X2,..., x*n*}, und die zweite Gruppe besteht aus {y1, y2,..., y*n*}, ist das Kreuzprodukt dieser Sätze:  
  
 {(X1, y1), (X1, y2),..., (X1, y*n*), (X2, y1), (X2, y2),...,  
  
 (x2, y*n*),..., (x*n*, y1), (x*n*, y2),..., (xn, y*n*)}  
  
> [!IMPORTANT]  
>  Wenn die Mengen im Cross Join aus Tupeln unterschiedlicher Attributhierarchien der gleichen Dimension bestehen, gibt die Funktion nur die Tupel zurück, die tatsächlich vorhanden sind. Weitere Informationen finden Sie unter [Schlüsselkonzepte in MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md).  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage enthält einfache Beispiele für die Verwendung der Crossjoin-Funktion auf der COLUMNS- und der ROWS-Achse einer Abfrage:  
  
 `SELECT`  
  
 `[Customer].[Country].Members *`  
  
 `[Customer].[State-Province].Members`  
  
 `ON 0,`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].Members,`  
  
 `[Product].[Category].[Category].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE Measures.[Internet Sales Amount]`  
  
 Das folgende Beispiel veranschaulicht das automatische Filtern, das erfolgt, wenn auf unterschiedliche Hierarchien derselben Dimension die Crossjoin-Funktion angewendet wird:  
  
 `SELECT`  
  
 `Measures.[Internet Sales Amount]`  
  
 `ON 0,`  
  
 `//Only the dates in Calendar Years 2003 and 2004 will be returned here`  
  
 `Crossjoin(`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]},`  
  
 `[Date].[Date].[Date].Members)`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 In den folgenden drei Beispielen wird das gleiche Ergebnis – Internet Sales Amount nach Bundesstaaten für die Bundesstaaten der USA – zurückgegeben. In den ersten beiden Beispielen werden die beiden Cross Join-Syntaxvarianten verwendet, im dritten Beispiel wird zur Veranschaulichung die WHERE-Klausel verwendet, um die gleichen Informationen zurückzugeben.  
  
### <a name="example-1"></a>Beispiel 1  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
       [Customer].[State-Province].Members  
   ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-2"></a>Beispiel 2  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
### <a name="example-3"></a>Beispiel 3  
  
```  
SELECT   
   [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
