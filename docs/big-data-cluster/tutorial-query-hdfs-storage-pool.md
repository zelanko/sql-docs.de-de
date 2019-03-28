---
title: Abfragen von HDFS-Daten im Speicherpool
titleSuffix: SQL Server 2019 big data clusters
description: Dieses Tutorial veranschaulicht, wie Sie HDFS-Daten in eine SQL Server-2019 big Data-Cluster (Vorschau) Abfragen. Sie erstellen eine externe Tabelle für Daten im Speicherpool und anschließend eine Abfrage ausführen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 57851a4e0f4cedde1e630afeca49ff26c971c7b5
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511117"
---
# <a name="tutorial-query-hdfs-in-a-sql-server-big-data-cluster"></a>Tutorial: HDFS-Abfrage in einer SQL Server-big Data-cluster

Dieses Tutorial veranschaulicht, wie Sie HDFS-Daten in eine SQL Server-2019 big Data-Cluster (Vorschau) Abfragen.

In diesem Tutorial erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Erstellen Sie eine externe Tabelle, die auf den HDFS-Daten in einer big Data-Cluster verweist.
> * Verknüpfen Sie diese Daten mit hohem Wert Daten in der master-Instanz.

> [!TIP]
> Falls gewünscht, können Sie herunterladen und Ausführen eines Skripts für die Befehle in diesem Tutorial. Anweisungen finden Sie in der [Virtualisierung Datenstichproben](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

- [Big Data-tools](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
- [Laden Sie Beispieldaten in Ihre big Data-cluster](tutorial-load-sample-data.md)

## <a name="create-an-external-table-to-hdfs"></a>Erstellen einer externen Tabelle in HDFS

Der Speicherpool enthält Web Clickstream-Daten in eine CSV-Datei in HDFS gespeichert. Verwenden Sie die folgenden Schritte aus, um eine externe Tabelle zu definieren, die die Daten in dieser Datei zugreifen kann.

1. Verbinden Sie in Azure Data Studio mit der SQL Server-Masterinstanz von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](connect-to-big-data-cluster.md#master).

1. Doppelklicken Sie auf die Verbindung in der **Server** Fenster im Server-Dashboard für die master-SQL Server-Instanz angezeigt wird. Wählen Sie **neue Abfrage**.

   ![SQL Server-Masterinstanz-Abfrage](./media/tutorial-query-hdfs-storage-pool/sql-server-master-instance-query.png)

1. Führen Sie den folgenden Transact-SQL-Befehl, um den Kontext zum Ändern der **Sales** Datenbank in der master-Instanz.

   ```sql
   USE Sales
   GO
   ```

1. Definieren Sie das Format der CSV-Datei zum Lesen aus HDFS. Drücken Sie F5, um die Anweisung auszuführen.

   ```sql
   CREATE EXTERNAL FILE FORMAT csv_file
   WITH (
       FORMAT_TYPE = DELIMITEDTEXT,
       FORMAT_OPTIONS(
           FIELD_TERMINATOR = ',',
           STRING_DELIMITER = '"',
           FIRST_ROW = 2,
           USE_TYPE_DEFAULT = TRUE)
   );
   ```

1. Erstellen Sie eine externe Datenquelle für den Speicherpool aus, wenn es nicht bereits vorhanden ist.

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
   BEGIN
     IF SERVERPROPERTY('ProductLevel') = 'CTP2.3'
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-mssql-controller:8080');
     ELSE IF SERVERPROPERTY('ProductLevel') = 'CTP2.4'
       CREATE EXTERNAL DATA SOURCE SqlStoragePool
       WITH (LOCATION = 'sqlhdfs://service-master-pool:50070');
   END
   ```

1. Erstellen einer externen Tabelle, die gelesen wird, kann die `/clickstream_data` aus dem Speicherpool. Die **SqlStoragePool** wird von der Masterinstanz von big Data-Cluster zugegriffen werden kann.

   ```sql
   CREATE EXTERNAL TABLE [web_clickstreams_hdfs]
   ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
   WITH
   (
       DATA_SOURCE = SqlStoragePool,
       LOCATION = '/clickstream_data',
       FILE_FORMAT = csv_file
   );
   GO
   ```

## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie die folgende Abfrage aus, um die HDFS-Daten zu verknüpfen, der `web_clickstream_hdfs` externe Tabelle mit relationalen Daten in der lokalen `Sales` Datenbank.

```sql
SELECT  
    wcs_user_sk,
    SUM( CASE WHEN i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
    SUM( CASE WHEN i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
    SUM( CASE WHEN i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
    SUM( CASE WHEN i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
    SUM( CASE WHEN i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
    SUM( CASE WHEN i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
    SUM( CASE WHEN i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
    SUM( CASE WHEN i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
    SUM( CASE WHEN i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
    SUM( CASE WHEN i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
  FROM [dbo].[web_clickstreams_hdfs]
  INNER JOIN item it ON (wcs_item_sk = i_item_sk
                        AND wcs_user_sk IS NOT NULL)
GROUP BY  wcs_user_sk;
GO
```

## <a name="clean-up"></a>Bereinigen

Verwenden Sie den folgenden Befehl aus, um die externe Tabelle, die in diesem Tutorial verwendeten zu entfernen.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_hdfs];
GO
```

## <a name="next-steps"></a>Nächste Schritte

Wechseln Sie zum nächsten Artikel erfahren, wie Sie Oracle aus einer big Data-Cluster Abfragen.
> [!div class="nextstepaction"]
> [Abfragen von externen Daten in Oracle](tutorial-query-oracle.md)
