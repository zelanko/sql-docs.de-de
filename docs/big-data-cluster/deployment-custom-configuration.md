---
title: Konfigurieren von bereit Stellungen
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie eine Big Data Cluster Bereitstellung mit Konfigurationsdateien anpassen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d7559ecf9c7b17ca21c088ed531a347f88e89ee2
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419436"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Konfigurieren von Bereitstellungs Einstellungen für Big Data Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Zum Anpassen der Konfigurationsdateien für die Cluster Bereitstellung können Sie einen beliebigen JSON-Format-Editor verwenden, z. b. vscode. Verwenden Sie den Befehl **azdata BDC config** , um diese bearbeitbaren Änderungen zu automatisieren. In diesem Artikel wird erläutert, wie Sie Big Data Cluster Bereitstellungen konfigurieren, indem Sie Bereitstellungs Konfigurationsdateien ändern. Es enthält Beispiele zum Ändern der Konfiguration für verschiedene Szenarien. Weitere Informationen zur Verwendung von Konfigurationsdateien in bereit Stellungen finden Sie im [Leitfaden zur Bereitstellung](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Vorraussetzungen

- [Installieren Sie azdata](deploy-install-azdata.md).

- Bei jedem der Beispiele in diesem Abschnitt wird davon ausgegangen, dass Sie eine Kopie einer der Standardkonfigurationen erstellt haben. Weitere Informationen finden Sie unter [Erstellen einer benutzerdefinierten Konfiguration](deployment-guidance.md#customconfig). Der folgende Befehl erstellt z. b. ein Verzeichnis `custom` namens, das zwei JSON-Bereitstellungs Konfigurationsdateien (" **Cluster. JSON** " und " **Control. JSON**") basierend auf der Standardkonfiguration " **AKS-dev-Test** " enthält:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a>Ändern des Cluster namens

Der Cluster Name ist der Name des Big Data Clusters und der Kubernetes-Namespace, der bei der Bereitstellung erstellt wird. Der Wert wird im folgenden Teil der Bereitstellungs Konfigurationsdatei " **Cluster. JSON** " angegeben:

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

Der folgende Befehl sendet ein Schlüssel-Wert-Paar an den Parameter " **--JSON-Values** ", um den Big Data Cluster Namen in **Test-Cluster**zu ändern:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Der Name des Big Data Clusters darf nur alphanumerische Zeichen (Kleinbuchstaben) und keine Leerzeichen enthalten. Alle Kubernetes-Artefakte (Container, Pods, Zustands behaftete Sets, Dienste) für den Cluster werden in einem Namespace mit dem gleichen Namen wie der angegebene Cluster Name erstellt.

## <a id="ports"></a>Endpunkt Anschlüsse aktualisieren

Endpunkte werden für den Controller in der **Datei "Control. JSON** " und für das Gateway und SQL Server Master Instanz in den entsprechenden Abschnitten in " **Cluster. JSON**" definiert. Der folgende Teil der " **Control. JSON** "-Konfigurationsdatei zeigt die Endpunkt Definitionen für den Controller an:

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

Im folgenden Beispiel wird die Inline-JSON verwendet, um den Port für den **Controller** Endpunkt zu ändern:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a>Pool Replikate konfigurieren

Die Merkmale der einzelnen Pools (z. b. der Speicherpool) werden in der Konfigurationsdatei " **Cluster. JSON** " definiert. Der folgende Teil der **Datei "Cluster. JSON** " zeigt z. b. eine Speicherpool Definition:

```json
"pools": [
   {
       "metadata": {
           "kind": "Pool",
           "name": "default"
       },
       "spec": {
           "type": "Storage",
           "replicas": 2
       }
   }
]
```

Sie können die Anzahl der Instanzen in einem Pool konfigurieren, indem Sie den Wert **Replikate** für die einzelnen Pools ändern. Im folgenden Beispiel wird die Inline-JSON verwendet, um diese Werte für die Speicher- `10` und `4` Datenpools in bzw. zu ändern:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a>Konfigurieren des Speichers

Sie können auch die Speicher Klasse und die Merkmale ändern, die für die einzelnen Pools verwendet werden. Im folgenden Beispiel wird dem Speicherpool eine benutzerdefinierte Speicher Klasse zugewiesen und die Größe des Anspruchs für persistente Volumes zum Speichern von Daten auf 100 GB aktualisiert. Erstellen Sie zuerst eine Datei Patch. JSON wie unten beschrieben, die zusätzlich zu *Typ* und *Replikaten* den neuen *Speicher* Abschnitt enthält.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
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
                },
        "type":"Storage",
        "replicas":2
      }
    }
  ]
}
```

Anschließend können Sie die Konfigurationsdatei " **Cluster. JSON** " mit dem Befehl " **azdata BDC config Patch** " aktualisieren.
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> Eine auf **kubeadm-dev-Test** basierende Konfigurationsdatei besitzt keine Speicher Definition für jeden Pool, aber Sie können den obigen Prozess bei Bedarf hinzufügen.

Weitere Informationen zur Speicherkonfiguration finden Sie unter [Daten Persistenz mit SQL Server Big Data-Cluster auf Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a>Konfigurieren des Speicherpools ohne Spark

Sie können auch die Speicherpools so konfigurieren, dass Sie ohne Spark ausgeführt werden, und einen separaten Spark-Pool erstellen. Dies ermöglicht es Ihnen, Spark-Compute-Energie unabhängig vom Speicher zu skalieren. Informationen zum Konfigurieren des Spark-Pools finden Sie in der [JSON-Patchdatei im Beispiel](#jsonpatch) am Ende dieses Artikels.



Standardmäßig ist die Einstellung " **includespark** " für den Speicherpool auf "true" festgelegt. Daher müssen Sie das Feld " **includespark** " der Speicherkonfiguration hinzufügen, um Änderungen vorzunehmen. Die folgende JSON-Patchdatei zeigt, wie diese hinzugefügt wird.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
        "type":"Storage",
        "replicas":2,
        "includeSpark":false
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

## <a id="podplacement"></a>Konfigurieren der Pod-Platzierung mithilfe von Kubernetes-Bezeichnungen

Sie können die Pod-Platzierung auf Kubernetes-Knoten mit bestimmten Ressourcen steuern, um verschiedene Arten von workloadanforderungen zu erfüllen. Beispielsweise können Sie sicherstellen, dass die Speicherpool-Pods auf Knoten mit mehr Speicherplatz oder SQL Server Master Instanzen in Knoten platziert werden, die über höhere CPU-und Arbeitsspeicher Ressourcen verfügen. In diesem Fall erstellen Sie zuerst einen heterogenen Kubernetes-Cluster mit unterschiedlichen Hardwaretypen und [weisen dann Knoten Bezeichnungen](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) entsprechend zu. Zum Zeitpunkt der Bereitstellung Big Data Clusters können Sie in der Konfigurationsdatei für die Cluster Bereitstellung dieselben Bezeichnungen auf Poolebene angeben. Kubernetes kümmert sich dann um die Affinität der Pods auf Knoten, die den angegebenen Bezeichnungen entsprechen.

Im folgenden Beispiel wird gezeigt, wie eine benutzerdefinierte Konfigurationsdatei bearbeitet wird, um eine Knoten Bezeichnungs Einstellung für die SQL Server Master Instanz einzuschließen. Beachten Sie, dass in den integrierten Konfigurationen kein *noschabel* -Schlüssel vorhanden ist, sodass Sie entweder manuell eine benutzerdefinierte Konfigurationsdatei bearbeiten oder eine Patchdatei erstellen und auf die benutzerdefinierte Konfigurationsdatei anwenden müssen.

Erstellen Sie im aktuellen Verzeichnis eine Datei mit dem Namen " **Patch. JSON** " mit folgendem Inhalt:

```json
{
  "patch": [
     {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Master')].spec",
      "value": {
           "type": "Master",
         "replicas": 1,
         "hadrEnabled": false,
         "endpoints": [
            {
             "name": "Master",
             "serviceType": "NodePort",
             "port": 31433
            }
          ],
         "nodeLabel": "<yourNodeLabel>"
       }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a id="jsonpatch"></a>JSON-Patchdateien

JSON-Patchdateien konfigurieren mehrere Einstellungen gleichzeitig. Weitere Informationen zu JSON-Patches finden Sie unter [JSON-Patches in python](https://github.com/stefankoegl/python-json-patch) und [jsonpath Online Evaluator](https://jsonpath.com/).

Die folgende Datei " **Patch. JSON** " führt die folgenden Änderungen durch:

- Aktualisiert den Port eines einzelnen Endpunkts in " **Control. JSON**".
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.endpoints[?(@.name=='Controller')].port",
          "value": 30000
        }   
      ]
    }
    ```

- Aktualisiert alle Endpunkte (**Port** und **serviceType**) in der **Datei "Control. JSON**".
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.endpoints",
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
        }
      ]
    }
    ```

- Aktualisiert die Controller Speichereinstellungen in " **Control. JSON**". Diese Einstellungen gelten für alle Cluster Komponenten, es sei denn, Sie werden auf Poolebene überschrieben.
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage",
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
        }   
      ]
    }
    ```

- Aktualisiert den Speicher Klassennamen in der **Datei "Control. JSON**".
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.storage.data.className",
          "value": "managed-premium"
        }   
      ]
    }
    ```

- Aktualisiert die Pool Speichereinstellungen für den Speicherpool in " **Cluster. JSON**".
    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
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

- Aktualisiert die Spark-Einstellungen für den Speicherpool in " **Cluster. JSON**".
    ```json
    {
      "patch": [
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
        }   
      ]
    }
    ```

- Erstellt einen Spark-Pool mit zwei Instanzen in " **Cluster. JSON**".
    ```json
    {
      "patch": [
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
> Weitere Informationen zur Struktur und zu den Optionen zum Ändern einer Bereitstellungs Konfigurationsdatei finden Sie unter [Referenz zur Bereitstellungs Konfigurationsdatei für Big Data-Cluster](reference-deployment-config.md).

Verwenden Sie **azdata BDC config** -Befehle, um die Änderungen in der JSON-Patchdatei anzuwenden. Im folgenden Beispiel wird die Datei **Patch. JSON** auf eine Ziel Bereitstellungs Konfigurationsdatei **Custom/Cluster. JSON**angewendet.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Verwenden von Konfigurationsdateien in Big Data Cluster Bereitstellungen finden Sie unter Bereitstellen [von SQL Server Big Data Clustern auf Kubernetes](deployment-guidance.md#configfile).
