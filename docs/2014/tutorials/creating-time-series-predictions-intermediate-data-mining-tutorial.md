---
title: Erstellen von Zeitreihen Vorhersagen (Data Mining-Tutorial für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fb22cffa-ac99-4d34-ac4a-9c93068e33e8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ca1aa4022931c78f6139a8058c05adc707af5e77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63313889"
---
# <a name="creating-time-series-predictions-intermediate-data-mining-tutorial"></a>Erstellen von Zeitreihenvorhersagen (Data Mining-Lernprogramm für Fortgeschrittene)
  In den vorherigen Aufgaben dieser Lektion haben Sie ein Zeitreihenmodell erstellt und die Ergebnisse untersucht. 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] erstellt standardmäßig immer einen Satz von fünf (5) Vorhersagen für ein Zeitreihenmodell und zeigt die vorhergesagten Werte in einem Prognosediagramm an. Sie können Prognosen jedoch auch mithilfe von Data Mining Extensions (DMX)-Vorhersageabfragen erzeugen.  
  
 In dieser Aufgabe erstellen Sie eine Vorhersageabfrage, mit der die gleichen Vorhersagen wie im Viewer generiert werden. Diese Aufgabe geht davon aus, dass Sie die Lektionen im Lernprogramm zu den Data Mining-Grundlagen bereits abgeschlossen haben und dass Sie mit der Verwendung des Generators für Vorhersageabfragen vertraut sind. Im Folgenden lernen Sie, wie Sie Abfragen für Zeitreihenmodelle erstellen.  
  
## <a name="creating-time-series-predictions"></a>Erstellen von Zeitreihenvorhersagen  
 Der erste Schritt beim Erstellen einer Vorhersageabfrage besteht normalerweise in der Auswahl eines Miningmodells und einer Eingabetabelle. Ein Zeitreihenmodell benötigt jedoch für reguläre Vorhersagen keine zusätzliche Eingabe. Es ist daher nicht erforderlich, eine neue Datenquelle für Vorhersagen anzugeben, wenn Sie dem Modell keine Daten hinzufügen oder Daten ersetzen.  
  
 Sie müssen für diese Lektion die Anzahl der Vorhersageschritte angeben. Sie können den Namen der Reihe angeben, um eine Vorhersage für eine bestimmte Kombination aus Produkt und Region zu erhalten.  
  
#### <a name="to-select-a-model-and-input-table"></a>So wählen Sie ein Modell und eine Eingabetabelle aus  
  
1.  Klicken Sie im Data Mining-Designer auf der Registerkarte **Mining Modellvorhersage** im Feld **Mining Modell** auf **Modell auswählen**.  
  
2.  Erweitern Sie im Dialogfeld **Mining Modell auswählen** die Planungsstruktur, wählen Sie das **Vorhersage** Modell aus der Liste aus, und klicken Sie dann auf **OK**.  
  
3.  Ignorieren Sie das Kontrollkästchen **Eingabe Tabelle (n) auswählen** .  
  
    > [!NOTE]  
    >  Bei einem Zeitreihenmodell müssen Sie keine separaten Eingabewerte angeben, wenn Sie keine Kreuzvorhersagen treffen.  
  
4.  Klicken Sie in der Spalte **Quelle** im Raster auf der Registerkarte **Mining Modellvorhersage** auf die Zelle in der ersten leeren Zeile, und wählen Sie dann **Mining Modell prognostizieren**aus.  
  
5.  Wählen Sie in der Spalte **Feld** die Option **Modellbereich**aus.  
  
     Auf diese Weise wird der Bezeichner für die Reihe zur Vorhersageabfrage hinzugefügt, um anzugeben, auf welche Kombination aus Modell und Region sich die Vorhersage bezieht.  
  
6.  Klicken Sie in der Spalte **Quelle** auf die nächste leere Zeile, und wählen Sie dann **Vorhersagefunktion**aus.  
  
7.  Wählen Sie in der Spalte **Feld** die Option **prättimeseries**aus.  
  
    > [!NOTE]  
    >  Sie können auch die `Predict`-Funktion mit Zeitreihenmodellen verwenden. Standardmäßig wird durch die Vorhersagefunktion jedoch nur eine Vorhersage für jede Reihe erstellt. Wenn Sie also mehrere Vorhersage Schritte angeben möchten, müssen Sie die Funktion " **prättimeseries** " verwenden.  
  
8.  Wählen Sie im Bereich **Mining Modell** die Mining Modell Spalte Amount aus **.** Ziehen Sie Amount in das Feld **Kriterium/Argument** für die Funktion " **prättimeseries** ", die Sie zuvor hinzugefügt haben.  
  
9. Klicken Sie auf das Feld **Kriterium/Argument** , und geben Sie nach dem Feldnamen ein Komma und anschließend **5**ein.  
  
     Der Text im Feld **Kriterium/Argument** sollte nun Folgendes anzeigen:  
  
     `[Forecasting].[Amount],5`  
  
10. Geben `PredictAmount`Sie in der Spalte **Alias** den Namen ein.  
  
11. Klicken Sie in der Spalte **Quelle** auf die nächste leere Zeile, und wählen Sie dann erneut **Vorhersagefunktion** aus.  
  
12. Wählen Sie in der Spalte **Feld** die Option **prättimeseries**aus.  
  
13. Wählen Sie im Bereich **Mining Modell** die Spalten Menge aus, und ziehen Sie Sie dann in das Feld **Kriterium/Argument** für die zweite Funktion von " **vorherentimeseries** ".  
  
14. Klicken Sie auf das Feld **Kriterium/Argument** , und geben Sie nach dem Feldnamen ein Komma und anschließend **5**ein.  
  
     Der Text im Feld **Kriterium/Argument** sollte nun Folgendes anzeigen:  
  
     `[Forecasting].[ Quantity],5`  
  
15. Geben `PredictQuantity`Sie in der Spalte **Alias** den Namen ein.  
  
16. Klicken Sie **auf zur Abfrageergebnis Sicht wechseln**.  
  
     Die Abfrageergebnisse werden im Tabellenformat angezeigt.  
  
 Im Generator für Vorhersageabfragen haben Sie drei verschiedene Ergebnistypen erstellt, einen für Werte aus einer Spalte und zwei zum Abrufen von Werten aus einer Vorhersagefunktion. Aus diesem Grund enthalten die Ergebnisse der Abfrage drei separate Spalten. Die erste Spalte enthält die Liste der Kombinationen aus Produkt und Region. Die zweite und dritte Spalte enthalten jeweils eine geschachtelte Tabelle mit Vorhersageergebnissen. Jede geschachtelte Tabelle enthält die Zeitschritte und vorhergesagten Werte, wie in der nachfolgenden Tabelle dargestellt:  
  
 Beispielergebnisse (Mengen werden auf zwei Dezimalstellen gerundet):  
  
 **M200 Europe-prätbetrag**  
  
|$TIME|Amount|  
|-----------|------------|  
|7/25/2008|99978,00|  
|8/25/2008|145575,07|  
|9/25/2008|116835,19|  
|10/25/2008|116537,38|  
|11/25/2008|107760,55|  
  
 **M200 Europe-prätmenge**  
  
|$TIME|Menge|  
|-----------|--------------|  
|7/25/2008|52|  
|8/25/2008|67|  
|9/25/2008|58|  
|10/25/2008|57|  
|11/25/2008|54|  
  
 **M200 Nordamerika-prätamount**  
  
|$TIME|Amount|  
|-----------|------------|  
|7/25/2008|348533,93|  
|8/25/2008|340097,98|  
|9/25/2008|257986,19|  
|10/25/2008|374658,24|  
|11/25/2008|379241,44|  
  
 **M200 Nordamerika-prätmenge**  
  
|$TIME|Menge|  
|-----------|--------------|  
|7/25/2008|272|  
|8/25/2008|152|  
|9/25/2008|250|  
|10/25/2008|181|  
|11/25/2008|290|  
  
> [!WARNING]  
>  Die in der Beispieldatenbank verwendeten Datumsangaben wurden für diese Version geändert. Wenn Sie eine frühere Version der Beispieldaten verwenden, können sich abweichende Ergebnisse ergeben.  
  
## <a name="saving-the-prediction-results"></a>Speichern der Vorhersageergebnisse  
 Sie können die Vorhersageergebnisse auf unterschiedlichste Weise nutzen. So können Sie beispielsweise die Ergebnisse vereinfachen und die Daten aus der Ergebnisansicht kopieren und in ein Excel-Arbeitsblatt oder in eine andere Datei einfügen.  
  
 Um den Prozess der Ergebnisspeicherung zu vereinfachen, bietet der Data Mining-Designer auch die Möglichkeit, die Daten in einer Datenquellensicht zu speichern. Die Funktionalität zum Speichern von Ergebnissen in einer Datenquellensicht ist nur in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] verfügbar. Die Ergebnisse können nur in einem vereinfachten Format gespeichert werden.  
  
#### <a name="to-flatten-the-results-in-the-results-pane"></a>So vereinfachen Sie die Ergebnisse im Ergebnisbereich  
  
1.  Klicken Sie im Abfrage-Generator Vorhersage auf **zur Abfrage Entwurfs Sicht wechseln**.  
  
     Die Sicht wird geändert, und Sie können den Text der DMX-Abfrage manuell bearbeiten.  
  
2.  Geben Sie das `FLATTENED`-Schlüsselwort nach dem `SELECT`-Schlüsselwort ein. Der vollständige Abfragetext sollte wie folgt lauten:  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    ```  
  
3.  Optional können Sie eine Klausel zum Einschränken der Ergebnisse eingeben. Beispiel:  
  
    ```  
    SELECT FLATTENED  
      [Forecasting].[Model Region],  
      (PredictTimeSeries([Forecasting].[Amount],5)) as [PredictAmount],  
      (PredictTimeSeries([Forecasting].[Quantity],5)) as [PredictQuantity]  
    FROM  
      [Forecasting]  
    WHERE [Forecasting].[Model Region] = 'M200 North America'   
    OR [Forecasting].[Model Region] = 'M200 Europe'  
  
    ```  
  
4.  Klicken Sie **auf zur Abfrageergebnis Sicht wechseln**.  
  
#### <a name="to-export-prediction-query-results"></a>So exportieren Sie Ergebnisse von Vorhersageabfragen  
  
1.  Klicken Sie auf **Abfrageergebnisse speichern**.  
  
2.  Wählen Sie [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]im Dialogfeld **Ergebnis der Data Mining-Abfrage speichern** für **Datenquelle**die Option aus. Wenn Sie die Daten in einer anderen relationalen Datenbank speichern möchten, können Sie auch eine Datenquelle erstellen.  
  
3.  Geben Sie in der Spalte **Tabellenname** einen neuen temporären Tabellennamen ein, z. b. **Test Vorhersagen**.  
  
4.  Klicken Sie auf **Speichern**.  
  
    > [!NOTE]  
    >  Stellen Sie eine Verbindung zur Instanz der Datenbank-Engine her, in der Sie die Daten gespeichert haben, und erstellen Sie eine Abfrage, um die Tabelle anzuzeigen, die Sie erstellt haben.  
  
## <a name="conclusion"></a>Zusammenfassung  
 Sie können nun ein grundlegendes Zeitreihenmodell erstellen, Prognosen interpretieren und Vorhersagen erstellen.  
  
 Die verbleibenden Aufgaben in diesem Lernprogramm sind optional und beschreiben erweiterte Zeitreihenvorhersagen. Wenn Sie dieses Thema weiter verfolgen, lernen Sie, wie Sie dem Modell neue Daten hinzufügen und Vorhersagen zur erweiterten Reihe erstellen können. Sie lernen zudem, Kreuzvorhersagen durchzuführen, indem Sie den Trend im Modell verwenden und die Daten durch eine neue Datenreihe ersetzen.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Erweiterte Zeitreihen Vorhersagen &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfragebeispiel Zeitreihenmodell](../../2014/analysis-services/data-mining/time-series-model-query-examples.md)  
  
  
