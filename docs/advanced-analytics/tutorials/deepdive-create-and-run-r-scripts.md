---
title: Compute-Zusammenfassungs Statistik revoscaler-Tutorial
description: 'Tutorial: Exemplarische Vorgehensweise zur Berechnung statistischer Zusammenfassungs Statistiken mithilfe der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 5f90cc0e6101e168e15ed7c1145d286f799375ac
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344710"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Compute-Zusammenfassungs Statistiken in R (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Es verwendet die in vorherigen Lektionen erstellten erstellten Datenquellen und computekontexte, um in diesem eine hoch gestützte R-Skripts auszuführen. In dieser Lektion verwenden Sie lokale Server und Remote Server-computekontexte für die folgenden Aufgaben:

> [!div class="checklist"]
> * Wechseln Sie in den computekontext SQL Server
> * Abrufen von Zusammenfassungs Statistiken zu Remote Datenobjekten
> * Lokale Zusammenfassung berechnen

Wenn Sie die vorherigen Lektionen abgeschlossen haben, sollten Sie über diese remotecomputekontexte verfügen: sqlcompute und sqlcomputetrace. Wenn Sie fortfahren, verwenden Sie sqlcompute und den lokalen computekontext in nachfolgenden Lektionen.

Verwenden Sie eine r-IDE oder **rgui** , um das R-Skript in dieser Lektion auszuführen.

## <a name="compute-summary-statistics-on-remote-data"></a>Compute-Zusammenfassungs Statistiken für Remote Daten

Bevor Sie R-Code Remote ausführen können, müssen Sie den remotecomputekontext angeben. Alle nachfolgenden Berechnungen erfolgen auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer, der im *sqlcompute* -Parameter angegeben ist.

Ein computekontext bleibt aktiv, bis Sie ihn ändern. Alle R-Skripts, die nicht in einem Remote Server Kontext ausgeführt werden *können* , werden jedoch automatisch lokal ausgeführt.

Um die Funktionsweise eines computekontexts anzuzeigen, generieren Sie eine Zusammenfassungs Statistik für die sqlbetrüds-Datenquelle auf dem Remote SQL Server. Dieses Datenquellen Objekt wurde in [Lektion 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) erstellt und stellt die ccbetrüger Small-Tabelle in der revodeepdive-Datenbank dar. 

1. Wechseln Sie in den computekontext in sqlcompute, der in der vorherigen Lektion erstellt wurde:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Ruft die [rxsummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) -Funktion auf und übergibt erforderliche Argumente, wie z. b. die Formel und die Datenquelle, und weist `sumOut`die Ergebnisse der Variablen zu.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Die R-Sprache bietet viele Zusammenfassungs Funktionen, aber **rxsummary** in **revoscaler** unterstützt die Ausführung auf verschiedenen remotecomputekontexten, einschließlich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zu ähnlichen Funktionen finden [Sie unter Daten Zusammenfassungen mithilfe von revoscaler](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Druckt den Inhalt von sumout in der Konsole.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Wenn Sie eine Fehlermeldung erhalten, warten Sie einige Minuten, bis die Ausführung abgeschlossen ist, und wiederholen Sie dann den Befehl.

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
  
2. Wenn Sie Daten aus SQL Server extrahieren, können Sie häufig eine bessere Leistung erzielen, indem Sie die Anzahl der für jeden Lesevorgang extrahierten Zeilen erhöhen, vorausgesetzt, die größere Blockgröße kann im Arbeitsspeicher belegt werden. Führen Sie den folgenden Befehl aus, um den Wert für den Parameter *rowsperread* für die Datenquelle zu erhöhen. Zuvor war der Wert von *rowsPerRead* auf 5000 festgelegt.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Ruft **rxsummary** für die neue Datenquelle auf.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   Die tatsächlichen Ergebnisse sollten denen entsprechen, die beim Ausführen von **rxSummary** im Kontext des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computers ausgegeben werden. Der Vorgang kann jedoch schneller oder langsamer sein. Dies hängt hauptsächlich von der Verbindung zu Ihrer Datenbank ab, da die Daten für die Analyse auf Ihren lokalen Computer übertragen werden.

4. Wechseln Sie für die nächsten Lektionen wieder zum remotecomputekontext.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Visualisieren von SQL Server-Daten mit R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)