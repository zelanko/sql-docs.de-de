---
title: Auswertung neuer Daten mit RevoScaleR und RxPredict – SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Bewerten von Daten mithilfe von der Sprache R in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 2a54ce22a7012f0747cd417f0f3b3fee0fda0ddf
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53644979"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Auswertung neuer Daten (SQL Server und die RevoScaleR-Lernprogramm)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Diese Lektion ist Teil der [RevoScaleR Tutorial](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [RevoScaleR-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In diesem Schritt verwenden Sie das logistische Regressionsmodell, das Sie erstellt, in der vorherigen Lektion haben, um ein anderes DataSet zu bewerten, das das dieselbe unabhängigen Variablen als Eingaben verwendet.

> [!div class="checklist"]
> * Bewerten neuer Daten
> * Erstellen eines Histogramms der Bewertungen

> [!NOTE]
> Sie benötigen DDL-Administratorberechtigungen für einige der folgenden Schritte aus.

## <a name="generate-and-save-scores"></a>Generieren und Speichern der Ergebnisse
  
1. Aktualisieren der Datenquelle SqlScoreDS (erstellt [Lektion zwei](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)), verwenden Sie die Spalteninformationen, die in der vorherigen Lektion erstellt haben.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Um sicherzustellen, dass Sie die Ergebnisse nicht verloren gehen, erstellen Sie ein neues Datenquellenobjekt. Klicken Sie dann verwenden Sie das neue Datenquellenobjekt, um eine neue Tabelle in der Datenbank RevoDeepDive aufzufüllen.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    Zu diesem Zeitpunkt ist die Tabelle noch nicht erstellt worden. Diese Anweisung definiert lediglich einen Datencontainer.
     
3. Überprüfen Sie die aktuelle Compute Context mit **rxGetComputeContext()**, und legen Sie den computekontext auf den Server, bei Bedarf.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Überprüfen Sie als Vorsichtsmaßnahme das Vorhandensein der Ausgabetabelle. Wenn bereits eine mit dem gleichen Namen vorhanden ist, erhalten Sie einen Fehler beim Versuch, die neue Tabelle zu schreiben.
  
    Rufen Sie dazu die Funktionen [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) und [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable)auf, und übergeben Sie den Tabellennamen als Eingabe.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **RxSqlServerTableExists** fragt den ODBC-Treiber ab und gibt TRUE zurück, wenn die Tabelle "false" vorhanden, andernfalls ist.
    + **RxSqlServerDropTable** führt die DDL-Anweisungen aus, und gibt true zurück, wenn die Tabelle erfolgreich gelöscht, "false" andernfalls.

5. Führen Sie [RxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) die Bewertungen erstellen und speichern Sie sie in der neuen Tabelle, die in Data Source SqlScoreDS definiert.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Die Funktion **rxPredict** ist eine weitere Funktion, die die Ausführung in Remotecomputekontexten unterstützt. Sie können die **RxPredict** Funktion zum Erstellen von Bewertungen aus Modellen basierend auf [RxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [RxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit), oder ["rxglm"](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm).
  
    - Der Parameter *writeModelVars* wurde in diesem Beispiel auf **TRUE** festgelegt. Dies bedeutet, dass die Variablen, die für die Schätzung verwendet wurden, in die neue Tabelle aufgenommen werden.
  
    - Der Parameter *predVarNames* gibt die Variable an, in der Ergebnisse gespeichert werden. Eine neue Variable übergeben `ccFraudLogitScore`.
  
    - Der *type* -Parameter für **rxPredict** definiert, wie die Vorhersagen berechnet werden sollen. Geben Sie das Schlüsselwort **Antwort** zum Generieren von Bewertungen basierend auf der Skala der Response-Variable. Oder verwenden Sie das Schlüsselwort **Link** zum Generieren von Bewertungen basierend auf der zugrunde liegenden Link-Funktion in diesem Fall werden Vorhersagen erstellt, mit einer logistischen Skala.

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

Nachdem die neue Tabelle erstellt wurde, berechnen und ein Histogramm von 10.000 vorhergesagten auswertungen anzuzeigen. Berechnung ist schneller, wenn Sie die hohen und niedrigen Werte angeben, also diese aus der Datenbank abrufen und Ihren Arbeitsdaten hinzufügen.

1. Erstellen Sie eine neue Datenquelle, SqlMinMax, das Abfragen die Datenbank, um die hohen und niedrigen Werte zu erhalten.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     In diesem Beispiel wird veranschaulicht, wie einfach die Verwendung von **RxSqlServerData** -Datenquellobjekten ist, um beliebige Datasets auf Grundlage von SQL-Abfragen, Funktionen oder gespeicherten Prozeduren zu definieren und diese anschließend in Ihrem R-Code zu verwenden. Die Variable speichert nicht die eigentlichen Werte, sondern lediglich die Datenquellendefinition. Die Abfrage wird ausgeführt, um die Werte nur dann zu generieren, wenn sie in einer Funktion wie **rxImport**verwendet wird.
      
2. Rufen Sie die [RxImport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) Funktion, legen Sie die Werte in einem Datenrahmen, die freigegeben werden können, verschiedene computekontexte.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Ergebnisse**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Nun, dass die maximale und minimale Werte verfügbar sind, verwenden Sie die Werte, um eine andere Datenquelle für die generierten Werte zu erstellen.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Verwenden Sie die SqlOutScoreDS Data Source-Objekt, erhalten die Bewertung zu berechnen und ein Histogramm angezeigt. Fügen Sie bei Bedarf den Code hinzu, um den Computekontext festzulegen.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Ergebnisse**
  
    ![Komplexes von R erstelltes Histogramm](media/rsql-sue-complex-histogram.png "complex histogram created by R")
  
## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Umwandeln von Daten mithilfe von R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)