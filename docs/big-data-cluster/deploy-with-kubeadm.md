---
title: Konfigurieren von Kubernetes mit kubeadm
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie Kubernetes in mehrere Ubuntu 16.04 oder 18.04 Computer (physisch oder virtuell) für SQL Server-2019 big Data-Cluster (Vorschau)-Bereitstellungen konfigurieren.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: c48a8a8ad84a1378eed09727a3e51a51252b88c6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803067"
---
# <a name="configure-kubernetes-on-multiple-machines-for-sql-server-big-data-cluster-deployments"></a>Konfigurieren von Kubernetes auf mehrere Computer für SQL Server-big Data-Cluster-Bereitstellungen

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält ein Beispiel zur Verwendung **Kubeadm** Kubernetes auf mehrere Computer für SQL Server-2019 big Data-Cluster (Vorschau)-Bereitstellungen zu konfigurieren. In diesem Beispiel werden mehrere Ubuntu 16.04 oder 18.04 LTS-Computer (physisch oder virtuell) das Ziel. Wenn Sie auf eine andere Linux-Plattform bereitstellen, müssen Sie einige der Befehle entsprechend Ihrem System ändern.  

> [!TIP] 
> Beispielskripts, die Kubernetes konfigurieren, finden Sie unter [erstellen Sie einen Kubernetes-Cluster mithilfe von Kubeadm unter Ubuntu 16.04 LTS oder 18.04 LTS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Mindestens 3 Linux-Computer – physische oder virtuelle Computer
- Empfohlene Konfiguration pro Computer:
   - 8 CPUs
   - 32 GB Arbeitsspeicher
   - 100 GB Speicher

## <a name="prepare-the-machines"></a>Vorbereiten der Computer

Es gibt einige Voraussetzungen, auf jedem Computer. Führen Sie in einer Bash-Terminal die folgenden Befehle auf jedem Computer aus:

1. Fügen Sie den aktuellen Computer aus, um die `/etc/hosts` Datei:

   ```bash
   echo $(hostname -i) $(hostname) | sudo tee -a /etc/hosts
   ```

1. Deaktivieren Sie die Auslagerung auf allen Geräten.

   ```bash
   sudo sed -i "/ swap / s/^/#/" /etc/fstab
   sudo swapoff -a
   ```

1. Importieren Sie die Schlüssel, und registrieren Sie sich das Repository für Kubernetes.

   ```bash
   sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
   echo 'deb http://apt.kubernetes.io/ kubernetes-xenial main' | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
   ```

1. Konfigurieren Sie Docker und Kubernetes Voraussetzungen auf dem Computer an.

   ```bash
   KUBE_DPKG_VERSION=1.11.3-00
   sudo apt-get update && /
   sudo apt-get install -y ebtables ethtool && /
   sudo apt-get install -y docker.io && /
   sudo apt-get install -y apt-transport-https && /
   sudo apt-get install -y kubelet=$KUBE_DPKG_VERSION kubeadm=$KUBE_DPKG_VERSION kubectl=$KUBE_DPKG_VERSION && /
   curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get | bash
   ```
 
1. Legen Sie `net.bridge.bridge-nf-call-iptables=1` fest. Für Ubuntu 18.04, die folgenden Befehle zuerst aktivieren `br_netfilter`.

   ```bash
   . /etc/os-release
   if [ "$VERSION_CODENAME" == "bionic" ]; then sudo modprobe br_netfilter; fi
   sudo sysctl net.bridge.bridge-nf-call-iptables=1
   ```

## <a name="configure-the-kubernetes-master"></a>Konfigurieren des Kubernetes-Masters

Wählen Sie nach dem Ausführen der zuvor eingegebenen Befehle auf jedem Computer, einem der Computer Ihrem Kubernetes-Master zu sein. Führen Sie die folgenden Befehle auf dem Computer.

1. Erstellen Sie zunächst eine rbac.yaml-Datei in Ihrem aktuellen Verzeichnis mit dem folgenden Befehl ein. 

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

1. Den Kubernetes-Master auf diesem Computer zu initialisieren. Ausgabe wird angezeigt, dass der Kubernetes-Master wurde erfolgreich initialisiert wurde.

   ```bash
   KUBE_VERSION=1.11.3
   sudo kubeadm init --pod-network-cidr=10.244.0.0/16 --kubernetes-version=$KUBE_VERSION
   ```

1. Beachten Sie die `kubeadm join` Befehl, mit dem Sie auf die anderen Server verwenden, um den Kubernetes-Cluster verknüpfen möchten. Kopieren Sie diese für die spätere Verwendung.

   ![Kubeadm join](./media/deploy-with-kubeadm/kubeadm-join.png)

1. Richten Sie einen Kubernetes-Konfigurationsdatei Basisverzeichnis ein.

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

## <a name="configure-the-kubernetes-agents"></a>Konfigurieren Sie die Kubernetes-agents

Die anderen Computer fungiert als Kubernetes-Agents im Cluster. 

Führen Sie auf allen Computern auf, die `kubeadm join` -Befehl, der Sie im vorherigen Abschnitt kopiert haben.

![Kubeadm Join-agents](./media/deploy-with-kubeadm/kubeadm-join-agents.png)

## <a name="view-the-cluster-status"></a>Zeigen Sie den Status des Clusters

Verwenden Sie zum Überprüfen der Verbindung mit Ihrem Cluster den [Kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) Befehl, um eine Liste der Clusterknoten.

```bash
kubectl get nodes
```

## <a name="next-steps"></a>Nächste Schritte

Die Schritte in diesem Artikel werden einen Kubernetes-Cluster auf mehrere Ubuntu-Computer konfiguriert. Der nächste Schritt ist SQL Server-2019 big Data-Cluster bereitstellen. Anweisungen hierzu finden Sie unter den folgenden Artikel:

[Bereitstellen von SQLServer in Kubernetes](deployment-guidance.md#deploy)
