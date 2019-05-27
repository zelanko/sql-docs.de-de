---
title: Durchsuchen eines neuronalen Netzwerkmodells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- mining model, neural network
- neural networks
- dependency network
ms.assetid: e4224cb7-115b-4889-ac07-03f096fb55fc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e4dcb323a309125695df6d3c483f8996d36fdfd
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66088453"
---
# <a name="browsing-a-neural-network-model"></a>Durchsuchen von Neural Network-Modellen
  Wenn Sie ein neuronales Netzwerk oder ein logistisches Regressionsmodell mithilfe von **Durchsuchen** öffnen, wird das Modell in einem interaktiven Viewer angezeigt, der mit dem Viewer für neuronale Netzwerkmodelle in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] vergleichbar ist. Mithilfe des Viewers können Sie Korrelationen untersuchen und Informationen zu den Mustern im Modell und zu den zugrunde liegenden Daten abrufen.  
  
##  <a name="BKMK_Tabs"></a> Durchsuchen des Modells  
 Modelle, die auf den [!INCLUDE[msCoName](../includes/msconame-md.md)]-Algorithmen "Neural Network" oder "Logistic Regression" basieren, ähneln sich insofern, als sie Daten als eine Gruppe von Verbindungen zwischen bekannten Eingaben und Ausgaben analysieren. Mit dem **Durchsuchen**-Viewer können Sie diese Verbindungen mithilfe der folgenden Steuerelemente untersuchen:  
  
-   [Variablen](#BKMK_Variables)  
  
-   [Eingaben](#BKMK_Inputs)  
  
-   [Ausgaben](#BKMK_Outputs)  
  
 Zum Testen dieses Viewers können Sie ein Modell mit dem [Assistent zum Klassifizieren &#40;Data Mining-Add-Ins für Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) erstellen und die Option **Erweitert** verwenden, um den Algorithmus im Dialogfeld **Algorithmusparameter** in Microsoft Logistic Regression zu ändern.  
  
###  <a name="BKMK_Variables"></a> Variablen  
 Im Bereich **Variablen** wird eine Liste der Eingabevariablen in der Reihenfolge angezeigt, in der sie sich auf das Modell auswirken. Sie verwenden die Steuerelemente **Eingabe** und **Ausgabe**, um das Modell zu filtern. Dadurch können Sie beeinflussen, welche Variablen angezeigt und in welcher Reihenfolge sie angezeigt werden.  
  
 Mit diesem Viewer können Sie die Faktoren untersuchen, die den größten Einfluss darauf haben, ob ein Kunde eher der Fahrradkäuferkategorie oder der Nichtkäuferkategorie angehört.  
  
 ![Testen der Auswirkungen auf das Ergebnis der ausgewählten Attribute](media/dm13-neuralnet-agebuyer1.gif "Testen der Auswirkung auf das Ergebnis ausgewählte Attribute")  
  
##### <a name="explore-variables"></a>Untersuchen von Variablen  
  
1.  Zunächst wird der Bereich **Variablen** auf der Grundlage der aktuellen Filter nach den wichtigsten Attributen sortiert. Die Länge des Balkens gibt die Stärke des Faktors an.  
  
     Im Beispiel können Sie erkennen, dass das Einkommen, gefolgt von der Region, der größte Einflussfaktor ist. Andererseits werden kinderreiche Familien, die mehrere Autos besitzen, aller Wahrscheinlichkeit nach kein Fahrrad kaufen.  
  
2.  Klicken Sie im Bereich **Variablen** auf die Spaltenüberschrift für **Attribut**.  
  
     Beim Sortieren nach Attributen sehen Sie die Container, die für die einzelnen Eingabespalten erstellt wurden. Spalten mit diskreten Werten, z. B. Beruf, werden nach den *Literalwerten* klassifiziert.  
  
3.  Beachten Sie die Wertebereiche, die für **Alter** und **Einkommen** gefunden wurden.  
  
     Wenn eine der Eingabespalten aus Zahlen besteht (d. h., die ganze Datenspalte weist einen Datentyp mit fortlaufenden numerischen Zahlen auf), werden die Zahlen Buckets zugeordnet oder in diskreten Bereichen klassifiziert.  
  
     Die Einkommensspalte wurde in Gruppierungen wie 78,4-154,06 (höchste Einkommensstufe) unterteilt.  
  
     ![Sortieren, um anzuzeigen, wie Variablen klassifiziert wurden](media/dm13-nn-bucketing-variables.gif "Sortierreihenfolge an, wie Variablen klassifiziert wurden")  
  
     Wenn Sie unterschiedliche Gruppierungen verwenden möchten, sollten Sie das Tool [Neu bezeichnen &#40;SQL Server Data Mining Add-Ins&#41;](relabel-sql-server-data-mining-add-ins.md) oder die Excel-Funktionen verwenden, um vor der Modellerstellung neue Einkommenskategorien einzurichten.  
  
4.  Klicken Sie auf **Begünstigt Ja**, um das Diagramm in der Standardansicht wiederherzustellen.  
  
     Standardmäßig wird die Ansicht nach dem Wert von **Begünstigt** sortiert, der als erster Ergebniswert festgelegt wurde. Sie können ändern, welche Ergebnisse der ersten und zweiten Spalte zugeordnet werden, indem Sie in **Ausgabe** einen neuen Wert für **Wert 1** und **Wert 2** auswählen.  
  
5.  Positionieren Sie die Maus auf dem obersten Farbbalken im Diagramm.  
  
     Eine QuickInfo wird angezeigt, die ein Ergebnis für *Wichtigkeit*, ein Ergebnispaar für *Wahrscheinlichkeit* und ein Ergebnispaar für *Prognosegüte* enthält.  
  
    -   Die **Wichtigkeit** wird für das gesamte Dataset berechnet. Sie identifiziert das Attribut, das auf der Grundlage aller Eingaben die stärkste Korrelation mit dem Zielergebnis aufweist. Der Viewer sortiert die Werte im Diagramm nach den Wichtigkeitsbewertungen.  
  
    -   Die **Wahrscheinlichkeit** wird für die einzelnen Sätze von Attribut/Wert-Paaren im gesamten Dataset berechnet und in den Zielergebnissen ausgegeben.  
  
    -   Die **Prognosegüte** gibt an, wie hilfreich ein bestimmtes Attribut/Wert-Paar für die Höherstufung eines Ergebnisses ist.  
  
     Hinweis: Die QuickInfo enthält die gleiche Informationen unabhängig davon, ob Sie die Maus über einen oder anderen Spalte positionieren.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="BKMK_Inputs"></a> Eingaben  
 Im Bereich **Eingaben** können Sie einen Satz von Eingaben auswählen und diesen als Filter auf das Modell anwenden. So erkennen Sie auf der Grundlage der Trainingsdaten, wie sich diese Optionen auf das Ergebnis auswirken.  
  
##### <a name="explore-inputs"></a>Untersuchen von Eingaben  
  
1.  Stellen Sie sich vor, Sie möchten eine bestimmte Zielgruppe analysieren und die Faktoren anzeigen, die den größten Einfluss auf das Kaufverhalten der Gruppe haben.  
  
     In der **Eingabe** Bereich klicken Sie auf die  **\<alle >** Zelle unter **Attribut**, und wählen Sie **Alter**.  
  
     Wählen Sie für **Wert** die jüngste Altersgruppe aus.  
  
2.  Auch wenn Sie nach einer bestimmten Altersgruppe filtern, werden Sie feststellen, dass die Pazifikregion fast am Anfang der Liste steht. Das liegt daran, dass Kunden aus der Pazifikregion mit weitaus größerer Wahrscheinlichkeit ein Fahrrad kaufen würden als Kunden in anderen Regionen.  
  
     Da die Region eine Größe ist, die Sie nicht beeinflussen können, können Sie die Eingaben ändern, um diese Variable aus der Analyse zu entfernen und andere Faktoren zu untersuchen.  
  
     Klicken Sie im Bereich **Eingabe** auf die leere Zelle unter **Alter**, und wählen Sie **Region** aus.  
  
     Wählen Sie für **Wert** den Eintrag **Europa** aus.  
  
3.  Fügen Sie weitere Eingabefilter hinzu, um eine bestimmte Interessensgruppe zu fokussieren.  
  
     Fügen Sie für das Eingabeattribut beispielsweise **Geschlecht** hinzu, und wählen Sie **Weiblich** als Wert aus.  
  
     ![Testen der Auswirkungen auf das Ergebnis der ausgewählten Attribute](media/dm13-neuralnet-agebuyer2.gif "Testen der Auswirkung auf das Ergebnis ausgewählte Attribute")  
  
     Sie werden feststellen, dass sich die Liste der Variablen ändert. Jetzt ist **Einkommen** die Variable, die für die Vorhersage des Zielergebnisses die größte Bedeutung hat.  
  
     Die Reihenfolge, in der Sie die Eingabefilter anwenden, wirkt sich nicht auf die Ergebnisse aus.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="BKMK_Outputs"></a> Ausgaben  
 Im Bereich **Ausgabe** können Sie das Ergebnis auswählen, das interessant für Sie ist. In neuronalen Netzwerken können Sie so viele Ergebnisspalten angeben, wie Sie möchten. Allerdings erhöht sich durch zusätzliche Ausgaben auch die Komplexität des Modells, sodass sich die Verarbeitungsdauer verlängern kann.  
  
 Um zwei Ausgaben zu vergleichen, müssen die Spalten den Typ **Vorhersagen** oder **Nur vorhersagen** aufweisen.  
  
##### <a name="explore-outputs"></a>Untersuchen von Ausgaben  
  
1.  Verwenden Sie die Liste **Ausgabeattribut**, um ein Attribut auszuwählen.  
  
2.  Wählen Sie zwei Ergebnisse aus den Listen Wert 1 und Wert 2 aus. Diese beiden Status der Ausgabeattribute werden im Bereich **Variablen** verglichen.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
## <a name="more-about-neural-network-models"></a>Weiteren Informationen über neuronale Netzwerkmodelle  
 Die Informationen in der Ereignisanzeige werden vom Server mithilfe einer gespeicherten Prozedur, die speziell für diesen Modelltyp abgerufen: System.Microsoft.AnalysisServices.System.DataMining.NeuralNet.GetAttributeScores.  
  
 Wenn Sie ein Modell mit mehreren vorhersagbaren Attributen mithilfe der Add-Ins erstellen möchten, verwenden Sie die Modellierungsoptionen unter **Erweitert**.  
  
 Weitere Informationen finden Sie unter [Erstellen einer Miningstruktur &#40;SQL Server Data Mining-Add-Ins&#41;](create-mining-structure-sql-server-data-mining-add-ins.md) und [Hinzufügen eines Modells zu einer Struktur &#40;Data Mining-Add-Ins für Excel&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
