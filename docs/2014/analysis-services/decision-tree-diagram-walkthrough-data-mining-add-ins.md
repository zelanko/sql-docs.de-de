---
title: Exemplarische Vorgehensweise für das Entscheidungsstruktur Diagramm (Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- shapes, data mining
- diagram, decision tree
- Visio shapes, decision tree
- decision tree [data mining]
ms.assetid: 9566f6a2-c750-4125-ba5e-42c7251a78c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ef951825144f381ab37a83526ec96321fe43cfec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66082282"
---
# <a name="decision-tree-diagram-walkthrough--data-mining-add-ins"></a>Exemplarische Vorgehensweise für das Entscheidungsstruktur Diagramm (Data Mining-Add-Ins)
  Wenn Sie ein Entscheidungsstrukturmodell erstellt haben, können Sie ein benutzerdefiniertes Diagramm in Visio erstellen. Dazu stehen Ihnen die Shapes Entscheidungsstruktur und Abhängigkeitsnetzwerk zur Verfügung. In diesem Thema werden die Anpassungen beschrieben, die Sie mithilfe der Form **Entscheidungs** Struktur und der folgenden Steuerelemente durchführen können:  
  
-   Rendern von Steuerelementen für das Entscheidungsstrukturdiagramm  
  
     Diese Optionen sind Teil des Entscheidungsstruktur- **Assistenten** , der gestartet wird, wenn Sie eine Form im Visio-Arbeitsbereich ablegen.  
  
-   Symbolleiste für **Data Mining-Layout**  
  
     Diese Optionen werden dem Visio-Arbeitsbereich hinzugefügt, um Ihnen die Interaktion mit dem Shape zu erleichtern.  
  
## <a name="build-a-decision-tree-diagram"></a>Erstellen eines Entscheidungsstrukturdiagramms  
 Legen Sie die Form Entscheidungsstruktur auf der Visio-Seite ab, um den Assistenten für die **Entscheidungsstruktur Visio-Shape** zu starten und Diagramm Optionen festzulegen.  
  
#### <a name="use-the-decision-tree-wizard"></a>Verwenden des Entscheidungsstruktur-Assistenten  
  
1.  Wenn **Microsoft Data Mining-Formen** in der Liste **Shapes** nicht angezeigt werden, klicken Sie auf **Weitere Formen**, wählen Sie **Schablone öffnen**aus, und öffnen Sie die Vorlage aus dem Standard Installationsverzeichnis.  
  
     \<Laufwerk>: \Programme (x85) \Microsoft SQL Server 2012 DM-Add-ins  
  
2.  Ziehen Sie die Form **Entscheidungs** Struktur auf die Seite.  
  
3.  Klicken Sie auf der Willkommensseite des Assistenten für das Entscheidungsstruktur- **Shape in Visio**auf **weiter**.  
  
4.  Wählen Sie auf der Seite **Datenquelle auswählen** des **Cluster-Assistenten**eine Verbindung mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Server aus, auf dem sich das Modell befindet, das Sie visualisieren möchten.  
  
5.  Wählen Sie ein geeignetes Mining Modell aus, und klicken Sie auf **weiter**.  
  
     Dieser Diagrammtyp unterstützt Modelle, die mit den Decision Trees oder dem Linear Regression-Algorithmus erstellt wurden.  
  
6.  Wählen Sie auf der Seite **Entscheidungsstruktur auswählen** eine einzelne Struktur aus, die angezeigt werden soll.  
  
     Eine Struktur modelliert die Interaktionen, die zu einem bestimmten Ergebnis führen, das Sie modelliert haben. Daher können Sie, auch wenn das Modell mehrere Ergebnisse enthält, nur eine Struktur gleichzeitig anzeigen.  
  
7.  Im Dialogfeld **Entscheidungsstruktur auswählen** können Sie auch diese Renderingoptionen festlegen:  
  
     **Maximale Renderingtiefe**  
     Mit dieser Option steuern Sie, wie viele Knoten angezeigt werden.  
  
     Eine Entscheidungsstruktur kann sehr tief verzweigt sein, sodass das fertige Diagramm möglicherweise nicht auf die Seite passt. Verwenden Sie dieses Steuerelement, um die wichtigeren, äußeren linken Knoten zu fokussieren.  
  
     Standardmäßig werden drei Knotenebenen angezeigt.  
  
     **Farbe und Anzeigetext für Werte auswählen**  
     Wählen Sie die Farbe aus, durch die die einzelnen Ergebnisse dargestellt werden. Wenn Sie keine Farben angeben, werden diese automatisch anhand der aktuellen Videodesignfarben generiert.  
  
8.  Klicken Sie auf **erweitert** , um die folgenden Optionen für die einzelnen Knoten im Entscheidungsstruktur Diagramm anzupassen.  
  
     **Schattierungs Variable** und **Status**  
     Wählen Sie das Zielergebnis aus, das Sie im Strukturdiagramm anzeigen möchten.  
  
     **Histogramm anzeigen**  
     Fügt jedem Knoten, in dem Definitionsregeln für diesen Knoten angezeigt werden, ein Diagramm hinzu.  
  
     **Bezeichnung anzeigen**  
     Fügt dem Histogramm Spaltennamen hinzu.  
  
     **Wahrscheinlichkeit anzeigen**  
     Zeigt die Wahrscheinlichkeit der einzelnen Werte an.  
  
     **Unterstützung anzeigen**  
     Zeigt die Unterstützung jedes einzelnen Werts an.  
  
     **Fußzeile anzeigen**  
     Fügt eine Fußzeile hinzu, in der alle angezeigten Werte summiert werden.  
  
     **Kopfzeile anzeigen**  
     Fügt Spaltenüberschriften hinzu.  
  
     **Status ohne Unterstützung anzeigen**  
     Ermöglicht die Anzeige fehlender Werte.  
  
9. Klicken Sie auf **Fertig** stellen, um das Diagramm zu erstellen.  
  
    > [!WARNING]  
    >  In einigen Umgebungen kann es vorkommen, dass Verbinder in Office 2013 nicht gerendert werden.  
  
## <a name="explore-and-modify-the-finished-diagram"></a>Durchsuchen und Ändern des fertigen Diagramms  
 Nachdem Sie den Assistenten für das Entscheidungsstruktur- **Shape in Visio**abgeschlossen haben, wird von Visio ein Strukturdiagramm auf der Seite erstellt, das die Regeln grafisch anzeigt, die zum vorhergesagten Ergebnis führen.  
  
 Anhand der folgenden Steuerelemente für Entscheidungsstrukturdiagramme können Sie weitere Änderungen am Shape vornehmen:  
  
#### <a name="using-the-decision-tree-option-menus"></a>Verwenden der Menüs mit Entscheidungsstrukturoptionen  
  
1.  Klicken Sie auf das Menüband **Add-ins** , und zeigen Sie dann eine der benutzerdefinierten Symbolleisten an, die für die Arbeit mit Data Mining Diagrammen verwendet werden:  
  
     **Layout **  
     Optimiert die Anordnung der Struktur, sodass sie auf die aktuelle Seite passt.  
  
     **Größe der Seite ändern**  
     Dieses Steuerelement war für frühere HTML-Versionen vorgesehen. Verwenden Sie stattdessen die Steuerelemente für die Anpassung von Visio-Seiten,  
  
     **Beschreibung**  
     Wenn ein Strukturknoten ausgewählt ist, klicken Sie auf diese Option, um die Details der im Knoten enthaltenen Fälle anzuzeigen.  
  
2.  Verwenden Sie die Option **neulayoutseite** im Visio-Menüband **Design** , um mit verschiedenen Struktur Layouts zu experimentieren.  
  
3.  Verwenden Sie die Option **Connectors** auf der Registerkarte **Entwurf** , um die Connectors zu ändern, die zwischen den Knoten in der Struktur verwendet werden.  
  
4.  Verwenden Sie das Steuerelement **schwenken und Zoomen** im **Aufgaben** Bereich des Menübands **Ansicht Ansicht** , um sich auf einen bestimmten Bereich des Diagramms zu konzentrieren.  
  
5.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Strukturknoten, und wählen Sie im Kontextmenü spezifische Optionen für Entscheidungsstrukturdiagramme aus:  
  
     **Zeichenblattlayout verbessern**  
     Verteilt die Knoten gleichmäßig auf dem Zeichenblatt und passt die Seitenansicht so an, dass alle Knoten sichtbar sind.  
  
     **Untergeordnete Elemente auf neues Zeichenblatt verschieben**  
     Verschiebt die untergeordneten Elemente des aktuell ausgewählten Knotens auf eine neue Seite.  
  
     **Untergeordnete Knoten reduzieren**  
     Blendet die untergeordneten Elemente des aktuell ausgewählten Knotens aus.  
  
     **Untergeordnete Knoten erweitern**  
     Blendet untergeordnete Elemente des ausgewählten Knotens wieder ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Problembehandlung bei Visio Data Mining-Diagrammen &#40;SQL Server Data Mining-Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)  
  
  
