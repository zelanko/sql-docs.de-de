---
title: Durchsuchen eines Clustermodells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining models, viewing
- clustering [data mining]
- mining model, clustering
ms.assetid: 7f3f0949-d791-403a-88e2-54cb1a803dae
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a0fd00201f782bba8b06ddde8753a86aeb89046
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52535726"
---
# <a name="browsing-a-clustering-model"></a>Durchsuchen eines Clustermodells
  Wenn Sie öffnen ein Clusteringmodell mit **Durchsuchen**, das Modell wird angezeigt, in einem interaktiven Viewer, der clustering-Viewer in etwa wie [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Die Viewer unterstützt Sie dabei, die erstellten Cluster zu untersuchen und die Clustermerkmale zu verstehen. Darüber hinaus können Sie einzelne Segmente mit anderen Segmenten oder mit der Grundgesamtheit vergleichen und die Unterschiede untersuchen.  
  
##  <a name="BKMK_Tabs"></a> Durchsuchen des Modells  
 Die **Durchsuchen** Fenster enthält die folgenden Tools, mit denen Sie das Clusteringmodell zu verstehen und die Attribute des zugrunde liegenden Datengruppen zu untersuchen:  
  
-   [Clusterdiagramm](#BKMK_ClusterDiagram)  
  
-   [Clusterprofile](#BKMK_ClusterProfiles)  
  
-   [Clustermerkmale](#BKMK_ClusterCharacteristics)  
  
-   [Clusterunterscheidung](#BKMK_ClusterDiscrimination)  
  
 Mit einem Clusteringmodell experimentieren möchten, können Sie die Beispieldaten auf der Registerkarte Training der Beispieldaten-Arbeitsmappe verwenden und erstellen Sie ein Clusteringmodell mit [Clustererstellungs-Assistenten &#40;Data Mining-Add-ins für Excel&#41; ](cluster-wizard-data-mining-add-ins-for-excel.md) und allen Standardeinstellungen .  
  
###  <a name="BKMK_ClusterDiagram"></a> Clusterdiagramm  
 Die **Clusterdiagramm** Registerkarte zeigt alle, die in einem Miningmodell enthaltenen Cluster an. Hier sehen Sie, wie viele verschiedene Gruppierungen im Dataset enthalten sind und wie nah oder weit sie voneinander entfernt liegen.  
  
##### <a name="explore-the-cluster-diagram"></a>Untersuchen des Clusterdiagramms  
  
1.  Klicken Sie auf Cluster 1 im Diagramm.  
  
     Sie können beobachten, wie sich die grauen Linien, die alle Cluster verbinden, ändern. Die Linien, die zum ausgewählten Cluster führen, sind in hellem Blau hervorgehoben.  
  
     ![Clusterdiagramm-Intro](media/dm13-cluster-diagram-intro.gif "Clusterdiagramm-Intro")  
  
     Anhand der Stärke der Linie, die einen Cluster mit einem anderen verbindet, können Sie die Ähnlichkeit der Cluster ableiten. Ist die Schattierung schwach oder ist keine Schattierung vorhanden, sind sich die Cluster kaum ähnlich. Je stärker die Linie ist, desto größer ist die Ähnlichkeit zwischen den beiden Clustern.  
  
2.  Klicken und ziehen Sie den Schieberegler zur linken Seite des Clusterdiagramms, um die Anzahl der Linien anzupassen, die im Viewer angezeigt werden.  
  
     Wenn Sie den Schieberegler nach unten ziehen, werden nur die stärksten Verbindungslinien zwischen Clustern angezeigt. So können Sie verwandte Gruppen leichter fokussieren.  
  
3.  Beachten Sie, dass die **Schattierungsvariable** -Steuerelement in der oberen rechten Ecke des der **Clusterdiagramm** Fenster.  
  
     Standardmäßig ist er festgelegt **Auffüllung**. Das bedeutet, dass die Cluster mit der dunkleren Schattierung größere Unterstützung erhalten.  
  
4.  Platzieren Sie den Cursor auf einem beliebigen Cluster.  
  
     Eine QuickInfo wird angezeigt, in der die Auffüllung des Clusters enthalten ist.  
  
5.  Klicken Sie nun die **Schattierungsvariable** Dropdownliste aus, und wählen Sie die **Alter** Variable. Wie Sie dies tun, wird eine Liste von Werten der **Zustand** Textfeld.  
  
     Die als Eingabe für dieses Modell verwendete Spalte Alter enthält fortlaufende numerische Werte, zu Clusteringzwecken werden die Zahlen vom Algorithmus jedoch immer diskretisiert. Hier sehen Sie den Container oder Gruppen, die der Algorithmus erstellt werden, z. B. "sehr niedrig (\<= 27)" und "sehr hoch (> = 63)".  
  
6.  Aus der **Zustand** Dropdown-Listen, die Option **sehr hohe** und festzustellen, wie das Diagramm ändert.  
  
     Indem Sie die Schattierungsvariable ändern, erkennen Sie auf einen Blick, welche Cluster mehr und welche nur wenige Kunden dieser Altersgruppe enthalten.  
  
     ![Ändern des clusterdiagramms zur Anzeige des Alters](media/dm13-cluster-diagramshadebyage.gif "Ändern des clusterdiagramms zur Anzeige des Alters")  
  
     Je stärker die Schattierung, desto größer ist der Anteil der Zielattribut- und Werteverteilung des Clusters.  
  
7.  Suchen Sie den Cluster, der schattierte Bereich ist dunkelsten bei der **Schattierungsvariable** nastaven NA hodnotu Alter > 65.  
  
     Zeigen Sie mit der Maus auf den Cluster.  
  
     Der in der QuickInfo angezeigte Wert zeigt jetzt die Grundgesamtheit der Kunden in diesem Cluster an, die älter als 65 sind.  
  
8.  Mit der rechten Maustaste in des Clusters, und wählen Sie **Cluster umbenennen**. Geben Sie einen neuen Namen, die informative, z. B. **über 65**. Der neue Name wird mit dem Modell auf dem Server gespeichert und kann zum Identifizieren des Clusters in den anderen Clusteringsichten verwendet werden.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterProfiles"></a> Clusterprofile  
 Die **Clusterprofile** Registerkarte können Sie die Zusammensetzung aller Cluster, auf einen Blick zu vergleichen. Dies ist ein guter Ausgangspunkt, um sich mit dem Modell vertraut zu machen. Diese Ansicht ist auch später hilfreich, wenn Sie einen bestimmten Cluster untersuchen und zu dem Schluss kommen, dass Sie verwandte Cluster suchen müssen.  
  
 **Clusterprofile** erhalten Sie auch einen guten Überblick darüber, wie der Cluster voneinander unterscheiden. Daher kann es praktisch sein, jedem Cluster mithilfe dieser Ansicht einen aussagekräftigen Namen zu geben.  
  
##### <a name="explore-the-cluster-profiles"></a>Untersuchen der Clusterprofile  
  
1.  Klicken Sie auf die Zelle für Berufsbezeichnungen, in der **Zustände** Spalte, um die Liste aller Werte für "Occupation" anzuzeigen.  
  
2.  Platzieren Sie jetzt den Cursor in den Clusterprofilen auf Beruf.  
  
     Die QuickInfo zeigt die Verteilung von Berufen in diesem Cluster an.  
  
     ![Anzeigen von ausführlicher Werte in QuickInfos oder in der Legende](media/dm13-cluster-profile-age-tooltip.gif "ausführliche Werte in QuickInfos oder in Legende anzeigen")  
  
     Beachten Sie, dass in einigen (z. B. die in der Abbildung), die Liste der Berufe Clustern ist nicht vollständig, und einige Berufe ersetzt werden, mit der Bezeichnung **andere**.  
  
     Dieses Verhalten ist programmbedingt, da es schwierig sein kann, den Unterschied zwischen vielen kleinen Balken im Histogramm auszumachen. Standardmäßig werden nur die wichtigsten Balken von größter Wichtigkeit beibehalten und die restlichen Balken werden in einem grau gruppiert **andere** Bucket.  
  
     Um die Anzahl der Balken zu ändern, die in einem beliebigen Histogramm angezeigt werden, verwenden Sie die Option **Histogrammbalken**.  
  
3.  Beachten Sie, dass die **Alter** -Kolumne befasst sich nicht in die Gruppe. Klicken Sie auf die Raute im Diagramm, durch das das Alter dargestellt wird.  
  
     Die Spalte Alter enthielt ursprünglich nur fortlaufende Zahlen. Der Clusteringalgorithmus erfordert diskrete Werte. Folglich wurden die numerischen Werte in der Spalte Alter – basierend auf der Werteverteilung – unter einer eingeschränkten Anzahl von Altersgruppen gruppiert.  
  
4.  Klicken Sie auf eines der Rautendiagramme in einem Clusterprofil.  
  
     Diese Rautendiagramme werden nur angezeigt, wenn die Quelldaten fortlaufende numerische Werte enthalten. Die Rautendiagramme stellen einige aussagekräftige Statistiken bereit, einschließlich der mittleren und Standardabweichung dieses Werts in den einzelnen Clustern:  
  
    -   Die Linie im Rautendiagramm stellt den Wertebereich für das Attribut dar. Die Werte werden auch angezeigt, der **Zustände** Spalte am linken Rand der **Profile** Diagramm.  
  
    -   Der Mittelpunkt der Raute orientiert sich am Mittelwert des Knotens.  
  
    -   Die Breite der Raute gibt die Varianz des Attributs in diesem Knoten an. Eine schlankere Raute sagt also aus, dass mithilfe des Knotens eine genauere Vorhersage getroffen werden kann.  
  
5.  Um mehr Platz im Diagramm schaffen, Maustaste einen Cluster, die Sie nicht benötigen, um sofort anzuzeigen, und wählen **Spalte ausblenden**. Dies nicht aus dem Modell gelöscht, reduzieren die Spalte nur vorübergehend.  
  
     Um Cluster anzuzeigen, die Sie ausgeblendet haben, können Sie auf, und ziehen Sie den Spaltenrand oder wählen Sie den Namen des Clusters aus der Liste, **mehr Cluster**.  
  
6.  Führen Sie in der Attributliste einen Bildlauf bis Bike Buyer durch, und suchen Sie dann den Cluster, der den höchsten Prozentsatz an Ja-Werten aufweist.  
  
     Mit der rechten Maustaste in der Spaltenüberschrift für den Cluster, die Sie umbenennen möchten, wählen Sie **Cluster umbenennen**, und geben **Bike Buyers**.  
  
     Der neue Clustername wird in allen Ansichten und auf dem Server beibehalten, bis Sie das Modell erneut verarbeiten.  
  
     ![Umbenennen von Clusters zur Diagramm leichter zu verwenden ist](media/dm13-cluster-rename.gif "Umbenennen von Clusters zum Diagramm leichter zu verwenden ist")  
  
 **Tipps**  
  
-   Klicken Sie auf eine Spaltenüberschrift, um die Attribute nach der Reihenfolge der Wichtigkeit für diesen Cluster zu sortieren.  
  
-   Ziehen Sie die Spalten, um sie im Viewer neu anzuordnen.  
  
-   Klicken Sie auf eine beliebige Zelle im profildiagramm, um detaillierte Statistikdaten in anzeigen. dem **Mininglegende**.  
  
-   Mit der rechten Maustaste in eine beliebige Zelle, und wählen Sie **Drillthrough für modellspalten** zur Ausgabe von der zugrunde liegenden Daten in einem neuen Arbeitsblatt in Excel.  
  
-   Mit der rechten Maustaste in der Clusterspalte Spaltenüberschrift, und wählen **Drillthroughs zu Strukturdaten** um ausführliche Informationen zu Clusterelementen abzurufen, die im Modell enthalten waren.  
  
     Z. B. Wenn Sie Kundenprofile erstellen, Sie die Kontaktinformationen in der zugrunde liegenden Daten (der Miningstruktur) belassen, jedoch nicht im Modell enthalten, da er nicht für die Analyse hilfreich ist. Nachdem die Kunden den Clustern zugewiesen wurden, können Sie die detaillierten Daten jedoch mithilfe eines Drillthrough-Vorgangs anzeigen.  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterCharacteristics"></a> Clustermerkmale  
 In der Ansicht Clustermerkmale können Sie einen einzelnen Cluster gründlich untersuchen, um herauszufinden, durch welche Attribute diese Datengruppe am stärksten charakterisiert wird.  
  
##### <a name="explore-the-cluster-characteristics"></a>Untersuchen der Clustermerkmale  
  
1.  Wählen Sie die **über 65** -cluster über die **Cluster** Liste.  
  
     Nachdem Sie einen Cluster ausgewählt haben, können Sie die Merkmale dieses Clusters eingehend untersuchen.  
  
     Die im Cluster enthaltenen Attribute werden in den **Variablen** -Spalten und der Status der aufgelisteten Attribute in der **Werte** -Spalte aufgelistet.  
  
     Attributstatus finden Sie in der Reihenfolge ihrer Wichtigkeit, zusammen mit ihrer Wahrscheinlichkeit in diesem Cluster, dargestellt als eine farbige Leiste in der **Wahrscheinlichkeit** Spalte.  
  
     ![Merkmale eines Clusteringmodells](media/dm13-cluster-characteristics.gif "Merkmale eines Clusteringmodells")  
  
2.  Klicken Sie auf die **Variablen** Spalte, um nach Attribut zu sortieren.  
  
     Indem Sie die Sortierungsvariable ändern, können Sie leichter erkennen, wie Werte für Variablen, z. B. Einkommen oder Autobesitz, in der Gruppe verteilt sind.  
  
3.  Klicken Sie auf **nach Excel kopieren**.  
  
     Der Arbeitsmappe wird ein neues Arbeitsblatt hinzugefügt, das die Merkmale des ausgewählten Clusters enthält.  
  
4.  Wählen Sie einen anderen Cluster jetzt in der Liste **Bike Buyers**.  
  
5.  Klicken Sie auf **nach Excel kopieren**.  
  
     Das neue Clustermerkmaldiagramm wird auf einem eigenen Arbeitsblatt hinzugefügt. Sie können es auf dem Arbeitsblatt mit dem anderen Profil zu vereinfachen, sie zu vergleichen, was im nächsten Schritt fortfahren.  
  
 **Tipps**  
  
-   Beachten Sie, dass das primäre Merkmal des Kunden in den Cluster über 65 ist, dass sie Ihr Produkt nicht kaufen! Wenn Sie wissen möchten, warum das so ist, können Sie die Cluster durchsuchen und Gruppen vergleichen. Oder Sie erstellen ein verwandtes Modell mithilfe eines Algorithmus, der sich für die Untersuchung von Ursachen und Ergebnissen eignet, z. B. ein Entscheidungsstrukturmodell oder ein Naïve Bayes-Modell.  
  
-   Wenn Sie eine vollständige Liste der Attribute und Wahrscheinlichkeitswerte für diesen Cluster (oder alle Cluster) abrufen möchten, können Sie eine Abfrage erstellen. Beispiele für Abfragen für Clustermodelle, finden Sie unter [Clusteringmodellabfragen](data-mining/clustering-model-query-examples.md).  
  
 [Zurück zum Anfang](#BKMK_Tabs)  
  
###  <a name="BKMK_ClusterDiscrimination"></a> Clusterunterscheidung  
 Sie verwenden die **Clusterunterscheidung** Tab, um Attribute zwischen zwei Clustern oder zwischen einem Cluster und allen anderen Fällen im Dataset zu vergleichen.  
  
 Um die Funktionen dieses Viewers zu markieren, Vergleichen wir ihn auf die Seite-an-Seite-Tabellen in Excel, die Sie auf der Grundlage erstellt die **Clustermerkmale** anzeigen.  
  
##### <a name="explore-cluster-discrimination"></a>Untersuchen der Clusterunterscheidung  
  
1.  Verwenden Sie die Listen **Cluster 1** und **Cluster 2** , um die zu vergleichenden Cluster auszuwählen.  
  
    -   Wählen Sie für Cluster 1 Über 65 aus.  
  
    -   Wählen Sie für Cluster 2 Bike Buyers aus.  
  
     Der Vergleich sollte ähnlich wie in der folgenden Grafik aussehen.  
  
     ![Vergleichen von Clustern in einem Modell](media/dm13-cluster-compareclusters.gif "Vergleichen von Clustern in einem Modell")  
  
     Beachten Sie, dass im Hintergrund die **Clusterunterscheidung** Viewer sendet komplexe Abfragen an die Datamining-Server, um die Attribute zu extrahieren, die wichtigsten beim unterscheiden zwischen den beiden Gruppen, erleichtert Ihnen die zu vergleichende sind, zwei Gruppen von Kunden.  
  
2.  Klicken Sie auf eines der **begünstigt...**  Spalten.  
  
     Der Balken rechts neben der Attribut- und Werteliste zeigt, welchen Funktionen oder Werte das wichtigste Merkmal des ausgewählten Clusters sind.  
  
3.  Vergleichen Sie die Listen jetzt in Excel.  
  
     ![Abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell](media/dm13-comparing-profiles-in-excel.gif "abhängigkeitsnetzwerkdiagramm für ein Zuordnungsmodell")  
  
     Da die zugrunde liegenden Statistik, die zur Darstellung der Grafik im Viewer verwendet wurde, in Excel in Tabellenform gespeichert wird, können Sie die tatsächlichen Wahrscheinlichkeitswerte filtern, sortieren und anzeigen.  
  
     Zusätzlich zur Verwendung von Excel wird empfohlen, den Cluster-Viewer für Visio auszuprobieren, mit dem Sie nicht nur Datenpunkte anzeigen, sondern die Grafik auch umfassend ändern und verbessern können. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise für das Cluster &#40;Data Mining-Add-ins&#41;](cluster-diagram-walkthrough-data-mining-add-ins.md).  
  
 **Tipps**  
  
 Nachdem Sie einige Einblicke in Gruppen von Kunden erhalten, versuchen Sie es mit der [Datenquellenwerte Szenario &#40;Tabellenanalysetools für Excel&#41; ](what-if-scenario-table-analysis-tools-for-excel.md) oder [Ziel suchen Szenario &#40;Tabellenanalysetools für Excel&#41; ](goal-seek-scenario-table-analysis-tools-for-excel.md) Tools, um Faktoren in Bezug auf das Modell zu untersuchen, die geändert werden kann, um das Ergebnis auswirken.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)   
 [Cluster-Assistent &#40;Data Mining-Add-ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
  
