---
title: Vorhersagen potenzieller Ergebnisse mithilfe von python-Modellen
description: Tutorial zum operationalisieren eines eingebetteten PYthon-Skripts in SQL Server gespeicherten Prozeduren mit T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/02/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: b04e57c45c6113d4a0404a3a338e6beba4cda813
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68468600"
---
# <a name="run-predictions-using-python-embedded-in-a-stored-procedure"></a>Ausführen von Vorhersagen mithilfe von python Embedded in einer gespeicherten Prozedur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist Teil eines Tutorials, [in-Database-python-Analyse für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt erfahren Sie, wie Sie die Modelle, die Sie im vorherigen Schritt trainiert und gespeichert haben, *operationalisieren* .

In diesem Szenario bedeutet Operationalisierung, dass das Modell für die Bewertung in der Produktionsumgebung bereitgestellt wird. Durch die Integration in SQL Server ist dies recht einfach, da Sie Python-Code in eine gespeicherte Prozedur einbetten können. Zum Abrufen von Vorhersagen aus dem Modell basierend auf neuen Eingaben müssen Sie die gespeicherte Prozedur einfach aus einer Anwendung abrufen und die neuen Daten übergeben.

Diese Lektion veranschaulicht zwei Methoden zum Erstellen von Vorhersagen auf der Grundlage eines python-Modells: Batch Bewertung und Bewertung der zeilenweise.

- **Batch Bewertung:** Wenn Sie mehrere Zeilen mit Eingabedaten bereitstellen möchten, übergeben Sie eine SELECT-Abfrage als Argument an die gespeicherte Prozedur. Das Ergebnis ist eine Tabelle mit Beobachtungen, die den Eingabe Fällen entsprechen.
- **Individuelle Bewertung:** Übergeben Sie einen Satz einzelner Parameterwerte als Eingabe.  Die gespeicherte Prozedur gibt eine einzelne Zeile oder einen Wert zurück.

Der gesamte für die Bewertung benötigte Python-Code wird als Teil der gespeicherten Prozeduren bereitgestellt.

## <a name="batch-scoring"></a>Batch Bewertung

Die ersten beiden gespeicherten Prozeduren veranschaulichen die grundlegende Syntax zum Umwickeln eines python-Vorhersage Aufrufes in einer gespeicherten Prozedur. Beide gespeicherten Prozeduren erfordern eine Datentabelle als Eingaben.

- Der Name des exakten Modells, das verwendet werden soll, wird als Eingabeparameter für die gespeicherte Prozedur bereitgestellt. Die gespeicherte Prozedur lädt das serialisierte Modell mithilfe der SELECT- `nyc_taxi_models`Anweisung in der gespeicherten Prozedur aus der Datenbanktabelle. Table.
- Das serialisierte Modell wird zur weiteren Verarbeitung mithilfe von `mod` python in der python-Variablen gespeichert.
- Die neuen Fälle, die bewertet werden müssen, werden aus der [!INCLUDE[tsql](../../includes/tsql-md.md)] in `@input_data_1`angegebenen Abfrage abgerufen. Wenn die Abfragedaten gelesen werden, werden die Zeilen im Standard-Datenrahmen, `InputDataSet`, gespeichert.
- Beide gespeicherten Prozeduren verwenden `sklearn` Funktionen von, um eine Genauigkeits Metrik zu berechnen, AUC (Bereich unter Kurve). Genauigkeits Metriken wie z. b. AUC können nur generiert werden, wenn Sie  auch die Ziel Bezeichnung (die gekippte Spalte) angeben. Für Vorhersagen ist die Ziel Bezeichnung (Variable `y`) nicht erforderlich, aber die Berechnung der Genauigkeits Metrik.

    Wenn Sie also keine Ziel Bezeichnungen für die zu bewertenden Daten haben, können Sie die gespeicherte Prozedur so ändern, dass die AUC-Berechnungen entfernt werden, und nur die Tipp Wahrscheinlichkeiten aus den Funktionen `X` zurückgeben (Variable in der gespeicherten Prozedur).

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

Führen Sie die folgenden T-SQL-Anweisungen aus, um die gespeicherten Prozeduren zu erstellen. Diese gespeicherte Prozedur erfordert ein Modell, das auf dem Paket "scikit-Learn" basiert, da es für dieses Paket spezifische Funktionen verwendet:

+ Der Datenrahmen, der Eingaben enthält, `predict_proba` `mod`wird an die Funktion des logistischen Regressionsmodells () übermittelt. Die `predict_proba` -Funktion`probArray = mod.predict_proba(X)`() gibt einen **float** -Wert zurück, der die Wahrscheinlichkeit angibt, dass ein Trinkgeld (beliebiger Betrag) angegeben wird.

```sql
DROP PROCEDURE IF EXISTS PredictTipSciKitPy;
GO

CREATE PROCEDURE [dbo].[PredictTipSciKitPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script
  @language = N'Python',
  @script = N'
import pickle;
import numpy;
from sklearn import metrics

mod = pickle.loads(lmodel2)
X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
y = numpy.ravel(InputDataSet[["tipped"]])

probArray = mod.predict_proba(X)
probList = []
for i in range(len(probArray)):
  probList.append((probArray[i])[1])

probArray = numpy.asarray(probList)
fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
aucResult = metrics.auc(fpr, tpr)
print ("AUC on testing data is: " + str(aucResult))

OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
',  
  @input_data_1 = @inquery,
  @input_data_1_name = N'InputDataSet',
  @params = N'@lmodel2 varbinary(max)',
  @lmodel2 = @lmodel2
WITH RESULT SETS ((Score float));
END
GO
```

### <a name="predicttiprxpy"></a>Präprxpy

Diese gespeicherte Prozedur verwendet die gleichen Eingaben und erstellt denselben Typ von Bewertungen wie die vorherige gespeicherte Prozedur, verwendet jedoch Funktionen aus dem **revoscalepy** -Paket, das mit SQL Server Machine Learning bereitgestellt wird.

```sql
DROP PROCEDURE IF EXISTS PredictTipRxPy;
GO

CREATE PROCEDURE [dbo].[PredictTipRxPy] (@model varchar(50), @inquery nvarchar(max))
AS
BEGIN
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script 
  @language = N'Python',
  @script = N'
import pickle;
import numpy;
from sklearn import metrics
from revoscalepy.functions.RxPredict import rx_predict;

mod = pickle.loads(lmodel2)
X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]
y = numpy.ravel(InputDataSet[["tipped"]])

probArray = rx_predict(mod, X)
probList = probArray["tipped_Pred"].values 

probArray = numpy.asarray(probList)
fpr, tpr, thresholds = metrics.roc_curve(y, probArray)
aucResult = metrics.auc(fpr, tpr)
print ("AUC on testing data is: " + str(aucResult))

OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
',  
  @input_data_1 = @inquery,
  @input_data_1_name = N'InputDataSet',
  @params = N'@lmodel2 varbinary(max)',
  @lmodel2 = @lmodel2
WITH RESULT SETS ((Score float));
END
GO
```

## <a name="run-batch-scoring-using-a-select-query"></a>Ausführen der Batch Bewertung mithilfe einer SELECT-Abfrage

Die gespeicherten Prozeduren **präpscikitpy** und **prättiprxpy** erfordern zwei Eingabeparameter: 

- Die Abfrage, die die Daten für die Bewertung abruft.
- Der Name eines trainierten Modells.

Wenn Sie diese Argumente an die gespeicherte Prozedur übergeben, können Sie ein bestimmtes Modell auswählen oder die für die Bewertung verwendeten Daten ändern.

1. Um das **scikit-Learn-** Modell für die Bewertung zu verwenden, müssen Sie die **prättipscikitpy**der gespeicherten Prozedur abrufen und dabei den Modellnamen und die Abfrage Zeichenfolge als Eingaben übergeben.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    Die gespeicherte Prozedur gibt die vorhergesagten Wahrscheinlichkeiten für jede Fahrt zurück, die als Teil der Eingabe Abfrage übermittelt wurde. 
    
    Wenn Sie SSMS (SQL Server Management Studio) zum Ausführen von Abfragen verwenden, werden die Wahrscheinlichkeiten als Tabelle im **Ergebnis** Bereich angezeigt. Der Bereich **Meldungen** gibt die Genauigkeits Metrik (AUC oder Bereich unter Kurve) mit einem Wert von ungefähr 0,56 aus.

2. Um das **revoscalepy** -Modell für die Bewertung zu verwenden, rufen Sie die **präprxpy**der gespeicherten Prozedur auf, und übergeben Sie den Modellnamen und die Abfrage Zeichenfolge als Eingaben.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>Einzeilige Bewertung

Manchmal empfiehlt es sich, anstelle der Batch Bewertung einen einzelnen Fall zu übergeben, Werte von einer Anwendung zu erhalten und ein einzelnes Ergebnis auf der Grundlage dieser Werte zurückzugeben. Beispielsweise können Sie ein Excel-Arbeitsblatt, eine Webanwendung oder einen Bericht einrichten, um die gespeicherte Prozedur aufzurufen und Eingaben an IT-Eingaben zu übergeben, die von Benutzern eingegeben oder ausgewählt wurden.

In diesem Abschnitt erfahren Sie, wie Sie einzelne Vorhersagen erstellen, indem Sie zwei gespeicherte Prozeduren aufrufen:

+ " [Prättipsinglemodescikitpy](#predicttipsinglemodescikitpy) " ist für die Einzel Zeilen Bewertung mit dem scikit-Learn-Modell konzipiert.
+ " [Prättipsinglemoderxpy](#predicttipsinglemoderxpy) " ist für die Einzel Zeilen Bewertung mithilfe des revoscalepy-Modells konzipiert.
+ Wenn Sie noch kein Modell trainiert haben, kehren Sie zu [Schritt 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)zurück!

Beide Modelle verwenden als Eingabe eine Reihe von einzelnen Werten, wie z. b. die Anzahl der Fahrgäste, die Fahrtstrecke usw. Eine Tabellenwert Funktion `fnEngineerFeatures`,, wird verwendet, um Werte für breiten-und Längengrade von den Eingaben in eine neue Funktion, direkte Entfernung, zu konvertieren. [Lektion 4](sqldev-py4-create-data-features-using-t-sql.md) enthält eine Beschreibung dieser Tabellenwert Funktion.

Beide gespeicherten Prozeduren erstellen eine Bewertung auf der Grundlage des python-Modells.

> [!NOTE]
> 
> Es ist wichtig, dass Sie alle Eingabe Features bereitstellen, die für das python-Modell erforderlich sind, wenn Sie die gespeicherte Prozedur aus einer externen Anwendung abrufen. Um Fehler zu vermeiden, müssen Sie die Eingabedaten zusätzlich zum Validieren von Datentyp und Daten Länge in einen Python-Datentyp umwandeln oder konvertieren.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Nehmen Sie sich eine Minute Zeit, um den Code der gespeicherten Prozedur zu überprüfen, die die Bewertung mit dem **scikit-Learn-** Modell ausführt.

```sql
DROP PROCEDURE IF EXISTS PredictTipSingleModeSciKitPy;
GO

CREATE PROCEDURE [dbo].[PredictTipSingleModeSciKitPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
  SELECT * FROM [dbo].[fnEngineerFeatures]( 
    @passenger_count,
    @trip_distance,
    @trip_time_in_secs,
    @pickup_latitude,
    @pickup_longitude,
    @dropoff_latitude,
    @dropoff_longitude)
    '
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script 
  @language = N'Python',
  @script = N'
import pickle;
import numpy;

# Load model and unserialize
mod = pickle.loads(model)

# Get features for scoring from input data
X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]

# Score data to get tip prediction probability as a list (of float)
probList = []
probList.append((mod.predict_proba(X)[0])[1])

# Create output data frame
OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
',
  @input_data_1 = @inquery,
  @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
    @trip_time_in_secs int ,
    @pickup_latitude float ,
    @pickup_longitude float ,
    @dropoff_latitude float ,
    @dropoff_longitude float',
    @model = @lmodel2,
    @passenger_count =@passenger_count ,
    @trip_distance=@trip_distance,
    @trip_time_in_secs=@trip_time_in_secs,
    @pickup_latitude=@pickup_latitude,
    @pickup_longitude=@pickup_longitude,
    @dropoff_latitude=@dropoff_latitude,
    @dropoff_longitude=@dropoff_longitude
WITH RESULT SETS ((Score float));
END
GO
```

### <a name="predicttipsinglemoderxpy"></a>PredictTipSingleModeRxPy

Die folgende gespeicherte Prozedur führt die Bewertung mithilfe des **revoscalepy** -Modells aus.

```sql
DROP PROCEDURE IF EXISTS PredictTipSingleModeRxPy;
GO

CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
DECLARE @inquery nvarchar(max) = N'
  SELECT * FROM [dbo].[fnEngineerFeatures]( 
    @passenger_count,
    @trip_distance,
    @trip_time_in_secs,
    @pickup_latitude,
    @pickup_longitude,
    @dropoff_latitude,
    @dropoff_longitude)
  '
DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models where name = @model);
EXEC sp_execute_external_script 
  @language = N'Python',
  @script = N'
import pickle;
import numpy;
from revoscalepy.functions.RxPredict import rx_predict;

# Load model and unserialize
mod = pickle.loads(model)

# Get features for scoring from input data
X = InputDataSet[["passenger_count", "trip_distance", "trip_time_in_secs", "direct_distance"]]

# Score data to get tip prediction probability as a list (of float)

probArray = rx_predict(mod, X)

probList = []
probList = probArray["tipped_Pred"].values

# Create output data frame
OutputDataSet = pandas.DataFrame(data = probList, columns = ["predictions"])
',
  @input_data_1 = @inquery,
  @params = N'@model varbinary(max),@passenger_count int,@trip_distance float,
    @trip_time_in_secs int ,
    @pickup_latitude float ,
    @pickup_longitude float ,
    @dropoff_latitude float ,
    @dropoff_longitude float',
    @model = @lmodel2,
    @passenger_count =@passenger_count ,
    @trip_distance=@trip_distance,
    @trip_time_in_secs=@trip_time_in_secs,
    @pickup_latitude=@pickup_latitude,
    @pickup_longitude=@pickup_longitude,
    @dropoff_latitude=@dropoff_latitude,
    @dropoff_longitude=@dropoff_longitude
WITH RESULT SETS ((Score float));
END
GO
```

### <a name="generate-scores-from-models"></a>Generieren von Bewertungen aus Modellen

Nachdem die gespeicherten Prozeduren erstellt wurden, ist es einfach, eine Bewertung auf der Grundlage beider Modelle zu generieren. Öffnen Sie einfach ein neues **Abfrage** Fenster, und geben Sie Parameter für die einzelnen featurespalten ein, oder fügen Sie Sie ein. Die sieben erforderlichen Werte sind für diese featurespalten in der angegebenen Reihenfolge:
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. Führen Sie diese Anweisung aus, um eine Vorhersage mit dem **revoscalepy** -Modell zu generieren:
  
    ```sql
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. Führen Sie diese Anweisung aus, um mit dem **scikit-Learn-** Modell ein Ergebnis zu generieren:

    ```sql
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'SciKit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

Die Ausgabe beider Prozeduren ist eine Wahrscheinlichkeit, dass ein Trinkgeld für die Taxifahrt mit den angegebenen Parametern oder Features bezahlt wird.

## <a name="conclusions"></a>Schlussfolgerungen

In diesem Tutorial haben Sie gelernt, wie Sie mit Python-Code arbeiten, der in gespeicherten Prozeduren eingebettet ist. Durch die Integration [!INCLUDE[tsql](../../includes/tsql-md.md)] in wird das Bereitstellen von python-Modellen für Vorhersagen und das erneute Trainieren von Modellen im Rahmen eines Unternehmensdaten Workflows deutlich vereinfacht.

## <a name="previous-step"></a>Vorheriger Schritt

[Trainieren und Speichern eines python-Modells](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>Siehe auch

[Python-Erweiterung in SQL Server](../concepts/extension-python.md)
