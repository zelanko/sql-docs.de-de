---
title: Exemplarische Vorgehensweise (Data Mining-Add-ins) Decision | Microsoft-Dokumentation
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
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4b4eb570d1d81bc724c885e8c277aa662cf4ff5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291716"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a>Entscheidung Exemplarische Vorgehensweise (Data Mining-Add-ins)
  Wenn Sie ein Entscheidungsstrukturmodell erstellt haben, können Sie ein benutzerdefiniertes Diagramm in Visio erstellen. Dazu stehen Ihnen die Shapes Entscheidungsstruktur und Abhängigkeitsnetzwerk zur Verfügung. In diesem Thema wird beschrieben, die Anpassungen, die Sie ausführen können, mit der **Entscheidungsstruktur** Form und diese Steuerelemente:  
  
-   Rendern von Steuerelementen für das Entscheidungsstrukturdiagramm  
  
     Diese Optionen sind Teil der **Entscheidungsstruktur-Assistenten** gestartet wird, wenn Sie eine Form auf dem Visio-Arbeitsbereich ablegen.  
  
-   **Data Mining Layout** Symbolleiste  
  
     Diese Optionen werden dem Visio-Arbeitsbereich hinzugefügt, um Ihnen die Interaktion mit dem Shape zu erleichtern.  
  
## <a name="build-a-decision-tree-diagram"></a>Erstellen eines Entscheidungsstrukturdiagramms  
 Sie legen Sie die Entscheidungsstruktur Form auf der Visio-Seite zum Starten der **Entscheidung Assistenten Shape in Visio** und Diagrammoptionen festzulegen.  
  
#### <a name="use-the-decision-tree-wizard"></a>Verwenden des Entscheidungsstruktur-Assistenten  
  
1.  Wenn Sie nicht angezeigt werden **Microsoft Data Mining-Shapes** in der **Formen** auf **weitere Shapes**Option **Schablone öffnen**, und öffnen Sie die die Vorlage aus den standardmäßigen Installationsspeicherort.  
  
     \<Laufwerk >: \Programme (x85) \Microsoft SQL Server 2012 DM-Add-Ins  
  
2.  Ziehen Sie die **Entscheidungsstruktur** Shape auf der Seite.  
  
3.  Klicken Sie auf der Seite Willkommen des der **Entscheidung Assistenten Shape in Visio**, klicken Sie auf **Weiter**.  
  
4.  Auf der **Vybrat Zdroj DAT** auf der Seite die **Clustererstellungs-Assistenten**, wählen Sie eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Server mit dem Modell, das Sie visuell darstellen möchten.  
  
5.  Wählen Sie ein geeignetes Miningmodell aus, und klicken Sie auf **Weiter**.  
  
     Dieser Diagrammtyp unterstützt Modelle, die mit dem Decision Trees oder dem Linear Regression-Algorithmus erstellt.  
  
6.  Auf der **Entscheidungsstruktur auswählen** Seite, und wählen Sie eine individuelle Struktur anzeigen.  
  
     In einer Struktur werden die Interaktionen abgebildet, die zu einem bestimmten modellierten Ergebnis geführt haben. Deshalb können Sie jeweils nur eine Struktur anzeigen, auch wenn das Modell mehrere Ergebnisse enthält.  
  
7.  In der **Entscheidungsstruktur auswählen** im Dialogfeld können Sie auch folgenden Renderingoptionen festlegen:  
  
     **Maximale Renderingtiefe**  
     Mit dieser Option steuern Sie, wie viele Knoten angezeigt werden.  
  
     Eine Entscheidungsstruktur kann sehr tief verzweigt sein, sodass das fertige Diagramm möglicherweise nicht auf die Seite passt. Verwenden Sie dieses Steuerelement, um die wichtigeren, äußeren linken Knoten zu fokussieren.  
  
     Standardmäßig werden drei Knotenebenen angezeigt.  
  
     **Wählen Sie die Farbe und Anzeigetext für Werte**  
     Wählen Sie die Farbe aus, durch die die einzelnen Ergebnisse dargestellt werden. Wenn Sie keine Farben angeben, werden diese automatisch anhand der aktuellen Videodesignfarben generiert.  
  
8.  Klicken Sie auf **erweitert** um die folgenden Optionen für jeden Knoten in das entscheidungsstrukturdiagramm anzupassen.  
  
     **Schattierungsvariable** und **Zustand**  
     Wählen Sie das Zielergebnis aus, das Sie im Strukturdiagramm anzeigen möchten.  
  
     **Histogramm anzeigen**  
     Fügt jedem Knoten, in dem Definitionsregeln für diesen Knoten angezeigt werden, ein Diagramm hinzu.  
  
     **Bezeichnung anzeigen**  
     Fügt dem Histogramm Spaltennamen hinzu.  
  
     **Wahrscheinlichkeit anzeigen**  
     Zeigt die Wahrscheinlichkeit der einzelnen Werte an.  
  
     **Zeigen Sie Unterstützung**  
     Zeigt die Unterstützung jedes einzelnen Werts an.  
  
     **Footer anzeigen**  
     Fügt eine Fußzeile hinzu, in der alle angezeigten Werte summiert werden.  
  
     **Header anzeigen**  
     Fügt Spaltenüberschriften hinzu.  
  
     **Status ohne Unterstützung anzeigen**  
     Ermöglicht die Anzeige fehlender Werte.  
  
9. Klicken Sie auf **Fertig stellen** auf das Diagramm zu erstellen.  
  
    > [!WARNING]  
    >  In einigen Umgebungen kann es vorkommen, dass Verbinder in Office 2013 nicht gerendert werden.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Durchsuchen und Ändern des fertigen Diagramms  
 Nach Abschluss der **Entscheidung Assistenten Shape in Visio**, erstellt Visio ein Strukturdiagramm auf der Seite, die grafisch die Regeln, die zum vorhergesagten Ergebnis führen.  
  
 Anhand der folgenden Steuerelemente für Entscheidungsstrukturdiagramme können Sie weitere Änderungen am Shape vornehmen:  
  
#### <a name="using-the-decision-tree-option-menus"></a>Verwenden der Menüs mit Entscheidungsstrukturoptionen  
  
1.  Klicken Sie auf die **-Add-Ins** zuerst das Menüband, und zeigen Sie anschließend eine der benutzerdefinierten Symbolleisten zur Bearbeitung von Datamining-Diagramme:  
  
     **Layout**  
     Optimiert die Anordnung der Struktur, sodass sie auf die aktuelle Seite passt.  
  
     **Größe der Seite ändern**  
     Dieses Steuerelement war für frühere HTML-Versionen vorgesehen. Verwenden Sie stattdessen Steuerungselemente die Visio-Seite,  
  
     **Beschreibung**  
     Wenn ein Strukturknoten ausgewählt ist, klicken Sie auf diese Option, um die Details der im Knoten enthaltenen Fälle anzuzeigen.  
  
2.  Verwenden der **neues Seitenlayout** -Option in der Visio **Entwurf** Multifunktionsleiste, um verschiedene Strukturlayouts experimentieren.  
  
3.  Verwenden der **Connectors** option die **Entwurf** Tab, um die Verbinder zwischen Knoten in der Struktur zu ändern.  
  
4.  Verwenden der **Schwenken und Zoomen** zu steuern, in der **Aufgabenbereich** des Visio **Ansicht** Multifunktionsleiste, um auf einen bestimmten Bereich des Diagramms zu konzentrieren.  
  
5.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Strukturknoten, und wählen Sie im Kontextmenü spezifische Optionen für Entscheidungsstrukturdiagramme aus:  
  
     **Zeichenblattlayout verbessern**  
     Verteilt die Knoten gleichmäßig auf dem Zeichenblatt und passt die Seitenansicht so an, dass alle Knoten sichtbar sind.  
  
     **Untergeordnete Elemente auf neues Zeichenblatt verschieben**  
     Die untergeordneten Elemente des aktuell ausgewählten Knotens verschoben auf eine neue Seite.  
  
     **Untergeordnete Knoten reduzieren**  
     Blendet die untergeordneten Elemente des aktuell ausgewählten Knotens aus.  
  
     **Untergeordnete Knoten erweitern**  
     Blendet untergeordnete Elemente des ausgewählten Knotens wieder ein.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung für Data Mining-Diagramme in Visio &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
