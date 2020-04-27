---
title: Anpassen und Verarbeiten des Vorhersagemodells (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63249403"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a>Anpassen und Verarbeiten des Forecasting-Modells (Data Mining-Lernprogramm für Fortgeschrittene)
  Der [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus umfasst mehrere Parameter, die sich darauf auswirken, wie ein Modell angelegt und wie die Zeitdaten analysiert werden. Eine Änderung dieser Eigenschaften kann sich wesentlich auf die Methode auswirken, mit der das Miningmodell Vorhersagen trifft.  
  
 Führen Sie für diesen Task im Lernprogramm die folgenden Tasks aus, das Modell zu ändern:  
  
1.  Sie passen die Art und Weise an, in der das Modell Zeiträume behandelt, indem Sie einen neuen Wert für den *PERIODICITY_HINT* -Parameter hinzufügen.  
  
2.  Sie erfahren über zwei andere wichtige Parameter für den Microsoft Time Series-Algorithmus: FORECAST_METHOD, mit dem Sie die zur Prognoseerstellung verwendete Methode festlegen, und PREDICTION_SMOOTHING, mit dem Sie den Übergang von langfristigen und kurzfristigen Vorhersagen anpassen können.  
  
3.  Optional geben Sie dem Algorithmus an, wie fehlende Werte zugeschrieben werden sollen.  
  
4.  Nachdem die Änderungen vorgenommen wurden, stellen Sie das Modell bereit und verarbeiten es.  
  
## <a name="setting-time-series-parameters"></a>Festlegen von Zeitreihenparametern  
 **Periodizitätshinweise**  
  
 Der *PERIODICITY_HINT* -Parameter stellt dem Algorithmus Informationen zu zusätzlichen Zeiträumen bereit, die in den Daten erwartet werden. Standardmäßig versuchen Zeitreihenmodelle, automatisch ein Muster in den Daten zu erkennen. Wenn Sie jedoch bereits den erwarteten Zeitzyklus kennen, kann ein Periodizitätshinweis die Genauigkeit des Modells eventuell verbessern. Wenn Sie jedoch den falschen Periodizitätshinweis geben, kann dies die Genauigkeit verringern; wenn Sie also nicht sicher sind, welcher Wert verwendet werden soll, ist es am besten, beim Standard zu bleiben.  
  
 Die Sicht beispielsweise, die für dieses Modell verwendet wird, aggregiert monatlich Umsatzdaten von [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Daher steht jede vom Modell verwendete Zeitscheibe einen Monat dar, und alle Vorhersagen werden in Bezug auf Monate getroffen. Da es 12 Monate in einem Jahr gibt, und Sie erwarten, dass sich die Verkaufs Muster mehrmals oder seltener wiederholen, legen Sie den *PERIODICITY_HINT* -Parameter `12`auf fest, um anzugeben, dass 12 Zeit Scheiben (Monate) einen kompletten Verkaufs Zeitraum darstellen.  
  
 **Prognosemethode**  
  
 Der *FORECAST_METHOD* -Parameter steuert, ob der Time Series-Algorithmus für kurzfristige oder langfristige Vorhersagen optimiert ist. Standardmäßig ist der *FORECAST_METHOD* -Parameter auf Mixed festgelegt. Dies bedeutet, dass zwei verschiedene Algorithmen gemischt und ausgeglichen werden, um gute Ergebnisse für die kurzfristige und langfristige Vorhersage bereitzustellen.  
  
 Wenn Sie jedoch wissen, dass Sie einen bestimmten Algorithmus verwenden möchten, können Sie den Wert entweder in ARIMA oder ARTxp ändern.  
  
 **Gewichtung langfristiger und kurzfristiger Vorhersagen**  
  
 Mit dem PREDICTION_SMOOTHING-Parameter können Sie auch die Methode anpassen, mit der langfristige und kurzfristige Vorhersagen kombiniert werden. Der Parameter ist standardmäßig auf 0,5 festgelegt; dies stellt den besten Kompromiss für die Gesamtgenauigkeit dar.  
  
#### <a name="to-change-the-algorithm-parameters"></a>So ändern Sie die Algorithmusparameter  
  
1.  Klicken Sie auf der Registerkarte **Mining Modelle** mit der rechten Maustaste auf **Prognose**, und wählen Sie **Algorithmusparameter festlegen**  
  
2.  Klicken Sie `PERIODICITY_HINT` in der Zeile des Dialog Felds **Algorithmusparameter** auf die Spalte **Wert** , und geben `{12}`Sie dann ein, einschließlich der geschweiften Klammern.  
  
     Standardmäßig fügt der Algorithmus auch den Wert {1} hinzu.  
  
3.  Überprüfen `FORECAST_METHOD` Sie in der Zeile, ob das Textfeld **Wert** entweder leer ist oder `MIXED`auf festgelegt ist. Wenn ein anderer Wert eingegeben wurde, geben `MIXED` Sie ein, um den Parameter wieder in den Standardwert zu ändern.  
  
4.  Überprüfen Sie in der **PREDICTION_SMOOTHING** Zeile, ob das Textfeld **Wert** entweder leer ist oder auf 0,5 festgelegt ist. Wenn ein anderer Wert eingegeben wurde, klicken Sie auf **Wert** , `0.5` und geben Sie ein, um den Parameter wieder in den Standardwert zu ändern.  
  
    > [!NOTE]  
    >  Der PREDICTION_SMOOTHING-Parameter ist nur in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise verfügbar. Sie können den Wert des PREDICTION_SMOOTHING-Parameters daher in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard nicht ändern. Das Standardverhalten sieht jedoch die Verwendung beider Algorithmen mit gleicher Gewichtung vor.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="handling-missing-data-optional"></a>Behandeln von unvollständigen Daten (optional)  
 Es kann häufig vorkommen, dass Verkaufsdaten unvollständig und mit NULL-Werten angegeben sind; auch kann es sein, dass die entsprechenden Daten nicht rechtzeitig von der Niederlassung gemeldet wurden und das Ende der Reihe eine leere Zelle aufweist. In derartigen Szenarien wird der folgende Fehler von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generiert, und das Modell wird nicht verarbeitet.  
  
 "Fehler (Data Mining): nicht synchronisierte Zeitstempel, beginnend \<mit Reihen Reihen Name>, des Mining Modells \<, Modellname>. Alle Zeitreihen müssen an der gleichen Zeitmarkierung enden und dürfen keine beliebig fehlenden Datenpunkte aufweisen. Wenn Sie den MISSING_VALUE_SUBSTITUTION-Parameter auf "Previous" oder auf eine numerische Konstante festlegen, werden nach Möglichkeit automatisch fehlende Datenpunkte ergänzt."  
  
 Sie können diese Fehlermeldung umgehen, indem Sie angeben, dass fehlende Werte von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatisch mit einer der folgenden Methoden bereitgestellt werden:  
  
-   Verwendung eines Mittelwerts. Dieser wird mit allen gültigen Werten in der gleichen Datenreihe berechnet.  
  
-   Verwendung des vorherigen Werts. Sie können mehrere fehlende Zellen durch vorherige Werte ersetzen; Sie können jedoch keine Anfangswerte auffüllen.  
  
-   Verwendung eines konstanten Werts, der vom Benutzer angegeben wird.  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a>So füllen Sie Lücken mit Durchschnittswerten  
  
1.  Klicken Sie auf der Registerkarte **Mining Modelle** mit der rechten Maustaste auf die Spalte **Prognose** , und wählen Sie **Algorithmusparameter festlegen**.  
  
2.  Klicken Sie im Dialogfeld **Algorithmusparameter** in der Zeile **MISSING_VALUE_SUBSTITUTION** auf die Spalte **Wert** , `Mean`und geben Sie ein.  
  
## <a name="build-the-model"></a>Erstellen des Modells  
 Um das Modell zu verwenden, müssen Sie es auf einem Server bereitstellen und dann verarbeiten, indem Sie die Trainingsdaten durch den Algorithmus verarbeiten lassen.  
  
#### <a name="to-process-the-forecasting-model"></a>So verarbeiten Sie das Prognosemodell  
  
1.  Klicken Sie im Menü **Miningmodell** von [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]auf **Miningstruktur und alle Modelle verarbeiten**.  
  
2.  Klicken Sie in der Meldung mit der Frage, ob Sie das Projekt erstellen und bereitstellen möchten, auf **Ja**.  
  
3.  Klicken Sie im Dialogfeld **Mining Struktur verarbeiten-vorher** sagen auf **Ausführen**.  
  
     Das Dialogfeld **Verarbeitungsstatus** wird geöffnet und zeigt Informationen zur Verarbeitung des Modells an. Die Verarbeitung des Modells kann einige Zeit in Anspruch nehmen.  
  
4.  Nachdem die Verarbeitung abgeschlossen ist, klicken Sie auf **Schließen** , um das Dialogfeld **Verarbeitungsstatus** zu schließen.  
  
5.  Klicken Sie erneut auf schließen, um das Dialogfeld **Mining Struktur verarbeiten-vorher** sagen zu **Schließen** .  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Untersuchen des Planungs Modells &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
