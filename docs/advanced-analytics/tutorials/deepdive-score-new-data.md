---
title: Bewerten neuer Daten mithilfe von revoscaler und rxvorhersage
description: 'Tutorial: Exemplarische Vorgehensweise zum Bewerten von Daten mit der Sprache R auf SQL Server.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ff3782fb760e4d3dd1059103bc835b94d9c7581f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714835"
---
# <a name="score-new-data-sql-server-and-revoscaler-tutorial"></a>Bewerten neuer Daten (SQL Server-und revoscaler-Tutorial)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Diese Lektion ist Teil des [revoscaler-Tutorials](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) zur Verwendung von [revoscaler-Funktionen](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server.

In diesem Schritt verwenden Sie das logistische Regressionsmodell, das Sie in der vorherigen Lektion erstellt haben, um ein anderes Dataset zu bewerten, das dieselben unabhängigen Variablen als Eingaben verwendet.

> [!div class="checklist"]
> * Bewerten neuer Daten
> * Erstellen eines Histogramms der Ergebnisse

> [!NOTE]
> Für einige dieser Schritte benötigen Sie DDL-Administratorrechte.

## <a name="generate-and-save-scores"></a>Generieren und Speichern von Bewertungen
  
1. Aktualisieren Sie die sqlscoreds-Datenquelle (erstellt in [Lektion 2](deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)), um die in der vorherigen Lektion erstellten Spalten Informationen zu verwenden.
  
    ```R
    sqlScoreDS <- RxSqlServerData(
        connectionString = sqlConnString,
        table = sqlScoreTable,
        colInfo = ccColInfo,
        rowsPerRead = sqlRowsPerRead)
    ```
  
2. Um sicherzustellen, dass die Ergebnisse nicht verloren gehen, erstellen Sie ein neues Datenquellen Objekt. Verwenden Sie anschließend das neue Datenquellen Objekt, um eine neue Tabelle in der Datenbank revodeepdive aufzufüllen.
  
    ```R
    sqlServerOutDS <- RxSqlServerData(table = "ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead )
    ```
    Zu diesem Zeitpunkt ist die Tabelle noch nicht erstellt worden. Diese Anweisung definiert lediglich einen Datencontainer.
     
3. Überprüfen Sie den aktuellen computekontext mithilfe von **rxgetcomputecontext ()** , und legen Sie bei Bedarf den computekontext auf den Server fest.
  
    ```R
    rxSetComputeContext(sqlCompute)
    ```
  
4. Überprüfen Sie als Vorsichtsmaßnahme, ob die Ausgabe Tabelle vorhanden ist. Wenn bereits eine mit demselben Namen vorhanden ist, erhalten Sie eine Fehlermeldung, wenn Sie versuchen, die neue Tabelle zu schreiben.
  
    Rufen Sie dazu die Funktionen [rxSqlServerTableExists](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable) und [rxSqlServerDropTable](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqlserverdroptable)auf, und übergeben Sie den Tabellennamen als Eingabe.
  
    ```R
    if (rxSqlServerTableExists("ccScoreOutput"))     rxSqlServerDropTable("ccScoreOutput")
    ```
  
    + **rxsqlservertableist** fragt den ODBC-Treiber ab und gibt true zurück, wenn die Tabelle vorhanden ist, andernfalls false.
    + **rxsqlserverdroptable** führt die DDL aus und gibt true zurück, wenn die Tabelle erfolgreich gelöscht wurde, andernfalls false.

5. Führen Sie [rxprognostizieren](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) aus, um die Ergebnisse zu erstellen, und speichern Sie Sie in der neuen Tabelle, die in der Datenquelle sqlscoreds definiert ist.
  
    ```R
    rxPredict(modelObject = logitObj,
        data = sqlScoreDS,
        outData = sqlServerOutDS,
        predVarNames = "ccFraudLogitScore",
          type = "link",
        writeModelVars = TRUE,
        overwrite = TRUE)
    ```
  
    Die Funktion **rxPredict** ist eine weitere Funktion, die die Ausführung in Remotecomputekontexten unterstützt. Sie können die **rxvorhersage** -Funktion verwenden, um Ergebnisse aus Modellen zu erstellen, die auf [rxlinmod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod), [rxlogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)oder [rxglm](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxglm)basieren.
  
    - Der Parameter *writeModelVars* wurde in diesem Beispiel auf **TRUE** festgelegt. Dies bedeutet, dass die Variablen, die für die Schätzung verwendet wurden, in die neue Tabelle aufgenommen werden.
  
    - Der Parameter *predVarNames* gibt die Variable an, in der Ergebnisse gespeichert werden. Hier übergeben Sie die neue Variable `ccFraudLogitScore`.
  
    - Der *type* -Parameter für **rxPredict** definiert, wie die Vorhersagen berechnet werden sollen. Geben Sie die Schlüsselwort **Antwort** zum Generieren von Bewertungen basierend auf der Skala der Antwortvariablen an. Oder verwenden Sie den Schlüsselwort **Link** , um Bewertungen basierend auf der zugrunde liegenden Link Funktion zu generieren. in diesem Fall werden Vorhersagen mit einer logistischen Skalierung erstellt.

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

## <a name="display-scores-in-a-histogram"></a>Anzeigen von Bewertungen in einem Histogramm

Nachdem die neue Tabelle erstellt wurde, berechnen Sie ein Histogramm der vorhergesagten Ergebnisse von 10.000, und zeigen Sie es an. Die Berechnung erfolgt schneller, wenn Sie die niedrigen und hohen Werte angeben. Daher sollten Sie diese aus der Datenbank erhalten und ihren Arbeitsdaten hinzufügen.

1. Erstellen Sie eine neue Datenquelle (sqlminmax), mit der die Datenbank abgefragt wird, um die niedrigen und hohen Werte zu erhalten.
  
    ```R
    sqlMinMax <- RxSqlServerData(
        sqlQuery = paste("SELECT MIN(ccFraudLogitScore) AS minVal,",
        "MAX(ccFraudLogitScore) AS maxVal FROM ccScoreOutput"),
        connectionString = sqlConnString)
    ```

     In diesem Beispiel wird veranschaulicht, wie einfach die Verwendung von **RxSqlServerData** -Datenquellobjekten ist, um beliebige Datasets auf Grundlage von SQL-Abfragen, Funktionen oder gespeicherten Prozeduren zu definieren und diese anschließend in Ihrem R-Code zu verwenden. Die Variable speichert nicht die eigentlichen Werte, sondern lediglich die Datenquellendefinition. Die Abfrage wird ausgeführt, um die Werte nur dann zu generieren, wenn sie in einer Funktion wie **rxImport**verwendet wird.
      
2. Ruft die [rximport](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rximport) -Funktion auf, um die Werte in einem Datenrahmen zu platzieren, der über computekontexte gemeinsam genutzt werden kann.
  
    ```R
    minMaxVals <- rxImport(sqlMinMax)
    minMaxVals <- as.vector(unlist(minMaxVals))
    ```

    **Ergebnisse**
     
    ```R
    > minMaxVals
     
    [1] -23.970256   9.786345
    ```

3. Nachdem die maximalen und minimalen Werte verfügbar sind, verwenden Sie die Werte, um eine andere Datenquelle für die generierten Ergebnisse zu erstellen.
  
    ```R
    sqlOutScoreDS <- RxSqlServerData(sqlQuery = "SELECT ccFraudLogitScore FROM ccScoreOutput",
        connectionString = sqlConnString,
        rowsPerRead = sqlRowsPerRead,
            colInfo = list(ccFraudLogitScore = list(
                low = floor(minMaxVals[1]),
                        high = ceiling(minMaxVals[2]) ) ) )
    ```

4. Verwenden Sie das Datenquellen Objekt sqloutscoreds, um die Ergebnisse zu erhalten, und berechnen Sie ein Histogramm, und zeigen Sie es an. Fügen Sie bei Bedarf den Code hinzu, um den Computekontext festzulegen.
  
    ```R
    # rxSetComputeContext(sqlCompute)
    rxHistogram(~ccFraudLogitScore, data = sqlOutScoreDS)
    ```
  
    **Ergebnisse**
  
    ![Komplexes von R erstelltes Histogramm](media/rsql-sue-complex-histogram.png "complex histogram created by R")
  
## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Umwandeln von Daten mithilfe von R](../../advanced-analytics/tutorials/deepdive-transform-data-using-r.md)