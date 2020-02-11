---
title: Planungs-Assistent (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081025"
---
# <a name="forecast-wizard-data-mining-add-ins-for-excel"></a>Planungs-Assistent (Data Mining-Add-Ins für Excel)
  ![Zuordnungs-Assistent (Data Mining-Menüband)](media/dmc-forecast.gif "Zuordnungs-Assistent (Data Mining-Menüband)")  
  
 Mit dem Planungs-Assistenten können Sie Werte in einer Zeitreihe vorhersagen. Für den Planungs-Assistenten wird der [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus verwendet. Es handelt sich dabei um einen Regressionsalgorithmus, der für die Vorhersage kontinuierlicher Spalten (z. B. Produktverkaufszahlen) verwendet wird.  
  
 Jedes Planungsmodell muss eine Fallreihe enthalten. Damit ist die Spalte gemeint, die zwischen Punkten in einer Sequenz unterscheidet. Beispiel: Wenn Sie Vergangenheitsdaten verwenden, um Verkaufszahlen über mehrere Monate hinweg zu planen, würden Sie als Fallreihe eine Spalte mit einer Datenreihe verwenden.  
  
 Sie können anhand eines Planungsmodells Vorhersagen erstellen, ohne neue Eingabedaten bereitzustellen.  
  
 Mit dem [Vorhersage &#40;Tabellenanalyse Tools für Excel&#41;](forecast-table-analysis-tools-for-excel.md) Tool können Sie im Menüband **analysieren** auch Vorhersagemodelle erstellen, die jedoch weniger anpassbar sind und nur Daten in Excel-Tabellen verwenden können.  
  
## <a name="using-the-forecast-wizard"></a>Verwenden des Planungs-Assistenten  
  
1.  Klicken Sie im **Data Mining** -Menüband auf **Vorhersagen**.  
  
2.  Wählen Sie in den **Quelldaten auswählen**die Excel-Tabelle, den Bereich oder die externe Datenquelle aus, die als Eingaben verwendet werden soll.  
  
     Wenn Sie eine externe Datenquelle verwenden, können Sie benutzerdefinierte Sichten oder Abfragen definieren und als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle speichern.  
  
3.  Wählen Sie auf der Seite **vorher** sagen für **Zeitstempel**eine Spalte aus, die einen eindeutigen numerischen Wert (einschließlich Datums-und Uhrzeitwerte) enthält, die als Fallreihe verwendet werden kann. Die Datenquelle muss nach dieser Spalte in aufsteigender Reihenfolge sortiert sein.  
  
     Wenn Ihre Daten nicht über eine solche Spalte verfügen, können Sie die Option \<kein Zeitstempel> verwenden. Der Assistent fügt eine eindeutige Sortierspalte für die Eingabedaten hinzu. Daher müssen Sie sicherstellen, dass die Daten wie gewünscht sortiert sind, bevor Sie den Assistenten ausführen und diese Option auswählen.  
  
4.  Optional können Sie auf **Parameter** klicken und das Verhalten des Mining Modells anpassen.  
  
     Planungsmodelle unterstützen verschiedene Algorithmen:  
  
    -   ARIMA  
  
    -   ARTXP (Regressionsmodelltyp)  
  
    -   ARTXP und ARIMA in Kombination  
  
     Weitere Informationen zu den Unterschieden finden Sie unter [Technische Referenz für den Microsoft Time Series-Algorithmus](data-mining/microsoft-time-series-algorithm-technical-reference.md).  
  
     Sie können außerdem Periodizitätshinweise hinzufügen, Glättungsoptionen angeben und Regressionsoptionen für das Modell anpassen.  
  
5.  Geben Sie auf der Seite **Fertig** stellen einen beschreibenden Namen für das DataSet und das Modell an, und legen Sie die folgenden Optionen fest, mit denen die Arbeit mit dem fertigen Modell gesteuert wird:  
  
    -   **Modell durchsuchen**. Wenn diese Option ausgewählt ist, wird das Fenster **Durchsuchen** geöffnet, sobald der Assistent die Verarbeitung des Modells abgeschlossen hat, damit Sie die Ergebnisse untersuchen können. Der Inhalt des Viewers hängt vom Typ des erstellten Modells ab. Weitere Informationen finden Sie unter durch [Suchen eines Vorhersagemodells](browsing-a-forecasting-model.md).  
  
    -   **Drillthrough aktivieren**. Wählen Sie diese Option aus, um die zugrunde liegenden Daten des fertigen Modells anzuzeigen. Diese Option ist nur verfügbar, wenn Sie ein Decision Tree-Modell erstellen.  
  
    -   **Temporäres Modell verwenden**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Die Daten sollten mindestens eine Spalte umfassen, die als Zeitreihe verwendet werden kann. Die Werte in dieser Spalte sollten eindeutig und fortlaufend sein, d. h., es sollten keine Lücken vorhanden sein. Bevor Sie den Assistenten ausführen, sortieren Sie die Daten nach der Zeitreihenspalte in aufsteigender Reihenfolge.  
  
 Falls Ihre Daten keine Zeit- oder Datumsspalte enthalten, können Sie eine beliebige numerische Reihe zuweisen oder die Spalte vom Assistenten erstellen lassen. Wenn der Assistent die Reihensortierspalte erstellen soll, vergewissern Sie sich, dass die anderen Spalten in der gewünschten Reihenfolge sortiert sind, bevor Sie den Assistenten starten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)   
 [Vorhersage &#40;Tabellenanalyse Tools für Excel&#41;](forecast-table-analysis-tools-for-excel.md)   
 [Durchsuchen eines Planungsmodells](browsing-a-forecasting-model.md)  
  
  
