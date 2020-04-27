---
title: 'Lektion 4: Erstellen von Zeitreihen Vorhersagen mit DMX | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63312090"
---
# <a name="lesson-4-creating-time-series-predictions-using-dmx"></a>Lektion 4: Erstellen von Zeitreihenvorhersagen mit DMX
  In dieser Lektion und in der folgenden Lektion verwenden Sie Data Mining-Erweiterungen (DMX), um unterschiedliche Typen von Vorhersagen basierend auf den Zeitreihen Modellen zu erstellen, die Sie in [Lektion 1: Erstellen eines Zeitreihen-Mining Modells und einer Mining Struktur](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md) erstellt haben, und [Lektion 2: Hinzufügen von Mining Modellen zur Zeitreihen-Mining Struktur](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md).  
  
 Ein Zeitreihenmodell bietet zahlreiche Optionen im Hinblick auf Vorhersagen:  
  
-   Verwendung vorhandener Muster im Miningmodell mit bestehenden Daten  
  
-   Verwendung vorhandener Muster im Miningmodell mit neuen Daten  
  
-   Aufnahme neuer Daten in das Modell oder Update des Modells  
  
 Nachfolgend finden Sie eine Zusammenfassung der Syntax für diese Vorhersagetypen:  
  
 Zeitreihenvorhersage (Standard)  
 Verwenden Sie die [prättimeseries-&#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx) , um die angegebene Anzahl von Vorhersagen aus dem trainierten Mining Modell zurückzugeben.  
  
 Informationen hierzu finden Sie beispielsweise unter " [prättimeseries &#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx) oder [Zeitreihen Modell-Abfrage Beispiele](../../2014/analysis-services/data-mining/time-series-model-query-examples.md).  
  
 EXTEND_MODEL_CASES  
 Verwenden Sie die [&#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx) mit dem EXTEND_MODEL_CASES-Argument, um neue Daten hinzuzufügen, die Reihe zu erweitern und Vorhersagen basierend auf dem aktualisierten Mining Modell zu erstellen.  
  
 Dieses Lernprogramm enthält ein Beispiel zur Verwendung des EXTEND_MODEL_CASES-Arguments.  
  
 REPLACE_MODEL_CASES  
 Verwenden Sie " [prättimeseries &#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx) mit dem REPLACE_MODEL_CASES-Argument, um die ursprünglichen Daten durch eine neue Datenreihe zu ersetzen, und erstellen Sie dann Vorhersagen basierend auf dem Anwenden der Muster im Mining Modell auf die neue Datenreihe.  
  
 Ein Beispiel für die Verwendung von REPLACE_MODEL_CASES finden Sie unter [Lektion 2: Erstellung eines Planungs Szenarios &#40;Data Mining ](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)-Lernprogramm für fortgeschrittene&#41;.  
  
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
  
 Die Auswahlliste kann Spalten aus dem Modell enthalten, wie z. b. den Namen der Produktlinie, für die Sie die Vorhersagen erstellen, oder Vorhersagefunktionen, wie z. b. [lag &#40;DMX-&#41;](/sql/dmx/lag-dmx) oder [prättimeseries &#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx), die speziell für Zeitreihen-Mining Modelle gelten.  
  
#### <a name="to-create-a-simple-time-series-prediction-query"></a>So erstellen Sie eine einfache Vorhersageabfrage für Zeitreihen  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    <select list>   
    ```  
  
     Durch:  
  
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
  
     Durch:  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    WHERE [criteria>]   
    ```  
  
     Durch:  
  
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
  
6.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
7.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `SimpleTimeSeriesPrediction.dmx`.  
  
8.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
     Nach Ausführung der Abfrage werden 6 Vorhersagen für jede der zwei Kombinationen aus Produkt und Region in der `WHERE`-Klausel zurückgegeben.  
  
 In der nächsten Lektion erstellen Sie eine Abfrage, mit der neue Daten für das Modell bereitgestellt werden. Außerdem vergleichen Sie die Ergebnisse dieser Vorhersage mit der Vorhersage, die Sie gerade erstellt haben.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Lektion 5: Erweitern des Zeitreihenmodells](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prättimeseries &#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx)   
 [Verzögerung &#40;DMX-&#41;](/sql/dmx/lag-dmx)   
 [Abfrage Beispiele für Zeitreihen Modelle](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Lektion 2: Erstellung eines Vorhersage Szenarios &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
  
