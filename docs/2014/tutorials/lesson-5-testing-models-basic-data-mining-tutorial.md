---
title: 'Lektion 5: Testen von Modellen (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 88a9d564b297d277d1566152cc11599bec912ddc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63185423"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a>Lektion 5: Testen von Modellen (Lernprogramm zu Datamining-Grundlagen)
  Nachdem Sie das Modell mit dem Trainingssatz für das Targeted Mailing-Szenario verarbeitet haben, können Sie die Modelle mit dem Testsatz überprüfen. Die Überprüfung ist ein wichtiger Schritt im Data Mining-Prozess. Sie sollten wissen, welche Leistung Ihre Miningmodelle für Targeted Mailing mit echten Daten erzielen, bevor Sie die Modelle in Ihrer Produktionsumgebung bereitstellen.  
  
 Da die Daten im Testsatz bereits bekannte Werte für das Fahrradkaufverhalten enthalten, ist es einfach, die Vorhersagegenauigkeit des Modells zu bestimmen. Das Modell mit den besten Ergebnissen wird von der Marketingabteilung von [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] zur Identifizierung von Kunden für die Target Mailing-Kampagne verwendet.  
  
 In dieser Lektion überprüfen Sie die Modelle mithilfe mehrerer Methoden:  
  
1.  Sie müssen die Vorhersagen anhand des Testsatzes, um festzustellen, wie genau das Modell bei bekannten Ergebnissen ist. Verwenden Sie eine *prognosegütediagramm* um dessen Effektivität zu messen.  
  
     [Überprüfen der Genauigkeit mit Prognosegütediagrammen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  Anschließend testen Sie die Modelle mit einer gefilterten Teilmenge der Daten. Sie können mehrere Modelle im selben Prognosegütediagramm vergleichen.  
  
     [Testen eines gefilterten Modells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 Weitere Informationen dazu, wie modellvalidierung im Allgemeinen, finden Sie unter [Data Mining-Konzepte](../../2014/analysis-services/data-mining/data-mining-concepts.md).  
  
## <a name="first-task-in-lesson"></a>Erste Aufgabe in der Lektion  
 [Überprüfen der Genauigkeit mit Prognosegütediagrammen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>Vorherige Lektion  
 [Lektion 4: Untersuchen der Targeted Mailing-Modelle &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 6: Erstellen und Verwenden von Vorhersagen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Prognosegütediagrammtyp (Registerkarte) &#40;Mininggenauigkeitsdiagrammsicht&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)   
 [Prognosegütediagramm &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Tests und Überprüfung &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [Klassifizierung Registerkarte &#40;Mininggenauigkeitsdiagrammsicht&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md)   
 [Klassifikationsmatrix &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
