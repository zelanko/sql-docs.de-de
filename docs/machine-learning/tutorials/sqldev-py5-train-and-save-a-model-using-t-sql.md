---
title: 'Python und T-SQL: Trainieren des Modells'
description: Python-Tutorial zum Trainieren und Speichern eines Modells in SQL Server mithilfe von Transact-SQL
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8d7bc2e2d46cb5b3f0c9619e59ab448e95bf4db2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775332"
---
# <a name="train-and-save-a-python-model-using-t-sql"></a>Trainieren und Speichern eines Python-Modells mit T-SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Dieser Artikel ist Teil des Tutorials [Python-Datenanalysen für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt lernen Sie, wie Sie ein Machine Learning-Modell mithilfe der Python-Pakete **scikit-learn** und **revoscalepy** trainieren können. Diese Python-Bibliotheken wurden mit SQL Server Machine Learning Services bereits installiert.

Sie laden die Module und rufen die erforderlichen Funktionen auf, um das Modell mithilfe einer gespeicherten SQL Server-Prozedur zu erstellen und zu trainieren. Für das Modell sind die Datenfeatures erforderlich, die Sie in früheren Lektionen entwickelt haben. Zum Schluss speichern Sie das trainierte Modell in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle.
 

## <a name="split-the-sample-data-into-training-and-testing-sets"></a>Unterteilen der Beispieldaten in Trainings- und Testdatensätze

1. Erstellen Sie eine gespeicherte Prozedur mit dem Namen **PyTrainTestSplit**, um die Daten in der Tabelle nyctaxi_sample in zwei Teile aufzuteilen: nyctaxi_sample_training und nyctaxi_sample_testing. 

    Diese gespeicherte Prozedur sollte bereits für Sie erstellt worden sein. Alternativ können Sie folgenden Code ausführen, um sie zu erstellen:

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

2. Sie können die Daten benutzerdefiniert aufteilen, indem Sie die gespeicherte Prozedur ausführen und einen Integer eingeben, der für den Prozentsatz der Daten steht, die dem Trainingsdatensatz zugeordnet werden sollen. Folgende Anweisung würde beispielsweise 60 % der Daten dem Trainingsdatensatz zuweisen.

    ```sql
    EXEC PyTrainTestSplit 60
    GO
    ```

## <a name="build-a-logistic-regression-model"></a>Erstellen eines logistischen Regressionsmodells

Sobald die Daten vorbereitet sind, können Sie sie für das Training des Modells verwenden. Hierfür können Sie eine gespeicherte Prozedur aufrufen, die Python-Code ausführt und die Tabelle mit den Trainingsdaten als Eingabe akzeptiert. Für dieses Tutorial erstellen Sie zwei Modelle, bei denen es sich um Binärklassifizierungsmodelle handelt:

+ Die gespeicherte Prozedur **PyTrainScikit** erstellt mithilfe des Pakets **scikit-learn** ein Vorhersagemodell für Trinkgeld.
+ Die gespeicherte Prozedur **TrainTipPredictionModelRxPy** erstellt mithilfe des Pakets **revoscalepy** ein Vorhersagemodell für Trinkgeld.

Jede gespeicherte Prozedur verwendet die angegebenen Eingabedaten, um ein logistisches Regressionsmodell zu erstellen und zu trainieren. Der gesamte Python-Code ist in der gespeicherten Systemprozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) umschlossen.

Sie können das wiederholte Trainieren des Modells mit neuen Daten vereinfachen, indem Sie den Aufruf von sp_execute_external_script in eine andere gespeicherte Prozedur umschließen und die neuen Trainingsdaten als Parameter übergeben. Dieser Vorgang wird im folgenden Abschnitt beschrieben.

### <a name="pytrainscikit"></a>PyTrainScikit

1.  Öffnen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ein neues **Abfragefenster**, und führen Sie die folgende Anweisung aus, um die gespeicherte Prozedur **PyTrainScikit** zu erstellen.  Die gespeicherte Prozedur enthält eine Definition der Eingabedaten. Sie müssen also eine Eingabeabfrage bereitstellen.

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

2. Führen Sie folgende SQL-Anweisungen aus, um das trainierte Modell in die Tabelle nyc\_taxi_models einzufügen.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC PyTrainScikit @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('SciKit_model', @model);
    ```

    Die Verarbeitung der Daten und die Anpassung des Modells kann einige Minuten dauern. Nachrichten, die an den **stdout**-Stream von Python weitergeleitet werden würden, werden im Fenster **Meldungen** von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]angezeigt. Beispiel:

    *STDOUT-Meldungen von einem externen Skript:* 
  *C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Öffnen Sie die Tabelle *nyc\_taxi_models*. Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte _model_enthält.

    *SciKit_model* *0x800363736B6C6561726E2E6C696E6561....*

### <a name="traintippredictionmodelrxpy"></a>TrainTipPredictionModelRxPy

Diese gespeicherte Prozedur verwendet das neue Paket **revoscalepy** für Python. Es enthält Objekte, Transformationen und Algorithmen, die denen für das R-Paket **RevoScaleR** ähneln. 

Wenn Sie **revoscalepy** verwenden, können Sie Remotecomputekontexte erstellen, Daten zwischen Computekontexten verschieben, Daten transformieren und Vorhersagemodelle mithilfe beliebter Algorithmen wie logistische und lineare Regressionen oder Entscheidungsstrukturen trainieren. Weitere Informationen finden Sie unter [revoscalepy (Python-Modul in SQL Server)](../python/ref-py-revoscalepy.md) und [revoscalepy-Funktionsreferenz](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

1. Öffnen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ein neues **Abfragefenster**, und führen Sie die folgende Anweisung aus, um die gespeicherte Prozedur _TrainTipPredictionModel_ zu erstellen.  Da die gespeicherte Prozedur schon eine Definition der Eingabedaten enthält, müssen Sie keine Eingabeabfrage bereitstellen.

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

    Diese gespeicherte Prozedur führt folgende Schritte als Teil des Modelltrainings aus:

    - Die SELECT-Abfrage wendet die benutzerdefinierte Skalarfunktion _fnCalculateDistance_ zum Berechnen der direkten Entfernung zwischen den Abhol- und Zielorten an. Die Ergebnisse der Abfrage werden in der Standardeingabevariable von Python, `InputDataset`, gespeichert.
    - Die binäre Variable _tipped_ dient als die Spalte *label* oder „outcome“, und das Modell wird mithilfe folgender Funktionsspalten angepasst: _passenger_count_, _trip_distance_, _trip_time_in_secs_ und _direct_distance_.
    - Das trainierte Modell wird serialisiert und in der Python-Variable `logitObj` gespeichert. Sie können die Variable als Ausgabe der gespeicherten Prozedur hinzufügen, indem Sie das T-SQL-Schlüsselwort OUTPUT verwenden. Im nächsten Schritt wird die Variable verwendet, um den Binärcode des Modells in die Datenbanktabelle _nyc_taxi_models_ einzufügen. Durch dieses Verfahren können Modelle einfach gespeichert und wiederverwendet werden.

2. Führen Sie die gespeicherte Prozedur folgendermaßen aus, um das trainierte **revoscalepy**-Modell in die Tabelle *nyc_taxi_models* einzufügen.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC TrainTipPredictionModelRxPy @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('revoscalepy_model', @model);
    ```

    Die Verarbeitung der Daten und die Anpassung des Modells können eine Weile dauern. Nachrichten, die an den **stdout**-Stream von Python weitergeleitet werden würden, werden im Fenster **Meldungen** von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]angezeigt. Beispiel:

    *STDOUT-Meldungen von einem externen Skript:* 
  *C:\Programme\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\revoscalepy*

3. Öffnen Sie die Tabelle *nyc_taxi_models*. Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte _model_enthält.

    *revoscalepy_model* *0x8003637265766F7363616c....*

Im nächsten Schritt verwenden Sie die trainierten Modelle zum Erstellen von Vorhersagen.

## <a name="next-step"></a>Nächster Schritt

[Ausführen von Vorhersagen mithilfe eines eingebetteten Python-Skripts in einer gespeicherten Prozedur](sqldev-py6-operationalize-the-model.md)

## <a name="previous-step"></a>Vorheriger Schritt

[Erstellen von Datenfunktionen mit T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)
