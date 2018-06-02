---
title: Ausdrücke (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 79909f574d818a599f30ad051be9cf6a980430a9
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579482"
---
# <a name="expressions-mdx"></a>Ausdrücke (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Ein Ausdruck ist eine Kombination aus Bezeichnern, Werten und Operatoren, [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] auswerten kann, um ein Ergebnis zu erhalten. Die Daten können an verschiedenen Stellen beim Zugriff oder Ändern von Daten verwendet werden. Beispielsweise können Sie einen Ausdruck als Teil der Daten, die von einer Abfrage abgerufen werden sollen, oder als Suchbedingung verwenden, um nach Daten zu suchen, die bestimmte Kriterien erfüllen.  
  
## <a name="simple-and-complex-expressions"></a>Einfache und komplexe Ausdrücke  
 Ein Ausdruck in MDX kann einfach oder komplex sein.  
  
 Ein einfacher Ausdruck kann einer der folgenden Ausdrücke sein:  
  
 Konstante  
 Eine Konstante ist ein Symbol, das einen bestimmten Datenwert in MDX darstellt. Zeichenfolgen-, numerische und Datumswerte können als Konstanten gerendert werden. Im Gegensatz zu numerischen Konstanten müssen Zeichenfolgen- und Datumskonstanten in einfache Anführungszeichen (') eingeschlossen werden.  
  
 Skalarfunktion  
 Eine Skalarfunktion gibt einen einzelnen Wert im Kontext einer Auswertung in MDX zurück. Zum Verständnis, wie Skalarfunktionen von MDX ausgewertet werden, muss der Unterschied zu den anderen MDX-Ausdrücken klar sein, denn die meisten MDX-Ausdrücke, -Anweisungen und -Skripts werden nicht für ein einzelnes Datenelement, sondern iterativ für eine Gruppe von Datenelementen (z. B. Zellen oder Elemente) ausgewertet. Zu dem Zeitpunkt, zu dem eine Skalarfunktion ausgewertet wird, ermittelt die Funktion üblicherweise nur den Wert für ein einzelnes Datenelement.  
  
 Objektbezeichner  
 MDX ist wegen der Beschaffenheit der mehrdimensionalen Daten objektorientiert. Objektbezeichner werden in MDX als einfache Ausdrücke angesehen. Weitere Informationen zu Bezeichnern finden Sie unter [Bezeichner &#40;MDX&#41;](../mdx/identifiers-mdx.md).  
  
 Ein komplexer Ausdruck kann aus Kombinationen dieser Entitäten erstellt werden, die durch Operatoren verknüpft sind.  
  
## <a name="expression-results"></a>Ergebnisse von Ausdrücken  
 Bei einfachen Ausdrücken, die aus einer einzelnen Konstanten, Variablen, Skalarfunktion oder einem Spaltennamen bestehen, entsprechen Datentyp, Sortierung, Genauigkeit, Anzahl der Dezimalstellen und Wert des Ausdrucks den jeweiligen Eigenschaften (Datentyp, Sortierung, Genauigkeit usw.) des Elements, auf das verwiesen wird. Da MDX direkt nur den OLE VARIANT-Datentyp unterstützt, tritt keine Koersion auf, wenn einfache Ausdrücke verwendet werden.  
  
 Bei einem komplexen Ausdruck kann eine Koersion auftreten, wenn mehrere einfache Ausdrücke mit unterschiedlichen Datentypen verwendet werden.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Die folgende Abfrage zeigt Beispiele berechneter Measures, deren Definitionen einfache Ausdrücke sind:  
  
 `WITH`  
  
 `MEMBER MEASURES.CONSTANTVALUE AS 1`  
  
 `MEMBER MEASURES.SCALARFUNCTION AS [Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.OBJECTIDENTIFIER AS [Measures].[Internet Sales Amount]`  
  
 `SELECT {MEASURES.CONSTANTVALUE,MEASURES.SCALARFUNCTION,MEASURES.OBJECTIDENTIFIER } ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Bei einem Ausdruck kann es sich auch um eine Berechnung handeln, wie z. B. `[Measures].[Discount Amount] * 1.5`. Im folgenden Beispiel wird gezeigt, wie eine Berechnung dazu verwendet wird, ein Element in einer MDX-SELECT-Anweisung zu definieren:  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Using Cube and Subcube Expressions (Verwenden von Cube- und Teilcubeausdrücken)](../mdx/using-cube-and-subcube-expressions.md)|Definiert Cube- und Teilcubeausdrücke.|  
|[Using Dimension Expressions (Verwenden von Dimensionsausdrücken)](../mdx/using-dimension-expressions.md)|Definiert Dimensionsausdrücke.|  
|[Using Member Expressions (Verwenden von Elementausdrücken)](../mdx/using-member-expressions.md)|Definiert Elementausdrücke.|  
|[Using Tuple Expressions (Verwenden von Tupelausdrücken)](../mdx/using-tuple-expressions.md)|Definiert Tupelausdrücke.|  
|[Using Set Expressions (Verwenden von Mengenausdrücken)](../mdx/using-set-expressions.md)|Definiert Mengenausdrücke.|  
|[Using Scalar Expressions (Verwenden von Skalarausdrücken)](../mdx/using-scalar-expressions.md)|Definiert skalare Ausdrücke.|  
|[Working with Empty Values (Arbeiten mit leeren Werten)](../mdx/working-with-empty-values.md)|Beschreibt, was ein leerer Wert ist und wie leere Werte gehandhabt werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Sprachreferenz &#40;MDX&#41;](../mdx/mdx-language-reference-mdx.md)   
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
