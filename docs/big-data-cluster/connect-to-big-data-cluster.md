---
title: Verbindung mit Master und HDFS
titleSuffix: SQL Server 2019 big data clusters
description: Erfahren Sie, wie für die master SQL Server-Instanz und das HDFS/Spark-Gateway für eine SQL Server-2019 big Data-Cluster (Vorschau) eine Verbindung herstellen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 4d3ca6a3e43781b35bfd24f04ee1cf0483b1eb05
ms.sourcegitcommit: 1f53b6a536ccffd701fc87e658ddac714f6da7a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54206266"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Verbinden Sie mit einer SQL Server-big Data-Cluster mit Azure Data Studio

In diesem Artikel wird beschrieben, wie aus Azure Data Studio eine Verbindung mit einer SQL Server-2019 big Data-Cluster (Vorschau) wird.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Ein bereitgestellter [big Data-Cluster für SQL Server-2019](deployment-guidance.md).
- [SQL Server-2019 big Data-Tools](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
   - **"kubectl"**

## <a name="connect-to-the-cluster"></a>Verbinden mit dem cluster

Wenn Sie mit einem big Data-Cluster verbinden, müssen Sie die Möglichkeit, mit der SQL Server-Masterinstanz oder das HDFS/Spark-Gateway verbinden. Die folgenden Abschnitte zeigen, Herstellen einer Verbindung mit jeder.

## <a id="master"></a> Master-Instanz

Master SQL Server-Instanz ist eine herkömmliche SQL Server-Instanz, die mit der relationalen SQL Server-Datenbanken. Die folgenden Schritte beschreiben, Herstellen einer Verbindung mit der Verwendung von Azure Data Studio Masterinstanz.

1. Suchen Sie über die Befehlszeile die IP-Adresse Ihrer master-Instanz mit dem folgenden Befehl aus:

   ```
   kubectl get svc endpoint-master-pool -n <your-cluster-name>
   ```

1. Drücken Sie in Azure Data Studio **F1** > **neue Verbindung**.

1. In **Verbindungstyp**Option **Microsoft SQL Server**.

1. Geben Sie die IP-Adresse in der SQL Server-Masterinstanz **Servernamen** (z. B.: **\<IP-Adresse\>, 31433**).

1. Geben Sie einen SQL-Anmeldenamen **Benutzernamen** und **Kennwort**.

   > [!TIP]
   > Standardmäßig ist der Benutzername **SA** und, sofern nicht geändert, das Kennwort entspricht der **MSSQL_SA_PASSWORD** Umgebungsvariable, die während der Bereitstellung verwendet.

1. Ändern Sie das Ziel **Datenbanknamen** eines relationalen Datenbanken.

   ![Verbinden Sie mit der master-Instanz](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Drücken Sie **Connect**, und die **Serverdashboard** sollte angezeigt werden.

## <a id="hdfs"></a> HDFS/Spark-gateway

Die **HDFS/Spark-Gateway** ermöglicht es Ihnen, für die Arbeit mit dem HDFS-Speicher-Pool und zum Ausführen von Spark-Aufträgen zu verbinden. Die folgenden Schritte beschreiben, wie eine Verbindung mit Azure Data Studio herstellen.

1. Finden Sie über die Befehlszeile die IP-Adresse Ihres HDFS/Spark-Gateways mit einem der folgenden Befehle aus.
   
   **AKS-Bereitstellungen:**

   ```
   kubectl get svc service-security-lb -n <your-cluster-name>
   ```

   **Nicht-AKS-Bereitstellungen**:

   ```
   kubectl get svc service-security-nodeport -n <your-cluster-name>
   ```
 
1. Drücken Sie in Azure Data Studio **F1** > **neue Verbindung**.

1. In **Verbindungstyp**Option **SQL Server-big Data-Cluster**.

   > [!TIP]
   > Wenn Sie nicht sehen die **SQL Server-big Data-Cluster** Verbindung geben, stellen Sie sicher, dass Sie installiert haben die [2019 für SQL Server-Erweiterung](../azure-data-studio/sql-server-2019-extension.md) und dass Sie Azure Data Studio nach der Erweiterung abgeschlossen neu gestartet installieren.

1. Geben Sie die IP-Adresse der big Data-Cluster in **Servernamen** (einen Port nicht angegeben).

1. Geben Sie `root` für die **Benutzer** , und geben Sie die **Kennwort** auf Ihre big Data-Cluster.

   ![Verbinden Sie mit HDFS/Spark-gateway](./media/connect-to-big-data-cluster/connect-to-cluster-hdfs-spark.png)

   > [!TIP]
   > Standardmäßig ist der Benutzername **Stamm** und das Kennwort entspricht der **KNOX_PASSWORD** Umgebungsvariable, die während der Bereitstellung verwendet.

1. Drücken Sie **Connect**, und die **Serverdashboard** sollte angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-2019 big Data-Cluster, finden Sie unter [was SQL Server-2019 big Data-Cluster sind](big-data-cluster-overview.md).