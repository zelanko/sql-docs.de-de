---
title: Bereitstellen SQL Server Big Data Clusters mit Azure Data Studio Notebooks
titleSuffix: Deploy SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data Cluster bereitzustellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f12a4f06ceb1c3a48b2b2fc661c59594e6d6cce3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426420"
---
# <a name="deploy-sql-server-big-data-cluster-with-azure-data-studio-notebooks"></a>Bereitstellen SQL Server Big Data Clusters mit Azure Data Studio Notebooks

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]stellt eine Erweiterung für Azure Data Studio bereit, die Bereitstellungs Notebooks umfasst. Ein Bereitstellungs Notebook umfasst Dokumentation und Code, den Sie in Azure Data Studio zum Erstellen eines SQL Server Big Data Clusters verwenden können. 

[Notebooks](notebooks-guidance.md) , die ursprünglich als Open-Source-Projekt implementiert wurden, wurden in [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)implementiert. Sie können markdown für Text in den Text Zellen und einen der verfügbaren Kernel zum Schreiben von Code in den Code Zellen verwenden.

Sie können Notebooks verwenden, um Big Data Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]bereitzustellen.

## <a name="prerequisites"></a>Vorraussetzungen
Folgende Voraussetzungen sind erforderlich, damit das Notebook gestartet werden kann:

* Neueste Version von [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download) installiert
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]Erweiterung in Azure Data Studio installiert

Zusätzlich zu den obigen Schritten erfordert die Bereitstellung von SQL Server 2019 Big Data Cluster auch Folgendes:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="launch-the-notebook"></a>Starten Sie das Notebook.

1. Installieren und starten Sie den [Azure Data Studio Insider-Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master).
1.  Klicken Sie auf der Registerkarte **Verbindungen** auf **...** , und wählen Sie **SQL Server Big Data Cluster bereitstellen...** aus.

   ![Ki und ml](media/deploy-notebooks/deploy-notebooks-1.png)

1. Wählen Sie im **Bereitstellungs Ziel**unter **Optionen**entweder **neuer Azure Kubernetes-Cluster** oder **vorhandener Azure Kubernetes Service-Cluster**aus.
1. Wählen Sie **Notebook öffnen**aus.

Mit dieser Aktion wird das entsprechende Notebook gestartet. Um die Bereitstellung abzuschließen, befolgen Sie die Anweisungen im Notebook, um einen Big Data Cluster [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] für in einem vorhandenen oder neuen Azure Kubernetes Service-Cluster bereitzustellen.
