---
title: Laden von Beispieldaten
titleSuffix: SQL Server big data clusters
description: In diesem Tutorial wird veranschaulicht, wie zum Laden von Beispieldaten in eine SQL Server-big Data-Cluster wird. Die Beispieldaten werden relationale Daten in der master-SQL Server-Instanz enthält. Darüber hinaus HDFS-Daten im Speicherpool. Diese Daten unterstützt andere Tutorials in diesem Abschnitt.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: d78fd9ecce71e9b7ffb86441fab134b1180d058a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66770827"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-big-data-cluster"></a>Tutorial: Laden Sie Beispieldaten in eine SQL Server-big Data-cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial wird erläutert, wie Sie mithilfe eines Skripts zum Laden von Beispieldaten in eine SQL Server-2019 big Data-Cluster (Vorschau). Viele der anderen Lernprogramme in der Dokumentation verwenden diesen Beispieldaten.

> [!TIP]
> Zusätzliche Beispiele für SQL Server-2019 big Data-Cluster (Vorschau) finden Sie in der [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) GitHub-Repository. Befinden sie sich die **sql-server-samples/samples/features/sql-big-data-cluster/** Pfad.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Eine bereitgestellte big Data-cluster](deployment-guidance.md)
- [Big Data-tools](deploy-big-data-tools.md)
   - **mssqlctl**
   - **kubectl**
   - **sqlcmd**
   - **curl**

## <a id="sampledata"></a> Laden von Beispieldaten

Die folgenden Schritte werden ein bootstrap-Skript zum Herunterladen von SQL Server-Datenbank-Sicherung, und Laden der Daten in Ihre big Data-Cluster verwenden. Zur einfacheren Verwendung, diese Schritte in ausgewiesen wurde [Windows](#windows) und [Linux](#linux) Abschnitte.

## <a id="windows"></a> Windows

Die folgenden Schritte beschreiben, wie Sie einen Windows-Client verwenden, um die Beispieldaten in Ihre big Data-Cluster zu laden.

1. Öffnen Sie eine neue Windows-Eingabeaufforderung.

   > [!IMPORTANT]
   > Verwenden Sie Windows PowerShell nicht für diese Schritte aus. In PowerShell das Skript fehl, da es, die PowerShell-Version des verwendet wird **curl**.

1. Verwendung **curl** das bootstrap-Skript für die Beispieldaten herunterladen.

   ```cmd
   curl -o bootstrap-sample-db.cmd "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.cmd"
   ```

1. Herunterladen der **Bootstrap-Beispiel-db.sql** Transact-SQL-Skript. Dieses Skript wird vom bootstrap-Skript aufgerufen.

   ```cmd
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Das bootstrap-Skript erfordert die folgenden positionelle Parameter für Ihre big Data-Cluster:

   | Parameter | Description |
   |---|---|
   | <CLUSTER_NAMESPACE> | Der Name gegeben haben Sie Ihre big Data-Cluster. |
   | <SQL_MASTER_IP> | Die IP-Adresse Ihrer master-Instanz. |
   | <SQL_MASTER_SA_PASSWORD> | Das SA-Kennwort für die master-Instanz. |
   | <KNOX_IP> | Die IP-Adresse des Gateways HDFS/Spark. |
   | <KNOX_PASSWORD> | Das Kennwort für das HDFS/Spark-Gateway. |

   > [!TIP]
   > Verwendung ["kubectl"](cluster-troubleshooting-commands.md) um die IP-Adressen für die SQL Server-Masterinstanz und Knox zu finden. Führen Sie `kubectl get svc -n <your-big-data-cluster-name>` und sehen Sie sich die externe IP-Adressen für die master-Instanz (**Master-svc-External**) und Knox (**Gateway-svc-External**). Der Standardname eines Clusters ist **Mssql-Cluster**.

1. Das bootstrap-Skript ausführen.

   ```cmd
   .\bootstrap-sample-db.cmd <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a id="linux"></a> Linux

Die folgenden Schritte beschreiben, wie Sie einen Linux-Client verwenden, um die Beispieldaten in Ihre big Data-Cluster zu laden.

1. Das bootstrap-Skript herunter, und Berechtigungen zuweisen.

   ```bash
   curl -o bootstrap-sample-db.sh "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sh"
   chmod +x bootstrap-sample-db.sh
   ```

1. Herunterladen der **Bootstrap-Beispiel-db.sql** Transact-SQL-Skript. Dieses Skript wird vom bootstrap-Skript aufgerufen.

   ```bash
   curl -o bootstrap-sample-db.sql "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/bootstrap-sample-db.sql"
   ```

1. Das bootstrap-Skript erfordert die folgenden positionelle Parameter für Ihre big Data-Cluster:

   | Parameter | Description |
   |---|---|
   | <CLUSTER_NAMESPACE> | Der Name gegeben haben Sie Ihre big Data-Cluster. |
   | <SQL_MASTER_IP> | Die IP-Adresse Ihrer master-Instanz. |
   | <SQL_MASTER_SA_PASSWORD> | Das SA-Kennwort für die master-Instanz. |
   | <KNOX_IP> | Die IP-Adresse des Gateways HDFS/Spark. |
   | <KNOX_PASSWORD> | Das Kennwort für das HDFS/Spark-Gateway. |

   > [!TIP]
   > Verwendung ["kubectl"](cluster-troubleshooting-commands.md) um die IP-Adressen für die SQL Server-Masterinstanz und Knox zu finden. Führen Sie `kubectl get svc -n <your-big-data-cluster-name>` und sehen Sie sich die externe IP-Adressen für die master-Instanz (**Master-svc-External**) und Knox (**Gateway-svc-External**). Der Standardname eines Clusters ist **Mssql-Cluster**.

1. Das bootstrap-Skript ausführen.

   ```bash
   sudo env "PATH=$PATH" ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Nächste Schritte

Nachdem das bootstrap-Skript ausgeführt wurde, hat Ihre big Data-Cluster die Beispieldatenbanken und HDFS-Daten. In den folgenden Tutorials werden die Beispieldaten verwenden, um big Data-Cluster-Funktionen zu veranschaulichen:

Data Virtualization:

- [Tutorial: HDFS-Abfrage in einer SQL Server-big Data-cluster](tutorial-query-hdfs-storage-pool.md)
- [Tutorial: Abfragen von Oracle aus einer SQL Server-big Data-cluster](tutorial-query-oracle.md)

Datenerfassung:

- [Tutorial: Erfassen von Daten in einen Pool des SQL Server-Daten mit Transact-SQL](tutorial-data-pool-ingest-sql.md)
- [Tutorial: Erfassen von Daten in einen Pool des SQL Server-Daten mit Spark-Aufträgen](tutorial-data-pool-ingest-spark.md)

Notebooks:

- [Tutorial: Führen Sie ein Beispiel-Notebook auf eine SQL Server-2019 big Data-cluster](tutorial-notebook-spark.md)