---
title: Prüfen der Sequence Clustering-Modells (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: f8a485d5-47ed-4dd5-bb66-ef4d6d463845
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a30991f6104263d4c6f497a721cee340f3dc9e2b
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49085476"
---
# <a name="exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Prüfen des Sequenzclustermodells (Data Mining-Lernprogramm)
  Nun, dass Sie erstellt haben die **Sequenzcluster mit Region** Modell durchsuchen können Sie es mit der [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequenzcluster-Viewer auf die **Miningmodell-Viewer** -Registerkarte des Data Mining-Designers. Die [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequenzcluster-Viewer enthält fünf Registerkarten: **Clusterdiagramm**, **Clusterprofile**, **Clustermerkmale**,  **ClusterDiscrimination**, und **Statusübergänge**. Weitere Informationen zum Verwenden des Viewers finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Sequenzcluster-Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).  
  
-   [Registerkarte Clusterdiagramm](#bkmk_CDiagram)  
  
-   [Registerkarte Clusterprofile](#bkmk_CProfiles)  
  
-   [Cluster-Registerkarte "Clustermerkmale"](#bkmk_CChars)  
  
-   [Registerkarte Clusterunterscheidung](#bkmk_CDiscrim2)  
  
-   [Registerkarte "Statusübergänge"](#bkmk_StateTran)  
  
-   [Generische Inhaltssicht](#bkmk_Generic)  
  
##  <a name="bkmk_CDiagram"></a> Registerkarte Clusterdiagramm  
 Die **Clusterdiagramm** Registerkarte zeigt die vom Algorithmus erkannten Cluster grafisch in der Datenbank an. Das Layout im Diagramm gibt die Beziehungen der Cluster an, wobei ähnliche Cluster nahe zusammen gruppiert sind. Standardmäßig gibt die Schattierung der einzelnen Knotenfarben die Dichte aller Fälle auf dem Cluster an, d. h., je dunkler die Schattierung des Knotens, desto mehr Fälle enthält er. Sie können die Bedeutung der Knotenschattierung ändern, sodass diese die Unterstützung in den einzelnen Clustern für ein Attribut und einen Status darstellt.  
  
 Sie können die Cluster auch umbenennen, um es einfacher zu machen, Zielcluster zu identifizieren und mit diesen zu arbeiten. Für dieses Lernprogramm benennen Sie den Cluster um, der den höchsten Prozentsatz an Kunden aus der Pazifikregion hat, und der Cluster, sowie den Cluster, der insgesamt die meisten Fälle enthält.  
  
> [!NOTE]  
>  Die Fälle, die bestimmten Clustern zugewiesen sind, können sich abhängig von den Daten und den Modellparametern ändern, wenn Sie das Modell neu verarbeiten. Auch wenn Sie Cluster umbenennen, gehen die Namen verloren, wenn Sie das Miningmodell erneut verarbeiten.  
  
#### <a name="to-change-the-attribute-used-for-highlighting-clusters"></a>So ändern Sie das für die Hervorhebung von Clustern verwendete Attribut  
  
1.  In der **Schattierungsvariable** Liste **Modell**.  
  
2.  Wählen Sie **Cycling Cap** in die **Zustand** Liste.  
  
     Das Diagramm wird aktualisiert, um die Konzentration des ausgewählten Produkts in jeden der Cluster anzuzeigen. Der Cluster mit der dunkelsten Schattierung weist die höchste Dichte für das Produkt "Cycling Caps" auf. Sie können die schattierungsvariable zur Verwendung von einem beliebigen Zustand einer beliebigen Eingabespalte ändern.  
  
3.  In der **Schattierungsvariable** Liste **Auffüllung**.  
  
     Wenn Sie die Schattierungsvariable in "Auffüllung" ändern, wird das Diagramm aktualisiert, um die Cluster der Größe nach zu vergleichen. Der Cluster, der die dunkelste Schattierung aufweist, enthält mehr Fälle als die anderen Cluster.  
  
#### <a name="to-rename-nodes-in-the-model"></a>So benennen Sie Knoten im Modell um  
  
1.  Änderung **Schattierungsvariable** zu `Region`, und legen Sie **Zustand** zu **Pacific**.  
  
2.  Heben Sie den dunkelsten Knoten im Diagramm hervor.  
  
3.  Mit der rechten Maustaste in diesem Cluster, und wählen Sie **Cluster umbenennen.**  
  
4.  Geben Sie den Namen**Pazifikcluster.**  
  
5.  Ändern Sie den Wert der **Schattierungsvariable** zu **Auffüllung**.  
  
6.  Suchen Sie im aktualisierten Diagramm den dunkelsten Cluster; dieser sollte der größte Cluster sein. Wenn Sie nicht mittels der Schattierung erkennen können, welcher Cluster am größten ist, halten Sie den Mauszeiger Maus über jedem Cluster an, und zeigen Sie die QuickInfo an. Wählen Sie dann den Cluster aus, der die meisten Fälle enthält.  
  
7.  Mit der rechten Maustaste in diesem Cluster, und wählen Sie **Cluster umbenennen**. Geben Sie den neuen Namen `Largest Cluster`.  
  
 Sie können einen Drillthrough von dem Knoten aus durchführen, der den Cluster darstellt, um Details der Fälle anzuzeigen, die in jedem Cluster enthalten sind. Dies kann nützlich sein, wenn Sie auf aufgrund der Ergebnisse Ihrer Analyse handeln, z. B. wenn Sie E-Mails an einen Kunden senden. Sie können auch die anderen Attribute der Fälle durchsuchen, die Sie in die Struktur eingeschlossen haben, aber nicht im Modell verwendet haben, z. B. Region und IncomeGroup. Weitere Informationen zu Drillthrough von Miningmodellen zu den zugrunde liegenden Fällen finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).  
  
#### <a name="to-drill-through-to-details-from-the-cluster-diagram"></a>So führen Sie einen Drillthrough zu Details vom Clusterdiagramm aus durch  
  
1.  Mit der rechten Maustaste `Pacific Cluster`Option **Drillthrough**, und wählen Sie dann **Modell-und Strukturspalten**.  
  
     Die **Drillthrough** Dialogfeld wird geöffnet. Spalten, die nicht im Modell verwendet werden, aber, die für Abfragen verfügbar sind, vorangestellt **Struktur**.  
  
     Sie können sehen, dass dieser Cluster meistens Kunden aus der Pazifikregion enthält und nur wenige Kunden aus anderen Regionen.  
  
2.  Klicken Sie in der geschachtelten Spalte "v Assoc Seq Line Items" auf das Pluszeichen, um die Sequenz von Elementen in einem bestimmten Kundenbefehl anzuzeigen.  
  
3.  Schließen der **Drillthrough** Dialogfeld.  
  
    > [!NOTE]  
    >  Die **spielen** Schaltfläche können Sie die Daten erneut abzufragen; erneutes Abfragen nicht ändert sich jedoch die Daten, die angezeigt werden, es sei denn, das Modell von einem anderen Prozess dynamisch im Hintergrund aktualisiert wurde.  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_CProfiles"></a> Registerkarte Clusterprofile  
 Die **Clusterprofile** Registerkarte zeigt die Sequenzen, die in jedem Cluster an. Die Cluster finden Sie in den einzelnen Spalten rechts von der **Zustände** Spalte.  
  
 Im Viewer die **Modell** Zeile beschreibt die gesamtverteilung der Elemente in einem Cluster und die **Model.samples** Zeile enthält Sequenzen der Elemente. Jede Linie der farbsequenzen in jeder Zelle der der **Model.samples** Zeile darstellt, das Verhalten eines zufällig ausgewählten Benutzers im Cluster.  
  
 Jede Farbe in einem Sequenzhistogramm steht für ein Produktmodell. In der Mininglegende werden Sequenzen von Produkten sowohl unter Verwendung der Farbcodierung als auch des Produktmodellnamens angezeigt. Wenn Sie dem Modell für Clustering, z. B. Region oder Einkommensgruppe, weitere Spalten hinzugefügt haben, enthält der Viewer eine zusätzliche Zeile für jede Spalte, die die Verteilung dieser Werte innerhalb jedes Clusters anzeigt.  
  
#### <a name="to-view-the-sequences-that-are-most-common-in-a-cluster"></a>So zeigen Sie die Sequenzen an, die in einem Cluster am häufigsten sind  
  
1.  Mit der rechten Maustaste die **Modell** Zeile in der Spalte für den Cluster `Largest Cluster`, und wählen Sie **Legende anzeigen**.  
  
     Die **Farbe** Spalte enthält einen schattierten Balken, der die Häufigkeit der Elemente, die in Sequenzen gesucht wurden angibt. Jedes Element wird durch eine andere Farbe dargestellt. Die **Bedeutung** Spalte führt die produktmodellnamen für jede Farbe. Die **Verteilung** Spalte verrät Ihnen, den Prozentsatz der Fälle, die dieses Element in einer Sequenz enthalten.  
  
2.  Schließen der **Mininglegende**.  
  
3.  Mit der rechten Maustaste die **Model.samples** Zeile in der Spalte mit der **Auffüllung** , und wählen Sie **Legende anzeigen**.  
  
4.  Überprüfen Sie die Liste der Sequenzen im Gesamtmodell`.`  
  
     In der Mininglegende werden zuerst die häufigsten Sequenzen aufgelistet. Das Produkt "Mountain Tire Tube" ist das erste Element in vielen Sequenzen. Das bedeutet, dass ein Kunde "Mountain Tire Tube" höchstwahrscheinlich als Erstes in den Warenkorb legen wird.  
  
#### <a name="to-drill-through-to-cases-from-the-cluster-viewer"></a>So führen Sie einen Drillthrough zu Fällen vom Cluster-Viewer aus durch  
  
1.  Scrollen Sie im Bereich Attribut finden Sie auf die Zeile für die `Region` Attribut.  
  
     Die Zeile enthält ein Histogramm für jeden Cluster im Modell sowie ein zusätzliches Histogramm für **Auffüllung**, d. h. den gesamten Satz von Fällen im Modell verwendet. Ein Histogramm ist eine Leiste mit verschiedenen Farben, wobei jede Farbe ein Attribut darstellt, und die Größe des farbigen Abschnitts für dieses Attribut stellt den Prozentsatz der Fälle mit diesem Attribut dar.  
  
2.  Vergleichen Sie die Histogramme für den Cluster, die Sie umbenannt `Pacific Cluster` und `Largest Cluster`. Jeder Cluster wird in einer anderen Spalte angezeigt.  
  
     Beide Cluster werden in Volltonfarben angezeigt, jedoch in unterschiedlichen Farben.  
  
3.  In der `Region` Zeile, halten Sie die Maus über dem farbigen Histogramm für `Largest Cluster`.  
  
     Die QuickInfo zeigt Werte an, die die tatsächlichen Prozentsätze der Fälle aus jedem Bereich anzeigen.  
  
4.  Mit der rechten Maustaste in des farbigen Histogramms der `Region` -Zeile für `Pacific Cluster`Option **Drillthrough**, und wählen Sie dann **nur Modellspalten**.  
  
5.  Verschieben Sie die Bildlaufleiste, um alle Kunden in diesen Cluster zu überprüfen.  
  
     Sie können erneut mittels Drillthrough zu den Details erkennen, dass der Cluster zumeist Bestellungen aus der Pazifikregion enthält, aber auch einige wenige aus den Regionen Nordamerika und Europa.  
  
6.  Schließen der **Drillthrough** Dialogfeld.  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_CChars"></a> Cluster-Registerkarte "Clustermerkmale"  
 Die **Clustermerkmale** Registerkarte fasst die Übergänge zwischen den Statuswerten eines Clusters mit Balken an, die die Bedeutung eines Attributwerts für den ausgewählten Cluster visuell darstellen. Die **Variablen** Spalte verrät Ihnen, was das Modell gefunden, für den ausgewählten Cluster oder Auffüllung wichtig sein: entweder einen bestimmten Wert oder die Beziehung zwischen Werten, bekannt als *Übergang*. Die **Werte** Spalte stellt weitere Details zum Wert oder Übergang bereit und **Wahrscheinlichkeit** Spalte stellt die Gewichtung dieses Attributs oder Übergangs visuell dar.  
  
#### <a name="to-view-the-important-attributes-for-a-cluster"></a>So zeigen Sie die wichtigen Attribute für einen Cluster an  
  
1.  In der **Cluster** Dropdownliste `Pacific Cluster`.  
  
     Die Liste aktualisiert wird, um die Merkmale des Clusters anzuzeigen, die Sie umbenannt `Pacific Cluster`. In diesem Cluster ist das wichtigste Merkmal ist `Region`.  
  
2.  Halten Sie die Maus über der schattierten Leiste in der Zeile für `Region`.  
  
     Die Wahrscheinlichkeit, dass der Wert "Pazifik" ist, ist sehr hoch. Weitere Informationen zum Interpretieren dieser Werte finden Sie unter [Microsoft Sequence Clustering Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md).  
  
3.  Sehen Sie die Liste der Eigenschaften für den Cluster durch, bis Sie die erste Übergangszeile gefunden haben.  
  
4.  Eine Übergangszeile enthält den Text Übergang in die **Variablen** Spalte und eine Kombination sequenzieller Attributwerte in die **Wert** Spalte. Die Sequenz kann auch Anfangspunkte und fehlende Werte enthalten.  
  
     Nehmen Sie z. B. an, dass der Übergang den Wert "[Start] -> Road Tire Tube" hat. Dies bedeutet, dass Kunden in diesem Cluster häufig "Road Tire Tube" zuerst in den Warenkorb gelegt haben. Dies kann anzeigen, dass das Produkt ein häufiges Element ist, das Kunden als Erstes suchen, oder es kann anzeigen, dass das Produkt einfach auf der Einkaufswebsite zu finden ist.  
  
5.  In der Liste aus, bis Sie den ersten Übergang finden, die nicht **[Start]** oder **fehlende** darin.  
  
     Nehmen wir beispielsweise an, die Sie feststellen, dass der Übergang **Touring Tire, Touring Tire Tube**. Dies bedeutet, dass Kunden in diesem Cluster diese Elemente und genau in dieser Reihenfolge häufig zusammen gekauft haben.  
  
6.  Halten Sie die Maus über der schattierten Leiste für diesen Übergang an.  
  
     Die Wahrscheinlichkeit dieses Übergangs wird als ein Prozentsatz angezeigt.  
  
7.  In der **Cluster** Dropdownliste **Auffüllung (alle)**.  
  
     Die Liste der Attribute wird aktualisiert, um die Eigenschaften aller Bestellungen anzuzeigen, die verwendet wurden, um das Modell zu erstellen. In diesem Miningmodell ist das wichtigste Merkmal für die unterschiedung zwischen Clustern wird `Region`, mit dem Wert **Nordamerika**.  
  
 Sie erkennen zwei Dinge, nachdem Sie diese Tasks überprüft haben. Zum einen benötigen Sie viele Daten, um eine sinnvolle Anzahl von Kombinationen abzurufen. Beispielsweise sind die Sequenzen mit den höchsten Wahrscheinlichkeiten wahrscheinlich eine **[Start]** oder **Missing** Zustand.  
  
 Die zweite ist, dass es eine starke clusteringauswirkung auf Attribute für `Region`, wodurch es schwieriger, die Gruppen von Sequenzen finden Sie unter. Daher entscheiden Sie sich, ein anderes Modell zu erstellen, das nur Sequenzen verwendet und keine Spalten für die Region oder das Einkommen enthalten.  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_CDiscrim2"></a> Registerkarte Clusterunterscheidung  
 Die **Clusterunterscheidung** Registerkarte können Sie die zwei Cluster, um zu bestimmen, welche Attribute einen bestimmten Cluster unterscheidet sich von einem anderen Cluster vergleichen. Die Registerkarte enthält vier Spalten: **Variablen**, **Werte**, **Cluster 1**, und **Cluster 2**.  Sie können eine beliebige Cluster die Verwendung als **Cluster 1** und **Cluster 2**.  
  
 Die **Variablen** Spalte verrät Ihnen, den Namen des Attributs, die entweder einen Spaltennamen oder eine Kombination aus Spaltennamen und dem Wort **Übergang**. Die **Werte** Spalte zeigt den genauen Wert des Attributs oder des Übergangs. Die schattierten Leisten in den Spalten für **Cluster 1** und **Cluster 2** geben die Stärke des Attributs in den Clustern, die Sie vergleichen. Je länger die Leiste, desto wahrscheinlicher schließt der Cluster Fälle mit diesem Attribut ein.  
  
#### <a name="to-compare-two-clusters-by-using-the-cluster-discrimination-tab"></a>So vergleichen Sie zwei Cluster mittels der Registerkarte "Clusterunterscheidung"  
  
1.  In der **Clusterunterscheidung** Registerkarte für **Cluster 1**Option `Pacific Cluster`.  
  
     Standardmäßig wird die Auswahl für **Cluster 2** Änderungen an **Komplement von Pacific *** Cluster**.  
  
     Das oberste Attribut, das unterscheidet `Pacific Cluster` von allen anderen Fällen ist die Region. Region ist ein so starkes Attribut für das Clustering, dass es andere Attribute verdeckt. Um diesen Effekt zu vermeiden, sollten einige der kleineren Cluster miteinander vergleichen. Wenn Sie dies tun, wird die Liste der Attribute geändert und enthält möglicherweise mehr Übergänge zwischen Modellen.  
  
2.  Suchen Sie eine Übergangszeile, und halten Sie die Maus über der schattierten Leiste an.  
  
     Die Elemente in der **Werte** Spalte kann sowohl Statuswerte als auch Übergänge enthalten. Die Schattierung für jedes Element gibt das Unterscheidungsergebnis an. Informationen zur Bedeutung anderer Ergebnisse finden Sie unter [Mingingmodellinhalt von Sequence Clustering-Modellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_StateTran"></a> Registerkarte "Statusübergänge"  
 Auf der **Statusübergänge** Registerkarte können Sie einen Cluster auswählen und die Statusübergänge durchsuchen. Bei Auswahl von **Auffüllung (alle)** aus der Dropdown-Clusterliste das Diagramm zeigt die Verteilung der Status für das ganze Miningmodell.  
  
 Jeder Knoten im Diagramm stellt einen Status oder möglichen Wert der Sequenzen dar, die Sie versuchen zu analysieren. Die Hintergrundfarbe der Knoten gibt die Frequenz dieses Status an. Zeilen verbinden einige Status und zeigen einen Übergang zwischen Status an. Sie können den Schieberegler nach oben oder unten verschieben, um den Wahrscheinlichkeitsschwellenwert für die Übergänge zu ändern. Einigen Knoten sind Zahlen zugeordnet, die die Wahrscheinlichkeit dieses Status angeben.  
  
#### <a name="to-explore-the-relationships-in-the-state-transition-tab"></a>So untersuchen Sie die Beziehungen auf der Registerkarte "Statusübergänge"  
  
1.  In der **Statusübergänge** den Miningmodell-Viewer, die auf der Registerkarte `Pacific Cluster` aus der Liste der Cluster. Sicherstellen, dass die **Kantenbezeichnungen anzeigen** ausgewählt ist.  
  
     Das Diagramm wird aktualisiert, um die Übergänge anzuzeigen, die in diesem Cluster am häufigsten sind.  
  
2.  Klicken Sie auf jeden Knoten, der mit einem anderen Knoten durch eine Linie verbunden ist.  
  
     Das Diagramm wird aktualisiert, und die Knoten mit Beziehungen werden hervorgehoben. Der numerische Wert neben der Linie gibt die Wahrscheinlichkeit des Übergangs an.  
  
3.  Schieben Sie den Regler bis zu **alle Links**, um die Anzahl der im Diagramm enthaltenen Übergänge zu erhöhen.  
  
4.  Wählen Sie **Auffüllung (alle)** aus **Cluster**.  
  
     Beachten Sie, dass beim Laden eines anderen Clusters das Diagramm zu den Standardanzeigeeinstellungen zurückgesetzt wird, sodass das Schieberegler-Steuerelement auf die mittlere Position zurückgesetzt wird.  
  
5.  Klicken Sie auf den dunkelsten Knoten im Diagramm, der sein soll **Sport-100**.  
  
     Beachten Sie, dass dieses Produkt nicht durch Linien mit anderen Produkten verbunden ist.  
  
6.  Schieben Sie den Schieberegler um einen Schritt nach oben, um die Anzahl der im Diagramm enthaltenen Übergänge zu vergrößern. Gehen Sie nicht ganz nach **alle Links** noch.  
  
     Das Diagramm wird durch das Hinzufügen einiger weiterer Übergänge zum Diagramm aktualisiert, aber keines enthält das Sport-100-Modell.  
  
7.  Verschieben Sie das Schieberegler-Steuerelement ganz nach **alle Links**. Klicken Sie auf den Knoten Sport-100, wenn bereits nicht ausgewählt.  
  
     Das Diagramm wird aktualisiert und zeigt zahlreiche Übergänge an, die das Sport-100-Produkt einschließen. Die Pfeilrichtung auf der verbindenden Zeile zeigt an, ob das Sport-100-Element als erstes oder als zweites Element im Paar ausgewählt wurde.  
  
8.  Klicken Sie auf den Knoten für "Touring Tire" und verschieben Sie das Schieberegler-Steuerelement zurück zur mittleren Position.  
  
     Zunächst werden zahlreiche Übergangszeilen angezeigt, die "Touring Tire" mit anderen Produkten verbinden. Wenn Sie jedoch den Wahrscheinlichkeitsschwellenwert erhöhen, werden die weniger wahrscheinlichen Übergänge aus dem Diagramm entfernt, sodass nur der Übergang "Touring Tire > Touring Tire Tube" übrig bleibt. Dieser Übergang zeigt, dass, wenn ein Kunde einen "Touring Tire" in den Warenkorb legt, eine hohe Wahrscheinlichkeit besteht, dass der Kunde als Nächstes einen "Touring Tire Tube" in den Warenkorb legen wird.  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
##  <a name="bkmk_Generic"></a> Generic Content Tree-Viewer  
 Dieser Viewer kann für alle Modelle verwendet werden, unabhängig vom Algorithmus oder Modelltyp. Die **MicrosoftGeneric Content Tree Viewer** steht über den **Viewer** Dropdown-Liste.  
  
 Eine Inhaltsstruktur ist die Darstellung eines Miningmodells als eine Reihe von Knoten, in der jeder Knoten das erlangte Wissen über die Trainingsdaten repräsentiert. Der Knoten kann ein Muster, ein Regelsatz, ein Cluster oder die Definition eines Datenbereichs mit gemeinsamen Attributen sein. Der genaue Inhalt des Knotens ist je nach Algorithmus und vorhersagbarem Attribut unterschiedlich, die allgemeine Darstellung des Inhalts ist jedoch gleich.  
  
 Sie können jeden Knoten erweitern, um zunehmend mehr Details anzuzeigen, und Sie können den Inhalt eines Knotens in die Zwischenablage kopieren. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
#### <a name="to-view-details-for-a-sequence-clustering-model-by-using-the-generic-content-tree-viewer"></a>So zeigen Sie Details für ein Sequenzclustermodell mittels Generic Content Tree Viewer an  
  
1.  In der **Miningmodell-Viewer** Registerkarte, klicken Sie auf die **Viewer** aus, und wählen Sie **Microsoft Generic Content Tree Viewer**.  
  
2.  In der **Knotenbeschriftung** Bereich, klicken Sie auf `Pacific Cluster (1)`.  
  
     Der Name für diesen Knoten enthält sowohl den Anzeigenamen, den Sie dem Cluster zugewiesen haben, und die zugrunde liegende Knoten-ID. Sie können mittels der Knoten-IDs einen Drilldown zu weiteren Details im Modell ausführen.  
  
3.  Erweitern Sie den ersten untergeordneten Knoten, der mit dem Namen **Sequenzebene für Cluster 1**.  
  
     Der Sequenzebenenknoten für einen Cluster enthält Details zu den Status und den Übergängen, die in diesem Cluster enthalten sind. Sie können die in der Spalte NODE_DISTRIBUTION verfügbaren Details verwenden, um die Sequenzen und die Status für die einzelnen Cluster oder für das Modell insgesamt zu untersuchen.  
  
4.  Fahren Sie fort, Knoten zu erweitern und die Details im HTML-Viewer-Bereich anzuzeigen.  
  
 Weitere Informationen zum Inhalt des Miningmodells, und wie Sie mit den Details im Viewer finden Sie unter [Miningmodellinhalt für Sequence Clustering-Modellen &#40;Analysis Services – Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md).  
  
 [Zurück zum Anfang](#bkmk_CDiagram)  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen ein Clustermodells für verwandte Sequenzen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Sequence Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Abfragebeispiele für Sequenzclusteringmodelle](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)  
  
  
