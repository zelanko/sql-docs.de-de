---
title: 'Lektion 4: Erstellen eines Sequenzclusterszenarios (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d34125b7b750daa1da25c9e8788172b5d9ca2c35
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62710602"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Lektion 4: Erstellen eines Sequenzclusterszenarios (Datamining-Lernprogramm für fortgeschrittene)
  Die Marketingabteilung von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] möchte verstehen, wie sich Kunden auf der [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] -Website bewegen. Das Unternehmen vermutet, dass es ein Muster für die Reihenfolge gibt, in der Kunden Produkte in ihre Einkaufskörbe legen. Die Reihenfolge der Einkaufssequenzen soll analysiert werden, um zu ermitteln, wie Kunden ihren Einkaufskörben zugehörige Elemente hinzufügen. Anhand dieser Informationen kann die Website dann so angepasst werden, dass Kunden angeregt werden, weitere Produkte zu kaufen.  
  
 Wenn Sie die Aufgaben in dieser Lektion ausgeführt haben, haben Sie ein Miningmodell erstellt, mit dem Sie, durch die Anwendung des [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus, das nächste Element vorhersagen können, das Kunden in ihren Einkaufskorb legen. Sie werden zwei Versionen des Modells ausprobieren: Eine analysiert nur die Reihenfolge der Produkte, während die andere einige zusätzliche demografische Kundendaten zum Clustering enthält. Abschließend werden Sie anhand der Modelle Vorhersagen erstellen, mit denen Sie Kunden bestimmte Produkte empfehlen können.  
  
 Zum Ausführen der Aufgaben in der Lektion verwenden Sie die Market Basket-Miningstruktur, die Sie in erstellt [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md). Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Erstellen einer Sequence Clustering-Miningmodellstruktur &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Verarbeiten des Sequenzclustermodells](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Prüfen der Sequence Clustering-Modell &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen ein Clustermodells für verwandte Sequenzen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen von Vorhersagen für ein Sequenzclustermodell &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen einer Sequence Clustering-Miningmodellstruktur &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Alle Lektionen  
 [Lektion 1: Erstellen der mittleres Datamining-Lösung &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Lektion 2: Erstellen eines Planungserstellungsszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Lektion 4: Sequenzclusterszenarios (Datamining-Lernprogramm für fortgeschrittene)  
  
 [Lesson 5: Erstellen von neuronalen Netzwerk- und logistischen Regressionsmodellen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramm zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Datamining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
