---
title: Exemplarische Vorgehensweise zum Cluster Diagramm (Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, cluster
- diagram, cluster
- shapes, data mining
- shapes, cluster
- data mining layout toolbar
ms.assetid: 761bef6a-37d4-4b19-944e-f2aadc75a242
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc2df250b0728934f258c8217d29adfb91e66ff5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087911"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a>Exemplarische Vorgehensweise für das Clusterdiagramm (Data Mining-Add-Ins)
  Nachdem Sie ein Clusteringmodell erstellt haben, können Sie es mithilfe der Form **Cluster** in Visio importieren und das Layout anschließend weiter anpassen und verbessern. Die **Data Mining-Shapes für Visio** enthalten die folgenden benutzerdefinierten Steuerelemente zum Arbeiten mit Data Mining Diagrammen:  
  
-   Rendern von Steuerelementen für das Clusterdiagramm  
  
     Diese Optionen sind Teil des **Cluster-Assistenten** , der gestartet wird, wenn Sie eine Form im Visio-Arbeitsbereich ablegen.  
  
-   Symbolleiste für **Data Mining-Layout**  
  
     Diese Optionen werden dem Visio-Arbeitsbereich hinzugefügt, um Ihnen die Interaktion mit dem Data Mining-Shape zu erleichtern. Die Optionen unterscheiden sich je nach Typ des verwendeten Data Mining-Modells.  
  
## <a name="build-a-cluster-diagram"></a>Erstellen eines Clusterdiagramms  
 Durch diese exemplarische Vorgehensweise wird veranschaulicht, wie Sie ein Clusteringdiagramm in Visio erstellen und anpassen.  
  
 Zum Ausführen der Schritte sollten Sie bereits über ein Clusteringmodell verfügen. Wenn Sie nicht über ein Modell verfügen, verwenden Sie den Assistenten [&#40;Data Mining-Add-Ins für Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md) , und erstellen Sie ein Modell mit dem Trainings Dataset in der Beispiel Arbeitsmappe, wobei alle Standardwerte verwendet werden.  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a>Verwenden des Assistenten für das Cluster-Shape in Visio  
  
1.  Wenn **Microsoft Data Mining-Formen** in der Liste **Shapes** nicht angezeigt werden, klicken Sie auf **Weitere Formen**, wählen Sie **Schablone öffnen**aus, und öffnen Sie die Vorlage aus dem Standard Installationsverzeichnis.  
  
     \<Laufwerk>: \Programme\Microsoft SQL Server 2012 DM Add-ins  
  
2.  Ziehen Sie die Form " **Cluster** " auf die Seite.  
  
3.  Klicken Sie auf der Willkommensseite des Assistenten für das **Cluster-Shape in Visio**auf **weiter**.  
  
4.  Wählen Sie auf der Seite **Datenquelle auswählen** des **Cluster-Assistenten**eine Verbindung mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Server aus, der die Data Mining Modelle enthält, die Sie visualisieren möchten.  
  
5.  Wählen Sie ein geeignetes Mining Modell aus, und klicken Sie auf **weiter**.  
  
     Um sicherzustellen, dass Sie ein Clusteringmodell auswählen, überprüfen Sie die Beschreibung im Bereich " **Eigenschaften** ".  
  
6.  Wenn die Verbindung erfolgreich hergestellt wurde, legen Sie auf der Seite **Optionen für Cluster Diagramm**fest, welche Art von Cluster Diagramm in die Visio-Präsentation aufgenommen werden soll:  
  
     **Nur Cluster-Shapes anzeigen**  
     Mit dieser Option erstellen Sie ein einfaches Clusterdiagramm, in dem jeder Cluster durch ein Rechteck oder ein anderes Shape Ihrer Wahl dargestellt wird.  
  
     **Cluster mit Merkmaldiagramm anzeigen**  
     Mit dieser Option erstellen Sie das gleiche Diagramm wie oben. In diesem Fall enthalten die Shapes jedoch Histogramme, die die Merkmale des Clusters beschreiben.  
  
     ![Beispiel des Clustermerkmal-Diagramms in Visio](media/dm13-visio-cluster-samplecharshape.gif "Beispiel des Clustermerkmal-Diagramms in Visio")  
  
     **Cluster mit Unterscheidungsdiagramm anzeigen**  
     Mit dieser Option erstellen Sie ebenfalls ein Clusterdiagramm. In diesem Fall werden jedoch die Merkmale des aktuellen Clusters aufgeführt, die sich am stärksten von den anderen Clustern unterscheiden.  
  
     Sie können auch zu einem anderen Diagrammtyp wechseln, nachdem das Diagramm vom Assistenten erstellt wurde. Klicken Sie dazu mit der rechten Maustaste auf einen Cluster, und wählen Sie einen neuen Diagrammtyp aus. Wählen Sie vorerst die Option **Cluster mit Merkmalen anzeigen**aus.  
  
7.  Belassen Sie die Option **Anzahl von Zeilen im Diagramm**5.  
  
     Mit dieser Option wird die Anzahl der Cluster im Modell nicht geändert. die Anzahl der Attribute, die als Funktionen der einzelnen Cluster angezeigt werden können, wird einfach eingeschränkt.  
  
     Die Option fungiert jedoch als Filter für die Diagramm Daten, sodass Sie die Anzahl der Elemente später nicht mehr erhöhen können.  
  
8.  Klicken Sie auf **Erweitert**.  
  
     Im Dialogfeld **Cluster Optionen** passen Sie die visuelle Darstellung von Formen an, die im Diagramm verwendet werden. Sie können die im Diagramm verwendeten Farben und das für die Cluster verwendete Shape ändern.  
  
     Das Steuerelement für **Schattierungs Variablen** funktioniert nicht in Office 2013.  
  
     ![Klicken auf "Erweitert", um Shape-Farben auszuwählen](media/dm13-visio-clusteroptions-advanced.gif "Klicken auf "Erweitert", um Shape-Farben auszuwählen")  
  
     **Tipp:** Einige Farben können später mithilfe von Visio-Designs und Steuerelementen zum Bearbeiten von Formen geändert werden. Ein Teil dieser Farbauswahl wird jedoch von Visio-Designs überschrieben. Aus diesem Grund wird empfohlen, mit den Standardfarben zu beginnen und die Änderungen schrittweise vorzunehmen.  
  
9. Klicken Sie auf **Fertig** stellen, um das Diagramm zu erstellen.  
  
     Der Assistent ruft Informationen aus dem Data Mining-Modell ab, rendert die Shapes und füllt jeden Cluster mit Attributen und Werten auf.  
  
     ![ein Abhängigkeitsnetzwerk](media/dm13-visiodepnet-defaultgraph.gif "ein Abhängigkeitsnetzwerk")  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Durchsuchen und Ändern des fertigen Diagramms  
 Nachdem das Diagramm vollständig erstellt wurde, können Sie dessen Erscheinungsbild, wie im folgenden Beispiel beschrieben, mithilfe von Visio-Steuerelementen anpassen.  
  
 ![Mithilfe von Visio angepasstes Clusterdiagramm](media/dm13-visio-clustercomplete1.gif "Mithilfe von Visio angepasstes Clusterdiagramm")  
  
 Alle grundlegenden Cluster-Shapes werden vom Assistenten generiert. Verwenden Sie die folgenden Tools zum Aktualisieren und Personalisieren des Diagramms:  
  
1.  Ziehen Sie den Schieberegler in das Steuerelement **Cluster Optionen** , um schwächere Beziehungen herauszufiltern und das Diagramm zu vereinfachen.  
  
2.  Verwenden Sie die Option für die Visio **-neulayoutseite** , um mit unterschiedlichen Cluster Layouts zu experimentieren.  
  
3.  Verwenden Sie die Option **Connectors** auf der Registerkarte **Entwurf** , um den connectorstil so zu ändern, dass Zeilen vom überschreiten von Clustern bleiben.  
  
4.  Klicken Sie auf das Menüband **Add-ins** , und zeigen Sie dann eine der benutzerdefinierten Symbolleisten an, die für die Arbeit mit Data Mining Diagrammen verwendet werden:  
  
     **Layout**  
     Optimiert die Anordnung der Cluster, sodass sie auf die aktuelle Seite passen.  
  
     **Größe der Seite ändern**  
     Dieses Steuerelement war für frühere HTML-Versionen vorgesehen. Verwenden Sie stattdessen Steuerungselemente zur Anpassung der Visio-Seitengröße.  
  
     **Beschreibung**  
     Wenn ein Cluster ausgewählt ist, klicken Sie auf diese Option, um Details zum Cluster anzuzeigen.  
  
     ![Klicken auf "Beschreibung", um Details zum Cluster abzurufen](media/dm13-visio-cluster-description-control.gif "Klicken auf "Beschreibung", um Details zum Cluster abzurufen")  
  
     **Kantenstärke**  
     Zeigt Vertrauensergebnisse für die Linien an, die die Cluster verbinden.  
  
     Wenn Sie eine spezielle Formatierung anwenden, die von der standardmäßig generierten Formatierung des Assistenten abweicht (einschließlich einiger Hintergründe), sind diese Zahlen u. U. nicht sichtbar.  
  
     **Slider**  
     Filtert die Linien zwischen den Clustern. Wenn Sie den Schieberegler verschieben, werden alle Zuordnungen bis auf die wichtigsten entfernt.  
  
     **Schattierung**  
     Dieses Steuerelement funktioniert nicht in Office 2013.  
  
5.  Verwenden Sie das Steuerelement **schwenken und Zoomen** im **Aufgaben** Bereich des Menübands **Ansicht Ansicht** , um sich auf eine Gruppe von Clustern zu konzentrieren und das Diagramm zu verschieben.  
  
6.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Cluster, um die Optionen für das Cluster-Shape anzuzeigen:  
  
    -   Ändern Sie das Diagrammformat.  
  
    -   Flügen Sie ein Clustermerkmaldiagramm hinzu.  
  
    -   Fügen Sie ein Clusterunterscheidungsdiagramm hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei Visio Data Mining-Diagrammen &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
