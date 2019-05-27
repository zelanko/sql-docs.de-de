---
title: Verwenden von Elementeigenschaften (MDX) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DIMENSION PROPERTIES keyword
- Properties function
- member properties [MDX]
- members [MDX], properties
ms.assetid: 26b5ad08-3799-4a5e-89f3-dca25e637d45
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8c0326d45af68db966f120fa12e35eb59f30becc
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66074161"
---
# <a name="using-member-properties-mdx"></a>Verwenden von Elementeigenschaften (MDX)
  Elementeigenschaften enthalten die grundlegenden Informationen zu jedem Element in jedem Tupel. Zu den grundlegenden Informationen gehören der Elementname, die übergeordnete Ebene, die Anzahl der untergeordneten Elemente usw. Elementeigenschaften sind für alle Elemente auf der jeweiligen Ebene verfügbar. Organisatorisch werden Elementeigenschaften als in Dimensionen organisierte Daten behandelt, die in einer einzigen Dimension gespeichert werden.  
  
> [!NOTE]  
>  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]werden Elementeigenschaften als Attributbeziehungen bezeichnet. Weitere Informationen finden Sie unter [Attributbeziehungen](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
 Eine Elementeigenschaft ist entweder *systemintern* oder *benutzerdefiniert*:  
  
 Systeminterne Elementeigenschaften  
 Alle Elemente unterstützen systeminterne Elementeigenschaften, wie z. B. den formatierten Wert eines Elements. Dimensionen und Ebenen stellen dagegen zusätzliche systeminterne dimensions- und ebenenspezifische Elementeigenschaften, wie die ID eines Elements, bereit.  
  
 Weitere Informationen finden Sie unter [Integrierte Elementeigenschaften &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
 Benutzerdefinierte Elementeigenschaften  
 Elemente haben häufig weitere ihnen zugeordnete Eigenschaften. Die Products-Ebene kann z. B. die Eigenschaften SKU (Stock Keeping Unit), SRP (Suggested Retail Price), Weight und Volume für jedes Produkt bieten. Diese Eigenschaften sind keine Elemente, sondern enthalten zusätzliche Informationen zu Elementen auf der Products-Ebene.  
  
 Weitere Informationen finden Sie unter [Benutzerdefinierte Elementeigenschaften &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
 Sowohl systeminterne und benutzerdefinierte Elementeigenschaften können mithilfe des abgerufen werden die `PROPERTIES` Schlüsselwort oder [Eigenschaften](/sql/mdx/properties-mdx) Funktion.  
  
## <a name="using-the-properties-keyword"></a>Verwenden des PROPERTIES-Schlüsselworts  
 Das `PROPERTIES`-Schlüsselwort gibt die Elementeigenschaften an, die für eine bestimmte Achsendimension verwendet werden müssen. Die `PROPERTIES` Schlüsselwort ist verborgen, innerhalb der `<axis specification>` -Klausel der MDX- [wählen](/sql/mdx/mdx-data-manipulation-select) Anweisung:  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
```  
  
 Die `<axis_specification>` -Klausel enthält eine optionale `<dim_props>` -Klausel (siehe folgende Syntax):  
  
```  
<axis_specification> ::= <set> [<dim_props>] ON <axis_name>  
```  
  
> [!NOTE]  
>  Weitere Informationen zu den Werten `<set>` und `<axis_name>` finden Sie unter [Angeben des Inhalts einer Abfrageachse &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
 Die `<dim_props>`-Klausel ermöglicht es Ihnen, mithilfe des `PROPERTIES`-Schlüsselworts Dimensions-, Ebenen- und Elementeigenschaften abzufragen. Nachstehend ist die Syntax der `<dim_props>` -Klausel definiert:  
  
```  
<dim_props> ::= [DIMENSION] PROPERTIES <property> [,<property>...]  
```  
  
 Die Aufteilung der Syntax von `<property>` variiert abhängig davon, welche Eigenschaft abgefragt wird:  
  
-   Bei einer kontextabhängigen systeminternen Elementeigenschaft muss der Name der Dimension oder der Ebene vor der Eigenschaft stehen. Nicht kontextabhängige systeminterne Elementeigenschaften können dagegen nicht durch den Dimensions- oder Ebenennamen qualifiziert werden. Weitere Informationen zur Verwendung der `PROPERTIES` -Schlüsselworts mit systeminternen Elementeigenschaften finden Sie unter [integrierte Elementeigenschaften &#40;MDX&#41;](mdx-member-properties-intrinsic-member-properties.md).  
  
-   Bei einer benutzerdefinierten Elementeigenschaft sollte der Name der Ebene vorangestellt werden, in der sie sich befindet. Weitere Informationen zur Verwendung der `PROPERTIES` -Schlüsselworts mit benutzerdefinierten Elementeigenschaften finden Sie unter [benutzerdefinierte Elementeigenschaften &#40;MDX&#41;](mdx-member-properties-user-defined-member-properties.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Verwenden von Eigenschaftswerten &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md)  
  
  
