---
title: Zeitreihenvorhersagen mit Ersetzungsdaten (Data Mining Tutorial für fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a23a6e1d-1d49-41ea-8314-925dc8e4df5e
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c96b70775105ea9446810ac3b064ae7cb07d4337
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312882"
---
# <a name="time-series-predictions-using-replacement-data-intermediate-data-mining-tutorial"></a>Erstellen von Zeitreihenvorhersagen mit Ersetzungsdaten (Data Mining-Lernprogramm für Fortgeschrittene)
  In dieser Aufgabe erstellen Sie auf Grundlage weltweiter Umsatzdaten ein neues Modell. Sie erstellen dann eine Vorhersageabfrage, mit der Sie das weltweite Umsatzmodell auf eine einzelnen Region anwenden.  
  
## <a name="building-a-general-model"></a>Erstellen eines allgemeinen Modells  
 Denken Sie daran, dass die Analyse der Ergebnisse des ursprünglichen Miningmodells große Unterschiede zwischen Regionen und Produktreihen aufgedeckt hat. Das M200-Modell verzeichnete beispielsweise einen starken Umsatz für Nordamerika, was für die Verkäufe des T1000-Modells nicht der Fall war. Allerdings ist die Analyse wurde dadurch erschwert, dass einige Reihen nicht viele Daten oder Daten zu einem anderen Zeitpunkt rechtzeitig gestartet hatten. Darüber hinaus fehlten einige Daten.  
  
 ![Reihenvorhersagen für Mengen M200 und T1000](../../2014/tutorials/media/6series-defaultforecasting.gif "Reihenvorhersagen für Mengen M200 und T1000")  
  
 Um einige dieser Data Quality-Probleme zu beheben, entscheiden Sie sich für eine Zusammenführung der weltweiten Umsatzdaten, um aus diesem Satz allgemeiner Verkaufstrends ein allgemeines Modell zu erstellen, mit dem zukünftige Verkäufe in einer beliebigen Region vorhergesagt werden können.  
  
 Wenn Sie Vorhersagen erstellen, wenden Sie das an den weltweiten Umsatzdaten trainierte Muster an, ersetzen aber die Vergangenheitsdaten-Punkte durch die Umsatzdaten jeder einzelnen Region. So wird die Form des Trends beibehalten, während die vorhergesagten Werte an den historischen Umsatzzahlen für jede Region und jedes Modell ausgerichtet werden.  
  
## <a name="performing-cross-prediction-with-a-time-series-model"></a>Kreuzvorhersagen mit einem Zeitreihenmodell  
 Das Verfahren, die Daten aus einer Reihe zur Vorhersage von Trends in einer anderen Reihe zu verwenden, wird "Kreuzvorhersage" genannt. Sie können Kreuzvorhersagen in vielen Szenarien verwenden: Sie könnten z. B. entscheiden, dass die Verkäufe von Fernsehern gute Rückschlüsse bei der Vorhersage der wirtschaftlichen Aktivität allgemein sind, und wenden ein an Umsatzdaten von Fernsehern trainiertes Modell auf allgemeine Wirtschaftsdaten an.  
  
 In SQL Server Data Mining, führen Sie kreuzvorhersagen mit dem Parameter REPLACE_MODEL_CASES innerhalb der Argumente der Funktion [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).  
  
 In der nächsten Aufgabe lernen Sie, wie REPLACE_MODEL_CASES verwendet wird. Sie erstellen aus den zusammengeführten Weltumsatzdaten ein Modell und dann eine Vorhersageabfrage, die das allgemeine Modell den Ersatzdaten zuordnet.  
  
 Es wird davon ausgegangen, dass Sie inzwischen mit dem Erstellen von Data Mining-Modelle vertraut sind; daher wurden die Anweisungen zum Erstellen des Modells vereinfacht.  
  
#### <a name="to-build-a-mining-structure-and-mining-model-using-the-aggregated-data"></a>So erstellen Sie eine Miningstruktur und ein Miningmodell mit den aggregierten Daten  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Miningstrukturen**, und wählen Sie dann **neue Miningstruktur** Data Mining-Assistenten zu starten.  
  
2.  Wählen Sie im Data Mining-Assistenten folgende Optionen aus:  
  
    -   Algorithmus: Microsoft Time Series  
  
    -   Verwenden Sie die Datenquelle, die Sie in dieser fortgeschrittenen Lektion bereits als Quelle für das Modell erstellt haben. Finden Sie unter [erweiterte Zeitreihenvorhersagen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md).  
  
         Datenquellensicht: `AllRegions`  
  
    -   Wählen Sie die folgenden Spalten für den Reihenschlüssel und den Zeitschlüssel aus:  
  
         Schlüsselzeit: ReportingDate  
  
         Schlüssel: Region  
  
    -   Wählen Sie die folgenden Spalten für `Input` und `Predict` aus:  
  
         SumQty  
  
         SumAmt  
  
         AvgAmt  
  
         AvgQty  
  
    -   Für **Miningstrukturname**, Typ: `All Regions`  
  
    -   Für **Miningmodellname**, Typ: `All Regions`  
  
3.  Verarbeiten Sie die neue Struktur und das neue Modell.  
  
#### <a name="to-build-the-prediction-query-and-map-the-replacement-data"></a>So erstellen Sie die Vorhersageabfrage und ordnen Ersetzungsdaten zu  
  
1.  Wenn das Modell nicht bereits geöffnet ist, doppelklicken Sie auf die AllRegions-Struktur, und klicken Sie im Data Mining-Designer auf die **Miningmodellvorhersage** Registerkarte.  
  
2.  In der **Miningmodell** Bereich, der das Modell AllRegions bereits ausgewählt sein sollte. Wenn sie nicht ausgewählt ist, klicken Sie auf **Modell auswählen**, und wählen Sie dann das AllRegions-Modell.  
  
3.  In der **Eingabetabelle(n)** Bereich, klicken Sie auf **Falltabelle auswählen**.  
  
4.  In der **Tabelle auswählen** (Dialogfeld), ändern Sie die Datenquelle in T1000 Pacific Region, und klicken Sie dann auf **OK**.  
  
5.  Mit der rechten Maustaste der Joinlinie zwischen dem Miningmodell und die Eingabedaten, und wählen Sie **Verbindungen ändern**. Ordnen Sie die Daten in der Datenquellensicht wie folgt dem Modell zu:  
  
    1.  Stellen Sie sicher, dass die ReportingDate-Spalte im Miningmodell der ReportingDate-Spalte in den Eingabedaten zugeordnet ist.  
  
    2.  In der **Zuordnung ändern** Dialogfeld, in der Zeile für die modellspalte AvgQty, klicken Sie auf unter **Tabellenspalte** und wählen Sie dann T1000 Pacific.Quantity aus. Klicken Sie auf **OK**.  
  
         In diesem Schritt ordnen Sie die Spalte zu, die Sie im Modell für die Vorhersage der Durchschnittsmenge aus den tatsächlichen Umsatzdaten der Reihe T1000 erstellt haben.  
  
    3.  Werden Sie nicht die Region-Spalte im Modell keiner Eingabespalte zugeordnet.  
  
         Da die Daten aller Reihen im Modell aggregiert sind, findet kein Abgleich der Reihenwerte wie T1000 Pacific statt, und bei der Ausführung der Vorhersageabfrage wird ein Fehler ausgegeben.  
  
6.  Nun erstellen Sie die Vorhersageabfrage.  
  
     Fügen Sie zunächst den Ergebnissen eine Spalte hinzu, die die Bezeichnung "AllRegions" aus dem Modell zusammen mit den Vorhersagen ausgibt. So wissen Sie, dass die Ergebnisse auf dem allgemeinen Modell basieren.  
  
    1.  Klicken Sie im Raster auf der ersten leeren Zeile unter **Quelle**, und wählen Sie dann AllRegions-Miningmodell.  
  
    2.  Für **Feld**, Region auswählen.  
  
    3.  Für **Alias**, Typ **Model Used**.  
  
7.  Im nächsten Schritt fügen Sie den Ergebnissen eine weitere Bezeichnung hinzu, der Sie entnehmen können, auf welche Reihe sich die Vorhersage bezieht.  
  
    1.  Klicken Sie auf eine leere Zeile, und wählen Sie unter **Quelle**Option **benutzerdefinierter Ausdruck**.  
  
    2.  In der **Alias** Spalte, Datentyp **ModelRegion**.  
  
    3.  In der **Kriterium/Argument** Spalte, Datentyp `'T1000 Pacific'`.  
  
8.  Nun richten Sie die Funktion für die Kreuzvorhersage ein.  
  
    1.  Klicken Sie auf eine leere Zeile, und wählen Sie unter **Quelle**Option **Vorhersagefunktion**.  
  
    2.  In der **Feld** Spalte **PredictTimeSeries**.  
  
    3.  Für **Alias**, Typ **Predicted Values**.  
  
    4.  Ziehen Sie das Feld AvgQty aus dem **Miningmodell** -Bereich in die **Kriterium/Argument** Spalte mithilfe des Drag & Drop-Vorgangs.  
  
    5.  In der **Kriterium/Argument** Spalte, nach dem Namen des Felds geben Sie den folgenden Text: `,5, REPLACE_MODEL_CASES`  
  
         Den vollständigen Text der der **Kriterium/Argument** Textfeld sollte wie folgt lauten: `[AllRegions].[AvgQty],5,REPLACE_MODEL_CASES`  
  
9. Klicken Sie auf **Ergebnisse**.  
  
## <a name="creating-the-cross-prediction-query-in-dmx"></a>Erstellen der Kreuzvorhersage-Abfrage in DMX  
 Möglicherweise ist Ihnen ein Problem aufgefallen, das bei Kreuzvorhersagen besteht: Sie müssen nämlich für jede Reihe eine neue Abfrage erstellen, um so das allgemeine Modell auf andere Datenreihen anwenden und jeden Satz von Eingaben dem Modell zuordnen zu können.  
  
 Sie haben aber die Möglichkeit, die Abfrage nicht im Designer zu erstellen, sondern zu DMX zu wechseln und die von Ihnen erstellte DMX-Anweisung zu bearbeiten. Die folgende DMX-Anweisung stellt beispielsweise die Abfrage dar, die Sie gerade erstellt haben:  
  
```  
SELECT  
      ([All Regions].[Region]) as [Model Used],  
      ('T-1000 Pacific') as [ModelRegion],  
      (PredictTimeSeries([All Regions].[Avg Qty],5, REPLACE_MODEL_CASES)) as [Predicted Quantity]  
     FROM [All Regions]  
PREDICTION JOIN  
    OPENQUERY([Adventure Works DW2003R2], 'SELECT [ReportingDate] FROM  
      (  
       SELECT  ReportingDate, ModelRegion, Quantity, Amount   
       FROM dbo.vTimeSeries   
       WHERE (ModelRegion = N''T1000 Pacific'')  
       ) as [T1000 Pacific]    ')   
    AS t  
ON   
[All Regions].[Reporting Date] = t.[ReportingDate]   
AND   
[All Regions].[Avg Qty] = t.[Quantity]  
```  
  
 Wenn Sie sie auf ein anderes Modell anwenden möchten, müssen Sie nur die Filterbedingung im Abfrageausdruck ersetzen und die mit den einzelnen Ergebnissen verknüpften Bezeichnungen aktualisieren.  
  
 Wenn Sie beispielsweise die Filterbedingungen und die Spaltenbezeichnungen ändern, indem Sie "Pacific" durch "North America" ersetzen, erhalten Sie Vorhersagen für das T1000-Produkt in Nordamerika auf Basis des allgemeinen Modells.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Vergleichen von Vorhersagen für Forecasting-Modellen &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Abfragebeispiel Zeitreihenmodell](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)   
 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)  
  
  
