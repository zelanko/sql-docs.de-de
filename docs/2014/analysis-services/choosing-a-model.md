---
title: Auswählen eines Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining algorithms
- mining models
- mining structures
- data mining models
- data mining structures
ms.assetid: 444bbf9c-cec8-460e-881d-38784fb146fa
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9817f7e8906d9e75f7c2b5d55db679d77e7cc47e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273886"
---
# <a name="choosing-a-model"></a>Auswählen eines Modells
  **Mining-Algorithmus:** dem Datamining *Algorithmus* ist der Mechanismus, der Muster aus Daten erstellt. Der Algorithmus definiert, wie Daten gezählt werden, wie Beziehungen abgeleitet werden und wie Muster gespeichert werden. Die Auswahl eines Algorithmus richtet sich teilweise nach der Art der zu analysierenden Daten. Beispielsweise unterstützten einige Algorithmen nur fortlaufende Nummern, während andere am besten mit einer begrenzten Anzahl unterschiedlicher Werte eingesetzt werden.  
  
 **Miningmodell:** das Ergebnis der Datenanalyse durch einen Algorithmus wird gespeichert, einem *Miningmodell*. Ein Miningmodell stellt eine Sammlung von Regeln, Statistiken und Mustern dar. Die *Inhalt* des Miningmodells hängt von der Algorithmus Sie verwendet, um die Daten zu verarbeiten, jedoch können Folgendes beinhalten:  
  
-   If-then-Regeln, die beschreiben, wie Produkte bei einer Transaktion gruppiert werden.  
  
-   Eine Entscheidungsstruktur, in der die zu einem Ergebnis führenden Pfade verfolgt werden und Wahrscheinlichkeiten für das Vorkommen jedes Pfads angegeben sind.  
  
-   Ein mathematisches Modell mit Gleichungen entweder für das gesamte Modell oder für Segmente des Modells.  
  
-   Sammlungen mit ähnlichen Elementen (namens *Cluster* oder *Segmente*), die durch gemeinsame Merkmale und einen ähnlichkeitswert definiert werden.  
  
-   *Knoten* in einem Netzwerk verbunden *Kanten*. Die Knoten stellen Elemente oder Elementgruppen dar. Die Kanten werden gemäß der Stärke der Beziehungen zwischen Knoten bewertet.  
  
 **Mithilfe des Modells:** , nachdem Sie ein Modell erstellt haben, Sie die bereitgestellten Viewern untersuchen können oder Sie können eine Abfrage für das Modell erstellen. Abfragen können für folgende Aufgaben verwendet werden:  
  
-   Vorhersagen künftiger Werte.  
  
-   Generieren einer Gruppe verwandter oder empfohlener Produkte.  
  
-   Zurückgeben von Regeln, Mustern oder Formeln im Modell.  
  
-   Abrufen von Metadaten aus dem Modell.  
  
-   Bereitstellen von Unterstützungs- und Wahrscheinlichkeitswerten für alle oder einige Vorhersagen.  
  
## <a name="types-of-machine-learning-algorithms"></a>Typen von Computerlernalgorithmen  
 Da die verschiedenen Typen von Algorithmen Daten in unterschiedlicher Weise verarbeiten, müssen Sie beim Erstellen eines Modells den Algorithmus auswählen, der für Ihre Zwecke und für die zu analysierenden Daten geeignet ist.  
  
 Die Data Mining-Add-Ins für Excel enthalten die folgenden allgemeinen Algorithmustypen:  
  
-   *Klassifizierungsalgorithmen*.  
  
     Diese Algorithmen sagen basierend auf den anderen Attributen im Dataset mindestens eine diskrete Variable voraus.  
  
-   *Regressionsalgorithmen*  
  
     Diese Algorithmen sagen basierend auf anderen Attributen im Dataset mindestens eine kontinuierliche Variable voraus, z. B. den Gewinn oder Verlust.  
  
-   *Segmentierungsalgorithmen*  
  
     Diese Algorithmen teilen Daten in Gruppen oder Cluster von Elementen auf, die über ähnliche Eigenschaften verfügen.  
  
-   *Zuordnungsalgorithmen*  
  
     Diese Algorithmen suchen Korrelationen zwischen verschiedenen Attributen in einem Dataset. Diese Art von Algorithmus wird am häufigsten zur Erstellung von Zuordnungsregeln verwendet. Zuordnungsregeln können für eine Warenkorbanalyse verwendet werden.  
  
-   *Sequenzanalysealgorithmen*  
  
     Diese Algorithmen fassen häufige Datensequenzen oder -periodizitäten zusammen, z. B. die Pfade, denen Benutzern bei der Navigation auf einer Website folgen.  
  
 Die von den SQL Server Data Mining-Add-Ins für Office verwendeten Algorithmen basieren auf den von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bereitgestellten Algorithmen. Sie können auch Algorithmen von Drittanbietern, die der OLE DB für Data Mining-Spezifikation entsprechen verwenden, wenn die Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] mit der Sie verbunden sind konfiguriert wurde, dass um Algorithmen von Drittanbietern zu ermöglichen.  
  
## <a name="requirements"></a>Anforderungen  
 Jeder Algorithmus unterscheidet sich in Bezug auf die Daten, die er verarbeiten kann.  
  
-   In einem linearen Regressionsmodell können nur numerische Werte modelliert werden. Sowohl die Eingabevariablen als auch die Zielergebnisse müssen Typen fortlaufender Zahlen sein. Verwenden Sie eine Entscheidungsstruktur oder ein Schätzmodell, wenn Sie diskrete und kontinuierliche Variablen kombinieren müssen.  
  
-   Für ein Naïve Bayes-Modell müssen alle Zahlen klassifiziert sein. Wenn Sie einen der Assistenten auf Grundlage dieses Algorithmus verwenden, erfolgt die Klassifizierung automatisch.  
  
-   Ein Entscheidungsstrukturmodell kann sowohl diskrete als auch kontinuierliche Variablen enthalten. Für Teilungen in der Struktur werden Zahlen ggf. jedoch automatisch klassifiziert.  
  
-   In neuronalen Netzwerken und logistischen Regressionsmodellen werden die als Ergebnisse oder Eingabevariablen verwendeten Zahlen automatisch klassifiziert. Wenn Sie Zahlen nach anderen Kriterien gruppieren möchten, sollten Sie das Tool Neu bezeichnen verwenden, um vor der Modellierung die Gruppierungen zu erstellen. Angenommen, Sie möchten Werte in einer **Alter** Spalte nach Zehntelwerten (10 bis 20, 21-30 und so weiter), anstatt die statistisch signifikanten Gruppierungen, die vom Modell (ein Beispiel für möglicherweise 35,6 bis 41,8 Jahre) gefunden.  
  
-   Für ein Zuordnungsmodell müssen Daten in Transaktionen gruppiert werden, wobei jede auf mehrere Elemente oder Zeilen verweist. Bei Verwendung der [Assistenten zum Zuordnen von &#40;Data Mining-Client für Excel&#41; ](associate-wizard-data-mining-client-for-excel.md) Assistenten oder dem [Warenkorbanalyse &#40;Tabellenanalysetools für Excel&#41; ](shopping-basket-analysis-table-analysistools-for-excel.md) Tools, die Daten dargestellte Layout aufweisen sollte die **zuordnen** der Beispielarbeitsmappe auf der Registerkarte.  
  
     Wenn Sie geschachtelte Tabellen in einer externen Datenquelle verwenden möchten, müssen Sie verwenden die [erweiterte Modellierung &#40;Data Mining-Add-ins für Excel&#41; ](advanced-modeling-data-mining-add-ins-for-excel.md) Modellierungsoptionen erstellen Sie eine Miningstruktur und ein Miningmodell, das auf dem Server gespeichert wird. Excel bietet keine Unterstützung für geschachtelte Tabellen.  
  
## <a name="feature-selection"></a>Funktionsauswahl  
 Je nach DataSet, der Algorithmus gelten unter Umständen *Funktionsauswahl*, zu der Sie Spalten auszusortieren und um zu bestimmen, welche Spalten der Daten in Bezug auf das Ergebnis statistisch signifikant sind.  
  
 Für jeden Algorithmus werden andere Methoden der Funktionsauswahl (wie Entropie oder diverse Informationsbewertungen) verwendet, um zu bestimmen, welche Trends wichtig sind und welche Abweichungen verworfen werden können.  
  
 In den Data Mining-Add-Ins für Excel wird die Funktionsauswahl unter Verwendung der für den jeweiligen Algorithmus geeigneten Bewertungsmethode automatisch angewendet. Wenn Sie die Ergebnisse der Funktionsauswahl beeinflussen möchten, verwenden Sie die Assistenten in der **Data Mining** zuerst das Menüband, und klicken Sie auf **erweitert** zum Festlegen von Parametern, die mit der **Algorithmusparameter**Dialogfeld.  
  
 Eine Liste der Funktionsauswahl Methoden, die von jedem Algorithmus verwendet, finden Sie im Thema auf [Funktionsauswahl &#40;Data Mining&#41; ](data-mining/feature-selection-data-mining.md) in SQL Server-Onlinedokumentation.  
  
## <a name="list-of-supported-algorithms"></a>Liste der unterstützten Algorithmen  
 Die folgenden Algorithmen werden standardmäßig bereitgestellt.  
  
|Algorithmusname|Description|Verwendung in|  
|--------------------|-----------------|-------------|  
|Microsoft Association Rules|Erstellt Regeln, die beschreiben, welche Elemente voraussichtlich zusammen in einer Transaktion angezeigt werden.|[Zuordnungs-Assistent &#40;Datamining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md)<br /><br /> [Warenkorbanalyse &#40;Tabelle AnalysisTools für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)|  
|Microsoft Clustering|Identifiziert Beziehungen in einem Dataset, die bei einer einfachen Betrachtung der Daten nicht unbedingt zu erkennen sind. Verwendet iterative Techniken, um Datensätze in Clustern zu gruppieren, die ähnliche Merkmale enthalten.|[Kategorien erkennen &#40;Tabellenanalysetools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)<br /><br /> [Cluster-Assistent &#40;Data Mining-Add-ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)|  
|Microsoft Decision Trees|Trifft Vorhersagen auf der Grundlage der Beziehungen zwischen Spalten im Dataset und stellt die Beziehungen in einer strukturähnlichen Reihe von Teilungen für bestimmte Werte dar.<br /><br /> Unterstützt die Vorhersage für diskrete und kontinuierliche Attribute.|[Assistent zum Klassifizieren &#40;Data Mining-Add-ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)<br /><br /> [Assistent zum Schätzen von &#40;Data Mining-Add-ins für Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)|  
|Microsoft Linear Regression|Findet im Fall einer linearen Abhängigkeit zwischen der Zielvariablen und den untersuchten Variablen die effizienteste Beziehung zwischen dem Zielelement und den zugehörigen Eingaben.<br /><br /> Unterstützt Vorhersagen für kontinuierliche Attribute.|Dieser Algorithmus ist in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verfügbar. In den Data Mining-Add-Ins für Office können Sie ein Modell erstellen, in dem dieser Algorithmus verwendet wird, indem Sie eine Struktur erstellen und dann manuell ein Modell hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [erweiterte Modellierung &#40;Data Mining-Add-ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Logistic Regression|Analysiert die Faktoren, die ein Ergebnis beeinflussen, wobei das Ergebnis auf zwei Werte beschränkt ist. Dabei handelt es sich üblicherweise um die Werte für das Eintreten oder Nichteintreten eines Ereignisses.<br /><br /> Unterstützt die Vorhersage für diskrete und kontinuierliche Attribute.|[Aus Beispiel füllen &#40;Tabellenanalysetools für Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)<br /><br /> [Zielsucheszenario &#40;Tabellenanalysetools für Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Was-Wenn-Szenario &#40;Tabellenanalysetools für Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Vorhersagerechner &#40;Tabellenanalysetools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)|  
|Microsoft Naive Bayes|Berechnet die Wahrscheinlichkeit für die Beziehung zwischen allen Eingabespalten und vorhersagbaren Spalten. Mithilfe dieses Algorithmus können Sie schnell Miningmodelle zum Ermitteln von Beziehungen generieren.<br /><br /> Unterstützt nur diskrete und diskretisierte Attribute.<br /><br /> Behandelt alle Eingabeattribute unabhängig voneinander.|[Wichtige Einflussfaktoren analysieren &#40;Tabellenanalysetools für Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)|  
|Microsoft Neural Network|Analysiert komplexe Eingabedaten oder Geschäftsprobleme, für die umfangreiche Trainingsdaten verfügbar sind, für die aber mithilfe anderer Algorithmen nicht problemlos Regeln abgeleitet werden können.<br /><br /> Kann mehrere Attribute vorhersagen.<br /><br /> Kann zum Klassifizieren diskreter Attribute und für die Regression kontinuierlicher Attribute verwendet werden.|Dieser Algorithmus ist in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verfügbar. In den Data Mining-Add-Ins für Office können Sie ein Modell erstellen, in dem dieser Algorithmus verwendet wird, indem Sie eine Struktur erstellen und dann manuell ein Modell hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [erweiterte Modellierung &#40;Data Mining-Add-ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Sequence Clustering|Identifiziert Cluster ähnlich angeordneter Ereignisse in einer Sequenz.<br /><br /> Stellt eine Kombination aus Sequenzanalyse und Clustering bereit.|Dieser Algorithmus steht nur in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zur Verfügung. In den Data Mining-Add-Ins für Office können Sie jedoch ein Modell erstellen, in dem dieser Algorithmus verwendet wird, indem Sie eine Struktur erstellen und dann ein Modell manuell hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [erweiterte Modellierung &#40;Data Mining-Add-ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Time Series|Analysiert zeitbezogene Daten mithilfe einer linearen Entscheidungsstruktur.<br /><br /> Muster können zur Vorhersage zukünftiger Werte in einer Zeitreihe verwendet werden.|[Prognostizieren &#40;Tabellenanalysetools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)<br /><br /> [Planungs-Assistent &#40;Data Mining-Add-ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Inhalt der Data Mining-Add-Ins für Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
