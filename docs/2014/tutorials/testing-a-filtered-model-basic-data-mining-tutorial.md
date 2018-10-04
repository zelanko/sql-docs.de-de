---
title: Testen eines gefilterten Modells (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e1264808911226150bc908e356e1b08ab90e72fc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055000"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>Testen eines gefilterten Modells (Lernprogramm zu Data Mining-Grundlagen)
  Nun, da Sie festgestellt haben, dass die `TM_Decision_Tree` Modell ist die höchste Genauigkeit bietet, passen Sie das Modell, um den Anforderungen besser entsprechen den [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] targeted mailing-Kampagne. Die Marketingabteilung möchte insbesondere ermitteln, ob Unterschiede zwischen männlichen und weiblichen Kunden vorliegen. Die Informationen können sie entscheiden, welche Zeitschriften für Werbung verwendet und welche Produkte ihre Mailings Funktion.  
  
## <a name="using-filters"></a>Mithilfe von Filtern  
 Filter ermöglichen es Ihnen, auf einfache Weise Modelle für Teilmengen von Daten zu erstellen. Der Filter wird nur auf das Modell angewendet; die zugrunde liegende Datenquelle wird nicht geändert.  
  
 In dieser Lektion erstellen Sie ein nach Geschlechtern gefiltertes Modell, um die Merkmale mit dem stärksten Einfluss auf das Kaufverhalten männlicher und weiblicher Kunden vorherzusagen.  
  
 Zunächst erstellen Sie eine Kopie der `TM_Decision_Tree` Modell.  
  
#### <a name="to-copy-the-decision-tree-model"></a>So kopieren Sie das Entscheidungsstrukturmodell  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], wählen Sie im Projektmappen-Explorer **BasicDataMining**.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die `TM_Decision_Tree` Modell, und wählen **Neues Miningmodell.**  
  
4.  In der **Modellname** Feld `TM_Decision_Tree_Male`.  
  
5.  Klicken Sie auf **OK**.  
  
 Erstellen Sie anschließend einen Filter, um Kunden auf Grundlage ihres Geschlechtes für das Modell auszuwählen.  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>So erstellen Sie einen Fallfilter für ein Miningmodell  
  
1.  Mit der rechten Maustaste die `TM_Decision_Tree_Male` Mining-Modell, um das Kontextmenü zu öffnen.  
  
     oder  
  
     Wählen Sie das Modell aus. Wählen Sie im Menü **Miningmodell** die Option **Modellfilter festlegen**aus.  
  
2.  Klicken Sie im Dialogfeld **Modellfilter** im Textfeld **Miningstrukturspalte** auf die oberste Zeile im Raster.  
  
     Die Dropdownliste zeigt nur die Namen der Spalten in dieser Tabelle an.  
  
3.  Wählen Sie im Textfeld Miningstrukturspalte **Geschlecht**.  
  
     Das Symbol auf der linken Seite des Textfelds ändert sich und gibt dadurch an, dass es sich beim ausgewählten Element um eine Tabelle oder eine Spalte handelt.  
  
4.  Klicken Sie auf die **Operator** Textfeld, und wählen Sie den Gleichheitsoperator (=), aus der Liste.  
  
5.  Klicken Sie auf die **Wert** Textfeld, und geben **M**.  
  
6.  Klicken Sie auf die nächste Zeile im Raster.  
  
7.  Klicken Sie auf **OK** schließen die **Modellfilter** Dialogfeld.  
  
     Der Filter wird der **Eigenschaften** Fenster. Alternativ können Sie starten die **Modellfilter** Dialogfeld aus der **Eigenschaften** Fenster.  
  
8.  Wiederholen Sie dieses Mal jedoch die oben genannten Schritte aus, nennen Sie das Modell `TM_Decision_Tree_Female` und **F** in die **Wert** Textfeld.  
  
## <a name="process-the-filtered-models"></a>Verarbeiten der gefilterten Modelle  
 Modelle können erst dann verwendet werden, wenn sie bereitgestellt und verarbeitet wurden. Weitere Informationen zur Verarbeitung von Modellen finden Sie unter [Verarbeiten von Modellen in der Targeted Mailing-Struktur &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md).  
  
#### <a name="to-process-the-filtered-model"></a>So verarbeiten Sie das gefilterte Modell  
  
1.  Mit der rechten Maustaste die `TM_Decision_Tree_Male` modellieren, und wählen Sie **Miningstruktur verarbeiten und alle Modelle**s  
  
2.  Klicken Sie auf **ausführen** zum Verarbeiten des neuen Modells.  
  
3.  Nachdem die Verarbeitung abgeschlossen ist, klicken Sie auf **schließen** in beiden Fenstern.  
  
     Sie verfügen nun über zwei neue Miningmodelle angezeigt, der **Miningmodelle** Registerkarte.  
  
## <a name="evaluate-the-results"></a>Auswerten der Ergebnisse  
 Zeigen Sie die Ergebnisse an, und werten Sie die Genauigkeit der gefilterten Modelle analog zu den vorhergehenden drei Modellen aus. Weitere Informationen finden Sie in den folgenden Themen:  
  
 [Untersuchen des Entscheidungsstrukturmodells &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [Überprüfen der Genauigkeit mit Prognosegütediagrammen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>So untersuchen Sie die gefilterten Modelle  
  
1.  Wählen Sie die **Miningmodell-Viewer** Registerkarte **Data Mining-Designer**.  
  
2.  Wählen Sie im Feld Miningmodell `TM_Decision_Tree_Male`.  
  
3.  Schieben Sie **Ebene anzeigen** zu `3`.  
  
4.  Ändern der **Hintergrund** Wert `1`.  
  
5.  Platzieren Sie den Cursor über dem Knoten mit der Bezeichnung **alle** um die Anzahl der fahrradkäufer im Vergleich zu nicht-fahrradkäufer anzuzeigen.  
  
6.  Wiederholen Sie die Schritte 1 bis 5 für `TM_Decision_Tree_Female`.  
  
7.  Untersuchen Sie die Ergebnisse für die `TM_Decision_Tree` und die Modelle nach dem Geschlecht gefiltert. Im Vergleich zu allen Fahrradkäufern weisen männliche und weibliche Fahrradkäufer einige Gemeinsamkeiten sowie drei interessante Unterschiede auf. Dies ist nützlich, Informationen, die [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] können verwenden, um die Marketingkampagne zu entwickeln.  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>So testen Sie den Lift für die gefilterten Modelle  
  
1.  Wechseln Sie zu der **Mininggenauigkeitsdiagramm** Registerkarte im Data Mining-Designer [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] , und wählen Sie die **Eingabeauswahl** Registerkarte.  
  
2.  In der **Dataset auswählen, für das Genauigkeitsdiagramm verwendet werden** Gruppe wählen Sie im **Testfälle für Miningstruktur verwenden**.  
  
3.  Auf der **Eingabeauswahl** -Registerkarte des Data Mining-Designers unter **wählen Sie die vorhersagbaren Miningmodellspalten im prognosegütediagramm angezeigt**, aktivieren Sie das Kontrollkästchen **synchronisieren Vorhersagespalten und Werte**.  
  
4.  In der **Name der vorhersagbaren Spalte** Spalte überprüfen Sie, ob **Bike Buyer** für jedes Modell ausgewählt ist.  
  
5.  In der **anzeigen** Spalte, wählen Sie die einzelnen Modelle.  
  
6.  In der **Wert Vorhersagen** Spalte `1`.  
  
7.  Wählen Sie die **Prognosegütediagramm** Registerkarte zum Anzeigen des prognosegütediagramms.  
  
     Wie Sie sehen, weisen alle drei Entscheidungsstrukturmodelle verglichen mit dem Zufallsvorhersagemodell einen deutlichen Anstieg auf und übertreffen das Clustering- und das Naive Bayes-Modell.  
  
## <a name="related-tasks"></a>Related Tasks  
 Weitere Informationen zu Filtern finden Sie unter [Filter für Miningmodelle &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Ein Beispiel dafür, wie zum Anwenden von Filtern auf geschachtelte Tabellen finden Sie unter [Data Mining Tutorial für fortgeschrittene &#40;Analysis Services – Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Überprüfen der Genauigkeit mit Prognosegütediagrammen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 6: Erstellen und Verwenden von Vorhersagen &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Miningmodelltasks und Anweisungen Mining](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Löschen eines Filters aus einem Miningmodell](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [Filter für Miningmodelle &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
