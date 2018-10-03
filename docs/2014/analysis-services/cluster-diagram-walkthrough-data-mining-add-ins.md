---
title: Exemplarische Vorgehensweise (Data Mining-Add-ins)-Cluster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
ms.openlocfilehash: b617305a8766ff94a699a054ac394be406dc7873
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057090"
---
# <a name="cluster-diagram-walkthrough-data-mining-add-ins"></a>Exemplarische Vorgehensweise für das Clusterdiagramm (Data Mining-Add-Ins)
  Nachdem Sie ein clustering-Modell erstellt haben, können Sie es importieren, in Visio mithilfe der **Cluster** strukturieren und anpassen und erweitern das Layout anschließend weiter. Die **Data Mining-Shapes für Visio** enthalten die folgenden benutzerdefinierten Steuerelemente zum Arbeiten mit Datamining-Diagramme:  
  
-   Rendern von Steuerelementen für das Clusterdiagramm  
  
     Diese Optionen sind Teil der **Clustererstellungs-Assistenten** gestartet wird, wenn Sie eine Form auf dem Visio-Arbeitsbereich ablegen.  
  
-   **Data Mining Layout** Symbolleiste  
  
     Diese Optionen werden dem Visio-Arbeitsbereich hinzugefügt, um Ihnen die Interaktion mit dem Data Mining-Shape zu erleichtern. Die Optionen unterscheiden sich je nach Typ des verwendeten Data Mining-Modells.  
  
## <a name="build-a-cluster-diagram"></a>Erstellen eines Clusterdiagramms  
 Durch diese exemplarische Vorgehensweise wird veranschaulicht, wie Sie ein Clusteringdiagramm in Visio erstellen und anpassen.  
  
 Zum Ausführen der Schritte sollten Sie bereits über ein Clusteringmodell verfügen. Wenn Sie nicht über ein Modell verfügen, verwenden Sie die [Clustererstellungs-Assistenten &#40;Data Mining-Add-ins für Excel&#41; ](cluster-wizard-data-mining-add-ins-for-excel.md) Assistenten, und erstellen Sie ein Modell mithilfe des trainingsdatasets in der Beispielarbeitsmappe mit allen Standardeinstellungen.  
  
#### <a name="use-the-cluster-visio-shape-wizard"></a>Verwenden Sie den Cluster-Shape in Visio-Assistenten  
  
1.  Wenn Sie nicht angezeigt werden **Microsoft Data Mining-Shapes** in der **Formen** auf **weitere Shapes**Option **Schablone öffnen**, und öffnen Sie die die Vorlage aus den standardmäßigen Installationsspeicherort.  
  
     \<Laufwerk >: \Programme\Microsoft SQL Server 2012 DM-Add-Ins  
  
2.  Ziehen Sie die **Cluster** Shape auf der Seite.  
  
3.  Klicken Sie auf der Seite Willkommen des der **Assistenten Shape in Visio Cluster**, klicken Sie auf **Weiter**.  
  
4.  Auf der **Vybrat Zdroj DAT** auf der Seite die **Clustererstellungs-Assistenten**, wählen Sie eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Server, der die Datamining-Modelle enthält, die Sie visualisieren möchten.  
  
5.  Wählen Sie ein geeignetes Miningmodell aus, und klicken Sie auf **Weiter**.  
  
     Um sicherzustellen, dass Sie ein Clusteringmodell auswählen, überprüfen Sie in der Beschreibung in der **Eigenschaften** Bereich.  
  
6.  Wenn die Verbindung erfolgreich ist, auf der Seite **Optionen für Clusterdiagramm**, welche Art von Clusterdiagramm in die Visio-Präsentation einschließen möchten:  
  
     **Nur Cluster-Shapes anzeigen**  
     Mit dieser Option erstellen Sie ein einfaches Clusterdiagramm, in dem jeder Cluster durch ein Rechteck oder ein anderes Shape Ihrer Wahl dargestellt wird.  
  
     **Cluster mit merkmaldiagramm anzeigen**  
     Mit dieser Option erstellen Sie das gleiche Diagramm wie oben. In diesem Fall enthalten die Shapes jedoch Histogramme, die die Merkmale des Clusters beschreiben.  
  
     ![Beispiel des clustermerkmal-Diagramms in Visio](media/dm13-visio-cluster-samplecharshape.gif "Beispiel des clustermerkmal-Diagramms in Visio")  
  
     **Cluster mit unterscheidungsdiagramm anzeigen**  
     Mit dieser Option erstellen Sie ebenfalls ein Clusterdiagramm. In diesem Fall werden jedoch die Merkmale des aktuellen Clusters aufgeführt, die sich am stärksten von den anderen Clustern unterscheiden.  
  
     Sie können auch zu einem anderen Diagrammtyp wechseln, nachdem das Diagramm vom Assistenten erstellt wurde. Klicken Sie dazu mit der rechten Maustaste auf einen Cluster, und wählen Sie einen neuen Diagrammtyp aus. Wählen Sie jetzt die Option **Cluster mit merkmaldiagramm anzeigen**.  
  
7.  Lassen Sie diese Option, **Anzahl der Zeilen im Diagramm**, 5.  
  
     Durch diese Option wird die Anzahl der Cluster im Modell nicht geändert, sondern lediglich die Anzahl der Attribute eingeschränkt, die als Funktionen der einzelnen Cluster angezeigt werden können.  
  
     Diese Aktion fungiert jedoch als Filter für die Diagrammdaten, sodass Sie die Anzahl der Elemente später nicht erhöhen können.  
  
8.  Klicken Sie auf **Erweitert**.  
  
     Die **Clusteroptionen** ist das Dialogfeld, in dem Sie die visuelle Darstellung des im Diagramm verwendeten Shapes anpassen. Sie können die im Diagramm verwendeten Farben und das für die Cluster verwendete Shape ändern.  
  
     Die **Schattierungsvariable** Steuerelement funktioniert nicht in Office 2013.  
  
     ![Klicken Sie auf ' Erweitert ', um die Shape-Farben auszuwählen](media/dm13-visio-clusteroptions-advanced.gif "klicken Sie auf ' Erweitert ', um die Shape-Farben auszuwählen")  
  
     **Tipp:** einige Farben können später mithilfe von Visio-Designs und Steuerelementen zur Bearbeitung von Shapes geändert werden. Ein Teil dieser Farbauswahl wird jedoch von Visio-Designs überschrieben. Aus diesem Grund wird empfohlen, mit den Standardfarben zu beginnen und die Änderungen schrittweise vorzunehmen.  
  
9. Klicken Sie auf **Fertig stellen** auf das Diagramm zu erstellen.  
  
     Der Assistent ruft Informationen aus dem Data Mining-Modell ab, rendert die Shapes und füllt jeden Cluster mit Attributen und Werten auf.  
  
     ![Ein Abhängigkeitsnetzwerk](media/dm13-visiodepnet-defaultgraph.gif "einem Abhängigkeitsnetzwerk")  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Durchsuchen und Ändern des fertigen Diagramms  
 Nachdem das Diagramm vollständig erstellt wurde, können Sie dessen Erscheinungsbild, wie im folgenden Beispiel beschrieben, mithilfe von Visio-Steuerelementen anpassen.  
  
 ![Clusterdiagramm mit Visio angepasst](media/dm13-visio-clustercomplete1.gif "Clusterdiagramm mit Visio angepasst")  
  
 Alle grundlegenden Cluster-Shapes werden vom Assistenten generiert. Verwenden Sie die folgenden Tools zum Aktualisieren und Personalisieren des Diagramms:  
  
1.  Ziehen Sie den Schieberegler der **Clusteroptionen** Steuerelement, um schwächere Beziehungen herauszufiltern und das Diagramm zu vereinfachen.  
  
2.  Verwenden Sie die **neues Seitenlayout** Option aus, um verschiedene clusterlayouts experimentieren.  
  
3.  Verwenden der **Connectors** option die **Entwurf** Registerkarte so ändern Sie die Connector-Formatvorlage aus, um Zeilen aus Verbinderformat Cluster beibehalten werden sollen.  
  
4.  Klicken Sie auf die **-Add-Ins** zuerst das Menüband, und zeigen Sie anschließend eine der benutzerdefinierten Symbolleisten zur Bearbeitung von Datamining-Diagramme:  
  
     **Layout**  
     Optimiert die Anordnung der Cluster, sodass sie auf die aktuelle Seite passen.  
  
     **Größe der Seite ändern**  
     Dieses Steuerelement war für frühere HTML-Versionen vorgesehen. Verwenden Sie stattdessen Steuerungselemente zur Anpassung der Visio-Seitengröße.  
  
     **Beschreibung**  
     Wenn ein Cluster ausgewählt ist, klicken Sie auf diese Option, um Details zum Cluster anzuzeigen.  
  
     ![Klicken Sie auf Beschreibung zum Abrufen von Details zum Cluster](media/dm13-visio-cluster-description-control.gif "klicken Sie auf Beschreibung zum Abrufen von Details zum Cluster")  
  
     **Kantenstärke**  
     Zeigt Vertrauensergebnisse für die Linien an, die die Cluster verbinden.  
  
     Wenn Sie eine spezielle Formatierung anwenden, die von der standardmäßig generierten Formatierung des Assistenten abweicht (einschließlich einiger Hintergründe), sind diese Zahlen u. U. nicht sichtbar.  
  
     **Schieberegler**  
     Filtert die Linien zwischen den Clustern. Wenn Sie den Schieberegler verschieben, werden alle Zuordnungen bis auf die wichtigsten entfernt.  
  
     **Schattierung**  
     Dieses Steuerelement funktioniert nicht in Office 2013.  
  
5.  Verwenden der **Schwenken und Zoomen** zu steuern, in der **Aufgabenbereich** des Visio **Ansicht** Multifunktionsleiste, um eine Reihe von Clustern konzentrieren und das Diagramm verschieben.  
  
6.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Cluster, um die Optionen für das Cluster-Shape anzuzeigen:  
  
    -   Ändern Sie das Diagrammformat.  
  
    -   Flügen Sie ein Clustermerkmaldiagramm hinzu.  
  
    -   Fügen Sie ein Clusterunterscheidungsdiagramm hinzu.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung für Data Mining-Diagramme in Visio &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
