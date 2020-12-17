---
title: 'R-Tutorial: Erstellen und Speichern des Modells'
description: In diesem Tutorial erfahren Sie Details zum Erstellen eines Machine Learning-Modells in der Sprache R für die Verwendung für datenbankinterne SQL Server-Analysen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15'
ms.openlocfilehash: 1974c58ad2adbad3b7e136ffa36ffa88b5783fc6
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97470051"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Erstellen eines R-Modells und Speichern in SQL Server (exemplarische Vorgehensweise)
[!INCLUDE [SQL Server 2016](../../includes/applies-to-version/sqlserver2016.md)]

Im folgenden Schritt wird demonstriert, wie Sie ein Machine Learning-Modell erstellen und das Modell in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]speichern. Nachdem Sie ein Modell gespeichert haben, können Sie es direkt aus dem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code mithilfe der gespeicherten Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) oder der [Funktion PREDICT (T-SQL)](../../t-sql/queries/predict-transact-sql.md) aufrufen.

## <a name="prerequisites"></a>Voraussetzungen

Bei diesem Schritt wird eine laufende R-Sitzung basierend auf den vorherigen Schritten in dieser Vorgehensweise angenommen. Es werden die Verbindungszeichenfolgen und Datenquellenobjekte verwendet, die in diesen Schritten erstellt wurden. Die folgenden Tools und Pakete werden zum Ausführen des Skripts verwendet.

+ Rgui.exe zum Ausführen von R-Befehlen
+ Management Studio zum Ausführen von T-SQL
+ ROCR-Paket
+ RODBC-Paket

### <a name="create-a-stored-procedure-to-save-models"></a>Erstellen einer gespeicherten Prozedur zum Speichern von Modellen

Im folgenden Schritt wird eine gespeicherte Prozedur verwendet, um ein trainiertes Modell in SQL Server zu speichern. Diese Aufgabe wird durch Erstellen einer gespeicherten Prozedur zum Ausführen dieses Vorgangs vereinfacht.

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
> Wenn Sie eine Fehlermeldung erhalten, stellen Sie sicher, dass Ihr Anmeldename über die Berechtigung zum Erstellen von Objekten verfügt. Sie können explizite Berechtigungen zum Erstellen von Objekten erteilen, indem Sie eine T-SQL-Anweisung wie die folgende ausführen: `exec sp_addrolemember 'db_owner', '<user_name>'`.

## <a name="create-a-classification-model-using-rxlogit"></a>Erstellen eines Klassifizierungsmodells mit rxLogit

Das Modell ist eine binäre Klassifizierung, die vorhersagt, ob der Taxifahrer eher ein Trinkgeld für eine bestimmte Fahrt erhält oder nicht. Verwenden Sie die Datenquelle, die Sie in der vorherigen Lektion erstellt haben, um die Trinkgeldklassifizierung mithilfe der logistischen Regression zu trainieren.

1. Rufen Sie die [rxLogit](/r-server/r-reference/revoscaler/rxlogit) -Funktion auf, die im **RevoScaleR** -Paket enthalten ist, um ein logistisches Regressionsmodell zu erstellen. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    Der Aufruf, der das Modell erstellt, wird in der system.time-Funktion eingeschlossen. Dadurch können Sie die erforderliche Zeit zum Erstellen des Modells abrufen.

2. Nachdem Sie das Modell erstellt haben, können Sie es mithilfe der `summary`-Funktion untersuchen und die Koeffizienten anzeigen.

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

1. Verwenden Sie zunächst die [RxSqlServerData](/r-server/r-reference/revoscaler/rxsqlserverdata)-Funktion, um ein Datenquellenobjekt zum Speichern des Bewertungsergebnisses zu definieren.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Um dieses Beispiel zu vereinfachen, ist die Eingabe für das logistische Regressionsmodell die gleiche Funktionsdatenquelle (`sql_feature_ds`), die Sie zum Trainieren des Modells verwendet haben.  Es wird in der Regel vorkommen, dass Sie neue Daten bewerten müssen oder andere Daten für das Testen oder Trainieren beiseite gestellt haben.
  
    + Die Vorhersageergebnisse werden in der Tabelle _taxiscoreOutput_ gespeichert. Beachten Sie, dass das Schema für diese Tabelle nicht definiert ist, wenn Sie es mit der rxSqlServerData-Funktion erstellen. Das Schema wird aus der rxPredict-Ausgabe abgerufen.
  
    + Um die Tabelle zu erstellen, die die vorhergesagten Werte speichert, muss der SQL-Login, der die Datenfunktion „rxSqlServer“ ausführt, über DDL-Berechtigungen in der Datenbank verfügen. Wenn dieser Anmeldename keine Tabellen erstellen kann, schlägt die Anweisung fehl.

2. Rufen Sie die Funktion [rxPredict](/r-server/r-reference/revoscaler/rxpredict) auf, um Ergebnisse zu generieren.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Wenn die Anweisung erfolgreich ausgeführt wird, nimmt dieser Vorgang einige Zeit in Anspruch. Nach Beendigung der Ausführung können Sie SQL Server Management Studio öffnen und überprüfen, ob die Tabelle erstellt wurde und ob diese die Spalte „Bewertung“ und andere erwartete Ausgaben enthält.

## <a name="plot-model-accuracy"></a>Zeichnen der Modellgenauigkeit

Um eine Vorstellung von der Genauigkeit des Modells zu erhalten, können Sie die Funktion [rxRoc](/r-server/r-reference/revoscaler/rxroc) verwenden, um die ROC-Kurve (Receiver Operating Characteristics Curve, Grenzwertoptimierungskurve) zu zeichnen. Da rxRoc eine der neuen Funktionen ist, die mit dem RevoScaleR-Paket bereitgestellt werden und Remotecomputekontexte unterstützt, haben Sie zwei Möglichkeiten:

+ Sie können die rxRoc-Funktion verwenden, um das Diagramm im Remotecomputekontext auszuführen und anschließend das Diagramm an Ihren lokalen Client zurückgeben.

+ Sie können die Daten auch in Ihren Clientcomputer importieren und andere Zeichenfunktionen von R verwenden, um das Leistungsdiagramm zu erstellen.

In diesem Abschnitt experimentieren Sie mit beiden Techniken.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Erstellen eines Diagramms im Remotecomputekontext (SQL Server)

1. Rufen Sie die rxRoc-Funktion auf, und stellen Sie die Daten bereit, die zuvor als Eingabe definiert wurden.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Dieser Aufruf gibt die Werte zurück, die beim Berechnen des ROC-Diagramms verwendet werden. Die Spalte „Bezeichnung“ verfügt über die Variable _tipped_ und zeigt die tatsächlichen Ergebnissen an, die Sie vorhersagen möchten, die Spalte _Bewertung_ enthält hingegen die Vorhersage.

2. Um das Diagramm zu zeichnen, können Sie das ROC-Objekt speichern und es dann mit der Zeichnungsfunktion zeichnen. Das Diagramm wird im Remotecomputekontext erstellt und anschließend an die R-Umgebung zurückgegeben.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Sie können das Diagramm anzeigen, indem Sie das Grafikgerät von R öffnen oder auf das Fenster **Zeichnung** in RStudio klicken.

    ![ROC-Zeichnung für das Modell](media/rsql-e2e-rocplot.png "ROC-Zeichnung für das Modell")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Erstellen der Zeichnungen im lokalen Computekontext mithilfe von Daten aus SQL Server

Sie können überprüfen, ob der Computekontext lokal ist, indem Sie `rxGetComputeContext()` an der Eingabeaufforderung ausführen. Der Rückgabewert sollte „RxLocalSeq Compute Context“ lauten.

1. Der Vorgang für den lokalen Computekontext ist weitgehend identisch. Verwenden Sie die Funktion [rxImport](/r-server/r-reference/revoscaler/rximport), um die angegebenen Daten in die lokale R-Umgebung zu verschieben.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Wenn Sie die Daten im lokalen Arbeitsspeicher verwenden, laden Sie das **ROCR**-Paket, und verwenden Sie die Vorhersagefunktion aus diesem Paket, um einige neue Vorhersagen zu erstellen.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Generieren Sie basierend auf den Werten, die in der Ausgabevariablen `pred`gespeichert sind, eine lokale Zeichnung.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Zeichnen der Modellleistung mithilfe von R](media/rsql-e2e-performanceplot.png "Zeichnen der Modellleistung mithilfe von R")

> [!NOTE]
> Je nachdem, wie viele Datenpunkte Sie verwendet haben, können sich Ihre Diagramme von diesen unterscheiden.

## <a name="deploy-the-model"></a>Bereitstellen des Modells

Nachdem Sie ein Modell erstellt und festgestellt haben, dass es gut funktioniert, möchten Sie es wahrscheinlich auf einer Site bereitstellen, über die es von Benutzern oder Personen in Ihrer Organisation verwendet oder in regelmäßigen Abständen neu trainiert und erstellt werden kann. Dieser Vorgang wird manchmal als *Operationalisierung* eines Modells bezeichnet. In SQL Server wird die Operationalisierung durch Einbetten von R-Code in eine gespeicherte Prozedur erreicht. Da sich der Code in der Prozedur befindet, kann er von jeder Anwendung aus aufgerufen werden, die eine Verbindung mit SQL Server herstellen kann.

Bevor Sie jedoch das Modell aus einer externen Anwendung aufrufen können, müssen Sie das Modell in der Datenbank speichern, die für die Produktion verwendet wird. Trainierte Modelle werden im Binärformat in einer einzelnen Spalte des Typs **varbinary(max)** gespeichert.

Ein typischer Bereitstellungsworkflow besteht aus den folgenden Schritten:

1. Serialisieren des Modells in eine hexadezimale Zeichenfolge
2. Übertragen des serialisierten Objekts in die Datenbank
3. Speichern des Modells in einer varbinary(max)-Spalte

In diesem Abschnitt erfahren Sie, wie Sie eine gespeicherte Prozedur verwenden, um das Modell beizubehalten und es für Vorhersagen verfügbar zu machen. Die in diesem Abschnitt verwendete gespeicherte Prozedur lautet „PersistModel“. Die Definition von „PersistModel“ befindet sich unter [Voraussetzungen](#prerequisites).

1. Wechseln Sie zurück zu Ihrer lokalen R-Umgebung, wenn Sie sie nicht bereits verwenden, serialisieren Sie das Modell, und speichern Sie es in einer Variablen.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Öffnen Sie eine ODBC-Verbindung mithilfe von **RODBC**. Wenn Sie das Paket bereits geladen haben, können Sie den Aufruf von RODBC weglassen.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Rufen Sie die gespeicherte Prozedur „PersistModel“ für SQL Server auf, um das serialisierte Objekt in die Datenbank zu übertragen und die binäre Darstellung des Modells in einer Spalte zu speichern. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Überprüfen Sie mit Management Studio, ob das Modell vorhanden ist. Klicken Sie in Objekt-Explorer mit der rechten Maustaste auf die Tabelle **nyc_taxi_models**, und klicken Sie auf **Oberste 1000 Zeilen auswählen**. In den Ergebnissen sollte eine binäre Darstellung in der Spalte **Modelle** angezeigt werden.

Das Speichern eines Modells in einer Tabelle erfordert nur eine INSERT-Anweisung. Es ist jedoch häufig einfacher, wenn es in einer gespeicherten Prozedur wie *PersistModel* umschlossen ist.

## <a name="next-steps"></a>Nächste Schritte

In der nächsten und letzten Lektion erfahren Sie, wie Sie eine Bewertung anhand des gespeicherten Modells mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)] ausführen.

> [!div class="nextstepaction"]
> [Bereitstellen des R-Modells und Verwendung in SQL](walkthrough-deploy-and-use-the-model.md)