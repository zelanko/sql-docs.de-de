---
title: 'Tutorial zu R und Transact-SQL: Trainieren des Modells'
description: In diesem Tutorial wird gezeigt, wie ein R-Modell mithilfe von gespeicherten Prozeduren in SQL Server und T-SQL-Funktionen trainiert, serialisiert und gespeichert wird.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/16/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ada26cbf8091b7e7b29e22378be5aa5f2b880314
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725233"
---
# <a name="lesson-3-train-and-save-a-model-using-t-sql"></a>Lektion 3: Trainieren und Speichern eines Modells mit T-SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Dieser Artikel ist Teil eines Tutorials für SQL-Entwickler zur Verwendung von R in SQL Server.

In dieser Lerneinheit erfahren Sie, wie Sie ein Machine Learning-Modell mit R trainieren. Sie trainieren das Modell mit den Datenfunktionen, die Sie in der vorherigen Lerneinheit erstellt haben, und speichern das trainierte Modell dann in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Tabelle. In diesem Fall sind die R-Pakete bereits mit [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] installiert, sodass alles über SQL ausgeführt werden kann.

## <a name="create-the-stored-procedure"></a>Erstellen der gespeicherten Prozedur

Wenn Sie R über T-SQL aufrufen, verwenden Sie die im System gespeicherte Prozedur [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Für Prozesse, die Sie häufig wiederholen, wie z. B. das erneute Trainieren eines Modells, ist es jedoch einfacher, den Aufruf von „sp_execute_exernal_script“ in einer anderen gespeicherten Prozedur einzuschließen.

1. Öffnen Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] ein neues Fenster **Abfrage**.

2. Führen Sie die folgende Anweisung aus, um die gespeicherte Prozedur **RxTrainLogitModel** zu erstellen. Diese gespeicherte Prozedur definiert die Eingabedaten und verwendet **rxLogit** aus RevoScaleR, um ein logistisches Regressionsmodell zu erstellen.

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

    - Um sicherzustellen, dass einige Daten zum Testen des Modells übrig bleiben, werden 70 % der Daten aus der Datentabelle „Taxi“ zu Trainingszwecken nach dem Zufallsprinzip ausgewählt.

    - Die SELECT-Abfrage verwendet die benutzerdefinierte Skalarfunktion *fnCalculateDistance* zum Berechnen der direkten Entfernung zwischen den Abhol- und Zielorten. Die Ergebnisse der Abfrage werden in der Standardeingabevariable von R, `InputDataset`, gespeichert.
  
    - Das R-Skript ruft die **rxLogit**-Funktion auf, die Teil der erweiterten R-Funktionen ist, die in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] enthalten sind, um das logistische Regressionsmodell zu erstellen.
  
        Die binäre Variable _tipped_ dient als die Spalte *label* oder „outcome“, und das Modell wird mithilfe folgender Funktionsspalten angepasst:  _passenger_count_, _trip_distance_, _trip_time_in_secs_und _direct_distance_.
  
    - Das trainierte Modell, das in der R-Variablen `logitObj` gespeichert ist, wird serialisiert und als Ausgabeparameter zurückgegeben.

## <a name="train-and-deploy-the-r-model-using-the-stored-procedure"></a>Trainieren und Bereitstellen des R-Modells mithilfe der gespeicherten Prozedur

Da die gespeicherte Prozedur schon eine Definition der Eingabedaten enthält, müssen Sie keine Eingabeabfrage bereitstellen.

1. Um das R-Modell zu trainieren und bereitzustellen, rufen Sie die gespeicherte Prozedur auf und fügen sie in die Datenbanktabelle _nyc_taxi_models_ ein, sodass Sie sie für zukünftige Vorhersagen verwenden können:

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC RxTrainLogitModel @model OUTPUT;
    INSERT INTO nyc_taxi_models (name, model) VALUES('RxTrainLogit_model', @model);
    ```

2. Nachrichten, die an den **stdout**-Stream von R weitergeleitet werden würden, werden im Fenster [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]Meldungen**von** angezeigt: 

    "STDOUT message(s) from external script: Gelesene Zeilen: 1193025, Total Rows Processed: 1193025, Total Chunk Time: 0.093 seconds"

    Darüber hinaus werden möglicherweise Meldungen angezeigt, die für die individuelle Funktion `rxLogit` spezifisch sind und die bei der Modellerstellung generierte Variablen und Testmetriken angeben.

3.  Wenn die Anweisung abgeschlossen ist, öffnen Sie die Tabelle *nyc_taxi_models*. Die Verarbeitung der Daten und die Anpassung des Modells können eine Weile dauern.

    Sie können sehen, dass eine neue Zeile hinzugefügt wurde, die das serialisierte Modell in der Spalte _model_ und den Modellnamen **RxTrainLogit_model** in der Spalte _name_ enthält.

    ```sql
    model                        name
    ---------------------------- ------------------
    0x580A00000002000302020....  RxTrainLogit_model
    ```

Im nächsten Schritt verwenden Sie das trainierte Modell zum Erstellen von Vorhersagen.

## <a name="next-lesson"></a>Nächste Lektion

[Lektion 4: Vorhersagen potenzieller Ergebnisse mithilfe eines R-Modells in einer gespeicherten Prozedur](../tutorials/sqldev-operationalize-the-model.md)

## <a name="previous-lesson"></a>Vorherige Lerneinheit

[Lektion 2: Erstellen von Datenfeatures mit R in T-SQL-Funktionen](..//tutorials/sqldev-create-data-features-using-t-sql.md)

