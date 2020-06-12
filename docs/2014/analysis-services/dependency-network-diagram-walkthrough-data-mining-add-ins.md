---
title: Exemplarische Vorgehensweise für das Abhängigkeits Netzwerkdiagramm (Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Visio shapes, dependency network
- shapes, data mining
- shapes, network
- dependencies
- diagram, dependency network
- data mining layout toolbar
- dependency network
ms.assetid: aac732a8-5262-4649-b7d7-3ccf6f9cfa8b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8138cef980e7b040a99a6e1db21f1b67fd84aeb5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528776"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a>Exemplarische Vorgehensweise für das Abhängigkeitsnetzwerkdiagramm (Data Mining-Add-Ins)
  Mehrere verschiedene Data Mining-Modelltypen verwenden ein Netzwerkdiagramm, um Beziehungen in den Daten zu untersuchen. Sie können diese Modelle mithilfe der Form **Abhängigkeits Netzwerk** in Visio importieren und das Layout anschließend weiter anpassen und verbessern. Die **Data Mining-Shapes für Visio** enthalten die folgenden benutzerdefinierten Steuerelemente zum Arbeiten mit Abhängigkeits Netzwerk Diagrammen:  
  
-   Rendern von Steuerelementen für das Netzwerkdiagramm  
  
     Diese Optionen sind Teil des Assistenten, der geöffnet wird, wenn Sie ein Shape auf dem Visio-Arbeitsbereich ablegen.  
  
-   Symbolleiste für **Data Mining-Layout**  
  
     Diese Optionen werden dem Visio-Arbeitsbereich hinzugefügt, um Ihnen die Interaktion mit dem Abhängigkeitsnetzwerkdiagramm zu erleichtern.  
  
## <a name="build-a-dependency-network-graph"></a>Erstellen eines Abhängigkeitsnetzwerkdiagramms  
 Sie können eine Form auf der Visio-Seite ablegen, um den Assistenten für das **Abhängigkeits Netzwerk von Visio** zu starten und Diagramm Optionen festzulegen.  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a>Verwenden des "Assistenten für das Abhängigkeitsnetzwerk-Shape in Visio"  
  
1.  Wenn **Microsoft Data Mining-Formen** in der Liste **Shapes** nicht angezeigt werden, klicken Sie auf **Weitere Formen**, wählen Sie **Schablone öffnen**aus, und öffnen Sie die Vorlage aus dem Standard Installationsverzeichnis.  
  
     \<drive>: \Programme (x85) \Microsoft SQL Server 2012 DM-Add-ins  
  
2.  Ziehen Sie die Form **Abhängigkeits Netzwerk** auf die Seite, um den Assistenten zu starten. Klicken Sie auf **Weiter**.  
  
3.  Klicken Sie auf der Willkommensseite des Assistenten für das **Abhängigkeits Netzwerk-Shape in Visio**auf **weiter**.  
  
4.  Wählen Sie auf der Seite **Datenquelle auswählen** des **Assistenten für das Abhängigkeits Netzwerk-Shape in Visio**eine Verbindung mit einem Server aus, auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dem sich das Modell befindet, das Sie visualisieren möchten.  
  
5.  Wählen Sie ein geeignetes Mining Modell aus, und klicken Sie auf **weiter**.  
  
     Zum Auswählen eines geeigneten Modells können Sie den Namen, die Beschreibung, die Spalten und den Typ der Daten im **Eigenschaften** Bereich überprüfen.  
  
     Dieses Shape unterstützt Modelle, die anhand der folgenden Algorithmen erstellt wurden:  
  
    -   Naive Bayes  
  
    -   Entscheidungsstrukturen  
  
    -   Zuordnungs Regeln  
  
6.  Wählen Sie auf der Seite die **Knoten zum Rendering**aus, passen Sie die Größe des Diagramms an, und Filtern Sie optional, um nur bestimmte Knoten einzubeziehen.  
  
     Bei einem großen DataSet kann ein Abhängigkeits Diagramm sehr groß werden und viele verbundene Objekte enthalten, die als *Knoten*dargestellt werden. Mithilfe dieses Dialogfelds können Sie ein benutzerdefiniertes Netzwerkdiagramm erstellen, das nur die interessanten Knoten enthält.  
  
     [Kunst Platzhalter]  
  
     **Anzahl der abzurufenden Knoten**  
     Falls das Modell weniger Knoten als die angegebene Knotenanzahl enthält, wirkt sich diese Einstellung nicht aus. Falls das Modell mehr Knoten als die angegebene Anzahl enthält, werden nur die wichtigsten Knoten angezeigt.  
  
     **Name enthält**  
     Lassen Sie dieses Feld leer, und klicken Sie auf den grünen Pfeil, um alle Knoten im Modell abzurufen.  
  
     Alternativ geben Sie eine Zeichenfolge ein und klicken auf den grünen Pfeil, um nur die Knoten zurückzugeben, die die angegebene Zeichenfolge enthalten.  
  
     Die meisten Modelle, die Sie anhand von Beispieldaten erstellen können, sind nicht besonders groß. Erhöhen Sie die Anzahl der Knoten auf 10, und klicken Sie auf den grünen Pfeil, um eine Abfrage auszuführen und eine Liste aller Knoten abzurufen.  
  
7.  Klicken Sie auf **erweitert** , um Schattierungs-und Shape-Optionen für das Diagramm festzulegen.  
  
8.  Klicken Sie auf schließen, um das Dialogfeld **Erweiterte** Optionen zu **Schließen** , und klicken Sie auf **Fertig** stellen, um das Diagramm zu erstellen.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Durchsuchen und Ändern des fertigen Diagramms  
 Nachdem das Abhängigkeitsnetzwerkdiagramm von Visio erstellt wurde, können Sie anhand der Visio-Funktionen weitere Änderungen und Verbesserungen am Diagramm vornehmen.  
  
 Die folgende Abbildung zeigt das Standardlayout eines Abhängigkeitsnetzwerkdiagramms.  
  
 [Kunst Platzhalter]  
  
1.  Verwenden Sie das Steuerelement **schwenken und Zoomen** im **Aufgaben** Bereich des Menübands **Ansicht Ansicht** , um sich auf einen Bereich des Diagramms zu konzentrieren und das Diagramm zu verschieben.  
  
2.  Experimentieren Sie mit verschiedenen Diagramm Layouts, die von der Visio **-Seite für neulayoutseiten** bereitgestellt werden.  
  
3.  Klicken Sie auf das Menüband **Add-ins** , und zeigen Sie dann eine der benutzerdefinierten Symbolleisten an, die für die Arbeit mit Data Mining Diagrammen verwendet werden:  
  
     **Layout**  
     Optimiert das Layout von Knoten auf dem Zeichenblatt und ändert die Anzeige so, dass alle Knoten sichtbar sind.  
  
     **Größe der Seite ändern**  
     Ändert die Zeichenblattgröße so, dass alle Knoten sichtbar sind.  
  
     **Kantenstärke**  
     Blendet die Anzeige der Kantenstärke für das gesamte Diagramm ein/aus. Eine Kante ist eine Verbindung zwischen Knoten. Sie können das Schieberegler-Steuerelement verwenden, um schwache Verbindungen herauszufiltern.  
  
     **Schieberegler**  
     Mit dem **Schieberegler** können Sie die Stärke der Beziehungen steuern, die im Abhängigkeits Netzwerkdiagramm angezeigt werden.  
  
     Jeder Knoten im Diagramm stellt einen Status dar. Ein Pfeil stellt einen Übergang zwischen zwei Status dar, und die Wahrscheinlichkeit, dass dieser einem Übergang zugeordnet ist. Zum Verringern der Anzahl von Knoten im Diagramm bewegen Sie die Schiebereglerleiste nach oben.  
  
     Zum Erhöhen der Anzahl von Knoten im Diagramm bewegen Sie die Schiebereglerleiste nach unten.  
  
     **Elemente hinzufügen**  
     Öffnet das Dialogfeld **zu Rendering-Knoten auswählen** , sodass Sie neue Knoten auswählen können, die dem Diagramm hinzugefügt werden sollen.  
  
4.  Sie können Diagramme so einfach oder komplex gestalten, wie Sie möchten, und Anmerkungen hinzufügen, während Sie mit dem Modell verbunden sind.  
  
     [ art placeholder]  
  
> [!WARNING]  
>  Die Hervorhebung abhängiger Knoten und andere Kontextmenüoptionen, die in früheren Versionen des Add-Ins verfügbar waren, sind in Office 2013 nicht funktionsfähig.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei Visio Data Mining-Diagrammen &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
