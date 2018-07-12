---
title: 'Lektion 2: Erstellen eines Planungserstellungsszenarios (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation'
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
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5db75cbdabd62b569c782bd48755ce817819a475
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155501"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Lektion 2: Erstellen eines Planungserstellungsszenarios (Data Mining-Lernprogramm für Fortgeschrittene)
  Als Sales Analyst für [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wurden Sie aufgefordert, den Verkauf von Produkten für das nächste Jahr zu prognostizieren. Sie wurden insbesondere angehalten, Prognosen für unterschiedliche Regionen und Produktlinien zu vergleichen. Darüber hinaus sollen Sie feststellen, ob der Verkauf verschiedener Produkte je nach Jahreszeit Schwankungen unterliegt.  
  
 In dieser Lektion fassen Sie die Vertriebsdaten des Unternehmens auf monatlicher Basis zusammen, um die angeforderten Informationen zu finden. Darüber hinaus unterteilen Sie die Verkaufszahlen in drei Regionen: Europa, Nordamerika und Pazifischer Raum.  
  
 Wenn Sie die Aufgaben in dieser Lektion ausgeführt haben, können Sie folgende Fragen beantworten:  
  
-   Welchen Schwankungen ist der Verkauf unterschiedlicher Fahrradmodelle im Laufe der Zeit unterworfen?  
  
-   Gibt es Unterschiede zwischen den Verkaufsmustern in den drei Regionen?  
  
-   Können wir vorhersagen, zu welchem Zeitpunkt die meisten Verkäufe stattfinden?  
  
 Die Lektion kann in zwei Teilen durchgeführt werden:  
  
-   Der erste Teil bietet eine Einführung in die Grundlagen der Erstellung und Verwendung eines Zeitreihenmodells.  
  
-   Im zweiten Teil wird die Erstellung eines allgemeinen Zeitreihenmodells erläutert, das auf allen Regionen basiert. Dieses allgemeine Modell kann für *Kreuzvorhersagen*verwendet werden.  
  
 Um die Aufgaben in dieser Lektion die unten aufgeführt sind, verwenden Sie die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenquelle, die Sie erstellt [Lektion 1: Erstellen der fortgeschrittene Data Mining-Lösung &#40;Data Mining Tutorial für fortgeschrittene&#41; ](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).  
  
> [!WARNING]  
>  Die Datumsangaben in der [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] -Beispieldatenbank für diese Version aktualisiert wurden. Wenn Sie eine frühere Version von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] verwenden, können Sie das Modell anhand der folgenden Schritte erstellen, die angezeigten Ergebnisse weichen jedoch möglicherweise ab.  
  
 **Erstellen eines einfachen Planungserstellungsmodells**  
  
-   [Hinzufügen einer Datenquellensicht für Vorhersagen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen eine Forecasting-Struktur und das Modell &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Ändern der Planungserstellungsstruktur &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [Anpassen und Verarbeiten des Forecasting-Modells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Untersuchen des Planungserstellungsmodells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen von Zeitreihenvorhersagen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 **Erstellen eines allgemeinen Planungserstellungsmodells für Kreuzvorhersagen**  
  
-   [Erweiterte Zeitreihenvorhersagen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [Zeitreihenvorhersagen mit aktualisierten Daten &#40;fortgeschrittene Data Mining-Lernprogramm&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [Zeitreihenvorhersagen mit Ersetzungsdaten &#40;fortgeschrittene Data Mining-Lernprogramm&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [Vergleichen von Vorhersagen für Forecasting-Modellen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Hinzufügen einer Datenquellensicht für Vorhersagen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [Grundlegendes zu den Anforderungen für ein Zeitreihenmodell &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>Alle Lektionen  
 [Lektion 1: Erstellen der mittleres Datamining-Lösung &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 Lektion 2: Planungserstellungsszenario (Data Mining-Tutorial für Fortgeschrittene)  
  
 [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lektion 4: Erstellen eines Sequenzclusterszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Lektion 5: Erstellen von neuronalen Netzwerk- und logistischen Regressionsmodellen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramm zu Datamining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Datamining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
