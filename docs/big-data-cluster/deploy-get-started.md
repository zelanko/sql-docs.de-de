---
title: Erste Schritte
titleSuffix: SQL Server big data clusters
description: Erfahren Sie mehr über die Schritte und Ressourcen für die Bereitstellung von SQL Server 2019 Big Data Clustern (Vorschauversion).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 41dd39c7aa613083f8ff47824ed6238b6f3c61b9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419425"
---
# <a name="get-started-with-sql-server-big-data-clusters"></a>Ersten Einstieg in SQL Server Big Data Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel bietet einen Überblick über die Bereitstellung eines [SQL Server 2019 Big Data-Clusters (Vorschauversion)](big-data-cluster-overview.md). Sie soll Sie an den Konzepten orientieren und ein Framework zum Verständnis der anderen Bereitstellungs Artikel in diesem Abschnitt bereitstellen. Ihre spezifischen Bereitstellungs Schritte unterscheiden sich je nach Platt Form Auswahl für Client und Server.

## <a id="tools"></a>Client Tools

Für Big Data-Cluster ist ein bestimmter Satz von Client Tools erforderlich. Bevor Sie einen Big Data Cluster für Kubernetes bereitstellen, sollten Sie die folgenden Tools installieren:

| Tool | Beschreibung |
|---|---|
| **azdata** | Stellt Big Data Cluster bereit und verwaltet Sie. |
| **kubectl** | Erstellt und verwaltet den zugrunde liegenden Kubernetes-Cluster. |
| **Azure Data Studio** | Grafische Oberfläche für die Verwendung des Big Data Clusters. |
| **SQL Server 2019-Erweiterung** | Azure Data Studio Erweiterung, die Big Data Cluster Funktionen aktiviert. |

Für verschiedene Szenarien sind andere Tools erforderlich. In jedem Artikel sollten die erforderlichen Tools für die Durchführung einer bestimmten Aufgabe erläutert werden. Eine vollständige Liste der Tools und Installations Links finden Sie unter [Install SQL Server 2019 Big Data Tools](deploy-big-data-tools.md).

## <a name="kubernetes"></a>Kubernetes

Big Data-Cluster werden als eine Reihe von miteinander verbundenen Containern bereitgestellt, die in [Kubernetes](https://kubernetes.io/docs/home)verwaltet werden. Sie können Kubernetes auf unterschiedlichste Weise hosten. Auch wenn Sie bereits über eine vorhandene Kubernetes-Umgebung verfügen, sollten Sie die entsprechenden Anforderungen für Big Data Cluster überprüfen.

- **Azure Kubernetes Service (AKS)** : AKS ermöglicht Ihnen die Bereitstellung eines verwalteten Kubernetes-Clusters in Azure. Sie verwalten und warten nur die-Agent-Knoten. Mit AKS müssen Sie keine eigene Hardware für den Cluster bereitstellen. Außerdem ist es einfach, ein Big Data Cluster [Bereitstellungs Skript](quickstart-big-data-cluster-deploy.md) zu verwenden, um den AKS-Cluster zu erstellen und den Big Data Cluster in einem Schritt bereitzustellen. Weitere Informationen zur Verwendung von AKS mit Big Data Clustern finden Sie unter [configure Azure Kubernetes Service for SQL Server 2019 Big Data Cluster (Preview) bereit Stellungen](deploy-on-aks.md).

- **Mehrere**Computer: Sie können Kubernetes auch auf mehreren Linux-Computern bereitstellen, bei denen es sich um physische Server oder virtuelle Computer handeln könnte. Das Tool [kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) kann verwendet werden, um den Kubernetes-Cluster zu erstellen. Diese Methode funktioniert gut, wenn Sie bereits über eine vorhandene Infrastruktur verfügen, die Sie für Ihren Big Data Cluster verwenden möchten. Weitere Informationen zur Verwendung von **kubeadm** -bereit Stellungen mit Big Data Clustern finden Sie unter [configure Kubernetes on multiple machines for SQL Server 2019 Big Data Cluster (Preview) bereit Stellungen](deploy-with-kubeadm.md).

- **Minikube**: Minikube ermöglicht Ihnen, Kubernetes lokal auf einem einzelnen Server auszuführen. Es ist eine gute Option, wenn Sie Big Data Cluster ausprobieren oder Sie in einem Test-oder Entwicklungsszenario verwenden müssen. Weitere Informationen zur Verwendung von minikube finden Sie in der [minikube-Dokumentation](https://kubernetes.io/docs/setup/minikube/). Spezifische Anforderungen für die Verwendung von Minikube mit Big Data Clustern finden Sie unter [Konfigurieren von Minikube für SQL Server 2019 Big Data Cluster Bereitstellungen](deploy-on-minikube.md).

## <a name="deploy-a-big-data-cluster"></a>Bereitstellen von Big Data-Clustern

Nachdem Sie Kubernetes konfiguriert haben, stellen Sie mit dem `azdata bdc create` Befehl einen Big Data Cluster bereit. Bei der Bereitstellung von können Sie verschiedene Ansätze verwenden.

- Wenn Sie in einer dev/Test-Umgebung bereitstellen, können Sie auswählen, ob Sie eine der von **azdata**bereitgestellten [Standardkonfigurationen](deployment-guidance.md#deploy) verwenden möchten.

- Zum Anpassen der Bereitstellung können Sie eigene [Bereitstellungs Konfigurationsdateien](deployment-guidance.md#configfile)erstellen und verwenden.

- Für eine vollständig unbeaufsichtigte Installation können Sie alle anderen Einstellungen in Umgebungsvariablen übergeben. Weitere Informationen finden Sie unter [unbeaufsichtigte bereit Stellungen](deployment-guidance.md#unattended).

## <a name="deployment-scripts"></a>Bereitstellungsskripts

Mithilfe von Bereitstellungs Skripts können Sie sowohl Kubernetes-als auch Big Data Cluster in einem einzigen Schritt bereitstellen. Sie stellen auch häufig Standardwerte für Big Data Cluster Einstellungen bereit. Ein Beispiel für ein Bereitstellungs Skript für Big Data Cluster in Azure Kubernetes Service (AKS) finden Sie im folgenden Artikel:

Stellen Sie [eine SQL Server 2019 Big Data-Cluster mit einem Bereitstellungs Skript (AKS) bereit](quickstart-big-data-cluster-deploy.md).

Sie können alle Bereitstellungs Skripts anpassen, indem Sie eine eigene Version erstellen, die die Big Data Cluster Umgebungsvariablen anders konfiguriert.

Stellen Sie [eine SQL Server 2019 Big Data Cluster mit Azure Data Studio Notebooks](deploy-notebooks.md)bereit.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie einen Big Data Cluster erfolgreich bereitgestellt haben, stellen Sie eine [Verbindung mit dem Cluster](connect-to-big-data-cluster.md) her, und laden Sie in Erwägung, [Beispiel Daten](tutorial-load-sample-data.md) für mehrere exemplarische Vorgehensweisen