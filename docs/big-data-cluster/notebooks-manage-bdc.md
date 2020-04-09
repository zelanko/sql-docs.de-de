---
title: 'Verwalten: Azure Data Studio-Notebooks'
titleSuffix: SQL Server Big Data Clusters
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data-Cluster zu verwalten und Probleme für ihn zu beheben.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 03/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 28ba612c1932dd511ee0cd99a2aa97dd127d63f7
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531333"
---
# <a name="manage-sql-server-big-data-clusters-with-azure-data-studio-notebooks"></a>Verwalten von SQL Server-Big Data-Clustern mit Azure Data Studio-Notebooks

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] stellt eine Erweiterung für Azure Data Studio bereit, die Notebooks umfasst. Ein Notebook stellt Dokumentation und Code bereit, die Sie in Azure Data Studio verwenden können, um Big Data-Cluster für SQL Server 2019 zu verwalten.

[Notebooks](../azure-data-studio/notebooks-guidance.md), die ursprünglich als Open-Source-Projekt implementiert wurden, wurden in [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download) integriert. Sie können Markdown für Text in den Textzellen und einen der verfügbaren Kernel verwenden, um Code in den Codezellen zu schreiben.

Sie können Notebooks verwenden, um Big Data-Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] bereitzustellen.

Zusätzlich zu Notebooks können Sie eine Sammlung von Notebooks anzeigen, die als Jupyter-Book bezeichnet wird. Ein Jupyter-Book stellt ein Inhaltsverzeichnis bereit, das Ihnen bei der Navigation durch eine Sammlung von Notebooks hilft, sodass Sie das gewünschte Notebook leicht finden können, egal ob zur Problembehandlung in SQL Server oder zum Anzeigen des Clusterstatus.

## <a name="prerequisites"></a>Voraussetzungen

Zum Öffnen eines Notebooks benötigen Sie Folgendes:

* die neueste Version von [Azure Data Studio-Insider-Build](https://aka.ms/azuredatastudio-rc)
* die [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung, die in Azure Data Studio installiert ist

Zusätzlich zu diesen Voraussetzungen benötigen Sie für die Bereitstellung von SQL Server 2019-Big Data-Clustern:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure-Befehlszeilenschnittstelle](/cli/azure/install-azure-cli)

## <a name="access-troubleshooting-notebooks"></a>Zugriff auf Notebooks zur Problembehandlung

Es gibt drei Möglichkeiten, um auf Notebooks zur Problembehandlung zuzugreifen.

### <a name="command-palette"></a>Befehlspalette

1. Wählen Sie **Ansicht** > **Befehlspalette** aus.

2. Geben Sie **Jupyter Books: SQL Server 2019 Guide** (Jupyter-Books: SQL Server 2019-Leitfaden) ein.

Das Viewlet „Jupyter Books“ mit dem Jupyter-Book, das die Fehlerbehebung für Notebooks für SQL Server-Big Data Cluster enthält, wird geöffnet.

### <a name="sql-master-dashboard"></a>SQL-Masterdashboard

1. Nachdem Sie Azure Data Studio-Insider-Build installiert haben, stellen Sie eine Verbindung mit einer SQL Server-Big Data-Clusterinstanz her.

2. Nachdem Sie mit der Instanz verbunden sind, klicken Sie mit der rechten Maustaste auf Ihren Servernamen unter **Verbindungen**, und wählen Sie **Verwalten** aus.

3. Wählen Sie im Dashboard **SQL Server-Big Data-Cluster** aus. Klicken Sie auf **SQL Server 2019 Guide** (SQL Server 2019-Leitfaden), um das Jupyter-Book mit den Notebooks zu öffnen, die Sie benötigen.
    ![Jupyter-Notebooks im Dashboard](media/manage-notebooks/jupyter-book-button.png)

4. Wählen Sie das Notebook für die Aufgabe aus, die Sie ausführen müssen.

### <a name="controller-dashboard"></a>Controllerdashboard

1. Klappen Sie in der Ansicht **Verbindungen** **SQL Server-Big Data-Cluster** auf.

2. Fügen Sie Details zu Controllerendpunkten hinzu.

3. Sobald Sie mit dem Controller verbunden sind, klicken Sie mit der rechten Maustaste auf den Endpunkt, und wählen Sie **Verwalten** aus.

4. Wählen Sie nach dem Laden des Dashboards **Troubleshoot** (Problembehandlung) aus, um die Problembehandlungsrichtlinien für das Jupyter-Book zu öffnen.

## <a name="use-troubleshooting-notebooks"></a>Verwenden von Notebooks zur Problembehandlung

1. Suchen Sie im Inhaltsverzeichnis des Jupyter-Book nach der Richtlinie zur Problembehandlung, das Sie benötigen.

2. Die Notebooks sind optimiert, sodass Sie nur **Run Cells** (Zellen ausführen) auswählen müssen. Diese Aktion führt jede Zelle im Notebook einzeln aus, bis das Notebook vollständig ist.

3. Wenn ein Fehler gefunden wird, schlägt das Jupyter-Book ein Notebook vor, das Sie ausführen können, um den Fehler zu beheben. Befolgen Sie die empfohlenen Schritte, und führen Sie das Notebook erneut aus.

## <a name="change-the-big-data-cluster"></a>Ändern des Big Data-Clusters

So ändern Sie den SQL Server-Big Data-Cluster für ein Notebook:

1. Klicken Sie in der Symbolleiste des Notebooks auf das Menü **Anfügen an**.

   ![Klicken auf das Menü „Anfügen an“ in der Symbolleiste des Notebooks](./media/notebooks-how-to-manage/select-attach-to-1.png)

2. Klicken Sie im Menü **Anfügen an** auf einen Server.

   ![Auswählen eines Servers im Menü „Anfügen an“](./media/notebooks-how-to-manage/select-attach-to-2.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Notebooks in Azure Data Studio finden Sie unter [Verwenden von Notebooks mit SQL Server](../azure-data-studio/notebooks-guidance.md).
