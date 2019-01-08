---
title: Klassifikationsmatrix (Analysis Services – Datamining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- displaying mining accuracy
- confusion matrix [data mining]
- classification matrix [Analysis Services]
- accuracy testing [data mining]
ms.assetid: 5c12f202-2ed9-41fa-bee2-0f7ab3ff058a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7949729f3ebee87d06e5e591c46513c111b70016
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53358892"
---
# <a name="classification-matrix-analysis-services---data-mining"></a>Klassifikationsmatrix (Analysis Services   Data Mining)
  In einer *Klassifikationsmatrix* werden alle im Modell enthaltenen Fälle in Kategorien unterteilt. Dabei wird festgestellt, ob der vorhergesagte Wert mit dem Istwert übereinstimmt. Alle Fälle in jeder Kategorie werden dann gezählt und die Summen in der Matrix angezeigt. Die Klassifikationsmatrix ist ein Standardtool für die Auswertung statistischer Modelle und auch unter dem Namen *Verwirrungsmatrix*bekannt.  
  
 In dem Diagramm, das bei Auswahl der **Klassifikationsmatrix** erstellt wird, werden die Istwerte für jeden angegebenen, vorhergesagten Status mit den vorhergesagten Werten verglichen. Durch die Zeilen der Matrix werden die vorhergesagten Werte und durch die Spalten die Istwerte des Modells dargestellt. In der Analyse werden die folgenden Kategorien verwendet: *falsch positiv*, *wahr positiv*, *falsch negativ*und *wahr negativ*.  
  
 Eine Klassifikationsmatrix ist ein wichtiges Tool, um die Ergebnisse der Vorhersage zu bewerten. Sie erleichtert das Verständnis der Vorhersagen, und die Auswirkungen falscher Vorhersagen sind leichter erkennbar. Mithilfe des Betrags und der Prozentsätze in den einzelnen Zellen der Matrix erkennen Sie auf Anhieb, wie häufig das Modell eine genaue Vorhersage getroffen hat.  
  
 In diesem Abschnitt wird erläutert, wie Sie eine Klassifikationsmatrix erstellen und die Ergebnisse interpretieren können.  
  
## <a name="understanding-the-classification-matrix"></a>Grundlegendes zur Klassifikationsmatrix  
 Das erstellte Modell ist ein Teil des Lernprogramms zu den Data Mining-Grundlagen. Mit dem [TM_DecisionTree]-Modell, das die Erstellung einer Targeted Mailing-Kampagne erleichtert, kann vorhergesagt werden, welche Kunden am ehesten ein Fahrrad kaufen werden. Um die erwartete Brauchbarkeit dieses Modells zu testen, verwenden Sie ein Dataset, für das die Werte der Ergebnisattributs, [Bike Buyer], bereits bekannt sind. Normalerweise verwenden Sie ein Testdataset, das Sie beim Erstellen der Miningstruktur zum Trainieren des Modells reserviert haben.  
  
 Es gibt nur zwei mögliche Ergebnisse: Ja (der Kunde kauft wahrscheinlich ein Fahrrad), und Nein (der Kunde kauft wahrscheinlich kein Fahrrad). Die resultierende Klassifikationsmatrix ist daher relativ einfach.  
  
## <a name="interpreting-the-results"></a>Interpretieren der Ergebnisse  
 Die folgende Tabelle enthält die Klassifikationsmatrix für das TM_DecisionTree-Modell. Bedenken Sie bei diesem vorhersagbaren Attribut, dass 0 Nein und 1 Ja bedeutet.  
  
|Vorhergesagt|0 (Ist-Wert)|1 (Ist-Wert)|  
|---------------|------------------|------------------|  
|0|362|144|  
|1|121|373|  
  
 Die erste Ergebniszelle mit dem Wert 362 gibt die Anzahl von *wahren positiven* Ergebnissen für den Wert 0 an. Da 0 angibt, dass der Kunde kein Fahrrad gekauft hat, können Sie aus dieser Zahl ablesen, dass das Modell den korrekten Wert für Kunden, die keinen Kauf getätigt haben, in 362 Fällen vorhergesagt hat.  
  
 Die darunter liegende Zelle mit dem Wert 121 gibt die Anzahl an *falschen positiven*Ergebnissen an, d. h. wie oft das Modell vorhergesagt hat, dass ein Kunde ein Fahrrad kaufen würde, dieser Kauf dann aber nicht getätigt wurde.  
  
 Die Zelle mit dem Wert 144 gibt die Anzahl von *falschen positiven* Ergebnissen für den Wert 1 an. Da 1 bedeutet, dass der Kunde ein Fahrrad gekauft hat, können Sie aus dieser Zahl ablesen, dass das Modell in 144 Fällen vorhergesagt hat, dass ein Kunde kein Fahrrad kaufen würde, er dann den Kauf jedoch dennoch getätigt hat.  
  
 Die Zelle mit dem Wert 373 gibt die Anzahl von wahren positiven Ergebnissen für den Zielwert 1 an. Das heißt, das Modell hat in 373 Fällen korrekt vorhergesagt, dass jemand ein Fahrrad kaufen würde.  
  
 Wenn Sie die Werte in den Zellen, die diagonal gegenüber liegen, addieren, können Sie die Gesamtgenauigkeit des Modells bestimmen. Eine Diagonale zeigt die Gesamtanzahl korrekter Vorhersagen an, die andere Diagonale gibt die Gesamtanzahl falscher Vorhersagen an.  
  
### <a name="using-multiple-predictable-values"></a>Verwenden von mehreren vorhersagbaren Werten  
 Der Fall [Bike Buyer] ist besonders leicht zu interpretieren, da es nur zwei mögliche Werte gibt. Wenn das vorhersagbare Attribut mehrere mögliche Werte hat, fügt die Klassifikationsmatrix eine neue Spalte für jeden möglichen Istwert hinzu und zählt dann die Anzahl der Übereinstimmungen für jeden vorhergesagten Wert. Die folgende Tabelle enthält die Ergebnisse für ein anderes Modell, in dem drei Werte (0, 1, 2) möglich sind.  
  
|Vorhergesagt|0 (Ist-Wert)|1 (Ist-Wert)|2 (Istwert)|  
|---------------|------------------|------------------|------------------|  
|0|111|3|5|  
|1|2|123|17|  
|2|19|0|20|  
  
 Auch wenn der Bericht durch die zusätzlichen Spalten komplexer wird, können die zusätzlichen Angaben sehr nützlich sein, wenn Sie die kumulierten Kosten einer falschen Vorhersage beurteilen möchten. Um Summen für die Diagonalen zu erstellen oder die Ergebnisse verschiedener Zeilenkombinationen zu vergleichen, klicken Sie auf der Registerkarte **Klassifikationsmatrix** auf die Schaltfläche **Kopieren** , und fügen Sie den Bericht in Excel ein. Sie können auch einen Client wie den Data Mining-Client für Excel verwenden, der [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen unterstützt, um direkt in Excel einen Klassifikationsbericht zu erstellen, der Zahlen und Prozentangaben enthält. Weitere Informationen finden Sie unter [SQL Server Data Mining](https://go.microsoft.com/fwlink/?LinkID=77733).  
  
## <a name="restrictions-on-the-classification-matrix"></a>Einschränkungen der Klassifikationsmatrix  
 Eine Klassifikationsmatrix kann nur mit diskreten vorhersagbaren Attributen verwendet werden.  
  
 Obwohl Sie bei der Modellauswahl auf der Registerkarte **Eingabeauswahl** im **Mininggenauigkeitsdiagramm** -Designer mehrere Modelle hinzufügen können, wird auf der Registerkarte **Klassifikationsmatrix** eine separate Matrix für jedes Modell angezeigt.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Die folgenden Themen enthalten weitere Informationen zum Erstellen und Verwenden von Klassifikationsmatrizen und weiteren Diagrammen.  
  
|Thema|Links|  
|------------|-----------|  
|Bietet eine exemplarische Vorgehensweise zum Erstellen eines Prognosegütediagramms für das Targeted Mailing-Modell.|[Lernprogramm zu Data Mining-Grundlagen](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [Überprüfen der Genauigkeit mit Prognosegütediagrammen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|Erläutert verwandte Diagrammtypen.|[Prognosegütediagramm &#40;Analysis Services – Data Mining&#41;](lift-chart-analysis-services-data-mining.md)<br /><br /> [Gewinndiagramm &#40;Analysis Services – Data Mining&#41;](profit-chart-analysis-services-data-mining.md)<br /><br /> [Punktdiagramm &#40;Analysis Services – Data Mining&#41;](scatter-plot-analysis-services-data-mining.md)|  
|Beschreibt die Verwendungsmöglichkeiten für die Kreuzvalidierung bei Miningmodellen und Miningstrukturen.|[Kreuzvalidierung &#40;Analysis Services – Data Mining&#41;](cross-validation-analysis-services-data-mining.md)|  
|Beschreibt Schritte zum Erstellen von Prognosegütediagrammen und anderen Genauigkeitsdiagrammen.|[Tasks und Anweisungen für Test und Überprüfung &#40;Data Mining&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Tests und Überprüfung &#40;Data Mining&#41;](testing-and-validation-data-mining.md)  
  
  
