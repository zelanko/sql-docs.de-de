---
title: Benutzerdefinierte Elementeigenschaften (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ba34243609b796eef635fc3b55cd99ef4f225638
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050410"
---
# <a name="user-defined-member-properties-mdx"></a>Benutzerdefinierte Elementeigenschaften (MDX)
  Benutzerdefinierte Elementeigenschaften können einer bestimmten benannten Ebene in einer Dimension als Attributbeziehungen hinzugefügt werden. Benutzerdefinierte Elementeigenschaften können nicht hinzugefügt werden, um die `(All)` Ebene einer Hierarchie oder der Hierarchie selbst.  
  
## <a name="creating-user-defined-member-properties"></a>Erstellen von benutzerdefinierten Elementeigenschaften  
 Benutzerdefinierte Elementeigenschaften können serverbasierten Dimensionen oder Cubes entweder über die Benutzeroberfläche oder programmgesteuert hinzugefügt werden.  
  
-   Um benutzerdefinierte Elementeigenschaften über die Benutzeroberfläche hinzuzufügen, verwenden Sie den Dimensions-Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Weitere Informationen finden Sie unter [Definieren von Attributbeziehungen](../attribute-relationships-define.md).  
  
-   Um benutzerdefinierte Elementeigenschaften programmgesteuert hinzuzufügen, kann Ihre Anwendung entweder Analysis Management Objects (AMO) oder eine Kombination aus XMLA (XML for Analysis) und ASSL (Analysis Services Scripting Language) verwenden. Weitere Informationen finden Sie unter [Attributbeziehungen](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Abrufen von benutzerdefinierten Elementeigenschaften  
 Sie können entweder eine benutzerdefinierte Elementeigenschaften Abrufen der `PROPERTIES` Schlüsselwort oder der [Eigenschaften](/sql/mdx/properties-mdx) Funktion.  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Verwenden des PROPERTIES-Schlüsselworts zum Abrufen von benutzerdefinierten Elementeigenschaften  
 Die Syntax für das Abrufen von benutzerdefinierten Elementeigenschaften gleicht der Syntax, mit der systeminterne Eigenschaften von Ebenenelementen abgerufen werden. Die folgende Syntax verdeutlicht dies:  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 Die `PROPERTIES` -Schlüsselwort steht hinter dem Mengenausdruck der Achsenspezifikation. Z. B. die folgende MDX-Abfrage die `PROPERTIES` Schlüsselwort ruft die `List Price` und `Dealer Price` benutzerdefinierte Elementeigenschaften und wird angezeigt, nachdem der Mengenausdruck, der die Produkte identifiziert im Januar verkauften:  
  
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
 Für das Zugreifen auf benutzerdefinierte Elementeigenschaften kann auch die `Properties`-Funktion verwendet werden. Die folgende MDX-Abfrage verwendet beispielsweise die `WITH` Schlüsselwort, um ein berechnetes Element besteht erstellen die `List Price` Elementeigenschaft:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Elementeigenschaften &#40;MDX&#41;](mdx-member-properties.md)   
 [Eigenschaften &#40;MDX&#41;](/sql/mdx/properties-mdx)  
  
  
