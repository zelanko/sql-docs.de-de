---
title: 'Lektion 5: Erweitern des Zeitreihen Modells | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7aad4946-c903-4e25-88b9-b087c20cb67d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2716e985897f8115d189d9410b7cdb13fb1af291
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62822066"
---
# <a name="lesson-5-extending-the-time-series-model"></a>Lektion 5: Erweitern des Zeitreihenmodells
  In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Enterprise können Sie einem Zeitreihenmodell neue Daten hinzufügen und die neuen Daten automatisch in das Modell einbeziehen. Es gibt zwei Möglichkeiten, einem Zeitreihen-Miningmodell neue Daten hinzuzufügen:  
  
-   Verknüpfen von Daten in einer externen Quelle mit den Trainingsdaten durch eine PREDICTION JOIN-Anweisung   
  
-   Bereitstellen von Daten in einzelnen Slices mit einer SINGLETON-Vorhersageabfrage  
  
 Angenommen, Sie haben das Miningmodell vor einigen Monaten mit vorhandenen Umsatzdaten trainiert. Wenn neue Umsatzzahlen vorliegen, können Sie diese verwenden, um die entsprechenden Vorhersagen zu aktualisieren. Dazu können Sie die neuen Umsatzzahlen als Eingabedaten bereitstellen und anhand des zusammengesetzten Datasets neue Vorhersagen generieren.  
  
## <a name="making-predictions-with-extend_model_cases"></a>Treffen von Vorhersagen mit EXTEND_MODEL_CASES  
 Nachfolgend finden Sie allgemeine Beispiele für eine Zeitreihenvorhersage mit dem EXTEND_MODEL_CASES-Parameter. Mit dem ersten Beispiel können Sie die Anzahl der Vorhersagen ab dem letzten Zeitschritt des ursprünglichen Modells angeben:  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>]  
```  
  
 Im zweiten Beispiel können Sie den Zeitschritt für Beginn und Ende der Vorhersagen angeben. Diese Option spielt eine wichtige Rolle bei der Erweiterung von Modellfällen, da Zeitschritte für Vorhersageabfragen standardmäßig immer am Ende der ursprünglichen Reihe beginnen.  
  
```  
SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n-start, n-end, EXTEND_MODEL_CASES)   
FROM <mining model>  
PREDICTION JOIN <source query>  
[WHERE <criteria>}  
```  
  
 In diesem Lernprogramm erstellen Sie beide Arten von Abfragen.  
  
#### <a name="to-create-a-singleton-prediction-query-on-a-time-series-model"></a>So erstellen Sie eine SINGLETON-Vorhersageabfrage für ein Zeitreihenmodell  
  
1.  Klicken Sie in **Objekt-Explorer**mit der rechten Maustaste auf [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Instanz von, zeigen Sie auf **neue Abfrage**, und klicken Sie dann auf **DMX**.  
  
     Der Abfrage-Editor wird mit einer neuen leeren Abfrage geöffnet.  
  
2.  Kopieren Sie das allgemeine Beispiel der SINGLETON-Anweisung in die leere Abfrage.  
  
3.  Ersetzen Sie Folgendes:  
  
    ```  
    SELECT [<model columns>,] PredictTimeSeries(<table column reference>, n, EXTEND_MODEL_CASES)   
    ```  
  
     durch:  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    ```  
  
     In der ersten Zeile wird ein Wert aus dem Modell zur Identifizierung der Reihe abgerufen.  
  
     Die zweite Zeile enthält die Vorhersagefunktion, mit der 6 Vorhersagen für Quantity abgerufen werden. Zum besseren Verständnis der Ergebnisse wird der Ergebnisspalte für die Vorhersage der Alias `PredictQty` zugewiesen.  
  
4.  Ersetzen Sie Folgendes:  
  
    ```  
    FROM <mining model>  
    ```  
  
     durch:  
  
    ```  
    FROM [Forecasting_MIXED]  
    ```  
  
5.  Ersetzen Sie Folgendes:  
  
    ```  
    PREDICTION JOIN <source query>  
    ```  
  
     durch:  
  
    ```  
    NATURAL PREDICTION JOIN   
    (  
       SELECT 1 AS [Reporting Date],  
       '10' AS [Quantity],  
       'M200 Europe' AS [Model Region]  
       UNION SELECT  
       2 AS [Reporting Date],  
       15 AS [Quantity]),  
       'M200 Europe' AS [Model Region]  
    ) AS t  
    ```  
  
6.  Ersetzen Sie Folgendes:  
  
    ```  
    [WHERE <criteria>]  
    ```  
  
     durch:  
  
    ```  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
     Die gesamte Anweisung sollte wie folgt aussehen:  
  
    ```  
    SELECT [Model Region],  
    PredictTimeSeries([Quantity],6, EXTEND_MODEL_CASES) AS PredictQty  
    FROM  
       [Forecasting_MIXED]  
    NATURAL PREDICTION JOIN   
       SELECT 1 AS [ReportingDate],  
      '10' AS [Quantity],  
      'M200 Europe' AS [ModelRegion]  
    UNION SELECT  
      2 AS [ReportingDate],  
      15 AS [Quantity]),  
      'M200 Europe' AS [ModelRegion]  
    ) AS t  
    WHERE [ModelRegion] = 'M200 Europe' OR  
    [ModelRegion] = 'M200 Pacific'  
    ```  
  
7.  Klicken Sie im Menü **Datei** auf **DMXQuery1. DMX speichern**unter.  
  
8.  Navigieren Sie im Dialogfeld **Speichern** unter in den entsprechenden Ordner, und benennen Sie die Datei `Singleton_TimeSeries_Query.dmx`.  
  
9. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Ausführen** .  
  
     Die Abfrage gibt Vorhersagen mit der Verkaufsmenge des Fahrradmodells M200 für die Regionen Europa und Pazifik zurück.  
  
## <a name="understanding-prediction-start-with-extend_model_cases"></a>Grundlegendes zum Beginn der Vorhersage mit EXTEND_MODEL_CASES  
 Nachdem Sie Vorhersagen auf der Grundlage des ursprünglichen Modells und mit neuen Daten erstellt haben, können Sie nun die Ergebnisse vergleichen, um zu sehen, wie sich das Update der Umsatzdaten auf die Vorhersagen auswirkt. Überprüfen Sie jedoch zuvor den Code, den Sie gerade erstellt haben, und beachten Sie Folgendes:  
  
-   Sie haben neue Daten nur für die Region Europa angegeben.  
  
-   Die neuen Daten umfassen nur einen Zeitraum von zwei Monaten.  
  
 Die folgende Tabelle zeigt, wie sich die neuen Werte für das M200-Modell in Europa auf die Vorhersagen auswirken. Da Sie keine neuen Daten für das M200-Modell in der Region Pazifik angegeben haben, wird diese Reihe zum Vergleich dargestellt:  
  
 **Produkt und Region: M200 Europe**  
  
|||||  
|-|-|-|-|  
|||Gegebenes Modell (`PredictTimeSeries`)|Modell mit aktualisierten Umsatzdaten (`PredictTimeSeries` mit `EXTEND_MODEL_CASES`)|  
|M200 Europe|7/25/2008 12:00:00 AM|77|10|  
|M200 Europe|8/25/2008 12:00:00 AM|64|15|  
|M200 Europe|9/25/2008 12:00:00 AM|59|72|  
|M200 Europe|10/25/2008 12:00:00 AM|56|69|  
|M200 Europe|11/25/2008 12:00:00 AM|56|68|  
|M200 Europe|12/25/2008 12:00:00 AM|74|89|  
  
 **Produkt und Region: M200 Pacific**  
  
|||||  
|-|-|-|-|  
|||Gegebenes Modell (`PredictTimeSeries`)|Modell mit aktualisierten Umsatzdaten (`PredictTimeSeries` mit `EXTEND_MODEL_CASES`)|  
|M200 Pacific|7/25/2008 12:00:00 AM|41|41|  
|M200 Pacific|8/25/2008 12:00:00 AM|44|44|  
|M200 Pacific|9/25/2008 12:00:00 AM|38|38|  
|M200 Pacific|10/25/2008 12:00:00 AM|41|41|  
|M200 Pacific|11/25/2008 12:00:00 AM|36|36|  
|M200 Pacific|12/25/2008 12:00:00 AM|11,9|11,9|  
  
 Aus diesen Ergebnissen sind zwei Dinge ersichtlich:  
  
-   Die ersten beiden Vorhersagen für die Datenreihe M200 Europe stimmen exakt mit den neuen Daten überein, die Sie bereitgestellt haben. Analysis Services gibt programmbedingt die tatsächlichen neuen Datenpunkte zurück, statt eine Vorhersage zu treffen. Dies liegt daran, dass bei der Erweiterung der Modellfälle die Zeitschritte für Vorhersageabfragen standardmäßig immer am Ende der ursprünglichen Reihe beginnen. Wenn Sie daher zwei neue Datenpunkte hinzufügen, überschneiden sich die ersten zwei zurückgegebenen Vorhersagen mit den neuen Daten.  
  
-   Nachdem alle neuen Datenpunkte verwendet wurden, erstellt [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Vorhersagen auf Grundlage des aktualisierten Modells. Ab September 2005 wird daher der Unterschied zwischen den Vorhersagen für die Datenreihe M200 Europe und dem ursprünglichen Modell (linke Spalte) sowie dem Modell mit EXTEND_MODEL_CASES (rechte Spalte) ersichtlich. Die Vorhersagen unterscheiden sich, da das Modell mit den neuen Daten aktualisiert wurde.  
  
## <a name="using-start-and-end-time-steps-to-control-predictions"></a>Verwenden von Zeitschritten für Beginn und Ende zur Steuerung von Vorhersagen  
 Wenn Sie ein Modell erweitern, werden die neuen Daten immer am Ende der Reihe angefügt. Die für Vorhersageabfragen verwendeten Zeitscheiben beginnen jedoch immer am Ende der ursprünglichen Reihe. Damit beim Hinzufügen von neuen Daten nur die neuen Vorhersagen abgerufen werden, müssen Sie den Startpunkt als Anzahl von Zeitscheiben angeben. Wenn Sie beispielsweise zwei neue Datenpunkte hinzufügen und vier neue Vorhersagen treffen möchten, gehen Sie wie folgt vor:  
  
-   Erstellen Sie eine PREDICTION JOIN-Anweisung für ein Zeitreihenmodell, und geben Sie neue Daten für einen Zeitraum von zwei Monaten an.  
  
-   Fordern Sie Vorhersagen für vier Zeitscheiben an, wobei der Startpunkt Zeitscheibe 3 und der Endpunkt Zeitscheibe 6 ist.  
  
 Anders ausgedrückt: Wenn die neuen Daten n Zeit Scheiben enthalten und Sie Vorhersagen für die Zeit Schritte 1 bis n anfordern, stimmen die Vorhersagen mit dem gleichen Zeitraum wie die neuen Daten überein. Wenn Sie neue Vorhersagen für Zeiträume benötigen, die nicht von den Daten abgedeckt werden, müssen die Vorhersagen bei Zeitscheibe n+1 nach der neuen Datenreihe beginnen, oder Sie müssen sicherstellen, dass Sie zusätzliche Zeitscheiben anfordern.  
  
> [!NOTE]  
>  Wenn Sie neue Daten hinzufügen, sind keine Vergangenheitsvorhersagen möglich.  
  
 Im folgenden Beispiel wird die DMX-Anweisung veranschaulicht, mit der nur die neuen Vorhersagen für zwei Reihen im vorangehenden Beispiel abgerufen werden können.  
  
```  
SELECT [Model Region],  
PredictTimeSeries([Quantity],3,6, EXTEND_MODEL_CASES) AS PredictQty  
FROM  
   [Forecasting_MIXED]  
NATURAL PREDICTION JOIN   
   SELECT 1 AS [ReportingDate],  
  '10' AS [Quantity],  
  'M200 Europe' AS [ModelRegion]  
UNION SELECT  
  2 AS [ReportingDate],  
  15 AS [Quantity]),  
  'M200 Europe' AS [ModelRegion]  
) AS t  
WHERE [ModelRegion] = 'M200 Europe'  
```  
  
 Die Vorhersage beginnt bei der Zeitscheibe 3, also nach dem Zeitraum von 2 Monaten, den die neuen Daten umfassen.  
  
 **Produkt und Region: M200 Europe**  
  
 Modell mit aktualisierten Daten (PredictTimeSeries mit EXTEND_MODEL_CASES)  
  
||||  
|-|-|-|  
|M200 Europe|9/25/2008 12:00:00 AM|72|  
|M200 Europe|10/25/2008 12:00:00 AM|69|  
|M200 Europe|11/25/2008 12:00:00 AM|68|  
|M200 Europe|12/25/2008 12:00:00 AM|89|  
  
## <a name="making-predictions-with-replace_model_cases"></a>Treffen von Vorhersagen mit REPLACE_MODEL_CASES  
 Das Ersetzen der Modellfälle ist sinnvoll, wenn Sie ein Modell mit einem Satz von Fällen trainieren und dieses Modell auf eine andere Datenreihe anwenden möchten. Eine ausführliche Exemplarische Vorgehensweise dieses Szenarios finden Sie in [Lektion 2: Erstellung eines Planungs Szenarios &#40;Data Mining ](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)-Lernprogramm für fortgeschrittene&#41;.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfrage Beispiele für Zeitreihen Modelle](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [Prättimeseries &#40;DMX-&#41;](/sql/dmx/predicttimeseries-dmx)  
  
  
