---
title: Steuern der Tablix-Datenbereichsanzeige auf einer Berichtsseite (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f81c48cc-f038-4f57-988d-e9a3cbb46424
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c6fd4b09947bc10a9e4e960ca1097f807a47c14f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106209"
---
# <a name="controlling-the-tablix-data-region-display-on-a-report-page-report-builder-and-ssrs"></a>Steuern der Tablix-Datenbereichsanzeige auf einer Berichtsseite (Berichts-Generator und SSRS)
  In diesem Thema werden die Eigenschaften für einen Tablix-Datenbereich beschrieben, die Sie modifizieren können, um die Darstellung eines Tablix-Datenbereichs bei der Anzeige des Datenbereichs in einem Bericht zu ändern.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="controlling-the-appearance-of-data"></a>Steuern der Darstellung von Daten  
 Mit den folgenden Funktionen kann die Darstellung eines Tablix-Datenbereichs gesteuert werden:  
  
-   **Formatieren von Daten.** Um Daten in einer Tabelle, Matrix oder Liste zu formatieren, legen Sie die Formateigenschaften des Textfelds in der Zelle fest. Sie können Eigenschaften für mehrere Zellen gleichzeitig festlegen. Um Daten in einem Diagramm zu formatieren, legen Sie Formatierungseigenschaften für die Reihe fest. Weitere Informationen finden Sie unter [Formatieren von Berichtselementen (Berichts-Generator und SSRS)](formatting-report-items-report-builder-and-ssrs.md) und [Formatieren eines Diagramms (Berichts-Generator und SSRS)](formatting-a-chart-report-builder-and-ssrs.md).  
  
-   **Schreiben von Ausdrücken**. Weitere Informationen finden Sie unter [Ausdrucksverwendungen in Berichten (Berichts-Generator und SSRS)](expression-uses-in-reports-report-builder-and-ssrs.md) und [Beispiele für Ausdrücke (Berichts-Generator und SSRS)](expression-examples-report-builder-and-ssrs.md).  
  
-   **Steuern der Sortierreihenfolge**. Um die Sortierreihenfolge zu steuern, müssen Sie Sortierungsausdrücke für den Datenbereich definieren. Um die Sortierreihenfolge für Zeilen und Spalten zu steuern, die einer Gruppe zugeordnet sind, müssen Sie Sortierungsausdrücke für die Gruppe, einschließlich der Detailgruppen, definieren. Sie können auch interaktive Sortierschaltflächen hinzufügen, um Benutzern zu ermöglichen, einen Tablix-Datenbereich oder dessen Gruppen zu sortieren. Weitere Informationen finden Sie unter [Sortieren von Daten in einem Datenbereich (Berichts-Generator und SSRS)](sort-data-in-a-data-region-report-builder-and-ssrs.md).  
  
-   **Anzeigen einer Meldung, wenn keine Daten vorhanden sind**. Wenn zur Laufzeit keine Daten für ein Berichtsdataset vorhanden sind, können Sie eine eigene Meldung schreiben, die statt des Datenbereichs angezeigt werden soll. Weitere Informationen finden Sie unter [Festlegen einer Meldung über fehlende Daten für einen Datenbereich &#40;Berichts-Generator und SSRS&#41;](../report-data/set-a-no-data-message-for-a-data-region-report-builder-and-ssrs.md).  
  
-   **Bedingtes Ausblenden von Daten**. Sie können die Hidden-Eigenschaft auf festgelegt, um bedingt zu steuern, ob ein Datenbereich oder Teile eines Datenbereichs angezeigt oder ausgeblendet, `True` oder auf einen Ausdruck. Ausdrücke können Verweise auf Berichtsparameter enthalten. Sie können auch ein Element zum Ein-/Ausschalten angeben, sodass die Benutzer entscheiden können, ob Detaildaten angezeigt werden sollen. Weitere Informationen finden Sie unter [Drilldownaktion &#40;Berichts-Generator und SSRS&#41;](drilldown-action-report-builder-and-ssrs.md).  
  
-   **Zusammenführen von Zellen.** Mehrere zusammenhängende Zellen in einer Tabelle können zu einer einzelnen Zelle kombiniert werden. Dies wird als mehrere Spalten überspannende Zellen oder Zusammenführung von Zellen bezeichnet. Zellen können nur horizontal oder vertikal kombiniert werden. Wenn Sie Zellen zusammenführen, bleiben nur die Daten in der ersten Zelle erhalten. Daten in anderen Zellen werden entfernt. Zusammengeführte Zellen können in ihre ursprünglichen Spalten aufgeteilt werden. Weitere Informationen finden Sie unter [Zusammenführen von Zellen in einem Datenbereich (Berichts-Generator und SSRS)](merge-cells-in-a-data-region-report-builder-and-ssrs.md).  
  
## <a name="controlling-tablix-data-region-position-and-expansion-on-a-page"></a>Steuern von Position und Erweiterung des Tablix-Datenbereichs auf einer Seite  
 Mit den folgenden Funktionen kann die Darstellung eines Tablix-Datenbereichs in einem gerenderten Bericht gesteuert werden:  
  
-   **Das Steuern von der Position eines Tablix-Datenbereichs in Verhältnis zu anderen Berichtselementen**. Ein Tablix-Datenbereich kann über, neben oder unter anderen Berichtselementen auf der Berichtsentwurfsoberfläche positioniert werden. Zur Laufzeit erweitert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nach Bedarf den Tablix-Datenbereich für die Daten, die für das verknüpfte Dataset abgerufen werden, und verschiebt ggf. Peer-Berichtselemente weiter nach außen. Um ein Tablix-Element neben einem anderen Berichtselement zu verankern, müssen Sie die Berichtselemente als Peers festlegen und ihre relativen Positionen anpassen. Weitere Informationen finden Sie unter [Renderingverhalten &#40;Berichts-Generator und SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).  
  
-   **Ändern der Erweiterungsrichtung**. Um zu steuern, ob ein Tablix-Datenbereich von links nach rechts (LTR) oder von rechts nach links (RTL) über die Breite der Seite erweitert wird, verwenden Sie die Direction-Eigenschaft, auf die über das Eigenschaftenfenster zugegriffen werden kann. Weitere Informationen finden Sie unter [Rendern von Datenbereichen (Berichts-Generator und SSRS)](rendering-data-regions-report-builder-and-ssrs.md).  
  
## <a name="controlling-how-a-tablix-data-region-renders-on-a-page"></a>Steuern, wie ein Tablix-Datenbereich auf einer Seite gerendert wird  
 In der folgenden Liste wird beschrieben, wie Sie die Anzeige eines Tablix-Datenbereichs in einem Bericht steuern können:  
  
-   **Steuern der Paginierung**. Um den Umfang der Daten zu steuern, die pro Berichtsseite angezeigt werden, können Sie Seitenumbrüche für Datenbereiche festlegen. Sie können auch Seitenumbrüche für Gruppen festlegen. Seitenumbrüche können sich auf die Leistung von bedarfsgesteuertem Rendering auswirken, wenn sich der Umfang der Daten verringert, der pro Seite verarbeitet werden muss. Weitere Informationen finden Sie unter [Paginierung in Reporting Services (Berichts-Generator und SSRS)](pagination-in-reporting-services-report-builder-and-ssrs.md) und [Hinzufügen eines Seitenumbruchs (Berichts-Generator und SSRS)](add-a-page-break-report-builder-and-ssrs.md).  
  
-   **Anzeigen von Daten auf beiden Seiten der Zeilenköpfe**. Zeilenköpfe müssen nicht unbedingt an der Seite eines Tablix-Datenbereichs angezeigt werden. Sie können die Zeilenköpfe zwischen Spalten verschieben, sodass Datenspalten vor den Zeilenköpfen angezeigt werden. Ändern Sie dazu die GroupsBeforeRowHeaders-Eigenschaft für die Matrix. Sie können auf diese Eigenschaft über das Eigenschaftenfenster zugreifen. Der Wert für diese Eigenschaft ist eine ganze Zahl; durch den Wert 2 werden beispielsweise zwei Gruppeninstanzen von Datenbereichsspalten-Daten vor der Spalte mit den Zeilenköpfen angezeigt.  
  
## <a name="controlling-how-tablix-row-and-column-groups-render"></a>Steuernd, wie Tablix-Zeilen- und -Spaltengruppen gerendert werden  
 Die Steuerung, wie ein Tablix-Datenbereich gerendert wird, hängt von den Gruppenstrukturen ab. Ein Tablix-Datenbereich kann vier Bereiche enthalten, wie in der folgenden Abbildung dargestellt:  
  
 ![Tablix data region areas](../media/rs-tablixareas.gif "Tablix data region areas")  
  
 Der Zeilengruppenbereich und der Spaltegruppenbereich enthalten Gruppenköpfe. Wenn ein Tablix-Datenbereich Gruppenheader hat, steuern Sie, wie Zeilen und Spalten wiederholt werden, indem Sie auf der Seite **Allgemein** des Dialogfelds **Tablix-Eigenschaften** Eigenschaften festlegen.  
  
 Wenn der Tablix-Datenbereich nur einen Tablix-Textbereich enthält, sind keine Gruppenheader vorhanden. Es gibt nur statische und dynamische Tablix-Elemente. Ein statisches Element wird einmal bezogen auf eine Tablix-Zeilengruppe oder -Spaltengruppe angezeigt. Ein dynamisches Element wird für jeden eindeutigen Gruppenwert einmal wiederholt. Beispiel: In einem Tablix-Datenbereich, in dem eine Bestellung angezeigt wird, können die Spaltennamen in der Bestellung in einem statischen Zeilenelement angezeigt werden. Jede Zeile in der Bestellung wird in einem dynamischen Zeilenelement angezeigt.  
  
 Sie können bestimmen, wie ein Tablix-Element gerendert wird, indem Sie Eigenschaften im Eigenschaftenbereich festlegen. Weitere Informationen finden Sie unter „Erweiterter Modus“ in [Gruppierungsbereich (Berichts-Generator)](grouping-pane-report-builder.md).  
  
 In der folgenden Liste wird beschrieben, wie Sie die Anzeige eines Tablix-Datenbereichs in einem Bericht steuern können:  
  
-   **Wiederholen von Zeilen- und Spaltenköpfen auf mehreren Seiten.** Sie können Zeilen- und Spaltenköpfe auf jeder Seite eines Tablix-Datenbereichs anzeigen. Weitere Informationen finden Sie unter [Anzeigen von Zeilen- und Spaltenüberschriften auf mehreren Seiten &#40;Berichts-Generator und SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).  
  
-   **Beibehalten von Zeilen- und Spaltenköpfen in der Ansicht beim Durchführen eines Bildlaufs.** Sie können steuern, ob die Zeilen- und Spaltenköpfe in einer Ansicht beibehalten werden, wenn Sie in einem Browser einen Bildlauf für einen Bericht durchführen. Weitere Informationen finden Sie unter [Sichtbarhalten von Kopfzeilen beim Scrollen durch einen Bericht (Berichts-Generator und SSRS)](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).  
  
 Weitere Informationen darüber, wie sich das Exportieren eines Berichts in unterschiedliche Formate auf das Rendern eines Tablix-Datenbereichs auf einer Seite auswirkt, finden Sie unter [Renderingverhalten (Berichts-Generator und SSRS)](rendering-behaviors-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verknüpfen mehrerer Datenbereiche mit einem Dataset &#40;Berichts-Generator und SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)   
 [Geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)   
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)   
 [Steuern von Seitenumbrüchen, Überschriften, Spalten und Zeilen &#40;Berichts-Generator und SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
