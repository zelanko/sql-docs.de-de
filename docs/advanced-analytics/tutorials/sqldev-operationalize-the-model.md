---
title: Lektion 6 Vorhersagen mögliche Ergebnissen mithilfe von R-Modelle (SQL Server-Machine Learning) | Microsoft Docs
description: Lernprogramm zur Einbettung von R in SQL Server gespeicherte Prozeduren und Funktionen des T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/08/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 32984626dfac11bd2465cb783c583f6b210f6b68
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249853"
---
# <a name="lesson-6-predict-potential-outcomes-using-an-r-model-in-a-stored-procedure"></a>Lektion 6: Vorhersagen von möglichen Ergebnissen, die mit R-Modell in einer gespeicherten Prozedur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Lernprogramms für SQL-Entwicklern zum Verwenden von R in SQL Server.

In diesem Schritt erfahren Sie, um das Modell mit neuen Beobachtungen zu verwenden, um mögliche Ergebnisse vorherzusagen. Das Modell wird in einer gespeicherten Prozedur umgeben, die direkt von einer anderen Anwendung aufgerufen werden kann. Die exemplarische Vorgehensweise veranschaulicht mehrere Möglichkeiten zum Bewerten von durchführen:

- **Batch scoring-Modus**: verwenden eine SELECT-Abfrage als Eingabe für die gespeicherte Prozedur. Die gespeicherte Prozedur gibt eine Tabelle mit Beobachtungen zurück, die mit den Eingabefällen übereinstimmen.

- **Einzelbewertungsmodus**: Übergeben Sie einen Satz von einzelnen Parameterwerten als Eingabe.  Die gespeicherte Prozedur gibt eine einzelne Zeile oder einen Wert zurück.

Sehen wir uns zuerst einmal an, wie die Bewertung im Allgemeinen abläuft.

## <a name="basic-scoring"></a>Grundlegende Bewertung

Die gespeicherte Prozedur **PredictTip** beschreibt die grundlegende Syntax für das Umschließen eines Vorhersageaufrufs in einer gespeicherten Prozedur.

```SQL
CREATE PROCEDURE [dbo].[PredictTip] @inquery nvarchar(max) 
AS 
BEGIN 
  
DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);  
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

+ Die SELECT-Anweisung ruft die serialisierten Modell aus der Datenbank ab und speichert das Modell in der R-Variable `mod` zur weiteren Verarbeitung mit r

+ Die neue Fälle für die Bewertung erhalten Sie vom der [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage, die im angegebenen `@inquery`, der erste Parameter der gespeicherten Prozedur. Wenn die Abfragedaten gelesen werden, werden die Zeilen im Standard-Datenrahmen, `InputDataSet`, gespeichert. Dieser Datenrahmen wird zum Übergeben der [RxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict) -Funktion in ["revoscaler"](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler), die die Ergebnisse generiert.
  
    `OutputDataSet<-rxPredict(modelObject = mod, data = InputDataSet, outData = NULL, predVarNames = "Score", type = "response", writeModelVars = FALSE, overwrite = TRUE);`
  
    Da ein data.frame eine einzelne Zeile enthalten kann, können Sie den gleichen Code für die Batchbewertung und die Einzelbewertung verwenden.
  
+ Der zurückgegebene Wert der `rxPredict` Funktion ist ein **"float"** , die die Wahrscheinlichkeit, dass der Treiber einen Betrag-Tipp ruft darstellt.

## <a name="batch-scoring"></a>Batchbewertung

Jetzt sehen wir uns an, wie die Batchbewertung funktioniert.

1.  Zunächst rufen wir einen kleineren Satz von Eingabedaten ab, mit denen wir arbeiten werden. Diese Abfrage erstellt eine „Top 10“-Liste der Fahrten mit Reisenden sowie anderen Funktionen, die benötigt werden, um eine Vorhersage zu erstellen.
  
    ```SQL
    SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance
    
    FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a

    LEFT OUTER JOIN

    (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052)    )b

    ON a.medallion=b.medallion AND a.hack_license=b.hack_license 
    AND a.pickup_datetime=b.pickup_datetime
    WHERE b.medallion IS NULL
    ```

    **Beispielergebnisse**
    
    ```
    passenger_count   trip_time_in_secs    trip_distance  dropoff_datetime   direct_distance
    1  283 0.7 2013-03-27 14:54:50.000   0.5427964547
    1  289 0.7 2013-02-24 12:55:29.000   0.3797099614
    1  214 0.7 2013-06-26 13:28:10.000   0.6970098661
    ```

    Diese Abfrage dient als Eingabe für die gespeicherte Prozedur **PredictTipMode**, der als Teil des Downloads.

2. Nehmen Sie sich an den Code der gespeicherten Prozedur überprüfen **PredictTipMode** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

    ```SQL
    /****** Object:  StoredProcedure [dbo].[PredictTipMode]  ******/
    CREATE PROCEDURE [dbo].[PredictTipMode] @inquery nvarchar(max)
    AS
    BEGIN
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
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

3.  Geben Sie den Abfragetext in einer Variablen, und übergeben Sie ihn als Parameter an die gespeicherte Prozedur:

    ```SQL
    -- Define the input data
    DECLARE @query_string nvarchar(max)
    SET @query_string='SELECT TOP 10 a.passenger_count as passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude,dropoff_longitude) AS direct_distance FROM  (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample  )a   LEFT OUTER JOIN (SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample TABLESAMPLE (70 percent) REPEATABLE (98052))b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'

    -- Call the stored procedure for scoring and pass the input data
    EXEC [dbo].[PredictTip] @inquery = @query_string;
    ```
  
4. Die gespeicherte Prozedur gibt eine Reihe von Werten, die die Vorhersage für jeden der obersten 10 Roundtrips darstellt. Die oberste Roundtrips sind jedoch auch einzelne Reisenden Reisen mit einer relativ kurzen Reise Entfernung, für die der Treiber einen Tipp abzurufenden unwahrscheinlich ist.
  

> [!TIP]
> 
> Anstatt nur der "Ja-Tipp" und "ohne-Tipp" Ergebnisse zurückgeben könnten Sie auch das wahrscheinlichkeitsergebnis für die Vorhersage zurückgeben, und wenden Sie dann eine WHERE-Klausel der _Score_ Spaltenwerte kategorisieren Sie das Ergebnis als "wahrscheinlich Tipp" oder " es unwahrscheinlich, dass Tipp", verwenden einen Schwellenwert, z. B. 0,5 oder 0,7. Dieser Schritt ist nicht in der gespeicherten Prozedur enthalten, aber es wäre leicht, ihn zu implementieren.

## <a name="single-row-scoring"></a>Einzeiliges Bewertung

Gelegentlich möchten Sie einzelne Werte aus einer Anwendung übergeben und ein einzelnes Ergebnis basierend auf diesen Werten erhalten. Beispielsweise könnten Sie ein Excel-Arbeitsblatt, eine Webanwendung oder einen Reporting Services-Bericht einrichten, um die gespeicherte Prozedur aufzurufen und Eingaben bereitzustellen, die von Benutzern eingegeben oder ausgewählt wurden.

In diesem Abschnitt erfahren Sie, wie einzelne Vorhersagen mit einer gespeicherten Prozedur zu erstellen.

1. Nehmen Sie sich an den Code der gespeicherten Prozedur überprüfen **PredictTipSingleMode**, die als Teil des Downloads enthalten ist.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0, @trip_distance float = 0, @trip_time_in_secs int = 0, @pickup_latitude float = 0, @pickup_longitude float = 0, @dropoff_latitude float = 0, @dropoff_longitude float = 0
    AS
    BEGIN
    DECLARE @inquery nvarchar(max) = N'SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs,  @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)';
    DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);
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
  
    - Diese gespeicherte Prozedur besitzt mehrerer einzelner Werte als Eingabe, wie die Anzahl der Reisende, Fahrstrecke usw.
  
        Wenn Sie die gespeicherte Prozedur von einer externen Anwendung aufrufen, stellen Sie sicher, dass die Daten den Anforderungen der R-Modell entspricht. Sie müssen möglicherweise sicherstellen, dass die Eingabedaten in einen R-Datentyp umgewandelt oder konvertiert werden können oder den Datentyp und die Datenlänge überprüfen. 
  
    -   Die gespeicherte Prozedur erstellt eine Bewertung auf Grundlage des gespeicherten R-Modells.
  
2. Probieren Sie es einfach aus, indem Sie die Werte manuell bereitstellen.
  
    Öffnen Sie ein neues **Abfrage** Fenster, und rufen Sie die gespeicherte Prozedur, und geben Sie Werte für jeden Parameter. Die Parameter vom Modell verwendeten merkmalspalten darstellen und erforderlich sind.

    ```
    EXEC [dbo].[PredictTipSingleMode] @passenger_count = 0,
    @trip_distance = 2.5,
    @trip_time_in_secs = 631,
    @pickup_latitude = 40.763958,
    @pickup_longitude = -73.973373,
    @dropoff_latitude =  40.782139,
    @dropoff_longitude = 73.977303
    ```

    Oder verwenden Sie dieses kürzere Form unterstützt für [Parameter an eine gespeicherte Prozedur](https://docs.microsoft.com/sql/relational-databases/stored-procedures/specify-parameters):
  
    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

3. Die Ergebnisse zeigen, dass die Wahrscheinlichkeit für einen Tipp Bei diesen Top 10 Reisen niedrig ist, da alle einzelnen Reisenden Zugriffe über einen relativ kurzen Abstand sind.

## <a name="conclusions"></a>Schlussfolgerungen

Dies ist der Abschluss für das Lernprogramm. Nun, da Sie So betten Sie ein R-Code in gespeicherten Prozeduren gelernt haben, können Sie diese Methoden zum Erstellen von Modellen Ihrer Wahl erweitern. Die Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)] macht es viel einfacher, R-Modelle für Vorhersagen bereitzustellen und das erneute Trainieren von Modellen im Rahmen eines Unternehmensdatenworkflows zu integrieren.

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 5: Trainieren Sie, und speichern Sie ein R-Modell mithilfe des T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)
