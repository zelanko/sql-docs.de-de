---
title: Dauerhaftigkeit von Daten mit SQL Server, die big Data-in Kubernetes Cluster | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 942442bca18e836c4f8711abc808a89649ff8593
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460575"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Dauerhaftigkeit von Daten mit SQL Server-big Data-Cluster in Kubernetes

[Persistente Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) Geben Sie ein Plug-In-Modell, für Speicher in Kubernetes, wie Speicher bereitgestellt, abgeschlossen abstrahiert, wie es verwendet wird. Aus diesem Grund können Sie bringen Ihren eigenen Speicher mit hoher Verfügbarkeit und binden diese in SQL Server-Cluster für die big Data-Cluster. Dies bietet Ihnen vollständige Kontrolle über den Typ der Speicher, Verfügbarkeit und Leistung, die erforderlich sind. Kubernetes unterstützt verschiedene Arten von speicherlösungen, einschließlich Azure-Datenträger/Dateien, NFS, lokalen Speicher und mehr.

## <a name="configure-persistent-volumes"></a>Konfigurieren von persistenten volumes

Die Möglichkeit, SQL Server-big Data-Cluster diese persistenten Volumes verwendet, ist die Verwendung [Speicherklassen](https://kubernetes.io/docs/concepts/storage/storage-classes/). Sie können unterschiedliche Speicherklassen für unterschiedliche Arten von Speicher zu erstellen, und geben sie zur Bereitstellungszeit big Data-Cluster. Sie können die Speicherklasse zu verwenden, für welche Zwecke (Pool) konfigurieren. SQL Server-big Data-Cluster erstellt [persistentes Volume Ansprüche](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) mit dem angegebenen Speicherkonto Klassennamen für die einzelnen Pods, die persistente Volumes erforderlich sind. Sie bindet dann die entsprechenden persistenten Volumes in den Pod.

> [!NOTE]

> Für CTP 2.0 nur `ReadWriteOnce` den Zugriffsmodus für das gesamte Cluster wird unterstützt.

## <a name="deployment-settings"></a>Bereitstellungseinstellungen

Um persistenten Speicher während der Bereitstellung zu verwenden, konfigurieren die **USE_PERSISTENT_VOLUME** und **STORAGE_CLASS_NAME** Umgebungsvariablen vor der Ausführung `mssqlctl create cluster` Befehl. **USE_PERSISTENT_VOLUME** nastaven NA hodnotu `true` standardmäßig. Sie können die Standardeinstellung überschreiben, und legen Sie ihn auf `false` in diesem Fall SQL Server-big Data-Cluster EmptyDir-Bereitstellungen verwendet. 

> [!WARNING]
> Ohne die dauerhaft ausgeführt, kann in einem nicht funktionierenden Cluster führen. Bei Pod neu gestartet wird verloren Metadaten und/oder Clusterdaten dauerhaft.

Wenn Sie das Flag auf "true" festgelegt haben, müssen Sie auch angeben **STORAGE_CLASS_NAME** als Parameter zur Bereitstellungszeit.

## <a name="aks-storage-classes"></a>AKS-Speicherklassen

Im Lieferumfang von AKS [zwei integrierte Speicherklassen](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) **Standard** und **verwaltete Premium-** zusammen mit der dynamischen Bereitstellung für sie. Sie können geben einen der beiden oder erstellen eigene Speicherklasse für die Bereitstellung von big Data-Cluster mit permanenten Speicher mit Lesezugriff aktiviert.

## <a name="minikube-storage-class"></a>Minikube-Speicherklasse

Minikube ist über eine integrierte-Klasse namens **standard** zusammen mit einer dynamischen Provisioner für sie. Beachten Sie, dass Minikube, wenn USE_PERSISTENT_VOLUME = True (Standard), müssen Sie den Standardwert für die Umgebungsvariable STORAGE_CLASS_NAME auch überschreiben, da der Standardwert unterscheidet. Legen Sie den Wert `standard`: 
```
SET STORAGE_CLASS_NAME=standard
```

Alternativ können Sie die Verwendung von persistenten Volumes auf Minikube unterdrücken:
```
SET USE_PERSISTENT_VOLUME=false
```


## <a name="kubeadm"></a>Kubeadm

Kubeadm kommt nicht mit einer integrierten Speicherklasse; Wir haben daher Skripts zum Einrichten von persistenten Volumes und Storage-Klassen, die Nutzung von lokalem Speicher erstellt oder [Turm](https://github.com/rook/rook) Speicher.

## <a name="on-premises-cluster"></a>Lokalen cluster

Lokale Cluster offensichtlich nicht stammen alle integrierte Klassen, aus diesem Grund müssen Sie einrichten [persistente Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)/[provisioners (Bereitstellungsmethoden)](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/) im voraus, und klicken Sie dann verwenden Sie die entsprechende Speicherklassen während der Clusterbereitstellung für SQL Server-big Data.

# <a name="customize-storage-size-for-each-pool"></a>Anpassen der Speichergröße für jeden pool
Standardmäßig beträgt die Größe des persistenten Volumes bereitgestellt, die für jede der Pods im Cluster bereitgestellten 6 GB. Dies ist konfigurierbar, durch Festlegen der Umgebungsvariablen `STORAGE_SIZE` auf einen anderen Wert. Sie können z. B. Führen Sie folgenden Befehl zum Festlegen des Werts auf 10 GB, vor dem Ausführen der `mssqlctl create cluster command`.

```bash
export STORAGE_SIZE=10Gi
```

Sie können auch unterschiedliche Konfigurationen für die Einstellungen für die dauerhafte Speicherung solcher Speicher Klassen- und persistentes Volume-Größen für andere Pools im Cluster verwenden. Beispielsweise können Sie konfigurieren die persistenten Volumes, die für den Speicherpool verwenden eine andere Speicherklasse und höheren Kapazität durch die Einstellung unter Umgebungsvariablen vor der Bereitstellung des Clusters bereitgestellt:

```bash
export STORAGE_POOL_USE_PERSISTENT_VOLUME=true
export STORAGE_POOL_STORAGE_CLASS_NAME=managed-premium
export STORAGE_POOL_STORAGE_SIZE=100Gi
```

Hier ist eine umfassende Liste der Umgebungsvariablen im Zusammenhang mit der persistenten Speicher für den SQL Server-Big Data-Cluster einrichten:

| Umgebungsvariable | Standardwert | Description |
|---|---|---|
| **USE_PERSISTENT_VOLUME** | true | `true` Persistentes Kubernetes-Volume verwenden Ansprüche für den Pod-Speicher. `false` für die Verwendung kurzlebiger Hostspeicher Pod-Speicher. |
| **STORAGE_CLASS_NAME** | default | Wenn `USE_PERSISTENT_VOLUME` ist `true` Dies gibt den Namen der Kubernetes-Speicher-Klasse verwenden. |
| **STORAGE_SIZE** | 6gi | Wenn `USE_PERSISTENT_VOLUME` ist `true`, dies weist darauf hin, persistentes Volume-Größe für jeden Pod. |
| **DATA_POOL_USE_PERSISTENT_VOLUME** | USE_PERSISTENT_VOLUME | `true` Ansprüche für Pods im Datenpool, persistentes Kubernetes-Volume verwenden. `false` für die Verwendung kurzlebiger Hostspeicher Daten Pool Pods. |
| **DATA_POOL_STORAGE_CLASS_NAME** | STORAGE_CLASS_NAME | Gibt den Namen der Kubernetes-Speicher-Klasse, die für Daten Pool Pods zugeordneten persistenten Volumes verwendet.|
| **DATA_POOL_STORAGE_SIZE** | STORAGE_SIZE |Gibt die Größe der persistenten Volumes für jedem Pod im Datenpool. |
| **STORAGE_POOL_USE_PERSISTENT_VOLUME** | USE_PERSISTENT_VOLUME | `true` Persistentes Kubernetes-Volume verwenden von Ansprüchen für die Pods im Speicherpool. `false` für die Verwendung kurzlebiger Hostspeicher Storage Pool Pods.|
| **STORAGE_POOL_STORAGE_CLASS_NAME** | STORAGE_CLASS_NAME | TIndicates der Namen der Kubernetes-Speicher-Klasse, die für die persistente Volumes verwendet, die Speicher-Pool-Pods zugeordnet ist. |
| **STORAGE_POOL_STORAGE_SIZE** | STORAGE_SIZE | Gibt die Größe der persistenten Volumes für jedem Pod im Speicherpool. |

## <a name="next-steps"></a>Nächste Schritte

Vollständige Dokumentation über Kubernetes-Volumes finden Sie in der [Kubernetes-Dokumentation auf Volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Weitere Informationen zum Bereitstellen von SQL Server-big Data-Cluster finden Sie unter [Gewusst wie: Bereitstellen von SQL Server, big Data-in Kubernetes Cluster](deployment-guidance.md).

