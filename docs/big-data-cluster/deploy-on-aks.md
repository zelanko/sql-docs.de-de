---
title: Konfigurieren von Azure Kubernetes Service für SQL Server 2019 CTP 2.0-Bereitstellungen | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: ea1ab30f9b3b8ef77834a56b059b2a56de4467b5
ms.sourcegitcommit: 448106b618fe243e418bbfc3daae7aee8d8553d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48796760"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-ctp-20"></a>Konfigurieren von Azure Kubernetes-Dienst für SQL Server 2019 CTP 2.0

Azure Kubernetes Service (AKS) vereinfacht das Erstellen, konfigurieren und Verwalten eines Clusters mit virtuellen Computern, die vorkonfiguriert sind mit einem Kubernetes-Cluster zum Ausführen von Anwendungen in Container. 

Dies können Sie Ihre vorhandenen Kenntnisse nutzen bzw. auf ein umfangreiches und stetig wachsendes Community Fachgebiet tätig und zur Bereitstellung und Verwaltung containerbasierter Anwendungen in Microsoft Azure.

Dieser Artikel beschreibt die Schritte zum Bereitstellen von Kubernetes in AKS mit der Azure CLI. Wenn Sie nicht über ein Azure-Abonnement verfügen, erstellen Sie ein kostenloses Konto, bevor Sie beginnen.

## <a name="prerequisites"></a>Vorraussetzungen

- Für eine Umgebung mit AKS ist die Mindestanforderungen des virtuellen Computers mindestens zwei Agent-VMs (zusätzlich zum Master) der Mindestgröße Standard_DS3_V2. Pro virtuellem Computer erforderliche Mindestressourcen sind 4 CPUs und 14 GB Arbeitsspeicher.

- In diesem Abschnitt erfordert, dass Sie der Azure CLI Version 2.0.4 oder höher. Bei Bedarf installieren oder aktualisieren, finden Sie unter [Installieren der Azure CLI 2.0](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli). Führen Sie `az --version` auf die Version zu ermitteln, bei Bedarf.

- Installieren Sie ["kubectl"](https://kubernetes.io/docs/tasks/tools/install-kubectl/). SQL Server-Big Data-Cluster erfordert, dass alle Nebenversionen im 1,10 Versionsbereich für Kubernetes, für Server und Client. Um eine bestimmte Version auf Kubectl-Client installieren zu können, finden Sie unter [Installieren von Kubectl über Curl binäre](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Müssen Sie für AKS verwenden `--kubernetes-version` -Parameter eine anderen Version als Standard fest. Beachten Sie, dass nach im Zeitrahmen CTP2. 0-Version, AKS nur 1.10.7 und 1.10.8-Versionen unterstützt. 


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
    --node-vm-size Standard_DS3_v2 \
    --node-count 2 \
    --kubernetes-version 1.10.7
    ```

    Sie können erhöhen oder verringern Sie die Anzahl der Standard-Agents durch Hinzufügen `--node-count <n>` auf die az Aks create-Befehl, in denen `<n>` ist die Anzahl von Agent-Knoten, die Sie möchten.

    Nach einigen Minuten ist der Befehl abgeschlossen ist, und gibt Informationen zum Cluster im JSON-Format.

1. Speichern Sie die JSON-Ausgabe aus dem vorherigen Befehl für die spätere Verwendung.

## <a name="connect-to-the-cluster"></a>Verbinden mit dem cluster

1. Um "kubectl" für die Verbindung mit Ihrem Kubernetes-Cluster zu konfigurieren, führen Sie die [az Aks Get-Credentials](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) Befehl. Dieser Schritt lädt der Anmeldeinformationen und der Kubectl-CLI für deren Verwendung konfiguriert.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Verwenden Sie zum Überprüfen der Verbindung mit Ihrem Cluster den [Kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) Befehl, um eine Liste der Clusterknoten.  Das folgende Beispiel zeigt die Ausgabe würden Sie 1 Master und Agent-Knoten 3.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Nächste Schritte

Die Schritte in diesem Artikel konfiguriert einen Kubernetes-Cluster in AKS. Der nächste Schritt ist SQL Server 2019 Big Data in den Cluster bereitstellen.

[Bereitstellen von SQL Server 2019 Big Data-Cluster in Kubernetes](quickstart-big-data-cluster-deploy.md)
