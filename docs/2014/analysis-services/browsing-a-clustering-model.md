---
title: Durchsuchen eines Clustering-Modells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3682d65ac06d970fed2d5346e9d39684485c5dfe
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527756"
---
# <a name="browsing-a-clustering-model"></a>Durchsuchen eines Clustermodells
  Wenn Sie ein Clustering-Modell mithilfe von **Durchsuchen**öffnen, wird das Modell in einem interaktiven Viewer angezeigt, der dem Clustering-Viewer in ähnelt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Die Viewer unterstützt Sie dabei, die erstellten Cluster zu untersuchen und die Clustermerkmale zu verstehen. Darüber hinaus können Sie einzelne Segmente mit anderen Segmenten oder mit der Grundgesamtheit vergleichen und die Unterschiede untersuchen.  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a>Untersuchen des Modells  
 Das Fenster **Durchsuchen** enthält die folgenden Tools, die Ihnen helfen, Ihr Clustering-Modell zu verstehen und die Attribute der zugrunde liegenden Datengruppen zu untersuchen:  
  
-   [Clusterdiagramm](#BKMK_ClusterDiagram)  
  
-   [Clusterprofile](#BKMK_ClusterProfiles)  
  
-   [Cluster Merkmale](#BKMK_ClusterCharacteristics)  
  
-   [Clusterunterscheidung](#BKMK_ClusterDiscrimination)  
  
 Um mit einem Clustering-Modell zu experimentieren, können Sie die Beispiel Daten auf der Registerkarte Training der Beispiel Daten-Arbeitsmappe verwenden und ein Clustering-Modell mithilfe des [Cluster-Assistenten &#40;Data Mining-Add-Ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) und alle Standardeinstellungen erstellen.  
  
###  <a name="cluster-diagram"></a><a name="BKMK_ClusterDiagram"></a>Cluster Diagramm  
 Auf der Registerkarte **Cluster Diagramm** werden alle Cluster in einem Mining Modell angezeigt. Hier sehen Sie, wie viele verschiedene Gruppierungen im Dataset enthalten sind und wie nah oder weit sie voneinander entfernt liegen.  
  
##### <a name="explore-the-cluster-diagram"></a>Untersuchen des Clusterdiagramms  
  
1.  Klicken Sie auf Cluster 1 im Diagramm.  
  
     Sie können beobachten, wie sich die grauen Linien, die alle Cluster verbinden, ändern. Die Linien, die zum ausgewählten Cluster führen, sind in hellem Blau hervorgehoben.  
  
     ![Clusterdiagramm-Intro](media/dm13-cluster-diagram-intro.gif "Clusterdiagramm-Intro")  
  
     Anhand der Stärke der Linie, die einen Cluster mit einem anderen verbindet, können Sie die Ähnlichkeit der Cluster ableiten. Ist die Schattierung schwach oder ist keine Schattierung vorhanden, sind sich die Cluster kaum ähnlich. Je stärker die Linie ist, desto größer ist die Ähnlichkeit zwischen den beiden Clustern.  
  
2.  Klicken und ziehen Sie den Schieberegler zur linken Seite des Clusterdiagramms, um die Anzahl der Linien anzupassen, die im Viewer angezeigt werden.  
  
     Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Verbindungslinien zwischen Clustern angezeigt. So können Sie verwandte Gruppen leichter fokussieren.  
  
3.  Beachten Sie das Steuerelement **Schattierungs Variable** in der oberen rechten Ecke des Fensters **Cluster Diagramm** .  
  
     Standardmäßig ist es auf **Population**festgelegt. Das bedeutet, dass die Cluster mit der dunkleren Schattierung größere Unterstützung erhalten.  
  
4.  Platzieren Sie den Cursor auf einem beliebigen Cluster.  
  
     Eine QuickInfo wird angezeigt, in der die Auffüllung des Clusters enthalten ist.  
  
5.  Klicken Sie nun auf die Dropdown Liste **Schattierungs Variable** , und wählen Sie die **Alter** -Variable aus. Wie Sie dies tun, wird eine Liste von Werten im Textfeld **Status** angezeigt.  
  
     Die als Eingabe für dieses Modell verwendete Spalte Alter enthält fortlaufende numerische Werte, zu Clusteringzwecken werden die Zahlen vom Algorithmus jedoch immer diskretisiert. Hier können Sie die vom Algorithmus erstellten Behälter oder Gruppen anzeigen, z. b. "sehr niedrig ( \<=27)" and "Very High (> = 63)".  
  
6.  Wählen Sie in der Dropdown Liste **Status** die Option **sehr hoch** aus, und sehen Sie sich an, wie sich das Diagramm  
  
     Indem Sie die Schattierungsvariable ändern, erkennen Sie auf einen Blick, welche Cluster mehr und welche nur wenige Kunden dieser Altersgruppe enthalten.  
  
     ![Ändern des Clusterdiagramms zur Anzeige des Alters](media/dm13-cluster-diagramshadebyage.gif "Ändern des Clusterdiagramms zur Anzeige des Alters")  
  
     Je stärker die Schattierung, desto größer ist der Anteil der Zielattribut- und Werteverteilung des Clusters.  
  
7.  Suchen Sie den Cluster, der als dunkel schattiert ist, wenn die **Schattierungs Variable** auf Age >65 festgelegt ist.  
  
     Zeigen Sie mit der Maus auf den Cluster.  
  
     Der in der QuickInfo angezeigte Wert zeigt jetzt die Grundgesamtheit der Kunden in diesem Cluster an, die älter als 65 sind.  
  
8.  Klicken Sie mit der rechten Maustaste auf den Cluster und wählen Sie **Cluster umbenennen** Geben Sie einen neuen beschreibenden Namen ein, z. b. **über 65**. Der neue Name wird mit dem Modell auf dem Server gespeichert und kann zum Identifizieren des Clusters in den anderen Clusteringsichten verwendet werden.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="cluster-profiles"></a><a name="BKMK_ClusterProfiles"></a>Cluster profile  
 Auf der Registerkarte **Cluster profile** können Sie die Zusammensetzung aller Cluster auf einen Blick vergleichen. Dies ist ein guter Ausgangspunkt, um sich mit dem Modell vertraut zu machen. Diese Ansicht ist auch später hilfreich, wenn Sie einen bestimmten Cluster untersuchen und zu dem Schluss kommen, dass Sie verwandte Cluster suchen müssen.  
  
 **Cluster profile** bieten Ihnen außerdem einen guten Überblick darüber, wie sich die Cluster voneinander unterscheiden. Daher kann es praktisch sein, jedem Cluster mithilfe dieser Ansicht einen aussagekräftigen Namen zu geben.  
  
##### <a name="explore-the-cluster-profiles"></a>Untersuchen der Clusterprofile  
  
1.  Klicken Sie in der Spalte **Zustände** auf die Zelle für die Berufe, um die Liste aller Werte für den Beruf anzuzeigen.  
  
2.  Platzieren Sie jetzt den Cursor in den Clusterprofilen auf Beruf.  
  
     Die QuickInfo zeigt die Verteilung von Berufen in diesem Cluster an.  
  
     ![Anzeigen ausführlicher Werte in QuickInfos oder in der Legende](media/dm13-cluster-profile-age-tooltip.gif "Anzeigen ausführlicher Werte in QuickInfos oder in der Legende")  
  
     Beachten Sie, dass in einigen Clustern (z. b. in der Grafik) die Liste der Berufe nicht fertiggestellt ist und einige Berufe durch die Bezeichnung **ersetzt werden.**  
  
     Dieses Verhalten ist programmbedingt, da es schwierig sein kann, den Unterschied zwischen vielen kleinen Balken im Histogramm auszumachen. Standardmäßig werden nur die wichtigsten Balken beibehalten, und die restlichen Balken werden in einem grauen **anderen** Bucket zusammengefasst.  
  
     Um die Anzahl der in einem Histogramm sichtbaren Balken zu ändern, verwenden Sie die Option **Histogrammbalken**.  
  
3.  Beachten Sie, dass die Spalte " **Age** " von anderen abweicht. Klicken Sie auf die Raute im Diagramm, durch das das Alter dargestellt wird.  
  
     Die Spalte Alter enthielt ursprünglich nur fortlaufende Zahlen. Der Clusteringalgorithmus erfordert diskrete Werte. Folglich wurden die numerischen Werte in der Spalte Alter – basierend auf der Werteverteilung – unter einer eingeschränkten Anzahl von Altersgruppen gruppiert.  
  
4.  Klicken Sie auf eines der Rautendiagramme in einem Clusterprofil.  
  
     Diese Rautendiagramme werden nur angezeigt, wenn die Quelldaten fortlaufende numerische Werte enthalten. Die Rautendiagramme stellen einige aussagekräftige Statistiken bereit, einschließlich der mittleren und Standardabweichung dieses Werts in den einzelnen Clustern:  
  
    -   Die Linie im Rautendiagramm stellt den Wertebereich für das Attribut dar. Die Werte werden auch in der Spalte **Zustände** auf der linken Seite des **Profil** Diagramms angezeigt.  
  
    -   Der Mittelpunkt der Raute orientiert sich am Mittelwert des Knotens.  
  
    -   Die Breite der Raute gibt die Varianz des Attributs in diesem Knoten an. Eine schlankere Raute sagt also aus, dass mithilfe des Knotens eine genauere Vorhersage getroffen werden kann.  
  
5.  Um mehr Platz im Diagramm zu schaffen, klicken Sie mit der rechten Maustaste auf einen Cluster, den Sie nicht sofort anzeigen müssen, und wählen Sie **Spalte ausblenden**aus. Dadurch wird die Spalte nicht aus dem Modell gelöscht, sondern nur vorübergehend reduziert.  
  
     Zum Anzeigen von Clustern, die Sie ausgeblendet haben, können Sie auf den Spalten Rand klicken und ihn ziehen oder den Cluster Namen aus der Liste, **Weitere Cluster**auswählen.  
  
6.  Führen Sie in der Attributliste einen Bildlauf bis Bike Buyer durch, und suchen Sie dann den Cluster, der den höchsten Prozentsatz an Ja-Werten aufweist.  
  
     Klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift des Clusters, den Sie umbenennen möchten, und wählen Sie **Cluster umbenennen** **aus.**  
  
     Der neue Clustername wird in allen Ansichten und auf dem Server beibehalten, bis Sie das Modell erneut verarbeiten.  
  
     ![Umbenennen von Clusters zur einfacheren Verwendung des Diagramms](media/dm13-cluster-rename.gif "Umbenennen von Clusters zur einfacheren Verwendung des Diagramms")  
  
 **Tipps**  
  
-   Klicken Sie auf eine Spaltenüberschrift, um die Attribute nach der Reihenfolge der Wichtigkeit für diesen Cluster zu sortieren.  
  
-   Ziehen Sie die Spalten, um sie im Viewer neu anzuordnen.  
  
-   Klicken Sie im Diagramm Profile auf eine beliebige Zelle, um ausführliche Statistiken in der **Mining Legende**anzuzeigen.  
  
-   Klicken Sie mit der rechten Maustaste auf eine beliebige Zelle, und wählen Sie **Drillthrough Modell Spalten** aus, um die zugrunde liegenden Daten in einem neuen Arbeitsblatt in Excel auszugeben  
  
-   Klicken Sie mit der rechten Maustaste auf die Spaltenüberschrift des Clusters, und wählen Sie **Drillthrough für Strukturdaten** aus, um ausführliche Informationen über die Cluster Mitglieder zu erhalten, die nicht im Modell enthalten waren  
  
     Wenn Sie z. b. die Profilerstellung für Kunden durchlaufen, können Sie die Kontaktinformationen in den zugrunde liegenden Daten (der Mining Struktur) belassen, aber nicht in das Modell einschließen, da dies für die Analyse nicht nützlich ist. Nachdem die Kunden den Clustern zugewiesen wurden, können Sie die detaillierten Daten jedoch mithilfe eines Drillthrough-Vorgangs anzeigen.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="cluster-characteristics"></a><a name="BKMK_ClusterCharacteristics"></a> Clustermerkmale  
 In der Ansicht Clustermerkmale können Sie einen einzelnen Cluster gründlich untersuchen, um herauszufinden, durch welche Attribute diese Datengruppe am stärksten charakterisiert wird.  
  
##### <a name="explore-the-cluster-characteristics"></a>Untersuchen der Clustermerkmale  
  
1.  Wählen Sie den Cluster **über 65** aus der Liste **Cluster** aus.  
  
     Nachdem Sie einen Cluster ausgewählt haben, können Sie die Merkmale dieses Clusters eingehend untersuchen.  
  
     Die im Cluster enthaltenen Attribute werden in den **Variablen** -Spalten und der Status der aufgelisteten Attribute in der **Werte** -Spalte aufgelistet.  
  
     Attribut Zustände werden in der Reihenfolge ihrer Wichtigkeit aufgeführt, und zwar zusammen mit ihrer Wahrscheinlichkeit in diesem Cluster, dargestellt als farbiger Balken in der **Wahrscheinlichkeits** Spalte.  
  
     ![Merkmale eines Clusteringmodells](media/dm13-cluster-characteristics.gif "Merkmale eines Clusteringmodells")  
  
2.  Klicken Sie auf die Spalte **Variablen** , um nach Attribut zu sortieren.  
  
     Indem Sie die Sortierungsvariable ändern, können Sie leichter erkennen, wie Werte für Variablen, z. B. Einkommen oder Autobesitz, in der Gruppe verteilt sind.  
  
3.  Klicken Sie **auf nach Excel kopieren**.  
  
     Der Arbeitsmappe wird ein neues Arbeitsblatt hinzugefügt, das die Merkmale des ausgewählten Clusters enthält.  
  
4.  Wählen Sie nun einen anderen Cluster aus der Liste **Bike Buyers**aus.  
  
5.  Klicken Sie **auf nach Excel kopieren**.  
  
     Das neue Clustermerkmaldiagramm wird auf einem eigenen Arbeitsblatt hinzugefügt. Sie können Sie auf das gleiche Arbeitsblatt wie das andere Profil verschieben, um Sie leichter vergleichen zu können, was Sie im nächsten Schritt tun werden.  
  
 **Tipps**  
  
-   Beachten Sie, dass das primäre Merkmal des Kunden im over 65-Cluster darin besteht, dass Sie Ihr Produkt nicht kaufen! Wenn Sie wissen möchten, warum das so ist, können Sie die Cluster durchsuchen und Gruppen vergleichen. Oder Sie erstellen ein verwandtes Modell mithilfe eines Algorithmus, der sich für die Untersuchung von Ursachen und Ergebnissen eignet, z. B. ein Entscheidungsstrukturmodell oder ein Naïve Bayes-Modell.  
  
-   Wenn Sie eine vollständige Liste der Attribute und Wahrscheinlichkeitswerte für diesen Cluster (oder alle Cluster) abrufen möchten, können Sie eine Abfrage erstellen. Beispiele für Abfragen für Clustering-Modelle finden Sie unter [Beispiele für Clustering-Modell Abfragen](data-mining/clustering-model-query-examples.md).  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="cluster-discrimination"></a><a name="BKMK_ClusterDiscrimination"></a>Cluster Unterscheidung  
 Sie können die Registerkarte **Cluster Unterscheidung** verwenden, um Attribute zwischen zwei Clustern oder zwischen einem Cluster und allen anderen Fällen im DataSet zu vergleichen.  
  
 Um die Features dieses Viewers hervorzuheben, vergleichen wir ihn mit den parallelen Tabellen in Excel, die Sie basierend auf der Ansicht **Cluster Merkmale** erstellt haben.  
  
##### <a name="explore-cluster-discrimination"></a>Untersuchen der Clusterunterscheidung  
  
1.  Verwenden Sie die Listen **Cluster 1** und **Cluster 2** , um die zu vergleichenden Cluster auszuwählen.  
  
    -   Wählen Sie für Cluster 1 Über 65 aus.  
  
    -   Wählen Sie für Cluster 2 Bike Buyers aus.  
  
     Der Vergleich sollte ähnlich wie in der folgenden Grafik aussehen.  
  
     ![Vergleichen von Clustern in einem Modell](media/dm13-cluster-compareclusters.gif "Vergleichen von Clustern in einem Modell")  
  
     Beachten Sie, dass der **Cluster** Unterscheidungs-Viewer im Bereich komplexe Abfragen an den Data Mining-Server sendet, um die Attribute zu extrahieren, die bei der Unterscheidung zwischen den beiden Gruppen am wichtigsten sind, sodass zwei Kunden Sätze einfacher verglichen werden können.  
  
2.  Klicken Sie auf eine der Spalten **begünstigt...** .  
  
     Der Balken rechts neben der Attribut- und Werteliste zeigt, welchen Funktionen oder Werte das wichtigste Merkmal des ausgewählten Clusters sind.  
  
3.  Vergleichen Sie die Listen jetzt in Excel.  
  
     ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-comparing-profiles-in-excel.gif "Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
     Da die zugrunde liegenden Statistik, die zur Darstellung der Grafik im Viewer verwendet wurde, in Excel in Tabellenform gespeichert wird, können Sie die tatsächlichen Wahrscheinlichkeitswerte filtern, sortieren und anzeigen.  
  
     Zusätzlich zur Verwendung von Excel wird empfohlen, den Cluster-Viewer für Visio auszuprobieren, mit dem Sie nicht nur Datenpunkte anzeigen, sondern die Grafik auch umfassend ändern und verbessern können. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise für das [Cluster Diagramm &#40;Data Mining-Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).  
  
 **Tipps**  
  
 Nachdem Sie einige Einblicke in Kundengruppen erhalten haben, verwenden Sie das [Was-wäre-wenn-Szenario &#40;Tabellenanalyse Tools für Excel&#41;](what-if-scenario-table-analysis-tools-for-excel.md) oder das [zielsuchszenario &#40;Tabellenanalyse Tools für Excel-&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md) Tools, um Faktoren im Modell zu untersuchen, die möglicherweise geändert werden, um das Ergebnis zu beeinflussen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)   
 [Cluster-Assistent &#40;Data Mining-Add-Ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
