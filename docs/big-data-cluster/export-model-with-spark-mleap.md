---
title: Exportieren Sie die Spark-Machine-Learning-Modellen mit MLeap | SqlServer
description: Exportieren Sie Spark-Machine learning-Modellen mit MLeap
services: SQL Server 2019 Big Data Cluster Spark
ms.service: SQL Server 2019 Big Data Cluster Spark
author: lgongmsft
ms.author: shivprashant
ms.reviewer: jroth
ms.custom: ''
ms.topic: conceptual
ms.date: 10/10/2018
ms.openlocfilehash: 546e46c6e9c5b2875f817fbf9a5fc3107afeb8a2
ms.sourcegitcommit: 29760037d0a3cec8b9e342727334cc3d01db82a6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50411853"
---
# <a name="export-models-using-mleap"></a>Exportieren von Modellen mithilfe von Mleap
Einen typischen Machine Learning-Szenario wird in Spark trainieren und bewerten außerhalb von Spark. Exportieren von Modellen in einem portablen Format so, dass sie außerhalb von Spark verwendet werden kann. [MLeap](https://github.com/combust/mleap) ist ein solches Modell Exchange-Format. Es bietet Spark Machine Learning-Pipelines und Modelle, die als portable Formate exportiert und in jedem JVM-basierten System mit verwendet die `Mleap` Common Language Runtime.

Diese Anleitung veranschaulicht, wie Sie die Spark-Modelle, die mithilfe von Mleap exportieren können. Die Schritte werden unten zusammengefasst und mit Code im folgenden Abschnitt beschrieben.

1. Zunächst erstellen einen Spark-Modell. Verwenden Sie für dieses **Trainings- und Erstellen von Machine Learning-Modell mit Spark [hier.](train-and-create-machinelearning-models-with-spark.md)**
2. Als Nächstes müssen wir **Training\test Daten und das Modell importieren**
3. **Exportieren Sie das Modell als `Mleap` Bundle**. Dieses exportierte Paket kann jetzt verwendet werden, um außerhalb von Spark zu bewerten.
4. Um zu überprüfen, importieren wir die `Mleap` erneut, zurück zu bündeln, und verwenden, um Spark zu bewerten.

## <a name="step-1---start-by-creating-a-spark-model"></a>Schritt 1: Start durch Erstellen eines Spark-Modells
Führen Sie [Schulungs- und erstellen Machine Learning-Modell mit Spark] (train-and-create-machinelearning-models-with-spark.md) zum Erstellen von Trainings-/Test-Sätzen und Modell und in den HDFS-Speicher beibehalten. Das Modell exportiert werden sollen, als `AdultCensus.mml` unter der `spark_ml` Verzeichnis.


## <a name="step-2---import-the-trainingtest-data-and-the-model"></a>Schritt 2: Importieren der Training\test Daten und dem Modell

Schritt 1 erstellt die `AdultCensus.mml`, d.h. ein Spark-Modell. 

Importieren Sie in diesem Schritt das Spark-Modell.

```python
import mleap.pyspark
from mleap.pyspark.spark_support import SimpleSparkSerializer
from pyspark.ml import PipelineModel

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

print("load pyspark model from hbfs")
model = PipelineModel.load(model_fs)
print("Model is " , model)
print("Model stages", model.stages)
```


## <a name="step-3---export-the-model-as-mleap-bundle"></a>Schritt 3: exportieren Sie das Modell als `Mleap` Bundle

Exportieren Sie das Spark-Modell als eine portierbare `Mleap` modellieren und speichern Sie die Daten im lokalen Speicher. Veröffentlichen Sie diesen Schritt, das Modell finden Sie in einer tragbaren `Mleap` formatieren und außerhalb von Spark verwendet werden können.

```python
import os

#Get the train and test datasets

# Write the train and test data sets to intermediate storage

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train = spark.read.orc(train_data_path)
test = spark.read.orc(test_data_path)

print("train: ({}, {})".format(train.count(), len(train.columns)))
train.printSchema()

print("test: ({}, {})".format(test.count(), len(test.columns)))
test.printSchema()

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# remove an old model file, if needed.
try:
    os.remove(model_file)
except OSError:
    pass

model_file_path = "jar:file:{}".format(model_file)
model.serializeToBundle(model_file_path, model.transform(train))

```

Beibehalten der `Mleap` Paket vom lokalen in Hdfs

```python
print("persist the mleap bundle from local to hdfs")
from subprocess import Popen, PIPE
proc = Popen(["hadoop", "fs", "-put", "-f", model_file, os.path.join("/spark_ml", model_name_export)], stdout=PIPE, stderr=PIPE)
s_output, s_err = proc.communicate()
if(s_err):
    print("Error when storing to HDFS")
```

## <a name="step-3---validate-by-importing-the-mleap-bundle-and-scoring-in-spark"></a>Schritt 3: Überprüfen, indem Sie importieren die `Mleap` Paket und Scoring in Spark
In Schritt 2 haben wir bereits das Modell auf einem tragbaren exportiert `Mleap` Format, das außerhalb von Spark verwendet werden kann. In diesem Schritt importieren wir die `Mleap` in Spark serialisiert und in Spark für die Bewertung für die Testsammlung.
   
```python
model_deserialized = PipelineModel.deserializeFromBundle(model_file_path)
print("The deserialized model is ", model_deserialized)
print("The deserialized model stages are", model_deserialized.stages)

from pyspark.ml.evaluation import BinaryClassificationEvaluator

# make prediction
pred = model_deserialized.transform(test)


# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Results of using the model score test set")
print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```

## <a name="references"></a>Verweise

* [Erste Schritte mit PySpark-notebooks](notebooks-guidance.md)
* [Trainieren und das Erstellen von Machine Learning-Modell mit Spark](train-and-create-machinelearning-models-with-spark.md)
