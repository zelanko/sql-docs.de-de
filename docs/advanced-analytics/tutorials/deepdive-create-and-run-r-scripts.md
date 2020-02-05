---
title: Zusammenfassungsstatistiken in RevoScaleR
description: 'RevoScaleR tutorial 5: How to compute statistical summary statistics using the R language on SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 43745602fc099f1b992eb1d76622ff3d7e6d0916
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74947276"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Berechnen von Zusammenfassungstatistiken in R (SQL Server- und RevoScaleR-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

This is tutorial 5 of the [RevoScaleR tutorial series](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) on how to use [RevoScaleR functions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) with SQL Server.

This tutorial uses the established data sources and compute contexts created in previous tutorials to run high-powered R scripts. In this tutorial, you will use local and remote server compute contexts for the following tasks:

> [!div class="checklist"]
> * Wechseln des Computekontexts auf SQL Server
> * Abrufen von Zusammenfassungsstatistiken für Remotedatenobjekte
> * Berechnen einer lokalen Zusammenfassung

If you completed the previous tutorials, you should have these remote compute contexts: sqlCompute and sqlComputeTrace. Moving forward, you use will sqlCompute and the local compute context in subsequent tutorials.

Use an R IDE or **Rgui** to run the R script in this tutorial.

## <a name="compute-summary-statistics-on-remote-data"></a>Berechnen von Zusammenfassungsstatistiken für Remotedaten

Bevor Sie einen R-Code ausführen können, müssen Sie den Remotecomputekontext angeben. Alle nachfolgenden Berechnungen erfolgen auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer, der im *sqlCompute*-Parameter angegeben ist.

Ein Computekontext bleibt so lange aktiv, bis Sie ihn ändern. Alle R-Skripts, die *nicht* in einem Remoteserverkontext ausgeführt werden können, werden automatisch lokal ausgeführt.

Um die Funktionsweise eines Computekontexts besser zu verstehen, generieren Sie eine Zusammenfassungsstatistik für die sqlFraudDS-Datenquelle auf der SQL Server-Remoteinstanz. This data source object was created in [tutorial two](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) and represents the ccFraudSmall table in the RevoDeepDive database. 

1. Switch the compute context to sqlCompute created in the previous tutorial:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Rufen Sie die Funktion [rxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) auf, und übergeben Sie alle erforderlichen Argumente, wie z. B. die Formel und die Datenquelle, und weisen Sie die Ergebnisse der Variablen `sumOut` zu.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Die R-Sprache stellt zahlreiche Zusammenfassungsfunktionen bereit, **rxSummary** in **RevoScaleR** unterstützt jedoch die Ausführung auf verschiedenen Remotecomputekontexten, einschließlich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zu ähnlichen Funktionen finden Sie unter [Datenzusammenfassungen unter Verwendung von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Druckt den Inhalt von sumOut in der Konsole.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Wenn Sie eine Fehlermeldung erhalten, warten Sie einige Minuten, bis die Ausführung abgeschlossen ist, und führen Sie dann den Befehl erneut aus.

**Ergebnisse**

```R
Summary Statistics Results for: ~gender + balance + numTrans + numIntlTrans + creditLine
Data: sqlFraudDS (RxSqlServerData Data Source)
Number of valid observations: 10000

 Name  Mean    StdDev  Min Max ValidObs    MissingObs
 balance       4075.0318 3926.558714            0   25626 100000
 numTrans        29.1061   26.619923 0     100 10000    0           100000
 numIntlTrans     4.0868    8.726757 0      60 10000    0           100000
 creditLine       9.1856    9.870364 1      75 10000    0          100000
 
 Category Counts for gender
 Number of categories: 2
 Number of valid observations: 10000
 Number of missing observations: 0

 gender Counts
  Male   6154
  Female 3846
```

## <a name="create-a-local-summary"></a>Erstellen einer lokalen Zusammenfassung

1. Ändern Sie den Computekontext, damit all Ihre Arbeit lokal ausgeführt wird.
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. Wenn Sie Daten aus SQL Server extrahieren, können Sie häufig eine bessere Leistung erzielen, indem Sie die Anzahl der für jeden Lesevorgang extrahierten Zeilen erhöhen, vorausgesetzt, es ist ausreichend Arbeitsspeicher für die größere Blockgröße vorhanden. Führen Sie den folgenden Befehl aus, um den Wert für den Parameter *rowsPerRead* in der Datenquelle zu erhöhen. Zuvor war der Wert von *rowsPerRead* auf 5000 festgelegt.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Rufen Sie **rxSummary** für die neue Datenquelle auf.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   Die tatsächlichen Ergebnisse sollten denen entsprechen, die beim Ausführen von **rxSummary** im Kontext des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computers ausgegeben werden. Der Vorgang kann jedoch schneller oder langsamer sein. Dies hängt hauptsächlich von der Verbindung zu Ihrer Datenbank ab, da die Daten für die Analyse auf Ihren lokalen Computer übertragen werden.

4. Switch back to the remote compute context for the next several tutorials.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Visualisieren von SQL Server-Daten mit R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)