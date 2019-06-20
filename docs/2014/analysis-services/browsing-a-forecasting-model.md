---
title: Durchsuchen eines Planungsmodells | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- forecasting [data mining]
- mining models, viewing
- mining model, time series
- time series [data mining]
ms.assetid: ad35a528-1949-4048-8678-3b9760c1c88c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 830aea002e8000feeda061f42af9084696ed6fe8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66088491"
---
# <a name="browsing-a-forecasting-model"></a>Durchsuchen eines Planungsmodells
  Beim Öffnen eines forecasting-Modells mit **Durchsuchen**, das Modell wird angezeigt, in einem interaktiven Viewer, ähnlich wie die Time Series-Modell-Viewer in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Mithilfe des Viewers können Sie Trends untersuchen, Reihen vergleichen, Vorhersagen erstellen und Informationen zum Modell und zu den zugrunde liegenden Daten abrufen.  
  
##  <a name="bkmk_Top"></a> Durchsuchen des Modells  
 Die **Durchsuchen** Viewer für Planungsmodelle stellt eine Diagrammsicht, die zeigt Trends im Lauf der Zeit, und ermöglicht Ihnen das Erstellen von Vorhersagen, und eine Modellansicht, die der Zeitreihe als Entscheidungs- oder regressionsstruktur darstellt.  
  
-   [Diagrammansicht](#bkmk_charts)  
  
-   [Modellansicht](#bkmk_Model)  
  
 Um mit einem Planungsmodell zu experimentieren, können Sie die Beispieldaten auf der Registerkarte "Planung" der beispieldatenarbeitsmappe verwenden und erstellen Sie ein Zeitreihenmodell mit den [prognostizieren Assistenten &#40;Data Mining-Add-ins für Excel&#41; ](forecast-wizard-data-mining-add-ins-for-excel.md) in die  **Datamining** Menüband oder [prognostizieren &#40;Tabellenanalysetools für Excel&#41; ](forecast-table-analysis-tools-for-excel.md) in die **analysieren** Menüband.  
  
###  <a name="bkmk_charts"></a> Diagramm  
 Die **Diagramm** Registerkarte zeigt den Trend in der Datenreihe im Laufe der Zeit sowie die vorhergesagten Werte. Die vertikale Achse des Diagramms stellt die Werte der Reihe dar, und die horizontale Achse stellt die Zeit.  
  
##### <a name="explore-the-forecasting-chart"></a>Untersuchen des Prognosediagramms  
  
1.  Dieses Modell enthält mehrere Zeitreihen. Um das Diagramm jedoch zu vereinfachen, können Sie eine einzelne Reihe oder nur wenige aufeinander bezogene Reihen anzeigen.  
  
     ![vergangenheitsvorhersagen im Prognosemodell](media/dm13-forecast-chart-historicpredictions.gif "vergangenheitsvorhersagen im Prognosemodell")  
  
     Verwenden Sie die Kontrollkästchen, um die Vorhersage nur für Nordamerika oder nur für die Verkaufsmenge auszuwählen.  
  
2.  Klicken Sie auf **Vorhersageschritte** , und geben Sie ein neuer Wert zu steuern, wie viele zukünftige Werte im Diagramm angezeigt werden soll.  
  
     Der Standardwert ist 5.  
  
3.  Klicken Sie auf einem beliebigen Punkt in der Zeile, die entweder für vergangenheits- oder zukunftswerte, um die genauen Werte für diesen Punkt rechtzeitig, angezeigt der **Mininglegende**.  
  
4.  Im Diagramm werden Vergangenheits- und Zukunftsdaten angezeigt. Beachten Sie die gepunktete Linie mit einem schattierten Hintergrund. Diese Werte sind die künftigen Vorhersagen, die auf dem Modell basieren.  
  
     Die Vergangenheitsdaten (mit denen Sie das Modell erstellt haben) werden auf der linken Seite des Diagramms angezeigt.  
  
5.  Wählen Sie die **vergangene Vorhersagen anzeigen** Option aus, um ein Gefühl für die Stabilität der Zeitreihe zu erhalten.  
  
     ![Prognosen für eine einzelne Reihe im Modell](media/dm13-forecast-chart-singleseries.gif "Prognosen für eine einzelne Reihe im Modell")  
  
     Vergangene Vorhersagen sind Werte, die basierend auf der Reihe bis zum entsprechenden Zeitpunkt vorhergesagt wurden und die mit tatsächlichen Vergangenheitswerten verglichen werden. Wenn die gepunktete Linie (mit den vorhergesagten Werten) weit von der durchgezogenen Linie (die tatsächlichen Werte) entfernt ist, bedeutet das, dass der erste Teil der Reihe die späteren Werte vielleicht nicht genau vorhersagt. Möglicherweise sind mehr Daten erforderlich, oder es könnte lediglich ein Hinweis auf die Flüchtigkeit im Zyklus sein.  
  
6.  Wählen Sie die **Abweichungen anzeigen** Option aus, um Fehlerindikatoren im Diagramm anzuzeigen.  
  
     Mithilfe der Fehlerindikatoren können Sie die Variabilität der Vorhersagen visuell bewerten. Die Qualität der Vorhersagen hängt von den Quelldaten ab. Wenn Sie die Anzahl der Vorhersageschritte erhöhen, sollten Sie jedoch einen stetigen Anstieg der Abweichungen feststellen.  
  
 **Tipps**  
  
-   Zum Umschalten der Anzeige der **Mininglegende**, mit der rechten Maustaste in einem beliebigen Zeitpunkt im Diagramm.  
  
     Sie können einen bestimmten Zeitbereich anzeigen, indem Sie auf das Diagramm klicken, eine Zeitauswahl über das Diagramm ziehen und dann durch erneutes Klicken den ausgewählten Bereich vergrößern.  
  
-   Um eine Kopie des aktuellen Diagramms zu erhalten, klicken Sie auf **nach Excel kopieren**, klicken Sie dann auf ein Arbeitsblatt in Excel. Im Arbeitsblatt wird eine Grafik mit allen festgelegten Optionen eingefügt, einschließlich einer Legende.  
  
     Diese Grafik ist jedoch statisch, sodass nicht die Legende bearbeiten oder der zugrunde liegenden Daten anzeigen; Wenn Sie eine Diagrammsicht mehr interaktive benötigen, verwenden die [Visio Viewer](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
-   Klicken Sie auf **Abs** in der Menüleiste des Viewers, um zwischen absoluten und relativen Kurven umzuschalten.  
  
     Diese Option ist nützlich, falls das Diagramm mehrere Modelle enthält, die Skalierung der Daten der einzelnen Modelle sich jedoch erheblich unterscheidet.  
  
     Wenn zum Beispiel die Geschäfte in der Pazifikregion neu sind und wenig Verkäufe verzeichnen, und wenn absolute Werte verwendet werden, wird die Linie, die die Verkäufe der Pazifikregion darstellt, möglicherweise flach dargestellt und tatsächliche Änderungen sind nur schwer erkennbar. Die anderen Modelle würden in diesem Fall jedoch mit einer stärker normalisierten Skalierung angezeigt.  
  
     Durch den Wechsel zur Anzeige mit relativen Werten können Sie die Skalierung verschiedener Modelle normalisieren und Unterschiede als Änderungsprozentsatz anzeigen. Wenn Änderungen für jedes Modell relativ sind, können diese ohne signifikante Verzerrung in demselben Diagramm angezeigt werden.  
  
 [Durchsuchen des Modells](#bkmk_Top)  
  
###  <a name="bkmk_Model"></a> Model  
 Ein Planungsmodell kann auch als Entscheidungsstruktur oder, bei einer größtenteils linearen Reihe, als Regressionsmodell dargestellt werden.  
  
 In diesem Modell liegt zum Beispiel basierend auf einer bestimmten Bedingung ein Unterschied in der Regressionsformel vor, sodass die Struktur in zwei Verzweigungen mit einer jeweils unterschiedlichen Regressionsformel aufgeteilt wird.  
  
 ![Filtern einer einzelnen Reihe im Prognosemodell](media/dm13-forecast-model-northamerica.gif "Filtern einer einzelnen Reihe im Prognosemodell")  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a>Untersuchen des Prognosemodells als Struktur  
  
1.  Klicken Sie auf die **Struktur** Dropdownliste aus, und wählen Sie ein Miningmodell angezeigt.  
  
     Für jedes vorhersagbare Attribut wird eine separate Struktur oder ein Regressionsknoten angezeigt. Wenn Ihre Daten beispielsweise Verkäufe für Europa, Nordamerika und Pazifik enthalten, sind drei verschiedene Modelle vorhanden, eines für jede Datenreihe.  
  
2.  Ziehen Sie die **Ebene anzeigen** Schieberegler, um niedrigere Ebenen der Struktur zu filtern und auf die wichtigsten Teilungen konzentrieren.  
  
3.  Klicken Sie auf jeden Knoten, um aussagekräftigen statistische Daten im Anzeigen der **Mininglegende**.  
  
     Wenn Sie mit der Maus auf einen Knoten zeigen, zeigt die QuickInfo ebenfalls diese statistischen Daten sowie die vollständige Formel an, die den betreffenden Knoten beschreibt.  
  
4.  Sollten Sie kopieren Sie die Informationen in der **Mininglegende**, mit der rechten Maustaste die **Mininglegende**Option **kopieren**, und klicken Sie in das Excel-Arbeitsblatt. Die **nach Excel kopieren** Option wird im Diagramm nicht die Statistiken kopiert.  
  
 [Durchsuchen des Modells](#bkmk_Top)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
