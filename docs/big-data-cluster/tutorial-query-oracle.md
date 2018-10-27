---
title: Wie Sie Oracle-Abfrage aus einer SQL Server-big Data-Cluster | Microsoft-Dokumentation
description: In diesem Tutorial wird veranschaulicht, wie Oracle-Daten aus einer SQL Server-2019 big Data-Cluster (Vorschau) abgefragt werden. Sie erstellen eine externe Tabelle für Daten in Oracle und anschließend eine Abfrage ausführen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/12/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 7f5383a6faf13f0454439a42efb7524eaeda7c76
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644173"
---
# <a name="tutorial-query-oracle-from-a-sql-server-big-data-cluster"></a>Tutorial: Abfragen von Oracle aus einer SQL Server-big Data-cluster

Dieses Tutorial veranschaulicht, wie Sie Oracle-Daten aus einer SQL Server-2019 big Data-Cluster Abfragen. Um dieses Tutorial ausführen zu können, müssen Sie auf einem Oracle-Server zugreifen. Wenn Sie keinen Zugriff haben, erhalten in diesem Tutorial Sie einen Überblick über die Funktionsweise der Datenvirtualisierung für externe Datenquellen in SQL Server-big Data-Cluster.

In diesem Tutorial erfahren Sie, wie Sie:

> [!div class="checklist"]
> * Erstellen Sie eine externe Tabelle für Daten in einer externen Oracle-Datenbank.
> * Verknüpfen Sie diese Daten mit hohem Wert Daten in der master-Instanz.

> [!TIP]
> Falls gewünscht, können Sie herunterladen und Ausführen eines Skripts für die Befehle in diesem Tutorial. Anweisungen finden Sie in der [Virtualisierung Datenstichproben](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) auf GitHub.

## <a id="prereqs"></a> Erforderliche Komponenten

* [Bereitstellen einen big Data-Cluster in Kubernetes](deployment-guidance.md).
* [Installieren Sie Studio für Azure Data und die Erweiterung für SQL Server-2019](deploy-big-data-tools.md).
* [Laden Sie Beispieldaten in den Cluster](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-oracle-table"></a>Erstellen einer Oracle-Tabelle

Die folgenden Schritte erstellen Sie eine Beispieltabelle namens `INVENTORY` in Oracle.

1. Verbinden Sie mit einer Oracle-Instanz und die Datenbank, die Sie für dieses Tutorial verwenden möchten.

1. Führen Sie die folgende Anweisung zum Erstellen der `INVENTORY` Tabelle:

   ```sql
    CREATE TABLE "INVENTORY"
    (
        "INV_DATE" NUMBER(10,0) NOT NULL,
        "INV_ITEM" NUMBER(10,0) NOT NULL,
        "INV_WAREHOUSE" NUMBER(10,0) NOT NULL,
        "INV_QUANTITY_ON_HAND" NUMBER(10,0)
    );

    CREATE INDEX INV_ITEM ON HR.INVENTORY(INV_ITEM);
    ```

1. Importieren Sie den Inhalt der **inventory.csv** -Datei in dieser Tabelle. Diese Datei wurde erstellt, indem Sie die Beispielskripts für die Erstellung in der [Voraussetzungen](#prereqs) Abschnitt.

## <a name="create-an-external-data-source"></a>Erstellen einer externen Datenquelle

Der erste Schritt ist die Erstellung eine externen Datenquelle, die auf den Oracle-Server zugreifen können.

1. Verbinden Sie in Azure Data Studio mit der SQL Server-Masterinstanz von Ihrer big Data-Cluster. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit der SQL Server-Masterinstanz](deploy-big-data-tools.md#master).

1. Doppelklicken Sie auf die Verbindung in der **Server** Fenster im Server-Dashboard für die master-SQL Server-Instanz angezeigt wird. Wählen Sie **neue Abfrage**.

   ![SQL Server-Masterinstanz-Abfrage](./media/tutorial-query-oracle/sql-server-master-instance-query.png)

1. Führen Sie den folgenden Transact-SQL-Befehl, um den Kontext zum Ändern der **Sales** Datenbank in der master-Instanz.

   ```sql
   USE Sales
   GO
   ```

1. Erstellen Sie datenbankweit gültige Anmeldeinformationen zur Verbindung mit des Oracle-Servers. Geben Sie die entsprechenden Anmeldeinformationen auf dem Oracle-Server in der folgenden Anweisung.

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleCredential]
   WITH IDENTITY = '<oracle_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_user_password,nvarchar(100),manager>';
   ```

1. Erstellen einer externen Datenquelle, die auf dem Oracle-Server verweist.

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',CREDENTIAL = [OracleCredential]);
   ```

## <a name="create-an-external-table"></a>Erstellen einer externen Tabelle

Als Nächstes erstellen Sie eine externe Tabelle, die mit dem Namen **Iventory_ora** über die `INVENTORY` Tabelle auf dem Oracle-Server.

```sql
CREATE EXTERNAL TABLE [inventory_ora]
    ([inv_date] DECIMAL(10,0) NOT NULL, [inv_item] DECIMAL(10,0) NOT NULL,
    [inv_warehouse] DECIMAL(10,0) NOT NULL, [inv_quantity_on_hand] DECIMAL(10,0))
WITH (DATA_SOURCE=[OracleSalesSrvr],
        LOCATION='<oracle_service_name,nvarchar(30),xe>.<oracle_schema,nvarchar(128),HR>.<oracle_table,nvarchar(128),INVENTORY>');
```

> [!NOTE]
> Tabellen- und Spaltennamen verwenden ANSI SQL-Bezeichner in Anführungszeichen, Ausführen von Abfragen für Oracle. Daher sind die Namen von Groß-/Kleinschreibung beachtet. Es ist wichtig, um den Namen in der Definition der externen Tabelle anzugeben, die die exakte Groß-/Kleinschreibung der Tabellen- und Spaltennamen in den Metadaten für Oracle entspricht.

## <a name="query-the-data"></a>Abfragen der Daten

Führen Sie die folgende Abfrage aus, um die Daten zu verknüpfen, der `iventory_ora` externe Tabelle mit den Tabellen in der lokalen `Sales` Datenbank.

```sql
SELECT TOP(100) w.w_warehouse_name, i.inv_item, SUM(i.inv_quantity_on_hand) as total_quantity
  FROM [inventory_ora] as i
  JOIN item as it
    ON it.i_item_sk = i.inv_item
  JOIN warehouse as w
    ON w.w_warehouse_sk = i.inv_warehouse
 WHERE it.i_category = 'Books' and i.inv_item BETWEEN 1 and 18000 --> get items within specific range
 GROUP BY w.w_warehouse_name, i.inv_item;
```

## <a name="clean-up"></a>Bereinigen

Verwenden Sie den folgenden Befehl aus, um die Datenbankobjekte, die in diesem Tutorial erstellten zu entfernen.

```sql
DROP EXTERNAL TABLE [inventory_ora];
DROP EXTERNAL DATA SOURCE [OracleSalesSrvr] ;
DROP DATABASE SCOPED CREDENTIAL [OracleCredential];
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Daten in den Datenpool erfasst werden:
> [!div class="nextstepaction"]
> [Laden von Daten in den Datenpool](tutorial-data-pool-ingest-sql.md)
