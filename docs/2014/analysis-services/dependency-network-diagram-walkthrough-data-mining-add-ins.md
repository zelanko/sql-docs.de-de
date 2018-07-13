---
title: Abhängigkeit Exemplarische Vorgehensweise (Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
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
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3efc5633a31af6d26fa7ae4abc5ce5b97f8542b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218460"
---
# <a name="dependency-network-diagram-walkthrough-data-mining-add-ins"></a>Exemplarische Vorgehensweise für das Abhängigkeitsnetzwerkdiagramm (Data Mining-Add-Ins)
  Mehrere verschiedene Data Mining-Modelltypen verwenden ein Netzwerkdiagramm, um Beziehungen in den Daten zu untersuchen. Sie können diese Modelle importieren, in Visio mithilfe der **Abhängigkeitsnetzwerk** strukturieren und anpassen und erweitern das Layout anschließend weiter. Die **Data Mining-Shapes für Visio** enthalten die folgenden benutzerdefinierten Steuerelemente zum Arbeiten mit abhängigkeitsnetzwerkdiagrammen:  
  
-   Rendern von Steuerelementen für das Netzwerkdiagramm  
  
     Diese Optionen sind Teil des Assistenten, der geöffnet wird, wenn Sie ein Shape auf dem Visio-Arbeitsbereich ablegen.  
  
-   **Data Mining Layout** Symbolleiste  
  
     Diese Optionen werden dem Visio-Arbeitsbereich hinzugefügt, um Ihnen die Interaktion mit dem Abhängigkeitsnetzwerkdiagramm zu erleichtern.  
  
## <a name="build-a-dependency-network-graph"></a>Erstellen eines Abhängigkeitsnetzwerkdiagramms  
 Sie löschen ein Shape auf der Visio-Seite zum Starten der **Abhängigkeitsnetzwerk Visio-Shape-Assistent** und Diagrammoptionen festzulegen.  
  
#### <a name="use-the-dependency-net-visio-shape-wizard"></a>Verwenden des "Assistenten für das Abhängigkeitsnetzwerk-Shape in Visio"  
  
1.  Wenn Sie nicht angezeigt werden **Microsoft Data Mining-Shapes** in der **Formen** auf **weitere Shapes**Option **Schablone öffnen**, und öffnen Sie die die Vorlage aus den standardmäßigen Installationsspeicherort.  
  
     \<Laufwerk >: \Programme (x85) \Microsoft SQL Server 2012 DM-Add-Ins  
  
2.  Ziehen Sie die **Abhängigkeitsnetzwerk** Form auf der Seite aus, um den Assistenten zu starten. Klicken Sie auf **Weiter**.  
  
3.  Klicken Sie auf der Seite Willkommen des der **Abhängigkeit Assistenten Shape in Visio**, klicken Sie auf **Weiter**.  
  
4.  Auf der **Vybrat Zdroj DAT** auf der Seite die **Abhängigkeit Assistenten Shape in Visio**, wählen Sie eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Server mit dem Modell, das Sie visuell darstellen möchten.  
  
5.  Wählen Sie ein geeignetes Miningmodell aus, und klicken Sie auf **Weiter**.  
  
     Zum Auswählen des geeigneten Modells können Sie überprüfen, der Name, Beschreibung, Spalten und Datentypen in der **Eigenschaften** Bereich.  
  
     Dieses Shape unterstützt Modelle, die anhand der folgenden Algorithmen erstellt wurden:  
  
    -   Naive Bayes  
  
    -   Entscheidungsstrukturen  
  
    -   Zuordnungsregeln  
  
6.  Auf der Seite **zu rendernde Knoten auswählen**, die Größe des Diagramms anpassen und optional filtern, um nur bestimmte Knoten einzuschließen.  
  
     Mit einem großen Dataset kann ein Abhängigkeitsdiagramm kann umfangreich und enthalten viele verbundene Objekte, dargestellt als *Knoten*. Mithilfe dieses Dialogfelds können Sie ein benutzerdefiniertes Netzwerkdiagramm erstellen, das nur die interessanten Knoten enthält.  
  
     [Art Plathalter]  
  
     **Anzahl der abzurufenden Knoten**  
     Falls das Modell weniger Knoten als die angegebene Knotenanzahl enthält, wirkt sich diese Einstellung nicht aus. Falls das Modell mehr Knoten als die angegebene Anzahl enthält, werden nur die wichtigsten Knoten angezeigt.  
  
     **Name enthält**  
     Lassen Sie dieses Feld leer, und klicken Sie auf den grünen Pfeil, um alle Knoten im Modell abzurufen.  
  
     Alternativ geben Sie eine Zeichenfolge ein und klicken auf den grünen Pfeil, um nur die Knoten zurückzugeben, die die angegebene Zeichenfolge enthalten.  
  
     Die meisten Modelle, die Sie anhand von Beispieldaten erstellen können, sind nicht besonders groß. Erhöhen Sie die Anzahl der Knoten auf 10, und klicken Sie auf den grünen Pfeil, um eine Abfrage auszuführen und eine Liste aller Knoten abzurufen.  
  
7.  Klicken Sie auf **erweitert** um die schattierungs- und shapeoptionen für das Diagramm festzulegen.  
  
8.  Klicken Sie auf **schließen** zum Beenden der **erweitert** Optionen (Dialogfeld), und klicken Sie dann auf **Fertig stellen** auf das Diagramm zu erstellen.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Durchsuchen und Ändern des fertigen Diagramms  
 Nachdem das Abhängigkeitsnetzwerkdiagramm von Visio erstellt wurde, können Sie anhand der Visio-Funktionen weitere Änderungen und Verbesserungen am Diagramm vornehmen.  
  
 Die folgende Abbildung zeigt das Standardlayout eines Abhängigkeitsnetzwerkdiagramms.  
  
 [Art Plathalter]  
  
1.  Verwenden der **Schwenken und Zoomen** zu steuern, in der **Aufgabenbereich** des Visio **Ansicht** Multifunktionsleiste, um auf einen Abschnitt des Diagramms zu konzentrieren und das Diagramm verschieben.  
  
2.  Experimentieren Sie mit der verschiedene Diagrammlayouts, die von Visio bereitgestellten **neues Seitenlayout** Option.  
  
3.  Klicken Sie auf die **-Add-Ins** zuerst das Menüband, und zeigen Sie anschließend eine der benutzerdefinierten Symbolleisten zur Bearbeitung von Datamining-Diagramme:  
  
     **Layout**  
     Optimiert das Layout von Knoten auf dem Zeichenblatt und ändert die Anzeige so, dass alle Knoten sichtbar sind.  
  
     **Größe der Seite ändern**  
     Ändert die Zeichenblattgröße so, dass alle Knoten sichtbar sind.  
  
     **Kantenstärke**  
     Blendet die Anzeige der Kantenstärke für das gesamte Diagramm ein/aus. Eine Kante ist eine Verbindung zwischen Knoten. Sie können das Schieberegler-Steuerelement verwenden, um schwache Verbindungen herauszufiltern.  
  
     **Schieberegler**  
     Die **Schieberegler** können Sie steuern die Stärke der Beziehungen, die in das Abhängigkeitsnetzwerk-Diagramm angezeigt werden.  
  
     Jeder Knoten im Diagramm stellt einen Status dar. Ein Pfeil stellt einen Übergang zwischen zwei Status dar, und die Wahrscheinlichkeit, dass dieser einem Übergang zugeordnet ist. Zum Verringern der Anzahl von Knoten im Diagramm bewegen Sie die Schiebereglerleiste nach oben.  
  
     Zum Erhöhen der Anzahl von Knoten im Diagramm bewegen Sie die Schiebereglerleiste nach unten.  
  
     **Hinzufügen von Elementen**  
     Öffnet die **zu rendernde Knoten auswählen** Dialogfeld, sodass Sie neue Knoten im Diagramm hinzuzufügende auswählen können.  
  
4.  Sie können Diagramme so einfach oder komplex gestalten, wie Sie möchten, und Anmerkungen hinzufügen, während Sie mit dem Modell verbunden sind.  
  
     [ art placeholder]  
  
> [!WARNING]  
>  Die Hervorhebung abhängiger Knoten und andere Kontextmenüoptionen, die in früheren Versionen des Add-Ins verfügbar waren, sind in Office 2013 nicht funktionsfähig.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung für Data Mining-Diagramme in Visio &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
