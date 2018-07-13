---
title: Abfragen von mehrdimensionalen Daten mit MDX | Microsoft-Dokumentation
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
- multidimensional data [Analysis Services], querying
ms.assetid: e0a5dd60-35a3-4a4f-b36f-52ecea814886
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4227c7a2483035c7fdf5ae472711ad0ea96c73bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37212300"
---
# <a name="querying-multidimensional-data-with-mdx"></a>Abfragen von mehrdimensionalen Daten mit MDX
  MDX (Multidimensional Expressions) ist eine Abfragesprache zum Verwenden und Abrufen von mehrdimensionalen Daten in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. MDX basiert auf der XMLA-Spezifikation (XML for Analysis) und verfügt über spezielle Erweiterungen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. MDX verwendet Ausdrücke bestehend aus Bezeichnern, Werten, Anweisungen, Funktionen und Operatoren, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] zum Abrufen von Objekten (z. B. einer Menge oder einem Element) oder Skalarwerten (z. B. einer Zeichenfolge oder einer Zahl) auswerten kann.  
  
 MDX-Abfragen und -Ausdrücke werden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] für folgende Zwecke verwendet:  
  
-   Zurückgeben von Daten aus einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Cube an eine Clientanwendung  
  
-   Formatieren von Abfrageergebnissen  
  
-   Ausführen von Cube-Entwurfsaufgaben, wie z. B. Definieren von berechneten Elementen, benannten Mengen, Zuweisungen mit definiertem Bereich oder Key Performance Indicators (KPI)  
  
-   Ausführen von Verwaltungsaufgaben, wie z. B. Dimensions- und Zellensicherheit  
  
 Die MDX-Syntax ist, oberflächlich betrachtet, der SQL-Syntax sehr ähnlich, die normalerweise bei relationalen Datenbanken verwendet wird. MDX ist jedoch keine Erweiterung von SQL und unterscheidet sich in vielerlei Hinsicht von SQL. Um MDX-Ausdrücke zum Entwerfen bzw. Sichern von Cubes oder MDX-Abfragen zum Zurückgeben und Formatieren von mehrdimensionalen Daten erstellen zu können, müssen Sie die grundlegenden Konzepte von MDX und der Dimensionsmodellierung, die MDX-Syntaxelemente, MDX-Operatoren, MDX-Anweisungen sowie MDX-Funktionen verstehen.  
  
> [!NOTE]  
>  Weitere Informationen finden Sie unter den im Abschnitt Additional Resources auf der [SQL Server 2005 – Analysis Services](http://go.microsoft.com/fwlink/?LinkId=80853) Seite auf der Website der Microsoft TechNet-Website. Weitere Informationen zu Leistungsproblemen im Zusammenhang mit MDX-Abfragen und -Berechnungen finden Sie im Abschnitt "Writing Efficient MDX" unter [SQL Server 2005 Analysis Services Performance Guide](http://go.microsoft.com/fwlink/?LinkId=81621)(in Englisch).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Grundlegende Konzepte in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md)|Mithilfe von MDX (Multidimensional Expressions) können Sie mehrdimensionale Daten abfragen oder MDX-Ausdrücke zur Verwendung innerhalb eines Cubes erstellen. Voraussetzung dafür ist jedoch, dass Sie über Grundkenntnisse der Dimensionskonzepte und Terminologie von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verfügen.|  
|[Grundlegendes zu MDX-Abfrage &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)|MDX (Multidimensional Expressions) ermöglicht Ihnen das Abfragen von mehrdimensionalen Objekten (z. B. Cubes) sowie das Zurückgeben von mehrdimensionalen Cellsets, die die Daten des jeweiligen Cubes enthalten. Dieses Thema und die zugehörigen Unterthemen bieten eine Übersicht über MDX-Abfragen.|  
|[MDX-Skripts Grundlagen &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)|In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]besteht ein MDX-Skript (Multidimensional Expressions) aus einem oder mehreren MDX-Ausdrücken oder -Anweisungen, die einen Cube mit Berechnungen auffüllen.<br /><br /> In einem MDX-Skript wird der Berechnungsprozess für einen Cube definiert. Ein MDX-Skript wird auch als Teil des Cubes selbst angesehen. Daher bewirkt ein Ändern eines MDX-Skripts, das einem Cube zugeordnet ist, dass der Berechnungsprozess für den Cube sofort geändert wird.<br /><br /> Um MDX-Skripts zu erstellen, können Sie den Cube-Designer in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Syntaxelemente &#40;MDX&#41;](/sql/mdx/mdx-syntax-elements-mdx)   
 [MDX-Sprachreferenz &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx)  
  
  
