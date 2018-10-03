---
title: Datamining-Algorithmen (Analysis Services – Datamining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation algorithms [Analysis Services]
- clustering [Data Mining]
- learning algorithms
- data mining [Analysis Services], models
- algorithms [data mining]
- mining models [Analysis Services], algorithms
- inductive learning
- mining models [Analysis Services], creating
- data mining [Analysis Services], algorithms
- machine learning algorithms [Analysis Services]
ms.assetid: ed1fc83b-b98c-437e-bf53-4ff001b92d64
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 490857f9a8c95853d3f89bc8b0cfb85a165f1fd1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218570"
---
# <a name="data-mining-algorithms-analysis-services---data-mining"></a>Data Mining-Algorithmen (Analysis Services - Data Mining)
  Ein *Datamining-Algorithmus* ist ein Satz von Heuristiken und Berechnungen, die Datamining-Modells aus Daten erstellt. Um ein Modell zu erstellen, werden vom Algorithmus zuerst die von Ihnen bereitgestellten Daten analysiert und bestimmte Muster oder Trends gesucht. Mithilfe der Ergebnisse dieser Analyse definiert der Algorithmus die optimalen Parameter zum Erstellen des Miningmodells. Diese Parameter werden dann für das gesamte Dataset übernommen, um aussagefähige Muster und ausführliche Statistiken zu extrahieren.  
  
 Das von einem Algorithmus aus Ihren Daten erstellte Miningmodell kann verschiedene Formen annehmen, einschließlich der folgenden:  
  
-   Eine Reihe von Clustern, die die Beziehungen der Fälle in einem Dataset beschreiben.  
  
-   Eine Entscheidungsstruktur, durch die ein Ergebnis vorhergesagt und beschrieben wird, wie sich unterschiedliche Kriterien auf dieses Ergebnis auswirken.  
  
-   Ein mathematisches Modell zum Vorhersagen von Umsätzen.  
  
-   Eine Gruppe von Regeln, die beschreiben, wie Produkte in einer Transaktion gruppiert werden, und die Wahrscheinlichkeiten, dass Produkte zusammen gekauft werden.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bietet mehrere Algorithmen für die Verwendung in den Datamining-Projektmappen. Diese Algorithmen stellen Implementierungen der bekanntesten im Data Mining verwendeten Methoden dar. Alle Data Mining-Algorithmen von Microsoft können angepasst und unter Verwendung der bereitgestellten APIs oder Data Mining-Komponenten in SQL Server Integration Services vollständig programmiert werden.  
  
 Sie können auch Drittanbieter-Algorithmen verwenden, die mit OLE DB-Spezifikation für Data Mining oder benutzerdefinierte Algorithmen entwickeln, die als Dienste registriert und dann innerhalb des SQL Server Data Mining-Frameworks verwendet werden können.  
  
## <a name="choosing-the-right-algorithm"></a>Auswählen des richtigen Algorithmus  
 Es kann schwierig sein, den besten Algorithmus für einen bestimmten analytischen Task auszuwählen. Während verschiedene Algorithmen zum Ausführen derselben Geschäftsaufgabe verwendet werden können, liefert jeder Algorithmus ein anderes Ergebnis, und einige Algorithmen können mehr als eine Ergebnisart ergeben. Sie können z. B. den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees-Algorithmus nicht nur für Vorhersagen verwenden, sondern auch als Möglichkeit, die Anzahl der Spalten in einem Dataset zu reduzieren, weil die Entscheidungsstruktur Spalten identifizieren kann, die sich nicht auf das endgültige Miningmodell auswirken.  
  
### <a name="choosing-an-algorithm-by-type"></a>Auswählen eines Algorithmus nach Typ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält die folgenden Algorithmentypen:  
  
-   **Klassifikationsalgorithmen** sagen basierend auf den anderen Attributen im Dataset mindestens eine diskrete Variable voraus.  
  
-   **Regressionsalgorithmen** Vorhersagen einer oder mehrerer kontinuierliche Variablen, wie z. B. den Gewinn oder Verlust basierend auf anderen Attributen im Dataset.  
  
-   **Segmentierungsalgorithmen** teilen Daten in Gruppen oder Cluster aus Elementen auf, die ähnliche Eigenschaften haben.  
  
-   **Zuordnungsalgorithmen** suchen nach Korrelationen zwischen verschiedenen Attributen in einem Dataset. Die häufigste Anwendung dieser Algorithmusart besteht im Erstellen von Zuordnungsregeln, die für eine Warenkorbanalyse verwendet werden können.  
  
-   **Sequenzanalysealgorithmen** fassen häufige datensequenzen oder -periodizitäten zusammen, wie z. B. einen webpfadfluss.  
  
 Es gibt jedoch keinen Grund, sich in Projektmappen auf einen Algorithmus zu beschränken. Erfahrene Analytiker verwenden manchmal einen Algorithmus, um die effizientesten Eingaben (d. h. Variablen) zu bestimmen, und wenden dann einen anderen Algorithmus an, um ein bestimmtes Ergebnis auf Grundlage dieser Daten vorherzusagen. Mithilfe von SQL Server Data Mining können Sie mehrere Modelle für eine einzelne Miningstruktur erstellen. Daher können innerhalb einer einzelnen Data Mining-Projektmappe ein Clustering-Algorithmus, ein Entscheidungsstrukturmodell und ein Naïve Bayes-Modell verwendet werden, um unterschiedliche Sichten der Daten zu erhalten. Sie können mithilfe mehrerer Algorithmen in einer einzelnen Projektmappe auch separate Tasks ausführen: Beispielsweise können Sie mit dem Regressionsalgorithmus eine finanzielle Vorhersage generieren und mit dem Neural Network-Algorithmus die Faktoren analysieren, durch die der Umsatz beeinflusst wird.  
  
### <a name="choosing-an-algorithm-by-task"></a>Auswählen eines Algorithmus nach Task  
 Um Ihnen die Auswahl eines Algorithmus für einen bestimmten Task zu erleichtern, ist in der folgende Tabelle angegeben, für welche Tasktypen die einzelnen Algorithmen üblicherweise verwendet werden.  
  
|Beispiele für Tasks|Microsoft-Algorithmen|  
|-----------------------|---------------------------------|  
|**Vorhersagen eines diskreten Attributs**<br /><br /> Kennzeichnen von Kunden in einer Liste potenzieller Käufer als Kunden mit wahrscheinlicher oder unwahrscheinlicher Kaufabsicht.<br /><br /> Berechnen der Wahrscheinlichkeit, dass ein Server innerhalb der nächsten sechs Monate ausfällt.<br /><br /> Kategorisieren von Therapieergebnissen und Untersuchen verwandter Faktoren.|[Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft Naive Bayes-Algorithmus](microsoft-naive-bayes-algorithm.md)<br /><br /> [Microsoft Clustering-Algorithmus](microsoft-clustering-algorithm.md)<br /><br /> [Microsoft Neural Network-Algorithmus](microsoft-neural-network-algorithm.md)|  
|**Vorhersagen eines kontinuierlichen Attributs**<br /><br /> Vorhersagen des Verkaufstrends für das nächste Jahr.<br /><br /> Vorhersagen von Websitebesuchern anhand historischer und saisonaler Trends.<br /><br /> Generieren einer Risikobewertung anhand demografischer Daten.|[Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft Time Series-Algorithmus](microsoft-time-series-algorithm.md)<br /><br /> [Microsoft Linear Regression-Algorithmus](microsoft-linear-regression-algorithm.md)|  
|**Vorhersagen einer Sequenz**<br /><br /> Ausführen einer Clickstreamanalyse für eine Unternehmenswebsite.<br /><br /> Analysieren der Faktoren, die zu einem Serverausfall führen.<br /><br /> Aufzeichnen und Analysieren von Arbeitsabläufen während ambulanter Arztbesuche, um Best Practices für allgemeine Abläufe aufzustellen.|[Microsoft Sequence Clustering-Algorithmus](microsoft-sequence-clustering-algorithm.md)|  
|**Suchen von Gruppen aus allgemeinen Elementen in Transaktionen**<br /><br /> Bestimmen der Produktplatzierung mithilfe der Warenkorbanalyse.<br /><br /> Vorschlagen zusätzlicher Produktkäufe für einen Kunden.<br /><br /> Analysieren einer Besucherumfrage zu einer Veranstaltung, um festzustellen, welche Aktivitäten oder Stände eine Korrelation aufweisen, und zukünftige Aktivitäten zu planen.|[Microsoft Association-Algorithmus](microsoft-association-algorithm.md)<br /><br /> [Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm.md)|  
|**Suchen von Gruppen mit ähnlichen Elementen**<br /><br /> Gruppieren von Patientenrisikoprofilen auf der Grundlage von Attributen wie demografischen oder Verhaltensdaten.<br /><br /> Analysieren von Benutzern anhand von Browsing- und Kaufmustern.<br /><br /> Identifizieren von Servern mit ähnlichen Verwendungsmerkmalen.|[Microsoft Clustering-Algorithmus](microsoft-clustering-algorithm.md)<br /><br /> [Microsoft Sequence Clustering-Algorithmus](microsoft-sequence-clustering-algorithm.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Die folgende Tabelle enthält Links zu Schulungsressourcen für die einzelnen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitgestellten Data Mining-Algorithmen:  
  
|||  
|-|-|  
|**Grundlegende Algorithmusbeschreibung**|Erläutert die Bedeutung und Funktionsweise des Algorithmus und zeigt mögliche Geschäftsszenarien auf, in denen der Algorithmus hilfreich sein könnte.|  
||[Microsoft Association-Algorithmus](microsoft-association-algorithm.md)<br /><br /> [Microsoft Clustering-Algorithmus](microsoft-clustering-algorithm.md)<br /><br /> [Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm.md)<br /><br /> [Microsoft Linear Regression-Algorithmus](microsoft-linear-regression-algorithm.md)<br /><br /> [Microsoft Logistic Regression-Algorithmus](microsoft-logistic-regression-algorithm.md)<br /><br /> [Microsoft Naive Bayes-Algorithmus](microsoft-naive-bayes-algorithm.md)<br /><br /> [Microsoft Neural Network-Algorithmus](microsoft-neural-network-algorithm.md)<br /><br /> [Microsoft Sequence Clustering-Algorithmus](microsoft-sequence-clustering-algorithm.md)<br /><br /> [Microsoft Time Series-Algorithmus](microsoft-time-series-algorithm.md)|  
|**Technische Referenz**|Stellt technische Details zur Implementierung des Algorithmus ggf. mit Verweisen auf wissenschaftliche Artikel bereit. Listet die Parameter auf, die Sie festlegen können, um das Verhalten des Algorithmus zu steuern und die Ergebnisse im Modell anzupassen. Beschreibt Datenanforderungen sowie Leistungstipps, falls möglich.|  
||[Technische Referenz für den Microsoft Association-Algorithmus](microsoft-association-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Clustering-Algorithmus](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Decision Trees-Algorithmus](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Linear Regression-Algorithmus](microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Logistic Regression-Algorithmus](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Naive Bayes-Algorithmus](microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Neural Network-Algorithmus](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Sequence Clustering-Algorithmus](microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [Technische Referenz für den Microsoft Time Series-Algorithmus](microsoft-time-series-algorithm-technical-reference.md)|  
|**Modellinhalt**|Beschreibt die Strukturierung der Informationen innerhalb der einzelnen Data Mining-Modelltypen und erläutert, wie die in den einzelnen Knoten gespeicherten Informationen interpretiert werden.|  
||[Mingingmodellinhalt von Clustermodellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-association-models-analysis-services-data-mining.md)<br /><br /> [Mingingmodellinhalt von Clustermodellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-clustering-models-analysis-services-data-mining.md)<br /><br /> [Mingingmodellinhalt von Entscheidungsstrukturmodellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)<br /><br /> [Mingingmodellinhalt von linearen Regressionsmodellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)<br /><br /> [Mingingmodellinhalt von logistischen Regressionsmodellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-logistic-regression-models.md)<br /><br /> [Mingingmodellinhalt von Naive Bayes-Modellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)<br /><br /> [Mingingmodellinhalt von neuronalen Netzwerkmodellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)<br /><br /> [Mingingmodellinhalt von Sequence Clustering-Modellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-sequence-clustering-models.md)<br /><br /> [Mingingmodellinhalt von Zeitreihenmodellen &#40;Analysis Services – Datamining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md)|  
|**Data Mining-Abfragen**|Stellt mehrere Abfragen bereit, die mit jedem Modelltyp verwendet werden können. Zu den Beispielen gehören Inhaltsabfragen, die Aufschluss über die im Modell enthaltenen Muster geben, und Vorhersageabfragen, die Sie beim Generieren von Vorhersagen auf Grundlage dieser Muster unterstützen.|  
||[Beispiele für Zuordnungsmodellabfragen](association-model-query-examples.md)<br /><br /> [Beispiele für Clusteringmodellabfragen](clustering-model-query-examples.md)<br /><br /> [Beispiele für Entscheidungsstruktur-Modellabfragen](decision-trees-model-query-examples.md)<br /><br /> [Beispiele für lineare Regressionsmodellabfragen](linear-regression-model-query-examples.md)<br /><br /> [Beispiele für logistische Regressionsmodellabfragen](logistic-regression-model-query-examples.md)<br /><br /> [Beispiele für Naive Bayes-Modellabfragen](naive-bayes-model-query-examples.md)<br /><br /> [Beispiele für Abfragen von neuronalen Netzwerkmodellen](neural-network-model-query-examples.md)<br /><br /> [Beispiele für Abfragen von Sequenzclustermodellen](sequence-clustering-model-query-examples.md)<br /><br /> [Beispiele für Abfragen von Zeitreihenmodellen](time-series-model-query-examples.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|**Thema**|**Beschreibung**|  
|---------------|---------------------|  
|Bestimmen des von einem Data Mining-Modell verwendeten Algorithmus|[Abfragen der für die Erstellung eines Miningmodell verwendeten Parameter](query-the-parameters-used-to-create-a-mining-model.md)|  
|Erstellen eines benutzerdefinierten Plug-In-Algorithmus|[Plug-In-Algorithmen](plugin-algorithms.md)|  
|Durchsuchen eines Modells mit einem algorithmusspezifischen Viewer|[Data Mining-Modell-Viewer](data-mining-model-viewers.md)|  
|Anzeigen des Inhalts eines Modells unter Verwendung eines generischen Tabellenformats|[Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)|  
|Hier erfahren Sie, wie die Daten eingerichtet und Algorithmen zum Erstellen von Modellen verwendet werden|[Miningstrukturen &#40;Analysis Services – Datamining&#41;](mining-structures-analysis-services-data-mining.md)<br /><br /> [Miningmodelle &#40;Analysis Services – Datamining&#41;](mining-models-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Tools](data-mining-tools.md)  
  
  
