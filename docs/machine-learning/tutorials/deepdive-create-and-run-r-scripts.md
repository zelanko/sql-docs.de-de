---
title: Zusammenfassungsstatistiken in RevoScaleR
description: 'Tutorial 5 zu RevoScaleR: Berechnen statistischer Zusammenfassungsstatistiken mithilfe der R-Sprache in SQL Server'
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: bb362f078dd4fbebedf88dc41e997a5feb702f55
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470641"
---
# <a name="compute-summary-statistics-in-r-sql-server-and-revoscaler-tutorial"></a>Berechnen von Zusammenfassungstatistiken in R (SQL Server- und RevoScaleR-Tutorial)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Bei diesem Tutorial handelt es sich um das 5. Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md). In diesem Tutorial erfahren Sie, wie Sie [RevoScaleR-Funktionen](/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server verwenden.

In diesem Tutorial werden die in den vorherigen Tutorials erstellten Datenquellen und Computekontexte verwendet, um leistungsstarke R-Skripts auszuführen. In diesem Tutorial verwenden Sie Computekontexte von lokalen und Remoteservern für die folgenden Aufgaben:

> [!div class="checklist"]
> * Wechseln des Computekontexts auf SQL Server
> * Abrufen von Zusammenfassungsstatistiken für Remotedatenobjekte
> * Berechnen einer lokalen Zusammenfassung

Wenn Sie die vorherigen Tutorials abgeschlossen haben, sollten Sie über die folgenden Remotecomputekontexte verfügen: sqlCompute und sqlComputeTrace. In den nachfolgenden Tutorials verwenden Sie sqlCompute und den lokalen Computekontext.

In diesem Tutorial verwenden Sie eine R-IDE oder **Rgui** zum Ausführen des R-Skripts.

## <a name="compute-summary-statistics-on-remote-data"></a>Berechnen von Zusammenfassungsstatistiken für Remotedaten

Bevor Sie einen R-Code ausführen können, müssen Sie den Remotecomputekontext angeben. Alle nachfolgenden Berechnungen erfolgen auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer, der im *sqlCompute*-Parameter angegeben ist.

Ein Computekontext bleibt so lange aktiv, bis Sie ihn ändern. Alle R-Skripts, die *nicht* in einem Remoteserverkontext ausgeführt werden können, werden automatisch lokal ausgeführt.

Um die Funktionsweise eines Computekontexts besser zu verstehen, generieren Sie eine Zusammenfassungsstatistik für die sqlFraudDS-Datenquelle auf der SQL Server-Remoteinstanz. Dieses Datenquellenobjekt wurde in [Tutorial 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) erstellt und stellt die ccFraudSmall-Tabelle in der RevoDeepDive-Datenbank dar. 

1. Wechseln Sie zum im vorherigen Tutorial erstellten Computekontext „sqlCompute“:
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```

2. Rufen Sie die Funktion [rxSummary](/machine-learning-server/r-reference/revoscaler/rxsummary) auf, und übergeben Sie alle erforderlichen Argumente, wie z. B. die Formel und die Datenquelle, und weisen Sie die Ergebnisse der Variablen `sumOut` zu.
  
    ```R
    sumOut <- rxSummary(formula = ~gender + balance + numTrans + numIntlTrans + creditLine, data = sqlFraudDS)
    ```
  
    Die R-Sprache stellt zahlreiche Zusammenfassungsfunktionen bereit, **rxSummary** in **RevoScaleR** unterstützt jedoch die Ausführung auf verschiedenen Remotecomputekontexten, einschließlich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zu ähnlichen Funktionen finden Sie unter [Datenzusammenfassungen unter Verwendung von RevoScaleR](/machine-learning-server/r/how-to-revoscaler-data-summaries).
  
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

4. Wechseln Sie für die nächsten Tutorials wieder zum Remotecomputekontext.

    ```R
    rxSetComputeContext(sqlCompute)
    ```

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Visualisieren von SQL Server-Daten mit R](../../machine-learning/tutorials/deepdive-visualize-sql-server-data-using-r.md)