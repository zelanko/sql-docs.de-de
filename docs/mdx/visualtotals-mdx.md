---
title: Visualsummen (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a5becd3382f07a9adc89055a253235495a7e50a8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
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
  
## <a name="remarks"></a>Bemerkungen  
 Der angegebene Mengenausdruck kann eine Menge angeben, die Elemente auf beliebigen Ebenen innerhalb ein und derselben Dimension enthält, im Allgemeinen Elemente, die in einer Vorgänger-Nachfolger-Beziehung zueinander stehen. Die **visualtotal** -Funktion gibt die Werte der untergeordneten Elemente in der angegebenen Menge zurück und ignoriert untergeordnete Elemente, die sich nicht in der Menge befinden, um die Ergebnis Summen zu berechnen. Bei hierarchisch geordneten Mengen werden die Gesamtwerte visuell summiert. Wenn die Reihenfolge der Elemente in der Menge die Hierarchie durchbricht, werden die Ergebnisse nicht als sichtbare Gesamtwerte zurückgegeben. Beispielsweise gibt VisualTotals (USA, WA, CA, Seattle) nicht WA als Seattle zurück. Vielmehr werden die Werte für WA, CA und Seattle zurückgegeben und anschließend zum sichtbaren Gesamtwert für USA summiert, wobei die Umsätze für Seattle doppelt gezählt werden.  
  
> [!NOTE]  
>  Wenn Sie die **visualsummen** -Funktion auf Dimensions Elemente anwenden, die nicht mit einem Measure verknüpft sind oder unter der Measure-Gruppen Granularität liegen, werden die Werte durch Null ersetzt.  
  
 Das optionale *Muster*gibt das Format für die Gesamt Bezeichnung an. *Pattern* erfordert ein Sternchen (*) als Ersatz Zeichen für das übergeordnete Element, und der restliche Text in der Zeichenfolge wird im Ergebnis mit dem übergeordneten Namen angezeigt. Wenn Sie ein literales Sternchen anzeigen möchten, verwenden Sie zwei\*\*Sternchen ().  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
