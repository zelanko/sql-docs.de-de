---
title: Erstellen eines R-Modells und speichern Sie mit SQL Server (Exemplarische Vorgehensweise) – SQL Server-Machine Learning
description: Dieses Tutorial zeigt, wie zum Erstellen eines R-Sprache-Modells für SQL Server in-Database-Analyse verwendet.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b02b1e0298af6fbb96ba5ddd8d5a18dc8e154598
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645479"
---
# <a name="build-an-r-model-and-save-to-sql-server-walkthrough"></a>Erstellen eines R-Modells und speichern Sie mit SQL Server (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Schritt erfahren Sie, wie ein Machine Learning-Modell zu erstellen und speichern Sie das Modell im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ein Modell gespeichert werden, können Sie diese direkt aufrufen [!INCLUDE[tsql](../../includes/tsql-md.md)] code mithilfe der gespeicherten Systemprozedur, [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) oder [Vorhersagefunktion (T-SQL)](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql).

## <a name="prerequisites"></a>Erforderliche Komponenten

Dieser Schritt setzt voraus, eine laufende R-Sitzung basierend auf den vorherigen Schritten in dieser exemplarischen Vorgehensweise. Er verwendet die Zeichenfolgen und Data Source Verbindungsobjekte in diesen Schritten erstellt haben. Die folgenden Tools und Pakete werden verwendet, um das Skript auszuführen.

+ Rgui.exe zum Ausführen von R-Befehlen
+ Management Studio zum Ausführen von T-SQL
+ ROCR-Paket
+ RODBC-Paket

### <a name="create-a-stored-procedure-to-save-models"></a>Erstellen einer gespeicherten Prozedur, um Modelle zu speichern.

Dieser Schritt verwendet eine gespeicherte Prozedur, um ein trainiertes Modell in SQL Server zu speichern. Erstellen eine gespeicherte Prozedur zum Ausführen dieses Vorgangs vereinfacht die Aufgabe.

Führen Sie den folgenden T-SQL-Code in ein Abfragefenster in Management Studio, um die gespeicherte Prozedur zu erstellen.

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
> Wenn Sie eine Fehlermeldung erhalten, stellen Sie sicher, dass die Anmeldung über die Berechtigung zum Erstellen von Objekten. Sie können die explizite Berechtigungen zum Erstellen von Objekten durch Ausführen einer T-SQL-Anweisung wie folgt erteilen: `exec sp_addrolemember 'db_owner', '<user_name>'`.

## <a name="create-a-classification-model-using-rxlogit"></a>Erstellen eines klassifizierungsmodells mit rxLogit

Das Modell ist eine binäre Klassifizierung, die vorhersagt, ob der taxifahrer eher ein Trinkgeld für eine bestimmte Fahrt erhält oder nicht abrufen. Verwenden Sie die Datenquelle, die Sie in der vorherigen Lektion die Trinkgeld-Klassifizierung trainiert erstellt mithilfe der logistischen Regression.

1. Rufen Sie die [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit) -Funktion auf, die im **RevoScaleR** -Paket enthalten ist, um ein logistisches Regressionsmodell zu erstellen. 

    ```R
    system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = featureDataSource));
    ```

    Der Aufruf, der das Modell erstellt, wird in der system.time-Funktion eingeschlossen. Dadurch können Sie die erforderliche Zeit zum Erstellen des Modells abrufen.

2. Nachdem Sie das Modell erstellt haben, können Sie überprüfen, mit der `summary` Funktion, und die Koeffizienten anzeigen.

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

1. Verwenden Sie zunächst die [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) Funktion, um ein Datenquellenobjekt, für das Speichern der Ergebnisse der Bewertung zu definieren.

    ```R
    scoredOutput <- RxSqlServerData(
      connectionString = connStr,
      table = "taxiScoreOutput"  )
    ```

    + Um dieses Beispiel zu vereinfachen, ist die Eingabe für das logistische Regressionsmodell die gleiche Funktion-Datenquelle (`sql_feature_ds`), die Sie zum Trainieren des Modells verwendet.  Es wird in der Regel vorkommen, dass Sie neue Daten bewerten müssen oder andere Daten für das Testen oder Trainieren beiseite gestellt haben.
  
    + Die Vorhersageergebnisse werden in der Tabelle gespeichert sein _TaxiscoreOutput_. Beachten Sie, dass das Schema für diese Tabelle nicht definiert ist, wenn Sie diese mithilfe von RxSqlServerData erstellen. Das Schema wird aus der Ausgabe RxPredict abgerufen.
  
    + Zum Erstellen der Tabelle, die die vorhergesagten Werte speichert, muss die SQL-Anmeldung, die die "rxsqlserver" Data-Funktion ausführt, DDL-Administratorrechte in der Datenbank verfügen. Wenn der Anmeldename keine Tabellen erstellen kann, schlägt die Anweisung fehl.

2. Rufen Sie die Funktion [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict) auf, um Ergebnisse zu generieren.

    ```R
    rxPredict(modelObject = logitObj,
        data = featureDataSource,
        outData = scoredOutput,
        predVarNames = "Score",
        type = "response",
        writeModelVars = TRUE, overwrite = TRUE)
    ```
    
    Wenn die Anweisung erfolgreich ist, dauert es einige Zeit ausgeführt. Nach Abschluss des Vorgangs können Sie SQL Server Management Studio öffnen und überprüfen, ob die Tabelle erstellt wurde, und enthält die Ergebnisspalte und andere Ausgabe erwartete.

## <a name="plot-model-accuracy"></a>Zeichnen der modellgenauigkeit

Um eine Vorstellung von der Genauigkeit des Modells zu erhalten, können Sie die [RxRoc](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxroc) Funktion, um die Receiver Operating Kurve zu zeichnen. Da RxRoc eine der neuen Funktionen von RevoScaleR-Paket bereitgestellt wird, die remotecomputekontexte unterstützt, Sie haben zwei Optionen:

+ Sie können die RxRoc-Funktion verwenden, führen Sie das Diagramm, in dem entfernten computekontext, und klicken Sie dann das Diagramm auf den lokalen Client zurückgeben.

+ Sie können die Daten auch in Ihren Clientcomputer importieren und andere Zeichenfunktionen von R verwenden, um das Leistungsdiagramm zu erstellen.

In diesem Abschnitt experimentieren Sie mit beiden Methoden.

### <a name="execute-a-plot-in-the-remote-sql-server-compute-context"></a>Erstellen eines Diagramms im Remotecomputekontext (SQL Server)

1. Rufen Sie die Funktion RxRoc, und geben Sie die Daten, die zuvor als Eingabe definiert.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    ```

    Dieser Aufruf gibt zurück, die Werte, die beim Berechnen der ROC-Diagramm verwendet wird. Die Bezeichnungsspalte ist _"tipped"_, IValidator.h die tatsächlichen Ergebnisse, die Sie vorhersagen möchten, während die _Bewertung_ Spalte hat die Vorhersage.

2. Um tatsächlich im Diagramm zu zeichnen, können das ROC-Objekt speichern und ziehen Sie es mit der Grafik-Funktion. Das Diagramm wird auf dem entfernten computekontext erstellt und an Ihre R-Umgebung zurückgegeben.

    ```R
    scoredOutput = rxImport(scoredOutput);
    rocObjectOut <- rxRoc(actualVarName= "tipped", predVarNames = "Score", scoredOutput);
    plot(rocObjectOut);
    ```

    Zeigen Sie das Diagramm, indem Sie das Grafikgerät von R öffnen, oder durch Klicken auf die **zeichnen** Fenster in RStudio.

    ![ROC-Zeichnung für das Modell](media/rsql-e2e-rocplot.png "ROC plot for the model")

### <a name="create-the-plots-in-the-local-compute-context-using-data-from-sql-server"></a>Erstellen der Zeichnungen im lokalen Computekontext mithilfe von Daten aus SQL Server

Sie können überprüfen, ob der computekontext ist mit lokalen `rxGetComputeContext()` an der Eingabeaufforderung. Der zurückgegebene Wert sollte "RxLocalSeq Compute Context".

1. Für den lokalen computekontext ist der Prozess ähnlich. Sie verwenden die [RxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport) Funktion, die die angegebenen Daten in Ihrer lokalen R-Umgebung zu bringen.

    ```R
    scoredOutput = rxImport(scoredOutput)
    ```

2. Mit den Daten im lokalen Speicher an, die Sie laden die **ROCR** Packen und verwenden Sie die Vorhersagefunktion aus diesem Paket, um einige neuen Vorhersagen zu erstellen.

    ```R
    library('ROCR');
    pred <- prediction(scoredOutput$Score, scoredOutput$tipped);
    ```

3. Eine lokale Zeichnung, basierend auf den in der Output-Variable gespeicherten Werten zu generieren `pred`.

    ```R
    acc.perf = performance(pred, measure = 'acc');
    plot(acc.perf);
    ind = which.max( slot(acc.perf, 'y.values')[[1]] );
    acc = slot(acc.perf, 'y.values')[[1]][ind];
    cutoff = slot(acc.perf, 'x.values')[[1]][ind];
    ```

    ![Zeichnen der Modellleistung mithilfe von R](media/rsql-e2e-performanceplot.png "plotting model performance using R")

> [!NOTE]
> Diagramme können sieht anders aus diesen, je nachdem wie viele Datenpunkte aus, die Sie verwendet.

## <a name="deploy-the-model"></a>Bereitstellen des Modells

Nachdem Sie ein Modell erstellt und überprüft, dass es ordnungsgemäß ausgeführt wird, sollten Sie es auf einer Website bereitstellen, in dem Benutzer oder Personen in Ihrer Organisation erstellen können, Verwenden des Modells oder vielleicht zu trainieren und kalibrieren Sie das Modell in regelmäßigen Abständen neu. Dieser Prozess wird manchmal genannt *operationalisieren* eines Modells. Operationalisierung erfolgt in SQL Server durch Einbetten von R-Code in einer gespeicherten Prozedur. Da der Code in der Prozedur befindet, kann sie von jeder Anwendung aufgerufen werden, die eine Verbindung mit SQL Server herstellen können.

Bevor Sie das Modell aus einer externen Anwendung aufrufen können, müssen Sie das Modell auf die für die Produktion verwendete Datenbank speichern. Trainierte Modelle werden gespeichert, in binärer Form, in einer einzelnen Spalte des Typs **'varbinary(max)'**.

Ein typische Bereitstellung-Workflow besteht aus die folgenden Schritte aus:

1. Serialisieren des Modells in eine hexadezimale Zeichenfolge
2. Übertragen des serialisierten Objekts in der Datenbank
3. Speichern Sie das Modell in einer varbinary(max)-Spalte

Erfahren Sie in diesem Abschnitt, wie Sie mithilfe eine gespeicherte Prozedur beibehalten des Modells und für Vorhersagen zur Verfügung stellen. Die gespeicherte Prozedur in diesem Abschnitt wird die PersistModel. Die Definition der PersistModel befindet sich in [Voraussetzungen](#prerequisites).

1. Wechseln Sie zurück zu Ihrer lokalen R-Umgebung, wenn Sie nicht bereits verwenden, serialisieren Sie das Modell und speichern Sie ihn in einer Variablen.

    ```R
    rxSetComputeContext("local");
    modelbin <- serialize(logitObj, NULL);
    modelbinstr=paste(modelbin, collapse="");
    ```

2. Öffnen Sie eine ODBC-Verbindung mit **RODBC**. Sie können den Aufruf von RODBC weglassen, wenn Sie bereits das Paket geladen haben.

    ```R
    library(RODBC);
    conn <- odbcDriverConnect(connStr);
    ```

3. Rufen Sie die PersistModel gespeicherte Prozedur in SQL Server auf Transmite des serialisierten Objekts in der Datenbank, und speichern Sie die binäre Darstellung des Modells in einer Spalte. 

    ```R
    q <- paste("EXEC PersistModel @m='", modelbinstr,"'", sep="");
    sqlQuery (conn, q);
    ```

4. Verwenden Sie Management Studio um zu überprüfen, ob das Modell vorhanden ist. Objekt-Explorer mit der Maustaste auf die **Nyc_taxi_models** Tabelle, und klicken Sie auf **oberste 1000 Zeilen auswählen**. In der Ergebnisse zu erzielen, sollte in eine binäre Darstellung der **Modelle** Spalte.

Das Speichern eines Modells in einer Tabelle erfordert nur eine INSERT-Anweisung. Allerdings ist es oft einfacher, wenn in einer gespeicherten Prozedur, z. B. umschlossen *PersistModel*.

## <a name="next-steps"></a>Nächste Schritte

In der nächsten, finalen Lektion erfahren Sie, wie zum Durchführen von Bewertungen für das gespeicherte Modell, indem [!INCLUDE[tsql](../../includes/tsql-md.md)].

> [!div class="nextstepaction"]
> [Bereitstellen Sie das R-Modell und verwenden Sie in SQL](walkthrough-deploy-and-use-the-model.md)
