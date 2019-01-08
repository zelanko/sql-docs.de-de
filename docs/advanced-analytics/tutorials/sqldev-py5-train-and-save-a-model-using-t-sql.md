---
title: Trainieren Sie und speichern Sie ein Python-Modell mithilfe von T-SQL – SQL Server-Machine Learning
description: Python-Tutorial zeigt, wie zum Trainieren und speichern ein Modell mithilfe von Transact-SQL in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a0991f43ed7446cc9b86325d4f536a0787b8dcc1
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645171"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>Trainieren und Speichern eines Python-Modells mit T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials, [In-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt erfahren Sie, wie zum Trainieren eines Machine Learning-Modells mithilfe der Python-Pakete **Scikit-erfahren Sie,** und **Revoscalepy**. Dieser Python-Bibliotheken sind in SQL Server Machine Learning Services bereits installiert.

Sie laden Sie die Module, und rufen die erforderlichen Funktionen zum Erstellen und Trainieren des Modells mithilfe einer gespeicherten SQL Server-Prozedur. Im Modell müssen die Data-Features, die Sie in den früheren Lektionen konzipiert. Speichern Sie abschließend das trainierte Modell in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle.
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Teilen Sie die Beispieldaten in Trainings- und Testsätze auf

1. Erstellen Sie eine gespeicherte Prozedur namens **PyTrainTestSplit** , die Daten in der Tabelle Nyctaxi_sample in zwei Teile unterteilen: Nyctaxi_sample_training und Nyctaxi_sample_testing. 

    Diese gespeicherte Prozedur sollte bereits für Sie erstellt werden, aber Sie können den folgenden Code zum Erstellen ausführen:

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

2. Um Ihre Daten mit einer benutzerdefinierten unterteilten Teilen kann, führen Sie die gespeicherte Prozedur, und geben Sie eine ganze Zahl, die den Prozentsatz der Daten, die in das Trainingsdataset darstellt. Die folgende Anweisung würde z. B. 60 % der Daten in das Trainingsdataset zuordnen.

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Erstellen eines logistischen Regressionsmodells

Nachdem die Daten vorbereitet wurde, können Sie es zum Trainieren eines Modells verwenden. Dazu rufen eine gespeicherte Prozedur, die einige Python-Code, der als ausführt Eingabe Schulung-Datentabelle. In diesem Tutorial erstellen Sie zwei Modelle, die beide Modelle mit binärer Klassifizierung:

+ Die gespeicherte Prozedur **PyTrainScikit** erstellt ein Modell mit Tip Vorhersage der **Scikit-erfahren Sie,** Paket.
+ Die gespeicherte Prozedur **TrainTipPredictionModelRxPy** erstellt ein Modell mit Tip Vorhersage der **Revoscalepy** Paket.

Jede gespeicherte Prozedur verwendet die eingegebenen Daten Sie zum Erstellen und Trainieren Sie ein Logistisches Regressionsmodell bereitstellen. Alle Python-Code wird die gespeicherte Systemprozedur, umschlossen [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Zum erneuten Trainieren des Modells auf neue Daten zu erleichtern, stellen Sie den Aufruf von Sp_execute_exernal_script in einer anderen gespeicherten Prozedur umschließen, und in den neuen Trainingsdaten als Parameter übergeben. Dieser Abschnitt führt Sie durch diesen Prozess.

### <a name="pytrainscikit"></a>PyTrainScikit

1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], öffnen Sie ein neues **Abfrage** Fenster, und führen Sie die folgende Anweisung zum Erstellen der gespeicherten Prozedur **PyTrainScikit**.  Die gespeicherte Prozedur enthält eine Definition der Eingabedaten, sodass Sie keine Eingabeabfrage bereitstellen müssen.

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

2. Führen Sie die folgende SQL-Anweisungen fügen Sie das trainierte Modell in Tabelle nyc\_Taxi_models.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Die Verarbeitung der Daten und Anpassung des Modells können ein paar Minuten dauern. Nachrichten, die auf Python weitergeleitet werden würden **"stdout"** Stream werden angezeigt, der **Nachrichten** Fenster [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Zum Beispiel:

    *Stdout-Meldung(en) aus dem externen Skript:*
  *c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Öffnen Sie die Tabelle *nyc\_Taxi_models*. Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte _model_enthält.

    *SciKit_model* *0x800363736B6C6561726E2E6C696E6561...*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

Diese gespeicherte Prozedur verwendet die neue **Revoscalepy** -Paket, das ist ein neues Paket für Python. Sie enthält Objekte, Transformation und Algorithmen wie für der Sprache R **RevoScaleR** Paket. 

Mithilfe von **Revoscalepy**, können Sie remotecomputekontexte erstellen, Verschieben von Daten zwischen compute-Kontexten, Transformieren von Daten und Trainieren Vorhersagemodelle mit gängigen Algorithmen wie z. B. logistische und lineare Regression, Entscheidungsstrukturen, und Weitere. Weitere Informationen finden Sie unter [Revoscalepy-Modul in SQL Server](../python/ref-py-revoscalepy.md) und [Revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

1. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], öffnen Sie ein neues **Abfrage** Fenster, und führen Sie die folgende Anweisung zum Erstellen der gespeicherten Prozedur _TrainTipPredictionModelRxPy_.  Da die gespeicherte Prozedur bereits eine Definition der Eingabedaten enthält, müssen Sie keine Eingabeabfrage bereitstellen.

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

    Diese gespeicherte Prozedur führt die folgenden Schritte als Teil des modelltrainings aus:

    - Die SELECT-Abfrage angewendet wird, die benutzerdefinierte Skalarfunktion _FnCalculateDistance_ , der Berechnung der direkten Entfernung zwischen den Abhol- und Zielorten. Die Ergebnisse der Abfrage werden in der standardmäßigen Python input-Variable gespeichert `InputDataset`.
    - Die binäre Variable _"tipped"_ dient als die *Bezeichnung* oder der Ergebnisspalte angezeigt, und das Modell wird mithilfe folgender Funktionsspalten angepasst: _Passenger_count_, _Trip_ Abstand_, _Trip_time_in_secs_, und _Direct_distance_.
    - Das trainierte Modell wird serialisiert und in der Python-Variable gespeicherte `logitObj`. Durch das T-SQL-Schlüsselwort OUTPUT hinzufügen, können Sie die Variable als Ausgabe der gespeicherten Prozedur hinzufügen. Im nächsten Schritt-diese Variable wird verwendet, um den binären Code des Modells in eine Datenbanktabelle einfügen _Nyc_taxi_models_. Dieser Mechanismus ermöglicht es, die einfach, zu speichern und Wiederverwenden von Modellen.

2. Führen Sie die gespeicherte Prozedur wie folgt, um das trainierte einfügen **Revoscalepy** Modell in die Tabelle *Nyc_taxi_models*.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Die Verarbeitung der Daten und Anpassung des Modells können eine Weile dauern. Nachrichten, die auf Python weitergeleitet werden würden **"stdout"** Stream werden angezeigt, der **Nachrichten** Fenster [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Zum Beispiel:

    *Stdout-Meldung(en) aus dem externen Skript:*
  *c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Öffnen Sie die Tabelle *nyc_taxi_models*. Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte _model_enthält.

    *Revoscalepy_model* *0x8003637265766F7363616c...*

Im nächsten Schritt verwenden Sie die trainierten Modelle zum Erstellen von Vorhersagen.

## <a name="next-step"></a>Nächster Schritt

[Führen Sie Vorhersagen mithilfe von Python in einer gespeicherten Prozedur eingebettet](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Vorherigen Schritt

[Erstellen von Datenfunktionen mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
