---
title: 'Python-Tutorial: Train Model (lineare Regression)'
description: In diesem Tutorial verwenden Sie die python-und lineare Regression in SQL Server Machine Learning Services, um die Anzahl der Ski-Vermietungen vorherzusagen. Sie trainieren ein lineares Regressionsmodell in Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 30f390681dc63d6de9a95e805b6cc8f273b2b8d7
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70242548"
---
# <a name="python-tutorial-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Python-Tutorial: Trainieren eines linearen Regressionsmodells in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im dritten Teil dieser vierteiligen tutorialreihe trainieren Sie ein lineares Regressionsmodell in Python. Im nächsten Teil dieser Serie stellen Sie dieses Modell in einer SQL Server Datenbank mit Machine Learning Services bereit.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Trainieren eines linearen Regressionsmodells
> * Treffen von Vorhersagen mit dem linearen Regressionsmodell

In [Teil 1](python-ski-rental-linear-regression.md)haben Sie gelernt, wie Sie die Beispieldatenbank wiederherstellen.

In [Teil 2](python-ski-rental-linear-regression-prepare-data.md)haben Sie gelernt, wie die Daten aus SQL Server in einen python-Datenrahmen geladen und die Daten in python vorbereitet werden.

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md)erfahren Sie, wie Sie das Modell in SQL Server speichern und dann gespeicherte Prozeduren aus den python-Skripts erstellen, die Sie in den Teilen 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden in SQL Server ausgeführt, um Vorhersagen basierend auf neuen Daten zu treffen.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Im dritten Teil dieses Tutorials wird davon ausgegangen, dass Sie [Teil eins](python-ski-rental-linear-regression.md) und seine Voraussetzungen erfüllt haben.

## <a name="train-the-model"></a>Trainieren des Modells

Um vorherzusagen, müssen Sie eine Funktion (Modell) finden, die die Abhängigkeit zwischen den Variablen in unserem Dataset am besten beschreibt. Dies wurde als trainieren des Modells bezeichnet. Das Trainings Dataset ist eine Teilmenge des gesamten Datasets aus der Pandas-Datenrahmen- **DF** , die Sie in Teil 2 dieser Reihe erstellt haben.

Sie trainieren Model **lin_model** mit einem LinearRegression-Algorithmus.

```python
# Store the variable we'll be predicting on.
target = "RentalCount"

# Generate the training set.  Set random_state to be able to replicate results.
train = df.sample(frac=0.8, random_state=1)

# Select anything not in the training set and put it in the testing set.
test = df.loc[~df.index.isin(train.index)]

# Print the shapes of both sets.
print("Training set shape:", train.shape)
print("Testing set shape:", test.shape)

# Initialize the model class.
lin_model = LinearRegression()

# Fit the model to the training data.
lin_model.fit(train[columns], train[target])
```

Es sollten ähnliche Ergebnisse wie die folgenden angezeigt werden.

```results
Training set shape: (362, 7)
Testing set shape: (91, 7)
```

## <a name="make-predictions"></a>Treffen von Vorhersagen

Verwenden Sie eine Vorhersagefunktion, um die Anzahl der Miet Werte mithilfe des Model **lin_model**vorherzusagen.

```python
# Generate our predictions for the test set.
lin_predictions = lin_model.predict(test[columns])
print("Predictions:", lin_predictions)
# Compute error between our test predictions and the actual values.
lin_mse = mean_squared_error(lin_predictions, test[target])
print("Computed error:", lin_mse)
```

```results
Predictions: [  40.   38.  240.   39.  514.   48.  297.   25.  507.   24.   30.   54.
   40.   26.   30.   34.   42.  390.  336.   37.   22.   35.   55.  350.
  252.  370.  499.   48.   37.  494.   46.   25.  312.  390.   35.   35.
  421.   39.  176.   21.   33.  452.   34.   28.   37.  260.   49.  577.
  312.   24.   24.  390.   34.   64.   26.   32.   33.  358.  348.   25.
   35.   48.   39.   44.   58.   24.  350.  651.   38.  468.   26.   42.
  310.  709.  155.   26.  648.  617.   26.  846.  729.   44.  432.   25.
   39.   28.  325.   46.   36.   50.   63.]
Computed error: 3.59831533436e-26
```

## <a name="next-steps"></a>Nächste Schritte

Im dritten Teil dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Trainieren eines linearen Regressionsmodells
* Treffen von Vorhersagen mit dem linearen Regressionsmodell

Um das Machine Learning-Modell bereitzustellen, das Sie erstellt haben, befolgen Sie den Teil vier dieser tutorialreihe:

> [!div class="nextstepaction"]
> [Python-Tutorial: Bereitstellen eines Machine Learning-Modells](python-ski-rental-linear-regression-deploy-model.md)