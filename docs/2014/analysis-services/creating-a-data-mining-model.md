---
title: Erstellen eines Data Mining-Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a8893960b5177563ccf98dbd21cb528ce399ea3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086724"
---
# <a name="creating-a-data-mining-model"></a>Erstellen eines Data Mining-Modells
  Die Datenmodellierung ist der Schritt der Data Mining, in dem Sie Muster und Trends durch Anwenden von *Algorithmen* auf Daten erstellen. Später können Sie anhand dieser Muster Analysen ausführen oder Vorhersagen treffen.  
  
 Die Data Mining-Add-Ins für Office unterstützen das Data Mining über Assistenten, die das Erstellen von Modellen erleichtern. Mit den Assistenten werden Daten analysiert und Korrelationen identifiziert sowie die statistische Bedeutung aller Variablen berechnet und automatisch das beste Modell ausgewählt.  
  
 Obwohl diese Funktionalität jedes wenig leistungsfähig ist, wie die Data Mining Tools von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], erleichtert die Kombination von Assistenten und der vertrauten Excel-Oberfläche die Erstellung, Änderung und Verwendung von Data Mining.  
  
## <a name="advanced-data-mining"></a>Erweitert (Data Mining)  
 Mit den erweiterten Assistenten können Sie neue Data Mining Modelle basierend auf in Excel gespeicherten Daten erstellen, indem Sie einen der Data Mining Algorithmen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]verwenden.  
  
### <a name="create-mining-structure"></a>Erstellen einer Miningstruktur  
 Der Strukturerstellungs-Assistent unterstützt Sie beim Erstellen einer neuen Data Mining-Struktur, die Sie als Grundlage für mehrere Miningmodelle verwenden können. Der Assistent bietet die Option, einen Teil der Daten für ein Testset zu reservieren. So können alle Modelle geschätzt werden, die dieselben Daten nach einem gleich bleibenden Teststandard verwenden.  
  
 [Mining Struktur &#40;SQL Server Data Mining-Add-Ins erstellen&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a>Hinzufügen eines Modells zu einer Struktur  
 Der Assistent zum Hinzufügen eines Modells zu einer Struktur unterstützt Sie beim Auswählen einer vorhandenen Data Mining-Struktur und Erstellen eines neuen Data Mining-Modells für diese Struktur. Sie können mehrere Miningmodelle zu einer Struktur hinzufügen, wobei die Parameter geändert oder verschiedene Data Mining-Algorithmen ausgewählt werden und das Ergebnis angepasst wird.  
  
 [Hinzufügen eines Modells zu einer Struktur &#40;Data Mining-Add-Ins für Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a>Wichtige Einflussfaktoren analysieren (Analysieren)  
 Sie wählen eine Spalte oder einen Ausgabewert von Interesse aus. Anschließend analysiert der Algorithmus alle Eingabedaten, um die Faktoren zu identifizieren, die den größten Einfluss auf das Ziel haben. Optional können Sie einen Bericht erstellen, in dem zwei beliebige Werte miteinander verglichen werden, sodass Sie feststellen können, wie sich die Einflussfaktoren ändern.  
  
 Das Tool **wichtige Einflussfaktoren analysieren** verwendet den Microsoft Naive Bayes-Algorithmus.  
  
 [Wichtige Einflussfaktoren &#40;Tabellenanalyse Tools für Excel analysieren&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a>Zuordnung [Data Mining]  
 Der Zuordnungs-Assistent erstellt ein Zuordnungs Modell, das Zuordnungen zwischen Elementen erkennt **, die in** mehreren Transaktionen angezeigt werden, z. b. in Market Basket-Analysen.  
  
 [Assistenten &#40;Data Mining-Client für Excel zuordnen&#41;](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a>Klassifizieren (Data Mining)  
 Der Assistent zum **klassifizieren** erstellt ein Klassifizierungs Modell, das die Faktoren analysiert, die zu einem Zielergebnis beigetragen haben. Mit diesem Assistenten können mehrere Algorithmen verwendet werden, u. a. Decision Trees, Naive Bayes und Neural Networks.  
  
 [Assistent zum Klassifizieren &#40;Data Mining-Add-Ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a>Cluster (Data Mining)  
 Der **Cluster** -Assistent erstellt ein Clusteringmodell, das Gruppen von Zeilen erkennt, die ähnliche Merkmale aufweisen. Clustering (manchmal auch *Segmentierung*genannt) ist eine nicht überwachte Lerntechnik, die sehr nützlich ist, wenn Sie versuchen, Muster und Gruppierungen in neuen Daten zu verstehen.  
  
 Der Microsoft Clustering-Algorithmus unterstützt diverse Ausführungen des K-Means- und EM (Expectation Maximization)-Clustering.  
  
 Der [Cluster-Assistent &#40;Data Mining-Add-Ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).  
  
## <a name="detect-categories-analyze"></a>Kategorien erkennen (Analysieren)  
 Mit dem Tool **Kategorien erkennen** können Sie ein beliebiges DataSet hinzufügen und das Clustering anwenden, um Gruppierungen von Daten zu suchen. Es ist nützlich, um Ähnlichkeiten zu suchen und Gruppen zu erstellen, um Sie weiter zu analysieren.  
  
 Das Tool **Kategorien erkennen** verwendet den Microsoft Clustering-Algorithmus.  
  
 [Erkennen von Kategorien &#40;Tabellenanalyse Tools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a>Schätzung (Data Mining)  
 Der Assistent zum Schätzen von Daten erstellt ein Schätzmodell, von dem Datenmuster extrahiert und die Muster verwendet werden, um kontinuierliche numerische Werte, Datums- oder Zeitwerte vorherzusagen. Er verwendet den [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus.  
  
 [Assistent zum Schätzen von Daten &#40;Data Mining-Add-Ins für Excel&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a>Aus Beispiel füllen (Analysieren)  
 Mit dem Tool **aus Beispiel füllen** können Sie fehlende Werte angeben. Sie geben einige Beispiele dafür an, worum es sich bei den fehlenden Werten handeln soll, und das Tool erstellt anhand sämtlicher Daten in der Tabelle Muster. Anschließend werden auf der Grundlage der Muster in den Daten neue Werte empfohlen.  
  
 Das Tool **aus Beispiel füllen** verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Füllen Sie aus Beispiel &#40;Tabellenanalyse Tools für Excel&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a>Planung (Analysieren)  
 Das Tool für die **Vorhersage** nimmt Daten, die sich im Laufe der Zeit ändern, und prognostiziert zukünftige Werte.  
  
 Das Tool für die **Vorhersage** verwendet den Microsoft Time Series-Algorithmus.  
  
 [Vorhersage &#40;Tabellenanalyse Tools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a>Planung [Data Mining]  
 Der **Planungs** -Assistent erstellt ein Planungsmodell, das Muster in einer Reihe von Zellen erkennt und anschließend weitere Werte vorhersagt.  
  
 [Planungs-Assistent &#40;Data Mining-Add-Ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a>Ausnahmen hervorheben (Analysieren)  
 Das Tool **Ausnahmen hervorheben** analysiert Muster in einer Datentabelle und findet Zeilen und Werte, die nicht dem Muster entsprechen. Sie können diese anschließend überprüfen und korrigieren und dann das Modell erneut ausführen oder Werte für spätere Maßnahmen mit Flags versehen.  
  
 Das Tool **Ausnahmen hervorheben** verwendet den Microsoft Clustering-Algorithmus.  
  
 [Ausnahmen &#40;Tabellenanalyse Tools für Excel markieren&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a>Vorhersagerechner (Analysieren)  
 Dieses Tool erstellt ein Modell, in dem die Faktoren analysiert werden, die zu den Zielergebnissen führen. Anschließend wird ein Ergebnis für neue Eingaben vorhergesagt, wobei aus diesen Mustern abgeleitete Kriterien zugrunde gelegt werden. Zudem wird ein interaktives Arbeitsblatt zur Entscheidungsfindung generiert, in dem Sie neue Eingaben auf einfache Weise bewerten können. Sie können das Bewertungsarbeitsblatt auch ausdrucken und offline nutzen.  
  
 Das **Vorhersagerechner** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Vorhersagerechner &#40;Tabellenanalyse Tools für Excel&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a>Szenario: Zielsuche (Analysieren)  
 Im **zielsuchtool** geben Sie einen Zielwert an, und das Tool identifiziert die zugrunde liegenden Faktoren, die geändert werden müssen, um dieses Ziel zu erreichen. Wenn Ihnen beispielsweise bekannt ist, dass die Kundenzufriedenheit in Bezug auf Anrufe um 20 % gesteigert werden muss, können Sie das Modell anweisen, die Faktoren vorherzusagen, die zum Erreichen dieses Ziels geändert werden müssen.  
  
 Das Tool zur **Zielsuche** verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 Details  
  
 [Zielsuchszenario &#40;Tabellenanalyse Tools für Excel&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a>Szenario: Was-wäre-wenn-Szenario (Analysieren)  
 Das Tool **Was-wäre-wenn-Analyse** ergänzt das Tool zur **Zielsuche** . Bei diesem Tool geben Sie den Wert ein, der geändert werden soll. Das Modell trifft eine Vorhersage, ob die betreffende Änderung zum Erreichen des gewünschten Ergebnisses ausreichend ist. Sie können beispielsweise das Modell anweisen abzuleiten, ob durch den Einsatz eines zusätzlichen Callcenter-Mitarbeiters die Kundenzufriedenheit um einen Punkt steigt.  
  
 Das **Was-wäre-wenn-** Tool verwendet den Microsoft Logistic Regression-Algorithmus.  
  
 [Was-wäre-wenn-Szenario &#40;Tabellenanalyse Tools für Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a>Warenkorbanalyse (Analysieren)  
 Das **waren Korb Analyse** -Tool erstellt Gruppen von Produkten, die häufig in Kauf genommen werden, um Muster zu identifizieren, die bei Cross-Selling oder Up-Selling verwendet werden können. Zudem werden Berichte auf der Grundlage der Preise und Kosten für Bündel zusammengehöriger Produkte generiert, um die Entscheidungsfindung zu erleichtern.  
  
 Sie können dieses Tool für häufig zusammen auftretende Ereignisse, Faktoren für eine Diagnose oder sonstige potenzielle Ursachen und Ergebnisse verwenden.  
  
 Das **waren Korb Analyse** Tool verwendet den Microsoft Association-Algorithmus.  
  
 [Waren Korb Analyse &#40;Tabellenanalyse für Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen und Bereinigen von Daten](exploring-and-cleaning-data.md)   
 [Validieren von Modellen und Verwenden von Modellen für Vorhersage &#40;Data Mining-Add-Ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Bereitstellen und Skalieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
