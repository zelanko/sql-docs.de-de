---
title: Verbindung mit Master und HDFS
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie für die master SQL Server-Instanz und das HDFS/Spark-Gateway für eine SQL Server-2019 big Data-Cluster (Vorschau) eine Verbindung herstellen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ed563fe6d0bfd69ce5dfb7484d4213bc9a47dd54
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860171"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Verbinden Sie mit einer SQL Server-big Data-Cluster mit Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie aus Azure Data Studio eine Verbindung mit einer SQL Server-2019 big Data-Cluster (Vorschau) wird. Es gibt zwei Haupt-Endpunkte, die für die Interaktion mit einem big Data-Cluster verwendet werden:

| Endpunkt | Description |
|---|---|
| Master für SQL Server-Instanz | Die SQL Server-Masterinstanz in den Cluster mit der relationalen SQL Server-Datenbanken. |
| HDFS/Spark-gateway | Zugriff auf HDFS-Speicher im Cluster und die Möglichkeit, die Spark-Aufträge auszuführen. |

> [!TIP]
> Mit der Version Februar 2019 von Azure Data Studio stellt eine Verbindung mit der master SQL Server-Instanz automatisch Benutzeroberfläche Zugriff auf das HDFS/Spark-Gateway bereit.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Ein bereitgestellter [big Data-Cluster für SQL Server-2019](deployment-guidance.md).
- [SQL Server-2019 big Data-Tools](deploy-big-data-tools.md):
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
   - **kubectl**

## <a id="master"></a> Verbinden mit dem cluster

Stellen Sie zum Verbinden mit einem big Data-Cluster mit Azure Data Studio eine neue Verbindung mit SQL Server-Instanz master im Cluster. Die folgenden Schritte beschreiben, Herstellen einer Verbindung mit der Verwendung von Azure Data Studio Masterinstanz.

1. Finden Sie über die Befehlszeile die IP-Adresse Ihrer master-Instanz mit dem folgenden Befehl aus:

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

Mit der Version Februar 2019 von Azure Data Studio kann mit der SQL Server-Masterinstanz Sie auch für die Interaktion mit dem HDFS/Spark-Gateway. Dies bedeutet, dass Sie nicht benötigen, verwenden Sie eine separate Verbindung für HDFS und Spark, die im nächsten Abschnitt beschrieben.

- Die Objekt-Explorer enthält nun ein neues **Datendienste** Knoten mit der rechten Maustaste-Unterstützung für big Data-Cluster Aufgaben wie erstellen neue Notebooks oder Spark-Aufträge übermitteln. 
- Die **Datendienste** Knoten enthält auch eine **HDFS** Ordner für das HDFS-durchsuchen und Ausführen von Aktionen wie z. B. Create External Table, oder Analysieren im Notebook.
- Die **Serverdashboard** für die Verbindung auch Registerkarten für enthält **SQL Server-big Data-Cluster** und **SQL Server-2019 (Vorschau)** beim Installieren der Erweiterung.

   ![Azure Data Services Studio Datenknoten](./media/connect-to-big-data-cluster/connect-data-services-node.png)

> [!IMPORTANT]
> Wenn dort **Unbekannter Fehler** in der Benutzeroberfläche möglicherweise zu [direkt an das HDFS/Spark-Gateway verbinden](#hdfs). Eine Ursache für diesen Fehler sind verschiedene Kennwörter für die master SQL Server-Instanz und das HDFS/Spark-Gateway. Azure Data Studio wird davon ausgegangen, dass für beide dasselbe Kennwort verwendet wird.
  
## <a id="hdfs"></a> Herstellen einer Verbindung das HDFS/Spark-Gateway mit

In den meisten Fällen, Herstellen einer Verbindung mit der SQL Server-Masterinstanz erhalten Sie Zugriff auf das HDFS und Spark auch über die **Datendienste** Knoten. Allerdings können Sie weiterhin eine dedizierte Verbindung mit erstellen die **HDFS/Spark-Gateway** bei Bedarf. Die folgenden Schritte beschreiben, wie eine Verbindung mit Azure Data Studio herstellen.

1. Finden Sie über die Befehlszeile die IP-Adresse Ihres HDFS/Spark-Gateways mit einem der folgenden Befehle aus.

   ```
   kubectl get svc endpoint-security -n <your-cluster-name>
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