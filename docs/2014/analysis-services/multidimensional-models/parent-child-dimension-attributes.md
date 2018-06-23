---
title: Attribute in über-/ Unterordnungshierarchien | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data members [Analysis Services]
- nonleaf members
- MembersWithDataCaption property
- members [Analysis Services]
- members [Analysis Services], data
- leaf members
- parent-child dimensions [Analysis Services]
- MembersWithData property
ms.assetid: 249971cc-4bcd-44f1-8241-bdacc04d3d38
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 26e8af7c0709faa813b1b4c85345858abe5fc520
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061033"
---
# <a name="attributes-in-parent-child-hierarchies"></a>Attribute in über- und untergeordneten Hierarchien
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]wird im Allgemeinen eine generelle Annahme hinsichtlich des Inhalts von Elementen in einer Dimension vorausgesetzt. Blattelemente enthalten Daten, die direkt aus den zugrunde liegenden Datenquellen abgeleitet wurden, Nichtblattelemente enthalten von Aggregationen abgeleitete Daten, die für untergeordnete Elemente ausgeführt wurden.  
  
 In einer Über-/Unterordnungshierarchie können einige Nichtblattelemente jedoch auch Daten enthalten, die von zugrunde liegenden Datenquellen abgeleitet sind, zusätzlich zu den aus untergeordneten Elementen aggregierten Daten. Für diese Nichtblattelemente in einer Über-/Unterordnungshierarchie werden spezielle vom System generierte untergeordnete Elemente erstellt, die die Daten der zugrunde liegenden Faktentabelle enthalten. Sie werden als *Datenelemente*bezeichnet und enthalten einen Wert, der direkt einem Nichtblattelement zugeordnet und unabhängig vom zusammenfassenden Wert ist, der aus den nachfolgenden Elementen des Nichtblattelements berechnet wird.  
  
 Datenelemente sind nur für Dimensionen mit Über-/Unterordnungshierarchien verfügbar und nur dann sichtbar, wenn das übergeordnete Attribut dies zulässt. Sie können den Dimensions-Designer verwenden, um die Sichtbarkeit von Datenelementen zu steuern. Um Datenelemente offen zu legen, legen Sie die `MembersWithData` -Eigenschaft für das übergeordnete Attribut auf `NonLeafDataVisible.` um das übergeordnete Attribut enthaltene Datenelemente auszublenden, legen die `MembersWithData` Eigenschaft für das übergeordnete Attribut zum `NonLeafDataHidden`.  
  
 Mit dieser Einstellung wird das normale Aggregationsverhalten von Nichtblattelementen nicht überschrieben, denn das Datenelement ist für Aggregationszwecke stets als untergeordnetes Element enthalten. Das normale Aggregationsverhalten kann jedoch durch eine benutzerdefinierte Rollupformel überschrieben werden. Die MDX (Multidimensional Expressions) [DataMember](/sql/mdx/datamember-mdx) Funktion bietet Ihnen die Möglichkeit, den Wert des dazugehörigen Datenelements unabhängig vom Wert für den Zugriff auf die `MembersWithData` Eigenschaft.  
  
 Die `MembersWithDataCaption` Eigenschaft des übergeordneten Attributs stellt [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mit der Vorlage zur ebenenbenennung zum Generieren von Elementnamen für Datenelemente verwendet.  
  
## <a name="using-data-members"></a>Verwenden von Datenelementen  
 Datenelemente sind hilfreich bei der Aggregation von Measures gemäß der Organisationsdimensionen mit Über-/Unterordnungshierarchien. Das folgende Diagramm zeigt z. B. eine Dimension, die drei Ebenen enthält, die die Bruttoumsätze von Produkten darstellen. Die erste Ebene zeigt die Bruttoumsätze für alle Vertriebsmitarbeiter. Die zweite Ebene enthält die Bruttoumsätze für alle Vertriebsmitarbeiter, nach Vertriebsmanagern sortiert, und die dritte Ebene enthält die Bruttoumsätze für alle Vertriebsmitarbeiter, nach Vertriebsmitarbeitern sortiert.  
  
 ![GROSS sales Volume-Dimension mit drei Ebenen](../media/agdatamember1.gif "Gross sales Volume-Dimension mit drei Ebenen")  
  
 Normalerweise würde der Wert des Elements Sales Manager 1 durch Aggregieren der Werte der Elemente Salesperson 1 und Salesperson 2 abgeleitet. Da jedoch auch Sales Manager 1 Produkte verkaufen kann, kann dieses Element auch Daten enthalten, die von der Faktentabelle abgeleitet sind, da möglicherweise Bruttoumsätze Sales Manager 1 zugeordnet sind.  
  
 Außerdem können die einzelnen Provisionen für jeden Vertriebsmitarbeiter unterschiedlich sein. In diesem Fall werden zwei unterschiedliche Skalen zum Berechnen der Provisionen für die einzelnen Bruttoumsätze der Vertriebsmanager im Gegensatz zum gesamten Bruttoumsatz ihres Vertriebspersonals verwendet. Deshalb ist die Möglichkeit wichtig, auf die Daten der zugrunde liegenden Faktentabelle für Nicht-Blattelemente zuzugreifen. Der MDX-Abfrage `DataMember` Funktion kann zum Abrufen der einzelnen Bruttoumsätze des Sales Manager 1-Elements verwendet werden, und ein benutzerdefinierter Rollupausdruck kann verwendet werden, um Datenelemente aus dem aggregierten Wert des Elements Sales Manager 1, bietet der Bruttogewinn auszuschließen. Verkaufsvolumen der diesem Element zugeordneten Vertriebsmitarbeiter bereitgestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsattributeigenschaftenverweis](dimension-attribute-properties-reference.md)   
 [Über-/ Unterordnungshierarchie](parent-child-dimension.md)  
  
  
