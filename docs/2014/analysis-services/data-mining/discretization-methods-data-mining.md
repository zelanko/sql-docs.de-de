---
title: Diskretisierungsmethoden (Datamining) | Microsoft Docs
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
- content types [data mining]
- discretization [Analysis Services]
- columns [data mining], discretization
- THRESHOLDS method
- CLUSTERS method
- DiscretizationBuckets property
- AUTOMATIC method
- EQUAL_AREAS method
- coding [Data Mining]
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c2cedf4996536560ff415746c7948cc62a86de77
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160536"
---
# <a name="discretization-methods-data-mining"></a>Diskretisierungsmethoden (Data Mining)
  Einige Algorithmen, die verwendet werden, um Data Mining-Modelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zu erstellen, benötigen bestimmte Inhaltstypen, um richtig zu funktionieren. Beispielsweise kann der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes-Algorithmus kontinuierliche Spalten nicht als Eingabe verwenden und keine kontinuierlichen Werte vorhersagen. Außerdem können einige Spalten so viele Werte enthalten, dass der Algorithmus interessante Muster in Daten, aus denen ein Modell erstellt wird, nur schwer identifizieren kann.  
  
 In diesen Fällen können Sie die Daten in den Spalten diskretisieren, sodass Sie die Algorithmen verwenden können, um ein Miningmodell zu erstellen. Unter*Diskretisierung* wird der Prozess verstanden, Werte in Buckets zu platzieren, sodass sich eine begrenzte Anzahl an möglichen Statuswerten ergibt. Die Buckets selbst werden als sortierte und diskrete Werte behandelt. Sie können sowohl numerische als auch Zeichenfolgenspalten diskretisieren.  
  
 Es gibt verschiedene Methoden für das Diskretisieren von Daten. Wenn Ihre Data Mining-Projektmappe relationale Daten verwendet, können Sie die Anzahl der Buckets für das Gruppieren von Daten steuern, indem Sie den Wert der <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> -Eigenschaft festlegen. Die Standardanzahl von Buckets beträgt 5.  
  
 Wenn Ihre Data Mining-Projektmappe Daten aus einem OLAP-Cube (Online Analytical Processing, Analytische Onlineverarbeitung) verwendet, berechnet der Data Mining-Algorithmus automatisch die Anzahl der zu erzeugenden Buckets, indem er die folgende Gleichung verwendet. Dabei steht „n“ für die Anzahl unterschiedlicher Werte in der Spalte:  
  
 `Number of Buckets = sqrt(n)`  
  
 Wenn Sie nicht möchten, dass [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Anzahl von Buckets berechnet, können Sie die <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> -Eigenschaft verwenden, um die Anzahl von Buckets manuell zu bestimmen.  
  
 Die folgende Tabelle beschreibt die Methoden, mit denen Sie Daten in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]diskretisieren können.  
  
|Diskretisierungsmethode|Description|  
|---------------------------|-----------------|  
|`AUTOMATIC`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bestimmt, welche Diskretisierungsmethode verwendet werden muss.|  
|`CLUSTERS`|Der Algorithmus unterteilt die Daten in Gruppen, indem er Stichproben der Schulungsdaten nimmt, diese als Initialisierungswerte eine Reihe von zufällig gewählten Punkten verwendet und anschließend mehrere Iterationen des Microsoft Clustering-Algorithmus anhand der Expectation-Maximization (EM)-Clusteringmethode ausführt. Die `CLUSTERS`-Methode ist von Vorteil, da sie für jede Verteilungskurve verwendet werden kann. Allerdings ist sie zeitaufwändiger als andere Diskretisierungsmethoden.<br /><br /> Diese Methode kann nur für numerische Spalten verwendet werden.|  
|`EQUAL_AREAS`|Der Algorithmus teilt die Daten in Gruppen auf, die die gleiche Anzahl von Werten enthalten. Diese Methode eignet sich vor allem für Normalverteilungskurven, jedoch nicht in Fällen, bei denen die Verteilung viele Werte umfasst, die sich in einer engen Gruppe der kontinuierlichen Daten befinden. Wenn beispielsweise die Hälfte der Artikel einen Kostenwert von "0" aufweisen, befindet sich die Hälfte der Daten unterhalb eines einzigen Punktes der Kurve. In einer solchen Verteilung trennt diese Methode die Daten, um gleiche Diskretisierungen in verschiedenen Bereichen zu erstellen. Dadurch wird eine ungenaue Darstellung der Daten erzeugt.|  
  
## <a name="remarks"></a>Hinweise  
  
-   Sie können die `EQUAL_AREAS` Methode, um Strings zu diskretisieren.  
  
-   Die `CLUSTERS` Methode verwendet eine zufällige Stichprobe von 1000 Datensätzen, um Daten zu diskretisieren. Verwenden Sie die `EQUAL_AREAS`-Methode, wenn Sie nicht möchten, dass der Algorithmus Stichproben von Daten nimmt.  
  
-   Das Lernprogramm für das Miningmodell für neurale Netzwerke bietet ein Beispiel dafür, wie Diskretisierung angepasst werden kann. Weitere Informationen finden Sie unter [Lektion 5: Erstellen von neuronalen Netzwerk- und logistischen Regressionsmodellen &#40;Mining-Lernprogramm für fortgeschrittene Data&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Inhaltstypen &#40;Datamining&#41;](content-types-data-mining.md)   
 [Inhaltstypen &#40;DMX&#41;](/sql/dmx/content-types-dmx)   
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningstrukturen &#40;Analysis Services – Datamining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Datentypen &#40;Datamining&#41;](data-types-data-mining.md)   
 [Miningstrukturspalten](mining-structure-columns.md)   
 [Spaltenverteilungen &#40;Datamining&#41;](column-distributions-data-mining.md)  
  
  
