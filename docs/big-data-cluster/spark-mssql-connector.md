---
title: Verbinden von Spark mit SQL Server
titleSuffix: SQL Server big data clusters
description: Hier erfahren Sie, wie Sie den Apache Spark-Connector für SQL Server und Azure SQL verwenden, um in SQL Server zu lesen und zu schreiben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning-bdc
ms.openlocfilehash: 3cb36c4bdddfaa97b9b6c08015308799d54cb0dc
ms.sourcegitcommit: 56f6892b3795da308d226d4b3c5c859ead2e830a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86438072"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-apache-spark-connector-for-sql-server-and-azure-sql"></a>Verwenden des Apache Spark-Connectors für SQL Server und Azure SQL, um aus Spark in SQL Server zu lesen und zu schreiben

Ein sehr wichtiges Muster für die Big Data-Nutzung ist die Verarbeitung großer Datenvolumen in Spark und das anschließende Schreiben der Daten in SQL Server, damit Branchenanwendungen darauf zugreifen können. Diese Nutzungsmuster profitieren von einem Connector, der wichtige SQL-Optimierungen nutzt und einen effizienten Schreibmechanismus bereitstellt.

Dieser Artikel bietet eine Übersicht über die Schnittstelle des Apache Spark-Connectors für SQL Server und Azure SQL und ihrer Instanziierung zur Verwendung mit dem AD-Modus und dem Modus ohne AD. Anschließend wird ein Beispiel zur Verwendung des Apache Spark-Connectors für SQL Server und Azure SQL zum Lesen und Schreiben in den folgenden Speicherorten in einem Big Data-Cluster veranschaulicht:
1. SQL Server-Masterinstanz
1. SQL Server-Datenpool

   ![Diagramm: Apache Spark-Connector für SQL Server und Azure SQL](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

## <a name="apache-spark-connector-for-sql-server-and-azure-sql-interface"></a>Schnittstelle für den Apache Spark-Connector für SQL Server und Azure SQL

SQL Server 2019 stellt den [**Apache Spark-Connector für SQL Server und Azure SQL für Big Data-Cluster**](https://github.com/microsoft/sql-spark-connector) bereit, der SQL Server-APIs für Massenschreibvorgänge zum Schreiben für Spark in SQL verwendet. Der Apache Spark-Connector für SQL Server und Azure SQL basiert auf Datenquellen-APIs von Spark und stellt eine bekannte Spark-JDBC-Connectorschnittstelle bereit. Informationen zu den Parametern der Schnittstelle finden Sie in der [Apache Spark-Dokumentation](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Zum Verweisen auf den Apache Spark-Connector für SQL Server und Azure SQL wird der Name **com.microsoft.sqlserver.jdbc.spark** verwendet. Der Apache Spark-Connector für SQL Server und Azure SQL unterstützt zwei Sicherheitsmodi zum Herstellen einer Verbindung mit SQL Server, den Modus ohne Active Directory und den Active Directory-Modus:
### <a name="non-ad-mode"></a>Modus ohne AD:
Im Sicherheitsmodus ohne AD verfügt jeder Benutzer über einen Benutzernamen und ein Kennwort, die bei der Instanziierung des Connectors als Parameter übergeben werden müssen, um Lese- und/oder Schreibvorgänge durchzuführen.
Im Folgenden wird ein Beispiel für die Connectorinstanziierung im Modus ohne AD veranschaulicht:
```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark" 

url = "jdbc:sqlserver://master-p-svc;databaseName=?;"
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("user", ?) \ 
   .option("password",?) 
writer.save() 
```
### <a name="ad-mode"></a>AD-Modus:
Im AD-Sicherheitsmodus muss der Benutzer `principal` und `keytab` bei der Containerinstanziierung als Parameter übergeben, nachdem er eine Schlüsseltabellendatei generiert hat.

In diesem Modus lädt der Treiber die Schlüsseltabellendatei in die entsprechenden Executor-Container. Dann verwenden die Executor-Container den Prinzipalnamen und die Schlüsseltabelle, um ein Token zu generieren, das zum Erstellen eines JDBC-Connectors für Lese-/Schreibvorgänge verwendet wird.

Im Folgenden wird ein Beispiel für die Connectorinstanziierung im AD-Modus veranschaulicht:
```python
# Note: '?' is a placeholder for a necessary user-specified value
connector_type = "com.microsoft.sqlserver.jdbc.spark"

url = "jdbc:sqlserver://master-p-svc;databaseName=?;integratedSecurity=true;authenticationScheme=JavaKerberos;" 
writer = df.write \ 
   .format(connector_type)\ 
   .mode("overwrite") 
   .option("url", url) \ 
   .option("principal", ?) \ 
   .option("keytab", ?)   

writer.save() 
```

Die folgende Tabelle beschreibt neue oder geänderte Schnittstellenparameter:

| Eigenschaftenname | Optional | BESCHREIBUNG |
|---|---|---|
| **isolationLevel** | Ja | Beschreibt die Isolationsstufe der Verbindung. Der Standardwert für den Connector lautet **READ_COMMITTED**. |

Der Connector verwendet SQL Server-APIs für Massenschreibvorgänge. Alle Parameter für Massenschreibvorgänge können vom Benutzer als optionale Parameter übergeben werden und werden vom Connector unverändert an die zugrunde liegende API übergeben. Weitere Informationen zu Massenschreibvorgängen finden Sie unter [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="apache-spark-connector-for-sql-server-and-azure-sql-sample"></a>Beispiel: Apache Spark-Connector für SQL Server und Azure SQL
Das Beispiel führt die folgenden Aufgaben aus:

- Lesen einer Datei aus HDFS und Ausführen einiger grundlegender Verarbeitungsschritte
- Schreiben des Dataframes in eine SQL Server-Masterinstanz als SQL-Tabelle und Einlesen der Tabelle in einen Dataframe
- Schreiben des Dataframes in einen SQL Server-Datenpool als externe SQL-Tabelle und Einlesen der externen Tabelle in einen Dataframe
### <a name="prerequisites"></a>Voraussetzungen

- Ein [SQL Server-Big Data-Cluster](deploy-get-started.md)

- [Azure Data Studio](https://aka.ms/getazuredatastudio)

### <a name="create-the-target-database"></a>Erstellen der Zieldatenbank

1. Öffnen Sie Azure Data Studio, und [stellen Sie eine Verbindung mit der SQL Server-Masterinstanz Ihres Big Data-Clusters her](connect-to-big-data-cluster.md).

1. Erstellen Sie eine neue Abfrage, und führen Sie den folgenden Befehl aus, um eine Beispieldatenbank namens **MyTestDatabase** zu erstellen.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

### <a name="load-sample-data-into-hdfs"></a>Laden von Beispieldaten in HDFS

1. Laden Sie [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) auf Ihren lokalen Computer herunter.

1. Starten Sie Azure Data Studio, und [stellen Sie eine Verbindung mit Ihrem Big Data-Cluster her](connect-to-big-data-cluster.md).

1. Klicken Sie mit der rechten Maustaste auf den HDFS-Ordner in Ihrem Big Data-Cluster, und wählen Sie **Neues Verzeichnis** aus. Nennen Sie das Verzeichnis **spark_data**.

1. Klicken Sie mit der rechten Maustaste auf das Verzeichnis **spark_data**, und wählen Sie **Dateien hochladen** aus. Laden Sie die Datei **AdultCensusIncome.csv** hoch.

   ![CSV-Datei „AdultCensusIncome“](./media/spark-mssql-connector/spark_data.png)

### <a name="run-the-sample-notebook"></a>Ausführen des Beispielnotebooks

Zur Veranschaulichung der Verwendung des Apache Spark-Connectors für SQL Server und Azure SQL mit diesen Daten im Modus ohne AD können Sie ein Beispielnotebook herunterladen, dieses in Azure Data Studio öffnen und alle Codeblöcke ausführen. Weitere Informationen zum Arbeiten mit Notebooks finden Sie unter [Verwenden von Notebooks mit SQL Server](../azure-data-studio/notebooks-guidance.md).

1. Führen Sie an einer PowerShell- oder Bash-Befehlszeile den folgenden Befehl aus, um das Beispielnotebook **mssql_spark_connector_non_ad_pyspark.ipynb** herunterzuladen:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector_non_ad_pyspark.ipynb"
   ```

1. Öffnen Sie die Datei mit dem Beispielnotebook in Azure Data Studio. Überprüfen Sie, ob eine Verbindung mit Ihrem HDFS-/Spark-Gateway für Ihren Big Data-Cluster besteht.

1. Führen Sie jede Codezelle im Beispiel aus, um zu sehen, wie der Apache Spark-Connector für SQL Server und Azure SQL verwendet wird.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Cluster finden Sie unter [Vorgehensweise: Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] auf Kubernetes](deployment-guidance.md).

Haben Sie Feedback oder Featurevorschläge für SQL Server-Big Data-Cluster? [Senden Sie uns eine Nachricht über Feedback zu Big Data-Cluster für SQL Server.](https://aka.ms/sql-server-bdc-feedback)
