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
ms.openlocfilehash: 64352409e567c5854d348dce8e6545317b41bc01
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725821"
---
# <a name="manage-big-data-clusters-for-sql-server-controller-dashboard"></a>Verwalten von Big Data-Clustern mit dem Controllerdashboard von SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Neben der Verwendung von **azdata** und dem Notebook für den Clusterstatus können Sie den Status eines Big Data-Clusters für SQL Server noch auf eine andere Weise anzeigen. Sie können den Big Data-Clustercontroller für SQL Server über das Viewlet **Verbindungen** hinzufügen. Damit können Sie die Clusterintegrität in einem Dashboard anzeigen.

![Dashboard](media/manage-with-controller-dashboard/controller-dashboard.png)
## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Voraussetzungen müssen erfüllt sein, damit das Notebook gestartet werden kann:

* Die neueste Version von [Azure Data Studio](../azure-data-studio/download-azure-data-studio.md) ist installiert.
* Die [[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]-Erweiterung ist in Azure Data Studio installiert.](../azure-data-studio/data-virtualization-extension.md)

Zusätzlich sind für Big Data-Cluster für SQL Server 2019 folgende Komponenten erforderlich:

* **azdata**
    - [Windows Installer](../azdata/install/deploy-install-azdata-installer.md)
    - [Linux-Paket-Manager](../azdata/install/deploy-install-azdata-linux-package.md)
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