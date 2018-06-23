---
title: Zeitreihenvorhersagen mit aktualisierten Daten (Data Mining-Lernprogramm für fortgeschrittene) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
caps.latest.revision: 23
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3478a52657e26fa8e376e88bc83a5c4d9813cdc8
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312358"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a>Erstellen von Zeitreihenvorhersagen mit aktualisierten Daten (Data Mining-Lernprogramm für Fortgeschrittene)
    
## <a name="creating-predictions-using-the-extended-sales-data"></a>Erstellen von Vorhersagen aus erweiterten Verkaufsdaten  
 In dieser Lektion erstellen Sie eine Vorhersageabfrage, durch die dem Modell die neuen Umsatzdaten hinzugefügt werden. Indem Sie das Modell mit neuen Daten erweitern, erhalten Sie aktuelle Vorhersagen, in denen die neuesten Datenpunkte enthalten sind.  
  
 Erstellen von zeitreihenvorhersagen, die neue Daten zu verwenden, ist einfach: Sie fügen Sie einfach den Parameter EXTEND_MODEL_CASES auf die [PredictTimeSeries &#40;DMX&#41; ](/sql/dmx/predicttimeseries-dmx) funktionieren, geben Sie die Quelle der neuen Daten und wie viele Vorhersagen, die Sie abrufen möchten.  
  
> [!WARNING]  
>  Der Parameter EXTEND_MODEL_CASES ist optional; standardmäßig wird das Modell immer dann erweitert, wenn Sie eine Vorhersageabfrage für eine Zeitreihe erstellen, indem neue Daten als Eingaben verknüpft werden.  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a>So erstellen Sie die Vorhersageabfrage und fügen neue Daten hinzu  
  
1.  Wenn das Modell nicht bereits geöffnet ist, doppelklicken Sie auf die Forecasting-Struktur und im Data Mining-Designer, klicken Sie auf die **Miningmodellvorhersage** Registerkarte.  
  
2.  In der **Miningmodell** Bereich, der das Modell Forecasting bereits ausgewählt sein sollte. Wenn es nicht aktiviert ist, klicken Sie auf **Modell auswählen**, und wählen Sie dann das Modell Forecasting.  
  
3.  In der **Eingabetabelle(n)** Bereich, klicken Sie auf **Falltabelle auswählen**.  
  
4.  In der **Tabelle auswählen** Dialogfeld wählen die Datenquelle [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].  
  
     Aus der Liste der Datenquellensichten, wählen Sie NewSalesData, und klicken Sie dann auf **OK**.  
  
5.  Mit der rechten Maustaste in der Oberfläche des Entwurfsbereichs, und wählen Sie **Verbindungen ändern**.  
  
6.  Mithilfe der **Zuordnung ändern** Dialogfeld ordnen die Spalten im Modell den Spalten in den externen Daten wie folgt:  
  
    -   Ordnen Sie die ReportingDate-Spalte im Miningmodell der NewDate-Spalte in den Eingabedaten an.  
  
    -   Ordnen Sie die Menge-Spalte im Miningmodell der NewAmount-Spalte in den Eingabedaten an.  
  
    -   Ordnen Sie die Menge-Spalte im Miningmodell der NewQty-Spalte in den Eingabedaten an.  
  
    -   Der reihenspalte in den Eingabedaten die ModelRegion-Spalte im Miningmodell zuordnen.  
  
7.  Nun erstellen Sie die Vorhersageabfrage.  
  
     Fügen Sie der Vorhersageabfrage zuerst eine Spalte für die Ausgabe der Reihe hinzu, für die Vorhersage gültig ist.  
  
    1.  Klicken Sie im Raster auf der ersten leeren Zeile unter **Quelle**, und wählen Sie dann Forecasting.  
  
    2.  In der **Feld** Spalte wählen Model Region und für **Alias**, Typ `Model Region`.  
  
8.  Fügen Sie dann die Vorhersagefunktion hinzu und bearbeiten Sie sie.  
  
    1.  Klicken Sie auf eine leere Zeile, und wählen Sie unter **Quelle**Option **Vorhersagefunktion**.  
  
    2.  Für **Feld**Option **PredictTimeSeries**.  
  
    3.  Für **Alias**, Typ **Predicted Values**.  
  
    4.  Ziehen Sie das Feld Menge aus der **Miningmodell** -Bereich in die **Kriterium/Argument** Spalte.  
  
    5.  In der **Kriterium/Argument** Spalte Geben Sie hinter dem Feldnamen, den folgenden Text: **5, EXTEND_MODEL_CASES**  
  
         Der vollständige Text des der **Kriterium/Argument** Textfeld sollte wie folgt lauten: `[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`  
  
9. Klicken Sie auf **Ergebnisse** und überprüfen Sie die Ergebnisse.  
  
     Die Vorhersagen beginnen im Juli (erste Zeitscheibe nach dem Ende der ursprünglichen Daten) und enden im November (fünfte Zeitscheibe nach dem Ende der ursprünglichen Daten).  
  
 Wie Sie sehen, müssen Sie das Ende der alten Daten wie auch die Anzahl der Zeitscheiben in den neuen Daten kennen, um effektiv mit Vorhersageabfragen dieses Typs zu arbeiten.  
  
 In diesem Modell endete die ursprüngliche Datenreihe z. B. im Juni, und die Daten beziehen sich auf die Monate Juli, August und September.  
  
 Vorhersagen, die EXTEND_MODEL_CASES verwenden, beginnen immer am Ende der ursprünglichen Datenreihe. Wenn Sie nur die Vorhersagen für die unbekannten Monate abrufen möchten, müssen Sie daher den Ausgangspunkt und den Endpunkt der Vorhersage angeben. Beide Werte werden als eine Reihe von Zeitscheiben angegeben, die am Ende der alten Daten startet.  
  
 Das folgende Verfahren veranschaulicht das Vorgehen.  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a>Ändern der Ausgangs- und Endpunkte von Vorhersagen  
  
1.  Klicken Sie im Generator für Vorhersageabfragen auf **Abfrage** zur DMX-Ansicht wechseln.  
  
2.  Suchen Sie die DMX-Anweisung, die die PredictTimeSeries-Funktion enthält, und ändern Sie sie folgendermaßen:  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  Klicken Sie auf **Ergebnisse** und überprüfen Sie die Ergebnisse.  
  
     Nun beginnen die Vorhersagen im Oktober (vierte Zeitscheibe bei Zählung vom Ende der ursprünglichen Daten) und endet im Dezember (sechste Zeitscheibe bei Zählung vom Ende der ursprünglichen Daten).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Zeitreihenvorhersagen mit Ersetzungsdaten &#40;fortgeschrittene Data Mining-Lernprogramm&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Miningmodellinhalt für Zeitreihenmodelle &#40;Analysis Services – Datamining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
