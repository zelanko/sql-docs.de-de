---
title: Attribute in über-/unterordnungshierarchien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 35521a8f12d3e5c16e63ba883a2b5d561bde4c96
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66073481"
---
# <a name="attributes-in-parent-child-hierarchies"></a>Attribute in über- und untergeordneten Hierarchien
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]erfolgt in der Regel eine allgemeine Annahme über den Inhalt von Elementen in einer Dimension. Blattelemente enthalten Daten, die direkt aus den zugrunde liegenden Datenquellen abgeleitet wurden, Nichtblattelemente enthalten von Aggregationen abgeleitete Daten, die für untergeordnete Elemente ausgeführt wurden.  
  
 In einer Über-/Unterordnungshierarchie können einige Nichtblattelemente jedoch auch Daten enthalten, die von zugrunde liegenden Datenquellen abgeleitet sind, zusätzlich zu den aus untergeordneten Elementen aggregierten Daten. Für diese Nichtblattelemente in einer Über-/Unterordnungshierarchie werden spezielle vom System generierte untergeordnete Elemente erstellt, die die Daten der zugrunde liegenden Faktentabelle enthalten. Sie werden als *Datenelemente*bezeichnet und enthalten einen Wert, der direkt einem Nichtblattelement zugeordnet und unabhängig vom zusammenfassenden Wert ist, der aus den nachfolgenden Elementen des Nichtblattelements berechnet wird.  
  
 Datenelemente sind nur für Dimensionen mit Über-/Unterordnungshierarchien verfügbar und nur dann sichtbar, wenn das übergeordnete Attribut dies zulässt. Sie können den Dimensions-Designer verwenden, um die Sichtbarkeit von Datenelementen zu steuern. Um Datenelemente offen zu legen, setzen Sie die `MembersWithData`-Eigenschaft für das übergeordnete Attribut auf `NonLeafDataVisible.`. Um im übergeordneten Attribut enthaltene Datenelemente auszublenden, setzen Sie die `MembersWithData`-Eigenschaft des übergeordneten Attributs auf `NonLeafDataHidden`.  
  
 Mit dieser Einstellung wird das normale Aggregationsverhalten von Nichtblattelementen nicht überschrieben, denn das Datenelement ist für Aggregationszwecke stets als untergeordnetes Element enthalten. Das normale Aggregationsverhalten kann jedoch durch eine benutzerdefinierte Rollupformel überschrieben werden. Mit der MDX-Funktion (Multidimensional Expressions) [DataMember](/sql/mdx/datamember-mdx) können Sie unabhängig vom Wert der- `MembersWithData` Eigenschaft auf den Wert des zugeordneten Datenmembers zugreifen.  
  
 Die `MembersWithDataCaption`-Eigenschaft des übergeordneten Attributs stellt für [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] die Benennungsvorlage für die Generierung von Elementnamen für Datenelemente bereit.  
  
## <a name="using-data-members"></a>Verwenden von Datenelementen  
 Datenelemente sind hilfreich bei der Aggregation von Measures gemäß der Organisationsdimensionen mit Über-/Unterordnungshierarchien. Das folgende Diagramm zeigt z. B. eine Dimension, die drei Ebenen enthält, die die Bruttoumsätze von Produkten darstellen. Die erste Ebene zeigt die Bruttoumsätze für alle Vertriebsmitarbeiter. Die zweite Ebene enthält die Bruttoumsätze für alle Vertriebsmitarbeiter, nach Vertriebsmanagern sortiert, und die dritte Ebene enthält die Bruttoumsätze für alle Vertriebsmitarbeiter, nach Vertriebsmitarbeitern sortiert.  
  
 ![Gross Sales Volume-Dimension mit drei Ebenen](../media/agdatamember1.gif "Gross Sales Volume-Dimension mit drei Ebenen")  
  
 Normalerweise würde der Wert des Elements Sales Manager 1 durch Aggregieren der Werte der Elemente Salesperson 1 und Salesperson 2 abgeleitet. Da jedoch auch Sales Manager 1 Produkte verkaufen kann, kann dieses Element auch Daten enthalten, die von der Faktentabelle abgeleitet sind, da möglicherweise Bruttoumsätze Sales Manager 1 zugeordnet sind.  
  
 Außerdem können die einzelnen Provisionen für jeden Vertriebsmitarbeiter unterschiedlich sein. In diesem Fall werden zwei unterschiedliche Skalen zum Berechnen der Provisionen für die einzelnen Bruttoumsätze der Vertriebsmanager im Gegensatz zum gesamten Bruttoumsatz ihres Vertriebspersonals verwendet. Deshalb ist die Möglichkeit wichtig, auf die Daten der zugrunde liegenden Faktentabelle für Nicht-Blattelemente zuzugreifen. Die MDX-Funktion `DataMember` kann zum Abrufen der einzelnen Bruttoumsätze des Sales Manager 1-Elements verwendet werden, und ein benutzerdefinierter Rollupausdruck kann verwendet kann, um Datenelemente aus dem aggregierten Wert des Sales Manager 1-Elements auszuschließen, wodurch die Bruttoumsätze der diesem Element zugeordneten Vertriebsmitarbeiter bereitgestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensions Attribut-Eigenschaften Referenz](dimension-attribute-properties-reference.md)   
 [Über-und untergeordnete Hierarchie](parent-child-dimension.md)  
  
  
