---
title: Erfassen von Daten in einem SQL Server-Datenpool
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird veranschaulicht, wie Sie Daten in den Daten Pool eines [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]erfassen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f2ae96a04da69835b4b13886637cf87e62996b57
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653313"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>Tutorial: Erfassen von Daten in einem SQL Server-Datenpool mit Transact-SQL

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial wird veranschaulicht, wie Transact-SQL zum Laden von Daten in den [Daten Pool](concept-data-pool.md) eines [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]verwendet wird. Mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]können Daten aus einer Vielzahl von Quellen erfasst und über Daten Pool Instanzen verteilt werden.

In diesem Tutorial lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen einer externen Tabelle im Datenpool
> * Einfügen von Webclickstream-Beispieldaten in die Datenpooltabelle
> * Verknüpfen von Daten aus der Datenpooltabelle mit lokalen Tabellen

> [!TIP]
> Wenn Sie möchten, können Sie ein Skript für die Befehle in diesem Tutorial herunterladen und ausführen. Anweisungen finden Sie in den [Beispielen zu Datenpools](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

- [Big-Data-Tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **Erweiterung von SQL Server 2019**
- [Load sample data into your big data cluster (Laden von Beispieldaten in ihren Big-Data-Cluster)](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>Erstellen einer externen Tabelle im Datenpool

Mit den folgenden Schritten wird eine externe Tabelle namens **web_clickstream_clicks_data_pool** im Datenpool erstellt. Diese Tabelle kann dann als Speicherort für die Erfassung von Daten im Big Data-Cluster verwendet werden.

1. Stellen Sie in Azure Data Studio eine Verbindung mit der SQL Server-Masterinstanz Ihres Big-Data-Clusters her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](connect-to-big-data-cluster.md#master).

1. Doppelklicken Sie im Fenster **Server** auf die Verbindung, um das Serverdashboard der SQL Server-Masterinstanz anzuzeigen. Wählen Sie **Neue Abfrage** aus.

   ![Abfrage der SQL Server-Masterinstanz](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. Führen Sie den folgenden Transact-SQL-Befehl aus, um in der Masterinstanz in den Kontext der **Sales**-Datenbank zu wechseln.

   ```sql
   USE Sales
   GO
   ```

1. Erstellen Sie eine externe Datenquelle für den Datenpool, wenn diese nicht bereits vorhanden ist.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://controller-svc/default');
   ```

1. Erstellen Sie eine externe Tabelle namens **web_clickstream_clicks_data_pool** im Datenpool.

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
  
1. In CTP 3.1 ist die Erstellung des Datenpools asynchron, es existiert bisher jedoch noch keine Möglichkeit zu bestimmen, wann diese abgeschlossen ist. Warten Sie vor dem Ausführen weiterer Aktionen zwei Minuten, um sicherzustellen, dass der Datenpool erstellt wurde.

## <a name="load-data"></a>Laden der Daten

In den folgenden Schritten werden die Webclickstream-Beispieldaten aus der externen Tabelle, die in den vorherigen Schritten erstellt wurde, in den Datenpool eingelesen.

1. Verwenden Sie eine `INSERT INTO`-Anweisung, um die Ergebnisse der Abfrage in den Datenpool (die externe Tabelle **web_clickstream_clicks_data_pool**) einzufügen.

   ```sql
   INSERT INTO web_clickstream_clicks_data_pool
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
     FROM sales.dbo.web_clickstreams_hdfs
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
                           AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;
   ```

1. Überprüfen Sie die eingefügten Daten mit zwei SELECT-Abfragen.

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>Abfragen der Daten

Verknüpfen Sie die gespeicherten Ergebnisse der Abfrage im Datenpool mit lokalen Daten in der **Sales**-Tabelle.

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

## <a name="clean-up"></a>Bereinigung

Verwenden Sie den folgenden Befehl, um die in diesem Tutorial erstellten Datenbankobjekte zu entfernen.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie Daten über Spark-Aufträgen in den Datenpool einlesen:
> [!div class="nextstepaction"]
> [Erfassen von Daten mit Spark-Aufträgen](tutorial-data-pool-ingest-spark.md)
