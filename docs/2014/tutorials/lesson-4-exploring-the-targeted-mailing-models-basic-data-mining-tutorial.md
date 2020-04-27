---
title: 'Lektion 4: Untersuchen der Ziel-Mailing-Modelle (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 97db61dc3b9adf2e345957c8e08aa752e51286e0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63312149"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a>Lektion 4: Untersuchen der Targeted Mailing-Modelle (Lernprogramm zu Data Mining-Grundlagen)
  Nachdem die Modelle im Projekt verarbeitet wurden, können Sie sie auf interessante Trends untersuchen. Da Muster bei bloßer Betrachtung der Zahlen komplex und schwierig erscheinen können, bietet SQL Server Data Mining visuelle Tools, mit deren Hilfe die Daten untersucht und die Regeln und Beziehungen, die von den Algorithmen innerhalb der Daten ermittelt wurden, interpretiert werden können. Sie können auch verschiedene Genauigkeitstests verwenden, um das Dataset zu überprüfen bzw. um vor der Bereitstellung festzustellen, welches Modell am besten geeignet ist.  
  
 Wenn Sie verwenden [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , um die Modelle zu untersuchen, wird jedes erstellte Modell auf der Registerkarte **Mining Modell-Viewer** im Data Mining-Designer aufgelistet. Sie können die Modelle mithilfe der Viewer untersuchen. Diese Viewer sind auch in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] verfügbar.  
  
 Jeder Algorithmus, den Sie zum Erstellen eines Modells in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verwendet haben, gibt einen anderen Ergebnistyp zurück. Daher enthält [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] benutzerdefinierte Viewer für jede Art von Computerlernmodellen.  
  
 Wenn Sie Details anzeigen möchten, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bietet auch einen HTML-Viewer mit dem Namen **Generic Content Tree Viewer**, der ausführliche Informationen über die Modelldaten und alle gefundenen Muster in einem semitabellarischen Format anzeigt. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
 In dieser Lektion werden die Ergebnisse von drei Modellen untersucht. Jeder Modelltyp basiert auf einem anderen Algorithmus und bietet unterschiedliche Einblicke in die Daten.  
  
-   Das Decision Tree-Modell gibt Erklärungen zu Faktoren, die den Fahrradkauf beeinflussen.  
  
-   Das Clustering-Modell gruppiert die Kunden nach Attributen, darunter das Fahrradkaufverhalten sowie andere ausgewählte Attribute.  
  
-   Mit dem Naive Bayes-Modell können Sie die Beziehung zwischen verschiedenen Attributen untersuchen.  
  
 Die folgenden Themen enthalten weitere Informationen zu den einzelnen Miningmodell-Viewern.  
  
-   [Untersuchen des Entscheidungsstruktur Modells &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [Erkunden des Clustering-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [Untersuchen des Naive Bayes-Modells &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 Alle drei Modelle können mit dem **Generic Content Tree Viewer**angezeigt werden, um Formeln, Datenwerte usw. zu extrahieren.  
  
## <a name="first-task-in-lesson"></a>Erste Aufgabe in der Lektion  
 [Untersuchen des Entscheidungsstruktur Modells &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>Vorherige Lektion  
 [Lektion 3: Hinzufügen und Verarbeiten von Modellen](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 5: Testen von Modellen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tasks und Anleitungen des Mining Modell-Viewers](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Data Mining-Modell-Viewer](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
