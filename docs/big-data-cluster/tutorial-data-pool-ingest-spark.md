---
title: Erfassen von Daten mit Spark-Aufträgen
titleSuffix: SQL Server 2019 big data clusters
description: In diesem Tutorial wird veranschaulicht, wie Daten in den Datenpool mit einer SQL Server-2019 big Data-Cluster (Vorschau) mit dem Spark-Aufträgen in Azure Data Studio erfasst wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 1611a8b0513e8f1a9e50d3cc612b114c88698df5
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58491903"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Tutorial: Erfassen von Daten in einen Pool des SQL Server-Daten mit Spark-Aufträgen

Dieses Tutorial veranschaulicht, wie Spark-Aufträgen zum Laden von Daten in die [Datenpool](concept-data-pool.md) von einer SQL Server-2019 big Data-Cluster (Vorschau). 

In diesem Tutorial erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Erstellen Sie eine externe Tabelle, in dem Datenpool.
> * Erstellen Sie einen Spark-Auftrag, um Daten aus HDFS zu laden.
> * Fragen Sie die Ergebnisse in der externen Tabelle.

> [!TIP]
> Falls gewünscht, können Sie herunterladen und Ausführen eines Skripts für die Befehle in diesem Tutorial. Anweisungen finden Sie in der [Daten pools, Beispielen](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

- [Big Data-tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
- [Laden Sie Beispieldaten in Ihre big Data-cluster](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Erstellen Sie eine externe Tabelle, in dem Datenpool

Die folgenden Schritte Erstellen einer externen Tabelle, in dem Datenpool mit dem Namen **Web_clickstreams_spark_results**. Diese Tabelle kann dann als einen Speicherort für die sammelerfassung von Daten in die big Data-Cluster verwendet werden.

1. Verbinden Sie in Azure Data Studio mit der SQL Server-Masterinstanz von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](connect-to-big-data-cluster.md#master).

1. Doppelklicken Sie auf die Verbindung in der **Server** Fenster im Server-Dashboard für die master-SQL Server-Instanz angezeigt wird. Wählen Sie **neue Abfrage**.

   ![SQL Server-Masterinstanz-Abfrage](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. Erstellen Sie eine externe Datenquelle für den Datenpool aus, wenn nicht bereits vorhanden.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
   ```

1. Erstellen einer externen Tabelle, die mit dem Namen **Web_clickstreams_spark_results** im Datenpool.

   ```sql
   USE Sales
   GO
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstreams_spark_results')
      CREATE EXTERNAL TABLE [web_clickstreams_spark_results]
      ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. In der CTP-Version 2.4 die Erstellung des Pools Daten ist asynchron, aber es gibt keine Möglichkeit, um zu bestimmen, wenn er noch abgeschlossen ist. Warten Sie zwei Minuten lang, um sicherzustellen, dass die Datenpool erstellt wird, bevor Sie fortfahren.

## <a name="start-a-spark-streaming-job"></a>Starten eines Streamingauftrags

Der nächste Schritt ist die Erstellung ein Streamingauftrags, die Web-Clickstream-Daten aus dem Speicherpool (HDFS) lädt in der externen Tabelle, die Sie in den Datenpool erstellt haben.

1. In Azure Data Studio, eine Verbindung mit der **HDFS/Spark-Gateway** von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit dem HDFS/Spark-Gateway](connect-to-big-data-cluster.md#hdfs).

1. Doppelklicken Sie auf das HDFS/Spark-Gateway-Verbindung in der **Server** Fenster. Wählen Sie dann **neue Spark-Auftrag**.

   ![Neue Spark-Auftrag](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. In der **neuer Auftrag** Fenster, geben Sie einen Namen in der **Auftragsname** Feld.

1. In der **Jar/Py-Datei** Dropdown-Menü, Option **HDFS**. Geben Sie dann den folgenden Pfad der JAR-Datei:

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. In der **Hauptklasse** Feld `FileStreaming`.

1. In der **Argumente** Geben Sie den folgenden Text, der das Kennwort an, in der SQL Server-Masterinstanz angeben der `<your_password>` Platzhalter. 

   ```text
   --server mssql-master-pool-0.service-master-pool --port 1433 --user sa --password <your_password> --database sales --table web_clickstreams_spark_results --source_dir hdfs:///clickstream_data --input_format csv --enable_checkpoint false --timeout 380000
   ```

   Die folgende Tabelle beschreibt jedes Argument:

   | Argument | Description |
   |---|---|
   | Servername | Verwenden von SQL Server für das Lesen des Tabellenschemas |
   | Portnummer | Die SQL Server Port lauscht (standardmäßig 1433) |
   | username | SQL Server einen Benutzernamen ein |
   | Kennwort | SQL Server-Anmeldekennworts |
   | Datenbanknamen | Zieldatenbank |
   | Name der externen Tabelle | Die Tabelle zu verwenden, um Ergebnisse zu erzielen |
   | Quellverzeichnis für das streaming | Dies muss ein vollständiger URI an, wie z. B. "Hdfs: / / / Clickstream_data" |
   | Eingabeformat | Dies kann "Csv", "Parquet" oder "Json" sein. |
   | Aktivieren der Prüfpunkt | true oder false |
   | timeout | Zeit für die auftragsausführung für in Millisekunden vor dem Beenden |

1. Drücken Sie **senden** auf den Auftrag zu übermitteln.

   ![Spark-Auftrag übermitteln](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

## <a name="query-the-data"></a>Abfragen der Daten

Die folgenden Schritte zeigen, dass im Spark-streaming-Auftrag die Daten aus HDFS in den Datenpool für die geladen werden.

1. Sehen Sie bevor Sie Abfragen, die erfassten Daten sich in der taskausgabe Verlauf, um festzustellen, ob der Auftrag wurde abgeschlossen.

   ![Spark-Auftragsverlauf](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. Gibt zurück, in der SQL Server-Masterinstanz Abfragefenster, das Sie am Anfang dieses Tutorials geöffnet.

1. Führen Sie die folgende Abfrage aus, um die erfassten Daten zu überprüfen.

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```

## <a name="clean-up"></a>Bereinigen

Verwenden Sie den folgenden Befehl aus, um die Datenbankobjekte, die in diesem Tutorial erstellten zu entfernen.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie ein Beispiel-Notebook in Azure Data Studio ausführen:
> [!div class="nextstepaction"]
> [Führen Sie ein Beispiel-notebook](tutorial-notebook-spark.md)
