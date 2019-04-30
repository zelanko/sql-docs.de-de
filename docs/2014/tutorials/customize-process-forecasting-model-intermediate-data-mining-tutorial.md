---
title: Anpassen und Verarbeiten des Forecasting-Modells (mittleres Datamining Tutorial) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4bd25e15-9d9e-4528-b7bc-ccb856643aec
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d2d0e73d1d9a4058ff63320552604b2bfa1bca8a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63249403"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a>Anpassen und Verarbeiten des Forecasting-Modells (Data Mining-Lernprogramm für Fortgeschrittene)
  Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus umfasst mehrere Parameter, die sich darauf auswirken, wie ein Modell angelegt und wie die Zeitdaten analysiert werden. Eine Änderung dieser Eigenschaften kann sich wesentlich auf die Methode auswirken, mit der das Miningmodell Vorhersagen trifft.  
  
 Führen Sie für diesen Task im Lernprogramm die folgenden Tasks aus, das Modell zu ändern:  
  
1.  Sie werden anpassen, wie das Modell Zeiträume behandelt, durch Hinzufügen eines neuen Werts für die *PERIODICITY_HINT* Parameter.  
  
2.  Lernen Sie zwei weitere wichtige Parameter für den Microsoft Time Series-Algorithmus ein: FORECAST_METHOD, mit dem Sie die zur prognoseerstellung verwendete Methode steuern können, und PREDICTION_SMOOTHING, mit dem Sie können anpassen, dem die Mischung der langfristigen und kurzfristigen Vorhersagen.  
  
3.  Optional geben Sie dem Algorithmus an, wie fehlende Werte zugeschrieben werden sollen.  
  
4.  Nachdem die Änderungen vorgenommen wurden, stellen Sie das Modell bereit und verarbeiten es.  
  
## <a name="setting-time-series-parameters"></a>Festlegen von Zeitreihenparametern  
 **Periodizitätshinweise**  
  
 Die *PERIODICITY_HINT* Parameter liefert den Algorithmus Informationen zu zusätzlichen Zeiträumen, die Sie erwarten, um die Daten anzuzeigen. Standardmäßig versuchen Zeitreihenmodelle, automatisch ein Muster in den Daten zu erkennen. Wenn Sie jedoch bereits den erwarteten Zeitzyklus kennen, kann ein Periodizitätshinweis die Genauigkeit des Modells eventuell verbessern. Wenn Sie jedoch den falschen Periodizitätshinweis geben, kann dies die Genauigkeit verringern; wenn Sie also nicht sicher sind, welcher Wert verwendet werden soll, ist es am besten, beim Standard zu bleiben.  
  
 Die Sicht beispielsweise, die für dieses Modell verwendet wird, aggregiert monatlich Umsatzdaten von [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Daher steht jede vom Modell verwendete Zeitscheibe einen Monat dar, und alle Vorhersagen werden in Bezug auf Monate getroffen. Da 12 Monate in einem Jahr vorhanden sind, und Sie erwarten, dass sich verkaufsmuster mehr oder weniger wiederholen jährlich, setzen Sie die *PERIODICITY_HINT* Parameter `12`, um anzugeben, dass 12 Zeitscheiben (Monate) bilden eine vollständigen Verkaufszyklus.  
  
 **Prognosemethode**  
  
 Die *FORECAST_METHOD* Parameter steuert, ob der Zeitreihenalgorithmus für kurz- oder langfristige Vorhersagen optimiert ist. In der Standardeinstellung die *FORECAST_METHOD* Parameter ist auf MIXED festgelegt, was bedeutet, dass zwei verschiedene Algorithmen sind Mittelweg aus Kurzzeit- und um gute Ergebnisse für die kurz- und langfristigen Vorhersagen bereitzustellen.  
  
 Wenn Sie wissen, dass Sie einen bestimmten Algorithmus verwenden möchten, können Sie den Wert jedoch auf ARTXP oder ARIMA ändern.  
  
 **Langfristiges Gewichten und. Kurzfristige Vorhersagen**  
  
 Mit dem PREDICTION_SMOOTHING-Parameter können Sie auch die Methode anpassen, mit der langfristige und kurzfristige Vorhersagen kombiniert werden. Der Parameter ist standardmäßig auf 0,5 festgelegt; dies stellt den besten Kompromiss für die Gesamtgenauigkeit dar.  
  
#### <a name="to-change-the-algorithm-parameters"></a>So ändern Sie die Algorithmusparameter  
  
1.  Auf der **Miningmodelle** Registerkarte der rechten Maustaste auf **Forecasting**, und wählen Sie **Algorithmusparameter festlegen**.  
  
2.  In der `PERIODICITY_HINT` Zeile die **Algorithmusparameter** Dialogfeld klicken Sie auf der **Wert** Spalte Geben Sie dann `{12}`, einschließlich der geschweiften Klammern.  
  
     Standardmäßig fügt der Algorithmus auch den Wert {1} hinzu.  
  
3.  In der `FORECAST_METHOD` Zeile, überprüfen Sie, ob die **Wert** Textfeld ist entweder leer oder festgelegt, `MIXED`. Wenn ein anderer Wert eingegeben wurde, geben Sie `MIXED` so ändern Sie den Parameter wieder auf den Standardwert.  
  
4.  In der **PREDICTION_SMOOTHING** Zeile, überprüfen Sie, ob die **Wert** Textfeld ist entweder leer oder den Wert auf 0,5. Wenn ein anderer Wert eingegeben wurde, klicken Sie auf **Wert** und `0.5` so ändern Sie den Parameter wieder auf den Standardwert.  
  
    > [!NOTE]  
    >  Der PREDICTION_SMOOTHING-Parameter ist nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise verfügbar. Sie können den Wert des PREDICTION_SMOOTHING-Parameters daher in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard nicht ändern. Das Standardverhalten sieht jedoch die Verwendung beider Algorithmen mit gleicher Gewichtung vor.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="handling-missing-data-optional"></a>Behandeln von unvollständigen Daten (optional)  
 Es kann häufig vorkommen, dass Verkaufsdaten unvollständig und mit NULL-Werten angegeben sind; auch kann es sein, dass die entsprechenden Daten nicht rechtzeitig von der Niederlassung gemeldet wurden und das Ende der Reihe eine leere Zelle aufweist. In derartigen Szenarien wird der folgende Fehler von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generiert, und das Modell wird nicht verarbeitet.  
  
 "Fehler (Datamining): Nicht synchronisierte Timestamps mit Reihen \<Reihenname >, des Miningmodells, \<Modellname >. Alle Zeitreihen müssen an der gleichen Zeitmarkierung enden und dürfen keine beliebig fehlenden Datenpunkte aufweisen. Wenn Sie den MISSING_VALUE_SUBSTITUTION-Parameter auf "Previous" oder auf eine numerische Konstante festlegen, werden nach Möglichkeit automatisch fehlende Datenpunkte ergänzt."  
  
 Sie können diese Fehlermeldung umgehen, indem Sie angeben, dass fehlende Werte von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatisch mit einer der folgenden Methoden bereitgestellt werden:  
  
-   Verwendung eines Mittelwerts. Dieser wird mit allen gültigen Werten in der gleichen Datenreihe berechnet.  
  
-   Verwendung des vorherigen Werts. Sie können mehrere fehlende Zellen durch vorherige Werte ersetzen; Sie können jedoch keine Anfangswerte auffüllen.  
  
-   Verwendung eines konstanten Werts, der vom Benutzer angegeben wird.  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a>So füllen Sie Lücken mit Durchschnittswerten  
  
1.  Auf der **Miningmodelle** Registerkarte der rechten Maustaste auf die **Forecasting** Spalte, und wählen **Algorithmusparameter festlegen**.  
  
2.  In der **Algorithmusparameter** Dialogfeld die **MISSING_VALUE_SUBSTITUTION** auf die **Wert** Spalte, und geben Sie `Mean`.  
  
## <a name="build-the-model"></a>Erstellen des Modells  
 Um das Modell zu verwenden, müssen Sie es auf einem Server bereitstellen und dann verarbeiten, indem Sie die Trainingsdaten durch den Algorithmus verarbeiten lassen.  
  
#### <a name="to-process-the-forecasting-model"></a>So verarbeiten Sie das Prognosemodell  
  
1.  Klicken Sie im Menü **Miningmodell** von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf **Miningstruktur und alle Modelle verarbeiten**.  
  
2.  Klicken Sie in der Meldung mit der Frage, ob Sie das Projekt erstellen und bereitstellen möchten, auf **Ja**.  
  
3.  In der **Miningstruktur verarbeiten - Forecasting** Dialogfeld klicken Sie auf **ausführen**.  
  
     Das Dialogfeld **Verarbeitungsstatus** wird geöffnet und zeigt Informationen zur Verarbeitung des Modells an. Die Verarbeitung des Modells kann einige Zeit in Anspruch nehmen.  
  
4.  Nachdem die Verarbeitung abgeschlossen ist, klicken Sie auf **Schließen** , um das Dialogfeld **Verarbeitungsstatus** zu schließen.  
  
5.  Klicken Sie auf **schließen** wieder zu schließen die **Miningstruktur verarbeiten - Forecasting** Dialogfeld.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Untersuchen des Planungserstellungsmodells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
