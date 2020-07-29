---
title: Bewerten von Daten mithilfe von RevoScaleR
description: 'Tutorial 8 zu RevoScaleR: Bewerten von Daten mithilfe der R-Programmiersprache in SQL Server'
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 58e58dcf3112566c09070cc6e522b29ffff6f3b9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757130"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Bewerten neuer Daten (SQL Server- und RevoScaleR-Tutorial)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Dies ist das achte Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In diesem Tutorial erfahren Sie, wie Sie das logistische Regressionsmodell verwenden, das Sie im letzten Tutorial erstellt haben, um ein weiteres Dataset zu bewerten, das dieselben unabhängigen Variablen als Eingaben verwendet.

> [!div class="checklist"]
> * Bewerten neuer Daten
> * Erstellen eines Histogramms der Ergebnisse

> [!NOTE]
> Sie benötigen DDL-Administratorberechtigungen für einige der folgenden Schritte.

## <a name="generate-and-save-scores"></a>Generieren und Speichern von Ergebnissen
  
1. Aktualisieren Sie die sqlScoreDS-Datenquelle (in [Tutorial 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md) erstellt), um die im letzten Tutorial erstellten Spalteninformationen zu verwenden.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Erstellen Sie ein neues Datenquellenobjekt, um sicherzustellen, dass die Ergebnisse nicht verloren gehen. Verwenden Sie anschließend das neue Datenquellenobjekt, um in der RevoDeepDive-Datenbank eine neue Tabelle aufzufüllen.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    Zu diesem Zeitpunkt ist die Tabelle noch nicht erstellt worden. Diese Anweisung definiert lediglich einen Datencontainer.
     
3. Überprüfen Sie den aktuellen Computekontext mithilfe von **rxGetComputeContext()** , und legen Sie ihn bei Bedarf auf den Server fest.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Überprüfen Sie vorsichtshalber, ob die Ausgabetabelle vorhanden ist. Wenn bereits eine mit demselben Namen vorhanden ist, erhalten Sie eine Fehlermeldung, wenn Sie versuchen, die neue Tabelle zu schreiben.
  
    Rufen Sie dazu die Funktionen [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) und [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable)auf, und übergeben Sie den Tabellennamen als Eingabe.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxSqlServerTableExists** fragt den ODBC-Treiber ab und gibt TRUE zurück, wenn die Tabelle existiert, und FALSE, wenn dem nicht so ist.
    + **rxSqlServerDropTable** führt die DDL-Anweisungen aus und gibt TRUE zurück, wenn die Tabelle erfolgreich gelöscht wurde, und FALSE, wenn dem nicht so ist.

5. Führen Sie [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) aus, um die Ergebnisse zu generieren, und speichern Sie sie in der neuen Tabelle, die in der Datenquelle „sqlScoreDS“ definiert ist.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Die Funktion **rxPredict** ist eine weitere Funktion, die die Ausführung in Remotecomputekontexten unterstützt. Sie können die Funktion **rxPredict** zum Generieren von Ergebnissen aus Modellen verwenden, die auf [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)oder [rxGlm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm) basieren.
  
    - Der Parameter *writeModelVars* wurde in diesem Beispiel auf **TRUE** festgelegt. Dies bedeutet, dass die Variablen, die für die Schätzung verwendet wurden, in die neue Tabelle aufgenommen werden.
  
    - Der Parameter *predVarNames* gibt die Variable an, in der Ergebnisse gespeichert werden. Hier wird eine neue Variable namens `ccFraudLogitScore` übergeben.
  
    - Der *type* -Parameter für **rxPredict** definiert, wie die Vorhersagen berechnet werden sollen. Legen Sie das Schlüsselwort **Antwort** fest, um basierend auf der Skala der Antwortvariablen Ergebnisse zu generieren. Verwenden Sie alternativ das Schlüsselwort **Link**, um basierend auf der zugrunde liegenden Linkfunktion Ergebnisse zu generieren. In diesem Fall werden die Vorhersagen auf Grundlage einer logistischen Skala generiert.

6. Nach einer Weile können Sie die Tabellenliste in Management Studio aktualisieren, um die neue Tabelle und deren Daten anzuzeigen.

7. Verwenden Sie zum Hinzufügen von zusätzlichen Variablen zu den Ausgabevorhersagen das *extraVarsToWrite*-Argument.  Im folgenden Beispiel wird z.B. die Variable *custID* aus der Auswertungsdatentabelle zu der Ausgabetabelle der Vorhersagen hinzugefügt.
  
    ```R
    rxPredict(modelObject = logitObj,
            data = sqlScoreDS,
            outData = sqlServerOutDS,
            predVarNames = "ccFraudLogitScore",
              type = "link",
            writeModelVars = TRUE,
            extraVarsToWrite = "custID",
            overwrite = TRUE)
    ```

## <a name="display-scores-in-a-histogram"></a>Anzeigen der Ergebnisse in einem Histogramm

Nachdem die neue Tabelle erstellt wurde, berechnen Sie ein Histogramm von 10.000 vorhergesagten Ergebnissen, und zeigen Sie es an. Die Berechnung erfolgt schneller, wenn Sie die hohen und niedrigen Werte angeben, rufen Sie diese also aus der Datenbank ab und fügen Sie sie Ihren Arbeitsdaten hinzu.

1. Erstellen Sie eine neue Datenquelle, sqlMinMax, die die Datenbank nach den hohen und niedrigen Werten abfragt.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     In diesem Beispiel wird veranschaulicht, wie einfach die Verwendung von **RxSqlServerData** -Datenquellobjekten ist, um beliebige Datasets auf Grundlage von SQL-Abfragen, Funktionen oder gespeicherten Prozeduren zu definieren und diese anschließend in Ihrem R-Code zu verwenden. Die Variable speichert nicht die eigentlichen Werte, sondern lediglich die Datenquellendefinition. Die Abfrage wird ausgeführt, um die Werte nur dann zu generieren, wenn sie in einer Funktion wie **rxImport**verwendet wird.
      
2. Rufen Sie die Funktion [rxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) auf, um die Werte in einem Datenrahmen zu platzieren, der für verschiedene Computekontexte freigegeben werden kann.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Ergebnisse**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Da die minimalen und maximalen Werte nun verfügbar sind, können Sie sie verwenden, um eine weitere Datenquelle für die generierten Ergebnisse zu erstellen.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Verwenden Sie das Datenquellobjekt „sqlOutScoreDS“ um die Ergebnisse abzurufen und ein Histogramm zu berechnen und anzuzeigen. Fügen Sie bei Bedarf den Code hinzu, um den Computekontext festzulegen.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Ergebnisse**
  
    ![Von R erstelltes komplexes Histogramm](media/rsql-sue-complex-histogram.png "Von R erstelltes komplexes Histogramm")
  
## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Umwandeln von Daten mithilfe von R](../../machine-learning/tutorials/deepdive-transform-data-using-r.md)