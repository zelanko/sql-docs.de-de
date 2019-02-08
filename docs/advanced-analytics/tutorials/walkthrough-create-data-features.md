---
title: Erstellen von Datenfunktionen mit R und SQL Server-Funktionen – SQL Server-Machine Learning
description: 'Tutorial: Erstellen von Datenfunktionen mit SQL Server-Funktionen für in-Database-Analyse.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 527f88ed14adc0140cbca179177e85670f72cafd
ms.sourcegitcommit: afc0c3e46a5fec6759fe3616e2d4ba10196c06d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55890011"
---
# <a name="create-data-features-using-r-and-sql-server-walkthrough"></a>Erstellen von Datenfunktionen mit R und SQL Server (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Data Engineering ist ein wichtiger Teil des maschinellen Lernens. Daten erfordern oft Transformation aus, bevor Sie es für die vorhersagemodellierung verwenden können. Wenn die Daten nicht über die Features verfügen, die Sie benötigen, können Sie diese aus vorhandenen Werten erstellen.

Sie möchten für diesen Modellierungstask möglicherweise lieber die Entfernung in Meilen zwischen zwei Orten haben anstatt die ungefähren Werte für den Breiten- und Längengrad des Abhol- und Zielorts. Um dieses Feature zu erstellen, berechnen Sie die direkte lineare Entfernung zwischen zwei Punkten mit den [Haversine-Formel](https://en.wikipedia.org/wiki/Haversine_formula).

Erfahren Sie in diesem Schritt zwei unterschiedliche Methoden zum Erstellen einer Funktion aus Daten:

> [!div class="checklist"]
> * Mithilfe einer benutzerdefinierten R-Funktion
> * Mithilfe einer benutzerdefinierten T-SQL-Funktion in [!INCLUDE[tsql](../../includes/tsql-md.md)]

Das Ziel ist, zum Erstellen eines neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Satz von Daten, der die ursprünglichen Spalten und die neue numerische Funktion enthält *Direct_distance*.

## <a name="prerequisites"></a>Erforderliche Komponenten

Dieser Schritt setzt voraus, eine laufende R-Sitzung basierend auf den vorherigen Schritten in dieser exemplarischen Vorgehensweise. Er verwendet die Zeichenfolgen und Data Source Verbindungsobjekte in diesen Schritten erstellt haben. Die folgenden Tools und Pakete werden verwendet, um das Skript auszuführen.

+ Rgui.exe zum Ausführen von R-Befehlen
+ Management Studio zum Ausführen von T-SQL

## <a name="featurization-using-r"></a>Featurebereitstellung mit R

Die Sprache R ist bekannt für ihre großen und vielseitigen statistischen Bibliotheken, doch Sie müssen ggf. weiterhin benutzerdefinierte Datentransformationen erstellen.

Zuerst machen wir die Möglichkeit, R-Benutzer sind es gewöhnt,: Rufen Sie die Daten auf Ihrem Laptop, und führen Sie eine benutzerdefinierte R-Funktion, *ComputeDist*, berechnet die Luftlinie zwischen zwei Punkten, die durch die Werte für Breiten- und Längengrad angegeben.

1. Denken Sie daran, dass das Datenquellenobjekt, die, das Sie zuvor erstellt haben, nur die ersten 1000 Zeilen erhält. Wir definieren eine Abfrage, die alle Daten abruft.

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. Erstellen Sie ein neues Datenquellenobjekt mithilfe der Abfrage.

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [RxSqlServerData](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) dauert entweder um eine Abfrage mit einer gültigen SELECT-Abfrage, als das Argument für die _SqlQuery_ Parameter oder den Namen des ein Table-Objekt, das als die _Tabelle_ der Parameter.
    
    - Wenn Sie Beispieldaten aus einer Tabelle möchten, müssen Sie verwenden die _SqlQuery_ Parameter Samplingparameter, die mit der T-SQL-TABLESAMPLE-Klausel definieren, und legen die _RowBuffering_ Argument auf "false".

3. Führen Sie den folgenden Code ein, um die benutzerdefinierte R-Funktion zu erstellen. ComputeDist verwendet zwei Paare von Breiten-und längengradwerten und berechnet die Luftlinie zwischen sie gibt die Entfernung in Meilen.

    ```R
    env <- new.env();
    env$ComputeDist <- function(pickup_long, pickup_lat, dropoff_long, dropoff_lat){
      R <- 6371/1.609344 #radius in mile
      delta_lat <- dropoff_lat - pickup_lat
      delta_long <- dropoff_long - pickup_long
      degrees_to_radians = pi/180.0
      a1 <- sin(delta_lat/2*degrees_to_radians)
      a2 <- as.numeric(a1)^2
      a3 <- cos(pickup_lat*degrees_to_radians)
      a4 <- cos(dropoff_lat*degrees_to_radians)
      a5 <- sin(delta_long/2*degrees_to_radians)
      a6 <- as.numeric(a5)^2
      a <- a2+a3*a4*a6
      c <- 2*atan2(sqrt(a),sqrt(1-a))
      d <- R*c
      return (d)
    }
    ```
  
    + Die erste Zeile definiert eine neue Umgebung. In R kann eine Umgebung verwendet werden, um Namespaces z.B. in Paketen einzuschließen. Sie können die `search()` -Funktion verwenden, um die Umgebungen in Ihrem Arbeitsbereich anzuzeigen. Um die Objekte in einer bestimmten Umgebung anzuzeigen, geben Sie `ls(<envname>)`ein.
    + Die Zeilen, die mit `$env.ComputeDist` beginnen, enthalten den Code, der die Haversine-Formel definiert, die die *Großkreisentfernung* zwischen zwei Punkten auf einer Kugel berechnet.

4. Wenn Sie die Funktion definiert, Sie sie anwenden auf Daten, erstellen Sie eine neue funktionsspalte, *Direct_distance*. aber vor dem Ausführen der Transformations, ändern Sie des computekontexts auf lokale.

    ```R
    rxSetComputeContext("local");
    ```

5. Rufen Sie die [RxDataStep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) Funktion, um die Daten für die Featureentwicklung abzurufen, und wenden die `env$ComputeDist` Funktion, um die Daten im Arbeitsspeicher.

    ```R
    start.time <- proc.time();
  
    changed_ds <- rxDataStep(inData = featureDataSource,
    transforms = list(direct_distance=ComputeDist(pickup_longitude,pickup_latitude, dropoff_longitude, dropoff_latitude),
    tipped = "tipped", fare_amount = "fare_amount", passenger_count = "passenger_count",
    trip_time_in_secs = "trip_time_in_secs",  trip_distance="trip_distance",
    pickup_datetime = "pickup_datetime",  dropoff_datetime = "dropoff_datetime"),
    transformEnvir = env,
    rowsPerRead=500,
    reportProgress = 3);
  
    used.time <- proc.time() - start.time;
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""));
    ```

    + Die RxDataStep-Funktion unterstützt verschiedene Methoden zum Ändern von Daten vorhanden. Weitere Informationen finden Sie im Artikel:  [Transformieren und die Teilmenge von Daten in Microsft R](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    Jedoch ein paar Punkte zu beachten, die in Bezug auf RxDataStep: 
    
    In anderen Datenquellen können Sie die Argumente *VarsToKeep* und *VarsToDrop*, aber diese werden für SQL Server-Datenquellen nicht unterstützt. Aus diesem Grund in diesem Beispiel haben wird die _transformiert_ Argument, um sowohl die Pass-Through-Spalten als auch den transformierten Spalten anzugeben. Darüber hinaus bei Ausführung in einer SQL Server compute Context verwenden, die _InData_ -Argument sind nur eine SQL Server-Datenquelle.

    Der vorangehende Code kann außerdem eine Warnmeldung angezeigt, die bei Ausführung auf größeren Datasets erstellen. Wenn die Anzahl der Zeilen, wie oft der Spalten erstellt wird (der Standardwert ist 3.000.000) festgelegten Wert überschreitet, RxDataStep wird eine Warnung zurückgegeben und die Anzahl der Zeilen im Frame zurückgegebenen Daten werden abgeschnitten. Um die Warnung zu entfernen, können Sie ändern die _MaxRowsByCols_ Argument in der RxDataStep-Funktion. Aber wenn _MaxRowsByCols_ ist zu groß ist, könnten Probleme bei den Datenrahmen in den Speicher geladen.

7. Sie können optional Aufrufen [RxGetVarInfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) um das Schema der transformierten Datenquelle überprüfen.

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Featurebereitstellung mit Transact-SQL

Erfahren Sie in dieser Übung, wie die gleiche Aufgabe, die anstelle von benutzerdefinierter R-Funktionen in SQL-Funktionen durchführen. 

Wechseln Sie zur [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder eine andere Abfrage-Editor, um das T-SQL-Skript auszuführen.

1. Verwenden Sie eine SQL-Funktion, mit dem Namen *FnCalculateDistance*. Die Funktion sollte bereits in der Datenbank NYCTaxi_Sample vorhanden sein. Überprüfen Sie im Objekt-Explorer, ob die Funktion vorhanden ist, indem Sie diesen Pfad navigieren: Datenbanken > NYCTaxi_Sample > Programmierbarkeit > Funktionen > Skalarwertfunktionen > dbo.fnCalculateDistance.

    Wenn die Funktion nicht vorhanden ist, mit der SQL Server Management Studio die Funktion in der Datenbank NYCTaxi_Sample generiert.

    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function calculates the direct distance between two geographical coordinates.
    RETURNS
    AS
    BEGIN
      DECLARE @distance decimal(28, 10)
      -- Convert to radians
      SET @Lat1 = @Lat1 / 57.2958
      SET @Long1 = @Long1 / 57.2958
      SET @Lat2 = @Lat2 / 57.2958
      SET @Long2 = @Long2 / 57.2958
      -- Calculate distance
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))
      --Convert to miles
      IF @distance <> 0
      BEGIN
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);
      END
      RETURN @distance
    END
    ```

2. Führen Sie in Management Studio in einem neuen Abfragefenster den folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung aus einer beliebigen Anwendung, die unterstützt [!INCLUDE[tsql](../../includes/tsql-md.md)] angezeigt, wie die Funktion arbeitet.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude 
    FROM nyctaxi_sample
    ```
3. Um die Werte direkt in eine neue Tabelle einzufügen (müssen Sie ihn zunächst erstellen), fügen Sie eine **INTO** -Klausel, die den Namen der Tabelle angibt.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. Sie können auch die SQL-Funktion aus R-Code aufrufen. Wechseln Sie zurück zum Rgui und speichern Sie die SQL-featurebereitstellung-Abfrage in eine R-Variable.

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > Diese Abfrage wurde geändert wurde, rufen Sie ein kleineres Datenbeispiel, um diese exemplarische Vorgehensweise zu beschleunigen. Sie können die TABLESAMPLE-Klausel entfernen, wenn alle Daten abgerufen werden soll. Allerdings je nach Umgebung, es möglich, laden die vollständige eines Datasets in R, was zu einem Fehler möglicherweise nicht.
  
5. Verwenden Sie die folgenden Codezeilen, um die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion aus Ihrer R-Umgebung aufzurufen und sie auf die Daten anzuwenden, die in *featureEngineeringQuery* definiert sind.
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
        dropoff_longitude = "numeric", dropoff_latitude = "numeric",
        passenger_count  = "numeric", trip_distance  = "numeric",
        trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  Nachdem das neue Feature erstellt wurde, rufen **RxGetVarsInfo** eine Zusammenfassung der Daten in der Funktionstabelle zu erstellen.
  
    ```R
    rxGetVarInfo(data = featureDataSource)
    ```

    **Ergebnisse**

    ```R
    Var 1: tipped, Type: integer
    Var 2: fare_amount, Type: numeric
    Var 3: passenger_count, Type: numeric
    Var 4: trip_time_in_secs, Type: numeric
    Var 5: trip_distance, Type: numeric
    Var 6: pickup_datetime, Type: character
    Var 7: dropoff_datetime, Type: character
    Var 8: direct_distance, Type: numeric
    Var 9: pickup_latitude, Type: numeric
    Var 10: pickup_longitude, Type: numeric
    Var 11: dropoff_latitude, Type: numeric
    Var 12: dropoff_longitude, Type: numeric
    ```

    > [!NOTE]
    > In einigen Fällen erhalten Sie möglicherweise einen Fehler wie diesen: *Die EXECUTE-Berechtigung wurde verweigert, für das Objekt "FnCalculateDistance"* Wenn dies der Fall ist, stellen Sie sicher, dass die Anmeldung, die Sie verwenden verfügt über Berechtigungen zum Ausführen von Skripts, und Erstellen von Objekten in der Datenbank, nicht nur auf der Instanz.
    > Überprüfen Sie das Schema für das Objekt FnCalculateDistance. Wenn das Objekt vom Datenbankbesitzer erstellt wurde und die Anmeldung auf die Rolle "db_datareader" gehört, müssen Sie den Anmeldenamen explizite Berechtigungen zum Ausführen des Skripts erhalten.

## <a name="comparing-r-functions-and-sql-functions"></a>Vergleich von R- und SQL-Funktionen

Erinnern Sie sich diesem Codeausschnitt, den Zeitpunkt des R-Codes verwendet?

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

Sie können versuchen, mit diesem mit dem SQL-Beispiel für benutzerdefinierte Funktion, um festzustellen, wie lange dauert die Datentransformation beim Aufrufen einer SQL-Funktion. Darüber hinaus testen Sie, wechseln von computekontexten mit RxSetComputeContext aus, und vergleichen Sie die Intervalle zu.

Die Zeiten variieren je nach netzwerkgeschwindigkeit und der Hardwarekonfiguration erheblich. In den uns getesteten Konfigurationen der [!INCLUDE[tsql](../../includes/tsql-md.md)] Funktion Ansatz war schneller als die Verwendung einer benutzerdefinierten R-Funktion. Aus diesem Grund haben wir die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktion für diese Berechnungen in den nachfolgenden Schritten.

> [!TIP]
> Sehr oft Featureentwicklung mit [!INCLUDE[tsql](../../includes/tsql-md.md)] schneller als R. T-SQL enthält z. B. schnelle Windowing- und Rangfolgefunktionen, die auf allgemeine Data Science-Berechnungen z.B. Rollierende gleitende Durchschnitte angewendet werden können und *n*-Kacheln. Wählen Sie je nach Daten und Aufgabe die effizienteste Methode.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen eines R-Modells und speichern in SQL](walkthrough-build-and-save-the-model.md)

