---
title: Bereitstellen eines R-Modells für Vorhersagen auf SQL Server
description: Tutorial, das zeigt, wie Sie ein R-Modell auf SQL Server für datenbankübergreifende Analysen bereitstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 96744b15bef03b7d8badc803b1fa5f5de382e64f
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470545"
---
# <a name="deploy-the-r-model-and-use-it-in-sql-server-walkthrough"></a>Bereitstellen des R-Modells und Verwendung in SQL Server (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In dieser Lektion erfahren Sie, wie Sie R-Modelle in einer Produktionsumgebung bereitstellen, indem Sie ein trainiertes Modell aus einer gespeicherten Prozedur aufrufen. Sie können die gespeicherte Prozedur aus R oder einer beliebigen Anwendungs Programmiersprache aufrufen, [!INCLUDE[tsql](../../includes/tsql-md.md)] die (z C#. b. Java, python usw.) unterstützt, und das Modell verwenden, um Vorhersagen zu neuen Beobachtungen zu treffen.

In diesem Artikel werden die beiden gängigsten Methoden zur Verwendung eines Modells in der Bewertung veranschaulicht:

> [!div class="checklist"]
> * Der **Batch Bewertungsmodus** generiert mehrere Vorhersagen.
> * **Einzelner Bewertungsmodus** generiert Vorhersagen nacheinander.

## <a name="batch-scoring"></a>Batch Bewertung

Erstellen Sie eine gespeicherte Prozedur, die den *prättipbatchmode*generiert, die mehrere Vorhersagen generiert und eine SQL-Abfrage oder-Tabelle als Eingabe übergibt. Eine Tabelle mit Ergebnissen wird zurückgegeben, die Sie direkt in eine Tabelle einfügen oder in eine Datei schreiben können.

- Ruft einen Satz von Eingabedaten als SQL-Abfrage ab
- Ruft das trainierte logistische Regressionsmodell auf, das Sie in der vorherigen Lektion gespeichert haben
- Vorhersagen der Wahrscheinlichkeit, dass der Treiber einen trinkwert ungleich 0 (null) erhält

1. Öffnen Sie in Management Studio ein neues Abfragefenster, und führen Sie das folgende T-SQL-Skript aus, um die gespeicherte Prozedur "prättipbatchmode" zu erstellen.
  
    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipBatchMode')
    DROP PROCEDURE v
    GO

    CREATE PROCEDURE [dbo].[PredictTipBatchMode] @input nvarchar(max)
    AS
    BEGIN
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model  FROM nyc_taxi_models);
      EXEC sp_execute_external_script @language = N'R',
         @script = N'
           mod <- unserialize(as.raw(model));
           print(summary(mod))
           OutputDataSet<-rxPredict(modelObject = mod,
             data = InputDataSet,
             outData = NULL,
             predVarNames = "Score", type = "response",
             writeModelVars = FALSE, overwrite = TRUE);
           str(OutputDataSet)
           print(OutputDataSet)',
      @input_data_1 = @input,
      @params = N'@model varbinary(max)',
      @model = @lmodel2
      WITH RESULT SETS ((Score float));
    END
    ```

    + Sie verwenden eine SELECT-Anweisung, um das gespeicherte Modell aus einer SQL-Tabelle aufzurufen. Das Modell wird aus der Tabelle als **varbinary (max)** -Daten abgerufen, die in der SQL-Variablen  _\@lmodel2_gespeichert sind und als Parameter *mod* an die gespeicherte System Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)übergeben werden.

    + Die Daten, die als Eingaben für die Bewertung verwendet werden, werden als SQL-Abfrage definiert und als Zeichenfolge in der SQL-Variablen  _\@Eingabe_gespeichert. Wenn Daten aus der Datenbank abgerufen werden, werden Sie in einem Datenrahmen mit dem Namen input *DataSet*gespeichert, der lediglich der Standardname für die Eingabedaten für die [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) -Prozedur ist. Sie können bei Bedarf einen anderen Variablennamen definieren, indem Sie den Parameter  *_\@input_data_1_name_* verwenden.

    + Um die Ergebnisse zu generieren, ruft die gespeicherte Prozedur die RX-Vorhersagefunktion aus der **revoscaler** -Bibliothek auf.

    + Der Rückgabewert, *Score*, ist die Wahrscheinlichkeit, dass dieser Treiber einen Tipp erhält, wenn das Modell den Wert erhält. Optional können Sie einen Filter auf die zurückgegebenen Werte anwenden, um die Rückgabewerte in die Gruppen "Tip" und "No Tip" zu kategorisieren.  Eine Wahrscheinlichkeit von weniger als 0,5 bedeutet beispielsweise, dass ein Trinkgeld unwahrscheinlich ist.
  
2.  Um die gespeicherte Prozedur im Batch Modus aufzurufen, definieren Sie die Abfrage, die als Eingabe für die gespeicherte Prozedur erforderlich ist. Im folgenden finden Sie die SQL-Abfrage, die Sie in SSMS ausführen können, um zu überprüfen, ob Sie funktioniert.

    ```sql
    SELECT TOP 10
      a.passenger_count AS passenger_count,
      a.trip_time_in_secs AS trip_time_in_secs,
      a.trip_distance AS trip_distance,
      a.dropoff_datetime AS dropoff_datetime,
      dbo.fnCalculateDistance( pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance
      FROM 
        (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude 
        FROM nyctaxi_sample)a 
      LEFT OUTER JOIN
      ( SELECT medallion, hack_license, pickup_datetime
      FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b
      ON a.medallion=b.medallion
      AND a.hack_license=b.hack_license
      AND a.pickup_datetime=b.pickup_datetime
      WHERE b.medallion is null
    ```

3. Verwenden Sie diesen R-Code zum Erstellen der Eingabe Zeichenfolge aus der SQL-Abfrage:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. Um die gespeicherte Prozedur aus R auszuführen, nennen Sie die **sqlQuery** -Methode des **rodbc** -Pakets, und verwenden `conn` Sie die SQL-Verbindung, die Sie zuvor definiert haben:

    ```R
    sqlQuery (conn, q);
    ```

    Wenn Sie einen ODBC-Fehler erhalten, überprüfen Sie, ob Syntax Fehler vorliegen und ob Sie über die richtige Anzahl von Anführungszeichen verfügen. 
    
    Wenn Sie einen Berechtigungs Fehler erhalten, stellen Sie sicher, dass die Anmeldung die Möglichkeit hat, die gespeicherte Prozedur auszuführen.

## <a name="single-row-scoring"></a>Einzel Zeilen Bewertung

Der einzelne Bewertungsmodus generiert nacheinander Vorhersagen, wobei ein Satz einzelner Werte als Eingabe an die gespeicherte Prozedur übergeben wird. Die Werte entsprechen den Funktionen im Modell, die das Modell verwendet, um eine Vorhersage zu erstellen, oder generieren ein anderes Ergebnis, z. b. einen Wahrscheinlichkeitswert. Sie können diesen Wert dann an die Anwendung oder den Benutzer zurückgeben.

Wenn Sie das Modell für Vorhersagen zeilenweise aufrufen, übergeben Sie einen Satz von Werten, die Features für jeden einzelnen Fall darstellen. Die gespeicherte Prozedur gibt dann eine einzelne Vorhersage oder Wahrscheinlichkeit zurück. 

Der *präpsinglemode* der gespeicherten Prozedur veranschaulicht diese Vorgehensweise. Dabei werden mehrere Parameter verwendet, die featurewerte darstellen (z. b. die Anzahl der Fahrgäste und die Fahrtstrecke), diese Features mithilfe des gespeicherten R-Modells bewertet und die Tipp Wahrscheinlichkeit ausgegeben.

1. Führen Sie die folgende Transact-SQL-Anweisung aus, um die gespeicherte Prozedur zu erstellen.

    ```sql
    USE [NYCTaxi_Sample]
    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO

    IF EXISTS (SELECT * FROM sys.objects WHERE type = 'P' AND name = 'PredictTipSingleMode')
    DROP PROCEDURE v
    GO

    CREATE PROCEDURE [dbo].[PredictTipSingleMode] @passenger_count int = 0,
    @trip_distance float = 0,
    @trip_time_in_secs int = 0,
    @pickup_latitude float = 0,
    @pickup_longitude float = 0,
    @dropoff_latitude float = 0,
    @dropoff_longitude float = 0
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        SELECT * FROM [dbo].[fnEngineerFeatures](@passenger_count, @trip_distance, @trip_time_in_secs, @pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude)'
      DECLARE @lmodel2 varbinary(max) = (SELECT TOP 1 model FROM nyc_taxi_models);

      EXEC sp_execute_external_script @language = N'R',  @script = N'
            mod <- unserialize(as.raw(model));
            print(summary(mod))
            OutputDataSet<-rxPredict(
              modelObject = mod,
              data = InputDataSet,
              outData = NULL,
              predVarNames = "Score",
              type = "response",
              writeModelVars = FALSE,
              overwrite = TRUE);
            str(OutputDataSet)
            print(OutputDataSet)
            ',
      @input_data_1 = @inquery,
      @params = N'
      -- passthrough columns
      @model varbinary(max) ,
      @passenger_count int ,
      @trip_distance float ,
      @trip_time_in_secs int ,
      @pickup_latitude float ,
      @pickup_longitude float ,
      @dropoff_latitude float ,
      @dropoff_longitude float',
      -- mapped variables
      @model = @lmodel2 ,
      @passenger_count =@passenger_count ,
      @trip_distance=@trip_distance ,
      @trip_time_in_secs=@trip_time_in_secs ,
      @pickup_latitude=@pickup_latitude ,
      @pickup_longitude=@pickup_longitude ,
      @dropoff_latitude=@dropoff_latitude ,
      @dropoff_longitude=@dropoff_longitude
      WITH RESULT SETS ((Score float));
    END
    ```

2. In SQL Server Management Studio können Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] **exec** -Prozedur (oder **Execute**) verwenden, um die gespeicherte Prozedur aufzurufen und die erforderlichen Eingaben zu übergeben. Versuchen Sie z. b., diese Anweisung in Management Studio auszuführen:

    ```sql
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    Die hier über gebenden Werte werden für die Variablen "Anzahl der _Fahrgäste\__ ", _"trip_distance_", " _Reise\_Zeit\_in\_Sekunden_", " _Pickup\_Latitude_", _Pickup\_-Längen_Grad, _Zielort\_-Breitengrad_und _\_Längen_Grad der Länge.

3. Um denselben-Befehl aus R-Code auszuführen, definieren Sie einfach eine R-Variable, die den gesamten gespeicherten Prozedur Aufrufsatz enthält, wie folgt:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    Die hier über gebenden Werte sind für die Variablen "Anzahl der _Fahrgäste\__ ", _"\_Fahrt Distanz_", " _\_Fahrt Zeit\_in\_Sekunden_", " _Pickup\_ " Breite_, _Pickup\_-Längen_Grad, _\_Zielort-Breitengrad_und _\_Zielort-Längen_Grad.

4. Wenden `sqlQuery` Sie (aus dem **rodbc** -Paket) an, und übergeben Sie die Verbindungs Zeichenfolge zusammen mit der Zeichen folgen Variablen, die den gespeicherten Prozedur aufzurufen.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > R Tools für Visual Studio (rtvs) bietet eine gute Integration in SQL Server und R. Weitere Beispiele für die Verwendung von rodbc mit einer SQL Server Verbindung finden Sie in diesem Artikel: [Arbeiten mit SQL Server und R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie gelernt haben, wie Sie mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten arbeiten und trainierte R-Modelle dauerhaft in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]speichern, sollte es relativ einfach sein, basierend auf diesem DataSet neue Modelle zu erstellen. Beispielsweise können Sie versuchen, diese zusätzlichen Modelle zu erstellen:

+ Ein Regressionsmodell, das die Höhe des Trinkgelds vorhersagt
+ Ein mehr klassiges Klassifizierungs Modell, das vorhersagt, ob der Tipp groß, Mittel oder klein ist

Möglicherweise möchten Sie auch diese zusätzlichen Beispiele und Ressourcen durchsuchen:

+ [Szenarien für Data Science und Lösungsvorlagen](data-science-scenarios-and-solution-templates.md)
+ [Datenbankinterne Advanced Analytics](sqldev-in-database-r-for-sql-developers.md)
+ [Machine Learning Server Anleitungen](https://docs.microsoft.com/machine-learning-server/r/how-to-introduction)
+ [Machine Learning Server zusätzlicher Ressourcen](https://docs.microsoft.com//machine-learning-server/resources-more)
