---
title: Lektion 3 trainieren und Speichern eines Modells mit R und T-SQL – SQL Server-Machine Learning
description: Tutorial zum Trainieren, serialisieren und Speichern eines R-Modells gespeicherten mithilfe von SQL Server, Prozeduren und T-SQL-Funktionen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f3abe58aac4d5920e64337f63a40dc8f87fb12d9
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645109"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Lektion 3: Trainieren und Speichern eines Modells mit T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In dieser Lektion erfahren Sie, wie Sie ein Machine Learning-Modell zu trainieren, indem Sie mit R. Sie Trainieren des Modells mit den Datenfeatures, die Sie in der vorherigen Lektion erstellt haben, und speichern Sie das trainierte Modell in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle. In diesem Fall sind die R-Pakete bereits installiert mit [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], sodass Sie alles über SQL erfolgen kann.

## <a name="create-the-stored-procedure"></a>Die gespeicherte Prozedur erstellen

Beim Aufrufen von R von T-SQL verwenden Sie die gespeicherte Systemprozedur, [Sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Für Prozesse, die Sie häufig wiederholen, wie z. B. das erneute Trainieren eines Modells ist es jedoch einfacher, den Aufruf von Sp_execute_exernal_script in eine andere gespeicherte Prozedur zu kapseln.

1. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], öffnen Sie ein neues **Abfrage** Fenster.

2. Führen Sie die folgende Anweisung zum Erstellen der gespeicherten Prozedur **RxTrainLogitModel**. Diese gespeicherte Prozedur definiert die Eingabedaten und verwendet **RxLogit** von RevoScaleR, um ein Logistisches Regressionsmodell zu erstellen.

    ```sql
    CREATE PROCEDURE [dbo].[RxTrainLogitModel] (@trained_model varbinary(max) OUTPUT)
    
    AS
    BEGIN
      DECLARE @inquery nvarchar(max) = N'
        select tipped, fare_amount, passenger_count,trip_time_in_secs,trip_distance,
        pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
        from nyctaxi_sample
        tablesample (70 percent) repeatable (98052)
    '
    
      EXEC sp_execute_external_script @language = N'R',
                                      @script = N'
    ## Create model
    logitObj <- rxLogit(tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance, data = InputDataSet)
    summary(logitObj)
    
    ## Serialize model 
    trained_model <- as.raw(serialize(logitObj, NULL));
    ',
      @input_data_1 = @inquery,
      @params = N'@trained_model varbinary(max) OUTPUT',
      @trained_model = @trained_model OUTPUT; 
    END
    GO
    ```

    - Um sicherzustellen, dass einige Daten zum Testen des Modells übrig bleibt, werden 70 % der Daten aus der Datentabelle "Taxi" für trainingszwecke nach dem Zufallsprinzip ausgewählt.

    - Die SELECT-Abfrage verwendet die benutzerdefinierte Skalarfunktion *fnCalculateDistance* zum Berechnen der direkten Entfernung zwischen den Abhol- und Zielorten. die Ergebnisse der Abfrage werden in der Eingabe standardmäßigen R-Variable gespeichert `InputDataset`.
  
    - Ruft das R-Skript die **RxLogit** -Funktion, die eine der erweiterten R-Funktionen ist in enthaltenen [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], um das logistische Regressionsmodell zu erstellen.
  
        Die binäre Variable _tipped_ dient als die Spalte *label* oder „outcome“, und das Modell wird mithilfe folgender Funktionsspalten angepasst:  _passenger_count_, _trip_distance_, _trip_time_in_secs_und _direct_distance_.
  
    - Das trainierte Modell, in der R-Variablen gespeicherte `logitObj`, wird serialisiert und als ein Ausgabeparameter zurückgegeben.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Trainieren Sie und Bereitstellen Sie des R-Modells mithilfe der gespeicherten Prozedur

Da die gespeicherte Prozedur bereits eine Definition der Eingabedaten enthält, müssen Sie keine Eingabeabfrage bereitstellen.

1. Zum Trainieren und das R-Modell bereitgestellt haben, rufen Sie die gespeicherte Prozedur, und fügen Sie es in der Datenbanktabelle _Nyc_taxi_models_, sodass Sie es für zukünftige Vorhersagen verwenden können:

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Sehen Sie sich die **Nachrichten** Fenster [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] für Nachrichten, die an die R weitergeleitet werden würden **"stdout"** Stream, wie diese Meldung: 

    "Stdout-Meldung(en) aus dem externen Skript: Gelesene Zeilen: 1193025, Ergebniszeilen verarbeitet: 1193025, total Chunk Time: 0.093 Seconds"

    Möglicherweise werden auch Nachrichten, die spezifisch für die individuelle Funktion angezeigt `rxLogit`, die Variablen anzeigen und Testen Sie die Metriken, die als Teil der Erstellung des Modells generiert.

3.  Wenn die Anweisung abgeschlossen ist, öffnen Sie die Tabelle *Nyc_taxi_models*. Die Verarbeitung der Daten und Anpassung des Modells können eine Weile dauern.

    Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte enthält _Modell_ und der Name des Modells **RxTrainLogit_model** in der Spalte _Namen_.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

Im nächsten Schritt verwenden Sie das trainierte Modell zum Vorhersagen zu generieren.

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 4: Vorhersagen von möglichen Ergebnissen, die mithilfe eines R-Modells in einer gespeicherten Prozedur](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 2: Erstellen von Datenfunktionen mit R und T-SQL-Funktionen](..//tutorials/sqldev-create-data-features-using-t-sql.md)

