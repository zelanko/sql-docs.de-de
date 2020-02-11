---
title: Vergleichen von Vorhersagen für Prognosemodelle (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 26cc445d3bad5c628628353d5c0c84ffa4755e97
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63066334"
---
# <a name="comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial"></a>Vergleichen von Vorhersagen für Modelle zur Planungserstellung (Data Mining-Lernprogramm für Fortgeschrittene)
  In den vorherigen Schritten dieses Lernprogramms haben Sie mehrere Zeitreihenmodelle erstellt:  
  
-   Vorhersagen für jede Kombination aus Region und Modell auf Basis der Daten für die einzelnen Modelle und Regionen  
  
-   Vorhersagen für jede Region auf Basis von aktualisierten Daten  
  
-   Vorhersagen für alle Modelle auf einer weltweiten Basis anhand von aggregierten Daten  
  
-   Vorhersagen für das M200-Modell in Nordamerika auf Basis des aggregierten Modells  
  
 Um die Funktionen für Zeitreihenvorhersagen zusammenzufassen, überprüfen Sie die Änderungen; Sie sehen so, wie sich die einzelnen Optionen für Erweitern oder Ersetzen der Daten auf die Prognoseergebnisse auswirkt.  
  
 [EXTEND_MODEL_CASES](#bkmk_EXTEND)  
  
 [REPLACE_MODEL_CASES](#bkmk_REPLACE)  
  
##  <a name="bkmk_EXTEND"></a>Vergleichen der ursprünglichen Ergebnisse mit Ergebnissen nach dem Hinzufügen von Daten  
 Sehen wir uns nur die Daten für die M200-Produktlinie in der Pazifikregion an, um zu erfahren, wie sich das Aktualisieren des Modells mit neuen Daten auf die Ergebnisse auswirkt. Erinnern Sie sich, dass die ursprüngliche Datenreihe im Juni 2004 endete und wir neue Daten für Juli, August und September abgerufen haben.  
  
-   Die erste Spalte zeigt die neu hinzugefügten Daten an.  
  
-   Die zweite Spalte zeigt die Prognose für Juli und später auf Grundlage der ursprünglichen Datenreihe.  
  
-   Die dritte Spalte zeigt die Prognose auf Grundlage der erweiterten Daten.  
  
|**M200 Pacific**|Aktualisierte tatsächlich Umsatzdaten|Prognose vor dem Hinzufügen von Daten|Erweiterte Vorhersage|  
|----------------------|-----------------------------|------------------------------------|-------------------------|  
|7-25-2008|**65**|32|**65**|  
|8-25-2008|**54**|37|**54**|  
|9-25-2008|**61**|32|**61**|  
|10-25-2008|Keine Daten|36|32|  
|11-25-2008|Keine Daten|31|41|  
|12-25-2008|Keine Daten|34|32|  
  
 Sie werden feststellen, dass sich die tatsächlichen Datenpunkte in den Prognosen, die die erweiterten Daten (hier fett hervorgehoben) verwenden, exakt wiederholen. Die Wiederholung ist programmbedingt. Solange tatsächliche Datenpunkte zur Verwendung vorhanden sind, gibt die Vorhersageabfrage die Istwerte zurück. Neue Vorhersagewerte werden erst ausgegeben, wenn die neuen tatsächlichen Datenpunkte aufgebraucht sind.  
  
 Im Allgemeinen gewichtet der Algorithmus die Änderungen in den neuen Daten stärker als Daten vom Anfang der Modelldaten. In diesem Fall geben die neuen Umsatzzahlen im Vergleich zum vorherigen Zeitraum jedoch nur eine Zunahme von 20-30 Prozent an. Die prognostizierten Umsätze verzeichneten also nur einen leichten Anstieg; anschließend gehen die Verkaufsprognosen erneut abwärts und entsprechen eher dem Trend in den Monaten vor den neuen Daten.  
  
##  <a name="bkmk_REPLACE"></a>Vergleichen der ursprünglichen und Kreuz Vorhersage Ergebnisse  
 Sie werden sich erinnern, dass das ursprüngliche Miningmodell einen großen Unterschied zwischen bestimmten Regionen und Modellreihen herausarbeitete. So waren die Verkäufe für das M200-Modell beispielsweise sehr stark, während sie für das T1000-Modell in allen Regionen ziemlich niedrig waren. Darüber hinaus haben einige Reihen keine großen Daten. Die Reihen waren unregelmäßig, was bedeutet, dass Sie nicht denselben Ausgangspunkt hatten.  
  
 ![Reihenvorhersagen für Mengen M200 und T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "Reihenvorhersagen für Mengen M200 und T1000")  
  
 Wie also haben sich die Vorhersagen geändert, als Sie die Prognosen auf Grundlage des allgemeinen Modells, basierend auf den weltweiten Umsätzen, und nicht mehr auf Grundlage der ursprünglichen Datasets ermittelt haben? Sie können sicherstellen, keine Informationen verloren oder die Vorhersagen verzerrt zu haben, indem Sie die Ergebnisse in einer Tabelle speichern, die Tabelle der Vorhersagen mit der Tabelle der Vergangenheitsdaten verknüpfen, und dann die zwei Datensätze für Vergangenheit und Vorhersage grafisch darstellen.  
  
 Das folgende Diagramm basiert auf nur einer Produktlinie, dem M200. Das Diagramm vergleicht die Vorhersagen, die jeweils mit dem ursprünglichen Miningmodell und dem aggregierte Miningmodell ermittelt wurden.  
  
 ![Excel-Diagramm zum Vergleich von Vorhersagen](../../2014/tutorials/media/m200-predictions-compared.gif "Excel-Diagramm zum Vergleich von Vorhersagen")  
  
 In diesem Diagramm können Sie erkennen, dass das aggregierte Miningmodell den allgemeinen Wertebereich und -trend beibehält, gleichzeitig jedoch die Schwankungen in den einzelnen Datenreihen minimiert.  
  
## <a name="conclusion"></a>Zusammenfassung  
 Sie haben gelernt, ein Zeitreihenmodell zu erstellen und anzupassen, das zur Prognoseerstellung verwendet werden kann.  
  
 Sie haben gelernt, Zeitreihenmodelle ohne erneute Verarbeitung zu aktualisieren, indem Sie neue Daten hinzufügen und Vorhersagen mit dem Parameter EXTEND_MODEL_CASES erstellen.  
  
 Sie können nun Modelle erstellen, die für Kreuzvorhersagen geeignet sind, indem Sie den Parameter REPLACE_MODEL_CASES verwenden und das Modell auf eine andere Datenreihe anwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Lernprogramm für fortgeschrittene &#40;Analysis Services-Data Mining-&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Abfragebeispiel Zeitreihenmodell](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
