---
title: 'Python-Tutorial: Trainieren des Modells'
description: In diesem Tutorial verwenden Sie Python und die lineare Regression in SQL Server Machine Learning Services zur Vorhersage von Verleihzahlen für einen Skiverleih. Dazu trainieren Sie ein lineares Regressionsmodell in Python.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/03/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e5f83fe37890c997865c44198cbe30bc13cdea4e
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727045"
---
# <a name="python-tutorial-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Python-Tutorial: Trainieren eines linearen Regressionsmodells in SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In Teil 3 dieser vierteiligen Tutorialreihe trainieren Sie ein lineares Regressionsmodell in Python. Im nächsten Teil dieser Reihe stellen Sie dann dieses Modell in einer SQL Server-Datenbank-Instanz mit Machine Learning Services bereit.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Trainieren eines linearen Regressionsmodells
> * Treffen von Vorhersagen mit dem linearen Regressionsmodell

In [Teil 1](python-ski-rental-linear-regression.md) dieser Tutorialreihe haben Sie gelernt, wie Sie die Beispieldatenbank wiederherstellen.

In [Teil 2](python-ski-rental-linear-regression-prepare-data.md) haben Sie erfahren, wie Sie die Daten aus SQL Server in einen Python-Datenrahmen laden und in Python vorbereiten.

In [Teil 4](python-ski-rental-linear-regression-deploy-model.md) haben Sie gelernt, wie Sie das Modell in SQL Server speichern und gespeicherte Prozeduren aus den Python-Skripts erstellen, die Sie in Teil 2 und 3 entwickelt haben. Die gespeicherten Prozeduren werden in SQL Server ausgeführt, um Vorhersagen basierend auf neuen Daten treffen zu können.

## <a name="prerequisites"></a>Voraussetzungen

* In diesem Teil der Tutorialreihe wird davon ausgegangen, dass Sie [Teil 1](python-ski-rental-linear-regression.md) und die erforderlichen Voraussetzungen abgeschlossen haben.

## <a name="train-the-model"></a>Trainieren des Modells

Für die Vorhersage müssen Sie eine Funktion (ein Modell) finden, die die Abhängigkeit zwischen den Variablen in unserem Dataset am besten beschreibt. Dies wird als Training des Modells bezeichnet. Das Trainingsdataset ist eine Teilmenge des gesamten Datensets aus dem Pandas-Datenrahmen **df**, den Sie im zweiten Teil dieser Reihe erstellt haben.

Dann trainieren Sie das Modell **lin_model** mit einem linearen Regressionsalgorithmus.

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

Das Ergebnis sollte etwa folgendermaßen aussehen:

```results
Training set shape: (362, 7)
Testing set shape: (91, 7)
```

## <a name="make-predictions"></a>Erstellen von Vorhersagen

Verwenden Sie eine Vorhersagefunktion, um die Verleihzahlen mithilfe des Modells **lin_model** vorherzusagen.

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

In Teil 3 dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Trainieren eines linearen Regressionsmodells
* Treffen von Vorhersagen mit dem linearen Regressionsmodell

Um das von Ihnen erstellte Machine-Learning-Modell einzusetzen, fahren Sie mit Teil 4 dieser Tutorialreihe fort:

> [!div class="nextstepaction"]
> [Python-Tutorial: Bereitstellen eines Machine Learning-Modells](python-ski-rental-linear-regression-deploy-model.md)