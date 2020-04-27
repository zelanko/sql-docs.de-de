---
title: Benutzerdefinierte Element Eigenschaften (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ead5a45bf163ca4e7998c30ab5c83f94cca9075b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074261"
---
# <a name="user-defined-member-properties-mdx"></a>Benutzerdefinierte Elementeigenschaften (MDX)
  Benutzerdefinierte Elementeigenschaften können einer bestimmten benannten Ebene in einer Dimension als Attributbeziehungen hinzugefügt werden. Benutzerdefinierte Elementeigenschaften können weder der `(All)`-Ebene einer Hierarchie noch der Hierarchie selbst hinzugefügt werden.  
  
## <a name="creating-user-defined-member-properties"></a>Erstellen von benutzerdefinierten Elementeigenschaften  
 Benutzerdefinierte Elementeigenschaften können serverbasierten Dimensionen oder Cubes entweder über die Benutzeroberfläche oder programmgesteuert hinzugefügt werden.  
  
-   Um benutzerdefinierte Elementeigenschaften über die Benutzeroberfläche hinzuzufügen, verwenden Sie den Dimensions-Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Weitere Informationen finden Sie unter [Definieren von Attributbeziehungen](../attribute-relationships-define.md).  
  
-   Um benutzerdefinierte Elementeigenschaften programmgesteuert hinzuzufügen, kann Ihre Anwendung entweder Analysis Management Objects (AMO) oder eine Kombination aus XMLA (XML for Analysis) und ASSL (Analysis Services Scripting Language) verwenden. Weitere Informationen finden Sie unter [Attributbeziehungen](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Abrufen von benutzerdefinierten Elementeigenschaften  
 Benutzerdefinierte Element Eigenschaften können mithilfe des `PROPERTIES` -Schlüssel Worts oder der [Properties](/sql/mdx/properties-mdx) -Funktion abgerufen werden.  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Verwenden des PROPERTIES-Schlüsselworts zum Abrufen von benutzerdefinierten Elementeigenschaften  
 Die Syntax für das Abrufen von benutzerdefinierten Elementeigenschaften gleicht der Syntax, mit der systeminterne Eigenschaften von Ebenenelementen abgerufen werden. Die folgende Syntax verdeutlicht dies:  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 Das `PROPERTIES`-Schlüsselwort steht hinter dem Mengenausdruck der Achsenspezifikation. In der folgende MDX-Abfrage ruft das `PROPERTIES`-Schlüsselwort beispielsweise die benutzerdefinierten Elementeigenschaften `List Price` und `Dealer Price` ab und wird nach dem Mengenausdruck angegeben, der die im Januar verkauften Produkte identifiziert.  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>Verwenden der Properties-Funktion zum Abrufen von benutzerdefinierten Elementeigenschaften  
 Für das Zugreifen auf benutzerdefinierte Elementeigenschaften kann auch die `Properties`-Funktion verwendet werden. Die folgende MDX-Abfrage verwendet beispielsweise das `WITH`-Schlüsselwort, um ein berechnetes Element zu erstellen, das aus der `List Price`-Elementeigenschaft besteht:  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 Weitere Informationen zum Erstellen berechneter Elemente finden Sie unter [Erstellen von berechneten Elementen in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Element Eigenschaften &#40;MDX-&#41;](mdx-member-properties.md)   
 [Properties &#40;MDX&#41;](/sql/mdx/properties-mdx)  
  
  
