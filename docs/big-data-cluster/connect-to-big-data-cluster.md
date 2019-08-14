---
title: Herstellen einer Verbindung mit der Masterinstanz und HDFS
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie eine Verbindung mit der SQL Server-Masterinstanz und dem HDFS/Spark-Gateway für einen Big-Data-Cluster für SQL Server 2019 (Vorschauversion) herstellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1f09763b210427c84efe75d693fee302d7048db7
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958642"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server mit Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie eine Verbindung mit einem Big-Data-Cluster für SQL Server 2019 (Vorschauversion) aus Azure Data Studio herstellen.

## <a name="prerequisites"></a>Voraussetzungen

- Ein bereitgestellter [Big-Data-Cluster für SQL Server 2019](deployment-guidance.md).
- [Big-Data-Tools für SQL Server 2019:](deploy-big-data-tools.md)
   - **Azure Data Studio**
   - **Erweiterung von SQL Server 2019**
   - **kubectl**

## <a id="master"></a> Herstellen einer Verbindung mit dem Cluster

Stellen Sie eine neue Verbindung mit der SQL Server-Masterinstanz im Cluster her, um eine Verbindung mit einem Big-Data-Cluster mit Azure Data Studio herzustellen. In den folgenden Schritten wird beschrieben, wie mithilfe von Azure Data Studio eine Verbindung mit der Masterinstanz hergestellt wird.

1. Suchen Sie in der Befehlszeile die IP-Adresse Ihrer Masterinstanz mit dem folgenden Befehl:

   ```
   kubectl get svc master-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Der Name des Big-Data-Clusters lautet standardmäßig **mssql-cluster**, sofern Sie den Namen nicht in einer Bereitstellungskonfigurationsdatei angepasst haben. Weitere Informationen finden Sie unter [Konfigurieren von Bereitstellungseinstellungen für Big-Data-Cluster](deployment-custom-configuration.md#clustername).

1. Drücken Sie **F1** > **Neue Verbindung** in Azure Data Studio.

1. Wählen Sie unter **Verbindungstyp** die Option **Microsoft SQL Server** aus.

1. Geben Sie für **Servername** die IP-Adresse der SQL Server-Masterinstanz ein (z. B.: **\<IP-Adresse\>,31433**).

1. Geben Sie einen **Benutzernamen** und ein **Kennwort** für die SQL-Anmeldung ein.

   > [!TIP]
   > Standardmäßig lautet der Benutzername **SA**, und das Kennwort (sofern nicht geändert) entspricht der Umgebungsvariable **MSSQL_SA_PASSWORD**, die während der Bereitstellung verwendet wird.

1. Ändern Sie den **Zieldatenbanknamen** in einen ihrer relationalen Datenbanken.

   ![Herstellen einer Verbindung mit der Masterinstanz](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Klicken Sie auf **Verbinden**, und das **Serverdashboard** sollte angezeigt werden.

Mit der Azure Data Studio-Version vom Februar 2019 können Sie mit dem Herstellen einer Verbindung mit der SQL Server-Masterinstanz auch mit dem HDFS/Spark-Gateway interagieren. Dies bedeutet, dass Sie keine separate Verbindung für HDFS und Spark verwenden müssen, die im nächsten Abschnitt beschrieben wird.

- Der Objekt-Explorer enthält jetzt einen neuen **Data Services**-Knoten für Big-Data-Cluster-Aufgaben (z. B. das Erstellen neuer Notebooks oder das Übermitteln von Spark-Aufträgen), die mit einem Rechtsklick ausgeführt werden können. 
- Der **Data Services**-Knoten enthält außerdem einen **HDFS**-Ordner zum Durchsuchen von HDFS und zum Ausführen von Aktionen wie das Erstellen einer externen Tabelle oder das Analysieren in Notebook.
- Das **Serverdashboard** für die Verbindung enthält auch Registerkarten für **Big-Data-Cluster für SQL Server** und **SQL Server 2019 (Vorschauversion)** , wenn die Erweiterung installiert ist.

   ![Data Services-Knoten für Azure Data Studio](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern für SQL Server 2019 finden Sie unter [Was sind Big Data-Cluster für SQL Server 2019?](big-data-cluster-overview.md).