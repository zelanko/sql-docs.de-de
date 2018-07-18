---
title: Grundlegendes zu MDX-Abfragen (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- statements [MDX]
- Multidimensional Expressions [Analysis Services], statements
- Multidimensional Expressions [Analysis Services], queries
- MDX [Analysis Services], statements
- MDX queries [Analysis Services]
- MDX [Analysis Services], queries
- queries [MDX]
ms.assetid: a560383b-bb58-472e-95f5-65d03d8ea08b
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cd81b9489e7b73f9897cd557999df3021e8f9e8d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163413"
---
# <a name="mdx-query-fundamentals-analysis-services"></a>Grundlegendes zu MDX-Abfragen (Analysis Services)
  MDX (Multidimensional Expressions) ermöglicht Ihnen das Abfragen von mehrdimensionalen Objekten (z. B. Cubes) sowie das Zurückgeben von mehrdimensionalen Cellsets, die die Daten des jeweiligen Cubes enthalten. Dieses Thema und die zugehörigen Unterthemen bieten eine Übersicht über MDX-Abfragen.  
  
 In den folgenden Themen werden MDX-Abfragen und die von ihnen erstellten Cellsets beschrieben und detailliertere Informationen zur grundlegenden MDX-Syntax bereitgestellt.  
  
> [!NOTE]  
>  Weitere Informationen zu Leistungsproblemen im Zusammenhang mit MDX-Abfragen und -Berechnungen finden Sie im Abschnitt "Writing Efficient MDX" unter [SQL Server 2005 Analysis Services Performance Guide](http://go.microsoft.com/fwlink/?LinkId=81621)(in Englisch).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Die grundlegende MDX-Abfrage &#40;MDX&#41;](mdx-query-the-basic-query.md)|Stellt grundlegende Syntaxinformationen für die MDX-SELECT-Anweisung bereit.|  
|[Einschränken der Abfrage mit Abfrage- und Slicerachsen &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md)|Beschreibt, was Abfrage- und Slicerachsen sind und wie diese angegeben werden.|  
|[Des Cubekontexts in einer Abfrage &#40;MDX&#41;](establishing-cube-context-in-a-query-mdx.md)|Beschreibt den Zweck, den die FROM-Klausel in einer MDX-SELECT-Anweisung hat.|  
|[Erstellen von benannten Mengen in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)|Beschreibt den Zweck benannter Mengen in MDX sowie die erforderlichen Techniken, um sie zu erstellen und in MDX-Abfragen zu verwenden.|  
|[Erstellen von berechneten Elementen in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)|Stellt Informationen zu berechneten Elementen in MDX bereit, einschließlich der Techniken, um sie zu erstellen und in MDX-Ausdrücken zu verwenden.|  
|[Erstellen von Zellenberechnungen in MDX &#40;MDX&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)|Erläutert den Prozess des Erstellens und Verwendens berechneter Zellen.|  
|[Erstellen und Verwenden von Eigenschaftswerten &#40;MDX&#41;](../../creating-and-using-property-values-mdx.md)|Erläutert das Erstellen und Verwenden der Eigenschaften von Dimensionen, Ebenen, Elementen und Zellen.|  
|[Bearbeiten von Daten &#40;MDX&#41;](mdx-data-manipulation-manipulating-data.md)|Beschreibt die Grundlagen für das Bearbeiten von Daten mit Drillthrough sowie Rollup und beschreibt Durchlaufreihenfolge und Lösungsreihenfolge in MDX.|  
|[Ändern von Daten &#40;MDX&#41;](mdx-data-modification-modifying-data.md)|Beschreibt, wie Rückschreiben verwendet wird, um mehrdimensionale Daten temporär oder dauerhaft zu ändern.|  
|[Verwenden von Variablen und Parameter &#40;MDX&#41;](using-variables-and-parameters-mdx.md)|Beschreibt, wie Variablen und Parameter in MDX-Abfragen verwendet werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Mehrdimensionale Ausdrücke &#40;MDX&#41; Verweis](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
