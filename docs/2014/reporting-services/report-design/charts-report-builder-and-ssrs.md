---
title: Diagramme (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.chartareaproperties.3doptions.f1
- "10256"
- sql12.rtp.rptdesigner.charttitleproperties.general.f1
- "10166"
- sql12.rtp.rptdesigner.seriesproperties.axesandchartarea.f1
- sql12.rtp.rptdesigner.chartproperties.general.f1
- sql12.rtp.rptdesigner.seriesproperties.seriesdata.f1
- "10251"
- "10172"
ms.assetid: d56d0521-362f-4361-843a-acf2c897a87c
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: feab5870c703fbe253923006a6f6ba84c4959cdd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120040"
---
# <a name="charts-report-builder-and-ssrs"></a>Diagramme (Berichts-Generator und SSRS)
  Wenn Sie Daten in einem visuellen Format zusammenfassen möchten, verwenden Sie den Diagrammdatenbereich. Diagramme ermöglichen es Ihnen, große Mengen aggregierter Informationen auf einen Blick zu präsentieren. Wichtig ist eine sorgfältige Aufbereitung und Analyse der Daten, bevor Sie das Diagramm erstellen, da so eine schnelle und effiziente Gestaltung der Diagramme erleichtert wird. Weitere Informationen finden Sie unter [Hinzufügen eines Diagramms zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md). Um ein Diagramm umgehend verwenden finden Sie in der Balken-, Spalten-, Sparkline und Kreisdiagrammen unter [Tutorials &#40;Berichts-Generator&#41; ](../report-builder-tutorials.md) oder die Balken- und Kreisdiagrammen unter [Reporting Services-Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).  
  
 Die folgende Abbildung zeigt viele der verschiedenen Elemente, die im Diagramm verwendet werden.  
  
 ![Diagrammelemente](../media/rs-chartelementsc.gif "Chart elements diagram")  
  
 Diagramme können getrennt von einem Bericht als Berichtsteile veröffentlicht werden. [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="DesigningChart"></a> Entwerfen eines Diagramms  
 Nachdem Sie der Entwurfsoberfläche einen Diagrammdatenbereich hinzugefügt haben, können Sie Berichtsdataset-Felder für numerische und nicht numerische Daten in den Diagrammdatenbereich des Diagramms ziehen. Wenn Sie in der Entwurfsoberfläche auf das Diagramm klicken, wird der Diagrammdatenbereich mit drei untergeordneten Bereichen angezeigt: Kategoriegruppen, Reihengruppen und Werte. Wenn der Bericht über ein freigegebenes oder eingebettetes Dataset verfügt, werden die Felder im Dataset im Berichtsdatenbereich angezeigt. Ziehen Sie die Felder aus dem Dataset in den entsprechenden Bereich. Wenn einem Bereich des Diagramms ein Feld hinzugefügt wird, wird in der Standardeinstellung in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ein Aggregat für das Feld berechnet. Sie können auch die Reihengruppierung verwenden, um Reihen dynamisch zu generieren. Das Diagramm ist darüber hinaus eng mit der Matrix verknüpft.  
  
 ![rs_chartwSeriesCategories](../media/rs-chartwseriescategories.gif "rs_chartwSeriesCategories")  
  
> [!NOTE]  
>  Die Daten im Diagramm unterscheiden sich zur Entwurfszeit von den Daten im Diagramm, wenn der Bericht verarbeitet wird. Es ist nicht die wirklichen Daten. Es handelt sich um generierte Daten, die hinzugefügt wurden, damit Sie das Diagramm zur Entwurfszeit mit einer Vorstellung von dessen tatsächlicher Darstellung erstellen können.  
  
  
  
##  <a name="SimilarMatrix"></a> Ähnlichkeiten mit einer Matrix  
 Eine Möglichkeit, die Funktionsweise von Diagrammen zu veranschaulichen, ist der Vergleich mit Matrizen.  
  
 ![Neue Matrix aus Toolbox hinzugefügt, markiert](../media/rs-matrixtemplatenewselected.gif "New Matrix added from Toolbox, selected")  
  
 Begrifflich ist ihre Organisation identisch:  
  
-   Die Spaltengruppe in der Matrix ist mit dem Kategoriegruppenbereich im Diagramm identisch.  
  
-   Die Zeilengruppe in der Matrix ist mit dem Reihengruppenbereich im Diagramm identisch.  
  
-   Der Datenbereich in der Matrix ist mit dem Wertebereich im Diagramm identisch.  
  
 
  
##  <a name="AddingData"></a> Hinzufügen von Daten zum Diagramm  
 Angenommen, Sie verfügen über einen Bericht, in dem der Vertrieb nach Namen anzeigt wird. Sie legen das Feld Vollständiger Name im Kategoriegruppenbereich und das Feld Vertrieb im Wertebereich ab.  
  
 Wenn Sie das Feld Vertrieb im Wertebereich ablegen, wird der Text des Datenfelds in der Legende angezeigt, und die Daten aus diesem numerischen Feld werden zu einem einzelnen Wert aggregiert. Standardmäßig wird der Wert mit der integrierten Funktion SUM aggregiert. Der Diagrammdatenbereich enthält einen einfachen Ausdruck für das Feld. Im Beispiel wird `[Sum(Sales)]` für den Feldausdruck `=Sum(Fields!Sales.Value)`angezeigt. Wenn keine Gruppen angegeben werden, zeigt das Diagramm nur einen Datenpunkt an. Um mehrere Datenpunkte anzuzeigen, müssen Sie die Daten gruppieren, indem Sie ein Gruppierungsfeld hinzufügen. Wenn Sie das Feld Name dem Kategoriegruppenbereich hinzufügen, wird dem Diagramm automatisch ein Gruppierungsfeld mit demselben Namen wie das Feld hinzugefügt. Wenn Felder hinzugefügt werden, in denen Werte entlang der x- und y-Achse definiert werden, verfügt das Diagramm über genügend Informationen, um die Daten korrekt zu zeichnen.  
  
 ![rs_chartwNoSeries](../media/rs-chartwnoseries.gif "rs_chartwNoSeries")  
  
 Wenn der Reihengruppenbereich leer bleibt, wird die Anzahl der Reihen zur Entwurfszeit festgelegt. In diesem Beispiel ist Vertrieb die einzige im Diagramm angezeigte Reihe.  
  
  
  
##  <a name="GroupsInChart"></a> Kategorie- und Reihengruppen in einem Diagramm  
 Diagramme unterstützen geschachtelte Kategorie- und Reihengruppen. In Diagrammen werden keine Detaildaten angezeigt. Fügen Sie Gruppen einem Diagramm hinzu, indem Sie Datasetfelder in die Kategorie- und Reihenablagezonen für ein ausgewähltes Diagramm ziehen.  
  
 Formdiagramme, z. B. Kreisdiagramme, unterstützen Kategoriegruppen und geschachtelte Kategoriegruppen. Andere Diagramme, z. B. Balkendiagramme, unterstützen Kategoriegruppen und Reihengruppen. Sie können Gruppen schachteln, müssen jedoch sicherstellen, dass die Anzahl der Kategorien oder Reihen nicht die Lesbarkeit der Informationen im Diagramm erschwert.  
  
### <a name="adding-series-grouping-to-a-chart"></a>Hinzufügen einer Reihengruppierung zu einem Diagramm  
 Wenn Sie dem Reihengruppenbereich ein Feld hinzufügen, hängt die Anzahl der Reihen von den im Feld enthaltenen Daten ab. Gehen Sie vom bereits weiter oben vorgestellten Beispiel aus, und nehmen Sie an, dass Sie dem Reihengruppenbereich das Feld Jahr hinzufügen. Die Anzahl der Werte im Feld Jahr bestimmt die Anzahl der im Diagramm angezeigten Reihen. Wenn das Feld Jahr die Jahre 2004, 2005 und 2006 enthält, werden im Diagramm drei Reihen für jedes Feld im Wertebereich angezeigt.  
  
  
  
##  <a name="DatasetConsiderations"></a> Überlegungen zu Datasets vor dem Erstellen eines Diagramms  
 Diagramme stellen eine Zusammenfassungsansicht Ihrer Daten bereit. Bei großen Datasets können die Informationen in einem Diagramm jedoch verdeckt oder unlesbar werden. So können fehlende oder NULL-Datenpunkte, für einen Diagrammtyp schlecht geeignete Datentypen sowie erweiterte Anwendungen, wie das Kombinieren von Diagrammen mit Tabellen, die Lesbarkeit eines Diagramms beeinträchtigen. Bevor Sie ein Diagramm erstellen, sollten Sie daher Ihre Daten sorgfältig aufbereiten und analysieren, sodass Sie Ihre Diagramme schnell und effizient gestalten können.  
  
 Sie können einem Bericht so viele Diagramme hinzufügen, wie Sie möchten. Ein Diagramm ist wie jeder andere Datenbereich, z. B. eine Matrix oder eine Tabelle, an ein einzelnes Dataset gebunden. Wenn Sie mehrere Datasets in einem Diagramm anzeigen möchten, können Sie ein zusätzliches Dataset erstellen, das eine JOIN oder UNION-Anweisung in der SQL-Abfrage verwendet, bevor Sie dem Diagramm Daten hinzufügen. Weitere Informationen über die JOIN- und UNION-Anweisungen finden Sie in der Onlinedokumentation oder einer anderen SQL-Referenz.  
  
 Ziehen Sie in Betracht, die Daten in der Datasetabfrage vorab zu aggregieren, falls keine detaillierten Daten notwendig oder nützlich sind. Verringern Sie die Anzahl der Kategorien im Dataset, um die einzelnen Datenpunkte eindeutiger anzuzeigen. Sie können das Dataset filtern oder der Abfrage eine Bedingung hinzufügen, die die Anzahl der zurückgegebenen Zeilen reduziert.  
  
##  <a name="BestPractices"></a> Bewährte Methoden für das Anzeigen von Daten in einem Diagramm  
 Diagramme sind höchst effektiv, wenn die Anzahl der angezeigten Elemente ein klares Bild der zugrunde liegenden Informationen ergibt. Manche Diagramme, wie Punktdiagramme, profitieren von zahlreichen Datenpunkten, während andere Diagramme, wie Kreisdiagramme, mit weniger Datenpunkten besser wirken. Daher sollten Sie bei der Auswahl des Diagrammtyps sorgfältig vorgehen und berücksichtigen, welche Werte in Ihrem Dataset enthalten sind und wie diese Informationen angezeigt werden sollen. Weitere Informationen finden Sie unter [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md).  
  
 Es gibt mehrere Methoden, um Daten in einem Diagramm zu konsolidieren:  
  
-   Wenn Sie ein Kreisdiagramm verwenden, können Sie kleinere Slices zu einem Slice mit dem Namen "Andere" zusammenfassen. Dadurch wird die Anzahl der Slices im Kreisdiagramm verringert. Weitere Informationen finden Sie unter [Zusammenfassen von kleinen Slices in einem Kreisdiagramm &#40;Berichts-Generator und SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md).  
  
-   Vermeiden Sie es, Datenpunktbezeichnungen zu verwenden, wenn zahlreiche Datenpunkte vorhanden sind. Datenpunktbezeichnungen sind höchst effektiv, wenn das Diagramm nur wenige Punkte enthält.  
  
-   Filtern Sie unerwünschte oder irrelevante Daten. Dies hilft Ihnen, die Schlüsseldaten hervorzuheben, die Sie im Diagramm aufzeigen möchten. Um Datenpunkte in einem Diagramm zu filtern, legen Sie einen Filter für eine Kategoriegruppe oder eine Reihengruppe fest. Standardmäßig verwendet das Diagramm die integrierte Sum-Funktion, um Werte, die zur selben Gruppe gehören, in einem einzelnen Datenpunkt in der Reihe zu aggregieren. Falls Sie die Aggregatfunktion einer Reihe ändern, müssen Sie auch die Aggregatfunktion im Filterausdruck ändern. Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
-   Wenn Sie Verhältnisdaten in einer Tabellen- oder Matrixvorlage darstellen möchten, sollten Sie erwägen, anstelle eines Balkendiagramms ein lineares Messgerät zu verwenden. Messgeräte sind besser geeignet, einzelne Werte innerhalb einer Zelle darzustellen. Weitere Informationen finden Sie unter [Geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).  
  
  
  
##  <a name="AggregateValues"></a> Aggregieren von Werten von einem Datenfeld im Diagramm  
 Wenn dem Wertebereich des Diagramms ein Feld hinzugefügt wird, wird in der Standardeinstellung in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ein Aggregat für das Feld berechnet. Wenn Sie ein Feld auf das Diagramm ziehen, ohne das Feld in einem bestimmten Bereich abzulegen, bestimmt das Diagramm anhand des Datentyps für das Feld, ob dieses Feld zur Kategorie- (x-) oder Wertachse (y-Achse) gehört. Numerische Felder, die im Wertebereich abgelegt werden, werden mit der SUM-Funktion aggregiert. Wenn der Datentyp des Wertefelds im Wertebereich String lautet, kann das Diagramm auch dann keinen numerischen Wert anzeigen, wenn sich in den Feldern Zahlen befinden. Im Diagramm wird daher die COUNT-Funktion angezeigt. Zur Vermeidung dieses Verhaltens sollten Sie sicherstellen, dass die verwendeten Felder numerische Datentypen und keine Zeichenfolgen mit formatierten Zahlen aufweisen. Sie können einen Visual Basic-Ausdruck Zeichenfolgenwerte in einen Typ mit numerischen Daten konvertieren die `CDbl` oder `CInt` Konstanten. Zum Beispiel wird mit dem folgenden komplexen Ausdruck das Feld `MyField` mit als Zeichenfolgen formatierten numerischen Werten konvertiert.  
  
 `=Sum(CDbl(Fields!MyField.Value))`  
  
 Weitere Informationen zu Aggregatausdrücken finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
  
  
##  <a name="InThisSection"></a> In diesem Abschnitt  
 [Hinzufügen eines Diagramms zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
 Beschreibt die ersten Schritte beim Hinzufügen eines Diagramms zum Bericht.  
  
 [Diagrammtypen &#40;Berichts-Generator und SSRS&#41;](chart-types-report-builder-and-ssrs.md)  
 Beschreibt alle in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] verfügbaren Diagrammtypen und -untertypen, einschließlich Überlegungen und bewährten Vorgehensweisen zur Verwendung der verschiedenen Diagrammtypen.  
  
 [Formatieren eines Diagramms &#40;Berichts-Generator und SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)  
 Verwenden Sie Formatierungen, um die Gesamtdarstellung zu verbessern und wichtige Datenpunkte des Diagramms hervorzuheben.  
  
 [Leere und Null-Datenpunkte in Diagrammen &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
 Beschreibt Überlegungen beim Arbeiten mit Diagrammen, die auf Feldern mit leeren oder NULL-Werten basieren.  
  
 [Anzeigen einer Reihe mit mehreren Datenbereichen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md)  
 Beschreibt das Hinzufügen von Skalierungsunterbrechungen zu einer Reihe mit mehreren Datenbereichen.  
  
 [Mehrere Reihen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)  
 Beschreibt verschiedene Methoden zum Anzeigen mehrerer Reihen in einem Diagramm, einschließlich der Kombination von Diagrammtypen, der Verwendung der sekundären Achse, dem Angeben verschiedener Diagrammtypen und der Verwendung mehrerer Diagrammbereiche.  
  
 [Verknüpfen mehrerer Datenbereiche mit dem gleichen Dataset &#40;Berichts-Generator und SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)  
 Stellt verschiedene Ansichten der Daten aus dem gleichen Berichtsdataset bereit.  
  
 [Hinzufügen oder Löschen einer Gruppe in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](add-or-delete-a-group-in-a-chart-report-builder-and-ssrs.md)  
 Beschreibt das Hinzufügen von Gruppen und geschachtelten Gruppen zu einem Diagramm.  
  
 [Hinzufügen eines gleitenden Durchschnitts zu einem Diagramm &#40;Berichts-Generator und SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
 Beschreibt die Verwendung der Formel "Gleitender Durchschnitt" zum Berechnen des Mittelwerts der Daten in der Reihe.  
  
 [Problembehandlung bei Diagrammen &#40;Berichts-Generator und SSRS&#41;](troubleshoot-charts-report-builder-and-ssrs.md)  
 Tipps zum Arbeiten mit Diagrammen.  
  
## <a name="see-also"></a>Siehe auch  
 [Bilder, Textfelder, Rechtecke und Linien &#40;Berichts-Generator und SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [Interaktive Sortierung, Dokumentstrukturen und Links &#40;Berichts-Generator und SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [Geschachtelte Datenbereiche &#40;Berichts-Generator und SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)   
 [Tutorial: Hinzufügen eines Säulendiagramms zu einem Bericht (Berichts-Generator)](../tutorial-add-a-column-chart-to-your-report-report-builder.md)   
 [Tutorial: Hinzufügen eines Kreisdiagramms zu einem Bericht (Berichts-Generator)](../tutorial-add-a-pie-chart-to-your-report-report-builder.md)   
 [Tutorial: Hinzufügen eines Balkendiagramms zu einem Bericht (Berichts-Generator)](../tutorial-add-a-bar-chart-to-your-report-report-builder.md)  
  
  
