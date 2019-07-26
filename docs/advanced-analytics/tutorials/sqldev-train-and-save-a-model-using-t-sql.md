---
title: 'Lektion 3: trainieren und Speichern eines Modells mit R und T-SQL'
description: Tutorial, das das trainieren, serialisieren und Speichern eines R-Modells mithilfe SQL Server gespeicherter Prozeduren und T-SQL-Funktionen veranschaulicht.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0825d99aee2639d28e95dfcaf79e1a8e915bf25a
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470533"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Lektion 3: Trainieren und Speichern eines Modells mit T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In dieser Lektion erfahren Sie, wie Sie ein Machine Learning-Modell mithilfe von R trainieren. Trainieren Sie das Modell mithilfe der Datenfunktionen, die Sie in der vorherigen Lektion erstellt haben, und speichern Sie dann das trainierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Modell in einer Tabelle. In diesem Fall sind die R-Pakete bereits mit [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]installiert, sodass alles von SQL ausgeführt werden kann.

## <a name="create-the-stored-procedure"></a>Erstellen der gespeicherten Prozedur

Wenn Sie R von T-SQL aufrufen, verwenden Sie die gespeicherte System Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Für Prozesse, die Sie häufig wiederholen, z. b. das erneute Trainieren eines Modells, ist es jedoch einfacher, den sp_execute_exernal_script-Aufrufvorgang in einer anderen gespeicherten Prozedur zu kapseln.

1. Öffnen [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Sie in ein neues **Abfrage** Fenster.

2. Führen Sie die folgende Anweisung aus, um die gespeicherte Prozedur " **rxtrainlogitmodel**" zu erstellen. Diese gespeicherte Prozedur definiert die Eingabedaten und verwendet **rxlogit** von revoscaler, um ein logistisches Regressionsmodell zu erstellen.

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

    - Um sicherzustellen, dass einige Daten zum Testen des Modells übrig bleiben, werden 70% der Daten für Trainingszwecke nach dem Zufallsprinzip aus der Taxi-Datentabelle ausgewählt.

    - Die SELECT-Abfrage verwendet die benutzerdefinierte Skalarfunktion *fnCalculateDistance* zum Berechnen der direkten Entfernung zwischen den Abhol- und Zielorten. Die Ergebnisse der Abfrage werden in der Standard-R-Eingabevariablen, `InputDataset`, gespeichert.
  
    - Das R-Skript ruft die **rxlogit** -Funktion auf, die eine der in enthaltenen [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]erweiterten R-Funktionen ist, um das logistische Regressionsmodell zu erstellen.
  
        Die binäre Variable _tipped_ dient als die Spalte *label* oder „outcome“, und das Modell wird mithilfe folgender Funktionsspalten angepasst:  _passenger_count_, _trip_distance_, _trip_time_in_secs_und _direct_distance_.
  
    - Das trainierte Modell, das in der R- `logitObj`Variablen gespeichert ist, wird serialisiert und als Output-Parameter zurückgegeben.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Trainieren und Bereitstellen des R-Modells mithilfe der gespeicherten Prozedur

Da die gespeicherte Prozedur bereits eine Definition der Eingabedaten enthält, ist es nicht erforderlich, eine Eingabe Abfrage bereitzustellen.

1. Um das R-Modell zu trainieren und bereitzustellen, nennen Sie die gespeicherte Prozedur, und fügen Sie Sie in die Datenbanktabelle _nyc_taxi_models_ein, damit Sie Sie für zukünftige Vorhersagen verwenden können:

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Sehen Sie  sich das Fenster [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Meldungen von für Nachrichten an, die an den **stdout** -Datenstrom von R weitergeleitet werden, wie in der folgenden Meldung: 

    "Stdout-Meldung (en) aus dem externen Skript: Gelesene Zeilen: 1193025, verarbeitete Zeilen gesamt: 1193025, gesamte Segment Zeit: 0,093 Sekunden "

    Möglicherweise werden auch Nachrichten angezeigt, `rxLogit`die für die jeweilige Funktion spezifisch sind, und die Variablen und Testmetriken anzeigen, die im Rahmen der Modell Erstellung generiert werden.

3.  Wenn die Anweisung abgeschlossen ist, öffnen Sie die Tabelle *nyc_taxi_models*. Die Verarbeitung der Daten und die Anpassung des Modells kann einige Zeit in Anspruch nehmen.

    Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell im Spalten _Modell_ und den Modellnamen **RxTrainLogit_model** im Spalten _Namen_enthält.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

Im nächsten Schritt verwenden Sie das trainierte Modell, um Vorhersagen zu generieren.

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 4: Vorhersagen potenzieller Ergebnisse mithilfe eines R-Modells in einer gespeicherten Prozedur](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Vorherige Lektion

[Lektion 2: Erstellen von Datenfunktionen mithilfe von R-und T-SQL-Funktionen](..//tutorials/sqldev-create-data-features-using-t-sql.md)

