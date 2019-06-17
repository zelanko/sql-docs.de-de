---
title: Datamining-Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- prediction queries [Analysis Services]
- queries [DMX], creating
- prediction queries [DMX]
- Prediction Query Builder
- mining models [Analysis Services], querying
ms.assetid: 802806a6-69bb-4c3c-b9aa-d1a1ddfc7fc2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2bfce63f3686f06c0289c818daac82f336fb2b17
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66084971"
---
# <a name="data-mining-queries"></a>Data Mining-Abfragen
  Data Mining-Abfragen eignen sich für viele Zwecke. Folgende Aktionen sind möglich:  
  
-   Anwenden des Modells auf neue Daten, um einzelne oder mehrere Vorhersagen zu treffen. Sie können Eingabewerte als Parameter oder in einem Batch bereitstellen.  
  
-   Abrufen einer statistischen Zusammenfassung der für das Training verwendeten Daten.  
  
-   Extrahieren von Mustern und Regeln oder Generieren eines Profils des typischen Falls, der ein Muster im Modell darstellt.  
  
-   Extrahieren von Regressionsformeln und anderen Berechnungen zur Erklärung von Mustern.  
  
-   Abrufen der Fälle, die einem bestimmten Muster entsprechen.  
  
-   Abrufen von Details zu einzelnen im Modell verwendeten Fällen, einschließlich in der Analyse nicht verwendeter Daten.  
  
-   Erneutes Trainieren eines Modells durch Hinzufügen neuer Daten oder Ausführen einer Kreuzvorhersage  
  
 Dieser Abschnitt bietet eine Übersicht über die Informationen, die Sie für die ersten Schritte mit Data Mining-Abfragen benötigen. Er beschreibt die Typen von Abfragen, die Sie für Data Mining-Objekte erstellen können, bietet eine Einführung in die Abfragetools und Abfragesprachen und stellt Links zu Beispielen für Abfragen bereit, die Sie für Modelle erstellen können, die mit den in SQL Server Data Mining verfügbaren Algorithmen erstellt wurden.  
  
 [Grundlegendes zu Data Mining-Abfragen](#bkmk_Understand)  
  
 [Abfragetools und -schnittstellen](#bkmk_Interfaces)  
  
 [Abfragen für unterschiedliche Modelltypen](#bkmk_ModelTypes)  
  
 [Anforderungen](#bkmk_Reqs)  
  
##  <a name="bkmk_Understand"></a> Grundlegendes zu Data Mining-Abfragen  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Data Mining unterstützt die folgenden Typen von Abfragen:  
  
-   [Vorhersageabfragen &#40;Data Mining&#41;](prediction-queries-data-mining.md)  
  
     Abfragen, mit denen Rückschlüsse anhand von Mustern im Modell und aus Eingabedaten gezogen werden können.  
  
-   [Inhaltsabfragen &#40;Data Mining&#41;](content-queries-data-mining.md)  
  
     Abfragen, die Metadaten, Statistiken und andere Informationen zum Modell selbst zurückgeben.  
  
-   [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md)  
  
     Abfragen, die die zugrunde liegenden Falldaten für das Modell und sogar Daten, die nicht im Modell verwendet wurden, aus der Struktur abrufen können.  
  
-   [Datendefinitionsabfragen &#40;Data Mining&#41;](data-definition-queries-data-mining.md)  
  
     Abfragen, die keine Informationen aus dem Modell zurückgeben, sondern zum Erstellen von Modellen und Strukturen oder zum Aktualisieren der Daten in einem Modell oder einer Struktur verwendet werden.  
  
 Bevor Sie Abfragen erstellen, sollten Sie sich mit den Unterschieden zwischen den Modellen vertraut machen, die mit den verschiedenen von SQL Server bereitgestellten Data Mining-Algorithmen erstellt werden können.  
  
-   Durchsuchen und untersuchen Sie jeden Modelltyp mit den benutzerdefinierten Data Mining-Viewern, die für jeden Algorithmustyp zur Verfügung stehen. Weitere Informationen finden Sie unter [Tasks und Anweisungen für Miningmodell-Viewer](mining-model-viewer-tasks-and-how-tos.md).  
  
-   Überprüfen Sie den Modellinhalt für jeden Modelltyp mit dem **Microsoft Generic Content Tree Viewer**. Weitere Informationen zum Interpretieren dieser Informationen finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).  
  
##  <a name="bkmk_Interfaces"></a> Abfragetools und -schnittstellen  
 Sie können Data Mining-Abfragen interaktiv mit einem der von SQL Server bereitgestellten Abfragetools erstellen. Der grafische Generator für Vorhersageabfragen ist sowohl in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] als auch in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verfügbar. Wenn Sie den Generator für Vorhersageabfragen bisher noch nicht verwendet haben, empfehlen wir, die Schritte im [Data Mining-Lernprogramm](../../tutorials/basic-data-mining-tutorial.md) durchzuarbeiten, um sich mit der Oberfläche vertraut zu machen. Kurze Übersicht der Schritte, finden Sie unter Erstellen einer Abfrage mit der [erstellt eine Vorhersage mithilfe des Generators für Vorhersageabfragen](create-a-prediction-query-using-the-prediction-query-builder.md).  
  
 Der Generator für Vorhersageabfragen ist nützlich zum Erstellen grundlegender Abfragen, die Sie später weiter anpassen können. Sie können Datenquellen leicht hinzufügen und Spalten zuordnen und dann zu DMX wechseln und die Abfrage anpassen, indem Sie eine WHERE-Klausel oder andere Funktionen hinzufügen.  
  
 Sobald Sie mit den Data Mining-Modellen und dem Erstellen von Abfragen vertraut sind, können Sie die Abfragen auch direkt mithilfe der Data Mining-Erweiterungen (Data Mining Extensions, DMX) schreiben. DMX ist eine Abfragesprache, die Transact-SQL ähnelt und in vielen verschiedenen Clients verwendet werden kann. DMX ist das bevorzugte Tool zum Erstellen von benutzerdefinierten Vorhersagen und komplexen Abfragen. Eine Einführung zu DMX finden Sie unter [erstellen und Abfragen von Data Mining-Modellen mit DMX: Lernprogramme &#40;Analysis Services – Datamining&#41;](../../tutorials/create-query-data-mining-models-dmx-tutorials.md).  
  
 DMX-Editoren werden sowohl in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] als auch in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bereitgestellt. Sie können Abfragen auch zunächst mit dem Generator für Vorhersageabfragen erstellen und dann zur Text-Editor-Ansicht wechseln und die DMX-Anweisung in einen anderen Client kopieren. Weitere Informationen finden Sie unter [Data Mining-Abfrageschnittstellen](data-mining-query-tools.md).  
  
 Sie können DMX-Anweisungen programmgesteuert erstellen und sie mit AMO oder XMLA vom Client an den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Server senden. Zum Erstellen von Abfragen für ein Miningmodell müssen Sie jedoch immer DMX verwenden.  
  
 Sie können die Metadaten, Statistiken und bestimmte Inhalte des Modells auch mit dynamischen Verwaltungssichten (Dynamic Management Views, DMVs) abfragen, die auf den Data Mining-Schemarowsets basieren. DMVs erleichtern das Abrufen von Modellinformationen durch die Eingabe von SELECT-Anweisungen, unterstützten jedoch nicht das Erstellen von Vorhersagen. Weitere Informationen zu den von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützten DMVs finden Sie unter [Verwenden von dynamischen Verwaltungssichten &#40;DMVs&#41; zum Überwachen von Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md).  
  
 Schließlich können Sie mithilfe von [Data Mining-Abfrageaufgabe](../../integration-services/control-flow/data-mining-query-task.md)oder [Transformation für Data Mining-Abfragen](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)Data Mining-Abfragen zur Verwendung in Integration Services-Paketen erstellen. Der Ablaufsteuerungstask unterstützt mehrere Typen von DMX-Abfragen, während die Datenflusstransformation nur Abfragen unterstützt, die Daten im Datenfluss verarbeiten, d. h. Abfragen, die die PREDICTION JOIN-Syntax verwenden.  
  
##  <a name="bkmk_ModelTypes"></a> Abfragen für unterschiedliche Modelltypen  
 Der Algorithmus, der beim Erstellen des Modells verwendet wurde, hat großen Einfluss auf die Art von Informationen, die Sie mit einer Data Mining-Abfrage abrufen können. Der Grund für die Unterschiede ist, dass jeder Algorithmus die Daten auf eine andere Weise verarbeitet und andere Arten von Mustern speichert. Einige Algorithmen erstellen z. B. Cluster, andere erstellen Strukturen. Daher müssen Sie ggf. spezialisierte Vorhersage- und Abfragefunktionen verwenden, abhängig vom Modelltyp, mit dem Sie arbeiten.  
  
 Die folgende Liste bietet eine Zusammenfassung der Funktionen, die Sie in Abfragen verwenden können:  
  
-   **Allgemeine Vorhersagefunktionen:** Die `Predict` -Funktion ist polymorph, d. h., es funktioniert mit allen Modelltypen verwendet. Diese Funktion erkennt automatisch den Modelltyp, mit dem Sie arbeiten, und fordert Sie zur Eingabe zusätzlicher Parameter auf. Weitere Informationen finden Sie unter [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx).  
  
    > [!WARNING]  
    >  Nicht alle Modelle werden verwendet, um Vorhersagen zu treffen. Beispielsweise können Sie ein Clusteringmodell erstellen, das über kein vorhersagbares Attribut verfügt. Aber selbst wenn ein Modell nicht über ein vorhersagbares Attribut verfügt, können Sie Vorhersageabfragen erstellen, die andere Typen nützlicher Informationen aus dem Modell zurückgeben.  
  
-   **Benutzerdefinierte Vorhersagefunktionen:** Jeder Modelltyp stellt einen Satz von Vorhersagefunktionen, die zum Arbeiten mit den von diesem Algorithmus erstellten Mustern entworfen wurden.  
  
     Für Zeitreihenmodelle wird z. B. die `Lag`-Funktion bereitgestellt, mit der Sie die Vergangenheitsdaten anzeigen können, die für das Modell verwendet wurden. Bei Clusteringmodellen liefern z. B. Funktionen wie `ClusterDistance` sinnvollere Informationen.  
  
     Weitere Informationen zu den Funktionen, die für jeden Modelltyp unterstützt werden, finden Sie unter den folgenden Links:  
  
    |||  
    |-|-|  
    |[Beispiele für Zuordnungsmodellabfragen](association-model-query-examples.md)|[Microsoft Naive Bayes-Algorithmus](microsoft-naive-bayes-algorithm.md)|  
    |[Beispiele für Clusteringmodellabfragen](clustering-model-query-examples.md)|[Beispiele für Abfragen von neuronalen Netzwerkmodellen](neural-network-model-query-examples.md)|  
    |[Beispiele für Entscheidungsstruktur-Modellabfragen](decision-trees-model-query-examples.md)|[Beispiele für Abfragen von Sequenzclustermodellen](sequence-clustering-model-query-examples.md)|  
    |[Beispiele für lineare Regressionsmodellabfragen](linear-regression-model-query-examples.md)|[Beispiele für Abfragen von Zeitreihenmodellen](time-series-model-query-examples.md)|  
    |[Beispiele für logistische Regressionsmodellabfragen](logistic-regression-model-query-examples.md)||  
  
     Sie können auch VBA-Funktionen aufrufen oder eigene Funktionen erstellen. Weitere Informationen finden Sie unter [Funktionen &#40;DMX&#41;](/sql/dmx/functions-dmx).  
  
-   **Allgemeine Statistiken:** Es gibt eine Anzahl von Funktionen, die mit nahezu jedem Modelltyp verwendet werden kann, die einen Standardsatz von beschreibenden Statistiken, wie z. B. die Standardabweichung zurückgibt.  
  
     Die `PredictHistogram`-Funktion gibt z. B. eine Tabelle zurück, in der alle Status der angegebenen Spalte aufgeführt sind.  
  
     Weitere Informationen finden Sie unter [Allgemeine Vorhersagefunktionen &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).  
  
-   **Benutzerdefinierte Statistiken:** Für jeden Modelltyp, um Statistiken zu generieren, die für die spezifische analytische Aufgabe relevant sind, werden zusätzliche unterstützende Funktionen bereitgestellt.  
  
     Wenn Sie z. B. mit einem Clusteringmodell arbeiten, können Sie die `PredictCaseLikelihood`-Funktion verwenden, um das einem bestimmten Fall und Cluster zugeordnete Wahrscheinlichkeitsergebnis zurückzugeben. Wenn Sie hingegen ein lineares Regressionsmodell erstellen, ist das Abrufen und Abfangen des Koeffizienten von größerer Bedeutung. In diesem Fall können Sie eine Inhaltsabfrage verwenden.  
  
-   **Modellfunktionen:** Die *Inhalt* aller Modelle dargestellt, in einem standardisierten Format, in dem Sie mit einer einfachen Abfrage Informationen abrufen kann. Zum Erstellen von Abfragen für den Modellinhalt verwenden Sie DMX. Einige Modellinhaltstypen können Sie auch mithilfe der Data Mining-Schemarowsets abfragen.  
  
     Im Modellinhalt ist die Bedeutung jeder Zeile bzw. jedes Knoten der Tabelle, die zurückgegeben wird, abhängig vom Typ des Algorithmus, der zum Erstellen des Modells verwendet wurde. Dies gilt ebenso für den Datentyp der Spalte. Weitere Informationen finden Sie unter [Inhaltsabfragen &#40;Data Mining&#41;](content-queries-data-mining.md).  
  
##  <a name="bkmk_Reqs"></a> Anforderungen  
 Bevor Sie eine Abfrage für ein Modell erstellen können, muss das Data Mining-Modell bereits verarbeitet sein. Für die Verarbeitung von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekten sind spezielle Berechtigungen erforderlich. Weitere Informationen zum Verarbeiten von Miningmodellen finden Sie unter [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md).  
  
 Um Abfragen für ein Data Mining-Modell auszuführen, sind je nach Typ der auszuführenden Abfrage unterschiedliche Berechtigungsstufen erforderlich. Zum Beispiel erfordert ein Drillthrough der Fall- oder Strukturdaten in der Regel zusätzliche Berechtigungen, die für das Miningstrukturobjekt oder das Miningmodellobjekt festgelegt werden können.  
  
 Wenn die Abfrage jedoch externe Daten verwendet und Anweisungen wie OPENROWSET oder OPENQUERY beinhaltet, müssen diese Anweisungen in der Datenbank, die Sie abfragen, aktiviert werden, und Sie müssen über Berechtigungen für die zugrunde liegenden Datenbankobjekte verfügen.  
  
 Weitere Informationen zu den Sicherheitskontexten, die zum Ausführen von Data Mining-Abfragen erforderlich sind, finden Sie unter [Sicherheitsübersicht &#40;Data Mining&#41;](security-overview-data-mining.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die Themen in diesem Abschnitt stellen jeden Data Mining-Abfragetyp im Detail vor und enthalten Links zu ausführlichen Beispielen für das Erstellen von Abfragen für Data Mining-Modelle.  
  
 [Vorhersageabfragen &#40;Data Mining&#41;](prediction-queries-data-mining.md)  
  
 [Inhaltsabfragen &#40;Data Mining&#41;](content-queries-data-mining.md)  
  
 [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md)  
  
 [Datendefinitionsabfragen &#40;Data Mining&#41;](data-definition-queries-data-mining.md)  
  
 [Schnittstellen für Data Mining-Abfragen](data-mining-query-tools.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Über diese Links erhalten Sie Informationen zum Erstellen und Verwenden von Data Mining-Abfragen.  
  
|Richtlinienübersicht|Links|  
|-----------|-----------|  
|Lernprogramme und exemplarische Vorgehensweisen zu Data Mining-Abfragen|[Lektion 6: Erstellen und Verwenden von Vorhersagen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)<br /><br /> [DMX-Tutorial für Zeitreihenvorhersagen](../../tutorials/time-series-prediction-dmx-tutorial.md)|  
|Verwenden von Data Mining-Abfragetools in SQL Server Management Studio und [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|[Erstellen einer DMX-Abfrage in SQL Server Management Studio](create-a-dmx-query-in-sql-server-management-studio.md)<br /><br /> [erstellt eine Vorhersage mithilfe des Generators für Vorhersageabfragen](create-a-prediction-query-using-the-prediction-query-builder.md)<br /><br /> [Anwenden von Vorhersagefunktionen auf ein Modell](apply-prediction-functions-to-a-model.md)<br /><br /> [Manuelles Bearbeiten eine Vorhersageabfrage](manually-edit-a-prediction-query.md)|  
|Arbeiten mit externen, in Vorhersageabfragen verwendeten Daten|[Auswählen und Zuordnen von Eingabedaten für eine Vorhersageabfrage](choose-and-map-input-data-for-a-prediction-query.md)<br /><br /> [Auswählen und Zuordnen von Eingabedaten für eine Vorhersageabfrage](choose-and-map-input-data-for-a-prediction-query.md)|  
|Arbeiten mit Abfrageergebnissen|[Anzeigen und Speichern der Ergebnisse einer Vorhersageabfrage](view-and-save-the-results-of-a-prediction-query.md)|  
|Verwenden der in Management Studio verfügbaren DMX- und XMLA-Abfragevorlagen|[Erstellen Sie eine Singleton-Abfrage aus einer Vorlage](create-a-singleton-prediction-query-from-a-template.md)<br /><br /> [Erstellen einer Data Mining-Abfrage mit XMLA](create-a-data-mining-query-by-using-xmla.md)<br /><br /> [Verwenden von Analysis Services-Vorlagen in SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|Weitere Informationen zu Inhaltsabfragen und Beispiele|[Erstellen einer Miningmodell-Inhaltsabfrage](create-a-content-query-on-a-mining-model.md)<br /><br /> [Abfragen der Parameter, mit denen ein Miningmodell erstellt wird](query-the-parameters-used-to-create-a-mining-model.md)<br /><br /> [Inhaltsabfragen &#40;Data Mining&#41;](content-queries-data-mining.md)|  
|Festlegen von Abfrageoptionen und Problembehandlung bei Abfrageberechtigungen und Abfragen|[Ändern des Timeoutwerts für Data Mining-Abfragen](data-mining-queries.md)|  
|Verwenden der Data Mining-Komponenten in Integration Services|[Data Mining-Abfragetask](../../integration-services/control-flow/data-mining-query-task.md)<br /><br /> [Transformation für Data Mining-Abfragen](../../integration-services/data-flow/transformations/data-mining-query-transformation.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](mining-model-content-analysis-services-data-mining.md)  
  
  
