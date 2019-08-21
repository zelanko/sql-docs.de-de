---
title: Verbinden von Spark mit SQL Server
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie den MSSQL-Spark-Connector in Spark zum Lesen und Schreiben von Daten in SQL Server verwenden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3ad3a0e03c75f7961864f70fc52655e47e2b89ea
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653300"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>Lesen und Schreiben von Daten in SQL Server aus Spark mithilfe des MSSQL-Spark-Connectors

Ein sehr wichtiges Muster für die Big Data-Nutzung ist die Verarbeitung großer Datenvolumen in Spark und das anschließende Schreiben der Daten in SQL Server, damit Branchenanwendungen darauf zugreifen können. Diese Nutzungsmuster profitieren von einem Connector, der wichtige SQL-Optimierungen nutzt und einen effizienten Schreibmechanismus bereitstellt.

In diesem Artikel wird anhand eines Beispiels erläutert, wie Sie den MSSQL-Spark-Connector verwenden, um Daten in folgenden Speicherorten innerhalb eines Big Data-Clusters zu lesen und zu schreiben:

1. SQL Server-Masterinstanz
1. SQL Server-Datenpool

   ![Diagramm: MSSQL-Spark-Connector](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

Das Beispiel führt die folgenden Aufgaben aus:

- Lesen einer Datei aus HDFS und Ausführen einiger grundlegender Verarbeitungsschritte
- Schreiben des Dataframes in eine SQL Server-Masterinstanz als SQL-Tabelle und Einlesen der Tabelle in einen Dataframe
- Schreiben des Dataframes in einen SQL Server-Datenpool als externe SQL-Tabelle und Einlesen der externen Tabelle in einen Dataframe

## <a name="mssql-spark-connector-interface"></a>Schnittstelle des MSSQL-Spark-Connectors

SQL Server 2019 (Vorschauversion) stellt den **MSSQL-Spark-Connector** für Big Data-Cluster bereit, die SQL Server-APIs für Massenschreibvorgänge zum Schreiben von Spark in SQL verwenden. Der MSSQL-Spark-Connector basiert auf Datenquellen-APIs von Spark und stellt eine vertraute Spark-JDBC-Connectorschnittstelle bereit. Informationen zu den Parametern der Schnittstelle finden Sie in der [Apache Spark-Dokumentation](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html). Der MSSQL-Spark-Connector wird als **com.microsoft.sqlserver.jdbc.spark** referenziert.

Die folgende Tabelle beschreibt neue oder geänderte Schnittstellenparameter:

| Eigenschaftenname | Optional | Beschreibung |
|---|---|---|
| **isolationLevel** | Ja | Beschreibt die Isolationsstufe der Verbindung. Der Standardwert für den MSSQL-Spark-Connector lautet **READ_COMMITTED**. |

Der Connector verwendet SQL Server-APIs für Massenschreibvorgänge. Alle Parameter für Massenschreibvorgänge können vom Benutzer als optionale Parameter übergeben werden und werden vom Connector unverändert an die zugrunde liegende API übergeben. Weitere Informationen zu Massenschreibvorgängen finden Sie unter [SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Ein [SQL Server-Big Data-Cluster](deploy-get-started.md)

- [Azure Data Studio](https://aka.ms/azdata-insiders)

## <a name="create-the-target-database"></a>Erstellen der Zieldatenbank

1. Öffnen Sie Azure Data Studio, und [stellen Sie eine Verbindung mit der SQL Server-Masterinstanz Ihres Big Data-Clusters her](connect-to-big-data-cluster.md).

1. Erstellen Sie eine neue Abfrage, und führen Sie den folgenden Befehl aus, um eine Beispieldatenbank namens **MyTestDatabase** zu erstellen.

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>Laden von Beispieldaten in HDFS

1. Laden Sie [AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv) auf Ihren lokalen Computer herunter.

1. Starten Sie Azure Data Studio, und [stellen Sie eine Verbindung mit Ihrem Big Data-Cluster her](connect-to-big-data-cluster.md).

1. Klicken Sie mit der rechten Maustaste auf den HDFS-Ordner in Ihrem Big Data-Cluster, und wählen Sie **Neues Verzeichnis** aus. Nennen Sie das Verzeichnis **spark_data**.

1. Klicken Sie mit der rechten Maustaste auf das Verzeichnis **spark_data**, und wählen Sie **Dateien hochladen** aus. Laden Sie die Datei **AdultCensusIncome.csv** hoch.

   ![CSV-Datei „AdultCensusIncome“](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>Ausführen des Beispielnotebooks

Um sich die Verwendung des MSSQL-Spark-Connectors mit diesen Daten anzusehen, können Sie ein Beispielnotebook herunterladen, es in Azure Data Studio öffnen und jeden Codeblock ausführen. Weitere Informationen zum Arbeiten mit Notebooks finden Sie unter [Verwenden von Notebooks in SQL Server 2019 (Vorschauversion)](notebooks-guidance.md).

1. Führen Sie an einer PowerShell- oder Bash-Befehlszeile den folgenden Befehl aus, um das Beispielnotebook **mssql_spark_connector.ipynb** herunterzuladen:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector.ipynb"
   ```

1. Öffnen Sie die Datei mit dem Beispielnotebook in Azure Data Studio. Überprüfen Sie, ob eine Verbindung mit Ihrem HDFS-/Spark-Gateway für Ihren Big Data-Cluster besteht.

1. Führen Sie jede Codezelle im Beispiel aus, um sich die Verwendung des MSSQL-Spark-Connectors anzusehen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden [Sie [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ](deployment-guidance.md) unter Bereitstellen auf Kubernetes