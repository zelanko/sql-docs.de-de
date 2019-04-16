---
title: Erfassen von Daten in einem Pool der SQL Server-Daten
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird veranschaulicht, wie zum Erfassen von Daten in den Datenpool von einer SQL Server-2019 big Data-Cluster (Vorschau) verwendet wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: eb0bd2639dc2e2738215c51a18d87a3eb771c826
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583433"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>Tutorial: Erfassen von Daten in einen Pool des SQL Server-Daten mit Transact-SQL

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieses Tutorial veranschaulicht, wie Transact-SQL zum Laden von Daten in die [Datenpool](concept-data-pool.md) von einer SQL Server-2019 big Data-Cluster (Vorschau). Mit SQL Server-big Data-Cluster können Daten aus einer Vielzahl von Quellen erfasst und Daten-poolinstanzen verteilt werden.

In diesem Tutorial erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Erstellen Sie eine externe Tabelle, in dem Datenpool.
> * Legen Sie Beispiel-Web-Websites Clickstream-Daten in der Datentabelle für den Pool ein.
> * Daten werden in der Datentabelle der Pool mit lokalen Tabellen verknüpft.

> [!TIP]
> Falls gewünscht, können Sie herunterladen und Ausführen eines Skripts für die Befehle in diesem Tutorial. Anweisungen finden Sie in der [Daten pools, Beispielen](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

- [Big Data-tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
- [Laden Sie Beispieldaten in Ihre big Data-cluster](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Erstellen Sie eine externe Tabelle, in dem Datenpool

Die folgenden Schritte Erstellen einer externen Tabelle, in dem Datenpool mit dem Namen **Web_clickstream_clicks_data_pool**. Diese Tabelle kann dann als einen Speicherort für die sammelerfassung von Daten in die big Data-Cluster verwendet werden.

1. Verbinden Sie in Azure Data Studio mit der SQL Server-Masterinstanz von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](connect-to-big-data-cluster.md#master).

1. Doppelklicken Sie auf die Verbindung in der **Server** Fenster im Server-Dashboard für die master-SQL Server-Instanz angezeigt wird. Wählen Sie **neue Abfrage**.

   ![SQL Server-Masterinstanz-Abfrage](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Führen Sie den folgenden Transact-SQL-Befehl, um den Kontext zum Ändern der **Sales** Datenbank in der master-Instanz.

   ```sql
   USE Sales
   GO
   ```

1. Erstellen Sie eine externe Datenquelle für den Datenpool aus, wenn nicht bereits vorhanden.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://service-mssql-controller:8080/datapools/default');
   ```

1. Erstellen einer externen Tabelle, die mit dem Namen **Web_clickstream_clicks_data_pool** im Datenpool.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstream_clicks_data_pool')
      CREATE EXTERNAL TABLE [web_clickstream_clicks_data_pool]
      ("wcs_user_sk" BIGINT , "i_category_id" BIGINT , "clicks" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. In der CTP-Version 2.4 die Erstellung des Pools Daten ist asynchron, aber es gibt keine Möglichkeit, um zu bestimmen, wenn er noch abgeschlossen ist. Warten Sie zwei Minuten lang, um sicherzustellen, dass die Datenpool erstellt wird, bevor Sie fortfahren.

## <a name="load-data"></a>Laden von Daten

Die folgenden Schritte aus erfassungs-Beispiel-Web-Websites Clickstream-Daten in den Datenpool mit der externen Tabelle, die in den vorherigen Schritten erstellt haben.

1. Definieren Sie Variablen für die Abfrage, die Sie zum Einfügen von Daten in den Datenpool für verwenden möchten. Für CTP 2.3 oder früher die **Modell... Sp_data_pool_table_insert_data** gespeicherte Prozedur ist erforderlich. Für CTP 2.4 und höher können Sie eine `INSERT INTO` Anweisung, um die Ergebnisse der Abfrage in den Datenpool für einzufügen (die **Web_clickstream_clicks_data_pool** externe Tabelle).

   ```sql
   IF SERVERPROPERTY('ProductLevel') = 'CTP2.4'
   BEGIN
      INSERT INTO web_clickstream_clicks_data_pool
      SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
        FROM sales.dbo.web_clickstreams_hdfs_parquet
      INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
                              AND wcs_user_sk IS NOT NULL)
      GROUP BY wcs_user_sk, i_category_id
      HAVING COUNT_BIG(*) > 100;
   END

   ELSE IF SERVERPROPERTY('ProductLevel') = 'CTP2.3'
   BEGIN
      DECLARE @db_name SYSNAME = 'Sales'
      DECLARE @schema_name SYSNAME = 'dbo'
      DECLARE @table_name SYSNAME = 'web_clickstream_clicks_data_pool'
      DECLARE @query NVARCHAR(MAX) = '
      SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
      FROM sales.dbo.web_clickstreams
      INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
         AND wcs_user_sk IS NOT NULL)
      GROUP BY wcs_user_sk, i_category_id
      HAVING COUNT_BIG(*) > 100;'

      EXEC model..sp_data_pool_table_insert_data @db_name, @schema_name, @table_name, @query
   END
   ```

1. Überprüfen Sie die eingefügten Daten mit zwei SELECT-Abfragen.

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>Abfragen der Daten

Verknüpfen Sie die gespeicherten Ergebnisse aus der Abfrage in den Datenpool mit lokalen Daten in die **Sales** Tabelle.

```sql
SELECT TOP (100)
   w.wcs_user_sk,
   SUM( CASE WHEN i.i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
   SUM( CASE WHEN w.i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
   SUM( CASE WHEN w.i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
   SUM( CASE WHEN w.i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
   SUM( CASE WHEN w.i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
   SUM( CASE WHEN w.i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
   SUM( CASE WHEN w.i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
   SUM( CASE WHEN w.i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
   SUM( CASE WHEN w.i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
   SUM( CASE WHEN w.i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
FROM [dbo].[web_clickstream_clicks_data_pool] as w
INNER JOIN (SELECT DISTINCT i_category_id, i_category FROM item) as i
   ON i.i_category_id = w.i_category_id
GROUP BY w.wcs_user_sk;
```

## <a name="clean-up"></a>Bereinigen

Verwenden Sie den folgenden Befehl aus, um die Datenbankobjekte, die in diesem Tutorial erstellten zu entfernen.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Erfassen von Daten in den Datenpool für mit Spark-Aufträgen:
> [!div class="nextstepaction"]
> [Erfassen von Daten mit Spark-Aufträgen](tutorial-data-pool-ingest-spark.md)
