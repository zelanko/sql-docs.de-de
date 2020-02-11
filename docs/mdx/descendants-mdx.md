---
title: Descendants (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2a981595c19c321ab498fe9eb65b8570eb17f3ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67999987"
---
# <a name="descendants-mdx"></a>Descendants (MDX)


  Gibt eine Menge von nachfolgenden Werten eines Elements auf einer angegebenen Ebene oder in einem angegebenen Abstand zurück. Optional können nachfolgende Werte anderer Ebenen ein- oder ausgeschlossen werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member expression syntax using a level expression  
Descendants(Member_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Member_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
Set expression syntax using a level expression  
Descendants(Set_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Set_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Level_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Ebene zurückgibt.  
  
 *Flüge*  
 Ein gültiger numerischer Ausdruck, der den Abstand vom angegebenen Element angibt.  
  
 *Desc_Flag*  
 Ein gültiger Zeichenfolgenausdruck, der ein Beschreibungs-Flag zur Unterscheidung möglicher Mengen von nachfolgenden Werten angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Ebene angegeben wird, gibt die **Descendants** -Funktion eine Menge zurück, die die nachfolgenden Elemente des angegebenen Elements oder die Elemente der angegebenen Menge auf einer angegebenen Ebene enthält, optional mit einem in *Desc_Flag*angegebenen Flag geändert werden.  
  
 Wenn *Distance* angegeben wird, gibt die **Descendants** -Funktion eine Menge zurück, die die nachfolgenden Elemente des angegebenen Elements oder die Elemente der angegebenen Menge enthält, die die angegebene Anzahl von Ebenen in der Hierarchie des angegebenen Elements enthalten, optional durch ein in *Desc_Flag*angegebenes Flag geändert werden. Das Distance-Argument dieser Funktion wird in der Regel bei unregelmäßigen Hierarchien verwendet. Wenn der angegebene Abstand null (0) ist, gibt die Funktion eine Menge zurück, die nur das angegebene Element oder die angegebene Menge enthält.  
  
 Wenn ein Mengen Ausdruck angegeben ist, wird die **Descendants** -Funktion für jedes Element der Menge einzeln aufgelöst, und die Gruppe wird erneut erstellt. Anders ausgedrückt: die Syntax, die für die **Descendants** -Funktion verwendet wird, ist funktional äquivalent zur MDX-Funktion [Generate](../mdx/generate-mdx.md) .  
  
 Wenn keine Ebene oder kein Abstand angegeben wird, wird der Standardwert für die von der Funktion verwendete Ebene durch Aufrufen der [Ebenenfunktion](../mdx/level-mdx.md) ( \<<Member>> bestimmt. Level) für das angegebene Element (wenn ein Element angegeben ist) oder durch Aufrufen der **Ebenenfunktion** für jedes Element der angegebenen Menge (sofern eine Menge angegeben ist). Wenn kein Ebenenausdruck, Abstand oder Flag angegeben ist, wird die Funktion ausgeführt, als wenn die folgende Syntax verwendet würde:  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Member_Expression.Level ,`  
  
 `SELF_BEFORE_AFTER`  
  
 `)`  
  
 Wenn eine Ebene und kein Beschreibungs-Flag angegeben ist, wird die Funktion ausgeführt, als wenn die folgende Syntax verwendet würde:  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Level_Expression,`  
  
 `SELF`  
  
 `)`  
  
 Durch Ändern des Wertes des Beschreibungs-Flags können Sie nachfolgende Elemente in der angegebenen Ebene bzw. dem angegebenen Abstand, untergeordnete Elemente vor und nach der angegebenen Ebene bzw. dem angegebenen Abstand (bis zum Blattknoten) sowie die untergeordneten Blattelemente unabhängig von der angegebenen Ebene bzw. dem angegebenen Abstand ein- oder ausschließen. In der folgenden Tabelle werden die im *Desc_Flag* -Argument zulässigen Flags beschrieben.  
  
|Flag|BESCHREIBUNG|  
|----------|-----------------|  
|SELF|Gibt nur nachfolgende Elemente auf der angegebenen Ebene oder in dem angegebenen Abstand zurück. Die Funktion schließt das angegebene Element ein, wenn es sich bei der angegebenen Ebene um die Ebene des angegebenen Elements handelt.|  
|AFTER|Gibt nachfolgende Elemente aus allen Ebenen zurück, die der angegebenen Ebene oder dem angegebenen Abstand untergeordnet sind.|  
|BEFORE|Gibt nachfolgende Elemente aus allen Ebenen zwischen dem angegebenen Element und der angegebenen Ebene oder im angegebenen Abstand zurück. Sie enthält den angegebenen Member, enthält jedoch keine Elemente aus der angegebenen Ebene oder Entfernung.|  
|BEFORE_AND_AFTER|Gibt nachfolgende Elemente aus allen Ebenen zurück, die der Ebene des angegebenen Elements untergeordnet sind. Das angegebene Element wird eingeschlossen, jedoch nicht Elemente der angegebenen Ebene oder im angegebenen Abstand.|  
|SELF_AND_AFTER|Gibt nachfolgende Elemente aus der angegebenen Ebene oder im angegebenen Abstand sowie alle Ebenen, die der angegebenen Ebene oder dem angegebenen Abstand untergeordnet sind, zurück.|  
|SELF_AND_BEFORE|Gibt nachfolgende Elemente aus der angegebenen Ebene oder im angegebenen Abstand sowie aus allen Ebenen zwischen dem angegebenen Element und der angegebenen Ebene oder im angegebenen Abstand, einschließlich des angegebenen Elements, zurück.|  
|SELF_BEFORE_AFTER|Gibt nachfolgende Elemente aus allen Ebenen zurück, die der Ebene des angegebenen Elements untergeordnet sind, sowie das angegebene Element selbst.|  
|LEAVES|Gibt nachfolgende Blattelemente zwischen dem angegebenen Element und der angegebenen Ebene oder im angegebenen Abstand zurück.|  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden das angegebene Element (United States), die Elemente zwischen dem angegebenen Element (United States) und den Elementen der Ebene vor der angegebenen Ebene (City) zurückgegeben. Im Beispiel werden das angegebene Element selbst (United States) und die Elemente der State-Province-Ebene (die Ebene vor der City-Ebene) zurückgegeben. Die Argumente in diesem Beispiel sind kommentiert, um Ihnen das Testen dieser Funktion mit anderen Argumenten zu erleichtern.  
  
```  
SELECT Descendants  
   ([Geography].[Geography].[Country].&[United States]  
      //, [Geography].[Geography].[Country]  
   , [Geography].[Geography].[City]  
      //, [Geography].[Geography].Levels (3)  
      //, SELF   
      //, AFTER  
      , BEFORE  
      // BEFORE_AND_AFTER  
      //, SELF_AND_AFTER  
      //, SELF_AND_BEFORE  
      //,SELF_BEFORE_AFTER  
      //,LEAVES   
   ) ON 0  
FROM [Adventure Works]   
```  
  
 Im folgenden Beispiel wird der tägliche Durchschnitt des `Measures.[Gross Profit Margin]` Measures zurückgegeben, der über die Tage jedes Monats im 2003-Geschäftsjahr aus dem **Adventure Works** -Cube berechnet wird. Die **Descendants** -Funktion gibt eine Menge von Tagen zurück, die vom aktuellen Element `[Date].[Fiscal]` der Hierarchie bestimmt werden.  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS Avg  
   (  
      Descendants( [Date].[Fiscal].CurrentMember,   
           [Date].[Fiscal].[Date]  
          ),   
        Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
   [Date].[Fiscal].[Month].Members ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Fiscal Year].&[2003])  
```  
  
 Im folgenden Beispiel wird ein Ebenenausdruck verwendet und der Internet Sales Amount für alle Bundesstaaten in Australien zurückgegeben, und es wird der Prozentsatz des gesamten Internet Sales Amount für Australien für jede Bundesland-Provinz zurückgegeben. In diesem Beispiel wird die Item-Funktion verwendet, um das erste (und einzige) Tupel aus der von der Vorgänger **Funktion zurück** gegebenen Menge zu extrahieren.  
  
```  
WITH MEMBER Measures.x AS   
   [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],  
      Ancestors   
         ( [Customer].[Customer Geography].CurrentMember,   
           [Customer].[Customer Geography].[Country]  
         ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],   
     [Customer].[Customer Geography].[State-Province], SELF   
   )    
} ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
