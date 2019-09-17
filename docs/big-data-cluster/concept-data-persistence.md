---
title: Datenpersistenz in Kubernetes
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie die Datenpersistenz in einem SQL Server 2019-Big-Data-Cluster funktioniert.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bb6d87803c0a3839afd8dbd1333b52c3abcc4518
ms.sourcegitcommit: dacf6c57f6a2e3cf2005f3268116f3c609639905
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2019
ms.locfileid: "70878739"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Datenpersistenz mit SQL Server-Big-Data-Clustern in Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Persistente Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) stellen ein Plug-In-Modell zum Speichern in Kubernetes bereit. Die Bereitstellung des Speichers wird von seiner Nutzung abstrahiert. Daher können Sie Ihren eigenen hochverfügbaren Speicher verwenden und in den SQL Server-Big-Data-Cluster einbinden. Dadurch erhalten Sie die vollständige Kontrolle über die Art des Speichers, der Verfügbarkeit und die Leistung, die Sie benötigen. Kubernetes unterstützt verschiedene Arten von Speicherlösungen einschließlich Azure-Datenträger und -Dateien, NFS, lokalen Speicher und mehr.

## <a name="configure-persistent-volumes"></a>Konfigurieren persistenter Volumes

Ein SQL Server-Big-Data-Cluster nutzt diese persistenten Volumes durch die Verwendung von [Speicherklassen](https://kubernetes.io/docs/concepts/storage/storage-classes/). Sie können unterschiedliche Speicherklassen für unterschiedliche Arten des Speicherns erstellen und diese zum Zeitpunkt der Bereitstellung des Big-Data-Clusters angeben. Sie können konfigurieren, welche Speicherklasse und welche Größe für das persistente Volume für welchen Zweck auf der Poolebene verwendet werden sollen. Ein SQL Server-Big-Data-Cluster erstellt [persistente Volumeansprüche](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) mit dem angegebenen Speicherklassennamen für jede Komponente, die persistente Volumes erfordert. Anschließend werden die entsprechenden persistenten Volumes im Pod bereitgestellt. 

## <a name="configure-big-data-cluster-storage-settings"></a>Konfigurieren der Speichereinstellungen für Big-Data-Cluster

Ähnlich wie bei anderen Anpassungen können Sie Speichereinstellungen in den Cluster Konfigurationsdateien zum Zeitpunkt der Bereitstellung für jeden Pool in der Konfigurationsdatei " **BDC. JSON** " und für die Steuerungs Dienste in der Datei " **Control. JSON** " angeben. Wenn in den Pool Spezifikationen keine Speicher Konfigurationseinstellungen vorhanden sind, werden die Steuerungs Speichereinstellungen **für alle anderen Komponenten**, einschließlich SQL Server Master (**Master** -Ressource), HDFS (**Storage-0-** Ressource) oder Daten, verwendet. Spool. Dies ist ein Beispiel für den Speicherkonfigurationsabschnitt, den Sie in die Spezifikation einschließen können:

```json
    "storage": 
    {
      "data": {
        "className": "default",
        "accessMode": "ReadWriteOnce",
        "size": "15Gi"
      },
      "logs": {
        "className": "default",
        "accessMode": "ReadWriteOnce",
        "size": "10Gi"
    }
```

Bei der Bereitstellung von Big-Data-Clustern wird zum Speichern von Daten, Metadaten und Protokollen für verschiedene Komponenten persistenter Speicher verwendet. Sie können die Größe der als Teil der Bereitstellung erstellten persistenten Volumeansprüche anpassen. Es wird empfohlen, die Speicherklassen mit einer *Retain*-[Rückforderungsrichtlinie](https://kubernetes.io/docs/concepts/storage/storage-classes/#reclaim-policy) zu verwenden.

> [!NOTE]
> In CTP 3.2 können Sie die Speicherkonfigurationseinstellungen nach der Bereitstellung nicht mehr ändern. Außerdem wird nur der Zugriffsmodus `ReadWriteOnce` für den gesamten Cluster unterstützt.

> [!WARNING]
> Die Ausführung ohne persistenten Speicher kann zwar in einer Testumgebung funktionieren, führt dann allerdings möglicherweise zu einem nicht funktionsfähigen Cluster. Bei Neustarts des Pods gehen Clustermetadaten und/oder Benutzerdaten dauerhaft verloren. Die Ausführung mit dieser Konfiguration wird nicht empfohlen. 

Im Abschnitt [Konfigurieren von Speicher](#config-samples) finden Sie weitere Beispiele zum Konfigurieren der Speichereinstellungen für die Bereitstellung Ihres SQL Server-Big-Data-Clusters.

## <a name="aks-storage-classes"></a>Azure Kubernetes Service-Speicherklassen

Azure Kubernetes Service (AKS) verfügt über [zwei integrierte Speicherklassen](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) (**Standard** und **managed-premium** (Premiumverwaltung)) und den dynamischen Anbieter für diese Klassen. Sie können eine dieser Klassen angeben oder Ihre eigene Speicherklasse zum Bereitstellen von Big-Data-Clustern mit aktiviertem persistenten Speicher erstellen. Standardmäßig enthält die integrierte Clusterkonfigurationsdatei für aks (*aks-dev-test*) die permanente Speicherkonfigurationen für die Verwendung der Speicherklasse **Standard**.

> [!WARNING]
> Persistente Volumes, die mit den integrierten Speicherklassen **Standard** und **managed-premium** (Premiumverwaltung) erstellt wurden, verfügen über eine *Delete*-Rückforderungsrichtlinie. Wenn Sie also den SQL Server-Big-Data-Cluster löschen, werden persistente Volumeansprüche und dadurch auch persistente Volumes gelöscht. Sie können mithilfe des **azure-disk**-Anbieters benutzerdefinierte Speicherklassen mit einer *Retain*-Rückforderungsrichtlinie erstellen, wie in [diesem](https://docs.microsoft.com/azure/aks/concepts-storage#storage-classes) Artikel gezeigt wird.


## <a name="minikube-storage-class"></a>Minikube-Speicherklasse

Minikube verfügt über eine integrierte Speicherklasse namens **Standard** und den dynamischen Anbieter für diese Klasse. Die integrierte Konfigurationsdatei für Minikube (*minikube-dev-test*) verfügt in der Spezifikation der Steuerungsebene über die Speicherkonfigurationseinstellungen. Die gleichen Einstellungen werden auf alle Poolspezifikationen angewendet. Sie können auch eine Kopie dieser Datei anpassen und für die Bereitstellung Ihres Big-Data-Clusters auf Minikube verwenden. Sie können die benutzerdefinierte Datei manuell bearbeiten und die Größe der persistenten Volumeansprüche für bestimmte Pools ändern, um die Workloads anzupassen, die Sie ausführen möchten. Im Abschnitt [Konfigurieren von Speicher](#config-samples) finden Sie Beispiele für die Bearbeitung mithilfe von *azdata*-Befehlen.

## <a name="kubeadm-storage-classes"></a>Kubeadm-Speicherklassen

Kubeadm verfügt über keine integrierte Speicherklasse. Sie müssen mithilfe des lokalen Speichers und Ihres bevorzugten Anbieters wie [Rook](https://github.com/rook/rook) Ihre eigenen Speicherklassen und persistente Volumes erstellen. In diesem Fall legen Sie den Wert für **className** auf die konfigurierte Speicherklasse fest. 

> [!NOTE]
>  In der integrierten Bereitstellungskonfigurationsdatei für *kubeadm kubeadm-dev-test* ist für die Daten und den Protokollspeicher kein Speicherklassenname angegeben. Vor der Bereitstellung müssen Sie die Konfigurationsdatei anpassen und den Wert für „className“ festlegen, da andernfalls die Validierungen vor der Bereitstellung fehlschlagen. Die Bereitstellung umfasst außerdem einen Validierungsschritt, mit dem überprüft wird, ob die Speicherklasse vorhanden ist. Dabei wird die Existenz der erforderlichen persistenten Volumes nicht überprüft. Sie müssen sicherstellen, dass Sie abhängig von der Skalierung Ihres Clusters ausreichend Volumes erstellen. In CTP 3.1 müssen Sie für die Standardclustergröße mindestens 23 Volumes erstellen. [Hier](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu) finden Sie ein Beispiel für das Erstellen persistenter Volumes mithilfe eines lokalen Anbieters.


## <a name="customize-storage-configurations-for-each-pool"></a>Anpassen der Speicherkonfigurationen für jeden Pool

Für alle Anpassungen müssen Sie zuerst eine Kopie der integrierten Konfigurationsdatei erstellen, die Sie verwenden möchten. Mit dem folgenden Befehl wird beispielsweise eine Kopie der *aks-dev-test*-Bereitstellungskonfigurationsdateien in einem Unterverzeichnis namens `custom` erstellt:

```bash
azdata bdc config init --source aks-dev-test --target custom
```

Dadurch werden zwei Dateien erstellt: " **BDC. JSON** " und " **Control. JSON** ", die angepasst werden können, indem Sie manuell bearbeitet werden, oder Sie können den Befehl " **azdata BDC config** " verwenden. Sie können eine Kombination aus den Bibliotheken „jsonpath“ und „jsonpatch“ verwenden, um Möglichkeiten zum Bearbeiten von Konfigurationsdateien bereitzustellen.


### <a id="config-samples"></a> Konfigurieren von Speicherklassennamen und/oder der Anspruchsgröße

Die Größe der persistenten Volumeansprüche, die für alle im Cluster bereitgestellten Pods bereitgestellt werden, beträgt standardmäßig 10 GB. Sie können diesen Wert aktualisieren, um die in einer benutzerdefinierten Konfigurationsdatei ausgeführten Workloads vor der Clusterbereitstellung anzupassen.

Im folgenden Beispiel wird in der **control.json**-Datei die Anspruchsgröße für persistente Volumes auf 32 Gi aktualisiert. Diese Einstellung wird auf alle Pools angewendet, wenn sie nicht auf Poolebene überschrieben wird:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.size=100Gi"
```

Im folgenden Beispiel wir gezeigt, wie die Speicherklasse für die **control.json**-Datei geändert wird:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.className=<yourStorageClassName>"
```

Eine andere Möglichkeit besteht darin, die benutzerdefinierte Konfigurationsdatei manuell zu bearbeiten oder wie im folgenden Beispiel eine „patch.json“-Datei zu verwenden, die die Speicherklasse für den Speicherpool ändert. Erstellen Sie eine *patch.json*-Datei mit dem folgenden Inhalt:

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.resources.storage-0.spec",
      "value": {
        "type":"Storage",
        "replicas":2,
        "storage":{
            "data":{
                    "size": "100Gi",
                    "className": "myStorageClass",
                    "accessMode":"ReadWriteOnce"
                    },
            "logs":{
                    "size":"32Gi",
                    "className":"myStorageClass",
                    "accessMode":"ReadWriteOnce"
                    }
                }
            }
        }
    ]
}
```

Wenden Sie die Patchdatei an. Verwenden Sie den **azdata bdc config patch**-Befehl, um die Änderungen in der JSON-Patchdatei anzuwenden. Im folgenden Beispiel wird die Datei „patch.json“ auf eine Zielkonfigurationsdatei „custom.json“ für die Bereitstellung angewendet.

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Nächste Schritte

Eine umfassende Dokumentation zu Volumes in Kubernetes finden Sie unter [Kubernetes-Dokumentation zu Volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Weitere Informationen zum Bereitstellen eines SQL Server-Big-Data-Clusters finden Sie unter [How to deploy SQL Server big data cluster on Kubernetes (Bereitstellen von SQL Server-Big-Data-Clustern in Kubernetes)](deployment-guidance.md).

