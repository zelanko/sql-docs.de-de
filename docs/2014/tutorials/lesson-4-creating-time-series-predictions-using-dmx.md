---
title: 'Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6b883e43-209d-489a-8dc3-9349f88acae8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 772e5f5f71ca82dd18fec48730522c80e907414f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56024881"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a>Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX
  In dieser Lektion und der folgenden Lektion, verwenden Sie Data Mining Extensions (DMX) erstellen Sie verschiedene Arten von Vorhersagen auf Grundlage der zeitreihenmodelle, die Sie in erstellt [Lektion 1: Erstellen ein Zeitreihenmodell Miningmodell und Miningstruktur](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) und [Lektion 2: Hinzufügen von Miningmodellen zur der Zeitreihen-Miningstruktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md).  
  
 Ein Zeitreihenmodell bietet zahlreiche Optionen im Hinblick auf Vorhersagen:  
  
-   Verwendung vorhandener Muster im Miningmodell mit bestehenden Daten  
  
-   Verwendung vorhandener Muster im Miningmodell mit neuen Daten  
  
-   Aufnahme neuer Daten in das Modell oder Update des Modells  
  
 Nachfolgend finden Sie eine Zusammenfassung der Syntax für diese Vorhersagetypen:  
  
 Zeitreihenvorhersage (Standard)  
 Verwendung [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) die angegebene Anzahl von Vorhersagen aus dem trainierten Miningmodell zurückgeben.  
  
 Beispielsweise finden Sie unter [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) oder [Time Series Model Query Examples](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).  
  
 EXTEND_MODEL_CASES  
 Verwendung [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) mit dem EXTEND_MODEL_CASES-Argument, um neue Daten hinzufügen, die Reihe erweitern und Vorhersagen auf Grundlage des aktualisierten Miningmodells erstellen.  
  
 Dieses Lernprogramm enthält ein Beispiel zur Verwendung des EXTEND_MODEL_CASES-Arguments.  
  
 REPLACE_MODEL_CASES  
 Verwendung [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) mit dem REPLACE_MODEL_CASES-Argument, um die ursprünglichen Daten durch eine neue Datenreihe ersetzen, und erstellen Sie vorhersagen auf Grundlage der Muster im Miningmodell auf neuen Daten anzuwenden Reihe.  
  
 Ein Beispiel für die wie REPLACE_MODEL_CASES verwendet, finden Sie unter [Lektion 2: Erstellen eines Planungserstellungsszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).  
  
## <a name="lesson-tasks"></a>Lektionsaufgaben  
 Im Rahmen dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
-   Erstellen einer Abfrage zum Abrufen der Standardvorhersagen auf Basis vorhandener Daten  
  
 In der folgenden Lektion führen Sie die nachstehenden verwandten Aufgaben aus:  
  
-   Erstellen einer Abfrage zur Bereitstellung neuer Daten sowie zum Abrufen aktualisierter Vorhersagen  
  
 Sie können Abfragen sowohl manuell mit DMX als auch mit dem Generator für Vorhersageabfragen in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] erstellen.  
  
## <a name="simple-time-series-prediction-query"></a>Einfache Vorhersageabfragen für Zeitreihen  
 Der erste Schritt besteht darin, mit der `SELECT FROM`-Anweisung und der `PredictTimeSeries`-Funktion Zeitreihenvorhersagen zu erstellen. Zeitreihenmodelle unterstützen eine vereinfachte Syntax zum Erstellen von Vorhersagen. Sie müssen lediglich angeben, wie viele Vorhersagen erstellt werden sollen; eine Bereitstellung von Eingaben ist nicht erforderlich. Die folgende Zeile stellt ein allgemeines Beispiel für die verwendete Anweisung dar:  
  
```  
SELECT <select list>   
FROM [<mining model name>]   
WHERE [<criteria>]  
```  
  
 Die Auswahlliste kann Spalten aus dem Modell enthalten, z. B. der Namen des Produkts Zeile, die Sie erstellen die Vorhersagen für, oder spezifische Vorhersagefunktionen, z. B. [Lag &#40;DMX&#41; ](/sql/dmx/lag-dmx) oder [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx), insbesondere für Zeitreihen-Miningmodelle sind.  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a>So erstellen Sie eine einfache Vorhersageabfrage für Zeitreihen  
  
1.  In **Objekt-Explorer**, mit der rechten Maustaste in der Instanzstatus von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     durch:  
  
    ```  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    ```  
  
     In der ersten Zeile wird ein Wert vom Miningmodell abgerufen, der die Reihe identifiziert.  
  
     In der zweiten und dritten Zeile wird die `PredictTimeSeries`-Funktion verwendet. In jeder Zeile wird ein anderes Attribut vorhergesagt: `[Quantity]` oder `[Amount]`. Die Zahlen hinter den Namen der vorhersagbaren Attribute geben die Anzahl der Zeitschritte an, die vorhergesagt werden sollen.  
  
     Mit der `AS`-Klausel wird ein Name für die Spalte bereitgestellt, die von der jeweiligen Vorhersagefunktion zurückgegeben wird. Wenn Sie keinen Alias angeben, werden beide Spalten standardmäßig mit der Bezeichnung `Expression` zurückgegeben.  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    [<mining model>]   
    ```  
  
     durch:  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     durch:  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT  
    [Forecasting_MIXED].[ModelRegion],  
    PredictTimeSeries([Forecasting_MIXED].[Quantity],6) AS PredictQty,  
    PredictTimeSeries ([Forecasting_MIXED].[Amount],6) AS PredictAmt  
    FROM   
    [Forecasting_MIXED]  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
6.  Auf der **Datei** Menü klicken Sie auf **Dmxquery1.DMX speichern**.  
  
7.  In der **speichern** Dialogfeld, navigieren Sie zu den entsprechenden Ordner, und nennen Sie die Datei `SimpleTimeSeriesPrediction.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die **Execute** Schaltfläche.  
  
     Nach Ausführung der Abfrage werden 6 Vorhersagen für jede der zwei Kombinationen aus Produkt und Region in der `WHERE`-Klausel zurückgegeben.  
  
 In der nächsten Lektion erstellen Sie eine Abfrage, mit der neue Daten für das Modell bereitgestellt werden. Außerdem vergleichen Sie die Ergebnisse dieser Vorhersage mit der Vorhersage, die Sie gerade erstellt haben.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Lesson 5: Erweitern die Zeitreihe zu modellieren.](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a>Siehe auch  
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)   
 [Lag &#40;DMX&#41;](/sql/dmx/lag-dmx)   
 [Abfragebeispiel Zeitreihenmodell](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Lektion 2: Erstellen eines Planungserstellungsszenarios &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
