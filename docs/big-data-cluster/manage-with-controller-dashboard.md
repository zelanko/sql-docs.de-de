---
title: Verwalten von Big Data-Clustern für SQL Server mit dem Controllerdashboard
titleSuffix: Manage SQL Server big data cluster with controller dashboard
description: Verwenden Sie ein Notebook aus Azure Data Studio, um einen Big Data-Cluster zu verwalten und Probleme für ihn zu beheben.
author: yualan
ms.author: alanyu
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a78074b7e32df18de1308d2354d98079d074f9bf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "73531943"
---
# <a name="manage-big-data-clusters-for-sql-server-controller-dashboard"></a>Verwalten von Big Data-Clustern mit dem Controllerdashboard von SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Neben der Verwendung von **azdata** und dem Notebook für den Clusterstatus können Sie den Status eines Big Data-Clusters für SQL Server noch auf eine andere Weise anzeigen. Sie können den Big Data-Clustercontroller für SQL Server über das Viewlet **Verbindungen** hinzufügen. Damit können Sie die Clusterintegrität in einem Dashboard anzeigen.

![Dashboard](media/manage-with-controller-dashboard/controller-dashboard.png)
## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen erfüllt sein, damit das Notebook gestartet werden kann:

* Die neueste Version von [Azure Data Studio Insiders-Build](https://docs.microsoft.com/sql/big-data-cluster/deploy-big-data-tools?view=sqlallproducts-download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc).
* [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung ist in Azure Data Studio installiert.

Zusätzlich sind für Big Data-Cluster für SQL Server 2019 folgende Komponenten erforderlich:

* **azdata**
    - [Windows Installer](deploy-install-azdata-installer.md)
    - [Linux-Paket-Manager](deploy-install-azdata-linux-package.md)
* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management)
* [Azure-Befehlszeilenschnittstelle](/cli/azure/install-azure-cli)

## <a name="add-sql-server-big-data-cluster-controller"></a>Hinzufügen des Big Data-Clustercontrollers für SQL Server

1. Klicken Sie im linken Bereich auf die Ansicht „Verbindungen“.
2. Klicken Sie im unteren Bereich der Ansicht „Verbindungen“ auf **Big Data-Cluster für SQL Server**, um die Ansicht zu erweitern.
3. Klicken Sie auf **Big Data-Clustercontroller für SQL Server hinzufügen**, um ein neues Dialogfeld zu öffnen.

## <a name="add-new-controller"></a>Hinzufügen des neuen Controllers

1. Fügen Sie Ihren Clusternamen hinzu.
2. Fügen Sie die URL Ihres Clusterverwaltungsdiensts hinzu. Diese finden Sie in der Tabelle mit den Dienstendpunkten im BDC-Dashboard, oder wenden Sie sich hierfür an den Clusteradministrator.
3. Fügen Sie Ihren Benutzernamen und das Kennwort hinzu.

## <a name="launch-controller-dashboard"></a>Starten des Controllerdashboards

1. Nachdem Sie den Controller erfolgreich hinzugefügt haben, können Sie ihn unter „Big Data-Cluster für SQL Server“ anzeigen.
2. Klicken Sie zum Starten des Dashboards mit der rechten Maustaste auf den Controller, und klicken Sie dann auf **Verwalten**.

## <a name="controller-dashboard"></a>Controllerdashboard

1. Das Controllerdashboard besteht aus drei Hauptkomponenten:

    - Der **Symbolleiste** oben mit Aktionen für das Dashboard
    - Dem **Navigationsbereich** auf der linken Seite, der sich je nach Ansicht im Dashboard verändert
    - Der **Ansicht**, die den Hauptteil der Seite ausmacht

2. Auf der Seite **Big Data-Cluster – Übersicht** wird Folgendes angezeigt:

    - **Clustereigenschaften** mit Informationen zu Ihrem Cluster
    - **Clusterübersicht** mit einer allgemeinen Übersicht über alle sowie die fehlerhaften Clusterkomponenten
    - **Dienstendpunkte**, um verschiedene Dienstendpunkte in Ihrem Big Data-Cluster für SQL Server zu kopieren oder darauf zuzugreifen

3. Im **Navigationsbereich** wird eine Liste der Dienste angezeigt. Durch Klicken auf einen beliebigen Dienst können Sie weitere Clusterdetails anzeigen. Dieselben Informationen werden auch angezeigt, wenn Sie unter **Clusterübersicht** auf einen Dienst klicken.

4. Unter **Clusterdetails** enthalten alle Ansichten dieselben Benutzeroberflächenkomponenten:

    - **Details zum Integritätsstatus** mit dem Zustand und dem Integritätsstatus der jeweiligen Komponente
    - **Metriken und Protokolle** mit zusätzlichen Metriken und Protokollen über Grafana und Kibana

1. Wird eine fehlerhafte Komponente angezeigt, klicken Sie in der Symbolleiste auf **Problembehandlung**, um Jupyter Book mit einem Notebook zum Diagnostizieren des Problems zu starten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Controller finden Sie in der [Controller-Dokumentation](concept-controller.md).