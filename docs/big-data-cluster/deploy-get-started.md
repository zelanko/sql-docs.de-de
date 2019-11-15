---
title: Erste Schritte
titleSuffix: SQL Server Big Data Clusters
description: Erfahren Sie mehr über die Schritte und Ressourcen für die Bereitstellung von SQL Server-Big Data-Clustern.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2bbb4c05a6760709fcb873cd8c39f301c37aeb2b
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73706364"
---
# <a name="get-started-with-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Erste Schritte mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel finden Sie eine Übersicht über die Bereitstellung von [[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md).

Informationen zu weiteren Bereitstellungsszenarios finden Sie unter:

- [Windows](../database-engine/install-windows/install-sql-server.md)
- [Linux](../linux/sql-server-linux-setup.md)
- [Docker-Container](../linux/sql-server-linux-configure-docker.md)

In diesem Artikel erhalten Sie einen Überblick über die grundlegenden Konzepte und das Grundwissen, um die anderen Bereitstellungsartikel in diesem Abschnitt zu verstehen. Die konkreten Schritte für die Bereitstellung hängen von der Plattform ab, die Sie für den Client und Server ausgewählt haben.

> [!TIP]
> Verwenden Sie eines der Beispielskripts aus dem [Abschnitt zu Skripts](#scripts), um schnell eine Umgebung mit Kubernetes und einem Big Data-Cluster bereitzustellen, damit Sie die Funktionen kennenlernen können. Verwenden Sie nach der Bereitstellung die [Clienttools](#tools) aus dem folgenden Abschnitt, um den Cluster zu verwalten.

## <a id="tools"></a> Clienttools

Für die Bereitstellung von Big-Data-Clustern benötigen Sie eine Reihe von bestimmten Clienttools. Installieren Sie die folgenden Tools, bevor Sie Big-Data-Cluster für Kubernetes bereitstellen:

| Tool | und Beschreibung |
|---|---|
| **azdata** | Zur Bereitstellung und Verwaltung von Big-Data-Clustern. |
| **kubectl** | Zur Erstellung und Verwaltung des zugrunde liegenden Kubernetes-Clusters. |
| **Azure Data Studio** | Grafische Benutzeroberfläche für die Verwendung des Big-Data-Clusters. |
| **Erweiterung von SQL Server 2019** | Erweiterung von Azure Data Studio zur Aktivierung von Big-Data-Clusterfunktionen. |

Für bestimmte Szenarios sind andere Tools erforderlich. Welche Tools für eine bestimmte Aufgabe erforderlich sind, erfahren Sie im jeweiligen Artikel. Eine vollständige Liste der Tools und Installationslinks finden Sie unter [Install SQL Server 2019 big data tools (Installieren von Big-Data-Tools für SQL Server 2019)](deploy-big-data-tools.md).

## <a name="kubernetes"></a>Kubernetes

Big-Data-Cluster werden als eine Reihe von miteinander verbundenen Containern bereitgestellt, die in [Kubernetes](https://kubernetes.io/docs/home) verwaltet werden. In Kubernetes stehen Ihnen verschiedene Hostingmöglichkeiten zur Verfügung. Auch wenn Sie bereits über eine vorhandene Kubernetes-Umgebung verfügen, sollten Sie die entsprechenden Anforderungen für Big-Data-Cluster überprüfen.

- **Azure Kubernetes Service (AKS)** : Mit AKS können Sie einen verwalteten Kubernetes-Cluster in Azure bereitstellen. Sie verwalten und warten nur die Agent-Knoten. Sie müssen mit AKS keine eigene Hardware für den Cluster bereitstellen. Außerdem können Sie mithilfe eines [Python-Skripts](quickstart-big-data-cluster-deploy.md) oder eines [Notebooks für die Bereitstellung](deploy-notebooks.md) in einem einzigen Schritt den AKS-Cluster erstellen und den Big-Data-Cluster bereitstellen. Weitere Informationen zum Konfigurieren von AKS für die Bereitstellung eines Big Data-Clusters finden Sie unter [Konfigurieren von Azure Kubernetes Service für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]-Bereitstellungen](deploy-on-aks.md).

- **Mehrere Computer**: Sie können Kubernetes auch auf mehreren Linux-Computern bereitstellen. Dabei kann es sich um physische Server oder virtuelle Computer handeln. Den Kubernetes-Cluster können Sie mithilfe des Tools [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) erstellen. Diese Art der Bereitstellung können Sie mit einem [Bash-Skript](deployment-script-single-node-kubeadm.md) automatisieren. Diese Methode eignet sich hervorragend, wenn Sie bereits über eine vorhandene Infrastruktur verfügen, die Sie für den Big-Data-Cluster verwenden möchten. Weitere Informationen zur Verwendung von **kubeadm**-Bereitstellungen mit Big Data-Clustern finden Sie unter [Konfigurieren von Kubernetes auf mehreren Computern für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]-Bereitstellungen](deploy-with-kubeadm.md).

## <a name="deploy-a-big-data-cluster"></a>Bereitstellen von Big Data-Clustern

Nach der Konfiguration von Kubernetes stellen Sie mit dem Befehl `azdata bdc create` einen Big-Data-Cluster bereit. Für die Bereitstellung gibt es verschiedene Ansätze:

- Wenn Sie für eine Entwicklungs-/Testumgebung bereitstellen, können Sie eine der [Standardkonfigurationen](deployment-guidance.md#deploy) von **azdata** verwenden.

- Wenn Sie Ihre Bereitstellung anpassen möchten, können Sie Ihre eigenen [Konfigurationsdateien für die Bereitstellung](deployment-guidance.md#configfile) erstellen und verwenden.

- Bei einer vollständig unbeaufsichtigten Installation können Sie alle weiteren Einstellungen in Umgebungsvariablen übergeben. Weitere Informationen hierzu finden Sie unter [Unbeaufsichtigte Bereitstellungen](deployment-guidance.md#unattended).


## <a id="scripts"></a>Bereitstellungsskripts

Mithilfe von Bereitstellungsskripts können Sie Kubernetes und Big-Data-Cluster in einem einzigen Schritt bereitstellen. Häufig enthalten Bereitstellungsskripts auch Standardwerte für die Einstellungen von Big-Data-Clustern. Sie können ein Bereitstellungsskript auch anpassen, indem Sie Ihre eigene Version erstellen, mit der die Bereitstellung des Big-Data-Clusters anders konfiguriert wird.

Folgende Bereitstellungsskripts sind derzeit verfügbar:

- [Python-Skript: Bereitstellen von Big-Data-Clustern in Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
- [Bash-Skript: Bereitstellen von Big-Data-Clustern in einem kubeadm-Cluster mit einem einzelnen Knoten](deployment-script-single-node-kubeadm.md)

## <a name="deployment-notebooks"></a>Bereitstellungsnotebooks

Sie können Big-Data-Cluster auch über die Ausführung eines Azure Data Studio-Notebooks bereitstellen. Weitere Informationen zur Bereitstellung in AKS mithilfe eines Notebooks finden Sie im folgenden Artikel:

- [Deploy a big data cluster with Azure Data Studio Notebooks (Bereitstellen von Big-Data-Clustern mit Azure Data Studio-Notebooks)](deploy-notebooks.md).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie einen Big-Data-Cluster erfolgreich bereitgestellt haben, stellen Sie nun eine [Verbindung mit dem Cluster](connect-to-big-data-cluster.md) her, und [laden Sie Beispieldaten](tutorial-load-sample-data.md) für die weitere Verwendung in verschiedenen exemplarischen Vorgehensweisen.
