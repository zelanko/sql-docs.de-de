---
title: Spalten Verteilungen (Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c7eab32f251b9622c6ac77febf2c004806c024b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78174571"
---
# <a name="column-distributions-data-mining"></a>Spaltenverteilungen [Data Mining]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]können Sie Spalten Verteilungen in einer Mining Struktur definieren, um zu beeinflussen, wie Algorithmen die Daten in diesen Spalten verarbeiten, wenn Sie Mining Modelle erstellen. Für einige Algorithmen ist es hilfreich, vor dem Verarbeiten des Modells für jede kontinuierliche Spalte die Verteilung zu definieren, wenn für die Spalten bekannt ist, dass sie normal verteilte Werte enthalten. Wenn Sie die Verteilungen nicht definieren, liefern die sich ergebenden Miningmodelle möglicherweise ungenauere Vorhersagen, da die Algorithmen weniger Informationen zum Interpretieren der Daten haben.

 Die in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügbaren Algorithmen unterstützen folgende Verteilungstypen:

 `Normal`Die Werte für die kontinuierliche Spalte bilden ein Histogramm mit normaler Verteilung.

 ![Histogramm mit Normalverteilung](../media/normal-distribution.gif "Histogramm mit Normalverteilung")

 `Log Normal`Die Werte für die kontinuierliche Spalte bilden ein Histogramm, in dem die Kurve am oberen Ende gestreckt wird und zum unteren Ende verzerrt wird.

 ![Histogramm mit Protokollnormalverteilung](../media/log-normal-distribution.gif "Histogramm mit Protokollnormalverteilung")

 `Uniform`Die Werte für die kontinuierliche Spalte bilden eine flache Kurve, in der alle Werte gleich wahrscheinlich sind.

 ![Histogramm mit Gleichverteilung](../media/uniform-distribution.gif "Histogramm mit Gleichverteilung")

 Weitere Informationen zu den von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitgestellten Algorithmen finden Sie unter [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).

## <a name="see-also"></a>Weitere Informationen
 [Inhaltstypen &#40;Data Mining-&#41;](content-types-data-mining.md) [Mining Strukturen &#40;Analysis Services-Data Mining-&#41;](mining-structures-analysis-services-data-mining.md) [Diskretisierungsmethoden &#40;Data Mining-&#41;](discretization-methods-data-mining.md) [Verteilungen &#40;DMX-&#41;](/sql/dmx/distributions-dmx) [Mining Struktur Spalten](mining-structure-columns.md)


