---
title: Erstellen von Datenfunktionen mithilfe von R-und SQL Server-Funktionen
description: Tutorial zum Erstellen von Datenfunktionen mit SQL Server Funktionen für Daten bankübergreifende Analysen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f12c20a54c0811e392eaa85684d7fac1a209c396
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714694"
---
# <a name="create-data-features-using-r-and-sql-server-walkthrough"></a>Erstellen von Datenfunktionen mithilfe von R und SQL Server (Exemplarische Vorgehensweise)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Data Engineering ist ein wichtiger Teil des maschinellen Lernens. Daten erfordern häufig eine Transformation, bevor Sie Sie für die Vorhersage Modellierung verwenden können. Wenn die Daten nicht über die Features verfügen, die Sie benötigen, können Sie diese aus vorhandenen Werten erstellen.

Sie möchten für diesen Modellierungstask möglicherweise lieber die Entfernung in Meilen zwischen zwei Orten haben anstatt die ungefähren Werte für den Breiten- und Längengrad des Abhol- und Zielorts. Zum Erstellen dieses Features berechnen Sie die direkte lineare Entfernung zwischen zwei Punkten, indem Sie die [Haversinus-Formel](https://en.wikipedia.org/wiki/Haversine_formula)verwenden.

In diesem Schritt erlernen Sie zwei verschiedene Methoden zum Erstellen eines Features aus Daten:

> [!div class="checklist"]
> * Verwenden einer benutzerdefinierten R-Funktion
> * Verwenden einer benutzerdefinierten T-SQL-Funktion in[!INCLUDE[tsql](../../includes/tsql-md.md)]

Ziel ist es, einen neuen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Satz von Daten zu erstellen, der die ursprünglichen Spalten sowie die neue numerische Funktion *direct_distance*enthält.

## <a name="prerequisites"></a>Vorraussetzungen

Dieser Schritt setzt eine laufende R-Sitzung voraus, die auf vorherigen Schritten in dieser exemplarischen Vorgehensweise basiert. Dabei werden die Verbindungs Zeichenfolgen und Datenquellen Objekte verwendet, die in diesen Schritten erstellt werden. Die folgenden Tools und Pakete werden zum Ausführen des Skripts verwendet.

+ "Rgui. exe" zum Ausführen von R-Befehlen
+ Management Studio zum Ausführen von T-SQL

## <a name="featurization-using-r"></a>Featurearisierung mithilfe von R

Die Sprache R ist bekannt für ihre großen und vielseitigen statistischen Bibliotheken, doch Sie müssen ggf. weiterhin benutzerdefinierte Datentransformationen erstellen.

Zuerst wird die Art und Weise beschrieben, wie R-Benutzer daran gewöhnt sind: Sie können die Daten auf Ihrem Laptop ablegen und dann eine benutzerdefinierte R-Funktion ( *computedist*) ausführen, die die lineare Entfernung zwischen zwei Punkten berechnet, die durch breiten-und Längengrad Werte angegeben werden.

1. Beachten Sie, dass das Datenquellen Objekt, das Sie zuvor erstellt haben, nur die obersten 1000 Zeilen erhält. Definieren wir also eine Abfrage, mit der alle Daten abgerufen werden.

    ```R
    bigQuery <- "SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,  pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude FROM nyctaxi_sample";
    ```

2. Erstellen Sie mithilfe der Abfrage ein neues Datenquellen Objekt.

    ```R
    featureDataSource <- RxSqlServerData(sqlQuery = bigQuery,colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric", dropoff_longitude = "numeric", dropoff_latitude = "numeric", passenger_count  = "numeric", trip_distance  = "numeric", trip_time_in_secs  = "numeric", direct_distance  = "numeric"), connectionString = connStr);
    ```

    - [Rxsqlserverdata](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxsqlserverdata) kann entweder eine Abfrage enthalten, die aus einer gültigen SELECT-Abfrage besteht, die als Argument für den _sqlQuery_ -Parameter bereitgestellt wird, oder den Namen eines Table-Objekts, das als _Tabellen_ Parameter bereitgestellt wird.
    
    - Wenn Sie Stichproben von Daten aus einer Tabelle durchführen möchten, müssen Sie den _sqlQuery_ -Parameter verwenden, samplingparameter mithilfe der T-SQL TABLESAMPLE-Klausel definieren und das _rowbuffereing_ -Argument auf false festlegen.

3. Führen Sie folgenden Code aus, um die benutzerdefinierte R-Funktion zu erstellen. Computedist nimmt zwei Paare von breiten-und Längengrad Werten an und berechnet die lineare Entfernung zwischen Ihnen und gibt den Abstand in Kilometern zurück.

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

4. Nachdem Sie die Funktion definiert haben, wenden Sie Sie auf die Daten an, um eine neue Funktions Spalte, *direct_distance*, zu erstellen. Ändern Sie jedoch vor dem Ausführen der Transformation den computekontext in local.

    ```R
    rxSetComputeContext("local");
    ```

5. Verwenden Sie die Funktion [rxdatastep](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatastep) , um die featureengineering-Daten abzurufen `env$ComputeDist` , und wenden Sie die Funktion auf die Daten im Arbeitsspeicher an.

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

    + Die rxdatastep-Funktion unterstützt verschiedene Methoden zum Ändern von Daten an Ort und Stelle. Weitere Informationen finden Sie in diesem Artikel:  [Transformieren und unterteilen von Daten in "mikrosft R"](https://docs.microsoft.com/r-server/r/how-to-revoscaler-data-transform)
    
    Bei rxdatastep sollten Sie jedoch einige Punkte beachten: 
    
    In anderen Datenquellen können Sie die Argumente *varstokeep* und *varstodrop*verwenden, diese werden jedoch für SQL Server Datenquellen nicht unterstützt. Daher haben wir in diesem Beispiel das _Transformationen_ -Argument zum Angeben der Pass-Through-Spalten und der transformierten Spalten verwendet. Außerdem kann das _InData_ -Argument bei der Ausführung in einem SQL Server computekontext nur eine SQL Server Datenquelle annehmen.

    Der vorangehende Code kann auch eine Warnmeldung ausgeben, wenn er für größere Datasets ausgeführt wird. Wenn die Anzahl der Zeilen, die die Anzahl der zu erstellenden Spalten überschreitet, einen festgelegten Wert überschreitet (der Standardwert ist 3 Millionen), gibt rxdatastep eine Warnung aus, und die Anzahl der Zeilen im zurückgegebenen Datenrahmen wird abgeschnitten. Um die Warnung zu entfernen, können Sie das _maxrowsbycols_ -Argument in der rxdatastep-Funktion ändern. Wenn _maxrowsbycols_ jedoch zu groß ist, können beim Laden des Daten Rahmens in den Arbeitsspeicher Probleme auftreten.

7. Optional können Sie [rxgetvarinfo](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxgetvarinfo) aufrufen, um das Schema der transformierten Datenquelle zu überprüfen.

    ```R
    rxGetVarInfo(data = changed_ds);
    ```

## <a name="featurization-using-transact-sql"></a>Featurebereitstellung mit Transact-SQL

In dieser Übung erfahren Sie, wie Sie dieselbe Aufgabe mithilfe von SQL-Funktionen anstelle von benutzerdefinierten R-Funktionen ausführen. 

Wechseln Sie zu [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) oder einem anderen Abfrage-Editor, um das T-SQL-Skript auszuführen.

1. Verwenden Sie eine SQL-Funktion mit dem Namen *fncalculatedistance*. Die Funktion sollte bereits in der NYCTaxi_Sample-Datenbank vorhanden sein. Überprüfen Sie in Objekt-Explorer, ob die Funktion vorhanden ist, indem Sie auf diesen Pfad Datenbanken > NYCTaxi_Sample > Programmierbarkeit > Funktionen > Skalarwertfunktionen > dbo. fncalculatedistance.

    Wenn die Funktion nicht vorhanden ist, verwenden Sie SQL Server Management Studio, um die Funktion in der NYCTaxi_Sample-Datenbank zu generieren.

    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function calculates the direct distance between two geographical coordinates.
    RETURNS decimal(28, 10)
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

2. Führen Sie in Management Studio in einem neuen Abfragefenster die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung aus einer beliebigen Anwendung aus, die unterstützt [!INCLUDE[tsql](../../includes/tsql-md.md)] , um zu sehen, wie die Funktion funktioniert.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude 
    FROM nyctaxi_sample
    ```
3. Wenn Sie Werte direkt in eine neue Tabelle einfügen möchten (Sie müssen Sie zuerst erstellen), können Sie eine **into** -Klausel hinzufügen, die den Tabellennamen angibt.

    ```sql
    USE nyctaxi_sample
    GO

    SELECT tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, pickup_datetime, dropoff_datetime,
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude) as direct_distance, pickup_latitude, pickup_longitude, dropoff_latitude, dropoff_longitude
    INTO NewFeatureTable
    FROM nyctaxi_sample
    ```

4. Sie können auch die SQL-Funktion aus R-Code abrufen. Wechseln Sie zurück zur rgui, und speichern Sie die SQL-featureabfrage in einer R-Variablen.

    ```R
    featureEngineeringQuery = "SELECT tipped, fare_amount, passenger_count,
        trip_time_in_secs,trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance,
        pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude
        FROM nyctaxi_sample
        tablesample (1 percent) repeatable (98052)"
    ```
  
    > [!TIP]
    > Diese Abfrage wurde geändert, um eine kleinere Stichprobe von Daten zu erhalten, um diese exemplarische Vorgehensweise schneller zu machen. Sie können die TABLESAMPLE-Klausel entfernen, wenn Sie alle Daten erhalten möchten. abhängig von Ihrer Umgebung ist es jedoch möglicherweise nicht möglich, das vollständige DataSet in R zu laden, was zu einem Fehler führt.
  
5. Verwenden Sie die folgenden Codezeilen, um die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion aus Ihrer R-Umgebung aufzurufen und sie auf die Daten anzuwenden, die in *featureEngineeringQuery* definiert sind.
  
    ```R
    featureDataSource = RxSqlServerData(sqlQuery = featureEngineeringQuery,
      colClasses = c(pickup_longitude = "numeric", pickup_latitude = "numeric",
        dropoff_longitude = "numeric", dropoff_latitude = "numeric",
        passenger_count  = "numeric", trip_distance  = "numeric",
        trip_time_in_secs  = "numeric", direct_distance  = "numeric"),
      connectionString = connStr)
    ```
  
6.  Nachdem das neue Feature erstellt wurde, rufen Sie **rxgetvarsinfo** auf, um eine Zusammenfassung der Daten in der Featuretabelle zu erstellen.
  
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
    > In einigen Fällen erhalten Sie möglicherweise eine Fehlermeldung wie die folgende: *Die EXECUTE-Berechtigung wurde für das Objekt ' fncalculatedistance ' verweigert* . Wenn dies der Fall ist, stellen Sie sicher, dass der verwendete Anmelde Name über Berechtigungen zum Ausführen von Skripts und Erstellen von Objekten in der Datenbank verfügt, nicht nur auf der-Instanz.
    > Überprüfen Sie das Schema für das Objekt, fncalculatedistance. Wenn das Objekt vom Datenbankbesitzer erstellt wurde und Ihre Anmeldung zu der Rolle db_datareader gehört, müssen Sie dem Anmelde Namen die expliziten Berechtigungen zum Ausführen des Skripts einräumen.

## <a name="comparing-r-functions-and-sql-functions"></a>Vergleichen von R-Funktionen und SQL-Funktionen

Merken Sie sich diesen Code, der verwendet wird, um den R-Code zu verwenden?

```R
start.time <- proc.time()
<your code here>
used.time <- proc.time() - start.time
print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2)," seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))
```

Sie können dies mit dem Beispiel für eine benutzerdefinierte SQL-Funktion verwenden, um zu sehen, wie lange die Datentransformation beim Aufrufen einer SQL-Funktion dauert. Wechseln Sie außerdem zum Wechseln von computekontexten mit rxsetcomputecontext, und vergleichen Sie die Zeitangaben.

Abhängig von der Netzwerkgeschwindigkeit und der Hardwarekonfiguration können ihre Zeiten erheblich variieren. In den getesteten Konfigurationen war der Funktions [!INCLUDE[tsql](../../includes/tsql-md.md)] Ansatz schneller als die Verwendung einer benutzerdefinierten R-Funktion. Daher verwenden wir die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktion für diese Berechnungen in nachfolgenden Schritten.

> [!TIP]
> Sehr häufig ist die Funktionsentwicklung [!INCLUDE[tsql](../../includes/tsql-md.md)] mit schneller als R. T-SQL enthält z. b. schnelle Fenster-und Rang Folge Funktionen, die auf allgemeine Data Science Berechnungen angewendet werden können, z. b. das parallele Verschieben von durchschnitten und *n*-Kacheln. Wählen Sie je nach Daten und Aufgabe die effizienteste Methode.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen eines R-Modells und speichern in SQL](walkthrough-build-and-save-the-model.md)

