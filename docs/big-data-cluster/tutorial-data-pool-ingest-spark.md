---
title: Erfassen von Daten mit Spark-Aufträgen
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird veranschaulicht, wie Daten mithilfe von Spark-Aufträgen in Azure Data Studio in den Daten Pool einer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] erfasst werden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5ffc2773144d2b1a170e2f087d7abf607af99ef6
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049859"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Tutorial: Erfassen von Daten in einem SQL Server-Daten Pool mit Spark-Aufträgen

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial wird veranschaulicht, wie Sie Spark-Aufträge verwenden, um Daten in den [Daten Pool](concept-data-pool.md) einer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]zu laden. 

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen einer externen Tabelle im Datenpool
> * Erstellen eines Spark-Auftrags zum Laden von Daten aus HDFS
> * Abfragen der Ergebnisse in der externen Tabelle

> [!TIP]
> Wenn Sie möchten, können Sie ein Skript für die Befehle in diesem Tutorial herunterladen und ausführen. Anweisungen finden Sie in den [Beispielen zu Datenpools](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) auf GitHub.

## <a id="prereqs"></a> Prerequisites

- [Big-Data-Tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019-Erweiterung**
- [Laden von Beispieldaten in Ihren Big Data-Cluster](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Erstellen einer externen Tabelle im Datenpool

Mit den folgenden Schritten wird eine externe Tabelle mit dem Namen **web_clickstreams_spark_results** im Datenpool erstellt. Diese Tabelle kann dann als Speicherort für die Erfassung von Daten im Big-Data-Cluster verwendet werden.

1. Stellen Sie in Azure Data Studio eine Verbindung mit der SQL Server-Masterinstanz Ihres Big Data-Clusters her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](connect-to-big-data-cluster.md#master).

1. Doppelklicken Sie im Fenster **Server** auf die Verbindung, um das Serverdashboard der SQL Server-Masterinstanz anzuzeigen. Wählen Sie **Neue Abfrage** aus.

   ![Abfrage der SQL Server-Masterinstanz](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. Erstellen Sie eine externe Datenquelle für den Datenpool, wenn diese nicht bereits vorhanden ist.

   ```sql
   USE Sales
   GO
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://controller-svc/default');
   ```

1. Erstellen Sie eine externe Tabelle mit dem Namen **web_clickstreams_spark_results** im Datenpool.

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
  
1. In CTP 3.1 ist die Erstellung des Datenpools asynchron, es existiert bisher jedoch noch keine Möglichkeit zu bestimmen, wann diese abgeschlossen ist. Warten Sie zwei Minuten, bevor Sie fortfahren, um sicherzustellen, dass der Datenpool erstellt wurde.

## <a name="start-a-spark-streaming-job"></a>Starten eines Spark-Streamingauftrags

Im nächsten Schritt erstellen Sie einen Spark-Streamingauftrag, der Webclickstreamdaten aus dem Speicherpool (HDFS) in die externe Tabelle lädt, die Sie im Datenpool erstellt haben. Diese Daten wurden/clickstream_data in Laden von [Beispiel Daten in ihren Big Data Cluster](tutorial-load-sample-data.md)hinzugefügt.

1. Stellen Sie in Azure Data Studio eine Verbindung mit der Masterinstanz Ihres Big-Data-Clusters her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Big-Data-Cluster](connect-to-big-data-cluster.md).

2. Erstellen Sie ein neues Notebook, und wählen Sie Spark aus. Scala als Kernel.

3. Ausführen des Spark-Erfassungs Auftrags
   1. Konfigurieren der Parameter für den Spark-SQL-Connector
      ```
      import org.apache.spark.sql.types._
      import org.apache.spark.sql.{SparkSession, SaveMode, Row, DataFrame}

      // Change per your installation
      val user= "username"
      val password= "****"
      val database =  "MyTestDatabase"
      val sourceDir = "/clickstream_data"
      val datapool_table = "web_clickstreams_spark_results"
      val datasource_name = "SqlDataPool"
      val schema = StructType(Seq(
      StructField("wcs_click_date_sk",IntegerType,true), StructField("wcs_click_time_sk",IntegerType,true), StructField("wcs_sales_sk",IntegerType,true), StructField("wcs_item_sk",IntegerType,true), 
      StructField("wcs_web_page_sk",IntegerType,true), StructField("wcs_user_sk",IntegerType,true)
      ))

      val hostname = "master-0.master-svc"
      val port = 1433
      val url = s"jdbc:sqlserver://${hostname}:${port};database=${database};user=${user};password=${password};"
      ```
   2. Definieren und Ausführen des Spark-Auftrags
      * Jeder Auftrag besteht aus zwei Teilen: "leserstream" und "Write-Stream". Im folgenden wird ein Datenrahmen mit dem oben definierten Schema erstellt und anschließend in die externe Tabelle im Daten Pool geschrieben.
      ```
      import org.apache.spark.sql.{SparkSession, SaveMode, Row, DataFrame}
      
      val df = spark.readStream.format("csv").schema(schema).option("header", true).load(sourceDir)
      val query = df.writeStream.outputMode("append").foreachBatch{ (batchDF: DataFrame, batchId: Long) => 
                batchDF.write
                 .format("com.microsoft.sqlserver.jdbc.spark")
                 .mode("append")
                  .option("url", url)
                  .option("dbtable", datapool_table)
                  .option("user", user)
                  .option("password", password)
                  .option("dataPoolDataSource",datasource_name).save()
               }.start()

      query.processAllAvailable()
      query.awaitTermination(40000)
      ```
## <a name="query-the-data"></a>Abfragen der Daten

Die folgenden Schritte zeigen, dass der Spark-Streamingauftrag die Daten aus HDFS in den Datenpool geladen hat.

1. Bevor Sie die erfassten Daten abfragen, sehen Sie sich die Ausgabe des Aufgabenverlaufs an, um sicherzustellen, dass der Auftrag abgeschlossen wurde.

   ![Spark-Auftragsverlauf](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. Wechseln Sie zurück zum Abfragefenster der SQL Server-Masterinstanz, das Sie zu Beginn des Tutorials geöffnet haben.

1. Führen Sie die folgende Abfrage aus, um die erfassten Daten zu überprüfen.

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```
1. Die Daten können auch in Spark abgefragt werden. Der folgende Code gibt beispielsweise die Anzahl der Datensätze in der Tabelle aus:
   ```
   def df_read(dbtable: String,
                url: String,
                dataPoolDataSource: String=""): DataFrame = {
        spark.read
             .format("com.microsoft.sqlserver.jdbc.spark")
             .option("url", url)
             .option("dbtable", dbtable)
             .option("user", user)
             .option("password", password)
             .option("dataPoolDataSource", dataPoolDataSource)
             .load()
             }

   val new_df = df_read(datapool_table, url, dataPoolDataSource=datasource_name)
   println("Number of rows is " +  new_df.count)
   ```
## <a name="clean-up"></a>Bereinigung

Verwenden Sie den folgenden Befehl, um die in diesem Tutorial erstellten Datenbankobjekte zu entfernen.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie in Azure Data Studio ein Beispielnotebook ausführen:
> [!div class="nextstepaction"]
> [Run a sample notebook (Ausführen eines Beispielnotebooks)](tutorial-notebook-spark.md)
