---
title: Vergleichen von Vorhersagen für Forecasting-Modellen (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ead8a1fe-60d8-4017-8fb8-6fe32168e46d
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a8ff27b38e2268ead42a1238250902b6ebf9cf18
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165772"
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
  
##  <a name="bkmk_EXTEND"></a> Vergleichen die ursprünglichen Ergebnisse und Ergebnissen nach dem Hinzufügen von Daten  
 Werfen wir einen Blick nur auf die Daten der M200-Produktlinie in der Pazifikregion. Hier können wir sehen, wie eine Aktualisierung des Modells mit neuen Daten sich auf die Ergebnisse auswirkt. Erinnern Sie sich, dass die ursprüngliche Datenreihe im Juni 2004 endete und wir neue Daten für Juli, August und September abgerufen haben.  
  
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
  
##  <a name="bkmk_REPLACE"></a> Vergleichen der ursprünglichen und Kreuzvorhersage-Ergebnisse  
 Sie werden sich erinnern, dass das ursprüngliche Miningmodell einen großen Unterschied zwischen bestimmten Regionen und Modellreihen herausarbeitete. So waren die Verkäufe für das M200-Modell beispielsweise sehr stark, während sie für das T1000-Modell in allen Regionen ziemlich niedrig waren. Zudem enthielten manche Reihen nur wenige Daten. Manche Reihen waren unregelmäßig, was bedeutet, dass sie nicht denselben Ausgangspunkt hatten.  
  
 ![Reihenvorhersagen für Mengen M200 und T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "Reihenvorhersagen für Mengen M200 und T1000")  
  
 Wie also haben sich die Vorhersagen geändert, als Sie die Prognosen auf Grundlage des allgemeinen Modells, basierend auf den weltweiten Umsätzen, und nicht mehr auf Grundlage der ursprünglichen Datasets ermittelt haben? Sie können sicherstellen, keine Informationen verloren oder die Vorhersagen verzerrt zu haben, indem Sie die Ergebnisse in einer Tabelle speichern, die Tabelle der Vorhersagen mit der Tabelle der Vergangenheitsdaten verknüpfen, und dann die zwei Datensätze für Vergangenheit und Vorhersage grafisch darstellen.  
  
 Das folgende Diagramm basiert auf nur einer Produktlinie, dem M200. Das Diagramm vergleicht die Vorhersagen, die jeweils mit dem ursprünglichen Miningmodell und dem aggregierte Miningmodell ermittelt wurden.  
  
 ![Excel-Diagramm Vergleichen von Vorhersagen](../../2014/tutorials/media/m200-predictions-compared.gif "Excel-Diagramm Vergleichen von Vorhersagen")  
  
 In diesem Diagramm können Sie erkennen, dass das aggregierte Miningmodell den allgemeinen Wertebereich und -trend beibehält, gleichzeitig jedoch die Schwankungen in den einzelnen Datenreihen minimiert.  
  
## <a name="conclusion"></a>Fazit  
 Sie haben gelernt, ein Zeitreihenmodell zu erstellen und anzupassen, das zur Prognoseerstellung verwendet werden kann.  
  
 Sie haben gelernt, Zeitreihenmodelle ohne erneute Verarbeitung zu aktualisieren, indem Sie neue Daten hinzufügen und Vorhersagen mit dem Parameter EXTEND_MODEL_CASES erstellen.  
  
 Sie können nun Modelle erstellen, die für Kreuzvorhersagen geeignet sind, indem Sie den Parameter REPLACE_MODEL_CASES verwenden und das Modell auf eine andere Datenreihe anwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Lernprogramm für fortgeschrittene &#40;Analysis Services – Datamining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)   
 [Beispiele für Abfragen von Zeitreihenmodellen](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
