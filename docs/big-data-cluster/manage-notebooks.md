---
title: Verwalten von SQL Server Big Data-Cluster mit Azure Data Studio Notebooks
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data Cluster zu verwalten und Probleme zu beheben.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8d87b09878539cccd40191d870bf97487579dca2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426400"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Verwalten von Big Data Clustern für SQL Server mit Azure Data Studio Notebooks

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]stellt eine Erweiterung für Azure Data Studio bereit, die Bereitstellungs Notebooks umfasst. Ein Bereitstellungs Notebook umfasst Dokumentation und Code, die Sie in Azure Data Studio verwenden können, um Big Data Cluster für SQL Server zu verwalten.

[Notebooks](notebooks-guidance.md) , die ursprünglich als Open-Source-Projekt implementiert wurden, wurden in [Azure Data Studio](http://docs.microsoft.com/sql/azure-data-studio/download)implementiert. Sie können markdown für Text in den Text Zellen und einen der verfügbaren Kernel zum Schreiben von Code in den Code Zellen verwenden.

Sie können Notebooks verwenden, um Big Data Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]bereitzustellen.

## <a name="prerequisites"></a>Vorraussetzungen

Folgende Voraussetzungen sind erforderlich, damit das Notebook gestartet werden kann:

* Neueste Version von [Azure Data Studio Insider-Build](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-master)
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]Erweiterung in Azure Data Studio installiert

Zusätzlich zu den obigen Schritten erfordert die Bereitstellung von SQL Server 2019 Big Data Cluster auch Folgendes:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)
