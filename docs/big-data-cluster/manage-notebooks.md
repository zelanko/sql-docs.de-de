---
title: Verwalten eines Big Data-Clusters für SQL Server mit Azure Data Studio-Notebooks
titleSuffix: Manage SQL Server big data cluster cluster with Azure Data Studio notebooks
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data-Cluster zu verwalten und Probleme für ihn zu beheben.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 09/09/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cb2fcaf7431b5d79698af009b533ee49254777fe
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70846646"
---
# <a name="manage-big-data-clusters-for-sql-server-with-azure-data-studio-notebooks"></a>Verwalten von Big Data-Clustern für SQL Server mit Azure Data Studio-Notebooks

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] stellt eine Erweiterung für Azure Data Studio bereit, die Notebooks umfasst. Ein Notebook enthält Dokumentation und Code, die Sie in Azure Data Studio verwenden können, um Big Data-Cluster für SQL Server zu verwalten.

[Notebooks](notebooks-guidance.md), die ursprünglich als Open-Source-Projekt implementiert wurden, wurden in [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/download) implementiert. Sie können Markdown für Text in den Textzellen und einen der verfügbaren Kernel verwenden, um Code in den Codezellen zu schreiben.

Sie können Notebooks verwenden, um Big Data-Cluster für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] bereitzustellen.

Zusätzlich zu Notebooks können Benutzer eine Sammlung von Notebooks anzeigen, die als jupyter-Bücher bezeichnet werden. Ein Jupyter Book stellt ein Inhaltsverzeichnis bereit, um in einer Sammlung von Notebooks zu navigieren, sodass ein Benutzer das benötigte Notebook leicht finden kann, egal, ob zur Problembehandlung von SQL Server oder zum Anzeigen des Clusterstatus.

## <a name="prerequisites"></a>Erforderliche Komponenten

Die folgenden Voraussetzungen müssen erfüllt sein, damit ein Notebook gestartet werden kann:

* Die neueste Version von [Azure Data Studio Insiders-Build](https://aka.ms/azuredatastudio-rc).
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung ist in Azure Data Studio installiert.

Zusätzlich hierzu sind folgende Komponenten erforderlich, um einen Big Data-Cluster für SQL Server 2019 bereitstellen zu können:

* [azdata](deploy-install-azdata.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)

## <a name="accessing-troubleshooting-notebooks"></a>Zugreifen auf Notebooks zur Problembehandlung
Es gibt drei Möglichkeiten, um auf Problem Behandlungs Notebooks zuzugreifen.

### <a name="command-palette"></a>Befehlspalette
1. Klicken Sie auf **Befehls Palette** **anzeigen** .
2. Geben Sie jupyter Books: Leitfaden zu SQL Server 2019 "
3. Dadurch wird das jupyter Books-Viewlet mit dem jupyter-Buch geöffnet, das die im Zusammenhang mit SQL Server Big Data-Clustern gehörigen der TSG enthält.

### <a name="sql-master-dashboard"></a>SQL-Master-Dashboard
1. Nachdem Sie Azure Data Studio Insiders installiert haben, stellen Sie eine Verbindung mit einer Big Data-Clusterinstanz für SQL Server her.
2. Sobald diese Verbindung erfolgreich hergestellt ist, klicken Sie im Viewlet „Verbindungen“ mit der rechten Maustaste auf den Servernamen, und klicken Sie dann auf **Verwalten**.
3. Klicken Sie auf dem Dashboard auf **SQL Server-Big Data-Cluster**. Klicken Sie auf **SQL Server 2019 Guide**, um das Jupyter Book mit den Notebooks zu öffnen, die Sie benötigen.
    ![button](media/manage-notebooks/jupyter-book-button.png)

1. Dadurch wird das jupyter Books-Viewlet geöffnet, in dem das jupyter-Buch der TSG bereits geöffnet ist.
4. Klicken Sie auf das Notebook für die Aufgabe, die Sie ausführen müssen.

### <a name="controller-dashboard"></a>Controller Dashboard
1. Erweitern Sie in der Ansicht Verbindungen **SQL Server Big Data-Cluster.**
2. Details zum Controller Endpunkt hinzufügen.
3. Klicken Sie nach erfolgreicher Verbindung mit Controller mit der rechten Maustaste auf den Endpunkt, und klicken Sie dann auf **verwalten.**
4. Nachdem das Dashboard geladen wurde, klicken Sie auf Problembehandlung, um das jupyter Book TSG zu starten.

## <a name="how-to-use-troubleshooting-notebooks"></a>Verwenden von Problem Behandlungs Notebooks
1. Durchsuchen Sie das vorhandene jupyter-Buch Inhaltsverzeichnis, bis Sie die benötigte TSG gefunden haben.
1. Alle Notebooks sind optimiert, wenn der Benutzer nur auf " **Zellen ausführen** " klicken muss. Dadurch wird jede Zelle im Notebook einzeln ausgeführt, bis Sie beendet ist.
1. Wenn ein Fehler auftritt, wird im jupyter-Buch ein Notebook vorgeschlagen, das Sie ausführen können, um den Fehler zu beheben. Führen Sie die Schritte aus, und führen Sie dann das Notebook erneut aus.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Notebooks in Azure Data Studio finden Sie unter [Verwenden von Notebooks in SQL Server 2019 (Vorschauversion)](notebooks-guidance.md).
