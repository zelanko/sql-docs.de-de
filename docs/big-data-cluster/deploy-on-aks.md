---
title: Konfigurieren von Azure Kubernetes Service
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie Azure Kubernetes Service (AKS) für SQL Server-2019 big Data-Cluster (Vorschau)-Bereitstellungen konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 07/10/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 872988b29cddc202ea2c0f199548bc28b946b918
ms.sourcegitcommit: e366f702c49d184df15a9b93c2c6a610e88fa0fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826522"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-big-data-cluster-deployments"></a>Konfigurieren von Azure Kubernetes Service für SQL Server-big Data-Cluster-Bereitstellungen

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt, wie Sie Azure Kubernetes Service (AKS) für SQL Server-2019 big Data-Cluster (Vorschau)-Bereitstellungen konfigurieren.

ACS vereinfacht das Erstellen, konfigurieren und Verwalten eines Clusters mit virtuellen Computern, die vorkonfiguriert sind mit einem Kubernetes-Cluster zum Ausführen von Anwendungen in Container. Dies können Sie Ihre vorhandenen Kenntnisse nutzen bzw. auf ein umfangreiches und stetig wachsendes Community Fachgebiet tätig und zur Bereitstellung und Verwaltung containerbasierter Anwendungen in Microsoft Azure.

Dieser Artikel beschreibt die Schritte zum Bereitstellen von Kubernetes in AKS mit der Azure CLI. Wenn Sie nicht über ein Azure-Abonnement verfügen, erstellen Sie ein kostenloses Konto, bevor Sie beginnen.

> [!TIP] 
> Ein Beispiel-Python-Skript, das sowohl AKS und SQL Server-big Data-Cluster bereitgestellt wird, finden Sie unter [Schnellstart: Bereitstellen von SQL Server, die big Data-in Azure Kubernetes Service (AKS Cluster)](quickstart-big-data-cluster-deploy.md).

## <a name="prerequisites"></a>Vorraussetzungen

- [Bereitstellen der SQL Server-2019 big Data-Tools](deploy-big-data-tools.md):
   - **Kubectl**
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
   - **Azure-Befehlszeilenschnittstelle**

- 1\.10 Mindestversion für Kubernetes-Server. Für AKS, müssen Sie `--kubernetes-version` Parameter, um eine andere als die standardmäßige Version anzugeben.

- Für eine optimale Leistung bei der Überprüfung des grundlegenden Szenarien in AKS zu verwenden:
   - 8 vCPUs in allen Knoten
   - 32 GB Arbeitsspeicher pro virtuellem Computer
   - 24 oder mehr angefügten Datenträger auf allen Knoten

   > [!TIP]
   > Azure-Infrastruktur bietet mehrere Optionen für die Größe für virtuelle Computer, finden Sie unter [hier](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) für die Auswahl in der Region, die Sie bereitstellen möchten.

## <a name="create-a-resource-group"></a>Erstellen einer Ressourcengruppe

Eine Azure-Ressourcengruppe ist eine logische Gruppe, in dem, die Azure Ressourcen bereitgestellt und verwaltet werden. Die folgenden Schritte aus, melden Sie sich bei Azure und erstellen eine Ressourcengruppe für den AKS-Cluster.

1. Führen Sie an der Eingabeaufforderung den folgenden Befehl aus, und befolgen Sie die Anweisungen, die Ihrem Azure-Abonnement anzumelden:

    ```azurecli
    az login
    ```

1. Wenn Sie mehrere Abonnements verfügen, können Sie alle Ihre Abonnements anzeigen, durch den folgenden Befehl ausführen:

   ```azurecli
   az account list
   ```

1. Wenn Sie in ein anderes Abonnement ändern möchten, können Sie diesen Befehl ausführen:

   ```azurecli
   az account set --subscription <subscription id>
   ```

1. Erstellen Sie eine Ressourcengruppe mit dem **az-Gruppe erstellen** Befehl. Das folgende Beispiel erstellt eine Ressourcengruppe namens `sqlbdcgroup` in die `westus2` Speicherort.

   ```azurecli
   az group create --name sqlbdcgroup --location westus2
   ```

## <a name="verify-available-kubernetes-versions"></a>Überprüfen Sie die verfügbare Kubernetes-Versionen

Verwenden Sie die neueste verfügbare Version von Kubernetes. Die neueste verfügbare Version hängt von den Speicherort der Bereitstellung des Clusters ab. Der folgende Befehl gibt Kubernetes-Versionen verfügbar an einem bestimmten Ort zurück.

Bevor Sie den Befehl ausführen, aktualisieren Sie das Skript. Ersetzen Sie dies `<Azure data center>` durch den Speicherort Ihres Clusters.

   **bash**

   ```bash
   az aks get-versions \
   --location <Azure data center> \
   --query orchestrators \
   --o table
   ```

   **PowerShell**

   ```powershell
   az aks get-versions `
   --location <Azure data center> `
   --query orchestrators `
   --o table
   ```

Wählen Sie die neueste verfügbare Version für Ihren Cluster. Notieren Sie die Versionsnummer. Sie werden im nächsten Schritt verwendet.

## <a name="create-a-kubernetes-cluster"></a>Erstellen Sie einen Kubernetes-cluster

1. Erstellen Sie einen Kubernetes-Cluster in AKS mit den [az Aks erstellen](https://docs.microsoft.com/cli/azure/aks) Befehl. Das folgende Beispiel erstellt einen Kubernetes-Cluster mit dem Namen *Kubcluster* mit einem Linux-Agent-Knoten der Größe **Standard_L8s**.

   Ersetzen Sie vor dem Ausführen des Skripts `<version number>` mit der Versionsnummer, die Sie in den vorherigen Schritt identifiziert haben.

   Stellen Sie sicher, dass den AKS-Cluster in der gleichen Ressourcengruppe zu erstellen, die Sie in den vorherigen Abschnitten verwendet.

   **bash:**

   ```bash
   az aks create --name kubcluster \
   --resource-group sqlbdcgroup \
   --generate-ssh-keys \
   --node-vm-size Standard_L8s \
   --node-count 1 \
   --kubernetes-version <version number>
   ```

   **PowerShell:**

   ```powershell
   az aks create --name kubcluster `
   --resource-group sqlbdcgroup `
   --generate-ssh-keys `
   --node-vm-size Standard_L8s `
   --node-count 1 `
   --kubernetes-version <version number>
   ```

   Sie können erhöhen oder verringern Sie die Anzahl von Kubernetes-Agent-Knoten durch Ändern der `--node-count <n>` , in denen `<n>` ist die Anzahl von Agent-Knoten, die Sie verwenden möchten. Dies schließt nicht den Hauptschlüssel Kubernetes-Knoten, der hinter den Kulissen von AKS verwaltet wird. Im vorherige Beispiel verwendet einen einzelnen Knoten nur für Evaluierungszwecke.

   Nach einigen Minuten ist der Befehl abgeschlossen ist, und gibt Informationen zum Cluster im JSON-Format.

   > [!TIP]
   > Wenn Sie alle Fehler, die Erstellung des Clusters in AKS erhalten, finden Sie unter den [Abschnitt zur Problembehandlung](#troubleshoot) dieses Artikels.

1. Speichern Sie die JSON-Ausgabe aus dem vorherigen Befehl für die spätere Verwendung.

## <a name="connect-to-the-cluster"></a>Verbinden mit dem cluster

1. Um "kubectl" für die Verbindung mit Ihrem Kubernetes-Cluster zu konfigurieren, führen Sie die [az Aks Get-Credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) Befehl. Dieser Schritt lädt der Anmeldeinformationen und der Kubectl-CLI für deren Verwendung konfiguriert.

   ```azurecli
   az aks get-credentials --resource-group=sqlbdcgroup --name kubcluster
   ```

1. Verwenden Sie zum Überprüfen der Verbindung mit Ihrem Cluster den [Kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) Befehl, um eine Liste der Clusterknoten.  Das folgende Beispiel zeigt die Ausgabe würden Sie 1 Master und Agent-Knoten 3.

   ```bash
   kubectl get nodes
   ```

## <a id="troubleshoot"></a> Problembehandlung

Wenn Sie Probleme beim Erstellen von Azure Kubernetes Service mit den vorherigen Befehlen haben, probieren Sie die folgenden Lösungen:

- Stellen Sie sicher, dass es sich bei der Installation der [neueste Azure-Befehlszeilenschnittstelle](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest).
- Versuchen Sie es die gleichen Schritte, die über einen anderen Ressourcennamen und den Clusternamen.

## <a name="next-steps"></a>Nächste Schritte

Die Schritte in diesem Artikel konfiguriert einen Kubernetes-Cluster in AKS. Der nächste Schritt ist einen SQL Server-2019 big Data-Cluster auf dem ACS-Kubernetes-Cluster bereitstellen. Weitere Informationen dazu, wie Sie big Data-Cluster bereitstellen finden Sie im folgenden Artikel:

[Wie Sie SQL Server-big Data-Cluster in Kubernetes bereitstellen](deployment-guidance.md)
