---
title: VisualTotals (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a5becd3382f07a9adc89055a253235495a7e50a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125838"
---
# <a name="visualtotals-mdx"></a>VisualTotals (MDX)


  Gibt eine Menge zurück, die durch dynamische Gesamtwertbildung der untergeordneten Elemente in einer angegebenen Menge generiert wird. Optional wird im Resultset ein Muster für den Namen des übergeordneten Elements verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
VisualTotals(Set_Expression[,Pattern])  
```  
  
## <a name="arguments"></a>Argumente  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Muster*  
 Ein gültiger Zeichenfolgenausdruck für das übergeordnete Element der Menge, der ein Sternchen (*) als Ersatzzeichen für den Namen des übergeordneten Elements enthält.  
  
## <a name="remarks"></a>Hinweise  
 Der angegebene Mengenausdruck kann eine Menge angeben, die Elemente auf beliebigen Ebenen innerhalb ein und derselben Dimension enthält, im Allgemeinen Elemente, die in einer Vorgänger-Nachfolger-Beziehung zueinander stehen. Die **VisualTotals** -Funktion fasst die Werte der untergeordneten Elemente in den angegebenen Satz und ignoriert die untergeordneten Elemente, die nicht in der Gruppe in das Ergebnis eingeschlossen sind. Bei hierarchisch geordneten Mengen werden die Gesamtwerte visuell summiert. Wenn die Reihenfolge der Elemente in der Menge die Hierarchie durchbricht, werden die Ergebnisse nicht als sichtbare Gesamtwerte zurückgegeben. Beispielsweise gibt VisualTotals (USA, WA, CA, Seattle) nicht WA als Seattle zurück. Vielmehr werden die Werte für WA, CA und Seattle zurückgegeben und anschließend zum sichtbaren Gesamtwert für USA summiert, wobei die Umsätze für Seattle doppelt gezählt werden.  
  
> [!NOTE]  
>  Anwenden der **VisualTotals** -Funktion auf Dimensionselemente, die beziehen sich nicht auf ein Measure oder unterhalb der Granularität der Measure-Gruppe führt dazu, dass die Werte durch Null ersetzt werden.  
  
 *Muster*, optional und gibt das Format für die gesamtbetragsbezeichnung an. *Muster* erfordert ein Sternchen (*), wie das Ersatzzeichen für das übergeordnete Element und den Rest des Texts in der Zeichenfolge im Ergebnis mit dem übergeordneten Namen verkettet angezeigt wird. Um ein Sternchen anzuzeigen, verwenden Sie zwei Sternchen (\*\*).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der sichtbare Gesamtwert für das dritte Quartal des Kalenderjahres 2001 basierend auf dem einzigen angegebenen nachfolgenden Wert, dem Monat Juli, zurückgegeben.  
  
```  
SELECT VisualTotals  
   ({[Date].[Calendar].[Calendar Quarter].&[2001]&[3]  
      ,[Date].[Calendar].[Month].&[2001]&[7]}) ON 0  
FROM [Adventure Works]  
```  
  
 Im folgenden Beispiel wird das [All]-Element der Category-Attributhierarchie in der Product-Dimension zusammen mit zwei seiner vier untergeordneten Elemente zurückgegeben. Der zurückgegebene Gesamtwert für das [All]-Element für das Internet Sales Amount-Measure stellt lediglich den Gesamtwert der Accessories- und Clothing-Elemente dar. Außerdem wird das Pattern-Argument zur Angabe der Bezeichnung für die [All Products]-Spalte verwendet.  
  
```  
SELECT  
   VisualTotals  
   ({[Product].[Category].[All Products]  
      ,[Product].[Category].[Accessories]  
      ,[Product].[Category].[Clothing]}  
      , '* - Visual Total'  
   ) ON Columns  
, [Measures].[Internet Sales Amount] ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
