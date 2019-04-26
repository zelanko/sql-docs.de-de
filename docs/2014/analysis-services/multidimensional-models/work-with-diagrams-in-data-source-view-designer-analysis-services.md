---
title: Verwenden von Diagrammen im Datenquellensicht-Designer (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.diagramorganizerpane.f1
- sql12.asvs.dsvdesigner.findtable.f1
- sql12.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0b127b3dac76663e77b7ce0fa4faa76a91628ccc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743656"
---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a>Verwenden von Diagrammen im Datenquellensicht-Designer (Analysis Services)
  Das Diagramm einer Datenquellensicht ist eine visuelle Darstellung der in der Datenquellensicht enthaltenen Objekte. Sie können interaktiv mit dem Diagramm arbeiten, um spezifische Objekte hinzuzufügen, auszublenden, zu löschen oder zu ändern. Außerdem können Sie mehrere Diagramme für dieselbe Datenquellensicht erstellen, um die Aufmerksamkeit auf eine Teilmenge von Objekten zu lenken.  
  
 Um den Bereich des Diagramms zu ändern, der im Bereich Diagramm angezeigt wird, klicken Sie auf den Pfeil mit den vier Spitzen in der unteren rechten Ecke des Bereichs, und ziehen Sie das Auswahlfeld über das Miniaturdiagramm, bis der Bereich markiert ist, der im Bereich Diagramm angezeigt werden soll.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Hinzufügen eines Diagramms](#bkmk_add)  
  
 [Bearbeitung oder Löschen eines Diagramms](#bkmk_edit)  
  
 [Suchen von Tabellen in einem Diagramm](#bkmk_findtables)  
  
 [Anordnen von Objekten in einem Diagramm](#bkmk_arrangeobjects)  
  
 [Beibehalten der Objektanordnung](#bkmk_preserve)  
  
##  <a name="bkmk_add"></a> Hinzufügen eines Diagramms  
 Diagramme von Datenquellensichten werden automatisch erstellt, wenn Sie die Datenquellensicht erstellen. Nachdem die Datenquellensicht erstellt wurde, können Sie zusätzliche Diagramme erstellen, entfernen bzw. bestimmte Objekte ausblenden, um eine benutzerfreundlichere Darstellung der Datenquellensicht zu erhalten.  
  
 Zum Erstellen eines neuen Diagramms klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Bereich **Diagrammplaner** und klicken anschließend auf **Neues Diagramm**.  
  
 Wenn Sie eine Datenquellensicht (DSV) in einem Analysis Services-Projekt erstmalig definieren, alle Tabellen und Sichten der Datenquellensicht hinzugefügt werden hinzugefügt der \<alle Tabellen > Diagramm. Dieses Diagramm wird im Bereich Diagrammplaner des Datenquellensicht-Designers angezeigt. Die Tabellen in diesem Diagramm (und ihre Spalten und Beziehungen) werden im Bereich Tabellen aufgelistet. Zudem werden die Tabellen in diesem Diagramm (und ihre Spalten und Beziehungen) grafisch im Schemabereich angezeigt. Allerdings wie Tabellen, Sichten und benannten Abfragen zum Hinzufügen, nach die \<alle Tabellen > Diagramm die bloße Anzahl von Objekten in diesem Diagramm erschwert die Aufgabe zur Visualisierung von Beziehungen, vor allem, wie mehrere Faktentabellen, um das Diagramm hinzugefügt werden und dimension Verknüpfen von Tabellen mit mehreren Faktentabellen verknüpft.  
  
 Zum Reduzieren des visuellen Durcheinanders, wenn Sie nur eine Teilmenge der Tabellen in der Datenquellensicht anzeigen möchten, können Sie Unterdiagramme (einfach Diagramme genannt) definieren, die aus ausgewählten Teilmengen der Tabellen, Sichten und benannten Abfragen in der Datenquellensicht bestehen. Sie können Diagramme verwenden, um Elemente in der Datenquellensicht gemäß den Geschäfts- oder Lösungsanforderungen zu gruppieren.  
  
 Sie können verknüpfte Tabellen und benannte Abfragen in separaten Diagrammen für geschäftliche Zwecke gruppieren. Diese Vorgehensweise eignet sich auch, um Datenquellensichten mit vielen Tabellen, Sichten und benannten Abfragen verständlicher zu gestalten. Die gleiche Tabelle oder benannte Abfrage kann in mehreren Diagrammen, mit Ausnahme von eingeschlossen werden die \<alle Tabellen > Diagramm. In der \<alle Tabellen > Diagramm alle Objekte, die in der Datenquellensicht enthalten sind genau einmal angezeigt.  
  
##  <a name="bkmk_edit"></a> Bearbeitung oder Löschen eines Diagramms  
 Beim Arbeiten mit einem Diagramm sollten Sie besonders auf die Befehle achten, die zum Hinzufügen und Entfernen von Objekten verwendet werden. Wenn Sie ein Objekt aus einem Diagramm löschen, wird es beispielsweise auch aus der Datenquellensicht gelöscht. Wenn Sie das Objekt nur aus dem Diagramm löschen möchten, sollten Sie stattdessen **Tabelle ausblenden** verwenden.  
  
 ![Screenshot des Diagrammarbeitsbereichs, Kontextmenü](../media/ssas-olapdsv-diagram.gif "Screenshot des Diagrammarbeitsbereichs, Kontextmenü")  
  
 Obwohl Sie Objekte einzeln ausblenden können, werden dem Diagramm alle zugehörigen Objekte wieder hinzugefügt, wenn Sie den Befehl Verknüpfte Tabellen anzeigen ausführen. Um zu steuern, welche Objekte in den Arbeitsbereich zurückgegeben werden, ziehen Sie die gewünschten Objekte einfach aus dem Bereich Tabellen.  
  
##  <a name="bkmk_findtables"></a> Suchen von Tabellen in einem Diagramm  
 Bei einem großen Schema ist im Bereich **Diagramm** der Bildlauf zu einer bestimmten Tabelle möglicherweise schwierig. Mithilfe der folgenden Tools können Sie jedoch auf einfache Weise eine Tabelle in einem Diagramm suchen.  
  
-   Führen Sie in der Tabellenliste im Bereich **Tabellen** einen Bildlauf durch.  
  
     Um eine Tabelle in das aktuell angezeigte Diagramm einzuschließen, ziehen Sie die Tabelle aus dem Bereich **Tabellen** in den Bereich Diagramm.  
  
     Um die Anzeige für eine Tabelle zu zentrieren, die bereits in das Diagramm eingeschlossen ist, wählen Sie die Tabelle im Bereich **Tabellen** aus.  
  
-   Tabellenlokator im **Diagramm** Bereich – der tabellenlokator ist ein 4-Wege-Pfeilsymbol und befindet sich am Schnittpunkt der vertikalen und horizontalen Bildlaufleisten in der unteren rechten Ecke des der **Diagramm** Bereich. Daraufhin wird eine Miniaturansicht des aktuellen Diagramms im Bereich Diagramm geöffnet. Mithilfe dieser Miniaturansicht können Sie die Ansicht im Bereich Diagramm ändern, um eine beliebige Stelle im Diagramm darzustellen.  
  
-   Verwenden der **Tabelle suchen** Dialogfeld im Feld-Right click auf einen offenen Bereich im Diagramm-Bereich, und klicken Sie auf **Tabelle suchen**. Oder klicken Sie auf der Symbolleiste oder im Menü **Datenquellensicht** auf den Befehl **Tabelle suchen** .  
  
     Sie können Zeichenfolgen und Platzhalterzeichen in das Feld Filter eingeben, um Teilmengen der Tabellen im Diagramm anzuzeigen.  
  
##  <a name="bkmk_arrangeobjects"></a> Anordnen von Objekten in einem Diagramm  
 Obwohl es möglich ist, mit dem Datenquellensicht-Designer mehrere Diagramme zu definieren, um eine Datenquellensicht verständlicher zu gestalten, können Diagramme mit Dutzenden von Tabellen schwer lesbar sein, und die manuelle Neuanordnung von Tabellenlayouts ist ein zeitraubender Prozess. Mit dem Datenquellensicht-Designer können die Tabellen im aktuellen Diagramm automatisch auf Basis der Beziehungen zwischen den Tabellen im aktuellen Diagramm in einem rechteckigen oder diagonalen Layout neu angeordnet werden.  
  
-   In einem rechteckigen Layout verlaufen die Beziehungslinien zwischen Tabellen und nicht zwischen Spalten. Beziehungslinien werden horizontal und vertikal zwischen Tabellen gezogen.  
  
-   In einem diagonalen Layout verlaufen Beziehungslinien so direkt wie möglich zwischen verknüpften Spalten in Tabellen. Eine Beziehung zu mehreren Spalten wird mit der ersten verknüpften Spalte in der Tabelle verbunden. Falls die Spalten in einer Tabelle nicht sichtbar sind, werden die Linien zum oberen Tabellenende hin gezogen.  
  
##  <a name="bkmk_preserve"></a> Beibehalten der Objektanordnung  
 Nachdem Sie die Tabellen manuell in der gewünschten Form angeordnet haben, kann beim Hinzufügen weiterer Tabellen eine Diagrammaktualisierung auftreten. Dabei werden neuere Änderungen, die Sie am Objektlayout vorgenommen haben, gelöscht.  
  
 Dieses Verhalten tritt mit höherer Wahrscheinlichkeit beim Hinzufügen einer Tabelle auf, da der Diagrammplaner in diesem Fall die anderen Tabellen verschieben muss, um Platz für die neue Tabelle zu schaffen. Anschließend wird das Diagramm neu gerendert, um zu gewährleisten, dass alle Tabellen und Verbindungslinien ordnungsgemäß dargestellt werden. Wenn Sie die Platzierung bestimmter Objekte manuell angepasst haben, können die Änderungen bei diesem Schritt verloren gehen.  
  
 Um dieses Problem zu vermeiden, fügen Sie zuerst alle Tabellen hinzu, bevor Sie abschließende Anpassungen vornehmen. Wenn Sie das Diagramm später erneut öffnen, sollten sich die Objekte an ihrer ursprünglichen Position befinden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellsichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)   
 [Datenquellensicht-Designer &#40;Analysis Services – Mehrdimensionale Daten&#41;](../data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
