---
title: 'Lektion 4: Untersuchen der Targeted Mailing-Modelle (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 820a65ce9d45a72fe6a7629aebb7bb10374dbfae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147313"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a>Lektion 4: Untersuchen der Targeted Mailing-Modelle (Lernprogramm zu Data Mining-Grundlagen)
  Nachdem die Modelle im Projekt verarbeitet wurden, können Sie sie auf interessante Trends untersuchen. Da Muster bei bloßer Betrachtung der Zahlen komplex und schwierig erscheinen können, bietet SQL Server Data Mining visuelle Tools, mit deren Hilfe die Daten untersucht und die Regeln und Beziehungen, die von den Algorithmen innerhalb der Daten ermittelt wurden, interpretiert werden können. Sie können auch verschiedene Genauigkeitstests verwenden, um das Dataset zu überprüfen bzw. um vor der Bereitstellung festzustellen, welches Modell am besten geeignet ist.  
  
 Bei Verwendung von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] um Ihre Modelle untersuchen zu können, wird jedes erstellte Modell aufgeführt, der **Miningmodell-Viewer** -Registerkarte im Data Mining-Designer. Sie können die Modelle mithilfe der Viewer untersuchen. Diese Viewer sind auch in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] verfügbar.  
  
 Jeder Algorithmus, den Sie zum Erstellen eines Modells in verwendet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] eine andere Art von Ergebnis zurückgibt. Daher enthält [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] benutzerdefinierte Viewer für jede Art von Computerlernmodellen.  
  
 Wenn Sie auf Informationen zugreifen möchten [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet auch HTML-Viewer wird aufgerufen, der **Generic Content Tree Viewer**, die ausführliche Informationen über die Modelldaten und Mustern, die gefunden wurden, in einem vereinfachten Tabellenformat anzeigt. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
 In dieser Lektion werden die Ergebnisse von drei Modellen untersucht. Jeder Modelltyp basiert auf einem anderen Algorithmus und bietet unterschiedliche Einblicke in die Daten.  
  
-   Das Decision Tree-Modell gibt Erklärungen zu Faktoren, die den Fahrradkauf beeinflussen.  
  
-   Das Clustering-Modell gruppiert die Kunden nach Attributen, darunter das Fahrradkaufverhalten sowie andere ausgewählte Attribute.  
  
-   Mit dem Naive Bayes-Modell können Sie die Beziehung zwischen verschiedenen Attributen untersuchen.  
  
 Die folgenden Themen enthalten weitere Informationen zu den einzelnen Miningmodell-Viewern.  
  
-   [Untersuchen des Entscheidungsstrukturmodells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Clustering-Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 Alle drei Modelle können angezeigt werden, mithilfe der **Generic Content Tree Viewer**, um Formeln, Datenwerte usw. zu extrahieren.  
  
## <a name="first-task-in-lesson"></a>Erste Aufgabe in der Lektion  
 [Untersuchen des Entscheidungsstrukturmodells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>Vorherige Lektion  
 [Lektion 3: Hinzufügen und Verarbeiten von Modellen](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 5: Testen von Modellen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodell-Viewer miningmodelltasks und Anweisungen](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Data Mining-Modell-Viewer](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
