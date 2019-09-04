---
title: 'Python-Tutorial: Modell bereitstellen (lineare Regression)'
description: In diesem Tutorial verwenden Sie die python-und lineare Regression in SQL Server Machine Learning Services, um die Anzahl der Ski-Vermietungen vorherzusagen. Mithilfe Machine Learning Services können Sie ein lineares Regressionsmodell, das in Python entwickelt wurde, in eine SQL Server Datenbank bereitstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 08f5d19af93ab180c660a264d5aaabc538d527a5
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242518"
---
# <a name="python-tutorial-deploy-a-linear-regression-model-to-sql-server-machine-learning-services"></a>Python-Tutorial: Stellen Sie ein lineares Regressionsmodell für SQL Server bereit Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im vierten Teil dieser vierteiligen tutorialreihe stellen Sie ein lineares Regressionsmodell, das in Python entwickelt wurde, mithilfe Machine Learning Services in einer SQL Server-Datenbank bereit.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen einer gespeicherten Prozedur, die das Machine Learning-Modell generiert
> * Speichern des Modells in einer Datenbanktabelle
> * Erstellen einer gespeicherten Prozedur, die Vorhersagen mithilfe des Modells erstellt
> * Ausführen des Modells mit neuen Daten

In [Teil 1](python-ski-rental-linear-regression.md)haben Sie gelernt, wie Sie die Beispieldatenbank wiederherstellen.

In [Teil 2](python-ski-rental-linear-regression-prepare-data.md)haben Sie gelernt, wie die Daten aus SQL Server in einen python-Datenrahmen geladen und die Daten in python vorbereitet werden.

In [Teil 3](python-ski-rental-linear-regression-train-model.md)haben Sie gelernt, wie Sie ein lineares Regressions Machine Learning-Modell in python trainieren.

## <a name="prerequisites"></a>Erforderliche Komponenten

* In Teil 4 dieses Tutorials wird davon ausgegangen, dass Sie [Teil eins](python-ski-rental-linear-regression.md) und seine Voraussetzungen erfüllt haben.

## <a name="create-a-stored-procedure-that-generates-the-model"></a>Erstellen einer gespeicherten Prozedur, die das Modell generiert

Erstellen Sie nun mithilfe der von Ihnen entwickelten python-Skripts eine gespeicherte Prozedur **generate_rental_rx_model** , die das lineare Regressionsmodell mithilfe von LinearRegression aus scikit-Learn trainiert und generiert.

Führen Sie die folgende T-SQL-Anweisung in Azure Data Studio aus, um die gespeicherte Prozedur zum Trainieren des Modells zu erstellen.

```sql
-- Stored procedure that trains and generates a Python model using the rental_data and a decision tree algorithm
DROP PROCEDURE IF EXISTS generate_rental_py_model;
go
CREATE PROCEDURE generate_rental_py_model (@trained_model varbinary(max) OUTPUT)
AS
BEGIN
    EXECUTE sp_execute_external_script
      @language = N'Python'
    , @script = N'
from sklearn.linear_model import LinearRegression
import pickle

df = rental_train_data

# Get all the columns from the dataframe.
columns = df.columns.tolist()

# Store the variable well be predicting on.
target = "RentalCount"

# Initialize the model class.
lin_model = LinearRegression()

# Fit the model to the training data.
lin_model.fit(df[columns], df[target])

# Before saving the model to the DB table, convert it to a binary object
trained_model = pickle.dumps(lin_model)'

, @input_data_1 = N'select "RentalCount", "Year", "Month", "Day", "WeekDay", "Snow", "Holiday" from dbo.rental_data where Year < 2015'
, @input_data_1_name = N'rental_train_data'
, @params = N'@trained_model varbinary(max) OUTPUT'
, @trained_model = @trained_model OUTPUT;
END;
GO
```

## <a name="store-the-model-in-a-database-table"></a>Speichern des Modells in einer Datenbanktabelle

Erstellen Sie eine Tabelle in der tutorialdb-Datenbank, und speichern Sie das Modell dann in der Tabelle.

1. Führen Sie die folgende T-SQL-Anweisung in Azure Data Studio aus, um eine Tabelle mit dem Namen **dbo. rental_py_models** zu erstellen, die zum Speichern des Modells verwendet wird.

    ```sql
    USE TutorialDB;
    DROP TABLE IF EXISTS dbo.rental_py_models;
    GO
    CREATE TABLE dbo.rental_py_models (
        model_name VARCHAR(30) NOT NULL DEFAULT('default model') PRIMARY KEY,
        model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

1. Speichern Sie das Modell in der Tabelle als binäres Objekt mit dem Modellnamen **linear_model**.

    ```sql
    DECLARE @model VARBINARY(MAX);
    EXEC generate_rental_py_model @model OUTPUT;
    
    INSERT INTO rental_py_models (model_name, model) VALUES('linear_model', @model);
    ```

## <a name="create-a-stored-procedure-that-makes-predictions"></a>Erstellen einer gespeicherten Prozedur, die Vorhersagen erstellt

1. Erstellen Sie eine gespeicherte Prozedur **py_predict_rentalcount** , die Vorhersagen mithilfe des trainierten Modells und eines Satzes neuer Daten trifft. Führen Sie den folgenden T-SQL-Server in Azure Data Studio aus.

    ```sql
    DROP PROCEDURE IF EXISTS py_predict_rentalcount;
    GO
    CREATE PROCEDURE py_predict_rentalcount (@model varchar(100))
    AS
    BEGIN
        DECLARE @py_model varbinary(max) = (select model from rental_py_models where model_name = @model);
    
        EXEC sp_execute_external_script
                    @language = N'Python',
                    @script = N'
    
    # Import the scikit-learn function to compute error.
    from sklearn.metrics import mean_squared_error
    import pickle
    import pandas as pd
    
    rental_model = pickle.loads(py_model)
    
    df = rental_score_data
    
    # Get all the columns from the dataframe.
    columns = df.columns.tolist()
    
    # Variable you will be predicting on.
    target = "RentalCount"
    
    # Generate the predictions for the test set.
    lin_predictions = rental_model.predict(df[columns])
    print(lin_predictions)
    
    # Compute error between the test predictions and the actual values.
    lin_mse = mean_squared_error(lin_predictions, df[target])
    #print(lin_mse)
    
    predictions_df = pd.DataFrame(lin_predictions)
    
    OutputDataSet = pd.concat([predictions_df, df["RentalCount"], df["Month"], df["Day"], df["WeekDay"], df["Snow"], df["Holiday"], df["Year"]], axis=1)
    '
    , @input_data_1 = N'Select "RentalCount", "Year" ,"Month", "Day", "WeekDay", "Snow", "Holiday"  from rental_data where Year = 2015'
    , @input_data_1_name = N'rental_score_data'
    , @params = N'@py_model varbinary(max)'
    , @py_model = @py_model
    with result sets (("RentalCount_Predicted" float, "RentalCount" float, "Month" float,"Day" float,"WeekDay" float,"Snow" float,"Holiday" float, "Year" float));
    
    END;
    GO
    ```

1. Erstellen Sie eine Tabelle zum Speichern der Vorhersagen.

    ```sql
    DROP TABLE IF EXISTS [dbo].[py_rental_predictions];
    GO

    CREATE TABLE [dbo].[py_rental_predictions](
     [RentalCount_Predicted] [int] NULL,
     [RentalCount_Actual] [int] NULL,
     [Month] [int] NULL,
     [Day] [int] NULL,
     [WeekDay] [int] NULL,
     [Snow] [int] NULL,
     [Holiday] [int] NULL,
     [Year] [int] NULL
    ) ON [PRIMARY]
    GO
    ```

1. Ausführen der gespeicherten Prozedur zum Vorhersagen der Anzahl von Vermietungen

    ```sql
    --Insert the results of the predictions for test set into a table
    INSERT INTO py_rental_predictions
    EXEC py_predict_rentalcount 'linear_model';

    -- Select contents of the table
    SELECT * FROM py_rental_predictions;
    ```

Sie haben erfolgreich ein Modell in einer SQL Server Machine Learning Services erstellt, trainiert und bereitgestellt. Anschließend haben Sie dieses Modell in einer gespeicherten Prozedur verwendet, um Werte basierend auf neuen Daten vorherzusagen.

## <a name="next-steps"></a>Nächste Schritte

Im vierten Teil dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Erstellen einer gespeicherten Prozedur, die das Machine Learning-Modell generiert
* Speichern des Modells in einer Datenbanktabelle
* Erstellen einer gespeicherten Prozedur, die Vorhersagen mithilfe des Modells erstellt
* Ausführen des Modells mit neuen Daten

Weitere Informationen zur Verwendung von python in SQL Server Machine Learning Services finden Sie unter:

+ [Python-Tutorials für SQL Server Machine Learning Services](sql-server-python-tutorials.md)