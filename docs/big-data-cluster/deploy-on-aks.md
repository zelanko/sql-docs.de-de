---
title: Konfigurieren von Azure Kubernetes Service für SQL Server-2019 big Data-Cluster-Bereitstellungen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Azure Kubernetes Service (AKS) für SQL Server-2019 big Data-Cluster (Vorschau)-Bereitstellungen konfigurieren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 07ee0ac0db742eca9a55decfcd78cb76b75e0160
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221656"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-preview-deployments"></a>Konfigurieren von Azure Kubernetes Service für Bereitstellungen von SQL Server-2019 (Vorschau)

Dieser Artikel beschreibt, wie Sie Azure Kubernetes Service (AKS) für SQL Server-2019 big Data-Cluster (Vorschau)-Bereitstellungen konfigurieren. 

ACS vereinfacht das Erstellen, konfigurieren und Verwalten eines Clusters mit virtuellen Computern, die vorkonfiguriert sind mit einem Kubernetes-Cluster zum Ausführen von Anwendungen in Container. Dies können Sie Ihre vorhandenen Kenntnisse nutzen bzw. auf ein umfangreiches und stetig wachsendes Community Fachgebiet tätig und zur Bereitstellung und Verwaltung containerbasierter Anwendungen in Microsoft Azure.

Dieser Artikel beschreibt die Schritte zum Bereitstellen von Kubernetes in AKS mit der Azure CLI. Wenn Sie nicht über ein Azure-Abonnement verfügen, erstellen Sie ein kostenloses Konto, bevor Sie beginnen.

> [!TIP] 
> Ein Beispiel-Python-Skript, das sowohl AKS und SQL Server-big Data-Cluster bereitgestellt wird, finden Sie unter [stellen Sie eine SQL-Server, die big Data-in Azure Kubernetes Service (AKS Cluster)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="prerequisites"></a>Erforderliche Komponenten

- Für eine Umgebung mit AKS für eine optimale Leistung beim Überprüfen von grundlegenden Szenarien empfehlen wir mindestens drei Agent-VMs (zusätzlich zum Master), mit mindestens 4 vCPUs und 32 GB Arbeitsspeicher, die jeder. Azure-Infrastruktur bietet mehrere Optionen für die Größe für virtuelle Computer, finden Sie unter [hier](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes) für die Auswahl in der Region, die Sie bereitstellen möchten.
  
- In diesem Abschnitt erfordert, dass Sie der Azure CLI Version 2.0.4 oder höher. Bei Bedarf installieren oder aktualisieren, finden Sie unter [Installieren der Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli). Führen Sie `az --version` auf die Version zu ermitteln, bei Bedarf.

- Installieren Sie ["kubectl"](https://kubernetes.io/docs/tasks/tools/install-kubectl/) mindestens mit Version 1.10 für Server und Client. Wenn Sie eine bestimmte Version auf "kubectl"-Client installieren möchten, finden Sie unter [Installieren von Kubectl über Curl binäre](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Für AKS, müssen Sie `--kubernetes-version` Parameter, um eine andere als die standardmäßige Version anzugeben.

> [!NOTE]
Beachten Sie, die die Client/Server-Version, Verzerren wird +/-1 Nebenversion unterstützt. Die Kubernetes-Dokumentation gibt an, dass "ein Client Schiefe nicht mehr als eine Nebenversion aus dem Master-muss, aber bis zu einer Nebenversion den Master führen kann. Z. B. v1. 3 Master sollte funktionieren mit v1. 1, v1. 2 und v1. 3-Knoten, und sollte mit Version 1.2, v1. 3 und v1. 4-Clients funktionieren." Weitere Informationen finden Sie unter [Kubernetes unterstützte Versionen und Komponenten, die datenschiefe](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

Beachten Sie außerdem, dass `az aks kubernetes install-cli` Kubectl-Client mit einer Version installiert. senken, die erforderlichen 1.10. Führen Sie die obigen Anweisungen, um die richtige Version der Kubectl-Client zu installieren.

## <a name="create-a-resource-group"></a>Erstellen einer Ressourcengruppe

Eine Azure-Ressourcengruppe ist eine logische Gruppe, in dem, die Azure Ressourcen bereitgestellt und verwaltet werden. Die folgenden Schritte aus, melden Sie sich bei Azure und erstellen eine Ressourcengruppe für den AKS-Cluster.

> [!TIP]
> Wenn Sie Windows verwenden, verwenden Sie PowerShell für den übrigen Schritten.

1. Führen Sie an der Eingabeaufforderung den folgenden Befehl aus, und befolgen Sie die Anweisungen, die Ihrem Azure-Abonnement anzumelden:

    ```bash
    az login
    ```

1. Wenn Sie mehrere Abonnements verfügen, können Sie alle Ihre Abonnements anzeigen, durch den folgenden Befehl ausführen:

   ```bash
   az account list
   ```

1. Wenn Sie in ein anderes Abonnement ändern möchten, können Sie diesen Befehl ausführen:

   ```bash
   az account set --subscription <subscription id>
   ```

1. Erstellen Sie eine Ressourcengruppe mit dem **az-Gruppe erstellen** Befehl. Das folgende Beispiel erstellt eine Ressourcengruppe namens `sqlbigdatagroup` in die `westus2` Speicherort.

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Erstellen Sie einen Kubernetes-cluster

1. Erstellen Sie einen Kubernetes-Cluster in AKS mit den [az Aks erstellen](https://docs.microsoft.com/cli/azure/aks) Befehl. Das folgende Beispiel erstellt einen Kubernetes-Cluster mit dem Namen *Kubcluster* mit einem Linux-Masterknoten und zwei Linux-Agent-Knoten. Stellen Sie sicher, dass den AKS-Cluster in der gleichen Ressourcengruppe zu erstellen, die Sie in den vorherigen Abschnitten verwendet.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_E4s_v3 \
    --node-count 3 \
    --kubernetes-version 1.10.8
    ```

    Sie können erhöhen oder verringern Sie die Anzahl der Standard-Agents durch Ändern der `--node-count <n>` , in denen `<n>` ist die Anzahl von Agent-Knoten, die Sie möchten.

    Nach einigen Minuten ist der Befehl abgeschlossen ist, und gibt Informationen zum Cluster im JSON-Format.

1. Speichern Sie die JSON-Ausgabe aus dem vorherigen Befehl für die spätere Verwendung.

## <a name="connect-to-the-cluster"></a>Verbinden mit dem cluster

1. Um "kubectl" für die Verbindung mit Ihrem Kubernetes-Cluster zu konfigurieren, führen Sie die [az Aks Get-Credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) Befehl. Dieser Schritt lädt der Anmeldeinformationen und der Kubectl-CLI für deren Verwendung konfiguriert.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Verwenden Sie zum Überprüfen der Verbindung mit Ihrem Cluster den [Kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) Befehl, um eine Liste der Clusterknoten.  Das folgende Beispiel zeigt die Ausgabe würden Sie 1 Master und Agent-Knoten 3.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Nächste Schritte

Die Schritte in diesem Artikel konfiguriert einen Kubernetes-Cluster in AKS. Der nächste Schritt ist SQL Server-2019 big Data in den Cluster bereitstellen.

[Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
