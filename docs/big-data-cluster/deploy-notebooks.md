---
title: Bereitstellen eines Big Data-Clusters für SQL Server mit Azure Data Studio-Notebooks
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data-Cluster bereitzustellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 18880c6cf0590c8a10c232cd2dd9d11e5279f918
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68470787"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Bereitstellen eines Big Data-Clusters für SQL Server mit Azure Data Studio-Notebooks

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] stellt eine Erweiterung für Azure Data Studio bereit, die Bereitstellungsnotebooks umfasst. Ein Bereitstellungsnotebook enthält Dokumentation und Code, die Sie in Azure Data Studio verwenden können, um Big Data-Cluster für SQL Server zu erstellen.

[Notebooks](notebooks-guidance.md), die ursprünglich als Open-Source-Projekt implementiert wurden, wurden in [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download) implementiert. Sie können Markdown für Text in den Textzellen und einen der verfügbaren Kernel verwenden, um Code in den Codezellen zu schreiben.

Sie können Notebooks verwenden, um Big Data-Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] bereitzustellen.

## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen erfüllt sein, damit das Notebook gestartet werden kann:

* Die neueste Version von [Azure Data Studio Insiders-Build](http://docs.microsoft.com/sql/azure-data-studio/download) ist installiert.
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung ist in Azure Data Studio installiert.

Zusätzlich hierzu sind folgende Komponenten erforderlich, um einen Big Data-Cluster für SQL Server 2019 bereitstellen zu können:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>Starten des Notebooks

1. Installieren und starten Sie den [Azure Data Studio Insiders-Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master).

1. Klicken Sie auf der Registerkarte **Verbindungen** auf **...** , und wählen Sie **SQL Server-Big Data-Cluster bereitstellen...** aus.

   ![KI und Machine Learning](media/deploy-notebooks/deploy-notebooks-1.png)

1. Wählen Sie in **Bereitstellungsziel** unter **Optionen** entweder **Neuer Azure Kubernetes-Cluster** oder **Vorhandener Azure Kubernetes Service-Cluster** aus.

1. Wählen Sie **Notebook öffnen** aus.

Mit dieser Aktion wird das entsprechende Notebook gestartet. Um die Bereitstellung abzuschließen, befolgen Sie die Anweisungen im Notebook, um einen Big Data Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] in einem vorhandenen oder neuen Azure Kubernetes Service-Cluster bereitzustellen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Bereitstellung finden Sie unter [Bereitstellungsanleitung für Big Data-Cluster für SQL Server](deployment-guidance.md).
