---
title: Erstellen von Datamining-Modells | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3c08737f07db68bd0e598844325d82172c3b1b44
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150681"
---
# <a name="creating-a-data-mining-model"></a>Erstellen eines Data Mining-Modells
  Die datenmodellierung wird der Schritt des Datamining, in dem Sie Muster und Trends erstellen durch Anwenden von *Algorithmen* an Daten. Später können Sie anhand dieser Muster Analysen ausführen oder Vorhersagen treffen.  
  
 Die Data Mining-Add-Ins für Office unterstützen das Data Mining über Assistenten, die das Erstellen von Modellen erleichtern. Mit den Assistenten werden Daten analysiert und Korrelationen identifiziert sowie die statistische Bedeutung aller Variablen berechnet und automatisch das beste Modell ausgewählt.  
  
 Obwohl diese Funktionalität ebenso leistungsstark wie die Data mining von bereitgestellten Tools ist [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], die Kombination aus Assistenten und der vertrauten Excel-Benutzeroberfläche erleichtert das Erstellen, ändern und Verwenden des Datamining.  
  
## <a name="advanced-data-mining"></a>Erweitert (Data Mining)  
 Die erweiterten Assistenten ermöglichen das Erstellen von neuen Datamining-Modelle basierend auf Daten in Excel gespeichert sind, mithilfe eines der Datamining-Algorithmen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
### <a name="create-mining-structure"></a>Miningstruktur erstellen  
 Der Strukturerstellungs-Assistent unterstützt Sie beim Erstellen einer neuen Data Mining-Struktur, die Sie als Grundlage für mehrere Miningmodelle verwenden können. Der Assistent bietet die Option, einen Teil der Daten für ein Testset zu reservieren. So können alle Modelle geschätzt werden, die dieselben Daten nach einem gleich bleibenden Teststandard verwenden.  
  
 [Erstellen der Miningstruktur &#40;SQL Server Data Mining-Add-ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a>Hinzufügen eines Modells zu einer Struktur  
 Der Assistent zum Hinzufügen eines Modells zu einer Struktur unterstützt Sie beim Auswählen einer vorhandenen Data Mining-Struktur und Erstellen eines neuen Data Mining-Modells für diese Struktur. Sie können mehrere Miningmodelle zu einer Struktur hinzufügen, wobei die Parameter geändert oder verschiedene Data Mining-Algorithmen ausgewählt werden und das Ergebnis angepasst wird.  
  
 [Hinzufügen eines Modells zu Struktur &#40;Data Mining-Add-ins für Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a>Wichtige Einflussfaktoren analysieren (Analysieren)  
 Sie wählen eine Spalte oder einen Ausgabewert von Interesse aus. Anschließend analysiert der Algorithmus alle Eingabedaten, um die Faktoren zu identifizieren, die den größten Einfluss auf das Ziel haben. Optional können Sie einen Bericht erstellen, in dem zwei beliebige Werte miteinander verglichen werden, sodass Sie feststellen können, wie sich die Einflussfaktoren ändern.  
  
 Die **wichtige Einflussfaktoren analysieren** Tool verwendet den Microsoft Naïve Bayes-Algorithmus.  
  
 [Wichtige Einflussfaktoren analysieren &#40;Tabellenanalysetools für Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a>Zuordnung [Data Mining]  
 Die **zuordnen** -Assistent erstellt ein Zuordnungsmodell, das elementzuordnungen erkennt, die in mehreren Transaktionen auftreten: z. B. in Warenkorbanalysen.  
  
 [Zuordnungs-Assistent &#40;Datamining-Client für Excel&#41;](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a>Klassifizieren (Data Mining)  
 Die **klassifizieren** -Assistent erstellt ein klassifizierungsmodell, das die Faktoren analysiert, die zum zielergebnis beigetragen haben. Mit diesem Assistenten können mehrere Algorithmen verwendet werden, u. a. Decision Trees, Naive Bayes und Neural Networks.  
  
 [Assistent zum Klassifizieren &#40;Data Mining-Add-ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a>Cluster (Data Mining)  
 Die **Cluster** Assistent erstellt ein Clustermodell, das Gruppen von Zeilen erkennt, die ähnliche Merkmale verfügen. Clustering (auch als bezeichnet *Segmentierung*) ist eine unüberwachte Lerntechnik, die sehr nützlich ist, wenn Sie versuchen, Muster und Gruppierungen in den neuen Daten zu verstehen.  
  
 Der Microsoft Clustering-Algorithmus unterstützt diverse Ausführungen des K-Means- und EM (Expectation Maximization)-Clustering.  
  
 [Cluster-Assistent &#40;Data Mining-Add-ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).  
  
## <a name="detect-categories-analyze"></a>Kategorien erkennen (Analysieren)  
 Die **Kategorien erkennen** Tool können Sie ein Dataset hinzufügen und das clustering anwenden, um Gruppierungen von Daten zu bestimmen. Es empfiehlt sich zum Ermitteln von Ähnlichkeiten sowie zum Erstellen von Gruppen, die weiter analysiert werden können.  
  
 Die **Kategorien erkennen** Tool verwendet Microsoft Clustering-Algorithmus.  
  
 [Kategorien erkennen &#40;Tabellenanalysetools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a>Schätzung (Data Mining)  
 Der Assistent zum Schätzen von Daten erstellt ein Schätzmodell, von dem Datenmuster extrahiert und die Muster verwendet werden, um kontinuierliche numerische Werte, Datums- oder Zeitwerte vorherzusagen. Er verwendet den [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus.  
  
 [Assistent zum Schätzen von &#40;Data Mining-Add-ins für Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a>Aus Beispiel füllen (Analysieren)  
 Die **aus Beispiel füllen** Tool können Sie beim Eingeben fehlender Werte. Sie geben einige Beispiele dafür an, worum es sich bei den fehlenden Werten handeln soll, und das Tool erstellt anhand sämtlicher Daten in der Tabelle Muster. Anschließend werden auf der Grundlage der Muster in den Daten neue Werte empfohlen.  
  
 Die **aus Beispiel füllen** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Aus Beispiel füllen &#40;Tabellenanalysetools für Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a>Planung (Analysieren)  
 Die **prognostizieren** Tool erfasst Daten, die mit der Zeit ändert, und sagt zukünftige Werte vorher.  
  
 Die **prognostizieren** Tool verwendet den Microsoft Time Series-Algorithmus.  
  
 [Prognose &#40;Tabellenanalysetools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a>Planung [Data Mining]  
 Die **prognostizieren** Assistent erstellt ein Planungsmodell, das Muster in einer Reihe von Zellen erkennt und anschließend weitere Werte vorhersagt.  
  
 [Planungs-Assistent &#40;Data Mining-Add-ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a>Ausnahmen hervorheben (Analysieren)  
 Die **Ausnahmen hervorheben** Tool analysiert Muster in einer Datentabelle und ermittelt Zeilen und Werte, die dem Muster nicht entsprechen. Sie können diese anschließend überprüfen und korrigieren und dann das Modell erneut ausführen oder Werte für spätere Maßnahmen mit Flags versehen.  
  
 Die **Ausnahmen hervorheben** Tool verwendet Microsoft Clustering-Algorithmus.  
  
 [Ausnahmen hervorheben &#40;Tabellenanalysetools für Excel&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a>Vorhersagerechner (Analysieren)  
 Dieses Tool erstellt ein Modell, in dem die Faktoren analysiert werden, die zu den Zielergebnissen führen. Anschließend wird ein Ergebnis für neue Eingaben vorhergesagt, wobei aus diesen Mustern abgeleitete Kriterien zugrunde gelegt werden. Zudem wird ein interaktives Arbeitsblatt zur Entscheidungsfindung generiert, in dem Sie neue Eingaben auf einfache Weise bewerten können. Sie können das Bewertungsarbeitsblatt auch ausdrucken und offline nutzen.  
  
 Die **Vorhersagerechner** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Vorhersagerechner &#40;Tabellenanalysetools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a>Szenario: Zielsuche (Analysieren)  
 In der **Zielsuche** Tool, Sie geben einen Zielwert und das Tool identifiziert die zugrunde liegenden Faktoren, die geändert werden müssen, damit dieses Ziel erreicht. Wenn Ihnen beispielsweise bekannt ist, dass die Kundenzufriedenheit in Bezug auf Anrufe um 20 % gesteigert werden muss, können Sie das Modell anweisen, die Faktoren vorherzusagen, die zum Erreichen dieses Ziels geändert werden müssen.  
  
 Die **Zielsuche** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 Details  
  
 [Zielsucheszenario &#40;Tabellenanalysetools für Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a>Szenario: Was-wäre-wenn-Szenario (Analysieren)  
 Die **Datenquellenwerte Analysis** tool ergänzt das **Zielsuche** Tool. Bei diesem Tool geben Sie den Wert ein, der geändert werden soll. Das Modell trifft eine Vorhersage, ob die betreffende Änderung zum Erreichen des gewünschten Ergebnisses ausreichend ist. Sie können beispielsweise das Modell anweisen abzuleiten, ob durch den Einsatz eines zusätzlichen Callcenter-Mitarbeiters die Kundenzufriedenheit um einen Punkt steigt.  
  
 Die **What-If** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Was-Wenn-Szenario &#40;Tabellenanalysetools für Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a>Warenkorbanalyse (Analysieren)  
 Die **Warenkorbanalyse** Tool erstellt Gruppen von Produkten, die häufig gekauft werden zusammen, um Muster identifiziert, die bei Cross-selling oder Up-Selling von nutzen. Zudem werden Berichte auf der Grundlage der Preise und Kosten für Bündel zusammengehöriger Produkte generiert, um die Entscheidungsfindung zu erleichtern.  
  
 Sie können dieses Tool für häufig zusammen auftretende Ereignisse, Faktoren für eine Diagnose oder sonstige potenzielle Ursachen und Ergebnisse verwenden.  
  
 Die **Warenkorbanalyse** Tool verwendet den Microsoft Association-Algorithmus.  
  
 [Warenkorbanalyse &#40;Tabelle AnalysisTools für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen und Bereinigen von Daten](exploring-and-cleaning-data.md)   
 [Überprüfen von Modellen und Verwenden von Modellen für Vorhersagen &#40;Data Mining-Add-ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Bereitstellen und Skalieren von Miningmodellen &#40;Data Mining-Add-ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  