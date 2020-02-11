---
title: Erstellen von partitionsbasierten Modellen in R
description: Erfahren Sie, wie Sie partitionierte Daten modellieren, trainieren und verwenden, die beim Verwenden der partitionsbasierten Modellierungsfunktionen von SQL Server-Machine Learning dynamisch erstellt werden.
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: tutorial
ms.author: davidph
author: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ee5d6cbf9b1d5430e431cf04fb3b86ae7fb5743b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "73726229"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>Tutorial: Erstellen von partitionsbasierten Modellen in SQL Server mit R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Die partitionsbasierte Modellierung in SQL Server 2019 beschreibt die Möglichkeit, Modelle über partitionierte Daten zu erstellen und zu trainieren. Bei geschichteten Daten, die auf natürliche Weise in ein jeweiliges Klassifizierungsschema segmentiert werden, z. B. geografische Regionen, Datum und Uhrzeit, Alter oder Geschlecht, können Sie ein Skript für das gesamte Dataset ausführen, das Partitionen, die nach all diesen Vorgängen intakt bleiben, modellieren, trainieren und bewerten kann. 

Die partitionsbasierte Modellierung wird mithilfe zwei neuer Parameter in [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) aktiviert:

+ Der Parameter **input_data_1_partition_by_columns**, der eine Spalte angibt, nach der partitioniert werden soll.
+ Der Parameter **input_data_1_order_by_columns**, der angibt, nach welchen Spalten sortiert werden soll. 

In diesem Tutorial erlernen Sie die partitionsbasierte Modellierung anhand der bekannten NYC-Taxibeispieldaten und mithilfe eines R-Skripts. Die Partitionsspalte für dieses Beispiel ist die Zahlungsmethode.

> [!div class="checklist"]
> * Die Partitionen basieren auf Zahlungsarten (5).
> * Erstellen und trainieren Sie Modelle für jede Partition, und speichern Sie die Objekte in der Datenbank.
> * Sagen Sie mithilfe von Beispieldaten, die für diesen Zweck vorgesehen sind, die Wahrscheinlichkeit von Trinkgeldern für jedes Partitionsmodell hervor.

## <a name="prerequisites"></a>Voraussetzungen
 
Für dieses Tutorial benötigen Sie Folgendes:

+ Ausreichend Systemressourcen. Das Dataset ist groß, und die Trainingsvorgänge sind sehr ressourcenintensiv. Verwenden Sie nach Möglichkeit ein System mit mindestens 8 GB RAM. Alternativ können Sie kleinere Datasets verwenden, um Ressourceneinschränkungen zu umgehen. Anweisungen zum Reduzieren des Datasets sind in diesem Artikel enthalten. 

+ Ein Tool zum Ausführen von T-SQL-Abfragen, z. B. [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

+ Die Beispieldatei [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), die Sie auf Ihre lokale Datenbank-Engine-Instanz [herunterladen und dort wiederherstellen](demo-data-nyctaxi-in-sql.md) können. Die Dateigröße beträgt ungefähr 90 MB.

+ eine Datenbank-Engine-Instanz in SQL Server 2019 mit Machine Learning Services und R-Integration

Überprüfen Sie Ihre Version, indem Sie **`SELECT @@Version`** in einem Abfragetool als T-SQL-Abfrage ausführen.

Überprüfen Sie die Verfügbarkeit von R-Paketen, indem Sie wie folgt eine gut formatierte Liste aller derzeit in Ihrer Datenbank-Engine-Instanz installierten R-Pakete zurückgeben:

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

## <a name="connect-to-the-database"></a>Herstellen der Verbindung mit der Datenbank

Starten Sie Management Studio, und stellen Sie eine Verbindung mit der Datenbank-Engine-Instanz her. Vergewissern Sie sich im Objekt-Explorer, dass die [NYCTaxi_Sample-Datenbank](demo-data-nyctaxi-in-sql.md) vorhanden ist. 

## <a name="create-calculatedistance"></a>Erstellen der CalculateDistance-Funktion

Die Beispieldatenbank enthält eine Skalarfunktion zum Berechnen von Entfernungen, jedoch funktioniert die gespeicherte Prozedur mit einer Tabellenwertfunktion besser. Führen Sie das folgende Skript aus, um die **CalculateDistance**-Funktion zu erstellen, die später im [Trainingsschritt](#training-step) verwendet wird.

Überprüfen Sie unter „\Programmability\Functions\Table-valued Functions“ in der Datenbank **NYCTaxi_Sample** im Objekt-Explorer, ob die Funktion erstellt wurde.

```sql
USE NYCTaxi_sample
GO

SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE FUNCTION [dbo].[CalculateDistance] (
    @Lat1 FLOAT
    ,@Long1 FLOAT
    ,@Lat2 FLOAT
    ,@Long2 FLOAT
    )
    -- User-defined function calculates the direct distance between two geographical coordinates.
RETURNS TABLE
AS
RETURN

SELECT COALESCE(3958.75 * ATAN(SQRT(1 - POWER(t.distance, 2)) / nullif(t.distance, 0)), 0) AS direct_distance
FROM (
    VALUES (CAST((SIN(@Lat1 / 57.2958) * SIN(@Lat2 / 57.2958)) + (COS(@Lat1 / 57.2958) * COS(@Lat2 / 57.2958) * COS((@Long2 / 57.2958) - (@Long1 / 57.2958))) AS DECIMAL(28, 10)))
    ) AS t(distance)
GO
 ```

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>Definieren einer Prozedur zum Erstellen und Trainieren von Modellen pro Partition

In diesem Tutorial umschließen Sie ein R-Skript in einer gespeicherten Prozedur. In diesem Schritt erstellen Sie eine gespeicherte Prozedur, die R verwendet, um ein Eingabedataset zu erstellen, ein Klassifizierungsmodell zum Vorhersagen von Trinkgeldern zu erstellen und das Modell anschließend in der Datenbank zu speichern.

Unter den von diesem Skript verwendeten Parametereingaben finden Sie die Parameter **input_data_1_partition_by_columns** und **input_data_1_order_by_columns**. Denken Sie daran, dass diese Parameter den Mechanismus darstellen, nach dem die partitionierte Modellierung erfolgt. Die Parameter werden als Eingaben an [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) übergeben, um Partitionen mit dem externen Skript zu verarbeiten, das für jede Partition einmal ausgeführt wird. 

[Verwenden Sie die Parallelität](#parallel) für diese gespeicherte Prozedur, um eine schnellere Ausführung zu erzielen.

Nachdem Sie dieses Skript ausgeführt haben, sollten Sie **train_rxLogIt_per_partition** unter „\Programmability\Stored Procedures“ in der Datenbank **NYCTaxi_Sample** im Objekt-Explorer finden können. Außerdem sollte eine neue Tabelle vorliegen, die zum Speichern von Modellen verwendet wird: **dbo.nyctaxi_models**.

```sql
USE NYCTaxi_Sample
GO

CREATE
    OR

ALTER PROCEDURE [dbo].[train_rxLogIt_per_partition] (@input_query NVARCHAR(max))
AS
BEGIN
    DECLARE @start DATETIME2 = SYSDATETIME()
        ,@model_generation_duration FLOAT
        ,@model VARBINARY(max)
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name();

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    # Make sure InputDataSet is not empty. In parallel mode, if one thread gets zero data, an error occurs
    if (nrow(InputDataSet) > 0) {
    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    
    # build classification model to predict a tip outcome
    duration <- system.time(logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet))[3];

    # First, serialize a model to and put it into a database table
    modelbin <- as.raw(serialize(logitObj, NULL));

    # Create the data source. To reduce data size, add rowsPerRead=500000 to cut the dataset by half.
    ds <- RxOdbcData(table="ml_models", connectionString=connStr);

    # Store the model in the database
    model_name <- paste0("nyctaxi.", InputDataSet[1,]$payment_type);
    
    rxWriteObject(ds, model_name, modelbin, version = "v1",
    keyName = "model_name", valueName = "model_object", versionName = "model_version", overwrite = TRUE, serialize = FALSE);
    } 
    
    '
        ,@input_data_1 = @input_query
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@input_data_1_order_by_columns = N'passenger_count'
        ,@parallel = 1
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS NONE
END;
GO
```

<a name="parallel"></a>

### <a name="parallel-execution"></a>Parallele Ausführung

Beachten Sie, dass die [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)-Eingaben `@parallel=1` enthalten, um die Parallelverarbeitung zu aktivieren. Im Gegensatz zu früheren Releases erhält der Abfrageoptimierer durch Festlegen von `@parallel=1` in SQL Server 2019 einen effektiveren Hinweis, wodurch die parallele Ausführung wahrscheinlicher wird.

Der Abfrageoptimierer wird bei Tabellen mit mehr als 256 Zeilen standardmäßig mit `@parallel=1` betrieben. Sie können dies jedoch explizit behandeln, indem Sie `@parallel=1` wie in diesem Skript festlegen.

> [!Tip]
> Für Trainingsworkloads können Sie `@parallel` mit einem beliebigen arbiträren Trainingsskript verwenden, sogar solche, die nicht von Microsoft stammende RX-Algorithmen verwenden In der Regel bieten nur RevoScaleR-Algorithmen (mit dem RX-Präfix) Parallelität in Trainingsszenarios in SQL Server. Mit dem neuen Parameter können Sie jedoch ein Skript parallelisieren, das Funktionen aufruft, einschließlich quelloffene R-Funktionen, die nicht speziell mit dieser Funktion entwickelt wurden. Das funktioniert, weil Partitionen eine Affinität für bestimmte Threads aufweisen. Alle in einem Skript aufgerufenen Vorgänge werden also je nach Partition auf dem jeweiligen Thread (`thread.`<a name="training-step"></a>) ausgeführt.

## <a name="run-the-procedure-and-train-the-model"></a>Ausführen der Prozedur und Trainieren des Modells

In diesem Abschnitt trainiert das Skript das Modell, dass Sie im vorherigen Schritt erstellt und gespeichert haben. In den folgenden Beispielen werden zwei Vorgehensweisen zum Trainieren Ihres Modells veranschaulicht: mithilfe des gesamten oder eines Teils des Datasets. 

Dieser Schritt wird eine Weile dauern. Das Training ist rechenintensiv und benötigt einige Minuten. Wenn die Systemressourcen, insbesondere der Arbeitsspeicher, nicht zum Laden ausreichen, sollten Sie eine Teilmenge der Daten verwenden. Im zweiten Beispiel wird die Syntax bereitstellt.

```sql
--Example 1: train on entire dataset
EXEC train_rxLogIt_per_partition N'
SELECT payment_type, tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

```sql
--Example 2: Train on 20 percent of the dataset to expedite processing.
EXEC train_rxLogIt_per_partition N'
  SELECT tipped, payment_type, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance
  FROM dbo.nyctaxi_sample TABLESAMPLE (20 PERCENT) REPEATABLE (98074)
  CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d
';
GO
```

> [!NOTE]
> Wenn Sie andere Workloads ausführen, können Sie `OPTION(MAXDOP 2)` an die SELECT-Anweisung anfügen, wenn Sie die Abfrageverarbeitung auf nur 2 Kerne begrenzen möchten.

## <a name="check-results"></a>Überprüfen der Ergebnisse

Das Ergebnis in der Modelltabelle sollte aus fünf verschiedenen Modellen bestehen, die auf den fünf Partitionen basieren, die nach den fünf Zahlungsmethoden segmentiert wurden. Die Modelle befinden sich in der Datenquelle **ml_models**.

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>Definieren einer Prozedur zum Vorhersagen von Ergebnissen

Sie können dieselben Parameter für die Bewertung verwenden. Das folgende Beispiel enthält ein R-Skript, das die Bewertung mit dem richtigen Modell für die Partition durchführt, das aktuell verarbeitet wird.

Erstellen Sie wie zuvor eine gespeicherte Prozedur, um Ihren R-Code zu umschließen.

```sql
USE NYCTaxi_Sample
GO

-- Stored procedure that scores per partition. 
-- Depending on the partition being processed, a model specific to that partition will be used
CREATE
    OR

ALTER PROCEDURE [dbo].[predict_per_partition]
AS
BEGIN
    DECLARE @predict_duration FLOAT
        ,@instance_name NVARCHAR(100) = @@SERVERNAME
        ,@database_name NVARCHAR(128) = db_name()
        ,@input_query NVARCHAR(max);

    SET @input_query = 'SELECT tipped, passenger_count, trip_time_in_secs, trip_distance, d.direct_distance, payment_type
                          FROM dbo.nyctaxi_sample TABLESAMPLE (1 PERCENT) REPEATABLE (98074)
                          CROSS APPLY [CalculateDistance](pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as d'

    EXEC sp_execute_external_script @language = N'R'
        ,@script = 
        N'
    
    if (nrow(InputDataSet) > 0) {

    #Get the partition that is currently being processed
    current_partition <- InputDataSet[1,]$payment_type;

    #Create the SQL query to select the right model
    query_getModel <- paste0("select model_object from ml_models where model_name = ", "''", "nyctaxi.",InputDataSet[1,]$payment_type,"''", ";")
    

    # Define the connection string
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
        
    #Define data source to use for getting the model
    ds <- RxOdbcData(sqlQuery = query_getModel, connectionString = connStr)

    # Load the model
    modelbin <- rxReadObject(ds, deserialize = FALSE)
    # unserialize model
    logitObj <- unserialize(modelbin);

    # predict tipped or not based on model
    predictions <- rxPredict(logitObj, data = InputDataSet, overwrite = TRUE, type = "response", writeModelVars = TRUE
        , extraVarsToWrite = c("payment_type"));        
    OutputDataSet <- predictions
    
    } else {
        OutputDataSet <- data.frame(integer(), InputDataSet[,]);        
    }
    '
        ,@input_data_1 = @input_query
        ,@parallel = 1
        ,@input_data_1_partition_by_columns = N'payment_type'
        ,@params = N'@instance_name nvarchar(100), @database_name nvarchar(128)'
        ,@instance_name = @instance_name
        ,@database_name = @database_name
    WITH RESULT SETS((
                tipped_Pred INT
                ,payment_type VARCHAR(5)
                ,tipped INT
                ,passenger_count INT
                ,trip_distance FLOAT
                ,trip_time_in_secs INT
                ,direct_distance FLOAT
                ));
END;
GO
```

## <a name="create-a-table-to-store-predictions"></a>Erstellen einer Tabelle zum Speichern von Vorhersagen

```sql
CREATE TABLE prediction_results (
    tipped_Pred INT
    ,payment_type VARCHAR(5)
    ,tipped INT
    ,passenger_count INT
    ,trip_distance FLOAT
    ,trip_time_in_secs INT
    ,direct_distance FLOAT
    );

TRUNCATE TABLE prediction_results
GO
```

## <a name="run-the-procedure-and-save-predictions"></a>Ausführen der Prozedur und Speichern von Vorhersagen

```sql
INSERT INTO prediction_results (
    tipped_Pred
    ,payment_type
    ,tipped
    ,passenger_count
    ,trip_distance
    ,trip_time_in_secs
    ,direct_distance
    )
EXECUTE [predict_per_partition]
GO
```

## <a name="view-predictions"></a>Anzeigen von Vorhersagen

Da die Vorhersagen gespeichert werden, können Sie eine einfache Abfrage ausführen, um ein Resultset zurückzugeben.

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) verwendet, um Vorgänge für partitionierte Daten zu durchlaufen. Im folgenden Tutorial erhalten Sie ausführlichere Informationen zum Aufrufen externer Skripts in gespeicherten Prozeduren und Verwenden von RevoScaleR-Funktionen.

> [!div class="nextstepaction"]
> [Exemplarische Vorgehensweise für R und SQL Server](walkthrough-data-science-end-to-end-walkthrough.md)

