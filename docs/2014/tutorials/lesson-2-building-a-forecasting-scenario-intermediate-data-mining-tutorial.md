---
title: 'Lektion 2: Erstellen eines Planungserstellungsszenarios (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62931528"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a>Lektion 2: Erstellen eines Planungserstellungsszenarios (Datamining-Lernprogramm für fortgeschrittene)
  Als Sales Analyst für [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]wurden Sie aufgefordert, den Verkauf von Produkten für das nächste Jahr zu prognostizieren. Sie wurden insbesondere angehalten, Prognosen für unterschiedliche Regionen und Produktlinien zu vergleichen. Darüber hinaus sollen Sie feststellen, ob der Verkauf verschiedener Produkte je nach Jahreszeit Schwankungen unterliegt.  
  
 Um die angeforderten Informationen zu suchen, die in dieser Lektion werden Sie zusammengefasst, die Daten des Unternehmens sales auf monatlicher Basis aus, und Sie darüber hinaus Verkaufszahlen in drei Regionen unterteilen: Europa, Nordamerika und pazifischer Raum.  
  
 Wenn Sie die Aufgaben in dieser Lektion ausgeführt haben, können Sie folgende Fragen beantworten:  
  
-   Welchen Schwankungen ist der Verkauf unterschiedlicher Fahrradmodelle im Laufe der Zeit unterworfen?  
  
-   Gibt es Unterschiede zwischen den Verkaufsmustern in den drei Regionen?  
  
-   Können wir vorhersagen, zu welchem Zeitpunkt die meisten Verkäufe stattfinden?  
  
 Die Lektion kann in zwei Teilen durchgeführt werden:  
  
-   Der erste Teil bietet eine Einführung in die Grundlagen der Erstellung und Verwendung eines Zeitreihenmodells.  
  
-   Im zweiten Teil wird die Erstellung eines allgemeinen Zeitreihenmodells erläutert, das auf allen Regionen basiert. Dieses allgemeine Modell kann für *Kreuzvorhersagen*verwendet werden.  
  
 Um die Aufgaben in dieser Lektion die unten aufgeführt sind, verwenden Sie die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] Datenquelle, die Sie im erstellten [Lektion 1: Erstellen der mittleres Datamining-Lösung &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).  
  
> [!WARNING]  
>  Die Datumsangaben in der [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] -Beispieldatenbank wurden für diese Version aktualisiert. Wenn Sie eine frühere Version von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]verwenden, können Sie das Modell anhand der folgenden Schritte erstellen, die angezeigten Ergebnisse weichen jedoch möglicherweise ab.  
  
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
  
 Lektion 2: Planungserstellungsszenario (Datamining-Lernprogramm für fortgeschrittene)  
  
 [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lektion 4: Erstellen eines Sequenzclusterszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [Lesson 5: Erstellen von neuronalen Netzwerk- und logistischen Regressionsmodellen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramm zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Datamining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
