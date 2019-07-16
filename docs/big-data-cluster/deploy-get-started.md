---
title: Erste Schritte
titleSuffix: SQL Server big data clusters
description: Erfahren Sie die Schritte und Ressourcen zum Bereitstellen von SQL Server-2019 big Data-Clustern (Vorschau).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8583610606e5d554f039a69688af3ddff8dc8bb3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958533"
---
# <a name="get-started-with-sql-server-big-data-clusters"></a>Erste Schritte mit SQL Server-big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel bietet einen Überblick über die Bereitstellung einer [SQL Server-2019 big Data-Cluster (Vorschau)](big-data-cluster-overview.md). Es soll Sie die Konzepte zu orientieren, und geben Sie ein Framework für das Verständnis der anderen bereitstellungsartikeln in diesem Abschnitt. Ihre spezifischen Bereitstellungsschritte hängen von Ihrer Plattform-Optionen für den Client und Server.

## <a id="tools"></a> -Clienttools

Big Data-Cluster erfordern einen bestimmten Satz von Client-Tools. Bevor Sie einen big Data-Cluster für Kubernetes bereitstellen, sollten Sie die folgenden Tools installieren:

| Tool | Beschreibung |
|---|---|
| **mssqlctl** | Wird bereitgestellt und verwaltet big Data-Cluster. |
| **kubectl** | Erstellt und verwaltet die zugrunde liegende Kubernetes-Cluster. |
| **Azure Data Studio** | Grafische Benutzeroberfläche für die Verwendung von big Data-Cluster. |
| **SQL Server-2019-Erweiterung** | Azure Data Studio-Erweiterung, die Funktionen für big Data-Cluster ermöglicht. |

Andere Tools sind für verschiedene Szenarien erforderlich. Alle Artikel sollte erläutern, die erforderlichen Tools für eine bestimmte Aufgabe. Eine vollständige Liste von Tools und Installationslinks, finden Sie unter [Installieren von SQL Server-2019 big Data-Tools](deploy-big-data-tools.md).

## <a name="kubernetes"></a>Kubernetes

Big Data-Cluster werden bereitgestellt, als eine Reihe von zusammenhängenden Container, die in verwaltet werden [Kubernetes](https://kubernetes.io/docs/home). Sie können die kubernetes-Clustern in verschiedene Arten hosten. Auch wenn Sie bereits über eine vorhandene Kubernetes-Umgebung verfügen, prüfen Sie die entsprechenden Anforderungen für big Data-Cluster.

- **Azure Kubernetes Service (AKS)** : AKS können Sie einen verwaltete Kubernetes-Cluster in Azure bereitstellen. Nur verwaltet, und behalten die Agent-Knoten. Mit AKS müssen Sie nicht Ihre eigene Hardware für den Cluster bereitstellen. Es ist auch einfach, einen big Data-Cluster verwenden [Bereitstellungsskript](quickstart-big-data-cluster-deploy.md) auf der AKS-Cluster erstellen und Bereitstellen der big Data-Cluster in einem Schritt. Weitere Informationen zur Verwendung von AKS mit big Data-Clustern finden Sie unter [Konfigurieren von Azure Kubernetes-Dienst für SQL Server-2019 big Data-Cluster (Vorschau) Bereitstellungen](deploy-on-aks.md).

- **Mehrere Computer**: Sie können auch Kubernetes bereitstellen, die auf mehreren Linux-Computern, die physischen Servern oder virtuellen Computern sein könnte. Die [Kubeadm](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) Tool zum Erstellen des Kubernetes-Clusters verwendet werden kann. Diese Methode funktioniert gut, wenn Sie bereits vorhandene Infrastruktur verfügen, die Sie für Ihre big Data-Cluster verwenden möchten. Weitere Informationen zur Verwendung von **Kubeadm** Bereitstellungen mit big Data-Clustern finden Sie unter [Kubernetes konfigurieren, auf mehreren Computern für SQL Server-2019 big Data-Cluster (Vorschau) Bereitstellungen](deploy-with-kubeadm.md).

- **Minikube**: Minikube können Sie lokale Ausführung von Kubernetes auf einem einzelnen Server. Es ist eine gute Option, wenn Sie, sich big Data-Cluster versuchen, oder für die Verwendung in einem Szenario mit Test- oder Entwicklungszwecken benötigen. Weitere Informationen zur Verwendung von Minikube finden Sie unter den [Minikube Dokumentation](https://kubernetes.io/docs/setup/minikube/). Bestimmte Anforderungen für die Verwendung von Minikube mit big Data-Clustern finden Sie unter [Minikube für SQL Server-2019 big Data-Cluster-Bereitstellungen konfigurieren](deploy-on-minikube.md).

## <a name="deploy-a-big-data-cluster"></a>Bereitstellen von Big Data-Clustern

Nach dem Konfigurieren von Kubernetes wird, die Sie Bereitstellen eines big Data-Clusters mit der `mssqlctl bdc create` Befehl. Bei der Bereitstellung können Sie verschiedene Ansätze nutzen.

- Wenn Sie in einer Dev / Test-Umgebung bereitstellen, können Sie eine der verwenden die [Standardkonfigurationen](deployment-guidance.md#deploy) gebotenen **Mssqlctl**.

- Informationen zum Anpassen der Bereitstellung können Sie erstellen und verwenden Sie Ihren eigenen [bereitstellungskonfigurationsdateien](deployment-guidance.md#configfile).

- Für eine vollständig unbeaufsichtigte Installation können Sie alle anderen Einstellungen in Umgebungsvariablen übergeben. Weitere Informationen finden Sie unter [unbeaufsichtigte Bereitstellungen](deployment-guidance.md#unattended).

## <a name="deployment-scripts"></a>Bereitstellungsskripts

Bereitstellungsskripts können sowohl Kubernetes und big Data-Cluster in einem einzigen Schritt bereitstellen. Sie bieten oft auch Standardwerte für big Data-Clustereinstellungen an. Ein Beispiel für ein Bereitstellungsskript für big Data-Cluster in Azure Kubernetes Service (AKS) finden Sie im folgenden Artikel:

[Bereitstellen einer SQL Server-2019 big Data-mit einem Bereitstellungsskript (AKS Cluster)](quickstart-big-data-cluster-deploy.md).

Sie können jedes Bereitstellungsskript anpassen, erstellen Sie Ihre eigene Version, die die Umgebungsvariablen für big Data-Cluster anders konfiguriert.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie erfolgreich einen big Data-Cluster bereitstellen [Verbinden mit dem Cluster](connect-to-big-data-cluster.md) und [Beispieldaten laden](tutorial-load-sample-data.md) für die Verwendung mit einer Reihe von exemplarischen Vorgehensweisen.