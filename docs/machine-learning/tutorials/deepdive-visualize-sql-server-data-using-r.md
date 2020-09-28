---
title: Visualisieren von Daten mithilfe von RevoScaleR
description: Erfahren Sie, wie Sie mithilfe von R-Funktionen die Verteilung der Werte in der Spalte „creditLine“ nach Geschlecht visualisieren können.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 23f3eb157a76a9a197cf0f15a72ae0e51f7cf13b
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180387"
---
#  <a name="visualize-sql-server-data-using-r-sql-server-and-revoscaler-tutorial"></a>Visualisieren von SQL Server-Daten mithilfe von R (Tutorial zu SQL Server und RevoScaleR)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Dies ist das sechste Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In diesem Tutorial verwenden Sie R-Funktionen zum Anzeigen der Verteilung von Werten in der Spalte *creditLine* nach Geschlecht.

> [!div class="checklist"]
> * Erstellen von Minimum- und Maximumwerten für Histogrammeingaben
> * Visualisieren von Daten in einem Histogramm mithilfe von **rxHistogram** aus **RevoScaleR**
> * Visualisieren mit Punktdiagrammen mithilfe von **levelplot** aus dem in der R-Basisverteilung enthaltenen **lattice**-Paket

In diesem Tutorial wird veranschaulicht, dass Sie Open-Source- und Microsoft-spezifische Funktionen in einem Skript kombinieren können.

## <a name="add-maximum-and-minimum-values"></a>Hinzufügen von Maximum- und Minimumwerten

Auf Grundlage der berechneten Zusammenfassungsstatistiken aus dem vorherigen Tutorial haben Sie einige nützliche Informationen über die Daten gefunden, die Sie in die Datenquelle für weitere Berechnungen einfügen können. So können Sie beispielsweise mithilfe der Minimum- und Maximumwerte Histogramme berechnen. In dieser Übung fügen Sie der Datenquelle **RxSqlServerData** den höchsten und den niedrigsten Wert hinzu.

1. Beginnen Sie, indem Sie einige temporäre Variablen einrichten.
  
    ```R
    sumDF <- sumOut$sDataFrame
    var <- sumDF$Name
    ```
  
2. Verwenden Sie die Variable *ccColInfo*, die Sie im vorherigen Tutorial zum Definieren von Spalten in der Datenquelle erstellt haben.
  
   Fügen Sie der Spaltensammlung neue berechnete Spalten (*numTrans*, *numIntlTrans* und *creditLine*) hinzu. Damit wird die ursprüngliche Definition überschrieben. Mit dem folgenden Skript werden auf Basis der Minimum- und Maximumwerte Faktoren hinzugefügt, die mit der Variablen „sumOut“ abgerufen werden. Mit dieser Variablen wird das speicherinterne Ergebnis aus **rxSummary** gespeichert. 
  
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
  
3. Wenden Sie nach dem Update der Spaltensammlung die folgende Anweisung an, um eine aktualisierte Version der zuvor definierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle zu erstellen.
  
    ```R
    sqlFraudDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlFraudTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
    Die Datenquelle „sqlFraudDS“ enthält nun die neuen Spalten, die mithilfe von *ccColInfo* hinzugefügt wurden.
  
An dieser Stelle wirken sich die Änderungen nur auf das Datenquellenobjekt in R aus. Es wurden noch keine neuen Daten in die Datenbanktabelle geschrieben. Sie können jedoch die in der Variablen „sumOut“ aufgezeichneten Daten verwenden, um Visualisierungen und Zusammenfassungen zu erstellen. 

> [!TIP]
> Wenn Sie vergessen haben, welchen Computekontext Sie verwenden, führen Sie **rxGetComputeContext** aus. Ein Rückgabewert von „RxLocalSeq Compute Context“ gibt an, dass Sie sich im lokalen Computekontext befinden.

## <a name="visualize-data-using-rxhistogram"></a>Visualisieren von Daten mit rxHistogram

1. Verwenden Sie den folgenden R-Code zum Aufrufen der [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) -Funktion, und übergeben Sie eine Formel sowie eine Datenquelle. Sie können dies zunächst lokal ausführen, um die erwarteten Ergebnisse anzuzeigen und zu sehen, wie lange es dauert.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Intern ruft **rxHistogram** die [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) -Funktion ab, die im **RevoScaleR** -Paket enthalten ist. **rxCube** gibt eine einzelne Liste (oder einen einzelnen Datenrahmen) aus, die (bzw. der) eine Spalte für jede in der Formel angegebene Variable enthält, sowie eine Spalte „counts“.
    
2. Nun legen Sie den Computekontext auf den SQL Server-Remotecomputer fest und führen **rxHistogram** erneut aus.
  
    ```R
    rxSetComputeContext(sqlCompute)
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
3. Die Ergebnisse sind identisch, da Sie die gleiche Datenquelle verwenden. Die Berechnungen im zweiten Schritt werden jedoch auf dem Remoteserver ausgeführt. Die Ergebnisse werden anschließend an Ihre lokale Arbeitsstation zum Zeichnen zurückgegeben.
   
  ![Histogrammergebnisse](media/rsql-sue-histogramresults.jpg "Histogrammergebnisse")


## <a name="visualize-with-scatter-plots"></a>Visualisieren mit Punktdiagrammen

Punktdiagramme werden beim Durchsuchen von Daten häufig verwendet, um die Beziehung zwischen zwei Variablen zu vergleichen. Hierzu können Sie integrierte R-Pakete mit Eingaben verwenden, die durch **RevoScaleR**-Funktionen bereitgestellt werden.

1. Rufen Sie die [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcrosstabs)-Funktion zur Berechnung des Mittelwerts von *fraudRisk* für sämtliche Kombinationen von *numTrans* und *numIntlTrans* auf:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Verwenden Sie zum Angeben der Gruppen, die zum Berechnen der Mittel der Gruppe verwendet werden, die Notation `F()` . In diesem Beispiel gibt `F(numTrans):F(numIntlTrans)` an, dass die ganzen Zahlen in den Variablen `numTrans` und `numIntlTrans` als Kategorievariablen mit einer Ebene für jeden Ganzzahlwert behandelt werden müssen.
  
    Der Rückgabewert von **rxCube** ist standardmäßig ein *rxCube-Objekt*, das eine Kreuztabelle darstellt. 
  
2. Rufen Sie die Funktion [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) auf, um die Ergebnisse in einen Datenrahmen zu konvertieren, der leicht in einem der Standardzeichenfunktionen von R verwendet werden kann.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Die Funktion **rxCube** enthält das optionale Argument *returnDataFrame* = **TRUE**, das Sie zur direkten Konvertierung der Ergebnisse in einen Datenrahmen verwenden können. Beispiel:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Die Ausgabe von **rxResultsDF** ist jedoch genauer. Zudem bleiben bei dieser Ausgabe die Namen der Quellspalten erhalten. Führen Sie zum Vergleichen der Ausgabe zunächst `head(cube1)`, dann `head(cubePlot)` aus.
  
3. Erstellen Sie mithilfe der **levelplot**-Funktion aus dem in allen R-Verteilungen enthaltenen **lattice**-Paket ein Wärmebild.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Ergebnisse**
  
    ![Punktdiagrammergebnis](media/rsql-sue-scatterplotresults.jpg "Punktdiagrammergebnis")
  
Aus dieser schnellen Analyse können Sie herauslesen, dass das Betrugsrisiko jeweils mit der Anzahl der Transaktionen und der Anzahl der internationalen Transaktionen ansteigt.

Weitere Informationen zur **rxCube**-Funktion und zu Kreuztabellen im Allgemeinen finden Sie unter [Datenzusammenfassungen mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von R-Modellen mithilfe von SQL Server-Daten](../../machine-learning/tutorials/deepdive-create-models.md)