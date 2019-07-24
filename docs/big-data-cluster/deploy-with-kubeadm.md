---
title: Konfigurieren von Kubernetes mit kubeadm
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie Kubernetes auf mehreren Ubuntu 16,04-oder 18,04-Computern (physisch oder virtuell) für SQL Server 2019 Big Data Cluster (Vorschau)-bereit Stellungen konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ea79503869e7d403e4d3f4f960de9c95760eda0f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419445"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-big-data-cluster-deployments"></a>Konfigurieren von Kubernetes auf mehreren Computern für SQL Server Big Data Cluster Bereitstellungen

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält ein Beispiel für die Verwendung von **kubeadm** zum Konfigurieren von Kubernetes auf mehreren Computern für bereit Stellungen von SQL Server 2019 Big Data Clustern (Vorschau). In diesem Beispiel sind mehrere Ubuntu 16,04-oder 18,04 LTS-Computer (physisch oder virtuell) das Ziel. Wenn Sie auf einer anderen Linux-Plattform bereitstellen, müssen Sie einige der Befehle so ändern, dass Sie Ihrem System entsprechen.  

> [!TIP] 
> Beispiel Skripts zum Konfigurieren von Kubernetes finden [Sie unter Create a Kubernetes Cluster using kubeadm on Ubuntu 16,04 LTS or 18,04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).

## <a name="prerequisites"></a>Vorraussetzungen

- Mindestens 3 physische Linux-Computer oder virtuelle Computer
- Empfohlene Konfiguration pro Computer:
   - 8 CPUs
   - 64 GB Arbeitsspeicher
   - 100 GB Speicher

## <a name="prepare-the-machines"></a>Vorbereiten der Computer

Auf jedem Computer gibt es mehrere erforderliche Voraussetzungen. Führen Sie in einem bash-Terminal auf jedem Computer die folgenden Befehle aus:

1. Fügen Sie den aktuellen Computer der `/etc/hosts` Datei hinzu:

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Deaktivieren Sie das austauschen auf allen Geräten.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Importieren Sie die Schlüssel, und registrieren Sie das Repository für Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Konfigurieren Sie die Docker-und Kubernetes-Voraussetzungen auf dem Computer.

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Legen Sie `net.bridge.bridge-nf-call-iptables=1` fest. Unter Ubuntu 18,04 aktivieren `br_netfilter`die folgenden Befehle zuerst.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Konfigurieren des Kubernetes-Masters

Nachdem Sie die vorherigen Befehle auf den einzelnen Computern ausgeführt haben, wählen Sie einen der Computer aus, der als Kubernetes Master ausgewählt werden soll. Führen Sie dann die folgenden Befehle auf diesem Computer aus.

1. Erstellen Sie zunächst mit dem folgenden Befehl eine RBAC. YAML-Datei in Ihrem aktuellen Verzeichnis. 

   ```bash
   cat <<EOF > rbac.yaml
   apiVersion: rbac.authorization.k8s.io/v1beta1
   kind: ClusterRoleBinding
   metadata:
     name: default-rbac
   subjects:
   - kind: ServiceAccount
     name: default
     namespace: default
   roleRef:
     kind: ClusterRole
     name: cluster-admin
     apiGroup: rbac.authorization.k8s.io
   EOF
   ```

1. Initialisieren Sie den Kubernetes-Master auf diesem Computer. Die Ausgabe sollte angezeigt werden, dass der Kubernetes Master erfolgreich initialisiert wurde.

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Beachten Sie `kubeadm join` den Befehl, den Sie auf den anderen Servern zum beitreten zum Kubernetes-Cluster verwenden müssen. Kopieren Sie diese zur späteren Verwendung.

   ![kubeadm beitreten](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Richten Sie eine Kubernetes-Konfigurationsdatei als Basisverzeichnis ein.

   ```bash
   mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
   ```

1. Konfigurieren Sie den Cluster und das Kubernetes-Dashboard.

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
   helm init
   kubectl apply -f rbac.yaml
   kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
   kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
   ```

## <a name="configure-the-kubernetes-agents"></a>Konfigurieren der Kubernetes-Agents

Die anderen Computer fungieren als Kubernetes-Agents im Cluster. 

Führen Sie auf allen anderen Computern den Befehl aus `kubeadm join` , den Sie im vorherigen Abschnitt kopiert haben.

![kubeadm-Join-Agents](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Anzeigen des Cluster Status

Um die Verbindung mit Ihrem Cluster zu überprüfen, verwenden Sie den Befehl [kubectl Get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) , um eine Liste der Cluster Knoten zurückzugeben.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Nächste Schritte

Mit den Schritten in diesem Artikel wurde ein Kubernetes-Cluster auf mehreren Ubuntu-Computern konfiguriert. Der nächste Schritt besteht darin, SQL Server 2019 Big Data Cluster bereitzustellen. Anweisungen finden Sie im folgenden Artikel:

[Bereitstellen von SQL Server auf Kubernetes](deployment-guidance.md#deploy)
