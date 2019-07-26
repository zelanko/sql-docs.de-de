---
title: Tutorial zum Erstellen, trainieren und bewerten von Partitions basierten Modellen in R
description: Erfahren Sie, wie Sie partitionierte Daten modellieren, trainieren und verwenden, die dynamisch erstellt werden, wenn Sie die Partitions basierten Modellierungsfunktionen von SQL Server Machine Learning verwenden.
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/27/2019
ms.topic: tutorial
ms.author: davidph
author: dphansen
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 024ddc72ae2b0a2c443546148a66d0fa85060cb6
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469199"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>Tutorial: Erstellen von Partitions basierten Modellen in R auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In SQL Server 2019 ist die Partitions basierte Modellierung die Möglichkeit, Modelle über partitionierte Daten zu erstellen und zu trainieren. Für stratifilierte Daten, die auf natürliche Weise in ein bestimmtes Klassifizierungsschema (z. b. geografische Regionen, Datum und Uhrzeit, Alter oder Geschlecht) segmentieren, können Sie das Skript über das gesamte Dataset ausführen, mit der Möglichkeit, Partitionen zu modellieren, zu trainieren und zu bewerten, die intakt bleiben. Alle diese Vorgänge. 

Die Partitions basierte Modellierung wird durch zwei neue Parameter auf [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)aktiviert:

+ **input_data_1_partition_by_columns**gibt eine Spalte an, nach der partitioniert werden soll.
+ **input_data_1_order_by_columns** gibt die Spalten an, nach denen sortiert werden soll. 

In diesem Tutorial erfahren Sie mehr über die Partitions basierte Modellierung mithilfe der klassischen Beispiel Daten und des R-Skripts für NYC Taxi. Die Partitions Spalte ist die Zahlungsmethode.

> [!div class="checklist"]
> * Partitionen basieren auf Zahlungs Typen (5).
> * Erstellen und trainieren Sie Modelle für jede Partition, und speichern Sie die Objekte in der Datenbank.
> * Prognostizieren Sie die Wahrscheinlichkeit der Tip-Ergebnisse für jedes Partitions Modell, indem Sie Beispiel Daten verwenden, die für diesen Zweck reserviert sind.

## <a name="prerequisites"></a>Vorraussetzungen
 
Um dieses Tutorial abzuschließen, benötigen Sie Folgendes:

+ Ausreichend Systemressourcen. Das DataSet ist umfangreich, und die Trainings Vorgänge sind ressourcenintensiv. Verwenden Sie nach Möglichkeit ein System mit mindestens 8 GB RAM. Alternativ können Sie kleinere Datasets verwenden, um Ressourceneinschränkungen zu umgehen. Anweisungen zum Verringern des Datasets sind Inline. 

+ Ein Tool für die Ausführung von T-SQL-Abfragen, z. b. [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

+ [NYCTaxi_Sample. bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), das Sie [herunterladen und](demo-data-nyctaxi-in-sql.md) in der lokalen Datenbank-Engine-Instanz wiederherstellen können. Die Dateigröße beträgt ungefähr 90 MB.

+ SQL Server 2019 Vorschau der Datenbank-Engine-Instanz mit Machine Learning Services-und R-Integration.

Überprüfen Sie die **`SELECT @@Version`** Version, indem Sie in einem Abfrage Tool als T-SQL-Abfrage ausführen. Die Ausgabe sollte "Microsoft SQL Server 2019 (CTP 2,4)-15,0. x" lauten.

Überprüfen Sie die Verfügbarkeit von r-Paketen, indem Sie eine gut formatierte Liste aller r-Pakete zurückgeben

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

## <a name="connect-to-the-database"></a>Verbindung mit der Datenbank herstellen

Starten Sie Management Studio, und stellen Sie eine Verbindung zur Datenbank-Engine-Instanz Vergewissern Sie sich in Objekt-Explorer, dass die [NYCTaxi_Sample-Datenbank](demo-data-nyctaxi-in-sql.md) vorhanden ist. 

## <a name="create-calculatedistance"></a>Calculatedistance erstellen

Die Demo Datenbank enthält eine Skalarfunktion für die Berechnung der Entfernung, aber unsere gespeicherte Prozedur funktioniert besser mit einer Tabellenwert Funktion. Führen Sie das folgende Skript aus, um die **calculatedistance** -Funktion zu erstellen, die später im [Trainingsschritt](#training-step) verwendet wird.

Um zu bestätigen, dass die Funktion erstellt wurde, überprüfen Sie die Funktionen "\programmability\functions\table-Value" in der **NYCTaxi_Sample** -Datenbank in Objekt-Explorer.

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

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>Definieren eines Verfahrens zum Erstellen und trainieren von pro-Partition-Modellen

In diesem Tutorial wird das R-Skript in einer gespeicherten Prozedur umschlossen. In diesem Schritt erstellen Sie eine gespeicherte Prozedur, die R verwendet, um ein Eingabe DataSet zu erstellen, ein Klassifizierungs Modell zum Vorhersagen von Tip-Ergebnissen zu erstellen und das Modell dann in der Datenbank zu speichern.

Zu den von diesem Skript verwendeten Parameter Eingaben werden **input_data_1_partition_by_columns** und **input_data_1_order_by_columns**angezeigt. Beachten Sie, dass diese Parameter der Mechanismus sind, mit dem die partitionierte Modellierung erfolgt. Die Parameter werden als Eingaben an [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) übermittelt, um Partitionen zu verarbeiten, bei denen das externe Skript einmal für jede Partition ausgeführt wird. 

Verwenden Sie für diese gespeicherte Prozedur [Parallelität](#parallel) für schnellere Zeit bis zum Abschluss.

Nachdem Sie dieses Skript ausgeführt haben, sollten Sie **train_rxLogIt_per_partition** in "\Program ability\gespeicherte Prozeduren" unter der **NYCTaxi_Sample** -Datenbank in Objekt-Explorer sehen. Außerdem sollte eine neue Tabelle zum Speichern von Modellen angezeigt werden: **dbo. nyctaxi_models**.

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

Beachten Sie, dass die [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) -Eingaben  **@parallel= 1**enthalten, die zum Aktivieren der parallelen Verarbeitung verwendet werden. Im Gegensatz zu früheren Versionen bietet das Setting  **@parallel= 1** in SQL Server 2019 einen stärkeren Hinweis für den Abfrageoptimierer, sodass die parallele Ausführung zu einem viel wahrscheinlicheren Ergebnis wird.

Standardmäßig wird der Abfrageoptimierer tendenziell unter  **@parallel= 1** für Tabellen mit mehr als 256 Zeilen ausgeführt. Wenn Sie dies jedoch explizit behandeln können, indem Sie  **@parallel= 1** wie in diesem Skript gezeigt festlegen.

> [!Tip]
> Für Schulungs Arbeitsthreads können Sie mit beliebigen Trainings **@parallel** Skripts verwenden, auch solche, die nicht-Microsoft-RX-Algorithmen verwenden. In der Regel bieten nur revoscaler-Algorithmen (mit dem RX-Präfix) Parallelität in Trainingsszenarien in SQL Server. Mit dem neuen Parameter können Sie jedoch ein Skript parallelisieren, das Funktionen aufruft, einschließlich Open Source-R-Funktionen, die nicht speziell mit dieser Funktion entwickelt wurden. Dies funktioniert, da Partitionen für bestimmte Threads eine Affinität aufweisen, sodass alle in einem Skript aufgerufenen Vorgänge auf Partitions Basis im angegebenen Thread ausgeführt werden.

<a name="training-step"></a>

## <a name="run-the-procedure-and-train-the-model"></a>Führen Sie die Prozedur aus, und trainieren Sie das Modell.

In diesem Abschnitt trainiert das Skript das Modell, das Sie im vorherigen Schritt erstellt und gespeichert haben. In den folgenden Beispielen werden zwei Ansätze zum Trainieren des Modells veranschaulicht: die Verwendung eines gesamten Datasets oder eines partiellen Datensatzes. 

Erwarten Sie, dass dieser Schritt eine Weile dauert. Das Training ist Rechen intensiv und dauert viele Minuten. Wenn die Auslastung der Systemressourcen, insbesondere des Arbeitsspeichers, unzureichend ist, verwenden Sie eine Teilmenge der Daten. Im zweiten Beispiel wird die-Syntax bereitstellt.

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
> Wenn Sie andere Arbeits Auslastungen ausführen, können Sie `OPTION(MAXDOP 2)` an die SELECT-Anweisung anfügen, wenn Sie die Abfrage Verarbeitung auf nur 2 Kerne begrenzen möchten.

## <a name="check-results"></a>Ergebnisse überprüfen

Das Ergebnis in der Tabelle Models sollte fünf verschiedene Modelle sein, basierend auf fünf Partitionen, die von den fünf Zahlungs Typen segmentiert werden. Modelle befinden sich in der **ml_models** -Datenquelle.

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>Definieren einer Prozedur zum Vorhersagen von Ergebnissen

Sie können dieselben Parameter für die Bewertung verwenden. Das folgende Beispiel enthält ein R-Skript, das die Bewertung mit dem richtigen Modell für die Partition durchführt, die derzeit verarbeitet wird.

Erstellen Sie wie zuvor eine gespeicherte Prozedur, um Ihren R-Code zu wrappen.

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

## <a name="view-predictions"></a>Vorhersagen anzeigen

Da die Vorhersagen gespeichert werden, können Sie eine einfache Abfrage ausführen, um ein Resultset zurückzugeben.

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) verwendet, um Vorgänge für partitionierte Daten zu durchlaufen. Weitere Informationen zum Aufrufen externer Skripts in gespeicherten Prozeduren und zum Verwenden von revoscaler-Funktionen finden Sie im folgenden Tutorial.

> [!div class="nextstepaction"]
> [Exemplarische Vorgehensweise für R und SQL Server](walkthrough-data-science-end-to-end-walkthrough.md)

<!--
## Old intro

**(Not for production workloads)**

One of the more common approaches for executing R or Python code on SQL data is providing script as an input parameter to the [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) stored procedure. In this CTP release, SQL Server 2019 adds new parameters to `sp_execute_external_script` to process partitions with the external script executing once for every partition:

| Parameter | Usage |
|-----------|-------|
| **input_data_1_partition_by_columns** | Specifies which columns to partition by. |
| **input_data_1_order_by_columns** | Specifies which columns to order by.  |

Partitions are an organizational mechanism for stratified data that naturally segments into a given classification scheme. Common examples include partitioning by geographic region, by date and time, by age or gender, and so forth. Given the existence of partitioned data, you might want to execute script over the entire data set, with the ability to model, train, and score partitions that remain intact over all these operations. Calling `sp_execute_external_script` with the new parameters allows you to do just that.

You can run this operation in parallel by combining `partition_by` with `@parallel`. If the input query can be parallelized, set `@parallel=1` as part of your arguments to `sp_execute_external_script`. By default, the query optimizer operates under `@parallel=1` on tables having more than 256 rows.

When the scenario is training, one advantage is that any arbitrary training script, even those using non-Microsoft-rx algorithms, can be parallelized by also using the @parallel parameter. Typically, you would have to use RevoScaleR algorithms (with the rx prefix) to obtain parallelism in training scenarios in SQL Server. But with the new parameter, you can parallelize a script that calls functions not specifically engineered with that capability.
-->
