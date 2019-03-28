---
title: Visualisieren von SQL Server-Daten, die mithilfe von RevoScaleR RxHistogram – SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Visualisieren von Daten, die Verwendung der Sprache R auf SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c39d19807cfe01ca9c96b47de020abb9227c43a0
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58513077"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Visualisieren von SQL Server-Daten mithilfe von R (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In dieser Lektion verwenden Sie R-Funktionen zum Anzeigen der Verteilung der Werte in der *CreditLine* -Spalte nach Geschlecht.

> [!div class="checklist"]
> * Min-Max-Variablen für Histogramm Eingaben erstellen
> * Visualisieren von Daten in einem Histogramm mit **RxHistogram** aus **RevoScaleR**
> * Visualisieren mit Punktdiagrammen mit **Levelplot** aus **Lattice** enthalten in der basisverteilung von R

In dieser Lektion wird veranschaulicht, können Sie die Open Source- und Microsoft-spezifische Funktionen in das gleiche Skript kombinieren.

## <a name="add-maximum-and-minimum-values"></a>Maximale und minimale Werte hinzufügen

Basierend auf der berechneten zusammenfassungsstatistiken aus der vorherigen Lektion, haben Sie einige nützliche Informationen zu den Daten entdeckt, die Sie in der Datenquelle für weitere Berechnungen einfügen können. Beispielsweise können die minimalen und maximalen Werte verwendet werden, um Histogramme zu berechnen. In dieser Übung fügen Sie die hohen und niedrigen Werte der **RxSqlServerData** -Datenquelle.

1. Beginnen Sie, indem Sie einige temporäre Variablen einrichten.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Verwenden Sie die Variable *CcColInfo* , dass Sie in der vorherigen Lektion definieren Sie Spalten in der Datenquelle erstellt haben.
  
   Neue berechnete Spalten hinzufügen (*NumTrans*, *NumIntlTrans*, und *CreditLine*) zur Spaltensammlung, die die ursprüngliche Definition zu überschreiben. Das folgende Skript fügt basierte auf den minimalen und maximalen Werten, abgerufen aus SumOut, die die Ausgabe im Arbeitsspeicher gespeichert sind, die Faktoren **RxSummary**. 
  
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
  
3. Nach dem Update der Spaltensammlung, gelten die folgende Anweisung hinzu, erstellen Sie eine aktualisierte Version der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquelle, die Sie zuvor definiert.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Die Datenquelle SqlFraudDS enthält nun die neuen Spalten hinzugefügt, mit *CcColInfo*.
  
An diesem Punkt beeinflussen die Änderungen nur das Datenquellenobjekt in R; keine neuen Daten wurde noch in die Datenbanktabelle geschrieben. Jedoch können Sie in der Variablen SumOut die aufgezeichneten Daten, um Visualisierungen und Zusammenfassungen zu erstellen. 

> [!TIP]
> Wenn Sie vergessen Sie welchen computekontext Sie verwenden, führen Sie **rxGetComputeContext()**. Ein Rückgabewert von "RxLocalSeq Compute Context" gibt an, dass Sie in den lokalen computekontext ausgeführt werden.

## <a name="visualize-data-using-rxhistogram"></a>Visualisieren von Daten mit rxHistogram

1. Verwenden Sie den folgenden R-Code zum Aufrufen der [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) -Funktion, und übergeben Sie eine Formel sowie eine Datenquelle. Sie können dies zunächst lokal ausführen, um die erwarteten Ergebnisse anzuzeigen und zu sehen, wie lange es dauert.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Intern ruft **rxHistogram** die [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) -Funktion ab, die im **RevoScaleR** -Paket enthalten ist. **RxCube** gibt Sie eine einzelne Liste (oder Datenrahmen), die eine Spalte für jede in der Formel angegebene Variable enthält sowie eine Spalte "Counts".
    
2. Nun legen Sie den computekontext auf den SQL Server-Remotecomputer, und führen **RxHistogram** erneut aus.
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Die Ergebnisse sind die gleichen genau, da Sie die gleiche Datenquelle verwenden, jedoch im zweiten Schritt werden die Berechnungen auf dem Remoteserver ausgeführt. Die Ergebnisse werden anschließend an Ihre lokale Arbeitsstation zum Zeichnen zurückgegeben.
   
  ![Historgrammergebnisse](media/rsql-sue-histogramresults.jpg "histogram results")


## <a name="visualize-with-scatter-plots"></a>Visualisieren mit Punktdiagrammen

Punktdiagrammen werden häufig beim Durchsuchen von Daten verwendet, um die Beziehung zwischen zwei Variablen vergleichen. Können Sie integrierte R-Pakete zu diesem Zweck mit Eingaben vom **RevoScaleR** Funktionen.

1. Rufen Sie die [RxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs) Funktion berechnet den Mittelwert der *FraudRisk* für jede Kombination von *NumTrans* und *NumIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Verwenden Sie zum Angeben der Gruppen, die zum Berechnen der Mittel der Gruppe verwendet werden, die Notation `F()` . In diesem Beispiel `F(numTrans):F(numIntlTrans)` gibt an, dass die ganzen Zahlen in den Variablen `numTrans` und `numIntlTrans` als kategorievariablen mit einer Ebene für jeden Ganzzahlwert behandelt werden soll.
  
    Der Standardwert der Rückgabewert von **RxCube** ist ein *RxCube-Objekt*, das eine Kreuztabelle darstellt. 
  
2. Rufen Sie [RxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) Funktion, um die Ergebnisse in einem Datenrahmen zu konvertieren, die leicht in einem der standardzeichenfunktionen von R verwendet werden kann.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Die **RxCube** Funktion schließt ein optionales Argument, *ReturnDataFrame* = **"true"**, das Sie verwenden können, um die Ergebnisse direkt in einen Datenrahmen zu konvertieren. Zum Beispiel:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Allerdings die Ausgabe des **RxResultsDF** ist sauberer und behält die Namen der Quellspalten. Sie können ausführen `head(cube1)` gefolgt von `head(cubePlot)` zum Vergleichen der Ausgabe.
  
3. Erstellen Sie eine temperaturverteilungskarte mithilfe der **Levelplot** -Funktion aus der **Lattice** Paket, das in allen R-Verteilungen enthalten.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Ergebnisse**
  
    ![Punktdiagrammergebnisse](media/rsql-sue-scatterplotresults.jpg "scatterplot results")
  
In dieser schnellen Analyse sehen Sie sich, dass das Betrugsrisiko mit der Anzahl der Transaktionen und die Anzahl der internationalen Transaktionen ansteigt.

Weitere Informationen zu den **RxCube** -Funktion und zu Kreuztabellen im Allgemeinen finden Sie unter [Zusammenfassungen von Daten mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von R-Modelle mithilfe von SQL Server-Daten](../../advanced-analytics/tutorials/deepdive-create-models.md)