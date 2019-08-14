---
title: Verwalten eines Big Data-Clusters für SQL Server mit Azure Data Studio-Notebooks
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data-Cluster zu verwalten und Probleme für ihn zu beheben.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d9c8edd91ced01135d740fecdf6cf837df9cac6b
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68470736"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Verwalten von Big Data-Clustern für SQL Server mit Azure Data Studio-Notebooks

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] stellt eine Erweiterung für Azure Data Studio bereit, die Notebooks umfasst. Ein Notebook enthält Dokumentation und Code, die Sie in Azure Data Studio verwenden können, um Big Data-Cluster für SQL Server zu verwalten.

[Notebooks](notebooks-guidance.md), die ursprünglich als Open-Source-Projekt implementiert wurden, wurden in [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download) implementiert. Sie können Markdown für Text in den Textzellen und einen der verfügbaren Kernel verwenden, um Code in den Codezellen zu schreiben.

Sie können Notebooks verwenden, um Big Data-Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] bereitzustellen.

Zusätzlich zu Notebooks können Benutzer Sammlungen von Notebooks anzeigen, die als Jupyter Books bezeichnet werden. Ein Jupyter Book stellt ein Inhaltsverzeichnis bereit, um in einer Sammlung von Notebooks zu navigieren, sodass ein Benutzer das benötigte Notebook leicht finden kann, egal, ob zur Problembehandlung von SQL Server oder zum Anzeigen des Clusterstatus.

## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen erfüllt sein, damit ein Notebook gestartet werden kann:

* Die neueste Version von [Azure Data Studio Insiders-Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master).
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung ist in Azure Data Studio installiert.

Zusätzlich hierzu sind folgende Komponenten erforderlich, um einen Big Data-Cluster für SQL Server 2019 bereitstellen zu können:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>Zugreifen auf Notebooks zur Problembehandlung

1. Nachdem Sie Azure Data Studio Insiders installiert haben, stellen Sie eine Verbindung mit einer Big Data-Clusterinstanz für SQL Server her.
2. Sobald diese Verbindung erfolgreich hergestellt ist, klicken Sie im Viewlet „Verbindungen“ mit der rechten Maustaste auf den Servernamen, und klicken Sie dann auf **Verwalten**.
3. Klicken Sie auf dem Dashboard auf **SQL Server-Big Data-Cluster**. Klicken Sie auf **SQL Server 2019 Guide**, um das Jupyter Book mit den Notebooks zu öffnen, die Sie benötigen.
    ![Schaltfläche](media/manage-notebooks/jupyter-book-button.png)

1. Wählen Sie im Fenster für Ordnerauswahl den Speicherort aus, in dem Ihr Jupyter Book gespeichert werden soll.
2. Klicken Sie auf **Neu laden**, um Azure Data Studio erneut zu laden, damit Ihr Jupyter Book angezeigt wird. Klicken Sie auf **Neue Instanz öffnen**, um eine neue Instanz von Azure Data Studio mit dem Jupyter Book zu öffnen.
3. In der Explorer-Ansicht sollte ein Abschnitt zu sehen sein, der den Namen **Books** hat. Ist dieser nicht erweitert, klicken Sie darauf, um die Notebooks anzuzeigen.
4. Klicken Sie auf das Notebook für die Aufgabe, die Sie ausführen müssen.

## <a name="next-steps"></a>Next Steps
Weitere Informationen zu Notebooks in Azure Data Studio finden Sie unter [Verwenden von Notebooks in SQL Server 2019 (Vorschauversion)](notebooks-guidance.md).