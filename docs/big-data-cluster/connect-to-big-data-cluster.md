---
title: Verbindung mit Master und HDFS
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie für die master SQL Server-Instanz und das HDFS/Spark-Gateway für eine SQL Server-2019 big Data-Cluster (Vorschau) eine Verbindung herstellen.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 245e88034194a01908b69d545deb9fa717c19a4a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66782976"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Verbinden Sie mit einer SQL Server-big Data-Cluster mit Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie aus Azure Data Studio eine Verbindung mit einer SQL Server-2019 big Data-Cluster (Vorschau) wird.

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
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Der big Data-cluster standardmäßig mit **Mssql-Cluster** , wenn Sie den Namen in einer Konfigurationsdatei für die Bereitstellung angepasst. Weitere Informationen finden Sie unter [Konfigurieren von bereitstellungseinstellungen für big Data-Cluster](deployment-custom-configuration.md#clustername).

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

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-2019 big Data-Cluster, finden Sie unter [was SQL Server-2019 big Data-Cluster sind](big-data-cluster-overview.md).