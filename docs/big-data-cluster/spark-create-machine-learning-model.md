---
title: Erstellen und Exportieren von Spark-Machine learning-Modellen mit MLeap
titleSuffix: SQL Server big data clusters
description: Verwenden Sie PySpark wird zum Trainieren und erstellen Sie mit Spark Machine Learning-Modelle in SQL Server-big Data-Clustern (Vorschau). Exportieren mit MLeap, und klicken Sie dann das Modell mit Java in SQL Server zu bewerten.
author: lgongmsft
ms.author: lgong
ms.manager: craigg
ms.reviewer: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 709d74ef33ab6b54ac688763b006d66e4210006d
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67412884"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-sql-server-big-data-clusters"></a>Erstellen, exportieren und Bewerten von Machine Learning-Modelle in SQL Server-big Data-Clustern für Spark

Das folgende Beispiel zeigt, wie zum Erstellen eines Modells mit [Spark ML](https://spark.apache.org/docs/latest/ml-guide.html), exportieren Sie das Modell, das [MLeap](http://mleap-docs.combust.ml/), und Bewerten des Modells in SQL Server mit der [Java-Spracherweiterung](../language-extensions/language-extensions-overview.md). Dies erfolgt im Rahmen einer big Data-Cluster mit SQL Server-2019.

Das folgende Diagramm veranschaulicht die Aufgaben in diesem Beispiel:

![Bewertung Exportieren mit Spark trainieren](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>Erforderliche Komponenten

Alle Dateien für dieses Beispiel befinden sich unter [ https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml ](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml).

Um das Beispiel auszuführen, müssen Sie auch die folgenden Voraussetzungen:

- Ein [SQL Server-big Data-Cluster](deploy-get-started.md)

- [Big Data-tools](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Das Trainieren des Modells mit Spark ML

In diesem Beispiel Volkszählungsdaten (**AdultCensusIncome.csv**) wird verwendet, um ein Modell der Spark ML-Pipeline zu erstellen.

1. Verwenden der [mleap_sql_test/setup.sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/setup.sh) Datei, die das Dataset aus dem Internet herunterladen und in HDFS in Ihrer SQL Server-big Data-Cluster. Dies ermöglicht es durch Spark zugegriffen werden kann.

1. Klicken Sie dann Herunterladen der Beispiel-Notebook [train_score_export_ml_models_with_spark.ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb). Führen Sie über eine PowerShell- oder Bash-Befehlszeile den folgenden Befehl zum Herunterladen des Notebooks aus:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   Dieses Notebook werden die Zellen mit den erforderlichen Befehlen für diesen Abschnitt des Beispiels enthält.

1. Öffnen Sie das Notebook in Azure Data Studio, und führen Sie jeden Codeblock. Weitere Informationen zum Arbeiten mit Notebooks finden Sie unter [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md).

Die Daten zunächst in Spark gelesen und in Trainings- und Testsätze aufteilen. Klicken Sie dann trainiert der Code eine Pipeline mit den Trainingsdaten. Schließlich wird das Modell auf eine MLeap Paket exportiert.

> [!TIP]
> Sie können auch überprüfen, oder führen Sie den Zusammenhang mit diesen Schritten außerhalb des Notebooks in Python-Code der [mleap_sql_test/mleap_pyspark.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_pyspark.py) Datei.

## <a name="model-scoring-with-sql-server"></a>Modell mit SQL Server bewerten

Nun, da das Modell der Spark ML-Pipeline in einer allgemeinen Serialisierung ist [MLeap Bundle](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html) -Format, Sie können die Bewertung des Modells in Java, ohne das Vorhandensein von Spark. 

Dieses Beispiel verwendet die [Java-Spracherweiterung](../language-extensions/language-extensions-overview.md) in SQL Server. Um das Modell in SQL Server zu bewerten, müssen Sie zuerst eine Java-Anwendung zu erstellen, die laden das Modell in Java und seine Bewertung können. Sie finden den Beispielcode für diese Java-Anwendung in der [Mssql-Mleap-app-Ordner](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mssql-mleap-app).

Nach dem Erstellen des Beispiels können Sie Transact-SQL zum Aufrufen von der Java-Anwendung, und Bewerten des Modells mit einer Datenbanktabelle. Dies ist in drei [mleap_sql_test/mleap_sql_tests.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_sql_tests.py) Quelldatei.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md)
