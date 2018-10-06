---
title: Herstellen einer Verbindung eine SQL Server big Data-cluster mit Azure Data Studio mit | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit einer SQL Server-2019 big Data-Cluster mit Azure Data Studio verbinden.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 971fc2f8e8a77b00f3d2c5cd6390fec351ffc0f3
ms.sourcegitcommit: c7d3a903eb7f410db3a0230101d24de0af17621a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2018
ms.locfileid: "48827301"
---
# <a name="connect-to-a-sql-server-big-data-cluster-with-azure-data-studio"></a>Verbinden Sie mit einer SQL Server-big Data-Cluster mit Azure Data Studio

Dieser Artikel beschreibt das Installieren von Azure Data Studio, die Erweiterung für SQL Server-2019 (Vorschau), und verbinden Sie dann mit einem big Data-Cluster. Die neue Erweiterung für SQL Server-2019 umfasst Unterstützung für die Vorschauversion [big Data-Cluster für SQL Server-2019](big-data-cluster-overview.md), eine integrierte [notebookfeatures](notebooks-guidance.md), und eine PolyBase [CreateExternalTable-Assistenten](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-azure-data-studio"></a>Installieren von Azure Data Studio

Um Azure Data Studio zu installieren, finden Sie unter [herunterladen und installieren Sie die neueste Version von Azure Data Studio](../azure-data-studio/download.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installieren der Erweiterung für SQL Server-2019 (Vorschau)

Um die Erweiterung zu installieren, finden Sie unter [Installieren der Erweiterung (Vorschau) für SQL Server-2019](../azure-data-studio/sql-server-2019-extension.md).

## <a name="connect-to-the-cluster"></a>Verbinden mit dem cluster

Wenn Sie mit einem big Data-Cluster verbinden, haben Sie die Option für die Verbindung mit SQL Server [Masterinstanz](concept-master-instance.md) oder das HDFS/Spark-Gateway. Die folgenden Abschnitte zeigen, Herstellen einer Verbindung mit jeder.

## <a name="master-instance"></a>Master-Instanz

1. Drücken Sie in Azure Data Studio **F1** > **neue Verbindung**.
1. In **Verbindungstyp**Option **Microsoft SQL Server**.
1. Geben Sie die IP-Adresse in der SQL Server-Masterinstanz **Servernamen** (z. B.:  **\<IP-Adresse\>, 31433**).
1. Ändern der **Datenbanknamen** auf die **High_value_data** Datenbank.

   ![Verbinden Sie mit der master-Instanz](./media/deploy-big-data-tools/connect-to-cluster.png)

1. Drücken Sie **Connect**, und die **Serverdashboard** sollte angezeigt werden.

## <a name="hdfsspark-gateway"></a>HDFS/Spark-gateway

1. Drücken Sie in Azure Data Studio **F1** > **neue Verbindung**.
1. In **Verbindungstyp**Option **SQL Server-big Data-Cluster**.
1. Geben Sie die IP-Adresse der big Data-Cluster in **Servernamen**.

   ![Verbinden Sie mit HDFS/Spark-gateway](./media/deploy-big-data-tools/connect-to-cluster-hdfs-spark.png)

1. Drücken Sie **Connect**, und die **Serverdashboard** sollte angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Führen Sie Notebooks in Azure Data Studio finden Sie unter [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md).
