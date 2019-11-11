---
title: Herstellen einer Verbindung mit der Masterinstanz und HDFS-Big Data-Clustern
description: Erfahren Sie, wie Sie eine Verbindung mit der SQL Server-Masterinstanz und dem HDFS/Spark-Gateway für einen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] herstellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0717226ee785df568d4cea75511e65acb728c592
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532240"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server mit Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie über Azure Data Studio eine Verbindung mit einem [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] herstellen.

## <a name="prerequisites"></a>Voraussetzungen

- Ein bereitgestellter [Big-Data-Cluster für SQL Server 2019](deployment-guidance.md).
- [Big-Data-Tools für SQL Server 2019:](deploy-big-data-tools.md)
   - **Azure Data Studio**
   - **Erweiterung von SQL Server 2019**
   - **kubectl**
   - **azdata**

## <a id="master"></a> Herstellen einer Verbindung mit dem Cluster

Stellen Sie eine neue Verbindung mit der SQL Server-Masterinstanz im Cluster her, um eine Verbindung mit einem Big-Data-Cluster mit Azure Data Studio herzustellen. In den folgenden Schritten wird beschrieben, wie mithilfe von Azure Data Studio eine Verbindung mit der Masterinstanz hergestellt wird.

1. Suchen Sie den Endpunkt der SQL Server-Masterinstanz:

   ```
   azdata bdc endpoint list -e sql-server-master
   ```

   > [!TIP]
   > Weitere Informationen zum Abrufen von Endpunkten finden Sie unter [Abrufen von Endpunkten](deployment-guidance.md#endpoints).

1. Drücken Sie **F1** > **Neue Verbindung** in Azure Data Studio.

1. Wählen Sie unter **Verbindungstyp** die Option **Microsoft SQL Server** aus.

1. Geben Sie den gefundenen Endpunktnamen für die SQL Server-Masterinstanz in das Textfeld **Name** ein (Beispiel: **\<IP-Adresse\>,31433**). 

1. Wählen Sie einen Authentifizierungstyp aus. Bei SQL Server-Masterinstanzen, die in Big Data-Clustern ausgeführt werden, werden nur **Windows-Authentifizierung** und **SQL-Anmeldung** unterstützt. 

1. Geben Sie den **Benutzernamen** und das **Kennwort** für die SQL-Anmeldung ein. Wenn Sie die Windows-Authentifizierung verwenden, ist dies nicht notwendig.

   > [!TIP]
   > Der Benutzername **SA** ist während der Bereitstellung eines Big Data-Clusters standardmäßig deaktiviert. Während der Bereitstellung wird ein neuer SysAdmin-Benutzer bereitgestellt, dessen Name und Kennwort den Umgebungsvariablen **AZDATA_USERNAME** bzw. **AZDATA_PASSWORD** entsprechen, die während der Bereitstellung verwendet wurden.

1. Ändern Sie den **Zieldatenbanknamen** in einen ihrer relationalen Datenbanken.

   ![Herstellen einer Verbindung mit der Masterinstanz](./media/connect-to-big-data-cluster/connect-to-cluster.png)

1. Klicken Sie auf **Verbinden**, und das **Serverdashboard** sollte angezeigt werden.

Mit der Azure Data Studio-Version vom Februar 2019 können Sie mit dem Herstellen einer Verbindung mit der SQL Server-Masterinstanz auch mit dem HDFS/Spark-Gateway interagieren. Dies bedeutet, dass Sie keine separate Verbindung für HDFS und Spark verwenden müssen, die im nächsten Abschnitt beschrieben wird.

- Der Objekt-Explorer enthält jetzt einen neuen **Data Services**-Knoten für Big-Data-Cluster-Aufgaben (z. B. das Erstellen neuer Notebooks oder das Übermitteln von Spark-Aufträgen), die mit einem Rechtsklick ausgeführt werden können. 
- Der **Data Services**-Knoten enthält außerdem einen **HDFS**-Ordner zum Durchsuchen von HDFS und zum Ausführen von Aktionen wie das Erstellen einer externen Tabelle oder das Analysieren in Notebook.
- Das **Serverdashboard** für die Verbindung enthält auch Registerkarten für **Big-Data-Cluster für SQL Server** und **SQL Server 2019 (Vorschauversion)** , wenn die Erweiterung installiert ist.

   ![Data Services-Knoten für Azure Data Studio](./media/connect-to-big-data-cluster/connect-data-services-node.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
