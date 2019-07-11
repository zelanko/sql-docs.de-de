---
title: Konfigurieren von Bereitstellungen
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie eine big Data-Clusterbereitstellung mit Konfigurationsdateien anpassen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 19654422bcc57f2ad00b9ab8170d163f848f188b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728889"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Konfigurieren von bereitstellungseinstellungen für big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Informationen zum Anpassen der Konfigurationsdatei des Cluster-Bereitstellung können Sie alle mit JSON-Format-Editor, z. B. VSCode verwenden. Verwenden Sie für die Skripterstellung diese Änderungen zur Automatisierung verwenden, die **Mssqlctl Bdc-Abschnitt "Config"** Befehl. In diesem Artikel wird erläutert, wie Sie big Data-Cluster-Bereitstellungen zu konfigurieren, durch das Ändern von Konfigurationsdateien für die Bereitstellung. Es bietet Beispiele für die Konfiguration für verschiedene Szenarien zu ändern. Weitere Informationen zur Verwendung von Konfigurationsdateien in Bereitstellungen finden Sie unter den [bereitstellungsanleitung](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Vorraussetzungen

- [Installieren Sie Mssqlctl](deploy-install-mssqlctl.md).

- Jedes der Beispiele in diesem Abschnitt wird davon ausgegangen, dass Sie eine Kopie der standard-Konfigurationsdateien erstellt haben. Weitere Informationen finden Sie unter [erstellen Sie eine benutzerdefinierte Konfigurationsdatei](deployment-guidance.md#customconfig). Der folgende Befehl erstellt z. B. ein Verzeichnis namens `custom` , enthält eine JSON-Bereitstellungskonfigurationsdatei basierend auf dem standardmäßigen **Aks-Dev-Test** Konfiguration:

   ```bash
   mssqlctl bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Clusternamen ändern

Den Namen des Clusters ist, den Namen des big Data-Cluster und der Kubernetes-Namespace, der bei der Bereitstellung erstellt wird. Er wird in der folgende Auszug aus der Konfigurationsdatei der Bereitstellung angegeben:

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

Der folgende Befehl sendet ein Schlüssel / Wert-Paar der **--Json-Werte** Parameter so ändern Sie den Clusternamen big Data **Test-Cluster**:

```bash
mssqlctl bdc config section set --config-profile custom -j "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Der Name des Ihrer big Data-Cluster muss nur Kleinbuchstaben alphanumerische Zeichen, keine Leerzeichen enthalten. Alle Kubernetes-Artefakte (Container, Pods, zustandsbehaftete Gruppen, Dienste) für den Cluster in einem Namespace mit demselben Namen wie der Cluster erstellt werden angegebenen Namen.

## <a id="ports"></a> Aktualisieren Sie die Endpunkt-ports

Endpunkte werden für die Steuerungsebene sowie für die einzelnen Pools definiert. Der folgende Auszug aus der Konfigurationsdatei zeigt die Endpunktdefinitionen für die Steuerungsebene:

```json
"endpoints": [
    {
        "name": "Controller",
        "serviceType": "LoadBalancer",
        "port": 30080
    },
    {
        "name": "ServiceProxy",
        "serviceType": "LoadBalancer",
        "port": 30777
    }
]
```

Im folgenden Beispiel wird Inline JSON so ändern Sie den Port für die **Controller** Endpunkt:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.controlPlane.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Konfigurieren Sie Pool-Replikate

Die Merkmale jeder Pool wie z. B. der Speicherpool ist in der Konfigurationsdatei definiert. Der folgende Auszug zeigt beispielsweise eine Speicher-Pool-Definition:

```json
"pools": [
    {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Storage",
            "replicas": 2,
            "storage": {
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
           },
        }
    }
]
```

Sie können die Anzahl der Instanzen in einem Pool konfigurieren, durch Ändern der **Replikate** Wert für jeden Pool. Im folgenden Beispiel wird Inline JSON so ändern Sie diese Werte für die datenspeicherung und dem Pools `10` und `4` bzw.:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a> Konfigurieren des Speichers

Sie können auch ändern, die Speicherklasse und die Eigenschaften, die für jeden Pool verwendet werden. Im folgenden Beispiel weist eine benutzerdefinierten Speicher-Klasse für den Speicherpool und die Größe der Anspruch auf das persistente Volume zum Speichern von Daten zu 100Gb aktualisiert. Benötigen Sie in diesem Abschnitt in der Konfigurationsdatei zum Aktualisieren der Einstellungen mithilfe der *Mssqlctl BDC-Config Set* Befehl, finden Sie unter folgenden wird eine Patch-Datei zu verwenden, um diesen Abschnitt hinzufügen:

```bash
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.className=storage-pool-class"
mssqlctl bdc config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].spec.storage.data.size=32Gi"
```

> [!NOTE]
> Eine Konfigurationsdatei basierend auf **Kubeadm-Dev-Test** keine Speicher-Definition für jeden Pool, aber dies manuell hinzugefügt werden, wenn erforderlich.

Weitere Informationen zur Speicherkonfiguration finden Sie unter [Dauerhaftigkeit von Daten mit SQL Server, die big Data-in Kubernetes Cluster](concept-data-persistence.md).

## <a id="sparkstorage"></a> Konfigurieren des Speichers, ohne spark

Sie können auch die Speicherpools, ohne Spark ausführen, und erstellen Sie einen separaten Spark-Pool konfigurieren. Dadurch können Sie zum Skalieren Spark Compute-Power-unabhängigen Speicher. Gewusst wie: Konfigurieren des Spark-Pools finden Sie unter den [JSON Patch-DateiBeispiel](#jsonpatch) am Ende dieses Artikels.

Sie benötigen in diesem Abschnitt, in der Konfigurationsdatei zum Aktualisieren der Einstellungen, die mit der `mssqlctl cluster config set command`. Die folgende JSON-Patch-Datei veranschaulicht, wie diese hinzufügen.

In der Standardeinstellung die **IncludeSpark** Einstellung für der Speicherpool auf true ist, festgelegt deshalb müssen Sie die **IncludeSpark** in der Speicherkonfiguration, um Änderungen vorzunehmen:

```bash
mssqlctl cluster config section set --config-profile custom -j "$.spec.pools[?(@.spec.type == ""Storage"")].includeSpark=false"
```

## <a id="podplacement"></a> Konfigurieren von Pod-Platzierung mit Kubernetes-Bezeichnungen

Sie können die Pod-Platzierung auf Kubernetes-Knoten steuern, die bestimmte Ressourcen, um verschiedene Arten von workloadanforderungen zu berücksichtigen. Beispielsweise empfiehlt es sich um sicherzustellen, dass die Speicher-Pool-Pods auf Knoten mit mehr Speicherplatz platziert werden, oder master SQL Server-Instanzen auf Knoten, die höhere CPU- und Speicherressourcen platziert werden. In diesem Fall erstellen Sie zunächst einen heterogenen Kubernetes-Cluster mit verschiedenen Arten von Hardware und dann [Knoten Bezeichnungen zuweisen](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) entsprechend. Zum Zeitpunkt der Bereitstellung von big Data-Cluster können Sie die gleiche Bezeichnungen auf der Ebene von Pools in der Bereitstellungskonfigurationsdatei für Cluster angeben. Kubernetes dann übernimmt die Pods auf Knoten, die die angegebenen Bezeichnungen entsprechen zuordnen.

Das folgende Beispiel zeigt, wie Sie eine benutzerdefinierte Konfigurationsdatei enthält eine Knoten-Label-Einstellung für die master-SQL Server-Instanz zu bearbeiten. Beachten Sie, dass es keine *NodeLabel* Schlüssel in den integrierten Konfigurationen, daher müssen Sie eine benutzerdefinierte Konfigurationsdatei manuell bearbeiten oder erstellen Sie eine Patchdatei und klicken Sie auf die benutzerdefinierte Konfigurationsdatei angewendet.

Erstellen Sie eine Datei mit dem Namen **patch.json** in Ihrem aktuellen Verzeichnis mit dem folgenden Inhalt:

```json
{
  "patch": [
     {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Master')].spec",
      "value": {
      "nodeLabel": "<yourNodeLabel>"
       }
    }
  ]
}
```

```bash
mssqlctl bdc config section set --config-profile custom -p ./patch.json
```

## <a id="jsonpatch"></a> JSON-Patch-Dateien

JSON-Patch-Dateien konfigurieren Sie Einstellungen für mehrere gleichzeitig. Weitere Informationen zu JSON-Patches, finden Sie unter [JSON-Patches in Python](https://github.com/stefankoegl/python-json-patch) und [JSONPath-Online-Ausdrucksauswertung](https://jsonpath.com/).

Die folgenden **patch.json** -Datei führt die folgenden Änderungen:

- Aktualisiert den Port für Endpunkt an.
- Aktualisiert alle Endpunkte (**Port** und **ServiceType**).
- Aktualisiert den Speicher der Steuerelement-Ebene. Diese Einstellungen gelten für alle Clusterkomponenten, es sei denn, die auf Pools überschrieben.
- Aktualisiert den Klassennamen "Storage" im Speicher der Steuerelement-Ebene.
- Aktualisiert die Pool-Einstellungen für den Speicherpool.
- Aktualisiert die Spark-Einstellungen für den Speicherpool.
- Erstellt einen Spark-Pool mit 2 Replikate für den cluster

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port",
      "value": 30000
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.endpoints",
      "value": [
        {
          "serviceType": "LoadBalancer",
          "port": 30001,
          "name": "Controller"
        },
        {
            "serviceType": "LoadBalancer",
            "port": 30778,
            "name": "ServiceProxy"
        }
      ]
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.controlPlane",
      "value": {
          "data": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
    },
    {
      "op": "replace",
      "path": "spec.controlPlane.spec.storage.data.className",
      "value": "managed-premium"
    },
    {
      "op": "add",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec.storage",
      "value": {
          "data": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "100Gi"
          },
          "logs": {
            "className": "managed-premium",
            "accessMode": "ReadWriteOnce",
            "size": "32Gi"
          }
        }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].hadoop.spark",
      "value": {
        "driverMemory": "2g",
        "driverCores": 1,
        "executorInstances": 3,
        "executorCores": 1,
        "executorMemory": "1536m"
      }
    },
    {
      "op": "add",
      "path": "spec.pools/-",
      "value":
      {
        "metadata": {
          "kind": "Pool",
          "name": "default"
        },
        "spec": {
          "type": "Spark",
          "replicas": 2
        },
        "hadoop": {
          "yarn": {
            "nodeManager": {
              "memory": 12288,
              "vcores": 6
            },
            "schedulerMax": {
              "memory": 12288,
              "vcores": 6
            },
            "capacityScheduler": {
              "maxAmPercent": 0.3
            }
          },
          "spark": {
            "driverMemory": "2g",
            "driverCores": 1,
            "executorInstances": 2,
            "executorMemory": "2g",
            "executorCores": 1
          }
        }
      }
    }   
  ]
}
```

> [!TIP]
> Weitere Informationen zur Struktur und Optionen zum Ändern einer Bereitstellungskonfigurationsdatei finden Sie unter [Bereitstellung-konfigurationsdateireferenz für big Data-Cluster](reference-deployment-config.md).

Verwendung **Mssqlctl BDC-Config Abschnitt Satz** zum Anwenden der Änderungen in der JSON Patch-Datei. Im folgenden Beispiel wird die **patch.json** Datei in eine Ziel-Bereitstellungskonfigurationsdatei **custom.json**.

```bash
mssqlctl bdc config section set --config-profile custom -p ./patch.json
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Verwendung von Konfigurationsdateien in big Data-Cluster-Bereitstellungen finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md#configfile).
