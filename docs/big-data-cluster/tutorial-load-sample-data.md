---
title: Laden von Beispieldaten
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird veranschaulicht, wie Beispiel Daten in einen SQL Server Big Data Cluster geladen werden. Die Beispiel Daten enthalten relationale Daten in der SQL Server Master Instanz. Außerdem sind HDFS-Daten im Speicherpool enthalten. Diese Daten unterstützen andere Tutorials in diesem Abschnitt.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5b35eccece4df47cb483932386cf6a38e45d2dc8
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419274"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Tutorial: Laden von Beispiel Daten in einen SQL Server Big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial wird erläutert, wie Sie ein Skript zum Laden von Beispiel Daten in einen SQL Server 2019 Big Data-Cluster (Vorschau) verwenden. In vielen der anderen Tutorials in der Dokumentation werden diese Beispiel Daten verwendet.

> [!TIP]
> Weitere Beispiele für SQL Server 2019 Big Data Cluster (Vorschau) finden Sie im GitHub-Repository für [SQL Server-Beispiele](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) . Sie befinden sich im **SQL-Server-Samples/Samples/Features/SQL-Big-Data-Cluster/** Path.

## <a name="prerequisites"></a>Vorraussetzungen

- [Ein bereitgestellter Big Data Cluster](deployment-guidance.md)
- [Big Data-Tools](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a>Laden von Beispiel Daten

In den folgenden Schritten wird ein Bootstrap-Skript zum Herunterladen einer SQL Server-Datenbanksicherung und zum Laden der Daten in ihren Big Data Cluster verwendet. Zur Erleichterung der Verwendung wurden diese Schritte in [Windows](#windows) -und [Linux](#linux) -Abschnitte aufgeteilt.

## <a id="windows"></a>Windows

In den folgenden Schritten wird beschrieben, wie Sie einen Windows-Client verwenden, um die Beispiel Daten in ihren Big Data-Cluster zu laden.

1. Öffnen Sie eine neue Windows-Eingabeaufforderung.

   > [!IMPORTANT]
   > Verwenden Sie für diese Schritte nicht Windows PowerShell. In PowerShell kann das Skript nicht ausgeführt werden, da es die PowerShell-Version von **curl**verwendet.

1. Verwenden Sie **curl** , um das Bootstrap-Skript für die Beispiel Daten herunterzuladen.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Laden Sie das Transact-SQL-Skript **Bootstrap-Sample-DB. SQL** herunter. Dieses Skript wird vom Bootstrap-Skript aufgerufen.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Das Bootstrap-Skript erfordert die folgenden Positions Parameter für Ihren Big Data Cluster:

   | Parameter | Beschreibung |
   |---|---|
   | < CLUSTER_NAMESPACE > | Der Name, den Sie Ihrem Big Data Cluster gegeben haben. |
   | <SQL_MASTER_IP> | Die IP-Adresse der Master Instanz. |
   | <SQL_MASTER_SA_PASSWORD> | Das SA-Kennwort für die Master Instanz. |
   | < KNOX_IP > | Die IP-Adresse des HDFS/Spark-Gateways. |
   | < KNOX_PASSWORD > | Das Kennwort für das HDFS-/Spark-Gateway. |

   > [!TIP]
   > Verwenden Sie [kubectl](cluster-troubleshooting-commands.md) , um die IP-Adressen für die SQL Server Master Instanz und Knox zu suchen. Führen `kubectl get svc -n <your-big-data-cluster-name>` Sie aus, und sehen Sie sich die externen IP-Adressen für die Master Instanz (**Master-SVC-extern**) und Knox (**Gateway-SVC-extern**) an. Der Standardname eines Clusters ist **MSSQL-Cluster**.

1. Führen Sie das Bootstrap-Skript aus.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a> Linux

In den folgenden Schritten wird beschrieben, wie Sie einen Linux-Client verwenden, um die Beispiel Daten in ihren Big Data Cluster zu laden.

1. Laden Sie das Bootstrap-Skript herunter, und weisen Sie ihm ausführbare Berechtigungen zu.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Laden Sie das Transact-SQL-Skript **Bootstrap-Sample-DB. SQL** herunter. Dieses Skript wird vom Bootstrap-Skript aufgerufen.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Das Bootstrap-Skript erfordert die folgenden Positions Parameter für Ihren Big Data Cluster:

   | Parameter | Beschreibung |
   |---|---|
   | < CLUSTER_NAMESPACE > | Der Name, den Sie Ihrem Big Data Cluster gegeben haben. |
   | <SQL_MASTER_IP> | Die IP-Adresse der Master Instanz. |
   | <SQL_MASTER_SA_PASSWORD> | Das SA-Kennwort für die Master Instanz. |
   | < KNOX_IP > | Die IP-Adresse des HDFS/Spark-Gateways. |
   | < KNOX_PASSWORD > | Das Kennwort für das HDFS-/Spark-Gateway. |

   > [!TIP]
   > Verwenden Sie [kubectl](cluster-troubleshooting-commands.md) , um die IP-Adressen für die SQL Server Master Instanz und Knox zu suchen. Führen `kubectl get svc -n <your-big-data-cluster-name>` Sie aus, und sehen Sie sich die externen IP-Adressen für die Master Instanz (**Master-SVC-extern**) und Knox (**Gateway-SVC-extern**) an. Der Standardname eines Clusters ist **MSSQL-Cluster**.

1. Führen Sie das Bootstrap-Skript aus.

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Nächste Schritte

Nachdem das Bootstrap-Skript ausgeführt wurde, verfügt Ihr Big Data Cluster über die Beispiel Datenbanken und HDFS-Daten. In den folgenden Tutorials werden die Beispiel Daten verwendet, um Big Data Cluster Funktionen zu veranschaulichen:

Datenvirtualisierung:

- [Tutorial: Abfragen von HDFS in einem SQL Server Big Data-Cluster](tutorial-query-hdfs-storage-pool.md)
- [Tutorial: Abfragen von Oracle von einem SQL Server Big Data-Cluster](tutorial-query-oracle.md)

Datenerfassung:

- [Tutorial: Erfassen von Daten in einem SQL Server-Daten Pool mit Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Tutorial: Erfassen von Daten in einem SQL Server-Daten Pool mit Spark-Aufträgen](tutorial-data-pool-ingest-spark.md)

He

- [Tutorial: Ausführen eines Beispiel Notebooks auf einem SQL Server 2019 Big Data-Cluster](tutorial-notebook-spark.md)