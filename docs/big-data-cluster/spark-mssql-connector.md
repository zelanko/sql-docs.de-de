---
title: Verbinden von Spark mit SQLServer
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie mit der MSSQL-Spark-Connector in Spark zum Lesen und Schreiben in SQL Server.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 878e08426fc58d6ad5a921eff4ac33dca18aa03c
ms.sourcegitcommit: f7ad034f748ebc3e5691a5e4c3eb7490e5cf3ccf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2019
ms.locfileid: "67469120"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>Das Lesen und Schreiben in SQL Server aus Spark mithilfe von der MSSQL-Spark-Connector

Ein Schlüssel big Data-Verwendungsmuster ist umfangreiche Data-Verarbeitung in Spark durch Schreiben von Daten in SQL Server für den Zugriff auf LOB-Anwendungen befolgt. Diese Verwendungsmuster profitieren von einer Connector nutzt die wichtige Optimierungen für SQL und bietet einen Mechanismus für die effiziente schreiben.

Dieser Artikel enthält ein Beispiel zur Verwendung des MSSQL-Spark-Connectors zum Lesen und Schreiben in den folgenden Speicherorten innerhalb einer big Data-Cluster:

1. Master SQL Server-Instanz
1. Die SQL Server-Daten-pool

   ![Diagramm der MSSQL-Spark-connector](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

Das Beispiel führt die folgenden Aufgaben:

- Lesen einer Datei aus einem HDFS und einige grundlegende Verarbeitungsvorgänge ausführen.
- Schreiben Sie den Dataframe in eine SQL Server-Masterinstanz als eine SQL-Tabelle und Lesen Sie die Tabelle in einen Dataframe.
- Schreiben Sie den Dataframe in einen Pool des SQL Server-Daten als eine externe SQL-Tabelle, und Lesen Sie die externe Tabelle in einen Dataframe.

## <a name="mssql-spark-connector-interface"></a>MSSQL-Spark-Connector-Schnittstelle

SQL Server-2019 Preview bietet die **MSSQL-Spark-Connector** für big Data Clustern, die SQL Server-Bulk verwendet Schreiben von APIs für Spark für SQL-Schreibvorgänge. MSSQL-Spark-Connector basiert auf Spark-Datenquelle, APIs und bietet eine vertraute Oberfläche des Spark-JDBC-Connector. Netzwerkschnittstellen-Parametern finden Sie unter [Apache Spark-Dokumentation](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Der MSSQL-Spark-Connector wird anhand des Namens verwiesen **com.microsoft.sqlserver.jdbc.spark**.

Die folgende Tabelle beschreibt die Parameter für die Benutzeroberfläche, die geändert oder sind neu:

| Eigenschaftenname | Optional | Description |
|---|---|---|
| **isolationLevel** | Ja | Hier wird beschrieben, die Isolationsstufe der Verbindung. Der Standardwert für MSSQLSpark Connector ist **READ_COMMITTED** |

Der Connector verwendet SQL Server-Bulk Schreiben von APIs. Jeder Bulk-Schreibvorgang Parameter können als optionale Parameter übergeben werden, durch den Benutzer und werden als übergeben-ist, indem Sie den Connector an die zugrunde liegende API. Weitere Informationen über die massenbearbeitung von Schreibvorgängen, finden Sie unter [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Ein [SQL Server-big Data-Cluster](deploy-get-started.md).

- [Azure Data Studio](https://aka.ms/azdata-insiders).

## <a name="create-the-target-database"></a>Erstellen Sie die Zieldatenbank

1. Öffnen Sie Azure Data Studio, und [Verbinden mit der SQL Server-Masterinstanz von Ihrer big Data-Cluster](connect-to-big-data-cluster.md).

1. Erstellen einer neuen Abfrage ein, und führen Sie den folgenden Befehl zum Erstellen einer Beispieldatenbank mit dem Namen **MyTestDatabase**.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>Laden Sie Beispieldaten in HDFS

1. Herunterladen [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) auf Ihrem lokalen Computer.

1. Starten Sie Azure Data Studio, und [Herstellen einer Verbindung Ihrer big Data-Cluster mit](connect-to-big-data-cluster.md).

1. Mit der rechten Maustaste auf den HDFS-Ordner in Ihrem big Data-Cluster, und wählen **neues Verzeichnis**. Nennen Sie das Verzeichnis **Spark_data**.

1. Klicken Sie mit der rechten Maustaste auf die **Spark_data** , und wählen **Hochladen von Dateien**. Hochladen der **AdultCensusIncome.csv** Datei.

   ![AdultCensusIncome CSV-Datei](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>Führen Sie die Beispiel-notebook

Um die Verwendung von der MSSQL-Spark-Connector mit diesen Daten zu veranschaulichen, können Sie ein Beispiel-Notebook herunterladen, öffnen Sie sie in Azure Data Studio und führen Sie jeden Codeblock. Weitere Informationen zum Arbeiten mit Notebooks finden Sie unter [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md).

1. Führen Sie über eine PowerShell- oder Bash-Befehlszeile den folgenden Befehl zum Herunterladen der **mssql_spark_connector.ipynb** Beispiel-Notebook:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector.ipynb"
   ```

1. Öffnen Sie in Azure Data Studio die Beispiel-Notebook-Datei. Stellen Sie sicher, dass er mit dem HDFS/Spark-Gateway für Ihre big Data-Cluster verbunden ist.

1. Führen Sie jede codezelle aus, in der Stichprobe, die Verwendung von MSSQL-Spark-Connector finden Sie unter.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md)