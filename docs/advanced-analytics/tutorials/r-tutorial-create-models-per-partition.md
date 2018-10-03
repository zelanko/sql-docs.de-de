---
title: Tutorial zum Erstellen, Trainieren und Bewerten von Partition basierenden Modellen in R (SQL Server Machine Learning Services) | Microsoft-Dokumentation
description: Informationen Sie zum Modellieren, Trainieren und Verwenden von partitionierten Daten, die dynamisch erstellt wird, wenn Sie die Partition-basierten Modellierung-Funktionen von SQL Server Machine Learning verwenden.
ms.custom: sqlseattle
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2018
ms.topic: tutorial
ms.author: heidist
author: HeidiSteen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3289e9f7493b7e5a6377de3491bd5726d557fdf7
ms.sourcegitcommit: 615f8b5063aed679495d92a04ffbe00451d34a11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232564"
---
# <a name="tutorial-create-partition-based-models-in-r-on-sql-server"></a>Tutorial: Erstellen von Partitionen basierenden Modellen in R in SQL Server
[!INCLUDE[appliesto-ssvnex-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In SQL Server-2019 ist die Partition-basierten Modellierung die Möglichkeit zum Erstellen und Trainieren von Modellen für partitionierte Daten. Für geschichteten Daten, die auf natürliche Weise in einem angegebenen Klassifizierungsschema - z. B. geografische Regionen, Datum und Uhrzeit, Alter oder Geschlecht - Segmente können Sie ausführen, Skript für den gesamten Daten, die Möglichkeit, modellieren, Trainieren und bewerten über Partitionen, die unverändert über alle diese Vorgänge. 

Partition-basierten Modellierung wird durch die beiden neuen Parameter aktiviert, auf [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql):

+ **input_data_1_partition_by_columns**, der angibt, dass einer Spalteninhalts für eine Partitionierung.
+ **input_data_1_order_by_columns** gibt an, welche Spalten nach der sortiert wird. 

Erfahren Sie in diesem Tutorial Partition-basierten Modellierung, die mit dem klassischen NYC Taxi-Beispieldaten und R-Skript aus. Die Partitionsspalte ist die Zahlungsmethode.

> [!div class="checklist"]
> * Partitionen basieren auf tarifarten (5).
> * Erstellen und Trainieren von Modellen in jeder Partition ein, und speichern Sie die Objekte in der Datenbank.
> * Wahrscheinlichkeitsvorhersage die Tip-Ergebnisse für jede Partitionsmodell mithilfe von Beispieldaten, die für diesen Zweck reserviert.

## <a name="prerequisites"></a>Erforderliche Komponenten
 
Für dieses Tutorial verwendet werden kann, müssen Sie über Folgendes verfügen:

+ Genügend Systemressourcen. Das Dataset ist groß und Training-Vorgänge sind mit großem Ressourcenaufwand. Verwenden Sie wenn möglich, einem System mit mindestens 8 GB RAM. Alternativ können Sie kleinere Datasets zu ressourceneinschränkungen umgehen. Anweisungen zur Reduzierung des Berechtigungssatzes für die Daten werden Inline. 

+ Ein Tool für die T-SQL-abfrageausführung, z. B. [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

+ [NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak), Sie können [herunterladen und Wiederherstellen von](sqldev-download-the-sample-data.md) auf Ihrer lokalen Datenbank-Engine-Instanz. Dateigröße beträgt ca. 90 MB.

+ SQL Server-2019 Vorschau-Datenbank-Engine-Instanz, mit Machine Learning Services und R-Integration.

Version überprüfen, indem Sie Ausführung **`SELECT @@Version`** als T-SQL-Abfrage in einem Abfragetool. Ausgabe muss "Microsoft SQL Server 2019 (CTP 2.0) - 15.0.x".

Überprüfen der Verfügbarkeit von R-Paketen durch die Rückgabe einer gut formatierten Liste von alle R-Pakete, die derzeit mit der Datenbank-Engine-Instanz installiert:

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

## <a name="connect-to-the-database"></a>Verbinden mit der Datenbank

Starten Sie Management Studio, und Verbinden mit der Datenbank-Engine-Instanz. Überprüfen Sie im Objekt-Explorer die [NYCTaxi_Sample Datenbank](sqldev-download-the-sample-data.md) vorhanden ist. 

## <a name="create-calculatedistance"></a>Erstellen von "calculatedistance"

Die Demodatenbank verfügt standardmäßig über eine skalare Funktion für die Berechnung der Entfernung, aber unsere gespeicherte Prozedur funktioniert besser mit einer Funktion mit Tabellenrückgabe. Führen Sie das folgende Skript zum Erstellen der **"calculatedistance"** Funktion verwendet die [Training Schritt](#training-step) später.

Wurde die Funktion erstellt überprüfen, um die \Programmability\Functions\Table-valued-Funktionen, unter dem **NYCTaxi_Sample** Datenbank im Objekt-Explorer.

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

## <a name="define-a-procedure-for-creating-and-training-per-partition-models"></a>Definieren Sie eine Prozedur zum Erstellen und Trainieren von Modellen pro partition

Dieses Tutorial dient als Wrapper für R-Skript in einer gespeicherten Prozedur. In diesem Schritt erstellen Sie eine gespeicherte Prozedur, die R zum Erstellen eines Eingabedatasets ein, und erstellen ein klassifizierungsmodell zum Vorhersagen von Tip-Ergebnisse verwendet werden soll, und klicken Sie dann das Modell in der Datenbank gespeichert.

Für die Parametereingaben, die durch dieses Skript verwendet wird, sehen Sie **input_data_1_partition_by_columns** und **input_data_1_order_by_columns**. Rückruf, der diese Parameter sind der Mechanismus, mit dem Modellierung partitioniert auftritt. Die Parameter werden als Eingaben für übergeben [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) zum Verarbeiten von Partitionen mit dem externen Skript ausführen einmal für jede Partition. 

Für diese gespeicherte Prozedur [Parallelismus](#parallel) für schnellere Zeit bis zum Abschluss.

Nach dem Ausführen dieses Skripts sollte **Train_rxLogIt_per_partition** in \Programmability\Stored Prozeduren unter der **NYCTaxi_Sample** Datenbank im Objekt-Explorer. Lesen Sie auch eine neue Tabelle zum Speichern von Modellen: **dbo.nyctaxi_models**.

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

Beachten Sie, dass die [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) Eingaben zählen  **@parallel= 1**verwendet, um die parallele Verarbeitung zu ermöglichen. Im Gegensatz zu vorherigen Versionen in SQL Server-2019, Festlegen von  **@parallel= 1** bietet einen stärkeren Hinweis für den Abfrageoptimierer, wodurch die parallele Ausführung ein Ergebnis mit größerer Wahrscheinlichkeit.

Standardmäßig ist die Abfrageoptimierer Betrieb unter  **@parallel= 1** für Tabellen, die über mehr als 256 Zeilen, aber Sie können Wenn Sie dies explizit durch Festlegen von behandeln  **@parallel= 1** wie in diesem Beispiel Skript.

> [!Tip]
> Zur Schulung Workoads, verwenden Sie **@parallel** mit jedem beliebigen trainingsskript, auch solche, die nicht-Microsoft-Rx-Algorithmen verwenden. In der Regel bieten nur über die RevoScaleR-Algorithmen (mit dem Rx-Präfix) Parallelität bei der aus-und weiterbildungsszenarien in SQL Server. Aber mit dem neuen Parameter, können Sie ein Skript, das Aufrufe von Funktionen, einschließlich der Open-Source-R-Funktionen, nicht speziell entwickelt, mit dieser Funktion parallelisieren. Dies funktioniert, da Partitionen über Affinität an bestimmte Threads verfügen, damit alle Vorgänge, die in einem Skript aufgerufen jeweils pro Partition, für den angegebenen Thread ausführen.

<a name="training-step"></a>

## <a name="run-the-procedure-and-train-the-model"></a>Die Prozedur auszuführen und das Modell trainieren

In diesem Abschnitt trainiert das Skript das Modell, das Sie erstellt und im vorherigen Schritt gespeichert haben. Die folgenden Beispiele zeigen zwei Ansätze zum Trainieren Ihres Modells: über einen ganzen Satz von Daten oder einen Teil der Daten. 

Erwarten Sie diesen Schritt, um eine gewisse Zeit dauern. Training ist rechenintensiv, so viele Minuten in Anspruch nehmen. Wenn die Systemressourcen, insbesondere Arbeitsspeicher nicht ausreichend, für das Laden sind, verwenden Sie eine Teilmenge der Daten. Im zweite Beispiel enthält die Syntax.

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
> Wenn Sie andere arbeitsauslastungen ausführen, können Sie hängen `OPTION(MAXDOP 2)` zur SELECT-Anweisung, wenn Sie nur 2 Kernen, die Verarbeitung von Abfragen einschränken möchten.

## <a name="check-results"></a>Ergebnisse der systemprüfung

Das Ergebnis in der Tabelle für die Modelle sollten fünf verschiedene Modelle, die basierend auf fünf Partitionen segmentiert nach der fünf Zahlungsarten sein. Modelle sind der **Ml_models** -Datenquelle.

```sql
SELECT *
FROM ml_models
```
 
## <a name="define-a-procedure-for-predicting-outcomes"></a>Definieren Sie eine Prozedur zum Vorhersagen von Ergebnissen

Sie können die gleichen Parameter für die Bewertung verwenden. Das folgende Beispiel enthält ein R-Skript, die bewertet wird, verwenden das richtige Modell für die Partition, die gerade verarbeitet wird.

Erstellen Sie eine gespeicherte Prozedur zum Umschließen von R-Code wie zuvor.

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

## <a name="create-a-table-to-store-predictions"></a>Erstellen Sie eine Tabelle zum Speichern von Vorhersagen

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

## <a name="run-the-procedure-and-save-predictions"></a>Führen Sie die Prozedur aus, und speichern Sie vorhersagen

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

Da die Vorhersagen gespeichert sind, können Sie eine einfache Abfrage, die ein Resultset zurückgeben ausführen.

```sql
SELECT *
FROM prediction_results;
```

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial verwendet Sie [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) partitionierte Daten Vorgänge durchlaufen. Näher betrachten, externe Skripts in gespeicherten Prozeduren aufrufen und RevoScaleR-Funktionen verwenden, fahren Sie mit dem folgenden Tutorial fort.

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
