---
title: Spaltenverteilungen [Datamining] | Microsoft-Dokumentation
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83da6c1ba0a278d2d6b80f309a7bc7f6a1688ba4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62724991"
---
# <a name="column-distributions-data-mining"></a>Spaltenverteilungen [Data Mining]
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]können Sie Spaltenverteilungen in einer Miningstruktur definieren, um zu beeinflussen, wie Algorithmen die Daten in diesen Spalten verarbeiten, wenn Sie Miningmodelle erstellen. Für einige Algorithmen ist es hilfreich, vor dem Verarbeiten des Modells für jede kontinuierliche Spalte die Verteilung zu definieren, wenn für die Spalten bekannt ist, dass sie normal verteilte Werte enthalten. Wenn Sie die Verteilungen nicht definieren, liefern die sich ergebenden Miningmodelle möglicherweise ungenauere Vorhersagen, da die Algorithmen weniger Informationen zum Interpretieren der Daten haben.  
  
 Die in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbaren Algorithmen unterstützen folgende Verteilungstypen:  
  
 **Normal**  
 Die Werte für die kontinuierliche Spalte bilden ein Histogramm, das einer Normalverteilung folgt.  
  
 ![Histogramm mit normalverteilung](../../analysis-services/data-mining/media/normal-distribution.gif "Histogramm mit normalverteilung")  
  
 **Log Normal**  
 Die Werte für die kontinuierliche Spalte bilden ein Histogramm, in dem die Kurve am oberen Ende einen gedehnten Verlauf und am unteren Ende  einen Schrägverlauf aufweist.  
  
 ![Histogramm mit protokollnormalverteilung](../../analysis-services/data-mining/media/log-normal-distribution.gif "Histogramm mit protokollnormalverteilung")  
  
 **Uniform**  
 Die Werte für die kontinuierliche Spalte bilden eine flache Kurve, in der alle Werte gleich wahrscheinlich sind.  
  
 ![Histogramm mit gleichverteilung](../../analysis-services/data-mining/media/uniform-distribution.gif "Histogramm mit gleichverteilung")  
  
 Weitere Informationen zu den von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitgestellten Algorithmen finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Inhaltstypen &#40;Data Mining&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Diskretisierungsmethoden &#40;Data Mining&#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md)   
 [Verteilungen &#40;DMX&#41;](../../dmx/distributions-dmx.md)   
 [Miningstrukturspalten](../../analysis-services/data-mining/mining-structure-columns.md)  
  
  
