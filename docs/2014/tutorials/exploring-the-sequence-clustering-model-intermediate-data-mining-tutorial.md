---
title: Untersuchen des Sequence Clustering-Modells (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f8a485d5-47ed-4dd5-bb66-ef4d6d463845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e0904239933361b80727700c94b03e379751251f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164053"
---
# <a name="exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Prüfen des Sequenzclustermodells (Data Mining-Lernprogramm)
  Nachdem Sie das **Sequence Clustering mit Regions** Modell erstellt haben, können Sie es untersuchen, indem Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] den Sequence Clustering-Viewer auf der Registerkarte **Mining Modell-Viewer** des Data Mining-Designers verwenden. Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequenz Cluster-Viewer enthält fünf Registerkarten: **Cluster Diagramm**, **Cluster profile**, **Cluster Merkmale**, Cluster **Unterscheidung**und **Statusübergänge**. Weitere Informationen zur Verwendung dieses Viewers finden [Sie unter Durchsuchen eines Modells mit dem Microsoft Sequence Cluster-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).  
  
-   [Registerkarte Cluster Diagramm](#bkmk_CDiagram)  
  
-   [Registerkarte Cluster profile](#bkmk_CProfiles)  
  
-   [Registerkarte Cluster Merkmale](#bkmk_CChars)  
  
-   [Registerkarte Cluster Unterscheidung](#bkmk_CDiscrim2)  
  
-   [Registerkarte Statusübergänge](#bkmk_StateTran)  
  
-   [Generische Inhaltssicht](#bkmk_Generic)  
  
##  <a name="bkmk_CDiagram"></a>Registerkarte Cluster Diagramm  
 Die Registerkarte **Cluster Diagramm** zeigt die Cluster, die der Algorithmus in der Datenbank ermittelt hat, grafisch an. Das Layout im Diagramm gibt die Beziehungen der Cluster an, wobei ähnliche Cluster nahe zusammen gruppiert sind. Standardmäßig gibt die Schattierung der einzelnen Knotenfarben die Dichte aller Fälle auf dem Cluster an, d. h., je dunkler die Schattierung des Knotens, desto mehr Fälle enthält er. Sie können die Bedeutung der Knotenschattierung ändern, sodass diese die Unterstützung in den einzelnen Clustern für ein Attribut und einen Status darstellt.  
  
 Sie können die Cluster auch umbenennen, um es einfacher zu machen, Zielcluster zu identifizieren und mit diesen zu arbeiten. Für dieses Lernprogramm benennen Sie den Cluster um, der den höchsten Prozentsatz an Kunden aus der Pazifikregion hat, und der Cluster, sowie den Cluster, der insgesamt die meisten Fälle enthält.  
  
> [!NOTE]  
>  Die Fälle, die bestimmten Clustern zugewiesen sind, können sich abhängig von den Daten und den Modellparametern ändern, wenn Sie das Modell neu verarbeiten. Auch wenn Sie Cluster umbenennen, gehen die Namen verloren, wenn Sie das Miningmodell erneut verarbeiten.  
  
#### <a name="to-change-the-attribute-used-for-highlighting-clusters"></a>So ändern Sie das für die Hervorhebung von Clustern verwendete Attribut  
  
1.  Wählen Sie in der Liste **Schattierungs Variable** die Option **Modell**aus.  
  
2.  Wählen Sie in der Liste **Status** die Option **radgrenze** aus.  
  
     Das Diagramm wird aktualisiert, um die Konzentration des ausgewählten Produkts in jeden der Cluster anzuzeigen. Der Cluster mit der dunkelsten Schattierung weist die höchste Dichte für das Produkt "Cycling Caps" auf. Sie können die Schattierungs Variable so ändern, dass ein beliebiger Status beliebiger Eingabe Spalten verwendet wird.  
  
3.  Wählen Sie in der Liste **Schattierungs Variable** die Option **Population**aus.  
  
     Wenn Sie die Schattierungsvariable in "Auffüllung" ändern, wird das Diagramm aktualisiert, um die Cluster der Größe nach zu vergleichen. Der Cluster, der die dunkelste Schattierung aufweist, enthält mehr Fälle als die anderen Cluster.  
  
#### <a name="to-rename-nodes-in-the-model"></a>So benennen Sie Knoten im Modell um  
  
1.  Ändern Sie die **Schattierungs Variable** in `Region`, und legen Sie **State** auf **Pacific**fest.  
  
2.  Heben Sie den dunkelsten Knoten im Diagramm hervor.  
  
3.  Klicken Sie mit der rechten Maustaste auf diesen Cluster und wählen Sie **Cluster umbenennen**  
  
4.  Geben Sie den Namen**Pacific Cluster ein.**  
  
5.  Ändern Sie den Wert der **Schattierungs Variablen** in **Population**.  
  
6.  Suchen Sie im aktualisierten Diagramm den dunkelsten Cluster; dieser sollte der größte Cluster sein. Wenn Sie nicht mittels der Schattierung erkennen können, welcher Cluster am größten ist, halten Sie den Mauszeiger Maus über jedem Cluster an, und zeigen Sie die QuickInfo an. Wählen Sie dann den Cluster aus, der die meisten Fälle enthält.  
  
7.  Klicken Sie mit der rechten Maustaste auf diesen Cluster und wählen Sie **Cluster umbenennen** Geben Sie den neuen Namen `Largest Cluster`ein.  
  
 Sie können einen Drillthrough von dem Knoten aus durchführen, der den Cluster darstellt, um Details der Fälle anzuzeigen, die in jedem Cluster enthalten sind. Dies kann nützlich sein, wenn Sie auf aufgrund der Ergebnisse Ihrer Analyse handeln, z. B. wenn Sie E-Mails an einen Kunden senden. Sie können auch die anderen Attribute der Fälle durchsuchen, die Sie in die Struktur eingeschlossen haben, aber nicht im Modell verwendet haben, z. B. Region und IncomeGroup. Weitere Informationen zum Ausführen eines Drillthrough von Mining Modellen zu den zugrunde liegenden Fällen finden Sie unter [Drillthrough-Abfragen &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-drill-through-to-details-from-the-cluster-diagram"></a>So führen Sie einen Drillthrough zu Details vom Clusterdiagramm aus durch  
  
1.  Klicken Sie mit `Pacific Cluster`der rechten Maustaste auf Drillthrough, und wählen Sie dann **Modell-und Struktur Spalten**aus. ****  
  
     Das Dialogfeld **Drillthrough** wird geöffnet. Spalten, die nicht im Modell verwendet werden, aber für Abfragen verfügbar sind, weisen das Präfix " **Structure**" auf.  
  
     Sie können sehen, dass dieser Cluster meistens Kunden aus der Pazifikregion enthält und nur wenige Kunden aus anderen Regionen.  
  
2.  Klicken Sie in der geschachtelten Spalte "v Assoc Seq Line Items" auf das Pluszeichen, um die Sequenz von Elementen in einem bestimmten Kundenbefehl anzuzeigen.  
  
3.  Schließen Sie das Dialogfeld **Drillthrough** .  
  
    > [!NOTE]  
    >  Mit der **Wiedergabe** Schaltfläche können Sie die Daten anweisen. die angezeigte Daten werden jedoch nicht von der Anforderung geändert, es sei denn, das Modell wurde im Hintergrund von einem anderen Prozess dynamisch aktualisiert.  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_CProfiles"></a>Registerkarte Cluster profile  
 Die Registerkarte **Cluster profile** zeigt die Sequenzen an, die sich in den einzelnen Clustern befinden. Die Cluster sind in den einzelnen Spalten rechts von der Spalte **Zustände** aufgeführt.  
  
 Im Viewer beschreibt die Zeile **Modell** die Gesamtverteilung der Elemente in einem Cluster, und die Zeile **Model. Samples** enthält Sequenzen der Elemente. Jede Zeile der Farbsequenzen in jeder Zelle der **Model. Samples** -Zeile stellt das Verhalten eines zufällig ausgewählten Benutzers im Cluster dar.  
  
 Jede Farbe in einem Sequenzhistogramm steht für ein Produktmodell. In der Mininglegende werden Sequenzen von Produkten sowohl unter Verwendung der Farbcodierung als auch des Produktmodellnamens angezeigt. Wenn Sie dem Modell für Clustering, z. B. Region oder Einkommensgruppe, weitere Spalten hinzugefügt haben, enthält der Viewer eine zusätzliche Zeile für jede Spalte, die die Verteilung dieser Werte innerhalb jedes Clusters anzeigt.  
  
#### <a name="to-view-the-sequences-that-are-most-common-in-a-cluster"></a>So zeigen Sie die Sequenzen an, die in einem Cluster am häufigsten sind  
  
1.  Klicken Sie mit der rechten Maustaste auf die Zeile **Modell** in der `Largest Cluster`Spalte für den Cluster, und wählen Sie **Legende anzeigen**aus.  
  
     Die **Color** -Spalte enthält einen schattierten Balken, der die Häufigkeit der in Sequenzen gefundenen Elemente angibt. Jedes Element wird durch eine andere Farbe dargestellt. In der Spalte **Bedeutung** werden die Produktmodell Namen für die einzelnen Farben aufgelistet. Die Spalte **Distribution** gibt Aufschluss über den Prozentsatz der Fälle, in denen dieses Element in einer Sequenz enthalten war.  
  
2.  Schließen Sie die **Mining Legende**.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Zeile **Model. Samples** in der Spalte mit der Überschrift, **Population,** und wählen Sie **Legende anzeigen**aus.  
  
4.  Durchsuchen der Liste der Sequenzen im Gesamtmodell`.`  
  
     In der Mininglegende werden zuerst die häufigsten Sequenzen aufgelistet. Das Produkt "Mountain Tire Tube" ist das erste Element in vielen Sequenzen. Das bedeutet, dass ein Kunde "Mountain Tire Tube" höchstwahrscheinlich als Erstes in den Warenkorb legen wird.  
  
#### <a name="to-drill-through-to-cases-from-the-cluster-viewer"></a>So führen Sie einen Drillthrough zu Fällen vom Cluster-Viewer aus durch  
  
1.  Scrollen Sie im Attribut Bereich nach unten, bis Sie die Zeile für `Region` das Attribut gefunden haben.  
  
     Die Zeile enthält ein Histogramm für jeden Cluster im Modell sowie ein zusätzliches Histogramm für die Auffüllung, d. h. den gesamten Satz von Fällen, die im Modell **verwendet werden.** Ein Histogramm ist eine Leiste mit verschiedenen Farben, wobei jede Farbe ein Attribut darstellt, und die Größe des farbigen Abschnitts für dieses Attribut stellt den Prozentsatz der Fälle mit diesem Attribut dar.  
  
2.  Vergleichen Sie die Histogramme für die Cluster, die `Pacific Cluster` Sie `Largest Cluster`umbenannt haben, und. Jeder Cluster wird in einer anderen Spalte angezeigt.  
  
     Beide Cluster werden in Volltonfarben angezeigt, jedoch in unterschiedlichen Farben.  
  
3.  Halten Sie `Region` in der Zeile die Maus über dem farbigen Histogramm für `Largest Cluster`.  
  
     Die QuickInfo zeigt Werte an, die die tatsächlichen Prozentsätze der Fälle aus jedem Bereich anzeigen.  
  
4.  Klicken Sie mit der rechten Maustaste auf das farbige `Region` Histogramm `Pacific Cluster`in der Zeile für, wählen Sie **Drillthrough**aus, und wählen Sie dann **nur Modell Spalten**aus.  
  
5.  Verschieben Sie die Bildlaufleiste, um alle Kunden in diesen Cluster zu überprüfen.  
  
     Sie können erneut mittels Drillthrough zu den Details erkennen, dass der Cluster zumeist Bestellungen aus der Pazifikregion enthält, aber auch einige wenige aus den Regionen Nordamerika und Europa.  
  
6.  Schließen Sie das Dialogfeld **Drillthrough** .  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_CChars"></a>Registerkarte Cluster Merkmale  
 Auf der Registerkarte **Cluster Merkmale** werden die Übergänge zwischen Zuständen in einem Cluster zusammengefasst, indem Balken angezeigt werden, die die Wichtigkeit des Attribut Werts für den ausgewählten Cluster visuell darstellen. Die Spalte **Variablen** gibt Aufschluss darüber, wie das Modell für den ausgewählten Cluster oder die ausgewählte Population wichtig ist: entweder ein bestimmter Wert oder die Beziehung zwischen den Werten, die als *Übergang*bezeichnet werden. Die Spalte **Werte** stellt weitere Details zum Wert oder Übergang bereit, und die **Wahrscheinlichkeits** Spalte stellt die Gewichtung dieses Attributs oder Übergangs visuell dar.  
  
#### <a name="to-view-the-important-attributes-for-a-cluster"></a>So zeigen Sie die wichtigen Attribute für einen Cluster an  
  
1.  Wählen Sie **** `Pacific Cluster`in der Dropdown Liste Cluster aus.  
  
     Die Liste wird aktualisiert, um die Eigenschaften des Clusters anzuzeigen, den `Pacific Cluster`Sie umbenannt haben. In diesem Cluster ist `Region`das wichtigste Merkmal.  
  
2.  Bewegen Sie die Maus über der schattierten Leiste in der `Region`Zeile für.  
  
     Die Wahrscheinlichkeit, dass der Wert "Pazifik" ist, ist sehr hoch. Weitere Informationen zum Interpretieren dieser Werte finden Sie unter [Technische Referenz für den Microsoft Sequence Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md).  
  
3.  Sehen Sie die Liste der Eigenschaften für den Cluster durch, bis Sie die erste Übergangszeile gefunden haben.  
  
4.  Eine Übergangs Zeile enthält den Text Übergang in der **Variablen** Spalte und eine Kombination aus sequenziellen Attributwerten in der Spalte **Wert** . Die Sequenz kann auch Anfangspunkte und fehlende Werte enthalten.  
  
     Nehmen wir beispielsweise an, dass der Übergang den Wert [Start]-> Road Tire Tube hat. Dies bedeutet, dass Kunden in diesem Cluster häufig "Road Tire Tube" zuerst in den Warenkorb gelegt haben. Dies kann anzeigen, dass das Produkt ein häufiges Element ist, das Kunden als Erstes suchen, oder es kann anzeigen, dass das Produkt einfach auf der Einkaufswebsite zu finden ist.  
  
5.  Führen Sie einen Bildlauf durch die Liste durch, bis Sie den ersten Übergang gefunden haben, der nicht über **[Start]** verfügt oder nicht **vorhanden** ist.  
  
     Nehmen wir beispielsweise an, dass Sie den Übergang **Touring Tire, Touring Tire Tube**finden. Dies bedeutet, dass Kunden in diesem Cluster diese Elemente und genau in dieser Reihenfolge häufig zusammen gekauft haben.  
  
6.  Halten Sie die Maus über der schattierten Leiste für diesen Übergang an.  
  
     Die Wahrscheinlichkeit dieses Übergangs wird als ein Prozentsatz angezeigt.  
  
7.  Wählen Sie in der Dropdown Liste **Cluster** die Option **Population (alle)** aus.  
  
     Die Liste der Attribute wird aktualisiert, um die Eigenschaften aller Bestellungen anzuzeigen, die verwendet wurden, um das Modell zu erstellen. In diesem Mining Modell ist `Region`das wichtigste Merkmal für die Unterscheidung zwischen Clustern, mit dem Wert **Nordamerika**.  
  
 Sie erkennen zwei Dinge, nachdem Sie diese Tasks überprüft haben. Zum einen benötigen Sie viele Daten, um eine sinnvolle Anzahl von Kombinationen abzurufen. Beispielsweise enthalten die Sequenzen mit den höchsten Wahrscheinlichkeiten wahrscheinlich den Status **[Start]** oder **fehlt** .  
  
 Die zweite besteht darin, dass es einen starken Clustering-Effekt auf `Region`Attribute für gibt, wodurch es schwieriger wird, die Gruppen von Sequenzen anzuzeigen. Daher entscheiden Sie sich, ein anderes Modell zu erstellen, das nur Sequenzen verwendet und keine Spalten für die Region oder das Einkommen enthalten.  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_CDiscrim2"></a>Registerkarte Cluster Unterscheidung  
 Mithilfe der Registerkarte **Cluster Unterscheidung** können Sie zwei Cluster vergleichen, um zu bestimmen, welche Attribute einen bestimmten Cluster von einem anderen Cluster unterscheiden. Die Registerkarte enthält vier Spalten: **Variablen**, **Werte**, **Cluster 1**und **Cluster 2**.  Sie können einen beliebigen Cluster auswählen, der als **Cluster 1** und **Cluster 2**verwendet werden soll.  
  
 Die Spalte **Variablen** zeigt den Namen des Attributs an, bei dem es sich entweder um einen Spaltennamen oder eine Kombination aus Spaltenname und Wort **Übergang**handeln kann. Die Spalte **Werte** zeigt den exakten Wert des Attributs oder des Übergangs an. Die schattierten Balken in den Spalten für **Cluster 1** und **Cluster 2** geben die Stärke des Attributs in den Clustern an, die Sie vergleichen. Je länger die Leiste, desto wahrscheinlicher schließt der Cluster Fälle mit diesem Attribut ein.  
  
#### <a name="to-compare-two-clusters-by-using-the-cluster-discrimination-tab"></a>So vergleichen Sie zwei Cluster mittels der Registerkarte "Clusterunterscheidung"  
  
1.  Wählen Sie `Pacific Cluster`auf der Registerkarte **Cluster Unterscheidung** für **Cluster 1**die Option aus.  
  
     Standardmäßig wird die Auswahl für **Cluster 2** in **Komplement of Pacific Cluster**geändert.  
  
     Das oberste Attribut, das `Pacific Cluster` von allen anderen Fällen unterscheidet, ist die Region. Region ist ein so starkes Attribut für das Clustering, dass es andere Attribute verdeckt. Um diesen Effekt zu vermeiden, sollten einige der kleineren Cluster miteinander vergleichen. Wenn Sie dies tun, wird die Liste der Attribute geändert und enthält möglicherweise mehr Übergänge zwischen Modellen.  
  
2.  Suchen Sie eine Übergangszeile, und halten Sie die Maus über der schattierten Leiste an.  
  
     Die Elemente in der Spalte **Werte** können sowohl Zustände als auch Übergänge enthalten. Die Schattierung für jedes Element gibt das Unterscheidungsergebnis an. Weitere Informationen zur Bedeutung verschiedener Bewertungen finden Sie unter [Mining Modell Inhalt von Sequence Clustering-Modellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_StateTran"></a>Registerkarte Statusübergänge  
 Auf der Registerkarte **Zustandsübergänge** können Sie einen Cluster auswählen und seine Zustandsübergänge durchsuchen. Wenn Sie in der Dropdown Liste Cluster die Option **Population (alle)** auswählen, zeigt das Diagramm die Verteilung der Zustände für das gesamte Mining Modell an.  
  
 Jeder Knoten im Diagramm stellt einen Status oder möglichen Wert der Sequenzen dar, die Sie versuchen zu analysieren. Die Hintergrundfarbe der Knoten gibt die Frequenz dieses Status an. Zeilen verbinden einige Status und zeigen einen Übergang zwischen Status an. Sie können den Schieberegler nach oben oder unten verschieben, um den Wahrscheinlichkeitsschwellenwert für die Übergänge zu ändern. Einigen Knoten sind Zahlen zugeordnet, die die Wahrscheinlichkeit dieses Status angeben.  
  
#### <a name="to-explore-the-relationships-in-the-state-transition-tab"></a>So untersuchen Sie die Beziehungen auf der Registerkarte "Statusübergänge"  
  
1.  Wählen Sie `Pacific Cluster` auf der Registerkarte **Statusübergänge** des Mining Modell-Viewers in der Liste der Cluster aus. Stellen Sie sicher, dass die Option **Edge-Bezeichnungen anzeigen** ausgewählt ist.  
  
     Das Diagramm wird aktualisiert, um die Übergänge anzuzeigen, die in diesem Cluster am häufigsten sind.  
  
2.  Klicken Sie auf jeden Knoten, der mit einem anderen Knoten durch eine Linie verbunden ist.  
  
     Das Diagramm wird aktualisiert, und die Knoten mit Beziehungen werden hervorgehoben. Der numerische Wert neben der Linie gibt die Wahrscheinlichkeit des Übergangs an.  
  
3.  Erhöhen Sie den Schieberegler bis zu **allen Links**, um die Anzahl der im Diagramm enthaltenen Übergänge zu erhöhen.  
  
4.  Wählen Sie im **Cluster**die Option **Population (alle)** aus.  
  
     Beachten Sie, dass beim Laden eines anderen Clusters das Diagramm zu den Standardanzeigeeinstellungen zurückgesetzt wird, sodass das Schieberegler-Steuerelement auf die mittlere Position zurückgesetzt wird.  
  
5.  Klicken Sie im Diagramm auf den dunkelsten Knoten, der **Sport-100**lauten soll.  
  
     Beachten Sie, dass dieses Produkt nicht durch Linien mit anderen Produkten verbunden ist.  
  
6.  Schieben Sie den Schieberegler um einen Schritt nach oben, um die Anzahl der im Diagramm enthaltenen Übergänge zu vergrößern. Gehen Sie noch nicht bis zu **allen Links** .  
  
     Das Diagramm wird durch das Hinzufügen einiger weiterer Übergänge zum Diagramm aktualisiert, aber keines enthält das Sport-100-Modell.  
  
7.  Verschieben Sie das Schieberegler-Steuerelement auf alle **Links**. Klicken Sie auf den Knoten Sport-100, wenn bereits nicht ausgewählt.  
  
     Das Diagramm wird aktualisiert und zeigt zahlreiche Übergänge an, die das Sport-100-Produkt einschließen. Die Pfeilrichtung auf der verbindenden Zeile zeigt an, ob das Sport-100-Element als erstes oder als zweites Element im Paar ausgewählt wurde.  
  
8.  Klicken Sie auf den Knoten für "Touring Tire" und verschieben Sie das Schieberegler-Steuerelement zurück zur mittleren Position.  
  
     Zum ersten Mal gibt es viele Übergangs Linien, die Touring Tire mit anderen Produkten verbinden. Wenn Sie jedoch den Wahrscheinlichkeits Schwellenwert erhöhen, werden die weniger wahrscheinlichen Übergänge aus dem Diagramm entfernt, sodass nur der Übergang, Touring Tire > Touring Tire Tube, erhalten bleibt. Dieser Übergang zeigt, dass, wenn ein Kunde einen "Touring Tire" in den Warenkorb legt, eine hohe Wahrscheinlichkeit besteht, dass der Kunde als Nächstes einen "Touring Tire Tube" in den Warenkorb legen wird.  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_Generic"></a>Generischer Inhaltsstruktur-Viewer  
 Dieser Viewer kann für alle Modelle verwendet werden, unabhängig vom Algorithmus oder Modelltyp. Der **microsoftgeneric Content Tree Viewer** ist in der Dropdown Liste **Viewer** verfügbar.  
  
 Eine Inhaltsstruktur ist die Darstellung eines Miningmodells als eine Reihe von Knoten, in der jeder Knoten das erlangte Wissen über die Trainingsdaten repräsentiert. Der Knoten kann ein Muster, ein Regelsatz, ein Cluster oder die Definition eines Datenbereichs mit gemeinsamen Attributen sein. Der genaue Inhalt des Knotens ist je nach Algorithmus und vorhersagbarem Attribut unterschiedlich, die allgemeine Darstellung des Inhalts ist jedoch gleich.  
  
 Sie können jeden Knoten erweitern, um zunehmend mehr Details anzuzeigen, und Sie können den Inhalt eines Knotens in die Zwischenablage kopieren. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
#### <a name="to-view-details-for-a-sequence-clustering-model-by-using-the-generic-content-tree-viewer"></a>So zeigen Sie Details für ein Sequenzclustermodell mittels Generic Content Tree Viewer an  
  
1.  Klicken Sie auf der Registerkarte **Mining Modell-Viewer** auf die Liste **Viewer** , und wählen Sie **Microsoft Generic Content Tree Viewer**aus.  
  
2.  Klicken Sie `Pacific Cluster (1)`im Bereich **Knoten Beschriftung** auf.  
  
     Der Name für diesen Knoten enthält sowohl den Anzeigenamen, den Sie dem Cluster zugewiesen haben, und die zugrunde liegende Knoten-ID. Sie können mittels der Knoten-IDs einen Drilldown zu weiteren Details im Modell ausführen.  
  
3.  Erweitern Sie den ersten untergeordneten Knoten mit dem Namen **Sequenz Ebene für Cluster 1**.  
  
     Der Sequenzebenenknoten für einen Cluster enthält Details zu den Status und den Übergängen, die in diesem Cluster enthalten sind. Sie können die in der Spalte NODE_DISTRIBUTION verfügbaren Details verwenden, um die Sequenzen und die Status für die einzelnen Cluster oder für das Modell insgesamt zu untersuchen.  
  
4.  Fahren Sie fort, Knoten zu erweitern und die Details im HTML-Viewer-Bereich anzuzeigen.  
  
 Weitere Informationen zum Mining Modell Inhalt und zur Verwendung der Details im Viewer finden Sie unter [Mining Modell Inhalt von Sequence Clustering-Modellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Erstellen eines zugehörigen Sequence Clustering-Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Sequence Clustering-Algorithmus](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Sequenzclusteringmodellabfragebeispiele](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)  
  
  
