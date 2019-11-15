---
title: 'Python-Tutorial: Vorbereiten von Daten'
description: In diesem Tutorial verwenden Sie Python und die lineare Regression in SQL Server-Machine Learning Services zur Vorhersage von Verleihzahlen für einen Skiverleih. Sie bereiten Daten aus einer SQL Server-Datenbank mithilfe von Python vor.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6424a453bff2f0f6d62caa8c9870ccc2ec10d578
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727054"
---
# <a name="python-tutorial-prepare-data-to-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Python-Tutorial: Vorbereiten von Daten zum Trainieren eines linearen Regressionsmodells in SQL Server-Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im zweiten Teil dieser vierteiligen Tutorialreihe bereiten Sie Daten aus einer SQL Server-Datenbank mithilfe von Python vor. Diese Daten verwenden Sie in einem späteren Teil dieser Reihe zum Trainieren und Bereitstellen eines linearen Regressionsmodells in Python mit SQL Server-Machine Learning Services.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Laden der Daten aus der SQL Server-Datenbank in einen **Pandas**-Datenrahmen
> * Vorbereiten der Daten in Python durch Entfernen einiger Spalten

In [Teil 1](python-ski-rental-linear-regression.md) dieser Tutorialreihe haben Sie gelernt, wie Sie die Beispieldatenbank wiederherstellen.

In [Teil 3](python-ski-rental-linear-regression-train-model.md) trainieren Sie ein lineares Regressionsmodell für Machine Learning in Python.

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md) wird beschrieben, wie Sie das Modell in SQL Server speichern und gespeicherte Prozeduren aus den Python-Skripts erstellen, die Sie in Teil 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden in SQL Server ausgeführt, um Vorhersagen basierend auf neuen Daten treffen zu können.

## <a name="prerequisites"></a>Voraussetzungen

* In diesem Teil der Tutorialreihe wird davon ausgegangen, dass Sie [Teil 1](python-ski-rental-linear-regression.md) und die erforderlichen Voraussetzungen abgeschlossen haben.

## <a name="explore-and-prepare-the-data"></a>Durchsuchen und Vorbereiten der Daten

Laden Sie die Daten aus der SQL Server-Datenbank in einen Pandas-Datenrahmen, um sie in Python verwenden zu können.

Erstellen Sie in Azure Data Studio ein neues Python-Notebook, und führen Sie das folgende Skript aus. Ersetzen Sie `<SQL Server>` durch Ihren eigenen SQL Server-Namen.

Importieren Sie mit dem folgenden Python-Skript das Dataset aus der Tabelle **dbo.rental_data** in Ihrer Datenbank in den Pandas-Datenrahmen **df**:

```python
import pandas as pd
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
from revoscalepy import RxComputeContext, RxInSqlServer, RxSqlServerData
from revoscalepy import rx_import

# Connection string to your SQL Server instance
conn_str = 'Driver=SQL Server;Server=<SQL Server>;Database=TutorialDB;Trusted_Connection=True;'

# Define the columns you will import
 column_info = {
         "Year" : { "type" : "integer" },
         "Month" : { "type" : "integer" },
         "Day" : { "type" : "integer" },
         "RentalCount" : { "type" : "integer" },
         "WeekDay" : {
             "type" : "factor",
             "levels" : ["1", "2", "3", "4", "5", "6", "7"]
         },
         "Holiday" : {
             "type" : "factor",
             "levels" : ["1", "0"]
         },
         "Snow" : {
             "type" : "factor",
             "levels" : ["1", "0"]
         }
     }

# Get the data from the SQL Server table
data_source = RxSqlServerData(table="dbo.rental_data",
                               connection_string=conn_str, column_info=column_info)
computeContext = RxInSqlServer(
     connection_string = conn_str,
     num_tasks = 1,
     auto_cleanup = False
)

RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)

# import data source and convert to pandas dataframe
df = pd.DataFrame(rx_import(input_data = data_source))
print("Data frame:", df)

# Get all the columns from the dataframe.
columns = df.columns.tolist()

# Filter the columns to remove ones we don't want to use in the training
columns = [c for c in columns if c not in ["Year"]]
```

Das Ergebnis sollte etwa folgendermaßen aussehen:

```results
Rows Processed: 453
Data frame:      Day  Holiday  Month  RentalCount  Snow  WeekDay  Year
0     20        1      1          445     2        2  2014
1     13        2      2           40     2        5  2014
2     10        2      3          456     2        1  2013
3     31        2      3           38     2        2  2014
4     24        2      4           23     2        5  2014
5     11        2      2           42     2        4  2015
6     28        2      4          310     2        1  2013
...
[453 rows x 7 columns]
```

## <a name="next-steps"></a>Nächste Schritte

Im zweiten Teil dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Laden der Daten aus der SQL Server-Datenbank in einen **Pandas**-Datenrahmen
* Vorbereiten der Daten in Python durch Entfernen einiger Spalten

Fahren Sie mit Teil 3 dieser Tutorialreihe fort, um ein Machine Learning-Modell zu trainieren, das Daten aus der Datenbank „TutorialDB“ verwendet:

> [!div class="nextstepaction"]
> [Python-Tutorial: Trainieren eines linearen Regressionsmodells](python-ski-rental-linear-regression-train-model.md)