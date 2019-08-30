---
title: Verwalten von SQL Server Big Data-Cluster mit Controller Dashboard
titleSuffix: Manage SQL Server big data cluster with controller dashboard
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data-Cluster zu verwalten und Probleme für ihn zu beheben.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 08/29/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5fadb9b069e6f70cb780e6dc69295f63330a683a
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160719"
---
# <a name="manage-big-data-clusters-for-sql-server-controller-dashboard"></a>Verwalten von Big Data Clustern für SQL Server Controller-Dashboard

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Zusätzlich zu **azdata** und dem Cluster Status Notebook gibt es eine weitere Möglichkeit, den Status eines SQL Server Big Data-Clusters anzuzeigen. Nun können Sie den SQL Server Big Data-Cluster Controller über das Ansichts-Viewlet hinzufügen. Auf diese Weise können Sie über ein Dashboard verfügen, um die Cluster Integrität anzuzeigen.

![Dashboard](media/manage-with-controller-dashboard/controller-dashboard.png)
## <a name="prerequisites"></a>Erforderliche Komponenten

Zum Starten des Notebooks sind folgende Voraussetzungen erforderlich:

* Die neueste Version von [Azure Data Studio Insiders-Build](https://docs.microsoft.com/sql/big-data-cluster/deploy-big-data-tools?view=sqlallproducts-download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc).
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung ist in Azure Data Studio installiert.

Zusätzlich zu den obigen Informationen erfordert SQL Server 2019-Big Data-Cluster auch Folgendes:

* **azdata**
    - [Linux-Paket-Manager](deploy-install-azdata-linux-package.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure CLI](/cli/azure/install-azure-cli)


## <a name="add-sql-server-big-data-cluster-controller"></a>Hinzufügen von SQL Server Big Data Cluster Controller

1. Klicken Sie im linken Bereich auf die Ansicht Verbindungen.
2. Klicken Sie unten in der Ansicht Verbindungen auf **SQL Server Big Data-Cluster** , um ihn zu erweitern.
3. Wenn Sie auf **SQL Server Big Data Cluster Controller hinzufügen**klicken, wird ein neues Dialogfeld geöffnet.

## <a name="add-new-controller"></a>Neuen Controller hinzufügen

1. Fügen Sie den Cluster Namen hinzu.
2. Fügen Sie die URL des Cluster verwaltungsdienstanbieter hinzu. Diese finden Sie in der Tabelle mit den Dienst Endpunkten Ihres BDC-Dashboards, oder Fragen Sie den Cluster Administrator.
3. Fügen Sie Benutzername und Kennwort hinzu.

## <a name="launch-controller-dashboard"></a>Controller Dashboard starten

1. Wenn Sie Ihren Controller erfolgreich hinzugefügt haben, können Sie ihn unter SQL Server Big Data-Cluster anzeigen.
2. Klicken Sie zum Starten des Dashboards mit der rechten Maustaste auf den Controller, und klicken Sie auf **Verwalten**

## <a name="controller-dashboard"></a>Controller Dashboard

1. Im Controller Dashboard gibt es drei Hauptkomponenten:

    - **Symbolleiste** oben, die Aktionen für das Dashboard enthält.
    - Der Navigationsbereich auf der linken Seite ändert sich in die unterschiedlichen Ansichten auf dem Dashboard.
    - **Ansicht** , die die Mehrzahl der Seite abdeckt.

2. Auf der **Übersichtsseite für Big Data-Cluster** können Sie Folgendes sehen:

    - **Cluster Eigenschaften** , um Informationen über Ihren Cluster anzuzeigen.
    - **Übersicht** über den Cluster, um allgemeine Übersicht über alle Cluster Komponenten und welche fehlerhaft sind
    - **Dienst Endpunkte** zum Kopieren oder zugreifen auf verschiedene Dienste innerhalb Ihres SQL Server Big Data-Clusters.

3. Im Navigationsbereich sehen Sie die Liste der Dienste **,** und klicken Sie auf einen, um weitere Cluster Details anzuzeigen. Dies ist die gleiche Ansicht, wenn Sie in der **Cluster Übersicht** auf einen Dienst klicken.

4. Jede Ansicht unter **Cluster Details** besteht aus den gleichen UI-Komponenten:

    - Integritäts **Status Details** , die den Status und den Integritäts Status der Komponente gemeinsam verwenden.
    - **Metriken und Protokolle** zum Anzeigen zusätzlicher Metriken und Protokolle über grafana und kibana.

1. Wenn Sie eine fehlerhafte Komponente anzeigen, klicken Sie auf der Symbolleiste auf Problembehandlung, um ein jupyter-Buch mit einem Notebook zu starten und die Diagnose des Problems zu erleichtern.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Controller finden Sie in [unserer Controller Dokumentation](concept-controller.md).