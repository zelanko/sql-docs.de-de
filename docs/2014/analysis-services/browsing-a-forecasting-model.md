---
title: Durchsuchen eines Vorhersagemodells | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66088491"
---
# <a name="browsing-a-forecasting-model"></a>Durchsuchen eines Planungsmodells
  Wenn Sie ein Vorhersagemodell mithilfe von **Durchsuchen**öffnen, wird das Modell in einem interaktiven Viewer angezeigt, der dem Zeitreihen Modell [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Viewer in ähnelt. Mithilfe des Viewers können Sie Trends untersuchen, Reihen vergleichen, Vorhersagen erstellen und Informationen zum Modell und zu den zugrunde liegenden Daten abrufen.  
  
##  <a name="bkmk_Top"></a>Untersuchen des Modells  
 Der **Such Viewer für** Vorhersagemodelle bietet eine Diagramm Ansicht, in der die Trends im Laufe der Zeit angezeigt werden, und Sie können Vorhersagen erstellen, und eine Modell Ansicht, die die Zeitreihe als Entscheidungsstruktur oder Regressions Struktur darstellt.  
  
-   [Diagramm Ansicht](#bkmk_charts)  
  
-   [Modell Ansicht](#bkmk_Model)  
  
 Um mit einem Vorhersagemodell zu experimentieren, können Sie die Beispiel Daten auf der Registerkarte "vorhersagen" der Beispiel Daten-Arbeitsmappe verwenden und ein Zeitreihen Modell mithilfe des Planungs- [Assistenten &#40;Data Mining-Add-Ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md) im **Data Mining** -Menüband erstellen oder [&#40;Tabellenanalyse Tools für Excel&#41;](forecast-table-analysis-tools-for-excel.md) auf dem Menüband **analysieren** erstellen.  
  
###  <a name="bkmk_charts"></a>Fluss  
 Die Registerkarte **Diagramm** zeigt den Trend in der Datenreihe im Laufe der Zeit sowie die vorhergesagten Werte an. Die vertikale Achse des Diagramms stellt die Werte der Reihe dar, und die horizontale Achse stellt die Zeit dar.  
  
##### <a name="explore-the-forecasting-chart"></a>Untersuchen des Prognosediagramms  
  
1.  Dieses Modell enthält mehrere Zeitreihen. Um das Diagramm jedoch zu vereinfachen, können Sie eine einzelne Reihe oder nur wenige aufeinander bezogene Reihen anzeigen.  
  
     ![Vergangenheitsvorhersagen im Prognosemodell](media/dm13-forecast-chart-historicpredictions.gif "Vergangenheitsvorhersagen im Prognosemodell")  
  
     Verwenden Sie die Kontrollkästchen, um die Vorhersage nur für Nordamerika oder nur für die Verkaufsmenge auszuwählen.  
  
2.  Klicken Sie auf **Vorhersage Schritte** , und geben Sie einen neuen Wert ein, um zu steuern, wie viele zukünftige Zeit Werte im Diagramm angezeigt werden sollen.  
  
     Der Standardwert ist 5.  
  
3.  Klicken Sie auf einen beliebigen Punkt in der Zeile (Verlauf oder Zukunft), um die genauen Werte für diesen Zeitpunkt anzuzeigen, die in der **Mining Legende**angezeigt werden.  
  
4.  Im Diagramm werden Vergangenheits- und Zukunftsdaten angezeigt. Beachten Sie die gepunktete Linie mit einem schattierten Hintergrund. Diese Werte sind die künftigen Vorhersagen, die auf dem Modell basieren.  
  
     Die Vergangenheitsdaten (mit denen Sie das Modell erstellt haben) werden auf der linken Seite des Diagramms angezeigt.  
  
5.  Wählen Sie die Option **historische Vorhersagen anzeigen** aus, um einen Sinn für die Stabilität der Zeitreihe zu erhalten.  
  
     ![Prognosen für eine einzelne Reihe im Modell](media/dm13-forecast-chart-singleseries.gif "Prognosen für eine einzelne Reihe im Modell")  
  
     Vergangene Vorhersagen sind Werte, die basierend auf der Reihe bis zum entsprechenden Zeitpunkt vorhergesagt wurden und die mit tatsächlichen Vergangenheitswerten verglichen werden. Wenn die gepunktete Linie (mit den vorhergesagten Werten) weit von der durchgezogenen Linie (die tatsächlichen Werte) entfernt ist, bedeutet das, dass der erste Teil der Reihe die späteren Werte vielleicht nicht genau vorhersagt. Möglicherweise sind mehr Daten erforderlich, oder es könnte lediglich ein Hinweis auf die Flüchtigkeit im Zyklus sein.  
  
6.  Wählen Sie die Option **Abweichungen anzeigen** aus, um Fehlerindikatoren im Diagramm anzuzeigen.  
  
     Mithilfe der Fehlerindikatoren können Sie die Variabilität der Vorhersagen visuell bewerten. Die Qualität der Vorhersagen hängt von den Quelldaten ab. Wenn Sie die Anzahl der Vorhersageschritte erhöhen, sollten Sie jedoch einen stetigen Anstieg der Abweichungen feststellen.  
  
 **Chti**  
  
-   Zum Umschalten der Anzeige der **Mining Legende**klicken Sie mit der rechten Maustaste auf einen beliebigen Punkt im Diagramm.  
  
     Sie können einen bestimmten Zeitbereich anzeigen, indem Sie auf das Diagramm klicken, eine Zeitauswahl über das Diagramm ziehen und dann durch erneutes Klicken den ausgewählten Bereich vergrößern.  
  
-   Um eine Kopie des aktuellen Diagramms zu erhalten, klicken Sie auf **nach Excel kopieren**, und klicken Sie dann auf ein Arbeitsblatt in Excel. Im Arbeitsblatt wird eine Grafik mit allen festgelegten Optionen eingefügt, einschließlich einer Legende.  
  
     Diese Grafik ist jedoch statisch, sodass Sie die Legende nicht bearbeiten oder die zugrunde liegenden Daten anzeigen können. Wenn Sie eine interaktive Diagramm Ansicht benötigen, verwenden Sie die [Visio-Viewer](viewing-data-mining-models-in-visio-data-mining-add-ins.md).  
  
-   Klicken Sie in der Viewer-Menüleiste auf **ABS** , um zwischen absoluten und relativen Kurven zu wechseln.  
  
     Diese Option ist nützlich, falls das Diagramm mehrere Modelle enthält, die Skalierung der Daten der einzelnen Modelle sich jedoch erheblich unterscheidet.  
  
     Wenn zum Beispiel die Geschäfte in der Pazifikregion neu sind und wenig Verkäufe verzeichnen, und wenn absolute Werte verwendet werden, wird die Linie, die die Verkäufe der Pazifikregion darstellt, möglicherweise flach dargestellt und tatsächliche Änderungen sind nur schwer erkennbar. Die anderen Modelle würden in diesem Fall jedoch mit einer stärker normalisierten Skalierung angezeigt.  
  
     Durch den Wechsel zur Anzeige mit relativen Werten können Sie die Skalierung verschiedener Modelle normalisieren und Unterschiede als Änderungsprozentsatz anzeigen. Wenn Änderungen für jedes Modell relativ sind, können diese ohne signifikante Verzerrung in demselben Diagramm angezeigt werden.  
  
 [Untersuchen des Modells](#bkmk_Top)  
  
###  <a name="bkmk_Model"></a>Modells  
 Ein Planungsmodell kann auch als Entscheidungsstruktur oder, bei einer größtenteils linearen Reihe, als Regressionsmodell dargestellt werden.  
  
 In diesem Modell liegt zum Beispiel basierend auf einer bestimmten Bedingung ein Unterschied in der Regressionsformel vor, sodass die Struktur in zwei Verzweigungen mit einer jeweils unterschiedlichen Regressionsformel aufgeteilt wird.  
  
 ![Filtern einer einzelnen Reihe im Prognosemodell](media/dm13-forecast-model-northamerica.gif "Filtern einer einzelnen Reihe im Prognosemodell")  
  
##### <a name="explore-the-forecasting-model-as-a-tree"></a>Untersuchen des Prognosemodells als Struktur  
  
1.  Klicken Sie **auf die** Dropdown Liste Struktur, und wählen Sie ein Modell für die Anzeige aus.  
  
     Für jedes vorhersagbare Attribut wird eine separate Struktur oder ein Regressionsknoten angezeigt. Wenn Ihre Daten beispielsweise Verkäufe für Europa, Nordamerika und Pazifik enthalten, sind drei verschiedene Modelle vorhanden, eines für jede Datenreihe.  
  
2.  Ziehen Sie den Schieberegler **Ebene anzeigen** , um die unteren Ebenen der Struktur herauszufiltern, und konzentrieren Sie sich auf die wichtigsten Teilungen.  
  
3.  Klicken Sie auf jeden Knoten, um einige beschreibende Statistiken in der **Mining Legende**anzuzeigen.  
  
     Wenn Sie mit der Maus auf einen Knoten zeigen, zeigt die QuickInfo ebenfalls diese statistischen Daten sowie die vollständige Formel an, die den betreffenden Knoten beschreibt.  
  
4.  Wenn Sie die Informationen in der **Mining Legende**kopieren möchten, klicken Sie mit der rechten Maustaste auf die **Mining Legende**, wählen Sie **Kopieren**aus, und klicken Sie dann in das Excel-Arbeitsblatt. Die Option **in Excel kopieren** kopiert das Diagramm, nicht die Statistiken.  
  
 [Untersuchen des Modells](#bkmk_Top)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
