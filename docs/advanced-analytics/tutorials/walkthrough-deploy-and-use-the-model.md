---
title: Stellen Sie das R-Modell, und verwenden Sie es in SQL (Exemplarische Vorgehensweise) | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 290659402622ab04de85e81f05328778b0f0c1eb
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983012"
---
# <a name="deploy-the-r-model-and-use-it-in-sql"></a>Bereitstellen Sie das R-Modell und verwenden Sie es in SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In dieser Lektion verwenden Sie R-Modelle in einer produktionsumgebung, durch den Aufruf eines trainierten Modells aus einer gespeicherten Prozedur. Rufen Sie anschließend die gespeicherte Prozedur aus R oder jeder beliebigen Anwendungsprogrammiersprache, die unterstützt [!INCLUDE[tsql](../../includes/tsql-md.md)] (z. B. c#, Java, Python usw.), um das Modell zum treffen von Vorhersagen für neue Beobachtungen zu verwenden.

Dieses Beispiel veranschaulicht die beiden am häufigsten verwendeten Arten eines Modells in der Bewertung:

- **Batchbewertungsmodus** wird verwendet, wenn müssen Sie sehr schnell mehrere Vorhersagen erstellen, durch Übergeben einer SQL abzufragen oder Tabelle als Eingabe. Eine Tabelle der Ergebnisse wird zurückgegeben, die Sie direkt in eine Tabelle einfügen, oder in eine Datei schreiben können.

- **Einzelbewertungsmodus** wird verwendet, wenn Sie einzelne Vorhersagen zu einem Zeitpunkt erstellen müssen. Sie haben einen Satz von einzelnen Werten an die gespeicherte Prozedur übergeben. Die Werte entsprechen den Funktionen im Modell, das Modell, die zum Erstellen einer Vorhersage verwendet werden, oder generieren ein anderes Ergebnis, wie z. B. ein Wahrscheinlichkeitswert. Sie können diesen Wert dann an die Anwendung oder den Benutzer zurückgeben.

## <a name="batch-scoring"></a>Batchbewertung

Eine gespeicherte Prozedur für die batchbewertung wurde erstellt, wenn Sie zunächst das PowerShell-Skript ausgeführt haben. Diese gespeicherte Prozedur, *PredictTipBatchMode*, bewirkt Folgendes:

- Ruft einen Satz von Eingabedaten als SQL-Abfrage ab
- Ruft das trainierte logistische Regressionsmodell auf, das Sie in der vorherigen Lektion gespeichert haben
- Prognostiziert die Wahrscheinlichkeit, dass der Treiber NULL-Tipp wird

1. Das Skript für die gespeicherte Prozedur kurz *PredictTipBatchMode*. Es veranschaulicht verschiedene Aspekte wie ein Modell mithilfe von [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]operationalisiert werden kann.
  
    ```tsql
    CREATE PROCEDURE [dbo].[PredictTipBatchMode]
    @input nvarchar(max)
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

    + Sie verwenden eine SELECT-Anweisung, um das gespeicherte Modell aus einer SQL-Tabelle aufzurufen. Das Modell wird aufgerufen, aus der Tabelle als **'varbinary(max)'** Daten, die in der SQL-Variablen gespeicherten _@lmodel2_, und als Parameter übergeben *mod* an das System gespeichert Prozedur [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

    + Die Daten, die als Eingaben verwendet werden, für die Bewertung als SQL-Abfrage definiert und als Zeichenfolge in der SQL-Variablen gespeichert _@input_. Wie Daten aus der Datenbank abgerufen werden, es befindet sich in einem Datenrahmen namens *"inputdataset"*, dies ist der voreingestellte Name für die Eingabedaten der [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) Prozedur; Sie können definieren, einen anderen Variablennamen an, die bei Bedarf mithilfe des Parameters *_@input_data_1_name_*.

    + Die gespeicherte Prozedur ruft die `rxPredict` -Funktion aus der **RevoScaleR** -Bibliothek auf, um die Bewertung zu generieren.

    + Der Rückgabewert *Bewertung*, ist die Wahrscheinlichkeit, anhand des Modells, ruft diese Treiber einen Tipp. Optional können Sie ganz einfach eine Art Filter auf die zurückgegebenen Werten die Rückgabewerte in "Trinkgeld" und "kein Trinkgeld"-Gruppen zu kategorisieren anwenden.  Eine Wahrscheinlichkeit von weniger als 0,5 bedeutet beispielsweise, dass ein Trinkgeld wahrscheinlich nicht ist.
  
2.  Um die gespeicherte Prozedur im Batchmodus aufzurufen, definieren Sie die Abfrage als Eingabe für die gespeicherte Prozedur. Dies ist die SQL-Abfrage; Sie können ihn ausführen, in SSMS, um sicherzustellen, dass es funktioniert.

    ```SQL
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

3. Verwenden Sie diesen R-Code, um die Eingabezeichenfolge aus der SQL-Abfrage zu erstellen:

    ```R
    input <- "N'SELECT TOP 10 a.passenger_count AS passenger_count, a.trip_time_in_secs AS trip_time_in_secs, a.trip_distance AS trip_distance, a.dropoff_datetime AS dropoff_datetime, dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) AS direct_distance FROM (SELECT medallion, hack_license, pickup_datetime, passenger_count,trip_time_in_secs,trip_distance, dropoff_datetime, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude FROM nyctaxi_sample)a LEFT OUTER JOIN ( SELECT medallion, hack_license, pickup_datetime FROM nyctaxi_sample  tablesample (1 percent) repeatable (98052)  )b ON a.medallion=b.medallion AND a.hack_license=b.hack_license AND  a.pickup_datetime=b.pickup_datetime WHERE b.medallion is null'";
    q <- paste("EXEC PredictTipBatchMode @inquery = ", input, sep="");
    ```

4. Rufen Sie zum Ausführen der gespeicherten Prozedur aus R die **SqlQuery** Methode der **RODBC** packen sowie die Verwendung der SQL-Verbindungs `conn` , die Sie zuvor definiert haben:

    ```R
    sqlQuery (conn, q);
    ```

    Wenn Sie einen ODBC-Fehler erhalten, überprüfen Sie die Abfragesyntax, sowie davon, ob Sie die richtige Anzahl von Anführungszeichen. 
    
    Wenn Sie fehlender Berechtigungen eine Fehlermeldung erhalten, stellen Sie sicher, dass es sich bei die Anmeldung die gespeicherte Prozedur ausführen kann.

## <a name="single-row-scoring"></a>Einzelzeilenbewertung

Wenn Sie das Modell für die Vorhersage pro Zeile für Zeile aufrufen, übergeben Sie einen Satz von Werten, die Features für jeden einzelnen Fall darstellen. Die gespeicherte Prozedur gibt eine einzige Vorhersage oder die Wahrscheinlichkeit zurück. 

Die gespeicherte Prozedur *PredictTipSingleMode* veranschaulicht diesen Ansatz. Es dauert, als mehrere Eingabeparameter, die featurewerte (z. B. Fahrgäste die Anzahl und die Wegstrecke) darstellt, bewertet diese Funktionen mit den gespeicherten R-Modells und gibt die Wahrscheinlichkeit Tipp.

1. Wenn die gespeicherte Prozedur *PredictTipSingleMode* wurde nicht erstellt, vom ersten PowerShell-Skript, können Sie die folgende Transact-SQL-Anweisung aus, um ihn jetzt erstellen ausführen.

    ```tsql
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

2. In SQL Server Management Studio können Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXEC** Prozedur (oder **EXECUTE**) zum Aufrufen der gespeicherten Prozedur, und übergeben sie die erforderlichen Eingaben. Versuchen Sie beispielsweise, die diese Anweisung in Management Studio ausführen:

    ```SQL
    EXEC [dbo].[PredictTipSingleMode] 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

    Die hier übergebenen Werte stehen für die Variablen _Fahrgäste\_Anzahl_, _Trip_distance_, _Reise\_Zeit\_in\_Sekunden_, _Pickup\_Latitude_, _Pickup\_Längengrad_, _Zielkoordinaten\_Latitude_, und _Zielkoordinaten\_Längengrad_.

3. Um diesen gleichen Aufruf von R-Code ausführen zu können, definieren Sie einfach eine R-Variable, die den gesamten gespeicherten Prozeduraufruf, wie die folgende enthält:

    ```R
    q2 = "EXEC PredictTipSingleMode 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303 ";
    ```

    Die hier übergebenen Werte stehen für die Variablen _Fahrgäste\_Anzahl_, _Reise\_Abstand_, _Reise\_Zeit\_in\_Sekunden_, _Pickup\_Latitude_, _Pickup\_Längengrad_, _Zielkoordinaten\_ Breitengrad_, und _Zielkoordinaten\_Längengrad_.

4. Rufen Sie `sqlQuery` (aus der **RODBC** Paket), und übergeben Sie die Verbindungszeichenfolge, zusammen mit dem String-Variable, die mit dem Aufruf der gespeicherten Prozedur.

    ```R
    # predict with stored procedure in single mode
    sqlQuery (conn, q2);
    ```

    >[!TIP]
    > R Tools für Visual Studio (RTVS) bietet eine hervorragende Integration mit SQL Server und R. Weitere Beispiele für die Verwendung von RODBC mit einer SQL Server-Verbindung finden Sie unter: [arbeiten mit SQL Server und R](https://docs.microsoft.com/visualstudio/rtvs/sql-server)

## <a name="summary"></a>Zusammenfassung

Jetzt wissen, Sie arbeiten mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten und trainierte R-Modellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], es sollte relativ einfach für Sie neue Modelle basierend auf dieses DataSet zu erstellen. Beispielsweise können Sie versuchen, diese zusätzliche Modelle zu erstellen:

- Ein Regressionsmodell, das die Höhe des Trinkgelds vorhersagt

- Ein mehrklassiges klassifizierungsmodell, das vorhersagt, ob die QuickInfo groß, Mittel oder klein ist.

Wir empfehlen außerdem, dass Sie sich einige dieser Beispiele und Ressourcen anschauen:

+ [Szenarien für Data Science und Lösungsvorlagen](data-science-scenarios-and-solution-templates.md)

+ [Datenbankinterne Advanced Analytics](sqldev-in-database-r-for-sql-developers.md)

+ [Microsoft R: Eintauchen in die Datenanalyse](https://msdn.microsoft.com/microsoft-r/data-analysis-in-microsoft-r)

+ [Zusätzliche Ressourcen](https://msdn.microsoft.com/microsoft-r/microsoft-r-more-resources)

## <a name="previous-lesson"></a>Vorherige Lektion

[Erstellen eines R-Modells und speichern Sie sie in SQL Server](walkthrough-build-and-save-the-model.md)

## <a name="next-steps"></a>Nächste Schritte

[SQL Server-R-Lernprogramme](sql-server-r-tutorials.md)

[Gewusst wie: Erstellen einer gespeicherten Prozedur mithilfe von sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)
