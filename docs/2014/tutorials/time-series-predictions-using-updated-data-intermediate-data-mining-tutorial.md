---
title: Zeitreihen Vorhersagen mit aktualisierten Daten (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2017defaba74071b1a12bee14a5d8907e4c71cda
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067556"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a>Erstellen von Zeitreihenvorhersagen mit aktualisierten Daten (Data Mining-Lernprogramm für Fortgeschrittene)
    
## <a name="creating-predictions-using-the-extended-sales-data"></a>Erstellen von Vorhersagen aus erweiterten Verkaufsdaten  
 In dieser Lektion erstellen Sie eine Vorhersageabfrage, durch die dem Modell die neuen Umsatzdaten hinzugefügt werden. Indem Sie das Modell mit neuen Daten erweitern, erhalten Sie aktuelle Vorhersagen, in denen die neuesten Datenpunkte enthalten sind.  
  
 Das Erstellen von Zeitreihen Vorhersagen, die neue Daten verwenden, ist einfach: Sie fügen einfach den Parameter EXTEND_MODEL_CASES der Funktion " [prättimeseries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) " hinzu, geben die Quelle der neuen Daten an und geben an, wie viele Vorhersagen Sie erhalten möchten.  
  
> [!WARNING]  
>  Der Parameter EXTEND_MODEL_CASES ist optional; standardmäßig wird das Modell immer dann erweitert, wenn Sie eine Vorhersageabfrage für eine Zeitreihe erstellen, indem neue Daten als Eingaben verknüpft werden.  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a>So erstellen Sie die Vorhersageabfrage und fügen neue Daten hinzu  
  
1.  Wenn das Modell nicht bereits geöffnet ist, doppelklicken Sie auf die Planungsstruktur, und klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modellvorhersage** .  
  
2.  Im Bereich **Mining Modell** sollte die Modellvorhersage bereits ausgewählt sein. Wenn diese Option nicht ausgewählt ist, klicken Sie auf **Modell auswählen**, und wählen Sie dann das Modell Vorhersagen aus.  
  
3.  Klicken Sie im Bereich **Eingabe Tabelle (n) auswählen** auf **Fall Tabelle auswählen**.  
  
4.  Wählen Sie im Dialogfeld **Tabelle auswählen** die Datenquelle aus [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].  
  
     Wählen Sie in der Liste der Datenquellen Sichten newsalesdata aus, und klicken Sie dann auf **OK**.  
  
5.  Klicken Sie mit der rechten Maustaste auf die Oberfläche des Entwurfs Bereichs und wählen Sie **Verbindungen ändern**aus.  
  
6.  Ordnen Sie im Dialogfeld **Zuordnung ändern** die Spalten im Modell den Spalten in den externen Daten wie folgt zu:  
  
    -   Ordnen Sie die ReportingDate-Spalte im Mining Modell der NewDate-Spalte in den Eingabedaten zu.  
  
    -   Ordnen Sie die Spalte Amount im Mining Modell der Spalte newamount in den Eingabedaten zu.  
  
    -   Ordnen Sie die Spalte Menge im Mining Modell der Spalte newqty in den Eingabedaten zu.  
  
    -   Ordnen Sie die Spalte ModelRegion im Mining Modell der Spalte Reihe in den Eingabedaten zu.  
  
7.  Nun erstellen Sie die Vorhersageabfrage.  
  
     Fügen Sie der Vorhersageabfrage zuerst eine Spalte für die Ausgabe der Reihe hinzu, für die Vorhersage gültig ist.  
  
    1.  Klicken Sie im Raster auf die erste leere Zeile unter **Quelle**, und wählen Sie dann Vorhersagen aus.  
  
    2.  Wählen Sie in der Spalte **Feld** die Option Modellbereich aus, und `Model Region`geben Sie als **Alias**ein.  
  
8.  Fügen Sie dann die Vorhersagefunktion hinzu und bearbeiten Sie sie.  
  
    1.  Klicken Sie auf eine leere Zeile, und wählen Sie unter **Quelle**die Option **Vorhersagefunktion**aus.  
  
    2.  Wählen Sie für **Feld**die Option **prättimeseries**aus.  
  
    3.  Geben **** Sie als Alias **vorhergesagte Werte**ein.  
  
    4.  Ziehen Sie die FeldMenge aus dem Bereich **Mining Modell** in die Spalte **Kriterium/Argument** .  
  
    5.  Geben Sie in der Spalte **Kriterium/Argument** nach dem Feldnamen den folgenden Text ein: **5, EXTEND_MODEL_CASES**  
  
         Der vollständige Text des Textfelds **Kriterium/Argument** sollte wie folgt lauten:`[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`  
  
9. Klicken Sie auf **Ergebnisse** , und überprüfen Sie die Ergebnisse.  
  
     Die Vorhersagen beginnen im Juli (erste Zeitscheibe nach dem Ende der ursprünglichen Daten) und enden im November (fünfte Zeitscheibe nach dem Ende der ursprünglichen Daten).  
  
 Wie Sie sehen, müssen Sie das Ende der alten Daten wie auch die Anzahl der Zeitscheiben in den neuen Daten kennen, um effektiv mit Vorhersageabfragen dieses Typs zu arbeiten.  
  
 In diesem Modell endete die ursprüngliche Datenreihe z. B. im Juni, und die Daten beziehen sich auf die Monate Juli, August und September.  
  
 Vorhersagen, die EXTEND_MODEL_CASES verwenden, beginnen immer am Ende der ursprünglichen Datenreihe. Wenn Sie nur die Vorhersagen für die unbekannten Monate abrufen möchten, müssen Sie daher den Ausgangspunkt und den Endpunkt der Vorhersage angeben. Beide Werte werden als eine Reihe von Zeitscheiben angegeben, die am Ende der alten Daten startet.  
  
 Das folgende Verfahren veranschaulicht das Vorgehen.  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a>Ändern der Ausgangs- und Endpunkte von Vorhersagen  
  
1.  Klicken Sie in Vorhersage Abfrage-Generator auf **Abfrage** , um zur DMX-Ansicht zu wechseln.  
  
2.  Suchen Sie die DMX-Anweisung, die die PredictTimeSeries-Funktion enthält, und ändern Sie sie folgendermaßen:  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  Klicken Sie auf **Ergebnisse** , und überprüfen Sie die Ergebnisse.  
  
     Nun beginnen die Vorhersagen im Oktober (vierte Zeitscheibe bei Zählung vom Ende der ursprünglichen Daten) und endet im Dezember (sechste Zeitscheibe bei Zählung vom Ende der ursprünglichen Daten).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Zeitreihen Vorhersagen mit Ersetzungs Daten &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Mining Modell Inhalt von Zeitreihen Modellen &#40;Analysis Services Data Mining-&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
