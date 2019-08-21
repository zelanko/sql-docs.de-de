---
title: Konfigurieren von Minikube
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie minikube [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] für bereit Stellungen auf einem einzelnen Computer konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b2022fe6ad8a0aa23c4dd7d917e925ae1daba572
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652405"
---
# <a name="configure-minikube-for-sql-server-big-data-cluster-deployments"></a>Konfigurieren von Minikube für Bereitstellungen von SQL Server-Big Data-Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie **minikube** auf einem einzelnen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Computer für bereit Stellungen konfigurieren. Minikube ist ein Tool, das die Ausführung von Kubernetes auf einem einzelnen Computer wie z.B. einem Laptop oder einem Desktop erleichtert. Minikube wird auf einem Kubernetes-Cluster mit einem einzelnen Knoten innerhalb eines virtuellen Computers ausgeführt, damit Benutzer Kubernetes testen oder alltägliche Entwicklungsaufgaben damit ausführen können. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- 64 GB Arbeitsspeicher.

- Wenn der Computer nur über den mindestens empfohlenen Arbeitsspeicher verfügt, konfigurieren Sie die Clusterbereitstellung mit nur einer Computepoolinstanz, einer Datenpoolinstanz und einer Speicherpoolinstanz. Diese Konfiguration sollte nur für Evaluierungsumgebungen verwendet werden, in denen die Dauerhaftigkeit und die Verfügbarkeit der Daten keine Rolle spielen. Informationen zu den Umgebungsvariablen, die festgelegt werden müssen, um die Anzahl von Replikaten für Daten-, Compute- und Speicherpools zu konfigurieren, finden Sie in der [Bereitstellungsdokumentation](deployment-guidance.md#configfile).

- Die VT-x- oder AMD-v-Virtualisierung muss im BIOS Ihres Computers aktiviert sein.

## <a name="install-dependencies"></a>Installieren von Abhängigkeiten

1. Installieren Sie [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Wenn noch kein Hypervisor installiert ist, installieren Sie jetzt einen.
   - Für OS X installieren Sie [xhyve driver](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads) oder [VMware Fusion](https://www.vmware.com/products/fusion).
   - Für Linux installieren Sie [VirtualBox](https://www.virtualbox.org/wiki/Downloads) oder [KVM](https://www.linux-kvm.org/).
   - Für Windows installieren Sie [VirtualBox](https://www.virtualbox.org/wiki/Downloads) oder [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Wenn Sie keinen externen Switch in Hyper-V konfiguriert haben, erstellen Sie einen, der über externen Netzwerk Zugriff verfügt. Erfahren Sie, wie Sie [einen externen Switch in Hyper-V für minikube erstellen](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Installieren von Minikube

Installieren Sie das minikube-Release gemäß den Anweisungen für die [Version v 1.3.0](https://github.com/kubernetes/minikube/releases/tag/v1.3.0). Der [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] funktioniert nur mit Version Version 1.0.0 und höher.

## <a name="create-a-minikube-cluster"></a>Erstellen eines Minikube-Clusters

Der folgende Befehl erstellt einen minikube-Cluster auf einer Hyper-V-VM mit 8 CPUs, 64 GB Arbeitsspeicher und Datenträger Größe von 100 GB. Die Datenträgergröße ist kein reservierter Speicherplatz.  Sie wird nach Bedarf auf diese Größe auf dem Datenträger erweitert.  Wir empfehlen, den Speicherplatz auf dem Datenträger nicht auf einen Wert unter 100 GB festzulegen, da bei unseren Tests mit niedrigeren Werten Probleme aufgetreten sind. Dadurch wird auch der Hyper-V-Switch mit externem Zugriff explizit angegeben.

Ändern Sie Parameter wie **--memory** nach Bedarf, je nachdem, welche Hardware Ihnen zur Verfügung steht und welchen Hypervisor Sie verwenden.  Stellen Sie sicher, dass der Parameterwert für **--hyper-v-virtual-switch** mit dem Namen übereinstimmt, den Sie beim Erstellen Ihres virtuellen Switches verwendet haben.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 65536 --disk-size 100g --hyperv-virtual-switch "External"
```

Wenn Sie Minikube mit VirtualBox verwenden, sieht der Befehl wie folgt aus:

```base
minikube start --cpus 8 --memory 65536 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Deaktivieren des automatischen Prüfpunkts mit Hyper-V

Unter Windows 10 ist auf virtuellen Computern ein automatischer Prüfpunkt aktiviert. Führen Sie den folgenden Befehl in PowerShell aus, um den automatischen Prüfpunkt auf dem virtuellen Computer zu deaktivieren und Arbeitsspeicher auf statisch festzulegen

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false -StaticMemory
```

## <a name="next-steps"></a>Nächste Schritte

Mit den Schritten in diesem Artikel wurde ein Minikube-Cluster konfiguriert. Der nächste Schritt besteht darin, SQL Server 2019-Big Data-Cluster bereitzustellen. Anweisungen finden Sie im folgenden Artikel:

[Bereit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] stellen auf Kubernetes](deployment-guidance.md#deploy)
