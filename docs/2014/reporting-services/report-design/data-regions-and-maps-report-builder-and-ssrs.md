---
title: Datenbereiche und Karten (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data regions
ms.assetid: 3afb8874-b36c-4e44-a0d8-80d2f7135fb1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0b9722ad68107c626f0b4e569ac6e7cbf8c3bf8
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66106089"
---
# <a name="data-regions-and-maps-report-builder-and-ssrs"></a>Datenbereiche und Karten (Berichts-Generator und SSRS)
  Ein Datenbereich ist ein Objekt in einem Bericht, der Daten aus einem Berichtsdataset anzeigt. Berichtsdaten können als Zahlen und Text in einer Tabelle, Matrix oder Liste, grafisch in einem Diagramm oder einem Messgerät und vor einem geografischen Hintergrund in einer Karte angezeigt werden. Tabellen, Matrizen und Listen basieren auf dem *Tablix* -Datenbereich, der bei Bedarf erweitert wird, um alle Daten aus dem Dataset anzuzeigen. Ein Tablix-Datenbereich unterstützt mehrere Zeilen- und Spaltengruppen mit statischen und dynamischen Zeilen und Spalten. In einem Diagramm werden mehrere Reihen und Kategoriegruppen in einer Vielzahl von Diagrammformaten angezeigt. In einem Messgerät wird ein einzelner Wert oder ein aggregierter Wert für ein Dataset angezeigt. In einer Karte werden räumliche Daten in Form von Kartenelementen angezeigt, deren Darstellung abhängig von den aggregierten Daten aus einem Dataset variieren kann.  
  
 Sie können einen Datenbereich oder eine Karte als Berichtsteil speichern. [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="table"></a>Tabelle  
 Eine Tabelle ist ein Datenbereich, in dem die Daten zeilenweise dargestellt werden. Tabellenspalten sind statisch: Sie bestimmen die Anzahl von Spalten, wenn Sie den Bericht entwerfen. Tabellenzeilen sind dynamisch: sie werden nach unten erweitert, um die Daten aufzunehmen. Sie können zu den Tabellen Gruppen hinzufügen, die die Daten nach ausgewählten Feldern oder Ausdrücken zusammenfassen. Weitere Informationen zum Hinzufügen einer Tabelle zu einem Bericht finden Sie unter [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md).  
  
## <a name="matrix"></a>Matrix  
 Eine Matrix wird auch als Kreuztabelle bezeichnet. Ein Matrixdatenbereich enthält dynamische Zeilen und Spalten: sie werden zur Aufnahme der Daten erweitert. Eine Matrix kann dynamische Spalten und Zeilen und statische Spalten und Zeilen enthalten. Spalten oder Zeilen können in anderen Spalten oder Zeilen enthalten sein, die zur Gruppierung von Daten verwendet werden können. Informationen zum Hinzufügen einer Matrix zu einem Bericht finden Sie unter [Matrizen &#40;Berichts-Generator und SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)  
  
## <a name="list"></a>Liste  
 Eine Liste ist ein Datenbereich, in dem Daten frei angeordnet dargestellt werden. Sie können Berichtselemente zu einem Formular anordnen, indem Sie Textfelder, Bilder und andere Datenbereiche beliebig in der Liste platzieren. Informationen zum Hinzufügen einer Liste zu einem Bericht finden Sie unter [listet &#40;Berichts-Generator und SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
## <a name="chart"></a>Diagramm  
 Ein Diagramm stellt Daten grafisch dar. Beispiele für Diagramme sind Balken-, Kreis- und Liniendiagramme, es werden jedoch weit mehr Arten unterstützt. Informationen zum Hinzufügen eines Diagramms zu einem Bericht finden Sie unter [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
## <a name="gauge"></a>Messgerät  
 Ein Messgerät präsentiert Daten als Bereich mit einem Indikator, der auf einen bestimmten Wert innerhalb des Bereichs zeigt. Messgeräte werden verwendet, um Key Performance Indicators (KPIs) und andere Daten anzuzeigen. Beispiele für Messgeräte umfassen lineare und runde Ausführungen. Weitere Informationen zum Hinzufügen eines Messgeräts zu einem Bericht finden Sie unter [Messgeräte &#40;Berichts-Generator und SSRS&#41;](gauges-report-builder-and-ssrs.md).  
  
## <a name="map"></a>Zuordnung  
 Mit einer Karte können Daten vor einem geografischen Hintergrund präsentiert werden. Kartendaten können räumliche Daten aus einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Abfrage, einer ESRI-Shape-Datei oder aus [!INCLUDE[msCoName](../../includes/msconame-md.md)] Bing-Kartenkacheln sein. Räumliche Daten bestehen aus Sätzen von Koordinaten zur Definition von Polygonen, die Formen oder Bereiche darstellen, von Linien, die Routen oder Pfade darstellen, und von Punkten, die durch Marker dargestellt werden. Sie können aggregierte Daten Kartenelementen zuordnen, um deren Farbe und Größe automatisch zu verändern. So kann der Markertyp für ein Geschäft auf Grundlage der Umsätze oder die Farbe für eine Straße auf Grundlage der Geschwindigkeitsbegrenzung variieren. Weitere Informationen finden Sie unter [Karten &#40;Berichts-Generator und SSRS&#41;](maps-report-builder-and-ssrs.md).  
  
## <a name="data-regions-in-the-report-layout"></a>Datenbereiche im Berichtslayout  
 Sie können mehrere Datenbereiche zu einem Bericht hinzufügen. Datenbereiche können größer werden, um die Daten aus dem Berichtsdataset aufzunehmen, mit denen sie verknüpft sind. Eine Matrix, in der beispielsweise Verkäufe für jedem Produkt nach Jahr angezeigt werden, weist z. B. eine Zeilengruppe basierend auf Produktnamen und eine Spaltengruppe basierend auf Jahren auf. Wenn Sie den Bericht ausführen, erweitert sich die Matrix für jedes Produkt nach unten und für jedes Jahr zur Seite. Ein Diagramm, das sich in der Berichtsentwurfsoberfläche neben der Matrix befindet, wird im gerenderten Bericht neben der erweiterten Matrix angezeigt. Die Art und Weise, wie Datenbereiche auf einer Seite gerendert werden, folgt einem Satz von Regeln basierend auf dem Ausgabeformat eines Berichts. Um beispielsweise zu steuern, wie ein Diagramm und eine Matrix auf einer Seite gerendert werden, können Sie ein Rechteck als Container verwenden oder beide Datenbereiche in einer Liste schachteln. Weitere Informationen finden Sie unter [Seitenlayout und Rendering &#40;Berichts-Generator und SSRS&#41;](page-layout-and-rendering-report-builder-and-ssrs.md)speichern.  
  
## <a name="nested-data-regions"></a>Geschachtelte Datenbereiche  
 Sie können Datenbereiche ineinander schachteln. Möchten Sie beispielsweise für jeden Vertriebsmitarbeiter in einer Datenbank einen Umsatzdatensatz erstellen, können Sie eine Liste mit Textfeldern und einem Bild zur Anzeige von Informationen zu dem Mitarbeiter erstellen. Anschließend fügen Sie der Liste Tabellen- und Diagrammdatenbereiche hinzu, um den Umsatzdatensatz des Mitarbeiters darzustellen. Weitere Informationen finden Sie unter [Geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).  
  
## <a name="multiple-data-regions-linked-to-the-same-dataset"></a>Mehrere mit dem gleichen Dataset verknüpfte Datenbereiche  
 Sie können mehr als einen Datenbereich mit dem gleichen Dataset verknüpfen, um andere Sichten der gleichen Daten bereitzustellen. Zum Beispiel können Sie die gleichen Daten in einer Tabelle und einem Diagramm anzeigen. Sie können den Bericht mit interaktiven Sortierungsschaltflächen in der Tabelle erstellen. Wenn Sie die Tabelle sortieren, wird das Diagramm auf diese Weise ebenfalls automatisch sortiert. Weitere Informationen finden Sie unter [Verknüpfen mehrerer Datenbereiche mit einem Dataset &#40;Berichts-Generator und SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md).  
  
## <a name="data-for-a-data-region"></a>Daten für einen Datenbereich  
 Jedes Tablix, Diagramm und Messgerät ist so ausgelegt, dass Daten von einem einzelnen Dataset angezeigt werden. In einer Karten werden räumliche Daten und analytische Daten aus demselben Dataset oder aus unterschiedlichen Datasets angezeigt. Sie können auch Werte aus Datasets einschließen, die nicht mit dem Datenbereich verknüpft sind, indem Sie folgendermaßen vorgehen:  
  
-   Aggregieren Sie die Werte, die nicht von der Sortierreihenfolge oder Gruppierung abhängig sind, die sich in einem anderen Dataset befinden.  
  
-   Suchen Sie Werte aus Name-Wert-Paaren in einem anderen Dataset.  
  
 Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Berichterstellungskonzepte &#40;Berichts-Generator und SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Berichte, Berichtsteile und Berichtsdefinitionen &#40;Berichts-Generator und SSRS&#41;](reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)   
 [Seitenlayout und Rendering (Berichts-Generator und SSRS)](page-layout-and-rendering-report-builder-and-ssrs.md)   
 [Lernprogramme &#40;Berichts-Generator&#41;](../report-builder-tutorials.md)   
 [Reporting Services-Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
