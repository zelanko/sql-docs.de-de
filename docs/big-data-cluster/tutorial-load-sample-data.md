---
title: Laden von Beispieldaten
titleSuffix: SQL Server 2019 big data clusters
description: In diesem Tutorial wird veranschaulicht, wie zum Laden von Beispieldaten in eine SQL Server-big Data-Cluster wird. Die Beispieldaten werden relationale Daten in der master-SQL Server-Instanz enthält. Darüber hinaus HDFS-Daten im Speicherpool. Diese Daten unterstützt andere Tutorials in diesem Abschnitt.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 67e97774a00fed123ba6733688e002f1b57ba743
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53439387"
---
# <a name="tutorial-load-sample-data-into-a-sql-server-2019-big-data-cluster"></a>Lernprogramm: Laden Sie Beispieldaten in eine SQL Server-2019 big Data-cluster

In diesem Tutorial wird erläutert, wie Sie mithilfe eines Skripts zum Laden von Beispieldaten in eine SQL Server-2019 big Data-Cluster (Vorschau). Viele der anderen Lernprogramme in der Dokumentation verwenden diesen Beispieldaten.

> [!TIP]
> Zusätzliche Beispiele für SQL Server-2019 big Data-Cluster (Vorschau) finden Sie in der [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster) GitHub-Repository. Befinden sie sich die **sql-server-samples/samples/features/sql-big-data-cluster/** Pfad.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Eine bereitgestellte big Data-cluster](deployment-guidance.md)
- [Big Data-tools](deploy-big-data-tools.md)
   - **mssqlctl**
   - **"kubectl"**
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
   | &LT; CLUSTER_NAMESPACE &GT; | Der Name gegeben haben Sie Ihre big Data-Cluster. |
   | &LT; SQL_MASTER_IP &GT; | Die IP-Adresse Ihrer master-Instanz. |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | Das SA-Kennwort für die master-Instanz. |
   | &LT; KNOX_IP &GT; | Die IP-Adresse des Gateways HDFS/Spark. |
   | &LT; KNOX_PASSWORD &GT; | Das Kennwort für das HDFS/Spark-Gateway. |

   > [!TIP]
   > Verwendung ["kubectl"](cluster-troubleshooting-commands.md) um die IP-Adressen für die SQL Server-Masterinstanz und Knox zu finden. Führen Sie `kubectl get svc -n <your-cluster-name>` und sehen Sie sich die externe IP-Adressen für die master-Instanz (**Endpunkt-Master-Pool**) und Knox (**Service-Sicherheit-lb** oder **Service-Sicherheit-Nodeport**).

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
   | &LT; CLUSTER_NAMESPACE &GT; | Der Name gegeben haben Sie Ihre big Data-Cluster. |
   | &LT; SQL_MASTER_IP &GT; | Die IP-Adresse Ihrer master-Instanz. |
   | &LT; SQL_MASTER_SA_PASSWORD &GT; | Das SA-Kennwort für die master-Instanz. |
   | &LT; KNOX_IP &GT; | Die IP-Adresse des Gateways HDFS/Spark. |
   | &LT; KNOX_PASSWORD &GT; | Das Kennwort für das HDFS/Spark-Gateway. |

   > [!TIP]
   > Verwendung ["kubectl"](cluster-troubleshooting-commands.md) um die IP-Adressen für die SQL Server-Masterinstanz und Knox zu finden. Führen Sie `kubectl get svc -n <your-cluster-name>` und sehen Sie sich die externe IP-Adressen für die master-Instanz (**Endpunkt-Master-Pool**) und Knox (**Service-Sicherheit-lb** oder **Service-Sicherheit-Nodeport**).

1. Das bootstrap-Skript ausführen.

   ```bash
   ./bootstrap-sample-db.sh <CLUSTER_NAMESPACE> <SQL_MASTER_IP> <SQL_MASTER_SA_PASSWORD> <KNOX_IP> <KNOX_PASSWORD>
   ```

## <a name="next-steps"></a>Nächste Schritte

Nachdem das bootstrap-Skript ausgeführt wurde, hat Ihre big Data-Cluster die Beispieldatenbanken und HDFS-Daten. Untersuchen diese Daten und big Data-Cluster finden Sie in der [Tutorials](tutorial-query-hdfs-storage-pool.md) in diesem Abschnitt.