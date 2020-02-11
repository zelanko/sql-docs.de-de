---
title: 'Lektion 2: Erstellung eines Vorhersage Szenarios (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ee814dc0891e70dfeccf2b96383d1d7b5c324aa8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62931528"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Lektion 2: Erstellen eines Planungserstellungsszenarios (Data Mining-Lernprogramm für Fortgeschrittene)
  Als Sales Analyst für [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]wurden Sie aufgefordert, den Verkauf von Produkten für das nächste Jahr zu prognostizieren. Sie wurden insbesondere angehalten, Prognosen für unterschiedliche Regionen und Produktlinien zu vergleichen. Darüber hinaus sollen Sie feststellen, ob der Verkauf verschiedener Produkte je nach Jahreszeit Schwankungen unterliegt.  
  
 In dieser Lektion fassen Sie die Vertriebsdaten des Unternehmens auf monatlicher Basis zusammen, um die angeforderten Informationen zu finden. Darüber hinaus unterteilen Sie die Verkaufszahlen in drei Regionen: Europa, Nordamerika und Pazifischer Raum.  
  
 Wenn Sie die Aufgaben in dieser Lektion ausgeführt haben, können Sie folgende Fragen beantworten:  
  
-   Welchen Schwankungen ist der Verkauf unterschiedlicher Fahrradmodelle im Laufe der Zeit unterworfen?  
  
-   Gibt es Unterschiede zwischen den Verkaufsmustern in den drei Regionen?  
  
-   Können wir vorhersagen, zu welchem Zeitpunkt die meisten Verkäufe stattfinden?  
  
 Die Lektion kann in zwei Teilen durchgeführt werden:  
  
-   Der erste Teil bietet eine Einführung in die Grundlagen der Erstellung und Verwendung eines Zeitreihenmodells.  
  
-   Im zweiten Teil wird die Erstellung eines allgemeinen Zeitreihenmodells erläutert, das auf allen Regionen basiert. Dieses allgemeine Modell kann für *Kreuzvorhersagen*verwendet werden.  
  
 Zum Durchführen der Aufgaben in dieser Lektion, die unten aufgelistet sind, verwenden Sie die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenquelle, die Sie in [Lektion 1: Erstellen der Data Mining ](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)-Data Mining-Projekt Mappe &#40;Data Mining-Lernprogramm für fortgeschrittene erstellt haben&#41;.  
  
> [!WARNING]  
>  Die Datumsangaben in der [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] -Beispieldatenbank wurden für diese Version aktualisiert. Wenn Sie eine frühere Version von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]verwenden, können Sie das Modell anhand der folgenden Schritte erstellen, die angezeigten Ergebnisse weichen jedoch möglicherweise ab.  
  
 **Erstellen eines einfachen Planungserstellungsmodells**  
  
-   [Hinzufügen einer Datenquellen Sicht für Vorhersage &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen einer Planungsstruktur und eines Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Ändern der Planungsstruktur &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [Anpassen und Verarbeiten des Vorhersagemodells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Untersuchen des Planungs Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen von Zeitreihen Vorhersagen &#40;Data Mining-Tutorial für fortgeschrittene&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 **Erstellen eines allgemeinen Planungserstellungsmodells für Kreuzvorhersagen**  
  
-   [Erweiterte Zeitreihen Vorhersagen &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [Zeitreihen Vorhersagen mit aktualisierten Data &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [Zeitreihen Vorhersagen mit Ersetzungs Daten &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [Vergleichen von Vorhersagen für Prognosemodelle &#40;Data&#41;Mining-Lernprogramm für Fortgeschrittene](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Hinzufügen einer Datenquellen Sicht für Vorhersage &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [Grundlegendes zu den Anforderungen für ein Zeitreihen Modell &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Alle Lektionen  
 [Lektion 1: Erstellen der Data Mining-Lösung für fortgeschrittene &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 Lektion 2: Planungserstellungsszenario (Data Mining-Tutorial für Fortgeschrittene)  
  
 [Lektion 3: aufbauen eines Market Basket-Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lektion 4: Entwickeln eines Sequence Clustering-Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Lektion 5: aufbauen von neuronalen Netzwerk-und logistischen Regressionsmodellen &#40;Data&#41;Mining-Lernprogramms](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services-Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
