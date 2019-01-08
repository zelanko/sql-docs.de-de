---
title: 'Berechnen von zusammenfassungsstatistiken RevoScaleR-Tutorial: SQL Server-Machine Learning'
description: Exemplarische Vorgehensweise im Lernprogramm zum statistische Verwendung der Sprache R auf SQL Server Übersichtsstatistiken zu berechnen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dea877323911b3965f7fef5d52ffc121b3990f7d
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645249"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Berechnen von zusammenfassungsstatistiken in R (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

Es verwendet die eingerichteten Datenquellen und computekontexten, die in den vorherigen Lektionen erstellt haben, leistungsstarke R-Skripts in diesem Artikel ausführen. In dieser Lektion verwenden Sie Server für lokale und remote computekontexte für die folgenden Aufgaben:

> [!div class="checklist"]
> * Wechseln Sie den computekontext auf SQL Server
> * Erhalten Sie eine Zusammenfassungsstatistik auf Remotedaten-Objekte
> * Berechnen eines lokalen Verzeichnisses

Wenn Sie die vorherigen Lektionen abgeschlossen haben, müssen Sie diese remotecomputekontexte: SqlCompute und SqlComputeTrace. Schritt nach vorne, Sie verwenden, werden SqlCompute und dem lokalen Kontext in den folgenden Lektionen berechnet.

Verwenden Sie eine R-IDE oder **Rgui** zum Ausführen des R-Skripts in dieser Lektion.

## <a name="compute-summary-statistics-on-remote-data"></a>Berechnen von zusammenfassungsstatistiken auf Remotedaten

Bevor Sie eine beliebige R-Code Remote ausführen können, müssen Sie angeben, die Remote-computekontext. Alle nachfolgende Berechnungen erfolgen auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im angegebenen Computer die *SqlCompute* Parameter.

Mit einem rechenkontext bleibt aktiv, bis Sie ihn ändern. Allerdings alle R-Skripts, die *kann nicht* Ausführung in einem remote-Server-Kontext wird automatisch lokal ausgeführt werden.

Um die Funktionsweise ein computekontexts, generieren Sie zusammenfassende Statistiken für die SqlFraudDS-Datenquelle auf dem SQL-Remoteserver. In diesem Datenquellenobjekt erstellt wurde [Lektion zwei](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) und die CcFraudSmall-Tabelle in der Datenbank RevoDeepDive darstellt. 

1. Wechseln Sie den computekontext, zum SqlCompute, die in der vorherigen Lektion erstellt haben:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Rufen Sie die [RxSummary](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsummary) funktionieren mit der erforderlichen Argumente, z. B. die Formel und die Datenquelle übergeben, und weisen Sie die Ergebnisse der Variablen `sumOut`.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Die Sprache R stellt viele Zusammenfassungsfunktion bereit, aber **RxSummary** in **RevoScaleR** unterstützt die Ausführung auf verschiedenen remotecomputekontexten, einschließlich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zu ähnlichen Funktionen finden Sie unter [Zusammenfassungen von Daten mithilfe von RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
3. Drucken Sie den Inhalt der SumOut an die Konsole.
  
    ```R
    sumOut
    ```
    > [!NOTE]
    > Wenn Sie eine Fehlermeldung erhalten, warten Sie einige Minuten für die Ausführung beendet wurde, und wiederholen den Befehl.

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

## <a name="create-a-local-summary"></a>Erstellen eines lokales Verzeichnisses

1. Ändern Sie den Computekontext, damit all Ihre Arbeit lokal ausgeführt wird.
  
    ```R
    rxSetComputeContext ("local")
    ```
  
2. Beim Extrahieren von Daten aus SQL Server erhalten häufig Sie eine bessere Leistung durch Erhöhen der Anzahl der Zeilen, die bei jedem Lesevorgang, extrahiert vorausgesetzt, dass die höheren Blockgröße im Arbeitsspeicher untergebracht werden kann. Führen Sie den folgenden Befehl zum Erhöhen des Werts für die *RowsPerRead* Parameter für die Datenquelle. Zuvor war der Wert von *rowsPerRead* auf 5000 festgelegt.
  
    ```R
    sqlServerDS1 <- RxSqlServerData(
       connectionString = sqlConnString,
       table = sqlFraudTable,
       colInfo = ccColInfo,
       rowsPerRead = 10000)
    ```

3. Rufen Sie **RxSummary** auf die neue Datenquelle.
  
    ```R
    rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlServerDS1)
    ```
  
   Die tatsächlichen Ergebnisse sollten denen entsprechen, die beim Ausführen von **rxSummary** im Kontext des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Computers ausgegeben werden. Der Vorgang kann jedoch schneller oder langsamer sein. Dies hängt hauptsächlich von der Verbindung zu Ihrer Datenbank ab, da die Daten für die Analyse auf Ihren lokalen Computer übertragen werden.

4. Wechseln Sie zurück zur Remote compute Context verwenden, für die nächsten mehreren Lektionen.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Visualisieren von SQL Server-Daten mit R](../../advanced-analytics/tutorials/deepdive-visualize-sql-server-data-using-r.md)