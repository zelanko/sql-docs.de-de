---
title: Train/Create ML-Modellen mit Spark
titleSuffix: SQL Server big data clusters
description: Verwenden Sie PySpark wird zum Trainieren und erstellen Sie mit Spark Machine Learning-Modelle in SQL Server-big Data-Clustern (Vorschau).
author: lgongmsft
ms.author: shivprashant
ms.manager: craigg
ms.reviewer: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: b9217b56da2e00ba50288f1643df809f482c2517
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860561"
---
# <a name="train-and-create-machine-learning-models-with-spark"></a>Trainieren und Erstellen von Machine Learning-Modellen mit Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Spark in SQL Server-big Data-Cluster ermöglicht künstliche Intelligenz und Machine Learning. Im Beispiel wird veranschaulicht, wie zum Trainieren eines Machine learning-Modell mithilfe von Python in Spark (PySpark), die mithilfe von Daten in HDFS gespeichert. 

Das Beispiel ist eine schrittweise Anleitung zur mit Codeausschnitten, die verwendet werden kann, eine Studio-Notebook in Azure Daten und jede Zelle um einen Schritt ausführen, zu einem Zeitpunkt. Weitere Informationen zur Verbindung mit Spark über Notebook finden Sie unter [hier](notebooks-guidance.md)

Im Beispiel:

1. Beginnen Sie mit **Verständnis für die Daten und die gewünschten Vorhersage**
2. **Die Daten in HDFS hochzuladen und Vorbereiten der Daten** zum Erstellen des Modells
3. **Wählen Sie die zu verwendenden Merkmale**
4. **Daten werden als Trainings- und Testsätze aufteilen.**
5. Zusammengestellt, die eine **ml-Pipeline und Erstellen eines Modells**
6. Verwenden Sie das erstellte Modell **Vorhersagen**
7. Als letzten Schritt **erstellte Modell zur späteren Verwendung beizubehalten**.

E2E-Machine Learning umfasst mehrere zusätzliche Schritte, z. B., Durchsuchen von Daten, Feature Auswahl und Principal Komponente Analysis, Modellauswahl. Viele dieser Schritte werden hier aus Gründen der Übersichtlichkeit ignoriert.

## <a name="step-1---understanding-the-data-and-prediction-desired"></a>Schritt 1: Grundlegendes zu den Daten und die gewünschten Vorhersage

Dieses Beispiel verwendet die adult Census Income Daten aus [hier]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv ). In `AdultCensusIncome.csv`, jede Zeile steht für Income bewegen und andere Merkmale wie, Stunden pro Woche, Education, "Occupation" usw. für einen bestimmten Erwachsener age. Erstellen Sie ein Modell, das Vorhersagen kann, wenn die Income bewegen. Das Modell übernimmt Age "und" Stunden pro Woche als Funktionen und Vorhersagen, ob das Einkommen wäre > 50 K oder < 50 k beträgt. 

## <a name="step-2---upload-the-data-to-hdfs-and-basic-explorations-on-data"></a>Schritt 2: Hochladen der Daten in HDFS und grundlegende auswertungen für Daten
Aus Azure Data Studio eine Verbindung mit dem HDFS/Spark-Gateway herstellen, und erstellen Sie ein Verzeichnis namens `spark_ml` unter HDFS. Herunterladen [AdultCensusIncome.csv]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv ) auf Ihrem lokalen Computer, und in HDFS hochzuladen. Hochladen von `AdultCensusIncome.csv` zu dem Ordner, die Sie erstellt haben.


Jetzt Schreiben von Code. Sie können den unten stehenden Code kopieren und fügen Sie ihn in einzelne Zellen eines Notebooks in Azure Data Studio. 

Der folgende Code liest die CSV-Datei in Spark-Datenrahmen. Weiter, die es zählt die Anzahl der Zeilen und Spalten und die geladenen Daten angezeigt.

```python
datafile = "/spark_ml/AdultCensusIncome.csv"

#Read the data to a spark data frame.
data_all = spark.read.format('csv').options(header='true', inferSchema='true', ignoreLeadingWhiteSpace='true', ignoreTrailingWhiteSpace='true').load(datafile)
print("Number of rows: {},  Number of coulumns : {}".format(data_all.count(), len(data_all.columns)))

#Replace "-" with "_" in column names
columns_new = [col.replace("-", "_") for col in data_all.columns]
data_all = data_all.toDF(*columns_new)

#Print Schema and show top 5 row
data_all.printSchema() 
data_all.show(5)
```

## <a name="step-3---select-features-to-use"></a>Schritt 3: Auswählen von Features zu verwenden

Verwenden Sie in diesem Schritt den folgenden zwei Begriffe
1. `Label`    – Bezieht sich auf den vorherzusagender Wert. Dies wird als eine Spalte in den Daten dargestellt.  
2. `Features` -Verweist auf die Eigenschaften in den Daten vorherzusagen. Einige Zeit als auch bezeichnet `predictors` 

In diesem Beispiel `Label`, ist die **Einkommen** Spalte. Wählen Sie aus Gründen der Einfachheit **Alter** und **Hours_per_week** als `Features`. In der Praxis werden Funktionen durch Anwenden von einigen korrelationstechniken ausgewählt, um zu verstehen, was am besten die predicting Bezeichnung charakterisieren.

```python
# Choose feature columns and the label column.
label = "income"
xvars = ["age", "hours_per_week"] #all numeric

print("label = {}".format(label))
print("features = {}".format(xvars))

select_cols = xvars
select_cols.append(label)
data = data_all.select(select_cols)

```

## <a name="step-4---split-as-training-and-test-set"></a>Schritt 4: als Trainings- und Testsätze aufteilen

Verwenden von 75 % der Zeilen trainiert das Modell und die restlichen 25 %, um die das Modell zu bewerten. Darüber hinaus das Trainieren beibehalten und testdatasets in den HDFS-Speicher. Der Schritt ist nicht erforderlich, aber zur Veranschaulichung gezeigt speichern und Laden von ORC-Format. Andere Formate, z. B. `Parquet` kann ebenfalls verwendet werden.

Veröffentlichen Sie diesen Schritt sehen Sie zwei Verzeichnisse, die mit dem Namen AdultCensusIncomeTrain und die AdultCensusIncomeTest erstellt

```python

# Split data into train and test.
train, test = data.randomSplit([0.75, 0.25], seed=123)

print("train ({}, {})".format(train.count(), len(train.columns)))
print("test ({}, {})".format(test.count(), len(test.columns)))

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train.write.mode('overwrite').orc(train_data_path)
test.write.mode('overwrite').orc(test_data_path)
print("train and test datasets saved to {} and {}".format(train_data_path, test_data_path))

```

## <a name="step-5---put-together-a-pipeline-and-build-a-model"></a>Schritt 5: zusammengestellt, die eine Pipeline aus, und Erstellen eines Modells
[Spark ML-Pipeline](https://spark.apache.org/docs/2.3.1/ml-pipeline.html) können alle Schritte als Workflow sequenzieren und erleichtern das Experimentieren mit verschiedenen Algorithmen und ihren Parametern. Der folgende Code erstellt zunächst die Phasen und setzt diese Phasen zusammen in Ml-Pipeline.  LogisticRegression wird verwendet, um das Modell zu erstellen.

```python
from pyspark.ml import Pipeline, PipelineModel
from pyspark.ml.feature import OneHotEncoder, StringIndexer, VectorAssembler
from pyspark.ml.classification import LogisticRegression

reg = 0.1
print("Using LogisticRegression model with Regularization Rate of {}.".format(reg))

# create a new Logistic Regression model.
lr = LogisticRegression(regParam=reg)

dtypes = dict(train.dtypes)
dtypes.pop(label)

si_xvars = []
ohe_xvars = []
featureCols = []
for idx,key in enumerate(dtypes):
    if dtypes[key] == "string":
        featureCol = "-".join([key, "encoded"])
        featureCols.append(featureCol)
        
        tmpCol = "-".join([key, "tmp"])
        si_xvars.append(StringIndexer(inputCol=key, outputCol=tmpCol, handleInvalid="skip")) #, handleInvalid="keep"
        ohe_xvars.append(OneHotEncoder(inputCol=tmpCol, outputCol=featureCol))
    else:
        featureCols.append(key)

# string-index the label column into a column named "label"
si_label = StringIndexer(inputCol=label, outputCol='label')

# assemble the encoded feature columns in to a column named "features"
assembler = VectorAssembler(inputCols=featureCols, outputCol="features")

```

Jetzt zusammengestellt, die die Pipeline. 

```python
# put together the pipeline
stages = []
stages.extend(si_xvars)
stages.extend(ohe_xvars)
stages.append(si_label)
stages.append(assembler)
stages.append(lr)
pipe = Pipeline(stages=stages)
print("Pipeline Created")

```

Nun, da die Pipeline erstellt wird, verwenden Sie, die zum Trainieren des Modells.

```python
# train the model
model = pipe.fit(train)
print("Model Trained")
print("Model is ", model)
print("Model Stages", model.stages)

```

## <a name="step-6---predict-using-the-model-and-evaluate-the-model-accuracy"></a>Schritt 6: Vorhersagen unter Verwendung des Modells und Auswerten der modellgenauigkeit
Der folgende Code verwendet Test-DataSet, um das Ergebnis mit dem im vorherigen Schritt erstellte Modell vorherzusagen. Er misst die Genauigkeit des Modells mit `areaUnderROC` und `areaUnderPR` Metrik.

```python
from pyspark.ml.evaluation import BinaryClassificationEvaluator
# make prediction
pred = model.transform(test)

# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```


## <a name="step-7---persist-the-models-to-hdfs"></a>Schritt 7: Beibehalten der Modelle in HDFS
Speichern Sie abschließend das Modell in HDFS für die spätere Verwendung. Nach diesem Schritt erstellte Modell gespeichert werden, als /spark_ml/AdultCensus.mml

```python
##NOTE: by default the model is saved to and loaded from path

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

model.write().overwrite().save(model_fs)
print("saved model to {}".format(model_fs))

# load the model file (from dbfs)
model2 = PipelineModel.load(model_fs)
assert str(model2) == str(model)
print("loaded model from {}".format(model_fs))
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Einstieg in das PySpark-Notebooks finden Sie unter [Verwendung von Notebooks](notebooks-guidance.md).