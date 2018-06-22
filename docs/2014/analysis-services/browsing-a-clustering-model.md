---
title: Durchsuchen eines Clustermodells | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fab210756002a80e392bac74e7d1378679b05b2f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046794"
---
# <a name="browsing-a-clustering-model"></a>Durchsuchen eines Clustermodells
  Wenn Sie öffnen ein Clusteringmodell mit **Durchsuchen**, das Modell wird angezeigt, in einem interaktiven Viewer, ähnlich wie den clustering-Viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Die Viewer unterstützt Sie dabei, die erstellten Cluster zu untersuchen und die Clustermerkmale zu verstehen. Darüber hinaus können Sie einzelne Segmente mit anderen Segmenten oder mit der Grundgesamtheit vergleichen und die Unterschiede untersuchen.  
  
##  <a name="BKMK_Tabs"></a> Untersuchen des Modells  
 Die **Durchsuchen** Fenster enthält die folgenden Tools, mit denen Sie das Clusteringmodell zu verstehen und die Attribute des zugrunde liegenden Datengruppen zu untersuchen:  
  
-   [Clusterdiagramm](#BKMK_ClusterDiagram)  
  
-   [Clusterprofile](#BKMK_ClusterProfiles)  
  
-   [Clustermerkmale](#BKMK_ClusterCharacteristics)  
  
-   [Clusterunterscheidung](#BKMK_ClusterDiscrimination)  
  
 Um mit einem Clusteringmodell zu experimentieren, können Sie die Beispieldaten auf der Registerkarte Training der Beispieldaten-Arbeitsmappe verwenden, und erstellen Sie ein Clusteringmodell mit [Clustererstellungs-Assistenten &#40;Data Mining-Add-ins für Excel&#41; ](cluster-wizard-data-mining-add-ins-for-excel.md) und allen Standardeinstellungen .  
  
###  <a name="BKMK_ClusterDiagram"></a> Clusterdiagramm  
 Die **Clusterdiagramm** Registerkarte werden alle, die in einem Miningmodell enthaltenen Cluster angezeigt. Hier sehen Sie, wie viele verschiedene Gruppierungen im Dataset enthalten sind und wie nah oder weit sie voneinander entfernt liegen.  
  
##### <a name="explore-the-cluster-diagram"></a>Untersuchen des Clusterdiagramms  
  
1.  Klicken Sie auf Cluster 1 im Diagramm.  
  
     Sie können beobachten, wie sich die grauen Linien, die alle Cluster verbinden, ändern. Die Linien, die zum ausgewählten Cluster führen, sind in hellem Blau hervorgehoben.  
  
     ![Clusterdiagramm-Intro](media/dm13-cluster-diagram-intro.gif "Clusterdiagramm-Intro")  
  
     Anhand der Stärke der Linie, die einen Cluster mit einem anderen verbindet, können Sie die Ähnlichkeit der Cluster ableiten. Ist die Schattierung schwach oder ist keine Schattierung vorhanden, sind sich die Cluster kaum ähnlich. Je stärker die Linie ist, desto größer ist die Ähnlichkeit zwischen den beiden Clustern.  
  
2.  Klicken und ziehen Sie den Schieberegler zur linken Seite des Clusterdiagramms, um die Anzahl der Linien anzupassen, die im Viewer angezeigt werden.  
  
     Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Verbindungslinien zwischen Clustern angezeigt. So können Sie verwandte Gruppen leichter fokussieren.  
  
3.  Beachten Sie, dass die **Schattierungsvariable** in der oberen rechten Ecke des Steuerelements die **Clusterdiagramm** Fenster.  
  
     Standardmäßig wird es auf festgelegt, **Auffüllung**. Das bedeutet, dass die Cluster mit der dunkleren Schattierung größere Unterstützung erhalten.  
  
4.  Platzieren Sie den Cursor auf einem beliebigen Cluster.  
  
     Eine QuickInfo wird angezeigt, in der die Auffüllung des Clusters enthalten ist.  
  
5.  Klicken Sie nun auf die **Schattierungsvariable** Dropdownliste aus, und wählen Sie die **Alter** Variable. Wie in diesem Fall wird eine Liste von Werten der **Zustand** Textfeld.  
  
     Die als Eingabe für dieses Modell verwendete Spalte Alter enthält fortlaufende numerische Werte, zu Clusteringzwecken werden die Zahlen vom Algorithmus jedoch immer diskretisiert. Hier sehen Sie die Klassifizierungen oder Gruppen, die der Algorithmus erstellt werden, z. B. "sehr niedrig (\<= 27)" und "sehr hoch (> = 63)".  
  
6.  Aus der **Status** Dropdownlisten auswählen **sehr hohen** und beobachten Sie, wie das Diagramm ändert.  
  
     Indem Sie die Schattierungsvariable ändern, erkennen Sie auf einen Blick, welche Cluster mehr und welche nur wenige Kunden dieser Altersgruppe enthalten.  
  
     ![Ändern des clusterdiagramms zur Anzeige des Alters](media/dm13-cluster-diagramshadebyage.gif "Ändern des clusterdiagramms zur Anzeige des Alters")  
  
     Je stärker die Schattierung, desto größer ist der Anteil der Zielattribut- und Werteverteilung des Clusters.  
  
7.  Suchen Sie den Cluster, die schattiert ist dunkelsten bei der **Schattierungsvariable** festgelegt ist, um Alter > 65.  
  
     Zeigen Sie mit der Maus auf den Cluster.  
  
     Der in der QuickInfo angezeigte Wert zeigt jetzt die Grundgesamtheit der Kunden in diesem Cluster an, die älter als 65 sind.  
  
8.  Mit der rechten Maustaste in des Clusters, und wählen Sie **Cluster umbenennen**. Geben Sie einen neuen Namen, die beschreibenden, z. B. **über 65**. Der neue Name wird mit dem Modell auf dem Server gespeichert und kann zum Identifizieren des Clusters in den anderen Clusteringsichten verwendet werden.  
  
 [Zurück nach oben](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterProfiles"></a> Clusterprofile  
 Die **Clusterprofile** Registerkarte können Sie die Zusammensetzung aller Cluster auf einen Blick zu vergleichen. Dies ist ein guter Ausgangspunkt, um sich mit dem Modell vertraut zu machen. Diese Ansicht ist auch später hilfreich, wenn Sie einen bestimmten Cluster untersuchen und zu dem Schluss kommen, dass Sie verwandte Cluster suchen müssen.  
  
 **Clusterprofile** erhalten Sie auch einen guten Überblick darüber, wie der Cluster voneinander unterscheiden. Daher kann es praktisch sein, jedem Cluster mithilfe dieser Ansicht einen aussagekräftigen Namen zu geben.  
  
##### <a name="explore-the-cluster-profiles"></a>Untersuchen der Clusterprofile  
  
1.  Klicken Sie auf die Zelle für Berufsbezeichnungen, in der **Zustände** -Spalte, um die Liste aller Werte für Beruf anzuzeigen.  
  
2.  Platzieren Sie jetzt den Cursor in den Clusterprofilen auf Beruf.  
  
     Die QuickInfo zeigt die Verteilung von Berufen in diesem Cluster an.  
  
     ![Anzeigen ausführlicher Werte in QuickInfos oder in der Legende](media/dm13-cluster-profile-age-tooltip.gif "Anzeigen ausführlicher Werte in QuickInfos oder in der Legende")  
  
     Beachten Sie, dass in einigen (z. B. die gerade in der Abbildung), die Liste der Berufe Clustern ist nicht vollständig, und einige Berufe ersetzt werden, mit der Bezeichnung **andere**.  
  
     Dieses Verhalten ist programmbedingt, da es schwierig sein kann, den Unterschied zwischen vielen kleinen Balken im Histogramm auszumachen. Standardmäßig werden nur die wichtigsten Balken von größter Wichtigkeit beibehalten und die restlichen Balken werden dabei in einem grau zusammengruppiert **andere** Bucket.  
  
     Um die Anzahl der Balken zu ändern, die in einem beliebigen Histogramm angezeigt werden, verwenden Sie die Option **Histogrammbalken**.  
  
3.  Beachten Sie, dass die **Alter** Spalte die anderen anders aussieht. Klicken Sie auf die Raute im Diagramm, durch das das Alter dargestellt wird.  
  
     Die Spalte Alter enthielt ursprünglich nur fortlaufende Zahlen. Der Clusteringalgorithmus erfordert diskrete Werte. Folglich wurden die numerischen Werte in der Spalte Alter – basierend auf der Werteverteilung – unter einer eingeschränkten Anzahl von Altersgruppen gruppiert.  
  
4.  Klicken Sie auf eines der Rautendiagramme in einem Clusterprofil.  
  
     Diese Rautendiagramme werden nur angezeigt, wenn die Quelldaten fortlaufende numerische Werte enthalten. Die Rautendiagramme stellen einige aussagekräftige Statistiken bereit, einschließlich der mittleren und Standardabweichung dieses Werts in den einzelnen Clustern:  
  
    -   Die Linie im Rautendiagramm stellt den Wertebereich für das Attribut dar. Die Werte werden auch angezeigt, der **Zustände** Spalte am linken Rand der **Profile** Diagramm.  
  
    -   Der Mittelpunkt der Raute orientiert sich am Mittelwert des Knotens.  
  
    -   Die Breite der Raute gibt die Varianz des Attributs in diesem Knoten an. Eine schlankere Raute sagt also aus, dass mithilfe des Knotens eine genauere Vorhersage getroffen werden kann.  
  
5.  Um mehr Platz im Diagramm schaffen, Maustaste einen Cluster müssen Sie nicht sofort anzuzeigen, und wählen **Spalte ausblenden**. Dadurch wird der Cluster nicht aus dem Modell gelöscht, sondern nur vorübergehend in der Spalte ausgeblendet.  
  
     Um Cluster anzuzeigen, die Sie ausgeblendet haben, klicken Sie auf, und ziehen Sie den Spaltenrand oder wählen Sie den Clusternamen aus der Liste **mehr Cluster**.  
  
6.  Führen Sie in der Attributliste einen Bildlauf bis Bike Buyer durch, und suchen Sie dann den Cluster, der den höchsten Prozentsatz an Ja-Werten aufweist.  
  
     Mit der rechten Maustaste für den Cluster, die Sie umbenennen möchten, wählen Sie den Spaltenüberschrift **umbenennen Cluster**, und geben **Fahrradkäufer**.  
  
     Der neue Clustername wird in allen Ansichten und auf dem Server beibehalten, bis Sie das Modell erneut verarbeiten.  
  
     ![Umbenennen von Clusters zur Diagramm einfacher zu verwenden ist](media/dm13-cluster-rename.gif "Umbenennen von Clusters zum Diagramm einfacher zu verwenden ist.")  
  
 **Tipps**  
  
-   Klicken Sie auf eine Spaltenüberschrift, um die Attribute nach der Reihenfolge der Wichtigkeit für diesen Cluster zu sortieren.  
  
-   Ziehen Sie die Spalten, um sie im Viewer neu anzuordnen.  
  
-   Klicken Sie auf eine beliebige Zelle im profildiagramm, um detaillierte Statistikdaten in Anzeigen der **Mininglegende**.  
  
-   Maustaste auf eine beliebige Zelle, und wählen Sie **Drillthrough-modellspalten** die zugrunde liegenden Daten in ein neues Arbeitsblatt in Excel ausgegeben.  
  
-   Mit der rechten Maustaste in der Clusterspalte Spaltenüberschrift und wählen Sie **Drillthroughs zu Strukturdaten** um detaillierte Informationen zu Clusterelementen abzurufen, die im Modell enthalten waren.  
  
     Wenn Sie Kundenprofile erstellen, können Sie die Kontaktinformationen z. B. in den zugrunde liegenden Daten (der Miningstruktur) belassen, ohne sie in das Modell einzuschließen, da sie für die Analyse nicht relevant sind. Nachdem die Kunden den Clustern zugewiesen wurden, können Sie die detaillierten Daten jedoch mithilfe eines Drillthrough-Vorgangs anzeigen.  
  
 [Zurück nach oben](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterCharacteristics"></a> Clustermerkmale  
 In der Ansicht Clustermerkmale können Sie einen einzelnen Cluster gründlich untersuchen, um herauszufinden, durch welche Attribute diese Datengruppe am stärksten charakterisiert wird.  
  
##### <a name="explore-the-cluster-characteristics"></a>Untersuchen der Clustermerkmale  
  
1.  Wählen Sie die **über 65** cluster von den **Cluster** Liste.  
  
     Nachdem Sie einen Cluster ausgewählt haben, können Sie die Merkmale dieses Clusters eingehend untersuchen.  
  
     Die im Cluster enthaltenen Attribute werden in den **Variablen** -Spalten und der Status der aufgelisteten Attribute in der **Werte** -Spalte aufgelistet.  
  
     Attributstatus werden aufgelistet, in der Reihenfolge ihrer Wichtigkeit von deren Wahrscheinlichkeit in diesem Cluster, dargestellt als eine farbige Leiste in begleitet die **Wahrscheinlichkeit** Spalte.  
  
     ![Merkmale eines Clusteringmodells](media/dm13-cluster-characteristics.gif "Merkmale eines Clusteringmodells")  
  
2.  Klicken Sie auf die **Variablen** Spalte nach Attribut zu sortieren.  
  
     Indem Sie die Sortierungsvariable ändern, können Sie leichter erkennen, wie Werte für Variablen, z. B. Einkommen oder Autobesitz, in der Gruppe verteilt sind.  
  
3.  Klicken Sie auf **nach Excel kopieren**.  
  
     Der Arbeitsmappe wird ein neues Arbeitsblatt hinzugefügt, das die Merkmale des ausgewählten Clusters enthält.  
  
4.  Wählen Sie jetzt einen anderen Cluster aus der Liste **Fahrradkäufer**.  
  
5.  Klicken Sie auf **nach Excel kopieren**.  
  
     Das neue Clustermerkmaldiagramm wird auf einem eigenen Arbeitsblatt hinzugefügt. Sie können es in dasselbe Arbeitsblatt verschieben wie das andere Profil, um den Vergleich zwischen beiden zu vereinfachen. Im nächsten Schritt nehmen Sie den Vergleich vor.  
  
 **Tipps**  
  
-   Kunden im Cluster Über 65 zeichnen sich durch das primäre Merkmal aus, dass sie Ihr Produkt nicht kaufen! Wenn Sie wissen möchten, warum das so ist, können Sie die Cluster durchsuchen und Gruppen vergleichen. Oder Sie erstellen ein verwandtes Modell mithilfe eines Algorithmus, der sich für die Untersuchung von Ursachen und Ergebnissen eignet, z. B. ein Entscheidungsstrukturmodell oder ein Naïve Bayes-Modell.  
  
-   Wenn Sie eine vollständige Liste der Attribute und Wahrscheinlichkeitswerte für diesen Cluster (oder alle Cluster) abrufen möchten, können Sie eine Abfrage erstellen. Beispiele für Abfragen für Clustermodelle, finden Sie unter [Abfragebeispiele Clustering](data-mining/clustering-model-query-examples.md).  
  
 [Zurück nach oben](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterDiscrimination"></a> Clusterunterscheidung  
 Verwenden Sie die **Clusterunterscheidung** Registerkarte ", um Attribute zwischen zwei Clustern oder zwischen einem Cluster und allen anderen Fällen im Dataset zu vergleichen.  
  
 Um die Funktionen dieses Viewers zu markieren, Vergleichen wir ihn auf die Seite-an-Seite-Tabellen in Excel, die Sie auf der Grundlage erstellt die **Clustermerkmale** anzeigen.  
  
##### <a name="explore-cluster-discrimination"></a>Untersuchen der Clusterunterscheidung  
  
1.  Verwenden Sie die Listen **Cluster 1** und **Cluster 2** , um die zu vergleichenden Cluster auszuwählen.  
  
    -   Wählen Sie für Cluster 1 Über 65 aus.  
  
    -   Wählen Sie für Cluster 2 Bike Buyers aus.  
  
     Der Vergleich sollte ähnlich wie in der folgenden Grafik aussehen.  
  
     ![Vergleichen von Clustern in einem Modell](media/dm13-cluster-compareclusters.gif "Vergleichen von Clustern in einem Modell")  
  
     Beachten Sie, dass im Hintergrund der **Clusterunterscheidung** Viewer sendet komplexe Abfragen an die Datamining-Server, um die Attribute zu extrahieren, die wichtigsten beim unterscheiden zwischen den beiden Gruppen, die einfacher zu vergleichen sind, zwei Sätze von Kunden.  
  
2.  Klicken Sie auf eines der **begünstigt...** Spalten auf.  
  
     Der Balken rechts neben der Attribut- und Werteliste zeigt, welchen Funktionen oder Werte das wichtigste Merkmal des ausgewählten Clusters sind.  
  
3.  Vergleichen Sie die Listen jetzt in Excel.  
  
     ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-comparing-profiles-in-excel.gif "abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
     Da die zugrunde liegenden Statistik, die zur Darstellung der Grafik im Viewer verwendet wurde, in Excel in Tabellenform gespeichert wird, können Sie die tatsächlichen Wahrscheinlichkeitswerte filtern, sortieren und anzeigen.  
  
     Zusätzlich zur Verwendung von Excel wird empfohlen, den Cluster-Viewer für Visio auszuprobieren, mit dem Sie nicht nur Datenpunkte anzeigen, sondern die Grafik auch umfassend ändern und verbessern können. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise für das Cluster &#40;Data Mining-Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).  
  
 **Tipps**  
  
 Nachdem Sie einige Einblicke in Gruppen von Kunden erhalten, versuchen Sie es mit der [Datenquellenwerte Szenario &#40;Tabellenanalysetools für Excel&#41; ](what-if-scenario-table-analysis-tools-for-excel.md) oder [Ziel Seek Szenario &#40;Tabellenanalysetools für Excel&#41; ](goal-seek-scenario-table-analysis-tools-for-excel.md) Tools, um Faktoren im Modell zu untersuchen, die geändert werden kann, um das Ergebnis auswirken.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)   
 [Cluster-Assistent &#40;Data Mining-Add-ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  