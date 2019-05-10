---
title: GPU-Unterstützung und TensorFlow
titleSuffix: SQL Server big data clusters
description: Bereitstellen eines big Data-Clusters mit GPU-Unterstützung und TensorFlow in Azure Data Studio Notebooks verwenden.
author: inchiosa
ms.author: marinch
ms.reviewer: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2d31736ee4dd68857e3afce678b6dd806701a82b
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774952"
---
# <a name="deploy-a-big-data-cluster-with-gpu-support-and-run-tensorflow"></a>Bereitstellen eines big Data-Clusters mit GPU-Unterstützung, und führen Sie TensorFlow

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird veranschaulicht, wie einen big Data-Cluster in Azure Kubernetes Service (AKS) bereitstellen, die GPU-fähiger knotenpools für rechenintensive Workloads unterstützt wird. Anschließend führen Sie die Beispiel-Notebooks in Azure Data Studio, die bildklassifizierung mit TensorFlow für GPU ausgeführt wird.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Big Data-Tools](deploy-big-data-tools.md):
  - **mssqlctl**
  - **kubectl**
  - **Azure Data Studio**
  - **SQL Server-2019-Erweiterung**
  - **Azure-Befehlszeilenschnittstelle**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="create-an-aks-cluster"></a>Erstellen eines AKS-Clusters

Die folgenden Schritte können, dass der Azure-Befehlszeilenschnittstelle um einen AKS-Cluster zu erstellen, der GPUs unterstützt.

1. Führen Sie an der Eingabeaufforderung den folgenden Befehl aus, und befolgen Sie die Anweisungen für die Anmeldung bei Ihrem Azure-Abonnement:

    ```azurecli
    az login
    ```

1. Erstellen Sie eine Ressourcengruppe mit dem **az-Gruppe erstellen** Befehl. Das folgende Beispiel erstellt eine Ressourcengruppe namens `sqlbigdatagroupgpu` in die `eastus` Speicherort.

   ```azurecli
   az group create --name sqlbigdatagroupgpu --location eastus
   ```

1. Erstellen Sie einen Kubernetes-Cluster in AKS mit den [az Aks erstellen](https://docs.microsoft.com/cli/azure/aks) Befehl. Das folgende Beispiel erstellt einen Kubernetes-Cluster mit dem Namen `gpucluster` in die `sqlbigdatagroupgpu` Ressourcengruppe aus.

   ```azurecli
   az aks create --name gpucluster --resource-group sqlbigdatagroupgpu --generate-ssh-keys --node-vm-size Standard_NC6s_v3 --node-count 3 --node-osdisk-size 50 --kubernetes-version 1.11.9 --location eastus
   ```

   > [!NOTE]
   > Dieser Cluster verwendet die **Standard_NC6s_v3** [-GPU-optimierte VM-Größe](https://docs.microsoft.com/azure/virtual-machines/linux/sizes-gpu), d. h. einen speziellen virtuellen Computer mit einer oder mehreren NVIDIA-GPUs verfügbar. Weitere Informationen finden Sie unter [Verwenden von GPUs für rechenintensive Workloads in Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/gpu-cluster).

1. Um "kubectl" für die Verbindung mit Ihrem Kubernetes-Cluster zu konfigurieren, führen Sie die [az Aks Get-Credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) Befehl.

   ```azurecli
   az aks get-credentials --overwrite-existing --resource-group=sqlbigdatagroupgpu --name gpucluster
   ```

## <a name="apply-yaml-manifest"></a>Anwenden von YAML-manifest

1. Verwendung **"kubectl"** zum Erstellen eines Kubernetes-Namespace mit dem Namen `gpu-resources`.

   ```bash
   kubectl create namespace gpu-resources
   ```

1. Speichern Sie den Inhalt der folgenden YAML-Datei in eine Datei namens **Nvidia-Gerät--Plug-in-ds.yaml**. Speichern Sie diese in das Arbeitsverzeichnis auf Ihrem Computer, die Sie ausführen **"kubectl"** aus.

   Update der `image: nvidia/k8s-device-plugin:1.11` halb Sie das Manifest Kubernetes-Version entsprechen. Z. B. wenn es sich bei Ihrem AKS-Cluster mit Kubernetes-Version 1.12 ausgeführt wird, aktualisieren Sie das Tag, `image: nvidia/k8s-device-plugin:1.12`.

   ```yaml
   apiVersion: extensions/v1beta1
   kind: DaemonSet
   metadata:
     labels:
       kubernetes.io/cluster-service: "true"
     name: nvidia-device-plugin
     namespace: gpu-resources
   spec:
     template:
       metadata:
         # Mark this pod as a critical add-on; when enabled, the critical add-on scheduler
         # reserves resources for critical add-on pods so that they can be rescheduled after
         # a failure.  This annotation works in tandem with the toleration below.
         annotations:
           scheduler.alpha.kubernetes.io/critical-pod: ""
         labels:
           name: nvidia-device-plugin-ds
       spec:
         tolerations:
         # Allow this pod to be rescheduled while the node is in "critical add-ons only" mode.
         # This, along with the annotation above marks this pod as a critical add-on.
         - key: CriticalAddonsOnly
           operator: Exists
         containers:
         - image: nvidia/k8s-device-plugin:1.11 # Update this tag to match your Kubernetes version
           name: nvidia-device-plugin-ctr
           securityContext:
             allowPrivilegeEscalation: false
             capabilities:
               drop: ["ALL"]
           volumeMounts:
             - name: device-plugin
               mountPath: /var/lib/kubelet/device-plugins
         volumes:
           - name: device-plugin
             hostPath:
               path: /var/lib/kubelet/device-plugins
         nodeSelector:
           beta.kubernetes.io/os: linux
           accelerator: nvidia
   ```

1. Verwenden der "kubectl" gelten Befehl aus, um das DaemonSet zu erstellen. **NVIDIA-Gerät--Plug-in-ds.yaml** im Arbeitsverzeichnis werden muss, wenn Sie den folgenden Befehl ausführen:

   ```bash
   kubectl apply -f nvidia-device-plugin-ds.yaml
   ```

## <a name="deploy-the-big-data-cluster"></a>Die big Data-Cluster bereitstellen

Um eine SQL Server-2019 big Data-Cluster (Vorschau) bereitstellen, der GPUs unterstützt, müssen Sie von einem bestimmten Docker-Registrierung und das Repository bereitstellen. Die folgenden Umgebungsvariablen unterscheiden sich für eine GPU-Bereitstellung:

| Umgebungsvariable | Wert |
|---|---|
| **DOCKER_REGISTRY** | `marinchcreus3.azurecr.io` |
| **DOCKER_REPOSITORY** | `ctp25-8-0-61-gpu` |
| **DOCKER_USERNAME** | `<your username, gpu-specific credentials provided by Microsoft>` |
| **DOCKER_PASSWORD** | `<your password, gpu-specific credentials provided by Microsoft>` |

Verwendung **Mssqlctl** zum Bereitstellen der Cluster, wählen Sie die Konfiguration des Aks-Dev-test.json und bereitstellen, die die benutzerdefinierten Werte oben, wenn Sie aufgefordert werden.

```bash
mssqlctl cluster create
```

> [!TIP]
> Der Standardname der big Data-Cluster ist `mssql-cluster`.

Sie können auch Ihre Bereitstellung weiter anpassen, durch eine benutzerdefinierte Bereitstellungskonfigurationsdatei übergeben. Weitere Informationen finden Sie unter den [bereitstellungsanleitung](deployment-guidance.md#customconfig).

## <a name="run-the-tensorflow-example"></a>Führen Sie das TensorFlow-Beispiel

Die folgenden zwei beispielnotebooks veranschaulichen Training zwei Modellen zur bildklassifizierung auf einem einzelnen Knoten des Spark-Clusters mit TensorFlow für GPU.

| Notebook-download | Description |
|---|---|
| [**tf-cuda8.ipynb**](https://aka.ms/AA4jdgd) | Wird verwendet, die CUDA 8 und CUDNN 6 TensorFlow 1.4.0.  |
| [**tf-cuda9.ipynb**](https://aka.ms/AA4ixzr) | Wird verwendet, die CUDA 9 und CUDNN 7 TensorFlow 1.12.0. |

Legen Sie die entsprechenden Notebook-Datei auf Ihrem lokalen Computer, und klicken Sie dann öffnen Sie, und führen Sie es in Azure Data Studio PySpark3-Kernel verwenden. Wählen Sie CUDA 9/CUDNN 7/TensorFlow 1.12.0, es sei denn, Sie haben eine ältere Version von CUDA oder TensorFlow benötigen. Weitere Informationen zur Verwendung von Notebooks mit big Data-Clustern finden Sie unter [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md).

> [!NOTE]
> Beachten Sie, dass die Notebooks-Software in Speicherorte im Dateisystem installiert. Dies ist möglich, da die Notebooks mit Stammberechtigungen im CTP-Version 2.5 derzeit ausgeführt werden.

Nach der Installation von NVIDIA-GPU-Bibliotheken und TensorFlow für GPU, Liste der Notebooks GPU-Geräte zur Verfügung stehen. Klicken sie dann anpassen und bewerten ein TensorFlow-Modells zur Erkennung von handgeschriebener Ziffern, die mit dem MNIST-DataSet. Nach der Überprüfung freier Speicherplatz verfügbar, sie herunterladen, und führen Sie das CIFAR-10-Image Classification-Beispiel aus [ https://github.com/tensorflow/models.git ](https://github.com/tensorflow/models.git). Durch das CIFAR-10-Beispiel in Clustern mit verschiedenen GPUs ausführen, können Sie beobachten, die Erhöhung der Geschwindigkeit von für jede Generation von GPU in Azure verfügbaren angeboten.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Um die big Data-Cluster zu löschen, verwenden Sie den folgenden Befehl aus:

```bash
mssqlctl cluster delete --name gpubigdatacluster
```

Der vorherige Befehl wird den AKS-Cluster nicht entfernt werden. Um die AKS-Cluster und die zugeordneten Ressourcen zu löschen, verwenden Sie den folgenden Befehl aus:

```azurecli
az group delete -n sqlbigdatagroupgpu
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-2019 big Data-Clustern (Vorschau), finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
