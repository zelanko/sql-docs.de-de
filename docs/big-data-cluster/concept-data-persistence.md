---
title: Die Datenpersistenz auf Kubernetes
titleSuffix: SQL Server big data clusters
description: Erfahren Sie mehr über die Funktionsweise der Dauerhaftigkeit von Daten in eine SQL Server-2019 big Data-Cluster.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: cfba93aaca23ca3303b6d9bd9752c1d458a9a81a
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388011"
---
# <a name="data-persistence-with-sql-server-big-data-cluster-on-kubernetes"></a>Dauerhaftigkeit von Daten mit SQL Server-big Data-Cluster in Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

[Persistente Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) Geben Sie ein Plug-In-Modell für die Speicherung in Kubernetes. Wie der Speicher bereitgestellt wird wird abstrahiert, wie es verwendet wird. Aus diesem Grund können Sie bringen Ihren eigenen Speicher mit hoher Verfügbarkeit und binden diese in der SQL Server-big Data-Cluster. Dies bietet Ihnen vollständige Kontrolle über den Typ der Speicher, Verfügbarkeit und Leistung, die erforderlich sind. Kubernetes unterstützt verschiedene Arten von speicherlösungen, einschließlich Azure-Datenträger/Dateien, NFS, lokalen Speicher und mehr.

## <a name="configure-persistent-volumes"></a>Konfigurieren von persistenten volumes

Die Möglichkeit, eine SQL Server-big Data-Cluster diese persistenten Volumes verwendet, ist die Verwendung [Speicherklassen](https://kubernetes.io/docs/concepts/storage/storage-classes/). Sie können unterschiedliche Speicherklassen für unterschiedliche Arten von Speicher zu erstellen, und geben sie zur Bereitstellungszeit big Data-Cluster. Sie können die Speicherklasse und die persistentes Volume Anspruch Größe für den Zweck auf der Poolebene konfigurieren. Erstellt eine SQL Server-big Data-Cluster [persistentes Volume Ansprüche](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) mit dem angegebenen Speicherkonto Klassennamen für jede Komponente, die persistente Volumes erforderlich sind. Sie bindet dann die entsprechenden persistenten Volumes in den Pod. 

## <a name="configure-big-data-cluster-storage-settings"></a>Konfigurieren der speichereinstellungen für big Data-cluster

Ähnlich wie andere Anpassungen, können Sie speichereinstellungen in den Konfigurationsdateien für den Cluster zum Zeitpunkt der Bereitstellung für jeden Pool und die Steuerungsebene angeben. Wenn keine Speicher-Konfigurationseinstellungen in den Pool-Spezifikationen vorhanden sind, und klicken Sie dann die speichereinstellungen für Steuerelement-Ebene verwendet werden. Dies ist ein Beispiel für den Abschnitt zur Speicherkonfiguration, den in der Spezifikation enthalten können:

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

Bereitstellung von big Data-Cluster verwendet permanenten Speicher zum Speichern von Daten, Metadaten und Protokolle für die verschiedenen Komponenten. Sie können anpassen, dass die Größe der persistentes Volume Ansprüche als Teil der Bereitstellung erstellt. Als bewährte Methode, wir empfehlen die Verwendung von Storage-Klassen mit einer *beibehalten* [freigeben Richtlinie](https://kubernetes.io/docs/concepts/storage/storage-classes/#reclaim-policy).

> [!NOTE]
> In CTP 3.1 können Sie Storage-Konfiguration die Einstellung nach der Bereitstellung nicht ändern. Darüber hinaus nur `ReadWriteOnce` den Zugriffsmodus für das gesamte Cluster wird unterstützt.

> [!WARNING]
> Ausgeführt wird, ohne den beständigen Speicher benötigen, kann in einer testumgebung arbeiten, aber in einem nicht funktionierenden Cluster resultieren. Bei Pod neu gestartet wird verloren Metadaten und/oder Clusterdaten dauerhaft. Wir empfehlen nicht in dieser Konfiguration ausgeführt. 

[Konfigurieren des Speichers](#config-samples) Abschnitt enthält weitere Beispiele zum Konfigurieren der speichereinstellungen für die SQL Server-big Data-Clusterbereitstellung.

## <a name="aks-storage-classes"></a>AKS-Speicherklassen

Im Lieferumfang von AKS [zwei integrierte Speicherklassen](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv) **Standard** und **verwaltete Premium-** zusammen mit der dynamischen Bereitstellung für sie. Sie können geben einen der beiden oder erstellen eigene Speicherklasse für die Bereitstellung von big Data-Cluster mit permanenten Speicher mit Lesezugriff aktiviert. Standardmäßig die integrierte in der Clusterkonfigurationsdatei für Aks *Aks-Dev-Test* im Lieferumfang von permanenten Speicher Empfohlene Konfigurationen, **Standard** Speicherklasse.

> [!WARNING]
> Persistente Volumes mit den integrierten Speicherklassen erstellt **Standard** und **verwaltete Premium-** verfügen über eine Richtlinie bei der Rückgewinnung von *löschen*. Daher zur Zeit die Sie löschen die SQL Server-big Data-Cluster, erhalten persistentes Volume Ansprüche auch gelöscht, und klicken Sie dann persistenten Volumes. Sie können benutzerdefinierte Speicherklassen mit erstellen **Azure-Datenträger** Privioner mit eine *beibehalten* Richtlinie freizugeben, siehe [dies](https://docs.microsoft.com/en-us/azure/aks/concepts-storage#storage-classes) Artikel.


## <a name="minikube-storage-class"></a>Minikube-Speicherklasse

Minikube ist über eine integrierte-Klasse namens **standard** zusammen mit einer dynamischen Provisioner für sie. Die integrierten Konfigurationsdatei für Minikube *Minikube-Dev-Test* verfügt über die speichereinstellungen für die Konfiguration in der Spezifikation der Steuerelement-Ebene. Die gleichen Einstellungen werden auf alle Daten des Pools angewendet werden. Sie können auch eine Kopie dieser Datei anpassen und es für Ihre big Data-Cluster-Bereitstellung auf Minikube. Sie können manuell bearbeiten Sie die benutzerdefinierte Datei, und ändern Sie die Größe der persistenten Volumes Ansprüche für bestimmte Pools, um die arbeitsauslastungen zu berücksichtigen, dass Sie ausführen möchten. Alternativ finden Sie unter [Konfigurieren des Speichers](#config-samples) im Abschnitt Beispiele dazu, wie Sie bearbeitet, mithilfe von *Mssqlctl* Befehle.

## <a name="kubeadm-storage-classes"></a>Kubeadm Speicherklassen

Kubeadm kommt nicht mit einer integrierten Speicherklasse. Sie müssen eigene Speicherklassen und persistente Volumes mit lokalen Speicher oder Ihre bevorzugte-Bereitstellung wie erstellen [Turm](https://github.com/rook/rook). In diesem Fall legen Sie die **ClassName** der Speicherklasse, die Sie konfiguriert haben. 

> [!NOTE]
>  In den integrierten in Bereitstellungskonfigurationsdatei für *Kubeadm Kubeadm-Dev-Test* es ist keine Speicher-Klassenname, die für die Speicherung von Daten- und Protokolldateien festgelegt. Sie müssen vor der Bereitstellung Anpassen der Konfigurationsdatei und legen Sie den Wert für ClassName andernfalls die Überprüfungen vor der Bereitstellung fehl. Bereitstellung verfügt auch über Schritt zur Überprüfung, der das Vorhandensein der Speicherklasse, aber nicht die erforderlichen persistente Volumes überprüft. Sie müssen sicherstellen, dass Sie genügend Volumes abhängig vom Umfang des Clusters erstellen. In CTP 3.1 müssen Sie für die Standardgröße für den Cluster mindestens 23 Volumes erstellen. [Hier](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu) ist ein Beispiel zum Erstellen von persistenten Volumes mit der lokalen Bereitstellung.


## <a name="customize-storage-configurations-for-each-pool"></a>Speicherkonfigurationen für jeden Pool anpassen

Für alle Anpassungen müssen Sie zunächst eine Kopie der integrierten erstellen in der Konfigurationsdatei, die Sie verwenden möchten. Beispielsweise der folgende Befehl erstellt eine Kopie der *Aks-Dev-Test* Bereitstellungskonfigurationsdatei in ein Unterverzeichnis namens `custom`:

```bash
mssqlctl bdc config init --source aks-dev-test --target custom
```

Klicken Sie dann, Sie können der Konfigurationsdatei anpassen, entweder indem Sie ihn manuell bearbeiten, oder Sie können **Mssqlctl BDC-Config Abschnitt Satz** Befehl. Diese Set-Befehl verwendet eine Kombination von Jsonpath und Jsonpatch-Bibliotheken zum Bearbeiten der Konfigurationsdatei zu bieten.

### <a name="configure-size"></a>Konfigurieren der Größe

Standardmäßig beträgt die Größe der einzelnen die Pods im Cluster bereitgestellten bereitgestellten persistentes Volume Ansprüche 10 GB. Sie können diesen Wert, um die Workloads zu verarbeiten, die Sie in eine benutzerdefinierte Konfigurationsdatei vor der Bereitstellung des Clusters ausgeführt werden, aktualisieren.

Das folgende Beispiel aktualisiert nur die Größe der Ansprüche, die persistenten Volumes im Speicherpool auf 100Gi gespeicherten Daten. Beachten Sie, dass Speicherabschnitt vorhanden in der Konfigurationsdatei für den Speicherpool sein muss, bevor Sie diesen Befehl ausführen:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.size=100Gi"
```

Das folgende Beispiel aktualisiert die Größe des persistenten Volumes Ansprüche für alle Pools auf 32Gi:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.storage.data.size=32Gi"
```

### <a id="config-samples"></a> Konfigurieren von Speicherklasse

Folgende Beispiel zeigt, wie die Speicherklasse für die Steuerungsebene geändert wird:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.storage.data.className=<yourStorageClassName>"
```

Eine weitere Möglichkeit ist die benutzerdefinierte Konfigurationsdatei manuell bearbeiten oder Jsonpatch wie im folgenden Beispiel zu verwenden, die Storage-Klasse für den Speicherpool ändert. Erstellen Sie eine *patch.json* Datei mit diesem Inhalt:

```json
{
  "patch": [
    {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage",
      "value": {
          "data": {
            "className": "default",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "default",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
      }
  ]
}
```

Wenden Sie die Patchdatei. Verwendung **Mssqlctl BDC-Config Abschnitt Satz** Befehl aus, um die Änderungen in der JSON Patch-Datei zu übernehmen. Im folgende Beispiel wird ein Ziel Deployment Configuration Datei custom.json patch.json Datei gilt.

```bash
mssqlctl bdc config section set --config-profile custom -p ./patch.json
```

## <a name="next-steps"></a>Nächste Schritte

Vollständige Dokumentation über Kubernetes-Volumes finden Sie in der [Kubernetes-Dokumentation auf Volumes](https://kubernetes.io/docs/concepts/storage/volumes/).

Weitere Informationen zum Bereitstellen einer SQL Server-big Data-Cluster finden Sie unter [Gewusst wie: Bereitstellen von SQL Server, big Data-in Kubernetes Cluster](deployment-guidance.md).

