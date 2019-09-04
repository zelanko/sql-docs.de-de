---
title: 'Python-Tutorial: Vorbereiten von Daten (lineare Regression)'
description: In diesem Tutorial verwenden Sie die python-und lineare Regression in SQL Server Machine Learning Services, um die Anzahl der Ski-Vermietungen vorherzusagen. Sie bereiten Daten mithilfe von python aus einer SQL Server-Datenbank vor.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c6c4d5fb4ffc5049f7e1325267b7623dc195e9d8
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242498"
---
# <a name="python-tutorial-prepare-data-to-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Python-Tutorial: Vorbereiten von Daten zum Trainieren eines linearen Regressionsmodells in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im Teil 2 dieser vierteiligen tutorialreihe bereiten Sie Daten aus einer SQL Server-Datenbank mithilfe von python vor. Später in dieser Reihe verwenden Sie diese Daten zum trainieren und Bereitstellen eines linearen Regressionsmodells in Python mit SQL Server Machine Learning Services.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Laden der Daten aus der SQL Server-Datenbank in ein **Pandas** -Datenrahmen
> * Bereiten Sie die Daten in python vor, indem Sie einige Spalten entfernen.

In [Teil 1](python-ski-rental-linear-regression.md)haben Sie gelernt, wie Sie die Beispieldatenbank wiederherstellen.

In [Teil 3](python-ski-rental-linear-regression-train-model.md)erfahren Sie, wie Sie ein lineares Regressionsmodell für Maschinelles Lernen in python trainieren.

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md)erfahren Sie, wie Sie das Modell in SQL Server speichern und dann gespeicherte Prozeduren aus den python-Skripts erstellen, die Sie in den Teilen 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden in SQL Server ausgeführt, um Vorhersagen basierend auf neuen Daten zu treffen.

## <a name="prerequisites"></a>Erforderliche Komponenten

* In Teil 2 dieses Tutorials wird davon ausgegangen, dass Sie [Teil eins](python-ski-rental-linear-regression.md) und seine Voraussetzungen erfüllt haben.

## <a name="explore-and-prepare-the-data"></a>Untersuchen und Vorbereiten der Daten

Um die Daten in Python zu verwenden, laden Sie die Daten aus der SQL Server-Datenbank in ein Pandas-Datenrahmen.

Erstellen Sie ein neues python-Notebook in Azure Data Studio, und führen Sie das folgende Skript aus. Ersetzen `<SQL Server>` Sie durch ihren eigenen SQL Server Namen.

Mit dem folgenden Python-Skript wird das DataSet aus der **dbo. rental_data** -Tabelle in der-Datenbank in eine Pandas-Datenrahmen- **DF**importiert.

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

Es sollten ähnliche Ergebnisse wie die folgenden angezeigt werden.

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

Im Teil 2 dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Laden der Daten aus der SQL Server-Datenbank in ein **Pandas** -Datenrahmen
* Bereiten Sie die Daten in python vor, indem Sie einige Spalten entfernen.

Zum Trainieren eines Machine Learning-Modells, das Daten aus der tutorialdb-Datenbank verwendet, führen Sie die folgenden drei Schritte aus:

> [!div class="nextstepaction"]
> [Python-Tutorial: Trainieren eines linearen Regressionsmodells](python-ski-rental-linear-regression-train-model.md)