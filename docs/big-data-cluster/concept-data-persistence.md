---
title: Die Datenpersistenz auf Kubernetes
titleSuffix: SQL Server 2019 big data clusters
description: Erfahren Sie mehr über die Funktionsweise der Dauerhaftigkeit von Daten in eine SQL Server-2019 big Data-Cluster.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 47fb255ea18fdf48765a1a40b1e05e06cdf7ee1e
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241741"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Dauerhaftigkeit von Daten mit SQL Server-big Data-Cluster in Kubernetes

[Persistente Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) Geben Sie ein Plug-In-Modell, für Speicher in Kubernetes, wie Speicher bereitgestellt, abgeschlossen abstrahiert, wie es verwendet wird. Aus diesem Grund können Sie bringen Ihren eigenen Speicher mit hoher Verfügbarkeit und binden diese in SQL Server-Cluster für die big Data-Cluster. Dies bietet Ihnen vollständige Kontrolle über den Typ der Speicher, Verfügbarkeit und Leistung, die erforderlich sind. Kubernetes unterstützt verschiedene Arten von speicherlösungen, einschließlich Azure-Datenträger/Dateien, NFS, lokalen Speicher und mehr.

## <a name="configure-persistent-volumes"></a>Konfigurieren von persistenten volumes

Die Möglichkeit, SQL Server-big Data-Cluster diese persistenten Volumes verwendet, ist die Verwendung [Speicherklassen](https://kubernetes.io/docs/concepts/storage/storage-classes/). Sie können unterschiedliche Speicherklassen für unterschiedliche Arten von Speicher zu erstellen, und geben sie zur Bereitstellungszeit big Data-Cluster. Sie können die Speicherklasse zu verwenden, für welche Zwecke (Pool) konfigurieren. SQL Server-big Data-Cluster erstellt [persistentes Volume Ansprüche](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) mit dem angegebenen Speicherkonto Klassennamen für die einzelnen Pods, die persistente Volumes erforderlich sind. Sie bindet dann die entsprechenden persistenten Volumes in den Pod.

> [!NOTE]
> Für die CTP-Version 2.2, nur `ReadWriteOnce` den Zugriffsmodus für das gesamte Cluster wird unterstützt.

## <a name="deployment-settings"></a>Bereitstellungseinstellungen

Um persistenten Speicher während der Bereitstellung zu verwenden, konfigurieren die **USE_PERSISTENT_VOLUME** und **STORAGE_CLASS_NAME** Umgebungsvariablen vor der Ausführung `mssqlctl create cluster` Befehl. **USE_PERSISTENT_VOLUME** nastaven NA hodnotu `true` standardmäßig. Sie können die Standardeinstellung überschreiben, und legen Sie ihn auf `false` in diesem Fall SQL Server-big Data-Cluster EmptyDir-Bereitstellungen verwendet. 

> [!WARNING]
> Ausgeführt wird, ohne den beständigen Speicher benötigen, kann in einer testumgebung arbeiten, aber in einem nicht funktionierenden Cluster resultieren. Bei Pod neu gestartet wird verloren Metadaten und/oder Clusterdaten dauerhaft.

Wenn Sie das Flag auf "true" festgelegt haben, müssen Sie auch angeben **STORAGE_CLASS_NAME** als Parameter zur Bereitstellungszeit.

## <a name="aks-storage-classes"></a>AKS-Speicherklassen

Im Lieferumfang von AKS [zwei integrierte Speicherklassen](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) **Standard** und **verwaltete Premium-** zusammen mit der dynamischen Bereitstellung für sie. Sie können geben einen der beiden oder erstellen eigene Speicherklasse für die Bereitstellung von big Data-Cluster mit permanenten Speicher mit Lesezugriff aktiviert.

## <a name="minikube-storage-class"></a>Minikube-Speicherklasse

Minikube ist über eine integrierte-Klasse namens **standard** zusammen mit einer dynamischen Provisioner für sie. Beachten Sie, dass Minikube, wenn `USE_PERSISTENT_VOLUME=true` (Standard), müssen Sie auch den Standardwert für überschreiben die **STORAGE_CLASS_NAME** Umgebungsvariable, da der Standardwert unterscheidet. Legen Sie den Wert `standard`: 

Verwenden Sie für Windows den folgenden Befehl ein:

```cmd
SET STORAGE_CLASS_NAME=standard
```

Verwenden Sie unter Linux den folgenden Befehl aus:

```cmd
export STORAGE_CLASS_NAME=standard
```

Alternativ können Sie unterdrücken, Verwendung von persistenten Volumes durch Festlegen auf Minikube `USE_PERSISTENT_VOLUME=false`.

## <a name="kubeadm"></a>Kubeadm

Kubeadm kommt nicht mit einer integrierten Speicherklasse. Sie können auch eigene persistente Volumes und Storage-Klassen, die mit lokalem Speicher oder Ihre bevorzugte-Bereitstellung wie erstellen [Turm](https://github.com/rook/rook). In diesem Fall legen Sie die **STORAGE_CLASS_NAME** der Speicherklasse, die Sie konfiguriert haben. Sie können alternativ festlegen `USE_PERSISTENT_VOLUME=false` in testumgebungen, aber beachten Sie die vorherige Warnung in der **bereitstellungseinstellungen** Abschnitt dieses Artikels.  

## <a name="on-premises-cluster"></a>Lokalen cluster

Lokale Cluster offensichtlich nicht stammen alle integrierte Klassen, aus diesem Grund müssen Sie einrichten [persistente Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)/[provisioners (Bereitstellungsmethoden)](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/) im voraus, und klicken Sie dann verwenden Sie die entsprechende Speicherklassen während der Clusterbereitstellung für SQL Server-big Data.

## <a name="customize-storage-size-for-each-pool"></a>Anpassen der Speichergröße für jeden pool
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

Hier ist eine umfassende Liste der Umgebungsvariablen im Zusammenhang mit der das Einrichten permanenter Speicher für die SQL Server-big Data-Cluster:

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

