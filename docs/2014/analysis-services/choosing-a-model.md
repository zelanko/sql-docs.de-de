---
title: Auswählen eines Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining algorithms
- mining models
- mining structures
- data mining models
- data mining structures
ms.assetid: 444bbf9c-cec8-460e-881d-38784fb146fa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd75efa13d6761c058b9e3b1f1878036d3d3e928
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088093"
---
# <a name="choosing-a-model"></a>Auswählen eines Modells
  **Mining Algorithmus:** Der Data Mining *Algorithmus* ist der Mechanismus, mit dem Muster aus Daten erstellt werden. Der Algorithmus definiert, wie Daten gezählt werden, wie Beziehungen abgeleitet werden und wie Muster gespeichert werden. Die Auswahl eines Algorithmus richtet sich teilweise nach der Art der zu analysierenden Daten. Beispielsweise unterstützten einige Algorithmen nur fortlaufende Nummern, während andere am besten mit einer begrenzten Anzahl unterschiedlicher Werte eingesetzt werden.  
  
 **Mining Modell:** Das Ergebnis der Datenanalyse durch einen Algorithmus wird in einem *Mining Modell*gespeichert. Ein Miningmodell stellt eine Sammlung von Regeln, Statistiken und Mustern dar. Der *Inhalt* des Mining Modells hängt von dem Algorithmus ab, den Sie verwendet haben, um die Daten zu verarbeiten, kann jedoch Folgendes umfassen:  
  
-   If-then-Regeln, die beschreiben, wie Produkte bei einer Transaktion gruppiert werden.  
  
-   Eine Entscheidungsstruktur, in der die zu einem Ergebnis führenden Pfade verfolgt werden und Wahrscheinlichkeiten für das Vorkommen jedes Pfads angegeben sind.  
  
-   Ein mathematisches Modell mit Gleichungen entweder für das gesamte Modell oder für Segmente des Modells.  
  
-   Sammlungen ähnlicher Elemente (als *Cluster* oder *Segmente*bezeichnet), die durch die von Ihnen freigegebenen Merkmale definiert werden, und durch ein Ähnlichkeits Ergebnis.  
  
-   *Knoten* in einem Netzwerk, die durch *Kanten*verbunden sind. Die Knoten stellen Elemente oder Elementgruppen dar. Die Kanten werden gemäß der Stärke der Beziehungen zwischen Knoten bewertet.  
  
 **Verwenden des Modells:** Nachdem Sie ein Modell erstellt haben, können Sie es mit den bereitgestellten Viewern untersuchen, oder Sie können eine Abfrage für das Modell erstellen. Abfragen können für folgende Aufgaben verwendet werden:  
  
-   Vorhersagen künftiger Werte.  
  
-   Generieren einer Gruppe verwandter oder empfohlener Produkte.  
  
-   Zurückgeben von Regeln, Mustern oder Formeln im Modell.  
  
-   Abrufen von Metadaten aus dem Modell.  
  
-   Bereitstellen von Unterstützungs- und Wahrscheinlichkeitswerten für alle oder einige Vorhersagen.  
  
## <a name="types-of-machine-learning-algorithms"></a>Typen von Computerlernalgorithmen  
 Da die verschiedenen Typen von Algorithmen Daten in unterschiedlicher Weise verarbeiten, müssen Sie beim Erstellen eines Modells den Algorithmus auswählen, der für Ihre Zwecke und für die zu analysierenden Daten geeignet ist.  
  
 Die Data Mining-Add-Ins für Excel enthalten die folgenden allgemeinen Algorithmustypen:  
  
-   *Klassifizierungs Algorithmen*.  
  
     Diese Algorithmen sagen basierend auf den anderen Attributen im Dataset mindestens eine diskrete Variable voraus.  
  
-   *Regressions Algorithmen*  
  
     Diese Algorithmen sagen basierend auf anderen Attributen im Dataset mindestens eine kontinuierliche Variable voraus, z. B. den Gewinn oder Verlust.  
  
-   *Segmentierungsalgorithmen*  
  
     Diese Algorithmen teilen Daten in Gruppen oder Cluster von Elementen auf, die über ähnliche Eigenschaften verfügen.  
  
-   *Zuordnungsalgorithmen*  
  
     Diese Algorithmen suchen Korrelationen zwischen verschiedenen Attributen in einem Dataset. Diese Art von Algorithmus wird am häufigsten zur Erstellung von Zuordnungsregeln verwendet. Zuordnungsregeln können für eine Warenkorbanalyse verwendet werden.  
  
-   *Sequenzanalysealgorithmen*  
  
     Diese Algorithmen fassen häufige Datensequenzen oder -periodizitäten zusammen, z. B. die Pfade, denen Benutzern bei der Navigation auf einer Website folgen.  
  
 Die von den SQL Server Data Mining-Add-Ins für Office verwendeten Algorithmen basieren auf den von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] bereitgestellten Algorithmen. Sie können auch Algorithmen von Drittanbietern verwenden, die der OLE DB für die Data Mining-Spezifikation entsprechen, wenn die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Instanz von, mit der Sie verbunden sind, so konfiguriert wurde, dass Sie Drittanbieter Algorithmen zulässt.  
  
## <a name="requirements"></a>Anforderungen  
 Jeder Algorithmus unterscheidet sich in Bezug auf die Daten, die er verarbeiten kann.  
  
-   In einem linearen Regressionsmodell können nur numerische Werte modelliert werden. Sowohl die Eingabevariablen als auch die Zielergebnisse müssen Typen fortlaufender Zahlen sein. Verwenden Sie eine Entscheidungsstruktur oder ein Schätzmodell, wenn Sie diskrete und kontinuierliche Variablen kombinieren müssen.  
  
-   Für ein Naïve Bayes-Modell müssen alle Zahlen klassifiziert sein. Wenn Sie einen der Assistenten auf Grundlage dieses Algorithmus verwenden, erfolgt die Klassifizierung automatisch.  
  
-   Ein Entscheidungsstrukturmodell kann sowohl diskrete als auch kontinuierliche Variablen enthalten. Für Teilungen in der Struktur werden Zahlen ggf. jedoch automatisch klassifiziert.  
  
-   In neuronalen Netzwerken und logistischen Regressionsmodellen werden die als Ergebnisse oder Eingabevariablen verwendeten Zahlen automatisch klassifiziert. Wenn Sie Zahlen nach anderen Kriterien gruppieren möchten, sollten Sie das Tool Neu bezeichnen verwenden, um vor der Modellierung die Gruppierungen zu erstellen. Beispielsweise kann es vorkommen, dass Sie Werte in einer Spalte vom Typ " **Age** " nach Dezile (10-20, 21-30 usw.) gruppieren möchten, anstatt die statistisch signifikanten Gruppierungen des Modells (z. b. 35,6-41,8 years).  
  
-   Für ein Zuordnungsmodell müssen Daten in Transaktionen gruppiert werden, wobei jede auf mehrere Elemente oder Zeilen verweist. Wenn Sie den Assistenten zum [Zuordnen von Assistenten &#40;Data Mining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md) oder die [waren Korb Analyse &#40;Table Analyzer for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) Tool verwenden, sollten die Daten so angelegt werden, wie Sie auf der Registerkarte **zuordnen** der Beispiel Arbeitsmappe angezeigt werden.  
  
     Wenn Sie in einer externen Datenquelle geclusterte Tabellen verwenden möchten, müssen Sie die Modellierungs Optionen [Erweiterte Modellierungs &#40;Data Mining-Add-Ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md) verwenden, um eine Mining Struktur und ein Mining Modell zu erstellen, die auf dem Server gespeichert werden. Excel bietet keine Unterstützung für geschachtelte Tabellen.  
  
## <a name="feature-selection"></a>Featureauswahl  
 Abhängig vom DataSet kann der Algorithmus die *Funktionsauswahl*anwenden, um nicht nützliche Spalten auszuwitcken und um zu bestimmen, welche Datenspalten in Bezug auf das Ergebnis statistisch signifikant sind.  
  
 Für jeden Algorithmus werden andere Methoden der Funktionsauswahl (wie Entropie oder diverse Informationsbewertungen) verwendet, um zu bestimmen, welche Trends wichtig sind und welche Abweichungen verworfen werden können.  
  
 In den Data Mining-Add-Ins für Excel wird die Funktionsauswahl unter Verwendung der für den jeweiligen Algorithmus geeigneten Bewertungsmethode automatisch angewendet. Wenn Sie die Ergebnisse der Funktionsauswahl beeinflussen möchten, verwenden Sie die Assistenten im Menüband **Data Mining** , und klicken Sie auf **erweitert** , um Parameter mithilfe des Dialog Felds **Algorithmusparameter** festzulegen.  
  
 Eine Liste der Funktionsauswahl Methoden, die von den einzelnen Algorithmen verwendet werden, finden Sie im Thema zur [Funktionsauswahl &#40;Data Mining-&#41;](data-mining/feature-selection-data-mining.md) in SQL Server-Onlinedokumentation.  
  
## <a name="list-of-supported-algorithms"></a>Liste der unterstützten Algorithmen  
 Die folgenden Algorithmen werden standardmäßig bereitgestellt.  
  
|Algorithmusname|Beschreibung|Verwendung in|  
|--------------------|-----------------|-------------|  
|Microsoft Association Rules|Erstellt Regeln, die beschreiben, welche Elemente voraussichtlich zusammen in einer Transaktion angezeigt werden.|[Assistenten &#40;Data Mining-Client für Excel zuordnen&#41;](associate-wizard-data-mining-client-for-excel.md)<br /><br /> [Waren Korb Analyse &#40;Tabellenanalyse für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)|  
|Microsoft Clustering|Identifiziert Beziehungen in einem Dataset, die bei einer einfachen Betrachtung der Daten nicht unbedingt zu erkennen sind. Verwendet iterative Techniken, um Datensätze in Clustern zu gruppieren, die ähnliche Merkmale enthalten.|[Erkennen von Kategorien &#40;Tabellenanalyse Tools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)<br /><br /> [Cluster-Assistent &#40;Data Mining-Add-Ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)|  
|Microsoft Decision Trees|Trifft Vorhersagen auf der Grundlage der Beziehungen zwischen Spalten im Dataset und stellt die Beziehungen in einer strukturähnlichen Reihe von Teilungen für bestimmte Werte dar.<br /><br /> Unterstützt die Vorhersage für diskrete und kontinuierliche Attribute.|[Assistent zum Klassifizieren &#40;Data Mining-Add-Ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)<br /><br /> [Assistent zum Schätzen von Daten &#40;Data Mining-Add-Ins für Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)|  
|Microsoft Linear Regression|Findet im Fall einer linearen Abhängigkeit zwischen der Zielvariablen und den untersuchten Variablen die effizienteste Beziehung zwischen dem Zielelement und den zugehörigen Eingaben.<br /><br /> Unterstützt Vorhersagen für kontinuierliche Attribute.|Dieser Algorithmus ist in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verfügbar. In den Data Mining-Add-Ins für Office können Sie ein Modell erstellen, in dem dieser Algorithmus verwendet wird, indem Sie eine Struktur erstellen und dann manuell ein Modell hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [Erweiterte Modellierung &#40;Data Mining-Add-Ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Logistic Regression|Analysiert die Faktoren, die ein Ergebnis beeinflussen, wobei das Ergebnis auf zwei Werte beschränkt ist. Dabei handelt es sich üblicherweise um die Werte für das Eintreten oder Nichteintreten eines Ereignisses.<br /><br /> Unterstützt die Vorhersage für diskrete und kontinuierliche Attribute.|[Füllen Sie aus Beispiel &#40;Tabellenanalyse Tools für Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)<br /><br /> [Zielsuchszenario &#40;Tabellenanalyse Tools für Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Was-wäre-wenn-Szenario &#40;Tabellenanalyse Tools für Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)<br /><br /> [Vorhersagerechner &#40;Tabellenanalyse Tools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)|  
|Microsoft Naive Bayes|Berechnet die Wahrscheinlichkeit für die Beziehung zwischen allen Eingabespalten und vorhersagbaren Spalten. Mithilfe dieses Algorithmus können Sie schnell Miningmodelle zum Ermitteln von Beziehungen generieren.<br /><br /> Unterstützt nur diskrete und diskretisierte Attribute.<br /><br /> Behandelt alle Eingabeattribute unabhängig voneinander.|[Wichtige Einflussfaktoren &#40;Tabellenanalyse Tools für Excel analysieren&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)|  
|Microsoft Neural Network|Analysiert komplexe Eingabedaten oder Geschäftsprobleme, für die umfangreiche Trainingsdaten verfügbar sind, für die aber mithilfe anderer Algorithmen nicht problemlos Regeln abgeleitet werden können.<br /><br /> Kann mehrere Attribute vorhersagen.<br /><br /> Kann zum Klassifizieren diskreter Attribute und für die Regression kontinuierlicher Attribute verwendet werden.|Dieser Algorithmus ist in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] verfügbar. In den Data Mining-Add-Ins für Office können Sie ein Modell erstellen, in dem dieser Algorithmus verwendet wird, indem Sie eine Struktur erstellen und dann manuell ein Modell hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [Erweiterte Modellierung &#40;Data Mining-Add-Ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Sequence Clustering|Identifiziert Cluster ähnlich angeordneter Ereignisse in einer Sequenz.<br /><br /> Stellt eine Kombination aus Sequenzanalyse und Clustering bereit.|Dieser Algorithmus steht nur in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] zur Verfügung. In den Data Mining-Add-Ins für Office können Sie jedoch ein Modell erstellen, in dem dieser Algorithmus verwendet wird, indem Sie eine Struktur erstellen und dann ein Modell manuell hinzufügen.<br /><br /> Weitere Informationen finden Sie unter [Erweiterte Modellierung &#40;Data Mining-Add-Ins für Excel&#41;](advanced-modeling-data-mining-add-ins-for-excel.md).|  
|Microsoft Time Series|Analysiert zeitbezogene Daten mithilfe einer linearen Entscheidungsstruktur.<br /><br /> Muster können zur Vorhersage zukünftiger Werte in einer Zeitreihe verwendet werden.|[Vorhersage &#40;Tabellenanalyse Tools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)<br /><br /> [Planungs-Assistent &#40;Data Mining-Add-Ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Inhalt der Data Mining-Add-Ins für Office](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
