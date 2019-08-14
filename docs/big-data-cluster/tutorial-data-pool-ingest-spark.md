---
title: Erfassen von Daten mit Spark-Aufträgen
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird veranschaulicht, wie Daten mithilfe von Spark-Aufträgen in Azure Data Studio im Datenpool eines Big-Data-Clusters für SQL Server 2019 (Vorschauversion) erfasst werden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 06/26/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6d0ea6d4fb7a3aea9788c089ad68cb3bf523837f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67957814"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>Lernprogramm: Erfassen von Daten in einem SQL Server-Datenpool mithilfe von Spark-Aufträgen

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial wird veranschaulicht, wie Daten mithilfe von Spark-Aufträgen in den [Datenpool](concept-data-pool.md) eines Big-Data-Clusters für SQL Server 2019 (Vorschauversion) geladen werden. 

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen einer externen Tabelle im Datenpool
> * Erstellen eines Spark-Auftrags zum Laden von Daten aus HDFS
> * Abfragen der Ergebnisse in der externen Tabelle

> [!TIP]
> Wenn Sie möchten, können Sie ein Skript für die Befehle in diesem Tutorial herunterladen und ausführen. Anweisungen finden Sie in den [Beispielen zu Datenpools](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

- [Big-Data-Tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Erweiterung von SQL Server 2019**
- [Load sample data into your big data cluster (Laden von Beispieldaten in ihren Big-Data-Cluster)](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Erstellen einer externen Tabelle im Datenpool

Mit den folgenden Schritten wird eine externe Tabelle mit dem Namen **web_clickstreams_spark_results** im Datenpool erstellt. Diese Tabelle kann dann als Speicherort für die Erfassung von Daten im Big-Data-Cluster verwendet werden.

1. Stellen Sie in Azure Data Studio eine Verbindung mit der SQL Server-Masterinstanz Ihres Big-Data-Clusters her. Weitere Informationen finden Sie unter [Connect to the SQL Server master instance (Herstellen einer Verbindung mit der SQL Server-Masterinstanz)](connect-to-big-data-cluster.md#master).

1. Doppelklicken Sie auf die Verbindung im Fenster **Server**, um das Serverdashboard der SQL Server-Masterinstanz anzuzeigen. Wählen Sie **Neue Abfrage** aus.

   ![Abfrage in der SQL Server-Masterinstanz](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. Erstellen Sie eine externe Datenquelle für den Datenpool, wenn diese nicht bereits vorhanden ist.

   ```sql
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

Im nächsten Schritt erstellen Sie einen Spark-Streamingauftrag, der Webclickstreamdaten aus dem Speicherpool (HDFS) in die externe Tabelle lädt, die Sie im Datenpool erstellt haben.

1. Stellen Sie in Azure Data Studio eine Verbindung mit der Masterinstanz Ihres Big-Data-Clusters her. Weitere Informationen finden Sie unter [Connect to a big data cluster (Herstellen einer Verbindung mit einem Big-Data-Cluster)](connect-to-big-data-cluster.md).

1. Doppelklicken Sie im Fenster **Server** auf die HDFS/Spark-Gatewayverbindung. Wählen Sie dann **New Spark Job** (Neuer Spark-Auftrag) aus.

   ![Neuer Spark-Auftrag](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. Geben Sie im Fenster **Neuer Auftrag** einen Namen in das Feld **Auftragsname** ein.

1. Wählen Sie im Dropdownmenü **Jar/py File** (JAR-/PY-Datei) die Option **HDFS** aus. Geben Sie dann den folgenden JAR-Dateipfad ein:

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. Geben Sie `FileStreaming` in das Feld **Main Class** (Hauptklasse) ein.

1. Geben Sie in das Feld **Argumente** den folgenden Text ein, und geben Sie das Kennwort für die SQL Server-Masterinstanz über den Platzhalter `<your_password>` an. 

   ```text
   --server mssql-master-pool-0.service-master-pool --port 1433 --user sa --password <your_password> --database sales --table web_clickstreams_spark_results --source_dir hdfs:///clickstream_data --input_format csv --enable_checkpoint false --timeout 380000
   ```

   In der folgenden Tabelle wird jedes Argument beschrieben:

   | Argument | und Beschreibung |
   |---|---|
   | Servername | Die zum Lesen des Tabellenschemas verwendete SQL Server-Instanz |
   | Portnummer | Der Port, an dem SQL Server lauscht (Standard: 1433) |
   | username | Benutzername für die SQL Server-Anmeldung |
   | Kennwort | Kennwort für die SQL Server-Anmeldung |
   | Datenbanknamen | Zieldatenbank |
   | Name der externen Tabelle | Die Tabelle, die für Ergebnisse verwendet werden soll |
   | Quellverzeichnis für Streaming | Muss ein vollständiger URI sein, z. B. „hdfs:///clickstream_data“ |
   | Eingabeformat | Kann „csv“, „parquet“ oder „json“ sein |
   | Prüfpunkt aktivieren | true oder false |
   | timeout | Zeit (in Millisekunden) zum Ausführen des Auftrags vor dem Beenden |

1. Klicken Sie auf **Submit** (Absenden), um den Auftrag zu übermitteln.

   ![Übermitteln des Spark-Auftrags](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

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

## <a name="clean-up"></a>Bereinigung

Verwenden Sie den folgenden Befehl, um die in diesem Tutorial erstellten Datenbankobjekte zu entfernen.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie in Azure Data Studio ein Beispielnotebook ausführen:
> [!div class="nextstepaction"]
> [Run a sample notebook (Ausführen eines Beispielnotebooks)](tutorial-notebook-spark.md)
