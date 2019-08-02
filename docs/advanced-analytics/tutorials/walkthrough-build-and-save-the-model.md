---
title: Erstellen eines R-Modells und speichern in SQL Server (Exemplarische Vorgehensweise)
description: Tutorial zum Erstellen eines R-sprach Modells, das für die SQL Server in-Database-Analyse verwendet wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: af2b1bf8f619800737863ff955011b011f4819d0
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715393"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Erstellen eines R-Modells und speichern in SQL Server (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Schritt erfahren Sie, wie Sie ein Machine Learning-Modell erstellen und das Modell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in speichern. Wenn Sie ein Modell speichern, können Sie es direkt aus [!INCLUDE[tsql](../../includes/tsql-md.md)] dem Code abrufen, indem Sie die gespeicherte System Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) oder die [Vorhersage (T-SQL)-Funktion](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)verwenden.

## <a name="prerequisites"></a>Vorraussetzungen

Dieser Schritt setzt eine laufende R-Sitzung voraus, die auf vorherigen Schritten in dieser exemplarischen Vorgehensweise basiert. Dabei werden die Verbindungs Zeichenfolgen und Datenquellen Objekte verwendet, die in diesen Schritten erstellt werden. Die folgenden Tools und Pakete werden zum Ausführen des Skripts verwendet.

+ "Rgui. exe" zum Ausführen von R-Befehlen
+ Management Studio zum Ausführen von T-SQL
+ Rocr-Paket
+ Rodbc-Paket

### <a name="create-a-stored-procedure-to-save-models"></a>Erstellen einer gespeicherten Prozedur zum Speichern von Modellen

In diesem Schritt wird eine gespeicherte Prozedur verwendet, um ein trainiertes Modell in SQL Server zu speichern. Durch das Erstellen einer gespeicherten Prozedur zum Ausführen dieses Vorgangs wird die Aufgabe vereinfacht.

Führen Sie den folgenden T-SQL-Code in einem Abfragefenster in Management Studio aus, um die gespeicherte Prozedur zu erstellen.

```sql
USE [NYCTaxi_Sample]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PersistModel')
  DROP PROCEDURE PersistModel
GO

CREATE PROCEDURE [dbo].[PersistModel] @m nvarchar(max)
AS
BEGIN
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;
    insert into nyc_taxi_models (model) values (convert(varbinary(max),@m,2))
END
GO
```

> [!NOTE]
> Wenn Sie einen Fehler erhalten, stellen Sie sicher, dass Ihre Anmeldung über die Berechtigung zum Erstellen von Objekten verfügt. Sie können explizite Berechtigungen zum Erstellen von-Objekten erteilen, indem Sie eine T-SQL- `exec sp_addrolemember 'db_owner', '<user_name>'`Anweisung wie die folgende ausführen:.

## <a name="create-a-classification-model-using-rxlogit"></a>Erstellen eines Klassifizierungs Modells mithilfe von rxlogit

Das Modell ist ein binärer Klassifizierer, der vorhersagt, ob der Taxi Treiber wahrscheinlich einen Tipp für eine bestimmte Fahrt erhält oder nicht. Verwenden Sie die Datenquelle, die Sie in der vorherigen Lektion erstellt haben, um den Tip Classifier mithilfe der logistischen Regression zu trainieren.

1. Rufen Sie die [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) -Funktion auf, die im **RevoScaleR** -Paket enthalten ist, um ein logistisches Regressionsmodell zu erstellen. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    Der Aufruf, der das Modell erstellt, wird in der system.time-Funktion eingeschlossen. Dadurch können Sie die erforderliche Zeit zum Erstellen des Modells abrufen.

2. Nachdem Sie das Modell erstellt haben, können Sie es mithilfe der `summary` -Funktion untersuchen und die Koeffizienten anzeigen.

    ```R
    summary(logitObj);
    ```

    **Ergebnisse**
    
    ```R
     *Logistic Regression Results for: tipped ~ passenger_count + trip_distance + trip_time_in_secs +*
     direct_distance* 
     *Data: featureDataSource (RxSqlServerData Data Source)*
     *Dependent variable(s): tipped*
     *Total independent variables: 5*
     *Number of valid observations: 17068*
     *Number of missing observations: 0*
     *-2\*LogLikelihood: 23540.0602 (Residual deviance on 17063 degrees of freedom)*
     *Coefficients:*
     *Estimate Std. Error z value Pr(>|z|)*
     *(Intercept)       -2.509e-03  3.223e-02  -0.078  0.93793*
     *passenger_count   -5.753e-02  1.088e-02  -5.289 1.23e-07 \*\*\**
     *trip_distance     -3.896e-02  1.466e-02  -2.658  0.00786 \*\**
     *trip_time_in_secs  2.115e-04  4.336e-05   4.878 1.07e-06 \*\*\**
     *direct_distance    6.156e-02  2.076e-02   2.966  0.00302 \*\**
     *---*
     *Signif. codes:  0 ‘\*\*\*’ 0.001 ‘\*\*’ 0.01 ‘\*’ 0.05 ‘.’ 0.1 ‘ ’ 1*
     *Condition number of final variance-covariance matrix: 48.3933*
     *Number of iterations: 4*
   ```

## <a name="use-the-logistic-regression-model-for-scoring"></a>Verwenden des logistischen Regressionsmodells für die Bewertung

Da das Modell bereits erstellt wurde, können Sie es verwenden, um vorherzusagen, ob der Fahrer eher eine Trinkgeld für eine bestimmte Fahrt erhält oder nicht.

1. Verwenden Sie zunächst die [rxsqlserverdata](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) -Funktion, um ein Datenquellen Objekt zum Speichern des Bewertungsergebnisses zu definieren.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Um dieses Beispiel zu vereinfachen, ist die Eingabe für das logistische Regressionsmodell dieselbe Merkmals Daten`sql_feature_ds`Quelle (), die Sie zum Trainieren des Modells verwendet haben.  Es wird in der Regel vorkommen, dass Sie neue Daten bewerten müssen oder andere Daten für das Testen oder Trainieren beiseite gestellt haben.
  
    + Die Vorhersage Ergebnisse werden in der Tabelle _taxiscoreoutput_gespeichert. Beachten Sie, dass das Schema für diese Tabelle nicht definiert ist, wenn Sie es mithilfe von rxsqlserverdata erstellen. Das Schema wird aus der rxvorhersage-Ausgabe abgerufen.
  
    + Um die Tabelle zu erstellen, in der die vorhergesagten Werte gespeichert werden, muss die SQL-Anmeldung, auf der die rxsqlserver-Daten Funktion ausgeführt wird, über DDL-Berechtigungen Wenn die Anmeldung keine Tabellen erstellen kann, schlägt die Anweisung fehl.

2. Rufen Sie die Funktion [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) auf, um Ergebnisse zu generieren.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Wenn die Anweisung erfolgreich ausgeführt wird, sollte die Ausführung einige Zeit in Anspruch nehmen. Wenn Sie fertig sind, können Sie SQL Server Management Studio öffnen und überprüfen, ob die Tabelle erstellt wurde und dass Sie die Ergebnisspalte und eine andere erwartete Ausgabe enthält.

## <a name="plot-model-accuracy"></a>Plotmodellgenauigkeit

Um eine Vorstellung von der Genauigkeit des Modells zu erhalten, können Sie die Funktion [rxroc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) zum Zeichnen der Empfänger Betriebskosten verwenden. Da rxroc eine der neuen Funktionen ist, die vom revoscaler-Paket bereitgestellt werden, das remotecomputekontexte unterstützt, haben Sie zwei Möglichkeiten:

+ Mit der rxroc-Funktion können Sie die Zeichnung im remotecomputekontext ausführen und dann die Zeichnung an Ihren lokalen Client zurückgeben.

+ Sie können die Daten auch in Ihren Clientcomputer importieren und andere Zeichenfunktionen von R verwenden, um das Leistungsdiagramm zu erstellen.

In diesem Abschnitt experimentieren Sie mit beiden Techniken.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Erstellen eines Diagramms im Remotecomputekontext (SQL Server)

1. Nennen Sie die Funktion rxroc, und stellen Sie die zuvor definierten Daten als Eingabe bereit.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Dieser Rückruf gibt die Werte zurück, die beim Berechnen des ROC-Diagramms verwendet werden. Die Bezeichnungs Spalteist mit den tatsächlichen Ergebnissen versehen, die Sie vorhersagen möchten, während die _Score_ -Spalte die Vorhersage enthält.

2. Um das Diagramm tatsächlich zu zeichnen, können Sie das Roc-Objekt speichern und es dann mit der plotfunktion zeichnen. Das Diagramm wird im remotecomputekontext erstellt und an Ihre R-Umgebung zurückgegeben.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Zeigen Sie das Diagramm an, indem Sie das Grafikgerät von R öffnen , oder indem Sie in rstudio auf das Zeichnungs Fenster klicken.

    ![ROC-Zeichnung für das Modell](media/rsql-e2e-rocplot.png "ROC plot for the model")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Erstellen der Zeichnungen im lokalen Computekontext mithilfe von Daten aus SQL Server

Sie können überprüfen, ob der computekontext lokal `rxGetComputeContext()` ist, indem Sie an der Eingabeaufforderung ausführen. Der Rückgabewert sollte "rxlocalabq Compute Context" lauten.

1. Für den lokalen computekontext ist der Prozess sehr ähnlich. Verwenden Sie die Funktion [rximport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) , um die angegebenen Daten in die lokale R-Umgebung zu übertragen.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Wenn Sie die Daten im lokalen Arbeitsspeicher verwenden, laden Sie das **rocr** -Paket und verwenden die Vorhersagefunktion aus diesem Paket, um einige neue Vorhersagen zu erstellen.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Generieren Sie basierend auf den in der Ausgabevariablen `pred`gespeicherten Werten einen lokalen Plot.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Zeichnen der Modellleistung mithilfe von R](media/rsql-e2e-performanceplot.png "plotting model performance using R")

> [!NOTE]
> Je nachdem, wie viele Datenpunkte Sie verwendet haben, können sich Ihre Diagramme von diesen unterscheiden.

## <a name="deploy-the-model"></a>Bereitstellen des Modells

Nachdem Sie ein Modell erstellt und festgestellt haben, dass es gut funktioniert, sollten Sie es wahrscheinlich auf einem Standort bereitstellen, auf dem Benutzer oder Personen in Ihrer Organisation das Modell verwenden können, oder Sie können das Modell in regelmäßigen Abständen neu trainieren und erneut erstellen. Dieser Prozess wird manchmal als *operationalisieren* eines Modells bezeichnet. In SQL Server wird die Operationalisierung durch Einbetten von R-Code in eine gespeicherte Prozedur erreicht. Da sich der Code in der Prozedur befindet, kann er von jeder Anwendung aufgerufen werden, die eine Verbindung mit SQL Server herstellen kann.

Bevor Sie das Modell aus einer externen Anwendung abrufen können, müssen Sie das Modell in der Datenbank speichern, die für die Produktion verwendet wird. Trainierte Modelle werden in Binär Form in einer einzelnen Spalte des Typs **varbinary (max)** gespeichert.

Ein typischer Bereitstellungs Workflow besteht aus den folgenden Schritten:

1. Serialisieren des Modells in eine hexadezimale Zeichenfolge
2. Überträgt das serialisierte Objekt an die Datenbank.
3. Speichern des Modells in einer varbinary (max)-Spalte

In diesem Abschnitt erfahren Sie, wie Sie eine gespeicherte Prozedur verwenden, um das Modell beizubehalten und für Vorhersagen verfügbar zu machen. Die in diesem Abschnitt verwendete gespeicherte Prozedur ist "persistModel". Die Definition von persistModel ist [Voraussetzung](#prerequisites).

1. Wechseln Sie zurück zu Ihrer lokalen R-Umgebung, wenn Sie Sie nicht bereits verwenden, serialisieren Sie das Modell, und speichern Sie es in einer Variablen.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Öffnen Sie eine ODBC-Verbindung mithilfe von **rodbc**. Wenn Sie das Paket bereits geladen haben, können Sie den rodbc-aufrufsbefehl weglassen.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Wenn Sie die gespeicherte Prozedur persistModel auf SQL Server aufzurufen, können Sie das serialisierte Objekt in die Datenbank übertragen und die binäre Darstellung des Modells in einer Spalte speichern. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Überprüfen Sie mit Management Studio, ob das Modell vorhanden ist. Klicken Sie in Objekt-Explorer mit der rechten Maustaste auf die Tabelle **nyc_taxi_models** , und klicken Sie auf **oberste 1000 Zeilen auswählen**. In den Ergebnissen sollte in der Spalte **Modelle** eine binäre Darstellung angezeigt werden.

Das Speichern eines Modells in einer Tabelle erfordert nur eine INSERT-Anweisung. Es ist jedoch häufig einfacher, wenn Sie in eine gespeicherte Prozedur, z. b. *persistModel*, umschließen.

## <a name="next-steps"></a>Nächste Schritte

In der nächsten und abschließenden Lektion erfahren Sie, wie Sie mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)]von eine Bewertung für das gespeicherte Modell durchführen.

> [!div class="nextstepaction"]
> [Bereitstellen des R-Modells und Verwendung in SQL](walkthrough-deploy-and-use-the-model.md)
