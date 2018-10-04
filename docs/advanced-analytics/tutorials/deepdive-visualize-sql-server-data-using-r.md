---
title: Visualisieren von SQL Server-Daten mithilfe von R (SQL und R tieferer) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0d34ece68c421dbb7aabd845e117c9f07e00d013
ms.sourcegitcommit: 2420c57d2952add3697dbe0467ee1d755c5c2ee5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "47217515"
---
#  <a name="visualize-sql-server-data-using-r-sql-and-r-deep-dive"></a>Visualisieren von SQL Server-Daten mithilfe von R (SQL und R tieferer)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil des Tutorials zur Verwendung von Data Science Deep Dive [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Die erweiterten Pakete in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] enthalten mehrere Funktionen, die für die Skalierbarkeit und die parallele Verarbeitung optimiert wurden. Diese Funktionen besitzen in der Regel das Präfix **rx** oder **Rx**.

In dieser exemplarischen Vorgehensweise verwenden Sie die **RxHistogram** Funktion zum Anzeigen der Verteilung der Werte in der _CreditLine_ -Spalte nach Geschlecht.

## <a name="visualize-data-using-rxhistogram"></a>Visualisieren von Daten mit rxHistogram

1. Verwenden Sie den folgenden R-Code zum Aufrufen der [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) -Funktion, und übergeben Sie eine Formel sowie eine Datenquelle. Sie können dies zunächst lokal ausführen, um die erwarteten Ergebnisse anzuzeigen und zu sehen, wie lange es dauert.
  
    ```R
    rxHistogram(~creditLine|gender, data = sqlFraudDS,  histType = "Percent")
    ```
 
    Intern ruft **rxHistogram** die [rxCube](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxcube) -Funktion ab, die im **RevoScaleR** -Paket enthalten ist. **RxCube** gibt Sie eine einzelne Liste (oder Datenrahmen), die eine Spalte für jede in der Formel angegebene Variable enthält sowie eine Spalte "Counts".
    
2. Nun legen Sie den computekontext auf den SQL Server-Remotecomputer, und führen **RxHistogram** erneut aus.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
 
3. Die Ergebnisse sind identisch, da Sie die gleiche Datenquelle verwenden. Die Berechnungen werden jedoch auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computer ausgeführt.  Die Ergebnisse werden anschließend an Ihre lokale Arbeitsstation zum Zeichnen zurückgegeben.
   
![Historgrammergebnisse](media/rsql-sue-histogramresults.jpg "histogram results")

4. Sie können auch aufrufen, die **RxCube** Funktion, und die Ergebnisse zu einer R, zeichnen die Funktion übergeben.  Das folgende Beispiel verwendet z.B. **rxCube** zur Berechnung des Mittelwerts von *fraudRisk* für jede Kombination von *numTrans* und *numIntlTrans*:
  
    ```R
    cube1 <- rxCube(fraudRisk~F(numTrans):F(numIntlTrans),  data = sqlFraudDS)
    ```
  
    Verwenden Sie zum Angeben der Gruppen, die zum Berechnen der Mittel der Gruppe verwendet werden, die Notation `F()` . In diesem Beispiel `F(numTrans):F(numIntlTrans)` gibt an, dass die ganzen Zahlen in den Variablen `numTrans` und `numIntlTrans` als kategorievariablen mit einer Ebene für jeden Ganzzahlwert behandelt werden soll.
  
    Da die niedrigen und hohen Ebenen bereits, mit der Datenquelle hinzugefügt wurden `sqlFraudDS` (mithilfe der `colInfo` Parameter), die Ebenen automatisch im Histogramm verwendet werden.
  
5. Der Standardwert der Rückgabewert von **RxCube** ist ein *RxCube-Objekt*, das eine Kreuztabelle darstellt. Sie können jedoch die Funktion [rxResultsDF](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxresultsdf) verwenden, um die Ergebnisse in einen Datenrahmen zu konvertieren, der leicht in einem der Standardzeichenfunktionen von R verwendet werden kann.
  
    ```R
    cubePlot <- rxResultsDF(cube1)
    ```
  
    Die **RxCube** Funktion schließt ein optionales Argument, *ReturnDataFrame* = **"true"**, das Sie verwenden können, um die Ergebnisse direkt in einen Datenrahmen zu konvertieren. Zum Beispiel:
    
    `print(rxCube(fraudRisk~F(numTrans):F(numIntlTrans), data = sqlFraudDS, returnDataFrame = TRUE))`
       
    Die Ausgabe von **rxResultsDF** ist jedoch viel genauer und behält die Namen der Quellspalten bei.
  
6. Abschließend führen Sie den folgenden Code zum Erstellen eine temperaturverteilungskarte mithilfe der `levelplot` -Funktion aus der **Lattice** -Paket, das in allen R-Verteilungen enthalten ist.
  
    ```R
    levelplot(fraudRisk~numTrans*numIntlTrans, data = cubePlot)
    ```
  
    **Ergebnisse**
  
    ![Punktdiagrammergebnisse](media/rsql-sue-scatterplotresults.jpg "scatterplot results")
  
Auch aus dieser schnellen Analyse können Sie herauslesen, dass das Betrugsrisiko jeweils mit der Anzahl der Transaktionen und der Anzahl der internationalen Transaktionen ansteigt.

Weitere Informationen zu den **RxCube** -Funktion und zu Kreuztabellen im Allgemeinen finden Sie unter [Zusammenfassungen von Daten mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).

## <a name="next-step"></a>Nächster Schritt

[Erstellen von R-Modelle mithilfe von SQL Server-Daten](../../advanced-analytics/tutorials/deepdive-create-models.md)

## <a name="previous-step"></a>Vorherigen Schritt

[Erstellen und Ausführen von R-Skripts](../../advanced-analytics/tutorials/deepdive-create-and-run-r-scripts.md)
