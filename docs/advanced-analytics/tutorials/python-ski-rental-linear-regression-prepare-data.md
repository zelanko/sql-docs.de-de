---
title: 'Python-Tutorial: Vorbereiten von Daten'
description: Im zweiten Teil dieser vierteiligen Tutorialreihe verwenden Sie Python, um Daten für die Vorhersage von Skiverleihen in SQL Server Machine Learning Services vorzubereiten.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/02/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9aeefb0b6fd9ca1a744d132fccf1eedfedbaa6e7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75681746"
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

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md) haben Sie gelernt, wie Sie das Modell in SQL Server speichern und gespeicherte Prozeduren aus den Python-Skripts erstellen, die Sie in Teil 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden in SQL Server ausgeführt, um Vorhersagen basierend auf neuen Daten treffen zu können.

## <a name="prerequisites"></a>Voraussetzungen

* In diesem Teil der Tutorialreihe wird davon ausgegangen, dass Sie [Teil 1](python-ski-rental-linear-regression.md) und die erforderlichen Voraussetzungen abgeschlossen haben.

## <a name="explore-and-prepare-the-data"></a>Durchsuchen und Vorbereiten der Daten

Laden Sie die Daten aus der SQL Server-Datenbank in einen Pandas-Datenrahmen, um sie in Python verwenden zu können.

Erstellen Sie in Azure Data Studio ein neues Python-Notebook, und führen Sie das folgende Skript aus. Ersetzen Sie `<SQL Server>` durch Ihren eigenen SQL Server-Namen.

Importieren Sie mit dem folgenden Python-Skript das Dataset aus der Tabelle **dbo.rental_data** in Ihrer Datenbank in den Pandas-Datenrahmen **df**:

Ersetzen Sie bei Bedarf die Verbindungsdetails in der Verbindungszeichenfolge.

```python
import pyodbc
import pandas
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Connection string to your SQL Server instance
conn_str = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server}; SERVER=localhost; DATABASE=TutorialDB; Trusted_Connection=yes')

query_str = 'SELECT Year, Month, Day, Rentalcount, Weekday, Holiday, Snow FROM dbo.rental_data'

df = pandas.read_sql(sql=query_str, con=conn_str)

print("Data frame:", df)

# Get all the columns from the dataframe.
columns = df.columns.tolist()

# Filter the columns to remove ones we don't want to use in the training
columns = [c for c in columns if c not in ["Year"]]
```

Das Ergebnis sollte etwa folgendermaßen aussehen:

```results
Data frame:      Year  Month  Day  RentalCount  WeekDay  Holiday  Snow
0    2014      1   20          445        2        1     0
1    2014      2   13           40        5        0     0
2    2013      3   10          456        1        0     0
3    2014      3   31           38        2        0     0
4    2014      4   24           23        5        0     0
..    ...    ...  ...          ...      ...      ...   ...
448  2013      2   19           57        3        0     1
449  2015      3   18           26        4        0     0
450  2015      3   24           29        3        0     1
451  2014      3   26           50        4        0     1
452  2015     12    6          377        1        0     1

[453 rows x 7 columns]
```

## <a name="next-steps"></a>Nächste Schritte

In Teil 2 dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Laden der Daten aus der SQL Server-Datenbank in einen **Pandas**-Datenrahmen
* Vorbereiten der Daten in Python durch Entfernen einiger Spalten

Fahren Sie mit Teil 3 dieser Tutorialreihe fort, um ein Machine Learning-Modell zu trainieren, das Daten aus der Datenbank „TutorialDB“ verwendet:

> [!div class="nextstepaction"]
> [Python-Tutorial: Trainieren eines linearen Regressionsmodells](python-ski-rental-linear-regression-train-model.md)