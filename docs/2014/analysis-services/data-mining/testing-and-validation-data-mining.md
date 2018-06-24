---
title: Tests und Überprüfung (Datamining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing data mining models
- comparing mining models
- continuous attribute charts
- data mining [Analysis Services], models
- charts [Analysis Services]
- predictive modeling [Analysis Services]
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- confidence scores [data mining]
- displaying mining accuracy
- predictions [Analysis Services], comparing mining models
- scoring [data mining]
- lift charts [Analysis Services]
- classification matrix [Analysis Services]
- CRISP-DM
- accuracy testing [data mining]
ms.assetid: 197144f5-21ed-4009-b448-fe412fb3916c
caps.latest.revision: 60
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0e83f8e0ad6227444f4dbc0962a83e1aedd8a5f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058604"
---
# <a name="testing-and-validation-data-mining"></a>Tests und Überprüfung (Data Mining)
  Die Überprüfung ist der Prozess des Bewertens, welche Leistung die Miningmodelle mit echten Daten erzielen. Es ist wichtig, dass Sie Ihre Miningmodelle überprüfen, indem Sie ihre Qualität und Merkmale studieren, bevor Sie sie in einer Produktionsumgebung bereitstellen.  
  
 In diesem Abschnitt werden einige grundlegende Konzepte im Zusammenhang mit der Modellqualität und die Strategien zur Modellvalidierung vorgestellt, die in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zur Verfügung stehen. Eine Übersicht dazu, wie Modellüberprüfungen in den größeren Data Mining-Prozess eingebunden werden können, finden Sie unter [Data Mining-Projektmappen](data-mining-solutions.md).  
  
## <a name="methods-for-testing-and-validation-of-data-mining-models"></a>Methoden zum Testen und Überprüfen von Data Mining-Modellen  
 Es gibt viele Ansätze zum Bewerten der Qualität und der Eigenschaften eines Data Mining-Modells.  
  
-   Verwenden Sie verschiedene Measures für die statistische Gültigkeit, um zu bestimmen, ob Probleme mit den Daten oder dem Modell vorliegen.  
  
-   Teilen Sie die Daten in Trainings- und Testsätze auf, um die Genauigkeit von Vorhersagen zu testen.  
  
-   Bitten Sie betriebswirtschaftliche Experten, die Ergebnisse des Data Mining-Modells zu überprüfen und zu bestimmen, ob die erkannten Muster für das gewollte Geschäftsszenario bedeutungsvoll sind.  
  
 Alle diese Methoden sind in der Data Mining-Methodologie nützlich und werden beim Erstellen, Testen und Optimieren von Modellen zur Lösung eines bestimmten Problems iterativ eingesetzt. Es gibt keine einzelne umfassende Regel, aus der Sie ableiten können, wann ein Modell ausreichend ist bzw. wann ausreichend Daten vorliegen.  
  
## <a name="definition-of-criteria-for-validating-data-mining-models"></a>Definition von Kriterien zum Überprüfen von Data Mining-Modellen  
 Data Mining-Measures lassen sich im Allgemeinen den Kategorien Genauigkeit, Zuverlässigkeit und Nützlichkeit zuteilen.  
  
 Die*Genauigkeit* ist ein Maß, das besagt, wie gut ein Ergebnis vom Modell mit den Attributen der bereitgestellten Daten korreliert wird. Es gibt verschiedenen Measures für die Genauigkeit, die jedoch alle von den verwendeten Daten abhängig sind. In der Praxis können Werte fehlen oder ungenau sein, oder die Daten können durch mehrere Prozesse verändert worden sein. Insbesondere in der Untersuchungs- und Entwicklungsphase kann es sein, dass eine bestimmte Menge an Fehlern in den Daten akzeptiert wird, insbesondere wenn Daten mit relativ einheitlichen Merkmalen vorliegen. Beispielsweise kann ein Modell, mit dem der Umsatz einer bestimmten Niederlassung anhand der vergangenen Umsätze vorhergesagt wird, auch dann stark korreliert und sehr genau sein, wenn die betreffende Niederlassung durchgängig eine falsche Buchhaltungsmethode verwendet hat. Deshalb müssen Genauigkeitsmaße durch Bewertungen der Zuverlässigkeit ausgeglichen werden.  
  
 Durch die*Zuverlässigkeit* wird bewertet, wie sich ein Data Mining-Modell bei Anwendung auf unterschiedliche Datasets verhält. Ein Data Mining-Modell ist zuverlässig, wenn es unabhängig von den bereitgestellten Testdaten die gleichen Typen von Vorhersagen erzeugt oder die gleichen Arten von Mustern sucht. Beispielsweise würde sich das Modell, das für die Niederlassung erzeugt wurde, in der die falsche Buchhaltungsmethode verwendet wurde, nicht gut auf andere Niederlassungen verallgemeinern lassen, und daher wäre es nicht zuverlässig.  
  
 Die*Nützlichkeit* schließt verschiedene Metriken ein, aus denen hervorgeht, ob das Modell nützliche Informationen liefert. Beispielsweise kann ein Data Mining-Modell, das den Standort einer Niederlassung mit dem Umsatz korreliert, sowohl genau als auch zuverlässig, aber nicht nützlich sein, weil sich dieses Ergebnis nicht dadurch verallgemeinern lässt, dass dem gleichen Standort weitere Niederlassungen hinzugefügt werden. Darüber hinaus beantwortet es die grundlegende Geschäftsfrage nicht, warum an bestimmten Standorten höhere Umsätze erzielt werden. Es kann sich auch herausstellen, dass ein anscheinend erfolgreiches Modell in Wirklichkeit bedeutungslos ist, weil es auf Kreuzkorrelationen der Daten basiert.  
  
## <a name="tools-for-testing-and-validation-of-mining-models"></a>Tools zum Testen und Überprüfen von Miningmodellen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt mehrere Ansätze zur Überprüfung von Data Mining-Lösungen, die alle Phasen der Data Mining-Testmethoden unterstützen.  
  
-   Partitionieren der Daten in Test- und Trainingssätze  
  
-   Filtern von Modellen, um verschiedene Kombinationen der gleichen Quelldaten zu schulen und zu testen.  
  
-   Das Messen von *Prognosegüte* und *Gewinn*. Ein *Prognosegütediagramm* ist eine Methode zur visuellen Darstellung der Verbesserung, die verglichen mit dem Anstellen Zufallsvorhersage aus dem Einsatz eines Data Mining-Modells resultiert.  
  
-   Ausführen der *Kreuzvalidierung* für Datasets  
  
-   Generieren von *Klassifikationsmatrizen*. Diese Diagramme tragen dazu bei, zutreffende und falsche Vermutungen in eine Tabelle einzufügen und zu sortieren, sodass Sie mühelos messen können, wie genau das Modell den Zielwert vorhersagt.  
  
-   Erstellen von *Punktdiagrammen* , um die Eignung einer Regressionsformel zu beurteilen.  
  
-   Erstellen von *Gewinndiagrammen* , in denen finanzielle Gewinne oder Kosten mit dem Miningmodell verknüpft werden, damit Sie den Wert der Empfehlungen beurteilen können.  
  
 Der Sinn dieser Metrik liegt nicht darin herauszufinden, ob das Data Mining-Modell die Antwort auf Ihre Geschäftsfrage liefert; vielmehr stellt diese Metrik objektive Messwerte bereit, mit denen Sie die Zuverlässigkeit Ihrer Daten für Vorhersageanalysen beurteilen und entscheiden können, ob bei der Entwicklung eine bestimmte Iteration implementiert werden soll.  
  
 Dieser Abschnitt enthält eine Übersicht der einzelnen Methoden und führt Sie durch die Schritte zur Messung der Genauigkeit von Modellen, die Sie mithilfe von SQL Server Data Mining erstellen.  
  
### <a name="related-topics"></a>Verwandte Themen  
  
|Thema|Links|  
|------------|-----------|  
|Erfahren Sie mehr darüber, wie Sie ein Testdataset mithilfe eines Assistenten oder mit DMX-Befehlen einrichten können.|[Trainings- und Testdatasets](training-and-testing-data-sets.md)|  
|Erfahren Sie mehr darüber, wie Sie die Verteilung und die Repräsentativität der Daten in einer Miningstruktur testen können.|[Übergreifende Überprüfung &#40;Analysis Services – Datamining&#41;](cross-validation-analysis-services-data-mining.md)|  
|Erfahren Sie mehr über die Typen von Genauigkeitsdiagrammen in [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].|[Prognosegütediagramm &#40;Analysis Services – Datamining&#41;](lift-chart-analysis-services-data-mining.md)<br /><br /> [Gewinndiagramm &#40;Analysis Services – Datamining&#41;](profit-chart-analysis-services-data-mining.md)<br /><br /> [Punktdiagramm &#40;Analysis Services – Datamining&#41;](scatter-plot-analysis-services-data-mining.md)|  
|Erfahren Sie mehr darüber, wie Sie eine Klassifikationsmatrix, auch bekannt unter dem Namen Verwirrungsmatrix, erstellen, um die Anzahl von als wahr positiv, falsch positiv, wahr negativ und falsch negativ klassifizierten Ergebnissen zu ermitteln.|[Klassifikationsmatrix &#40;Analysis Services – Datamining&#41;](classification-matrix-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Tools](data-mining-tools.md)   
 [Datamining-Lösungen](data-mining-solutions.md)   
 [Tests und Überprüfung miningmodelltasks und &#40;Datamining&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  