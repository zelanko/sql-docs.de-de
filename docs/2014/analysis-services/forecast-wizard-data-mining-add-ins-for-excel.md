---
title: Planungs-Assistent (Data Mining-Add-ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- forecasting [data mining]
- time series [data mining]
ms.assetid: c5b33f75-42d4-4598-89e7-94815c142ce6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f0717d8a81cc89897de005144dd631d23da42137
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66081025"
---
# <a name="forecast-wizard-data-mining-add-ins-for-excel"></a>Planungs-Assistent (Data Mining-Add-Ins für Excel)
  ![Zuordnungs-Assistenten im Data Mining-Menüband](media/dmc-forecast.gif "Zuordnungs-Assistent im Data Mining-Menüband")  
  
 Mit dem Planungs-Assistenten können Sie Werte in einer Zeitreihe vorhersagen. Für den Planungs-Assistenten wird der [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus verwendet. Es handelt sich dabei um einen Regressionsalgorithmus, der für die Vorhersage kontinuierlicher Spalten (z. B. Produktverkaufszahlen) verwendet wird.  
  
 Jedes Planungsmodell muss eine Fallreihe enthalten. Damit ist die Spalte gemeint, die zwischen Punkten in einer Sequenz unterscheidet. Beispiel: Wenn Sie Vergangenheitsdaten verwenden, um Verkaufszahlen über mehrere Monate hinweg zu planen, würden Sie als Fallreihe eine Spalte mit einer Datenreihe verwenden.  
  
 Sie können anhand eines Planungsmodells Vorhersagen erstellen, ohne neue Eingabedaten bereitzustellen.  
  
 Die [prognostizieren &#40;Tabellenanalysetools für Excel&#41; ](forecast-table-analysis-tools-for-excel.md) tool in der **analysieren** Menüband, außerdem können Sie Planungsmodelle erstellen, ist aber weniger anpassbar und können nur Daten in Excel-Tabellen verwenden.  
  
## <a name="using-the-forecast-wizard"></a>Verwenden des Planungs-Assistenten  
  
1.  In der **Data Mining** des Menübands, klicken Sie auf **prognostizieren**.  
  
2.  In der **Quelldaten auswählen**, wählen Sie die Excel-Tabelle, Bereich oder externen Datenquelle, die als Eingaben verwendet.  
  
     Wenn Sie eine externe Datenquelle verwenden, können Sie benutzerdefinierte Sichten oder Abfragen definieren und als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle speichern.  
  
3.  Auf der **Forecasting** Seite für **Zeitstempel**, wählen Sie eine Spalte, die eindeutige numerische Werte (Dies schließt Datums-und Uhrzeitwerte) enthält, die als fallserie verwendet werden können. Die Datenquelle muss nach dieser Spalte in aufsteigender Reihenfolge sortiert sein.  
  
     Wenn Ihre Daten nicht mit eine solchen Spalte verfügt, können Sie die Option \<kein Timestamp >. Der Assistent fügt eine eindeutige Sortierspalte für die Eingabedaten hinzu. Daher müssen Sie sicherstellen, dass die Daten wie gewünscht sortiert sind, bevor Sie den Assistenten ausführen und diese Option auswählen.  
  
4.  Sie können optional klicken **Parameter** und das Verhalten des Miningmodells anzupassen.  
  
     Planungsmodelle unterstützen verschiedene Algorithmen:  
  
    -   ARIMA  
  
    -   ARTXP (Regressionsmodelltyp)  
  
    -   ARTXP und ARIMA in Kombination  
  
     Weitere Informationen zu den Unterschieden finden Sie unter [Microsoft Time Series Algorithm Technical Reference](data-mining/microsoft-time-series-algorithm-technical-reference.md).  
  
     Sie können außerdem Periodizitätshinweise hinzufügen, Glättungsoptionen angeben und Regressionsoptionen für das Modell anpassen.  
  
5.  Auf der **Fertig stellen** Seite Geben Sie einen beschreibenden Namen für das DataSet und das Modell, und legen Sie die folgenden Optionen, die steuern, wie Sie mit dem fertigen Modell arbeiten:  
  
    -   **Modell durchsuchen,**. Wenn diese Option ausgewählt ist, sobald der Assistent nach Abschluss der Verarbeitung des Modells, öffnen ein **Durchsuchen** Fenster können Sie die Ergebnisse zu untersuchen. Der Inhalt des Viewers hängt vom Typ des erstellten Modells ab. Weitere Informationen finden Sie unter [Durchsuchen eines Modells Vorhersagen](browsing-a-forecasting-model.md).  
  
    -   **Aktivieren von Drillthrough**. Wählen Sie diese Option aus, um die zugrunde liegenden Daten des fertigen Modells anzuzeigen. Diese Option ist nur verfügbar, wenn Sie ein Decision Tree-Modell erstellen.  
  
    -   **Temporäres Modell**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
### <a name="requirements"></a>Anforderungen  
 Die Daten sollten mindestens eine Spalte umfassen, die als Zeitreihe verwendet werden kann. Die Werte in dieser Spalte sollten eindeutig und kontinuierlich sein – d. h., es sollten keine Lücken vorhanden sein. Bevor Sie den Assistenten ausführen, sortieren Sie die Daten nach der Zeitreihenspalte in aufsteigender Reihenfolge.  
  
 Falls Ihre Daten keine Zeit- oder Datumsspalte enthalten, können Sie eine beliebige numerische Reihe zuweisen oder die Spalte vom Assistenten erstellen lassen. Wenn der Assistent die Reihensortierspalte erstellen soll, vergewissern Sie sich, dass die anderen Spalten in der gewünschten Reihenfolge sortiert sind, bevor Sie den Assistenten starten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Datamining-Modells](creating-a-data-mining-model.md)   
 [Prognostizieren &#40;Tabellenanalysetools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)   
 [Durchsuchen eines Planungsmodells](browsing-a-forecasting-model.md)  
  
  
