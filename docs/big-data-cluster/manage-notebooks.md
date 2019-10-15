---
title: Verwalten von SQL Server Big Data-Clustern mit Azure Data Studio Notebooks
titleSuffix: Manage SQL Server Big Data Clusters with Azure Data Studio notebooks
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data-Cluster zu verwalten und Probleme für ihn zu beheben.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e22b16cf8658e53e6bdc5db0fcd82692f3730fc7
ms.sourcegitcommit: c7a202af70fd16467a498688d59637d7d0b3d1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72313678"
---
# <a name="manage-sql-server-big-data-clusters-with-azure-data-studio-notebooks"></a>Verwalten von SQL Server Big Data-Clustern mit Azure Data Studio Notebooks

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] stellt eine Erweiterung für Azure Data Studio bereit, die Notebooks umfasst. Ein Notebook enthält Dokumentation und Code, die Sie in Azure Data Studio zum Verwalten von SQL Server 2019-Big Data-Clustern verwenden können.

[Notebooks](notebooks-guidance.md) wurden ursprünglich als Open-Source-Projekt implementiert und wurden in [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download)integriert. Sie können Markdown für Text in den Textzellen und einen der verfügbaren Kernel verwenden, um Code in den Codezellen zu schreiben.

Sie können Notebooks verwenden, um Big Data-Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] bereitzustellen.

Zusätzlich zu Notebooks können Sie eine Sammlung von Notebooks anzeigen, die als jupyter-Buch bezeichnet wird. Ein jupyter-Buch stellt ein Inhaltsverzeichnis bereit, das Sie bei der Navigation in einer Sammlung von Notebooks unterstützt. so können Sie problemlos das benötigte Notebook finden, unabhängig davon, ob Sie SQL Server oder den Cluster Status anzeigen möchten.

## <a name="prerequisites"></a>Erforderliche Komponenten

Zum Öffnen eines Notebooks benötigen Sie diese Voraussetzungen:

* Die neueste Version von [Azure Data Studio Insider Build](https://aka.ms/azuredatastudio-rc)
* Die [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung, installiert in Azure Data Studio

Zusätzlich zu diesen Voraussetzungen benötigen Sie zum Bereitstellen von SQL Server 2019-Big Data-Clustern auch Folgendes:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="access-troubleshooting-notebooks"></a>Zugriff auf Problem Behandlungs Notebooks
Es gibt drei Möglichkeiten, um auf Problem Behandlungs Notebooks zuzugreifen.

### <a name="command-palette"></a>Befehlspalette
1. Wählen Sie  > -**Befehls Palette** **anzeigen**aus.
2. Geben Sie **jupyter Books ein: SQL Server 2019 Guide @ no__t-0.

Das jupyter Books-Viewlet mit dem jupyter-Buch, das die Problem Behandlungs Notebooks enthält, die sich auf SQL Server Big Data-Cluster beziehen, wird geöffnet.

### <a name="sql-master-dashboard"></a>SQL-Master-Dashboard
1. Nachdem Sie Azure Data Studio Insider installiert haben, stellen Sie eine Verbindung mit einer SQL Server Big Data-Cluster Instanz her.
2. Nachdem Sie eine Verbindung mit der Instanz hergestellt haben, klicken Sie unter **Verbindungen** mit der rechten Maustaste auf den Servernamen, und wählen Sie **Verwalten**.
3. Wählen Sie im Dashboard **SQL Server Big Data-Cluster**aus. Wählen Sie **SQL Server 2019-Handbuch** aus, um das jupyter-Buch zu öffnen, das die benötigten Notebooks enthält.
    ![jupyter Notebooks im Dashboard @ no__t-1

1. Wählen Sie das Notebook für die Aufgabe aus, die Sie ausführen müssen.

### <a name="controller-dashboard"></a>Controller Dashboard
1. Erweitern Sie in der Ansicht Verbindungen **SQL Server Big Data-Cluster**.
2. Details zum Controller Endpunkt hinzufügen.
3. Nachdem Sie mit dem Controller verbunden sind, klicken Sie mit der rechten Maustaste auf den Endpunkt, und wählen Sie **Verwalten**aus.
4. Nachdem das Dashboard geladen wurde, **Wählen Sie** Problembehandlung aus, um die Handbücher zur Problembehandlung für jupyter zu öffnen

## <a name="use-troubleshooting-notebooks"></a>Verwenden von Problem Behandlungs Notebooks
1. Suchen Sie nach dem Handbuch zur Problembehandlung, das Sie im jupyter-Buch Inhaltsverzeichnis benötigen.
1. Die Notebooks sind optimiert, sodass Sie nur **Zellen ausführen**auswählen müssen. Diese Aktion führt jede Zelle im Notebook einzeln aus, bis das Notebook fertiggestellt ist.
1. Wenn ein Fehler gefunden wird, wird im jupyter-Buch ein Notebook vorgeschlagen, das Sie ausführen können, um den Fehler zu beheben. Führen Sie die empfohlenen Schritte aus, und führen Sie das Notebook dann erneut aus.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Notebooks in Azure Data Studio finden Sie unter [Verwenden von Notebooks in SQL Server 2019 (Vorschauversion)](notebooks-guidance.md).
