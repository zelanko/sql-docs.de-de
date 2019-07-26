---
title: Lektion 4 Vorhersagen potenzieller Ergebnisse mithilfe von R-Modellen
description: Tutorial zum operationalisieren eines eingebetteten R-Skripts in SQL Server gespeicherten Prozeduren mit T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: a3bd6671ee1f48c67f58e9b1ee17772b18184bc0
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68469049"
---
# <a name="lesson-4-run-predictions-using-r-embedded-in-a-stored-procedure"></a>Lektion 4: Ausführen von Vorhersagen mithilfe von R Embedded in einer gespeicherten Prozedur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In diesem Schritt erfahren Sie, wie Sie das Modell für neue Beobachtungen verwenden, um potenzielle Ergebnisse vorherzusagen. Das Modell wird in einer gespeicherten Prozedur umschließt, die direkt von anderen Anwendungen aufgerufen werden kann. In der exemplarischen Vorgehensweise werden verschiedene Möglichkeiten zum Ausführen der Bewertung veranschaulicht:

- **Batch Bewertungsmodus**: Verwenden Sie eine SELECT-Abfrage als Eingabe für die gespeicherte Prozedur. Die gespeicherte Prozedur gibt eine Tabelle mit Beobachtungen zurück, die mit den Eingabefällen übereinstimmen.

- **Einzelner Bewertungsmodus**: Übergeben Sie einen Satz einzelner Parameterwerte als Eingabe.  Die gespeicherte Prozedur gibt eine einzelne Zeile oder einen Wert zurück.

Sehen wir uns zuerst einmal an, wie die Bewertung im Allgemeinen abläuft.

## <a name="basic-scoring"></a>Grundlegende Bewertung

Die gespeicherte Prozedur **rxvorhersage** veranschaulicht die grundlegende Syntax zum Umwickeln eines revoscaler rxvorhersage-Aufrufes in einer gespeicherten Prozedur.

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

+ Die SELECT-Anweisung ruft das serialisierte Modell aus der Datenbank ab und speichert das Modell in der r `mod` -Variablen zur weiteren Verarbeitung mithilfe von r.

+ Die neuen Fälle für die Bewertung werden aus der [!INCLUDE[tsql](../../includes/tsql-md.md)] in `@inquery`angegebenen Abfrage abgerufen, dem ersten Parameter für die gespeicherte Prozedur. Wenn die Abfragedaten gelesen werden, werden die Zeilen im Standard-Datenrahmen, `InputDataSet`, gespeichert. Dieser Datenrahmen wird an die [rxvorhersage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) -Funktion in [revoscaler](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)übergeben, die die Ergebnisse generiert.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Da ein data.frame eine einzelne Zeile enthalten kann, können Sie den gleichen Code für die Batchbewertung und die Einzelbewertung verwenden.
  
+ Der von der `rxPredict` -Funktion zurückgegebene Wert ist ein **float** -Wert, der die Wahrscheinlichkeit darstellt, dass der Treiber einen beliebigen Betrag erhält.

## <a name="batch-scoring-a-list-of-predictions"></a>Batch Bewertung (eine Liste von Vorhersagen)

Ein häufiges Szenario ist das Generieren von Vorhersagen für mehrere Beobachtungen im Batch Modus. In diesem Schritt sehen wir uns an, wie die Batch Bewertung funktioniert.

1.  Beginnen Sie, indem Sie einen kleineren Satz von Eingabedaten erhalten, mit denen Sie arbeiten können. Diese Abfrage erstellt eine „Top 10“-Liste der Fahrten mit Reisenden sowie anderen Funktionen, die benötigt werden, um eine Vorhersage zu erstellen.
  
    ```sql
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Beispiel Ergebnisse**
    
    ```sql
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

2. Erstellen Sie eine gespeicherte Prozedur mit dem Namen **rxvorhertbatchoutput** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

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

3.  Geben Sie den Abfragetext in einer Variablen an, und übergeben Sie ihn als Parameter an die gespeicherte Prozedur:

    ```sql
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'
    
    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[RxPredictBatchOutput] @model = 'RxTrainLogit_model', @inquery = @query_string;
    ```
  
Die gespeicherte Prozedur gibt eine Reihe von Werten zurück, die die Vorhersage für die ersten 10 Fahrten darstellen. Die häufigsten Fahrten sind aber auch Einzelpersonen Fahrten mit einer relativ kurzen Fahrtstrecke, bei der der Treiber wahrscheinlich keinen Tipp erhält.
  

> [!TIP]
> 
> Anstatt nur die Ergebnisse "Yes-Tip" und "No-Tip" zurückzugeben, können Sie auch das Wahrscheinlichkeits Ergebnis für die Vorhersage zurückgeben und dann eine WHERE-Klausel auf die Werte der _Bewertungs Spalte anwenden_ , um das Ergebnis als "wahrscheinlich Tip" oder "unwahrscheinlich an Tip" zu kategorisieren, indem Sie einen Schwellenwert, z. b. 0,5 oder 0,7. Dieser Schritt ist nicht in der gespeicherten Prozedur enthalten, aber es wäre leicht, ihn zu implementieren.

## <a name="single-row-scoring-of-multiple-inputs"></a>Einzeilige Bewertung mehrerer Eingaben

Manchmal möchten Sie mehrere Eingabewerte übergeben und eine einzelne Vorhersage auf der Grundlage dieser Werte erhalten. Beispielsweise können Sie ein Excel-Arbeitsblatt, eine Webanwendung oder einen Reporting Services Bericht einrichten, um die gespeicherte Prozedur aufzurufen und Eingaben bereitzustellen, die von Benutzern von diesen Anwendungen eingegeben oder ausgewählt wurden.

In diesem Abschnitt erfahren Sie, wie Sie einzelne Vorhersagen mithilfe einer gespeicherten Prozedur erstellen, die mehrere Eingaben annimmt, wie z. b. die Anzahl der Fahrgäste, die Fahrtstrecke usw. Die gespeicherte Prozedur erstellt eine Bewertung auf der Grundlage des zuvor gespeicherten R-Modells.
  
Wenn Sie die gespeicherte Prozedur aus einer externen Anwendung abrufen, stellen Sie sicher, dass die Daten den Anforderungen des R-Modells entsprechen. Sie müssen möglicherweise sicherstellen, dass die Eingabedaten in einen R-Datentyp umgewandelt oder konvertiert werden können oder den Datentyp und die Datenlänge überprüfen. 

1. Erstellen Sie eine gespeicherte Prozedur **rxvorhertsinglerow**.
  
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
  
    Öffnen Sie ein neues **Abfrage** Fenster, und geben Sie die gespeicherte Prozedur an, und geben Sie für jeden Parameterwerte an. Die Parameter stellen featurespalten dar, die vom Modell verwendet werden, und sind erforderlich.

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

    Oder verwenden Sie dieses kürzere Formular, das für [Parameter einer gespeicherten Prozedur](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters)unterstützt wird:
  
    ```sql
    EXEC [dbo].[RxPredictSingleRow] 'RxTrainLogit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Die Ergebnisse geben an, dass die Wahrscheinlichkeit, dass ein Trinkgeld erhält, bei den ersten 10 Fahrten niedrig (null) ist, da es sich bei allen um Einzelpersonen übergreifende Fahrten über eine relativ kurze Entfernung handelt.

## <a name="conclusions"></a>Schlussfolgerungen

Dies ist der Abschluss für das Lernprogramm. Nachdem Sie erfahren haben, wie Sie R-Code in gespeicherte Prozeduren einbetten, können Sie diese Vorgehensweisen erweitern, um eigene Modelle zu erstellen. Die Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)] macht es viel einfacher, R-Modelle für Vorhersagen bereitzustellen und das erneute Trainieren von Modellen im Rahmen eines Unternehmensdatenworkflows zu integrieren.

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 3: Trainieren und Speichern eines R-Modells mit T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)
