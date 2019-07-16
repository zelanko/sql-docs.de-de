---
title: Vorhersagen von möglichen Ergebnissen, die mithilfe von Python-Modelle – SQL Server-Machine Learning
description: Veranschaulicht, wie zum operationalisieren von eingebetteten PYthon-Skript in SQL Server gespeicherte Prozeduren mit T-SQL-Funktionen
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/02/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: e5f88beb2c429091fcea8ce66e4defa291e718d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961848"
---
# <a name="run-predictions-using-python-embedded-in-a-stored-procedure"></a>Führen Sie Vorhersagen mithilfe von Python in einer gespeicherten Prozedur eingebettet
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials, [In-Database Python Analytics für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md). 

In diesem Schritt erfahren Sie, wie *operationalisieren* die Modelle, die Sie trainiert und im vorherigen Schritt gespeichert haben.

In diesem Szenario bedeutet die operationalisierung des Modells in einer produktionsumgebung, für die Bewertung bereitstellen. Die Integration in SQL Server dadurch recht einfach, da Sie Python-Code in einer gespeicherten Prozedur einbetten können. Um Vorhersagen aus dem Modell basierend auf neue Eingaben zu erhalten, rufen Sie die gespeicherte Prozedur von einer Anwendung, und übergeben Sie die neuen Daten.

In dieser Lektion wird veranschaulicht, zwei Methoden zum Erstellen von Vorhersagen auf Grundlage eines Python-Modells: batch-Bewertung und bewerten die Zeile für Zeile.

- **Batchbewertung:** Um mehrere Zeilen von Eingabedaten zu gewährleisten, übergeben Sie eine SELECT-Abfrage als Argument an die gespeicherte Prozedur ein. Das Ergebnis ist eine Tabelle mit Beobachtungen mit den Eingabefällen entspricht.
- **Einzelne Bewertung:** Übergeben Sie einen Satz von einzelnen Parameterwerten als Eingabe an.  Die gespeicherte Prozedur gibt eine einzelne Zeile oder einen Wert zurück.

Alle Python-Code, die erforderlich sind, für die Bewertung wird als Teil der gespeicherten Prozeduren bereitgestellt.

## <a name="batch-scoring"></a>Batchbewertung

Die ersten beiden gespeicherten Prozeduren veranschaulicht die grundlegende Syntax für das Umschließen eines vorhersageaufrufs Python in einer gespeicherten Prozedur. Beide gespeicherten Prozeduren erfordern eine Tabelle mit Daten als Eingabe an.

- Die genauen Modellnamen verwenden, wird als Eingabeparameter an die gespeicherte Prozedur bereitgestellt. Die gespeicherte Prozedur lädt das serialisierte Modell aus der Datenbanktabelle `nyc_taxi_models`.table, verwenden die SELECT-Anweisung in der gespeicherten Prozedur.
- Das serialisierte Modell wird in der Python-Variable gespeicherte `mod` zur weiteren Verarbeitung mithilfe von Python.
- Die neue Fälle, die bewertet werden müssen, erhalten Sie vom der [!INCLUDE[tsql](../../includes/tsql-md.md)] in angegebene Abfrage `@input_data_1`. Wenn die Abfragedaten gelesen werden, werden die Zeilen im Standard-Datenrahmen, `InputDataSet`, gespeichert.
- Sowohl gespeicherte Prozedur verwenden Funktionen von `sklearn` um eine genauigkeitsmetrik, AUC (Bereich unter der Kurve) zu berechnen. Genauigkeitsmetriken wie z. B. AUC können nur generiert, wenn Sie auch die Zielmarke angeben (die _"tipped"_ Spalte). Vorhersagen ist nicht erforderlich, die zielbezeichnung (Variable `y`), jedoch die Berechnung der Genauigkeit-Metrik.

    Aus diesem Grund, wenn Sie nicht, dass die Ziel-Bezeichnungen für Daten haben, die bewertet werden, Sie können ändern, die gespeicherte Prozedur, um die AUC-Berechnungen zu entfernen und nur die Tip-Wahrscheinlichkeiten zurückgeben, von den Funktionen (Variablen `X` in der gespeicherten Prozedur).

### <a name="predicttipscikitpy"></a>PredictTipSciKitPy

Exportspezifikation aus den folgenden T-SQL-Anweisungen, um die gespeicherten Prozeduren zu erstellen. Diese gespeicherte Prozedur erfordert ein Modell basierend auf der Scikit-Paket, erfahren Sie, da es sich um Funktionen, die spezifisch für das Paket verwendet:

+ Der Datenrahmen, der mit Eingaben übergeben wird, um die `predict_proba` Funktion das logistische Regressionsmodell `mod`. Die `predict_proba` Funktion (`probArray = mod.predict_proba(X)`) gibt eine **"float"** , die die Wahrscheinlichkeit, die gewährt wird, ein Trinkgeld (beliebige Höhe) darstellt.

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

### <a name="predicttiprxpy"></a>PredictTipRxPy

Diese gespeicherte Prozedur verwendet die gleichen Eingaben und die gleiche Art von Bewertungen als die vorherige gespeicherte Prozedur erstellt, aber es werden Funktionen aus der **Revoscalepy** Paket mit SQL Server-Machine Learning bereitgestellt.

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

## <a name="run-batch-scoring-using-a-select-query"></a>Führen Sie die batchbewertung mithilfe einer SELECT-Abfrage

Die gespeicherten Prozeduren **PredictTipSciKitPy** und **PredictTipRxPy** erfordert zwei Eingabeparameter: 

- Die Abfrage, die die Daten für die Bewertung abruft
- Der Name eines trainierten Modells

Durch die Übergabe dieser Argumente an die gespeicherte Prozedur, können Sie wählen Sie ein bestimmtes Modell oder ändern die Daten, die für die Bewertung verwendet.

1. Verwenden der **Scikit-erfahren Sie,** für die Bewertung zu modellieren, rufen Sie die gespeicherte Prozedur **PredictTipSciKitPy**, übergeben Sie den Modellnamen und Abfragezeichenfolge als Eingaben.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipSciKitPy] 'SciKit_model', @query_string;
    ```

    Die gespeicherte Prozedur gibt die vorhergesagte Wahrscheinlichkeiten für jede Fahrt, die als Teil der Eingabeabfrage übergeben wurde. 
    
    Wenn Sie SSMS (SQL Server Management Studio) zum Ausführen von Abfragen verwenden, erscheint die Wahrscheinlichkeiten als Tabelle in der **Ergebnisse** Bereich. Die **Nachrichten** Bereich gibt die genauigkeitsmetrik (AUC oder Fläche unter der Kurve) mit einem Wert von ca. 0.56.

2. Verwenden der **Revoscalepy** für die Bewertung zu modellieren, rufen Sie die gespeicherte Prozedur **PredictTipRxPy**, übergeben Sie den Modellnamen und Abfragezeichenfolge als Eingaben.

    ```sql
    DECLARE @query_string nvarchar(max) -- Specify input query
      SET @query_string='
      select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance,
      dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
      from nyctaxi_sample_testing'
    EXEC [dbo].[PredictTipRxPy] 'revoscalepy_model', @query_string;
    ```

## <a name="single-row-scoring"></a>Bewertung der einzelnen Zeile

In einigen Fällen-Batch-Bewertungen, empfiehlt für die Übergabe in einem einzigen Gehäuse, Abrufen von Werten aus einer Anwendung, und ein einzelnes Resultset basierend auf diesen Werten. Beispielsweise könnten Sie Einrichten einer Excel-Arbeitsblatt, Webanwendung oder Bericht zum Aufrufen der gespeicherten Prozedur, und übergeben Sie es Eingaben eingegebenen oder ausgewählten Benutzer.

In diesem Abschnitt erfahren Sie, wie Sie einzelne Vorhersagen zu erstellen, indem zwei gespeicherten Prozeduren aufrufen:

+ [PredictTipSingleModeSciKitPy](#predicttipsinglemodescikitpy) dient für die einzelnen Zeile Bewertung Verwendung der Scikit-Modell zu erfahren.
+ [PredictTipSingleModeRxPy](#predicttipsinglemoderxpy) für die einzelnen Zeile Bewertung mit dem Revoscalepy-Modell dient.
+ Wenn Sie noch nicht getan haben ein Modell trainiert, wiederherstellen, [Schritt 5](sqldev-py5-train-and-save-a-model-using-t-sql.md)!

Beide Modelle Take als Eingabe eine Reihe von einzelnen Werten, z. B. die Anzahl der Fahrgäste, Fahrtstrecke und So weiter. Eine Funktion mit Tabellenrückgabe `fnEngineerFeatures`, wird verwendet, um Werte für Breiten- und Längengrad zu konvertieren, aus den Eingaben ein neues Feature, die direkte Entfernung. [Lektion 4](sqldev-py4-create-data-features-using-t-sql.md) enthält eine Beschreibung dieser Funktion mit Tabellenrückgabe.

Beide gespeicherten Prozeduren erstellen Sie eine Bewertung, die basierend auf dem Python-Modell.

> [!NOTE]
> 
> Es ist wichtig, dass Sie angeben, dass alle die eingegebenen Merkmale, die von der Python-Modell erforderlich ist, wenn Sie die gespeicherte Prozedur aus einer externen Anwendung aufrufen. Um Fehler zu vermeiden, müssen Sie die umwandeln oder konvertieren die Eingabedaten in einem Python-Datentyp, zusätzlich zum Überprüfen von Datentypen und die Datenlänge.

### <a name="predicttipsinglemodescikitpy"></a>PredictTipSingleModeSciKitPy

Kurz den Code der gespeicherten Prozedur zu überprüfen, der ausführt, Bewertung mithilfe der **Scikit-erfahren Sie,** Modell.

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

Die folgende gespeicherte Prozedur führt Bewertungen mithilfe der **Revoscalepy** Modell.

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

Nachdem Sie die gespeicherten Prozeduren erstellt wurden, ist es einfach, eine Bewertung anhand von beider Modelle zu generieren. Öffnen Sie einfach ein neues **Abfrage** Fenster, und geben oder fügen Sie Parameter für jeden der merkmalspalten. Die sieben erforderlich, dass die Werte für diese Funktionsspalten, in der Reihenfolge:
    
+ *passenger_count*
+ *trip_distance* v*trip_time_in_secs*
+ *pickup_latitude*
+ *pickup_longitude*
+ *dropoff_latitude*
+ *dropoff_longitude*

1. Generieren Sie eine Vorhersage mithilfe der **Revoscalepy** Modell, und führen Sie diese Anweisung:
  
    ```sql
    EXEC [dbo].[PredictTipSingleModeRxPy] 'revoscalepy_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

2. Generieren Sie eine Bewertung mithilfe der **Scikit-erfahren Sie,** Modell, und führen Sie diese Anweisung:

    ```sql
    EXEC [dbo].[PredictTipSingleModeSciKitPy] 'SciKit_model', 1, 2.5, 631, 40.763958,-73.973373, 40.782139,-73.977303
    ```

Die Ausgabe von beiden Verfahren ist die Wahrscheinlichkeit des eine trinkgeldbereichs für die taxifahrten mit den angegebenen Parametern oder Funktionen.

## <a name="conclusions"></a>Schlussfolgerungen

In diesem Tutorial haben Sie gelernt, wie zum Arbeiten mit Python-Code in gespeicherten Prozeduren eingebettet wird. Die Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)] macht es viel einfacher, Python-Modelle für Vorhersagen bereitzustellen und erneutes Trainieren von Modellen im Rahmen dieses Workflows ein Enterprise-Daten zu integrieren.

## <a name="previous-step"></a>Vorherigen Schritt

[Trainieren Sie und speichern Sie ein Python-Modell](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="see-also"></a>Siehe auch

[Python-Erweiterung in SQL Server](../concepts/extension-python.md)
