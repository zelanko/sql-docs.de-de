---
title: 'Tutorial zu R und Transact-SQL: Ausführen von Vorhersagen'
description: Tutorial zum Operationalisieren eines eingebetteten R-Skripts in gespeicherten SQL Server-Prozeduren mit T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4b8e516d2e96c1cc4812a36800fd22371729445d
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81115973"
---
# <a name="lesson-4-run-predictions-using-r-embedded-in-a-stored-procedure"></a>Lektion 4: Ausführen von Vorhersagen mithilfe eines eingebetteten R-Skripts in einer gespeicherten Prozedur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In diesem Schritt erfahren Sie, wie Sie das Modell für neue Beobachtungen verwenden, um potenzielle Ergebnisse vorherzusagen. Das Modell wird in einer gespeicherten Prozedur umschlossen, die direkt von anderen Anwendungen aufgerufen werden kann. In der exemplarischen Vorgehensweise werden verschiedene Möglichkeiten zum Ausführen der Bewertung beschrieben:

- **Batchbewertungsmodell:** Verwenden Sie eine SELECT-Abfrage als Eingabe für die gespeicherte Prozedur. Die gespeicherte Prozedur gibt eine Tabelle mit Beobachtungen zurück, die mit den Eingabefällen übereinstimmen.

- **Einzelbewertungsmodus:** Übergeben Sie individuelle Parameterwerte als Eingabe.  Die gespeicherte Prozedur gibt eine einzelne Zeile oder einen Wert zurück.

Sehen wir uns zuerst einmal an, wie die Bewertung im Allgemeinen abläuft.

## <a name="basic-scoring"></a>Grundlegende Bewertung

Die gespeicherte Prozedur **RxPredict** beschreibt die grundlegende Syntax für das Umschließen eines RevoScaleR rxPredict-Aufrufs in einer gespeicherten Prozedur.

```sql
CREATE PROCEDURE [dbo].[RxPredict] (@model varchar(250), @inquery nvarchar(max))
AS 
BEGIN 

DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);  
EXEC sp_execute_external_script @language = N'R',
  @script = N' 
    mod <- unserialize(as.raw(model)); 
    print(summary(mod)) 
    OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE); 
    str(OutputDataSet) 
    print(OutputDataSet) 
    ', 
  @input_data_1 = @inquery, 
  @params = N'@model varbinary(max)',
  @model = @lmodel2 
  WITH RESULT SETS ((Score float));
END
GO
```

+ Die SELECT-Anweisung ruft das serialisierte Modell aus der Datenbank ab und speichert das Modell in der R-Variable `mod` zur weiteren Verarbeitung mit R.

+ Die neuen Fälle für die Bewertung werden aus der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfrage abgerufen, die in `@inquery` festgelegt ist, dem ersten Parameter für die gespeicherte Prozedur. Wenn die Abfragedaten gelesen werden, werden die Zeilen im Standard-Datenrahmen, `InputDataSet`, gespeichert. Dieser Datenrahmen wird der [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)-Funktion in [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) übergeben, die die Bewertungen generiert.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Da ein data.frame eine einzelne Zeile enthalten kann, können Sie den gleichen Code für die Batchbewertung und die Einzelbewertung verwenden.
  
+ Der von der `rxPredict`-Funktion zurückgegebene Wert ist ein **float**-Wert, der die Wahrscheinlichkeit darstellt, dass der Fahrer ein Trinkgeld in beliebiger Höhe erhält.

## <a name="batch-scoring-a-list-of-predictions"></a>Batchbewertung (Liste von Vorhersagen)

Ein häufigeres Szenario ist das Generieren von Vorhersagen für mehrere Beobachtungen im Batchmodus. In diesem Schritt sehen wir uns an, wie die Batchbewertung funktioniert.

1.  Rufen Sie zunächst eine Reihe von Eingabedaten ab, mit denen Sie arbeiten werden. Diese Abfrage erstellt eine „Top 10“-Liste der Fahrten mit Reisenden sowie anderen Funktionen, die benötigt werden, um eine Vorhersage zu erstellen.
  
    ```sql
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Beispielergebnisse**
    
    ```sql
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

2. Erstellen Sie eine gespeicherte Prozedur mit dem Namen **RxPredictBatchOutput** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

    ```sql
    CREATE PROCEDURE [dbo].[RxPredictBatchOutput] (@model varchar(250), @inquery nvarchar(max))
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script 
      @language = N'R',
      @script = N'
        mod <- unserialize(as.raw(model));
        print(summary(mod))
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);
        str(OutputDataSet)
        print(OutputDataSet)
      ',
      @input_data_1 = @inquery,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

3.  Stellen Sie den Abfragetext in einer Variable bereit, und übergeben Sie diese als Parameter an die gespeicherte Prozedur:

    ```sql
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'
    
    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[RxPredictBatchOutput] @model = 'RxTrainLogit_model', @inquery = @query_string;
    ```
  
Die gespeicherte Prozedur gibt eine Reihe von Werten zurück, die die Vorhersage für jede Fahrt der „Top 10-Fahrten“ darstellt. Bei den besten Fahrten handelt es sich jedoch um Fahrten von Einzelpersonen mit einer relativ kurzen Fahrtstrecke, für die der Fahrer wahrscheinlich kein Trinkgeld erhält.
  

> [!TIP]
> 
> Anstatt nur die Ergebnisse mit Informationen wie „Trinkgeld/Kein Trinkgeld“ zurückzugeben, könnten Sie auch den Wahrscheinlichkeitswert für die Vorhersage zurückgeben und anschließend auf die Spalte _Score_ eine WHERE-Klausel anwenden, um die Bewertung als „Trinkgeld“ oder „Kein Trinkgeld“ zu kategorisieren und dabei einen Schwellenwert wie z. B. 0,5 oder 0,7 verwenden. Dieser Schritt ist nicht in der gespeicherten Prozedur enthalten, aber es wäre leicht, ihn zu implementieren.

## <a name="single-row-scoring-of-multiple-inputs"></a>Einzeilige Bewertung mehrerer Eingaben

Manchmal möchten Sie mehrere Eingabewerte übergeben und basierend auf diesen Werten eine einzelne Vorhersage erhalten. Beispielsweise könnten Sie ein Excel-Arbeitsblatt, eine Webanwendung oder einen Reporting Services-Bericht einrichten, um die gespeicherte Prozedur aufzurufen und Eingaben bereitzustellen, die von Benutzern dieser Anwendungen eingegeben oder ausgewählt wurden.

In diesem Abschnitt erfahren Sie, wie Sie einzelne Vorhersagen mithilfe einer gespeicherten Prozedur erstellen, bei der mehrere Eingaben wie beispielsweise die Anzahl der Fahrgäste, die Fahrtstrecke usw. berücksichtigt werden. Die gespeicherte Prozedur erstellt eine Bewertung auf Grundlage des zuvor gespeicherten R-Modells.
  
Überprüfen Sie, ob die Daten mit den Anforderungen des R-Modells übereinstimmen, wenn Sie die gespeicherte Prozedur aus einer externen Anwendung aufrufen. Sie müssen möglicherweise sicherstellen, dass die Eingabedaten in einen R-Datentyp umgewandelt oder konvertiert werden können oder den Datentyp und die Datenlänge überprüfen. 

1. Erstellen Sie eine gespeicherte **RxPredictSingleRow**-Prozedur
  
    ```sql
    CREATE PROCEDURE [dbo].[RxPredictSingleRow] @model varchar(50), @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT model FROM nyc_taxi_models WHERE name = @model);
    EXEC sp_execute_external_script  
      @language = N'R',
      @script = N'  
        mod <- unserialize(as.raw(model));  
        print(summary(mod));  
        OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);  
        str(OutputDataSet);
        print(OutputDataSet); 
        ',  
      @input_data_1 = @inquery,  
      @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,@trip_time_in_secs int ,  @pickup_latitude float ,@pickup_longitude float ,@dropoff_latitude float ,@dropoff_longitude float', @model = @lmodel2, @passenger_count =@passenger_count, @trip_distance=@trip_distance, @trip_time_in_secs=@trip_time_in_secs, @pickup_latitude=@pickup_latitude, @pickup_longitude=@pickup_longitude, @dropoff_latitude=@dropoff_latitude, @dropoff_longitude=@dropoff_longitude  
      WITH RESULT SETS ((Score float));  
    END
    ```

2. Probieren Sie es einfach aus, indem Sie die Werte manuell bereitstellen.
  
    Öffnen Sie ein neues **Abfrage**-Fenster, und rufen Sie die gespeicherte Prozedur auf, die Werte für jeden der Parameter bereitstellt. Die Parameter stellen Funktionsspalten dar, die vom Modell verwendet werden und erforderlich sind.

    ```sql
    EXEC [dbo].[RxPredictSingleRow] @model = 'RxTrainLogit_model',
    @passenger_count = 1,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = -73.977303
    ```

    Oder verwenden Sie diese kürzere Form, die für [Parameter für eine gespeicherte Prozedur](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters) unterstützt wird:
  
    ```sql
    EXEC [dbo].[RxPredictSingleRow] 'RxTrainLogit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Die Ergebnisse geben an, dass die Wahrscheinlichkeit eines Trinkgelds für diese „Top 10-Fahrten“ sehr niedrig ist, da hier nur Einzelpersonen über eine relativ kurze Entfernung mitgefahren sind.

## <a name="conclusions"></a>Zusammenfassung

Dies ist der Abschluss für das Lernprogramm. Nachdem Sie erfahren haben, wie Sie R-Code in gespeicherte Prozeduren einbetten, können Sie diese Vorgehensweisen erweitern, um eigene Modelle zu erstellen. Die Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)] macht es viel einfacher, R-Modelle für Vorhersagen bereitzustellen und das erneute Trainieren von Modellen im Rahmen eines Unternehmensdatenworkflows zu integrieren.

## <a name="previous-lesson"></a>Vorherige Lerneinheit

[Lektion 3: Trainieren und Speichern eines R-Modells mit T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)
