---
title: Datenpersistenz in Kubernetes
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie die Datenpersistenz in einem SQL Server 2019-Big-Data-Cluster funktioniert.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 87f0e82d0e12656bb7a06be1951874b656dbf4b0
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532390"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Datenpersistenz mit SQL Server-Big-Data-Clustern in Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Persistente Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) stellen ein Plug-In-Modell zum Speichern in Kubernetes bereit. Die Bereitstellung des Speichers wird von seiner Nutzung abstrahiert. Daher können Sie Ihren eigenen hochverfügbaren Speicher verwenden und in den SQL Server-Big-Data-Cluster einbinden. Dadurch erhalten Sie die vollständige Kontrolle über die Art des Speichers, der Verfügbarkeit und die Leistung, die Sie benötigen. Kubernetes unterstützt verschiedene Arten von Speicherlösungen einschließlich Azure-Datenträger und -Dateien, NFS, lokalen Speicher und mehr.

## <a name="configure-persistent-volumes"></a>Konfigurieren persistenter Volumes

Ein SQL Server-Big-Data-Cluster nutzt diese persistenten Volumes durch die Verwendung von [Speicherklassen](https://kubernetes.io/docs/concepts/storage/storage-classes/). Sie können unterschiedliche Speicherklassen für unterschiedliche Arten des Speicherns erstellen und diese zum Zeitpunkt der Bereitstellung des Big-Data-Clusters angeben. Sie können konfigurieren, welche Speicherklasse und welche Größe für das persistente Volume für welchen Zweck auf der Poolebene verwendet werden sollen. Ein SQL Server-Big-Data-Cluster erstellt [persistente Volumeansprüche](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) mit dem angegebenen Speicherklassennamen für jede Komponente, die persistente Volumes erfordert. Anschließend werden die entsprechenden persistenten Volumes im Pod bereitgestellt. 

Im Folgenden sind einige wichtige Aspekte aufgeführt, die beim Planen der Speicherkonfiguration für einen Big Data-Cluster zu beachten sind:

- Für eine erfolgreiche Big Data Cluster-Bereitstellung müssen Sie sicherstellen, dass die erforderliche Anzahl von persistenten Volumes verfügbar ist. Wenn Sie in einem AKS-Cluster bereitstellen und eine der integrierten Speicherklassen (`default` oder `managed-premium`) verwenden, unterstützen diese die dynamische Bereitstellung für die persistenten Volumes. Das bedeutet, dass Sie die persistenten Volumes nicht vorab erstellen müssen. Sie müssen jedoch sicherstellen, dass die im AKS-Cluster verfügbaren Workerknoten so viele Datenträger anfügen können, wie persistente Volumes für die Bereitstellung erforderlich sind. Abhängig von der [VM-Größe](/azure/virtual-machines/linux/sizes/), die für die Workerknoten angegeben wird, kann jeder Knoten eine bestimmte Anzahl von Datenträgern anfügen. Bei einem Cluster mit Standardgröße (ohne Hochverfügbarkeit) sind mindestens 24 Datenträger erforderlich. Wenn Sie Hochverfügbarkeit aktivieren oder einen Pool zentral hochskalieren, müssen Sie für jedes zusätzliche Replikat mindestens zwei persistente Volumes sicherstellen, unabhängig von der Ressource, die Sie zentral hochskalieren.

- Wenn der Speicheranbieter für die Speicherklasse, die Sie in der Konfiguration bereitstellen, keine dynamische Bereitstellung unterstützt, müssen Sie die persistenten Volumes vorab erstellen. Die dynamische Bereitstellung wird beispielsweise nicht vom `local-storage`-Anbieter unterstützt. Weitere Informationen hierzu finden Sie in diesem [Beispielskript](https://github.com/microsoft/sql-server-samples/tree/cu1-bdc/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu) in einem mit `kubeadm` bereitgestellten Kubernetes-Cluster.

- Wenn Sie einen Big Data-Cluster bereitstellen, können Sie dieselbe Speicherklasse konfigurieren, die von allen Komponenten im Cluster verwendet werden soll. Als bewährte Methode für eine Produktionsbereitstellung benötigen verschiedene Komponenten jedoch unterschiedliche Speicherkonfigurationen, um verschiedene Workloads in Bezug auf die Größe oder den Durchsatz zu unterstützen. Sie können die im Controller angegebene Standardspeicherkonfiguration für jede SQL Server-Masterinstanz und für jeden Daten- und Speicherpool überschreiben. Im folgenden Artikel werden diese Schritte anhand von Beispielen veranschaulicht.

- Ab SQL Server 2019 CU1 können Sie die Speicherkonfigurationseinstellungen nach der Bereitstellung nicht mehr ändern. Dies gilt nicht nur für die Änderung der Größe des persistenten Volumeanspruchs für jede Instanz, sondern auch für die Skalierung von Vorgängen, die nach der Bereitstellung nicht unterstützt werden. Daher ist die Planung des Speicherlayouts vor der Erstellung eines Big Data-Clusters sehr wichtig.

- Aufgrund der Art der Bereitstellung als Containeranwendungen in Kubernetes und der Verwendung von Features wie zustandsbehafteten Sätzen und permanentem Speicher stellt Kubernetes sicher, dass Pods im Falle von Integritätsproblemen neu gestartet und an denselben permanenten Speicher angefügt werden. Für den Fall, dass ein Knoten ausfällt und ein Pod auf einem anderen Knoten neu gestartet werden muss, besteht jedoch ein höheres Risiko einer Nichtverfügbarkeit, wenn für den fehlerhaften Knoten ein lokaler Speicher verwendet wird. Um dieses Risiko zu umgehen, müssen Sie entweder eine zusätzliche Redundanz konfigurieren und [Funktionen für Hochverfügbarkeit](deployment-high-availability.md) aktivieren oder redundanten Remotespeicher verwenden. Hier finden Sie eine Übersicht über die Speicheroptionen für verschiedene Komponenten in den Big Data-Clustern.

| Ressourcen | Speichertyp für Daten | Speichertyp für Protokoll |  Hinweise |
|---|---|---|--|
| SQL Server-Masterinstanz | Lokaler Speicher (Replikate >= 3) oder redundanter Remotespeicher (Replikat = 1) | Lokaler Speicher | Die auf einem zustandsbehafteten Satz basierende Implementierung, bei der Pods auf den Knoten bleiben, stellt sicher, dass Neustarts und vorübergehende Fehler keinen Datenverlust verursachen. |
| Computepool | Lokaler Speicher* | Lokaler Speicher | Keine Benutzerdaten gespeichert |
| Datenpool | Lokaler/Redundanter Remotespeicher | Lokaler Speicher | Verwenden Sie redundante Remotespeicher, wenn der Datenpool nicht aus anderen Datenquellen neu erstellt werden kann.  |
| Speicherpool (HDFS) | Lokaler/Redundanter Remotespeicher | Lokaler Speicher | HDFS-Replikation ist aktiviert. |
| Spark-Pool | Lokaler Speicher* | Lokaler Speicher | Keine Benutzerdaten gespeichert |
| Steuerung (controldb, metricsdb, logsdb)| Redundanter Remotespeicher | Lokaler Speicher | Wichtig für die Verwendung von Speicherebenenredundanz für Big Data-Cluster-Metadaten. |

> [!IMPORTANT]
> Sie müssen sicherstellen, dass sich die steuerungsbezogenen Komponenten auf einem redundanten Remotespeicher befinden. Der `controldb-0`-Pod hostet eine SQL Server-Instanz mit Datenbanken, in denen alle Metadaten zu den Clusterdienstzuständen, verschiedenen Einstellungen usw. gespeichert werden. Wenn diese Instanz nicht verfügbar ist, treten Integritätsprobleme mit anderen abhängigen Diensten im Cluster auf.

## <a name="configure-big-data-cluster-storage-settings"></a>Konfigurieren der Speichereinstellungen für Big-Data-Cluster

Ähnlich wie bei anderen Anpassungen können Sie zum Zeitpunkt der Bereitstellung in den Clusterkonfigurationsdateien für jeden Pool in der `bdc.json`-Konfigurationsdatei und für die Steuerungsdienste in der `control.json`-Datei die Speichereinstellungen angeben. Wenn in den Poolspezifikationen keine Speicherkonfigurationseinstellungen vorhanden sind, werden die Steuerungsspeichereinstellungen für alle anderen Komponenten, einschließlich der SQL Server-Masterinstanz (`master`-Ressource), HDFS (`storage-0`-Ressource) oder des Datenpools, verwendet. Dies ist ein Beispiel für den Speicherkonfigurationsabschnitt, den Sie in die Spezifikation einschließen können:

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

> [!WARNING]
> Die Ausführung ohne persistenten Speicher kann zwar in einer Testumgebung funktionieren, führt dann allerdings möglicherweise zu einem nicht funktionsfähigen Cluster. Bei Neustarts des Pods gehen Clustermetadaten und/oder Benutzerdaten dauerhaft verloren. Die Ausführung mit dieser Konfiguration wird nicht empfohlen. 

Im Abschnitt [Konfigurieren von Speicher](#config-samples) finden Sie weitere Beispiele zum Konfigurieren der Speichereinstellungen für die Bereitstellung Ihres SQL Server-Big-Data-Clusters.

## <a name="aks-storage-classes"></a>Azure Kubernetes Service-Speicherklassen

Azure Kubernetes Service (AKS) verfügt über [zwei integrierte Speicherklassen](/azure/aks/azure-disks-dynamic-pv/) (`default` und `managed-premium`) und den dynamischen Anbieter für diese Klassen. Sie können eine dieser Klassen angeben oder Ihre eigene Speicherklasse zum Bereitstellen von Big-Data-Clustern mit aktiviertem persistenten Speicher erstellen. Standardmäßig enthält die integrierte Clusterkonfigurationsdatei für AKS (`aks-dev-test`) die permanente Speicherkonfigurationen für die Verwendung der Speicherklasse `default`.

> [!WARNING]
> Persistente Volumes, die mit den integrierten Speicherklassen`default` und `managed-premium` erstellt wurden, verfügen über eine *Delete*-Rückforderungsrichtlinie. Wenn Sie also den SQL Server-Big-Data-Cluster löschen, werden persistente Volumeansprüche und dadurch auch persistente Volumes gelöscht. Sie können mithilfe des `azure-disk`-Anbieters benutzerdefinierte Speicherklassen mit einer `Retain`-Rückforderungsrichtlinie erstellen, wie in [diesem](/azure/aks/concepts-storage/#storage-classes) Artikel gezeigt wird.

## <a name="storage-classes-for-kubeadm-clusters"></a>Speicherklassen für `kubeadm`-Cluster 

Kubernetes-Cluster, die mit `kubeadm` bereitgestellt werden, verfügen über keine integrierte Speicherklasse. Sie müssen mithilfe des lokalen Speichers und Ihres bevorzugten Anbieters wie [Rook](https://github.com/rook/rook) Ihre eigenen Speicherklassen und persistente Volumes erstellen. In diesem Fall legen Sie den Wert für `className` auf die konfigurierte Speicherklasse fest. 

> [!NOTE]
>  In den integrierten Bereitstellungskonfigurationsdateien für kubeadm (`kubeadm-dev-test` oder `kubeadm-prod`) ist für die Daten und den Protokollspeicher kein Speicherklassenname angegeben. Vor der Bereitstellung müssen Sie die Konfigurationsdatei anpassen und den Wert für „className“ festlegen, da andernfalls die Validierungen vor der Bereitstellung fehlschlagen. Die Bereitstellung umfasst außerdem einen Validierungsschritt, mit dem überprüft wird, ob die Speicherklasse vorhanden ist. Dabei wird die Existenz der erforderlichen persistenten Volumes nicht überprüft. Sie müssen sicherstellen, dass Sie abhängig von der Skalierung Ihres Clusters ausreichend Volumes erstellen. Für die standardmäßig festgelegte minimale Clustergröße (Standardskalierung, keine Hochverfügbarkeit) müssen Sie mindestens 24 persistente Volumes erstellen. [Hier](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu) finden Sie ein Beispiel für das Erstellen persistenter Volumes mithilfe eines lokalen Anbieters.


## <a name="customize-storage-configurations-for-each-pool"></a>Anpassen der Speicherkonfigurationen für jeden Pool

Für alle Anpassungen müssen Sie zuerst eine Kopie der integrierten Konfigurationsdatei erstellen, die Sie verwenden möchten. Mit dem folgenden Befehl wird beispielsweise eine Kopie der `aks-dev-test`-Konfigurationsdateien für Bereitstellungen in einem Unterverzeichnis namens `custom` erstellt:

```bash
azdata bdc config init --source aks-dev-test --target custom
```

Dadurch werden zwei Dateien erstellt (`bdc.json` und `control.json`), die entweder durch manuelles Bearbeiten oder mithilfe des Befehls `azdata bdc config` angepasst werden können. Sie können eine Kombination aus den Bibliotheken „jsonpath“ und „jsonpatch“ verwenden, um Möglichkeiten zum Bearbeiten von Konfigurationsdateien bereitzustellen.


### <a id="config-samples"></a> Konfigurieren von Speicherklassennamen und/oder der Anspruchsgröße

Die Größe der persistenten Volumeansprüche, die für alle im Cluster bereitgestellten Pods bereitgestellt werden, beträgt standardmäßig 10 GB. Sie können diesen Wert aktualisieren, um die in einer benutzerdefinierten Konfigurationsdatei ausgeführten Workloads vor der Clusterbereitstellung anzupassen.

Im folgenden Beispiel wird in der `control.json`-Datei die Anspruchsgröße für persistente Volumes auf 32 Gi aktualisiert. Diese Einstellung wird auf alle Pools angewendet, wenn sie nicht auf Poolebene überschrieben wird:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.size=100Gi"
```

Im folgenden Beispiel wird gezeigt, wie die Speicherklasse für die `control.json`-Datei geändert wird:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.storage.data.className=<yourStorageClassName>"
```

Eine andere Möglichkeit besteht darin, die benutzerdefinierte Konfigurationsdatei manuell zu bearbeiten oder wie im folgenden Beispiel eine „patch.json“-Datei zu verwenden, die die Speicherklasse für den Speicherpool ändert. Erstellen Sie eine `patch.json`-Datei mit dem folgenden Inhalt:

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

Wenden Sie die Patchdatei an. Verwenden Sie den `azdata bdc config patch`-Befehl, um die Änderungen in der JSON-Patchdatei anzuwenden. Im folgenden Beispiel wird die `patch.json`-Datei auf eine `custom.json`-Zielkonfigurationsdatei für die Bereitstellung angewendet.

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Nächste Schritte

Eine umfassende Dokumentation zu Volumes in Kubernetes finden Sie unter [Kubernetes-Dokumentation zu Volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Weitere Informationen zum Bereitstellen eines SQL Server-Big-Data-Clusters finden Sie unter [How to deploy SQL Server big data cluster on Kubernetes (Bereitstellen von SQL Server-Big-Data-Clustern in Kubernetes)](deployment-guidance.md).
