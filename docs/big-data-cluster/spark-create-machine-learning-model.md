---
title: Erstellen und Exportieren von Spark-Machine Learning-Modellen mit msprung
titleSuffix: SQL Server big data clusters
description: Verwenden Sie pyspark, um Machine Learning-Modelle mit Spark auf SQL Server Big Data Clustern (Vorschauversion) zu trainieren und zu erstellen. Exportieren Sie mit msprung, und bewerten Sie dann das Modell mit Java in SQL Server.
author: lgongmsft
ms.author: lgong
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aa4c31eca725e8e662937259f078cf00a3441915
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "67727374"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-sql-server-big-data-clusters"></a>Erstellen, exportieren und bewerten von Spark-Machine Learning-Modellen auf SQL Server Big Data Clustern

Im folgenden Beispiel wird gezeigt, wie Sie ein Modell mit [Spark ml](https://spark.apache.org/docs/latest/ml-guide.html)erstellen, das Modell in [msprung](http://mleap-docs.combust.ml/)exportieren und das Modell in SQL Server mit seiner [Java-Spracherweiterung](../language-extensions/language-extensions-overview.md)bewerten. Dies erfolgt im Kontext eines SQL Server 2019 Big Data Clusters.

Das folgende Diagramm veranschaulicht die in diesem Beispiel ausgeführte Arbeit:

![Trainieren des Ergebnis Exports mit Spark](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>Vorraussetzungen

Alle Dateien für dieses Beispiel befinden sich unter [https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml).

Zum Ausführen des Beispiels müssen die folgenden Voraussetzungen erfüllt sein:

- Ein [SQL Server Big Data-Cluster](deploy-get-started.md)

- [Big Data-Tools](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Modell Training mit Spark ml

In diesem Beispiel wird die Verwendung von Volkszählungsdaten ("**adultcensusincome. CSV**") zum Erstellen eines Spark ml-Pipeline Modells verwendet.

1. Verwenden Sie die Datei [mleap_sql_test/Setup. sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/setup.sh) , um das DataSet aus dem Internet herunterzuladen, und platzieren Sie es in HDFS in Ihrem SQL Server Big Data-Cluster. Dadurch kann von Spark auf ihn zugegriffen werden.

1. Laden Sie dann das Beispiel Notebook [train_score_export_ml_models_with_spark. ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb)herunter. Führen Sie in einer PowerShell-oder bash-Befehlszeile den folgenden Befehl aus, um das Notebook herunterzuladen:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Dieses Notebook enthält Zellen mit den erforderlichen Befehlen für diesen Abschnitt des Beispiels.

1. Öffnen Sie das Notebook in Azure Data Studio, und führen Sie jeden Codeblock aus. Weitere Informationen zum Arbeiten mit Notebooks finden Sie unter [Verwenden von Notebooks in SQL Server 2019 Preview](notebooks-guidance.md).

Die Daten werden zuerst in Spark gelesen und in Trainings-und Test Datasets aufgeteilt. Anschließend trainiert der Code ein Pipeline Modell mit den Trainingsdaten. Schließlich wird das Modell in ein msprung-Bündel exportiert.

> [!TIP]
> Sie können den Python-Code, der mit diesen Schritten verknüpft ist, auch außerhalb des Notebooks in der [mleap_sql_test/mleap_pyspark. py-](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_pyspark.py) Datei überprüfen oder ausführen.

## <a name="model-scoring-with-sql-server"></a>Modell Bewertung mit SQL Server

Da sich das Spark ml-Pipeline Modell nun in einem allgemeinen Serialisierungs- [msprung-Bundle](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html) -Format befindet, können Sie das Modell in Java bewerten, ohne dass Spark vorhanden ist. 

In diesem Beispiel wird die [Java-Spracherweiterung](../language-extensions/language-extensions-overview.md) in SQL Server verwendet. Um das Modell in SQL Server bewerten zu können, müssen Sie zunächst eine Java-Anwendung erstellen, die das Modell in Java laden und bewerten kann. Den Beispielcode für diese Java-Anwendung finden Sie im [Ordner "MSSQL-mleap-App](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mssql-mleap-app)".

Nach dem Aufbau des Beispiels können Sie Transact-SQL verwenden, um die Java-Anwendung aufzurufen und das Modell mit einer Datenbanktabelle zu bewerten. Dies kann in der Quelldatei [mleap_sql_test/mleap_sql_tests. py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_sql_tests.py) angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter Bereitstellen [SQL Server Big Data Clustern auf Kubernetes](deployment-guidance.md)
