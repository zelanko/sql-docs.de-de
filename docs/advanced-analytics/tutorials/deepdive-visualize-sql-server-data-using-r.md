---
title: Visualisieren von SQL Server Daten mithilfe von revoscaler rxhistogram
description: 'Tutorial: Exemplarische Vorgehensweise zum Visualisieren von Daten mit der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 210fade2820c53ba585043827e7e3d2c36315319
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344654"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Visualisieren von SQL Server Daten mithilfe von R (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Verwenden Sie in dieser Lektion R-Funktionen, um die Verteilung von Werten in der *creditline* -Spalte nach Geschlecht anzuzeigen.

> [!div class="checklist"]
> * Min-Max-Variablen für histogrammeingaben erstellen
> * Visualisieren von Daten in einem Histogramm mithilfe von **rxhistogram** aus **revoscaler**
> * Visualisieren mit Punkt Diagrammen mithilfe von " **levelplot** " aus der in der Basis-R-Verteilung enthaltenen **Gitter**

Wie in dieser Lektion veranschaulicht, können Sie Open Source-und Microsoft-spezifische Funktionen im gleichen Skript kombinieren.

## <a name="add-maximum-and-minimum-values"></a>Maximale und minimale Werte hinzufügen

Basierend auf den berechneten Zusammenfassungs Statistiken aus der vorherigen Lektion haben Sie einige nützliche Informationen zu den Daten ermittelt, die Sie in die Datenquelle einfügen können, um weitere Berechnungen auszuführen. Beispielsweise können die minimalen und maximalen Werte verwendet werden, um Histogramme zu berechnen. Fügen Sie in dieser Übung die hohen und niedrigen Werte zur **rxsqlserverdata** -Datenquelle hinzu.

1. Beginnen Sie, indem Sie einige temporäre Variablen einrichten.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Verwenden Sie die Variable *cccolinfo* , die Sie in der vorherigen Lektion erstellt haben, um die Spalten in der Datenquelle zu definieren.
  
   Fügen Sie der Spalten Auflistung neue berechnete Spalten (*numtrans*, *numintltrans*und *creditline*) hinzu, die die ursprüngliche Definition überschreiben. Das folgende Skript fügt Faktoren basierend auf den minimalen und maximalen Werten hinzu, die aus sumout abgerufen werden, wobei die Speicher interne Ausgabe von **rxsummary**gespeichert wird. 
  
    ```R 
    ccColInfo <- list(
        gender = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Male", "Female")),
        cardholder = list(type = "factor",
          levels = c("1", "2"), 
          newLevels = c("Principal", "Secondary")), 
        state = list(type = "factor", 
          levels = as.character(1:51), 
          newLevels = stateAbb), 
        balance  = list(type = "numeric"),
        numTrans = list(type = "factor", 
          levels = as.character(sumDF[var == "numTrans", "Min"]:sumDF[var == "numTrans", "Max"])),
        numIntlTrans = list(type = "factor",  
            levels = as.character(sumDF[var == "numIntlTrans", "Min"]:sumDF[var =="numIntlTrans", "Max"])),
        creditLine = list(type = "numeric")
            )
    ```
  
3. Nachdem Sie die Spalten Auflistung aktualisiert haben, wenden Sie die folgende Anweisung an, um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aktualisierte Version der Datenquelle zu erstellen, die Sie zuvor definiert haben.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Die sqlbetrüds-Datenquelle enthält jetzt die neuen Spalten, die mithilfe von *cccolinfo*hinzugefügt wurden.
  
Zu diesem Zeitpunkt wirken sich die Änderungen nur auf das Datenquellen Objekt in R aus. Es wurden noch keine neuen Daten in die Datenbanktabelle geschrieben. Sie können jedoch die in der sumout-Variablen erfassten Daten verwenden, um Visualisierungen und Zusammenfassungen zu erstellen. 

> [!TIP]
> Wenn Sie vergessen haben, welchen computekontext Sie verwenden, führen Sie **rxgetcomputecontext ()** aus. Der Rückgabewert "rxlocalabq Compute Context" zeigt an, dass Sie im lokalen computekontext ausgeführt werden.

## <a name="visualize-data-using-rxhistogram"></a>Visualisieren von Daten mithilfe von rxhistogram

1. Verwenden Sie den folgenden R-Code zum Aufrufen der [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) -Funktion, und übergeben Sie eine Formel sowie eine Datenquelle. Sie können dies zunächst lokal ausführen, um die erwarteten Ergebnisse anzuzeigen und zu sehen, wie lange es dauert.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Intern ruft **rxHistogram** die [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) -Funktion ab, die im **RevoScaleR** -Paket enthalten ist. **rxcube** gibt eine einzelne Liste (oder einen Datenrahmen) aus, die eine Spalte für jede in der Formel angegebene Variable sowie eine zählungs Spalte enthält.
    
2. Legen Sie nun den computekontext auf den Remote SQL Server Computer fest, und führen Sie **rxhistogram** erneut aus.
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Die Ergebnisse sind genau identisch, da Sie die gleiche Datenquelle verwenden, aber im zweiten Schritt werden die Berechnungen auf dem Remote Server ausgeführt. Die Ergebnisse werden anschließend an Ihre lokale Arbeitsstation zum Zeichnen zurückgegeben.
   
  ![Historgrammergebnisse](media/rsql-sue-histogramresults.jpg "histogram results")


## <a name="visualize-with-scatter-plots"></a>Visualisieren mit Punkt Diagrammen

Punkt Diagramme werden häufig beim Durchsuchen von Daten verwendet, um die Beziehung zwischen zwei Variablen zu vergleichen. Sie können integrierte R-Pakete zu diesem Zweck mit Eingaben verwenden, die von **revoscaler** -Funktionen bereitgestellt werden.

1. Mit der [rxcube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) -Funktion können Sie den Mittelwert von *fraudrisk* für jede Kombination von *numtrans* und *numintltrans*berechnen:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Verwenden Sie zum Angeben der Gruppen, die zum Berechnen der Mittel der Gruppe verwendet werden, die Notation `F()` . In diesem Beispiel `F(numTrans):F(numIntlTrans)` gibt an, dass die ganzen Zahlen in den `numTrans` Variablen `numIntlTrans` und als kategorische Variablen mit einer Ebene für jeden ganzzahligen Wert behandelt werden sollen.
  
    Der Standard Rückgabewert von **rxcube** ist ein *rxcube-Objekt*, das eine Kreuz Tabellen Darstellung darstellt. 
  
2. Ruft die [rxresultdf](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) -Funktion auf, um die Ergebnisse in einen Datenrahmen zu konvertieren, der problemlos in einer der standardmäßigen Zeichnungsfunktionen von R verwendet werden kann.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Die **rxcube** -Funktion enthält ein optionales Argument, *returndataframe* = **true**, das Sie verwenden können, um die Ergebnisse direkt in einen Datenrahmen zu konvertieren. Zum Beispiel:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Die Ausgabe von **rxresultdf** ist jedoch sauberer und behält die Namen der Quell Spalten bei. Sie können ausführen `head(cube1)` `head(cubePlot)` , um die Ausgabe zu vergleichen.
  
3. Erstellen Sie eine wärmemap mithilfe der **levelplot** -Funktion aus dem **Gitter** Paket, das in allen R-Verteilungen enthalten ist.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Ergebnisse**
  
    ![Punktdiagrammergebnisse](media/rsql-sue-scatterplotresults.jpg "scatterplot results")
  
Anhand dieser kurzen Analyse können Sie festzustellen, dass das Risiko eines Betrugs mit der Anzahl von Transaktionen und der Anzahl der internationalen Transaktionen zunimmt.

Weitere Informationen zur **rxcube** -Funktion und zu Kreuz Tabellen im Allgemeinen finden [Sie unter Daten Zusammenfassungen mithilfe von revoscaler](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von R-Modellen mithilfe von SQL Server Daten](../../advanced-analytics/tutorials/deepdive-create-models.md)