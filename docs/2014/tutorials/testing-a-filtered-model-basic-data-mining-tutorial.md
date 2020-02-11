---
title: Testen eines gefilterten Modells (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0d74f8c-600d-4df5-a742-695e6947a071
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: baa4910b2849c4eb2dd04c6d0115c83683ee8bea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63044095"
---
# <a name="testing-a-filtered-model-basic-data-mining-tutorial"></a>Testen eines gefilterten Modells (Lernprogramm zu Data Mining-Grundlagen)
  Nachdem Sie festgestellt haben, dass `TM_Decision_Tree` das Modell am genauesten ist, passen Sie das Modell so an, dass es den Anforderungen [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] der Ziel-Mailingkampagne besser entspricht. Die Marketingabteilung möchte insbesondere ermitteln, ob Unterschiede zwischen männlichen und weiblichen Kunden vorliegen. Anhand dieser Informationen soll entschieden werden, welche Zeitschriften für Werbemaßnahmen berücksichtigt und welche Produkte beworben werden sollen.  
  
## <a name="using-filters"></a>Verwenden von Filtern  
 Filter ermöglichen es Ihnen, auf einfache Weise Modelle für Teilmengen von Daten zu erstellen. Der Filter wird nur auf das Modell angewendet; die zugrunde liegende Datenquelle wird nicht geändert.  
  
 In dieser Lektion erstellen Sie ein nach Geschlechtern gefiltertes Modell, um die Merkmale mit dem stärksten Einfluss auf das Kaufverhalten männlicher und weiblicher Kunden vorherzusagen.  
  
 Zuerst erstellen Sie eine Kopie des `TM_Decision_Tree` Modells.  
  
#### <a name="to-copy-the-decision-tree-model"></a>So kopieren Sie das Entscheidungsstrukturmodell  
  
1.  Wählen [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Sie in Projektmappen-Explorer die Option **basicdatamining**aus.  
  
2.  Klicken Sie auf die Registerkarte **Miningmodelle** .  
  
3.  Klicken Sie mit `TM_Decision_Tree` der rechten Maustaste auf das Modell, und wählen Sie **Neues Mining Modell**  
  
4.  Geben `TM_Decision_Tree_Male`Sie im Feld **Modellname den Namen** ein.  
  
5.  Klicken Sie auf **OK**.  
  
 Erstellen Sie anschließend einen Filter, um Kunden auf Grundlage ihres Geschlechtes für das Modell auszuwählen.  
  
#### <a name="to-create-a-case-filter-on-a-mining-model"></a>So erstellen Sie einen Fallfilter für ein Miningmodell  
  
1.  Klicken Sie mit der `TM_Decision_Tree_Male` rechten Maustaste auf das Mining Modell, um das Kontextmenü zu öffnen.  
  
     – oder –  
  
     Wählen Sie das Modell aus. Wählen Sie im Menü **Miningmodell** die Option **Modellfilter festlegen**aus.  
  
2.  Klicken Sie im Dialogfeld **Modellfilter** im Textfeld **Miningstrukturspalte** auf die oberste Zeile im Raster.  
  
     Die Dropdownliste zeigt nur die Namen der Spalten in dieser Tabelle an.  
  
3.  Wählen Sie im Textfeld Mining Struktur Spalte die Option **Geschlecht**aus.  
  
     Das Symbol auf der linken Seite des Textfelds ändert sich und gibt dadurch an, dass es sich beim ausgewählten Element um eine Tabelle oder eine Spalte handelt.  
  
4.  Klicken Sie auf das Textfeld **Operator** , und wählen Sie den Gleichheits Operator (=) aus der Liste aus.  
  
5.  Klicken Sie auf das Textfeld **Wert** , und geben Sie **M**ein.  
  
6.  Klicken Sie auf die nächste Zeile im Raster.  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld **Modell Filter** zu schließen.  
  
     Der Filter wird im Fenster **Eigenschaften** angezeigt. Alternativ können Sie das Dialogfeld **Modell Filter** im Fenster **Eigenschaften** starten.  
  
8.  Wiederholen Sie die obigen Schritte, benennen Sie das Modell `TM_Decision_Tree_Female` mit dieser Zeit, und geben Sie **F** im Textfeld **Wert** ein.  
  
## <a name="process-the-filtered-models"></a>Verarbeiten der gefilterten Modelle  
 Modelle können erst dann verwendet werden, wenn sie bereitgestellt und verarbeitet wurden. Weitere Informationen zur Verarbeitung von Modellen finden Sie unter [Verarbeiten von Modellen in der Ziel-e-Mail-&#40;grundlegende Data Mining ](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)-Lernprogramm&#41;.  
  
#### <a name="to-process-the-filtered-model"></a>So verarbeiten Sie das gefilterte Modell  
  
1.  Klicken Sie mit der `TM_Decision_Tree_Male` rechten Maustaste auf das Modell, und wählen Sie **Mining Struktur und alle Modelle verarbeiten**.  
  
2.  Klicken Sie auf **Ausführen** , um die neuen Modelle zu verarbeiten.  
  
3.  Nachdem die Verarbeitung abgeschlossen ist, klicken Sie in beiden Verarbeitungs Fenstern auf **Schließen** .  
  
     Auf der Registerkarte **Mining Modelle** werden nun zwei neue Modelle angezeigt.  
  
## <a name="evaluate-the-results"></a>Auswerten der Ergebnisse  
 Zeigen Sie die Ergebnisse an, und werten Sie die Genauigkeit der gefilterten Modelle analog zu den vorhergehenden drei Modellen aus. Weitere Informationen finden Sie unter  
  
 [Untersuchen des Entscheidungsstruktur Modells &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
 [Testen der Genauigkeit mit Lift Charts &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
#### <a name="to-explore-the-filtered-models"></a>So untersuchen Sie die gefilterten Modelle  
  
1.  Wählen Sie im **Data Mining-Designer**die Registerkarte **Mining Modell-Viewer** aus.  
  
2.  Wählen Sie `TM_Decision_Tree_Male`im Feld Mining Modell die Option aus.  
  
3.  Folie **zeigt** die Ebene `3`auf an.  
  
4.  Ändern Sie **** den Wert für `1`background in.  
  
5.  Platzieren Sie den Cursor über dem Knoten mit der Bezeichnung **alle** , um die Anzahl der Fahrrad Käufer im Vergleich zu nicht Fahrrad Käufern anzuzeigen.  
  
6.  Wiederholen Sie die `TM_Decision_Tree_Female`Schritte 1-5 für.  
  
7.  Untersuchen Sie die Ergebnisse `TM_Decision_Tree` für die und die Modelle, die nach Geschlecht gefiltert werden. Im Vergleich zu allen Fahrradkäufern weisen männliche und weibliche Fahrradkäufer einige Gemeinsamkeiten sowie drei interessante Unterschiede auf. Dies sind nützliche Informationen, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] die Sie verwenden können, um Ihre Marketingkampagne zu entwickeln.  
  
#### <a name="to-test-the-lift-of-the-filtered-models"></a>So testen Sie den Lift für die gefilterten Modelle  
  
1.  Wechseln Sie in zur Registerkarte **Mining Genauigkeits Diagramm** im [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Data Mining-Designer, und wählen Sie die Registerkarte **Eingabeauswahl** aus.  
  
2.  Wählen Sie im Gruppenfeld Dataset **auswählen, das für das Genauigkeits Diagramm verwendet werden soll** die Option **Testfälle für Mining Struktur verwenden**aus.  
  
3.  Aktivieren Sie auf der Registerkarte **Eingabeauswahl** des Data Mining-Designers unter **Wählen Sie die vorhersagbaren Mining Modell Spalten**aus, die im Prognose Prognose Diagramm angezeigt werden sollen das Kontrollkästchen **Vorhersage Spalten und-Werte synchronisieren**.  
  
4.  Überprüfen Sie in der Spalte **Name der vorhersagbaren Spalte** , ob **Bike Buyer** für jedes Modell ausgewählt ist.  
  
5.  Wählen Sie in der Spalte **anzeigen** die einzelnen Modelle aus.  
  
6.  Wählen Sie `1`in der Spalte **Wert vorhersagen** aus.  
  
7.  Wählen Sie die Registerkarte **Lift Chart** aus, um das Lift-Diagramm anzuzeigen.  
  
     Wie Sie sehen, weisen alle drei Entscheidungsstrukturmodelle verglichen mit dem Zufallsvorhersagemodell einen deutlichen Anstieg auf und übertreffen das Clustering- und das Naive Bayes-Modell.  
  
## <a name="related-tasks"></a>Related Tasks  
 Weitere Informationen zu Filtern finden Sie unter [Filter für Mining Modelle &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 Ein Beispiel für das Anwenden von Filtern auf eine Reihe von Tabellen finden Sie unter Data Mining-Lernprogramm für fort [geschrittene &#40;Analysis Services Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).  
  
## <a name="previous-task-in-lesson"></a>Vorherige Aufgabe in der Lektion  
 [Testen der Genauigkeit mit Lift Charts &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 6: Erstellen und arbeiten mit Vorhersagen &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services-Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Mining Modell Tasks und Anleitungen](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Löschen eines Filters aus einem Mining Modell](../../2014/analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)   
 [Filter für Mining Modelle &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
