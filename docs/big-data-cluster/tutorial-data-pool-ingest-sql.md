---
title: 'Gewusst wie: Erfassen von Daten in einen Pool des SQL Server-Daten mit Transact-SQL | Microsoft-Dokumentation'
description: In diesem Tutorial wird veranschaulicht, wie zum Erfassen von Daten in den Datenpool von einer SQL Server-2019 big Data-Cluster (Vorschau) mit der Sp_data_pool_table_insert_data, die gespeicherte Prozedur wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/16/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: c909379c92b2eb9a98c1c191987570946a8cc002
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644164"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>Tutorial: Erfassen von Daten in einen Pool des SQL Server-Daten mit Transact-SQL

Dieses Tutorial veranschaulicht, wie Transact-SQL zum Laden von Daten in die [Datenpool](concept-data-pool.md) von einer SQL Server-2019 big Data-Cluster (Vorschau). Mit SQL Server-big Data-Cluster können Daten aus einer Vielzahl von Quellen erfasst und Daten-poolinstanzen verteilt werden.

In diesem Tutorial erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Erstellen Sie eine externe Tabelle, in dem Datenpool.
> * Legen Sie Beispiel-Web-Websites Clickstream-Daten in der Datentabelle für den Pool ein.
> * Daten werden in der Datentabelle der Pool mit lokalen Tabellen verknüpft.

> [!TIP]
> Falls gewünscht, können Sie herunterladen und Ausführen eines Skripts für die Befehle in diesem Tutorial. Anweisungen finden Sie in der [Daten pools, Beispielen](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

* [Bereitstellen einen big Data-Cluster in Kubernetes](deployment-guidance.md).
* [Installieren Sie Studio für Azure Data und die Erweiterung für SQL Server-2019](deploy-big-data-tools.md).
* [Laden Sie Beispieldaten in den Cluster](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-in-the-data-pool"></a>Erstellen Sie eine externe Tabelle, in dem Datenpool

Die folgenden Schritte Erstellen einer externen Tabelle, in dem Datenpool mit dem Namen **Web_clickstream_clicks_data_pool**. Diese Tabelle kann dann als einen Speicherort für die sammelerfassung von Daten in die big Data-Cluster verwendet werden.

1. Verbinden Sie in Azure Data Studio mit der SQL Server-Masterinstanz von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](deploy-big-data-tools.md#master).

1. Doppelklicken Sie auf die Verbindung in der **Server** Fenster im Server-Dashboard für die master-SQL Server-Instanz angezeigt wird. Wählen Sie **neue Abfrage**.

   ![SQL Server-Masterinstanz-Abfrage](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Führen Sie den folgenden Transact-SQL-Befehl, um den Kontext zum Ändern der **Sales** Datenbank in der master-Instanz.

   ```sql
   USE Sales
   GO
   ```

1. Erstellen einer externen Tabelle, die mit dem Namen **Web_clickstream_clicks_data_pool** im Datenpool. Die `SqlDataPool` Datenquelle ist eine spezielle Datenquellentyp, die von der Masterinstanz von alle big Data-Cluster verwendet werden kann.

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
  
1. In CTP 2.0 die Erstellung des Pools Daten ist asynchron, aber es gibt keine Möglichkeit, um zu bestimmen, wenn er noch abgeschlossen ist. Warten Sie zwei Minuten lang, um sicherzustellen, dass die Datenpool erstellt wird, bevor Sie fortfahren.

## <a name="load-data"></a>Laden von Daten

Die folgenden Schritte aus erfassungs-Beispiel-Web-Websites Clickstream-Daten in den Datenpool mit der externen Tabelle, die in den vorherigen Schritten erstellt haben.

1. Definieren Sie Variablen für die Abfrage, die Sie zum Einfügen von Daten in den Datenpool für verwenden möchten. Verwenden Sie dann die **Modell... Sp_data_pool_table_insert_data** gespeicherte Prozedur zum Einfügen von der Ergebnis aus der Abfrage in der Datenpool (die **Web_clickstream_clicks_data_pool** externe Tabelle).

   ```sql
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
