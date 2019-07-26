---
title: Trainieren und Speichern eines python-Modells mit T-SQL
description: Python-Tutorial, das zeigt, wie ein Modell mithilfe von Transact-SQL auf SQL Server trainiert und gespeichert wird.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 41403018f6b3a2740328ad1576f8c357e7896b12
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470566"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>Trainieren und Speichern eines python-Modells mit T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist Teil eines Tutorials, [in-Database-python-Analyse für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt erfahren Sie, wie Sie ein Machine Learning-Modell mithilfe der Python **-Pakete scikit-Learn** und **revoscalepy**trainieren. Diese python-Bibliotheken wurden bereits mit SQL Server Machine Learning Services installiert.

Sie laden die Module und rufen die erforderlichen Funktionen auf, um das Modell mithilfe einer gespeicherten Prozedur SQL Server zu erstellen und zu trainieren. Für das Modell sind die Daten Features erforderlich, die Sie in früheren Lektionen entwickelt haben. Schließlich speichern Sie das trainierte Modell in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle.
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Aufteilen der Beispiel Daten in Trainings-und Testsätze

1. Erstellen Sie eine gespeicherte Prozedur mit dem Namen **pytraintestsplit** , um die Daten in der nyctaxi_sample-Tabelle in zwei Teile zu unterteilen: nyctaxi_sample_training und nyctaxi_sample_testing. 

    Diese gespeicherte Prozedur sollte bereits für Sie erstellt worden sein, aber Sie können den folgenden Code ausführen, um Sie zu erstellen:

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainTestSplit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainTestSplit] (@pct int)
    AS
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_training
    SELECT * into nyctaxi_sample_training FROM nyctaxi_sample WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) < @pct
    
    DROP TABLE IF EXISTS dbo.nyctaxi_sample_testing
    SELECT * into nyctaxi_sample_testing FROM nyctaxi_sample
    WHERE (ABS(CAST(BINARY_CHECKSUM(medallion,hack_license)  as int)) % 100) > @pct
    GO
    ```

2. Wenn Sie Ihre Daten mithilfe einer benutzerdefinierten Teilung aufteilen möchten, führen Sie die gespeicherte Prozedur aus, und geben Sie eine ganze Zahl ein, die den Prozentsatz der dem Trainings Satz zugeordneten Daten darstellt. Beispielsweise würde die folgende Anweisung dem Trainings Satz 60% der Daten zuordnen.

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Erstellen eines logistischen Regressionsmodells

Nachdem Sie die Daten vorbereitet haben, können Sie Sie zum Trainieren eines Modells verwenden. Dazu rufen Sie eine gespeicherte Prozedur auf, die einen Python-Code ausführt und die Trainingsdaten Tabelle als Eingabe annimmt. In diesem Tutorial erstellen Sie zwei Modelle, beide binäre Klassifizierungs Modelle:

+ Die gespeicherte Prozedur **pytrainscikit** erstellt mithilfe des Pakets " **scikit-Learn** " ein Tip-Vorhersagemodell.
+ Die gespeicherte Prozedur **traintipvorhertionmodelrxpy** erstellt mithilfe des **revoscalepy** -Pakets ein Tip-Vorhersagemodell.

Jede gespeicherte Prozedur verwendet die Eingabedaten, die Sie zum Erstellen und Trainieren eines logistischen Regressionsmodells bereitstellen. Der gesamte Python-Code wird in der gespeicherten System Prozedur " [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)" verpackt.

Um das erneute Trainieren des Modells für neue Daten zu vereinfachen, wrappen Sie den sp_execute_exernal_script-Befehl in einer anderen gespeicherten Prozedur, und übergeben Sie die neuen Trainingsdaten als Parameter. In diesem Abschnitt werden Sie durch diesen Prozess geführt.

### <a name="pytrainscikit"></a>PyTrainScikit

1.  Öffnen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Sie in ein neues **Abfrage** Fenster, und führen Sie die folgende Anweisung aus, um die gespeicherte Prozedur **pytrainscikit**zu erstellen.  Die gespeicherte Prozedur enthält eine Definition der Eingabedaten, sodass Sie keine Eingabe Abfrage bereitstellen müssen.

    ```sql
    DROP PROCEDURE IF EXISTS PyTrainScikit;
    GO

    CREATE PROCEDURE [dbo].[PyTrainScikit] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    from sklearn.linear_model import LogisticRegression
    
    ##Create SciKit-Learn logistic regression model
    X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
    y = numpy.ravel(InputDataSet[["tipped"]])
    
    SKLalgo = LogisticRegression()
    logitObj = SKLalgo.fit(X, y)
    
    ##Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    GO
    ```

2. Führen Sie die folgenden SQL-Anweisungen aus, um das trainierte Modell\_in die Tabelle NYC taxi_models einzufügen.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Die Verarbeitung der Daten und die Anpassung des Modells kann einige Minuten in Anspruch nehmen. Nachrichten, die an den **stdout** -Stream von python weitergeleitet werden,  werden im Fenster [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Meldungen von angezeigt. Zum Beispiel:

    *Stdout-Meldung (en) aus dem externen Skript:* 
  *c:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Öffnen Sie die *Tabelle\_NYC taxi_models*. Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte _model_enthält.

    *SciKit_model* *0x800363736b6c6561726e2e6c696e6561....*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

Diese gespeicherte Prozedur verwendet das neue **revoscalepy** -Paket, bei dem es sich um ein neues Paket für python handelt. Sie enthält Objekte, Transformationen und Algorithmen, die denen für das **revoscaler** -Paket der R-Sprache ähneln. 

Mithilfe von **revoscalepy**können Sie remotecomputekontexte erstellen, Daten zwischen computekontexten verschieben, Daten transformieren und Vorhersagemodelle mithilfe beliebter Algorithmen (z. b. logistische und lineare Regression, Entscheidungsbäume usw.) trainieren. Weitere Informationen finden Sie unter [revoscalepy-Modul in SQL Server](../python/ref-py-revoscalepy.md) -und [revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

1. Öffnen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Sie in ein neues **Abfrage** Fenster, und führen Sie die folgende Anweisung aus, um die gespeicherte Prozedur " _traintipvorhertionmodelrxpy_" zu erstellen.  Da die gespeicherte Prozedur bereits eine Definition der Eingabedaten enthält, ist es nicht erforderlich, eine Eingabe Abfrage bereitzustellen.

    ```sql
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    from revoscalepy.functions.RxLogit import rx_logit
    
    ## Create a logistic regression model using rx_logit function from revoscalepy package
    logitObj = rx_logit("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    GO
    ```

    Diese gespeicherte Prozedur führt die folgenden Schritte im Rahmen des Modell Trainings aus:

    - Die SELECT-Abfrage wendet die benutzerdefinierte Skalarfunktion _fncalculatedistance_ an, um die direkte Entfernung zwischen den Pick-up-und Dropdown-Speicherorten zu berechnen. Die Ergebnisse der Abfrage werden in der standardmäßigen python-Eingabevariablen, `InputDataset`, gespeichert.
    - Die _binäre Variable wird_ als Bezeichnungs- *oder Ergebnis* Spalte verwendet, und das Modell ist mit den folgenden Merkmals Spalten geeignet: _passenger_count_, _trip_distance_, _trip_time_in_secs_und _direct_distance_.
    - Das trainierte Modell wird serialisiert und in der python-Variablen `logitObj`gespeichert. Durch Hinzufügen der T-SQL-Schlüsselwort Ausgabe können Sie die Variable als Ausgabe der gespeicherten Prozedur hinzufügen. Im nächsten Schritt wird diese Variable verwendet, um den binären Code des Modells in eine Datenbanktabelle _nyc_taxi_models_einzufügen. Dieser Mechanismus vereinfacht das Speichern und wieder verwenden von Modellen.

2. Führen Sie die gespeicherte Prozedur wie folgt aus, um das trainierte **revoscalepy** -Modell in die *nyc_taxi_models*-Tabelle einzufügen.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Die Verarbeitung der Daten und die Anpassung des Modells kann einige Zeit in Anspruch nehmen. Nachrichten, die an den **stdout** -Stream von python weitergeleitet werden,  werden im Fenster [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Meldungen von angezeigt. Zum Beispiel:

    *Stdout-Meldung (en) aus dem externen Skript:* 
  *c:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Öffnen Sie die Tabelle *nyc_taxi_models*. Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte _model_enthält.

    *revoscalepy_model* *0x8003637265766, f.* ...

Im nächsten Schritt verwenden Sie die trainierten Modelle, um Vorhersagen zu erstellen.

## <a name="next-step"></a>Nächster Schritt

[Ausführen von Vorhersagen mithilfe von python Embedded in einer gespeicherten Prozedur](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Vorheriger Schritt

[Erstellen von Datenfunktionen mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
