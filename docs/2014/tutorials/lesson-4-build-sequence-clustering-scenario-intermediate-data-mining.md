---
title: 'Lektion 4: Entwickeln eines Sequenz Cluster Szenarios (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62710602"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a>Lektion 4: Erstellen eines Sequenzclusterszenarios (Data Mining-Lernprogramm für Fortgeschrittene)
  Die Marketingabteilung von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] möchte verstehen, wie sich Kunden auf der [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] -Website bewegen. Das Unternehmen vermutet, dass es ein Muster für die Reihenfolge gibt, in der Kunden Produkte in ihre Einkaufskörbe legen. Die Reihenfolge der Einkaufssequenzen soll analysiert werden, um zu ermitteln, wie Kunden ihren Einkaufskörben zugehörige Elemente hinzufügen. Anhand dieser Informationen kann die Website dann so angepasst werden, dass Kunden angeregt werden, weitere Produkte zu kaufen.  
  
 Wenn Sie die Aufgaben in dieser Lektion ausgeführt haben, haben Sie ein Miningmodell erstellt, mit dem Sie, durch die Anwendung des [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus, das nächste Element vorhersagen können, das Kunden in ihren Einkaufskorb legen. Sie werden zwei Versionen des Modells ausprobieren: Eine analysiert nur die Reihenfolge der Produkte, während die andere einige zusätzliche demografische Kundendaten zum Clustering enthält. Abschließend werden Sie anhand der Modelle Vorhersagen erstellen, mit denen Sie Kunden bestimmte Produkte empfehlen können.  
  
 Um die Aufgaben in der Lektion abzuschließen, verwenden Sie die Market Basket-Mining Struktur, die Sie in [Lektion 3: Erstellen eines Market Basket-Szenarios &#40;Data Mining ](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)-Lernprogramm für fortgeschrittene erstellt haben&#41;. Diese Lektion enthält die folgenden Aufgaben:  
  
-   [Erstellen einer Sequence Clustering-Mining Modellstruktur &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [Verarbeiten des Sequenzclustermodells](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [Erkunden des Sequence Clustering-Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen eines zugehörigen Sequence Clustering-Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [Erstellen von Vorhersagen für ein Sequenz Cluster Modell &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen einer Sequence Clustering-Mining Modellstruktur &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Alle Lektionen  
 [Lektion 1: Erstellen der Data Mining-Lösung für fortgeschrittene &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Lektion 2: Erstellung eines Vorhersage Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lektion 3: Erstellen eines Warenkorbszenarios &#40;Data Mining-Tutorial für Fortgeschrittene&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 Lektion 4: Sequenzclusterszenarios (Data Mining-Tutorial für Fortgeschrittene).  
  
 [Lektion 5: Erstellen von neuronalen Netzwerk- und logistischen Regressionsmodellen &#40;Data Mining-Tutorial für Fortgeschrittene&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services-Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
