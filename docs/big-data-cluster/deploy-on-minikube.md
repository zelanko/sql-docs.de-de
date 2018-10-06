---
title: Konfigurieren von Minikube für SQL Server 2019 CTP 2.0-Bereitstellungen | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/05/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 1f20f2adc916a456e4a1975804fac1640ee95f69
ms.sourcegitcommit: 8aecafdaaee615b4cd0a9889f5721b1c7b13e160
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2018
ms.locfileid: "48818048"
---
# <a name="configure-minikube-for-sql-server-2019-ctp-20"></a>Konfigurieren von Minikube für SQL Server 2019 CTP 2.0

Minikube ist ein Tool, das zum Ausführen von Kubernetes auf einem einzelnen Computer wie einem Laptop oder einem Desktop erleichtert. Minikube führt einen Einzelknoten-Kubernetes-Cluster auf einem virtuellen Computer auf Ihrem Laptop für Benutzer, um die Kubernetes ausprobieren oder entwickeln sie mit der täglichen. 

## <a name="prerequisites"></a>Vorraussetzungen

- Um einem Minikube-Cluster für SQL Server 2019 CTP 2.0 in einer Clusterkonfiguration SQL Big Data ausführen zu können, empfiehlt es sich, dass es sich bei Ihrem Computer mindestens 32 GB RAM verfügen.

   > [!TIP] 
   > Wenn der Computer nicht genügend Arbeitsspeicher verfügt, klicken Sie dann die Cluster-Konfiguration so ändern, dass nur 3 Instanzen erstellt werden: compute-Instanz mit einem master und zwei Instanzen.

- VT-X- oder AMD-V-Virtualisierung muss im BIOS des Computers aktiviert werden.

## <a name="install-dependencies"></a>Installieren von Abhängigkeiten

1. Sofern nicht bereits installiert ist, installieren Sie Git auf [Windows](https://git-for-windows.github.io/), [Linux- oder Mac](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

1. Installieren Sie ["kubectl"](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

1. Installieren von Python 3:
   - Wenn Pip nicht vorhanden ist, laden Sie herunter [Get-clspip.py](https://bootstrap.pypa.io/get-pip.py) , und führen Sie `python get-pip.py`.
   - Install-Anforderungen mit `python -m pip install requests`.

1. Wenn Sie nicht bereits einen Hypervisor installiert haben, installieren Sie eine jetzt.
   - Installieren Sie für OS X, [Xhyve-Treiber](https://git.k8s.io/minikube/docs/drivers.md), [VirtualBox](https://www.virtualbox.org/wiki/Downloads), oder [VMware Fusion](https://www.vmware.com/products/fusion).
   - Installieren unter Linux [VirtualBox](https://www.virtualbox.org/wiki/Downloads) oder [KVM](http://www.linux-kvm.org/).
   - Installieren Sie für Windows, [VirtualBox](https://www.virtualbox.org/wiki/Downloads) oder [Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install). Wenn Sie keinen externen Switch in hyper-V konfiguriert haben, erstellen Sie das externe Netzwerk zugreifen kann.  Finden Sie unter Vorgehensweise [Erstellen von externen Switches in hyper-V für Minikube](https://blogs.msdn.microsoft.com/wasimbloch/2017/01/23/setting-up-kubernetes-on-windows10-laptop-with-minikube/).

## <a name="install-minikube"></a>Installieren von Minikube

Installieren von Minikube gemäß den Anweisungen für die [v0.28.2 Version](https://github.com/kubernetes/minikube/releases/tag/v0.28.2). Die SQL Server 2019 CTP 2.0 big Data-Cluster funktioniert nur mit Version v0.24.1 oder höher.

## <a name="create-a-minikube-cluster"></a>Erstellen Sie einen Minikube-cluster

Der folgende Befehl erstellt einen Minikube-Cluster in einem Hyper-V-Computer mit 8 CPUs, 28 GB Arbeitsspeicher und Datenträgergröße von 100 GB an. Die Größe des Datenträgers ist nicht reservierten Speicherplatz.  Es vergrößert wird, um die Größe auf dem Datenträger nach Bedarf.  Es wird empfohlen, ändern den Datenträger nicht weniger als 100 GB Speicherplatz, um etwas wie wir beim Testen Probleme aufgetreten. Hiermit wird auch die hyper-V-Switch mit externem Zugriff explizit.

Ändern Sie die Parameter wie z. B. **– Arbeitsspeicher** Bedarf je nach verfügbarer Hardware und dem Hypervisor, die Sie verwenden.  Stellen Sie sicher, dass die **– hyper-V** virtuellen Switch-Parameter-Wert entspricht dem Namen, die Sie beim Erstellen des virtuellen Switches verwendet.

```bash
minikube start --vm-driver="hyperv" --cpus 8 --memory 28672 --disk-size 100g --hyperv-virtual-switch "External"
```

Bei Verwendung von Minikube mit VirtualBox würde der Befehl wie folgt aussehen:

```base
minikube start --cpus 8 --memory 28672 --disk-size 100g
```

## <a name="disable-automatic-checkpoint-with-hyper-v"></a>Automatische Prüfpunkte mit Hyper-V deaktivieren

Unter Windows 10 ist ein automatischer Prüfpunkt auf einem virtuellen Computer aktiviert. Führen Sie den folgenden Befehl in PowerShell zum Deaktivieren der automatischen Prüfpunkts auf dem virtuellen Computer an.

```PowerShell
Set-VM -Name minikube -CheckpointType Disabled -AutomaticCheckpointsEnabled $false
```

## <a name="next-steps"></a>Nächste Schritte

Die Schritte in diesem Artikel konfiguriert einen Minikube-Cluster. Der nächste Schritt ist für die Bereitstellung von SQL Server 2019 CTP 2.0 auf dem Cluster.

[Bereitstellen von SQL Server 2019 CTP 2.0 auf Kubernetes](deployment-guidance.md#deploy)
