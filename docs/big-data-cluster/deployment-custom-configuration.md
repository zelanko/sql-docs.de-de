---
title: Konfigurieren von Bereitstellungen
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie eine Big-Data-Clusterbereitstellung mit Konfigurationsdateien anpassen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7d04df5bf881f285ab28508443fbf0ce1056fada
ms.sourcegitcommit: 316c25fe7465b35884f72928e91c11eea69984d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2019
ms.locfileid: "68969493"
---
# <a name="configure-deployment-settings-for-big-data-clusters"></a>Konfigurieren von Bereitstellungseinstellungen für Big-Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sie können einen beliebigen JSON-Format-Editor verwenden (z. B. VS Code), um die Konfigurationsdateien für Ihre Clusterbereitstellung anzupassen. Verwenden Sie den Befehl **azdata bdc config**, um für diese Bearbeitungen Skripts zu erstellen und sie zu automatisieren. In diesem Artikel wird erläutert, wie Sie Big-Data-Clusterbereitstellungen konfigurieren, indem Sie Bereitstellungskonfigurationsdateien ändern. Er enthält Beispiele zum Ändern der Konfiguration für verschiedene Szenarios. Weitere Informationen zur Verwendung von Konfigurationsdateien in Bereitstellungen finden Sie im [Leitfaden zur Bereitstellung](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Vorraussetzungen

- [Installieren Sie azdata](deploy-install-azdata.md).

- Bei jedem der Beispiele in diesem Abschnitt wird davon ausgegangen, dass Sie eine Kopie einer der Standardkonfigurationen erstellt haben. Weitere Informationen finden Sie unter [Create a custom configuration (Erstellen einer benutzerdefinierten Konfiguration)](deployment-guidance.md#customconfig). Mit dem folgenden Befehl wird z. B. ein Verzeichnis namens `custom` erstellt, das die beiden JSON-Bereitstellungskonfigurationsdateien **cluster.json** und **control.json** enthält, basierend auf der Standardkonfiguration für **aks-dev-test**:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Ändern von Clusternnamen

Der Clustername entspricht dem Namen des Big-Data-Clusters und dem Kubernetes-Namespace, der bei der Bereitstellung erstellt wird. Er wird im folgenden Teil der Bereitstellungskonfigurationsdatei **cluster.json** angegeben:

```json
"metadata": {
    "kind": "Cluster",
    "name": "mssql-cluster"
},
```

Der folgende Befehl sendet ein Schlüssel-Wert-Paar an den **--json-values**-Parameter, um den Big-Data-Clusternamen in **test-cluster** zu ändern:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Der Name Ihres Big-Data-Clusters darf nur alphanumerische Zeichen (Kleinbuchstaben) und keine Leerzeichen enthalten. Alle Kubernetes-Artefakte (Container, Pods, zustandsbehaftete Sets, Dienste) für den Cluster werden in einem Namespace mit dem gleichen Namen wie der angegebene Clustername erstellt.

## <a id="ports"></a> Aktualisieren von Endpunktports

Endpunkte werden für den Controller in der Datei **control.json** und für das Gateway und die SQL Server-Masterinstanz in den entsprechenden Abschnitten in der Datei **cluster.json** definiert. Der folgende Teil der Konfigurationsdatei **control.json** zeigt die Endpunktdefinitionen für den Controller an:

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

Im folgenden Beispiel wird das Inline-JSON-Format verwendet, um den Port für den **Controller**-Endpunkt zu ändern:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Konfigurieren von Poolreplikaten

Die Merkmale der einzelnen Pools (z. B. des Speicherpools) werden in der Konfigurationsdatei **cluster.json** definiert. Der folgende Teil der Datei **cluster.json** zeigt z. B. eine Speicherpooldefinition an:

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

Sie können die Anzahl der Instanzen in einem Pool konfigurieren, indem Sie den **Replikate**-Wert für die einzelnen Pools ändern. Im folgenden Beispiel wird das Inline-JSON-Format verwendet, um diese Werte für die Speicher- und Datenpools in `10` bzw. `4` zu ändern:

```bash
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Storage"")].spec.replicas=10"
azdata bdc config replace --config-file custom/cluster.json --json-values "$.spec.pools[?(@.spec.type == ""Data"")].spec.replicas=4"
```

## <a id="storage"></a> Konfigurieren des Speichers

Sie können auch die Speicherklasse und die Merkmale ändern, die für die einzelnen Pools verwendet werden. Im folgenden Beispiel wird dem Speicherpool eine benutzerdefinierte Speicherklasse zugewiesen, und die Größe des Anspruchs für persistente Volumes zum Speichern von Daten wird auf 100 GB aktualisiert. Erstellen Sie zuerst eine „patch.json“-Datei (wie unten beschrieben), die zusätzlich zu *Typ* und *Replikaten* den neuen *Speicher*-Abschnitt enthält.

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

Anschließend können Sie mit dem Befehl **azdata bdc config patch** die Konfigurationsdatei **cluster.json** aktualisieren.
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json
```

> [!NOTE]
> Eine auf **kubeadm-dev-test** basierende Konfigurationsdatei besitzt keine Speicherdefinition für die einzelnen Pools, aber Sie können sie mit dem obigen Prozess bei Bedarf hinzufügen.

Weitere Informationen zur Speicherkonfiguration finden Sie unter [Datenpersistenz mit Big-Data-Cluster für SQL Server in Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a> Konfigurieren von Speicherpools ohne Spark

Sie können die Speicherpools auch so konfigurieren, dass sie ohne Spark ausgeführt werden, und einen separaten Spark-Pool erstellen. Dies ermöglicht es Ihnen, Spark-Computeleistung unabhängig vom Speicher zu skalieren. Informationen zum Konfigurieren des Spark-Pools finden Sie im [JSON-Patchdateibeispiel](#jsonpatch) am Ende dieses Artikels.



Standardmäßig ist die Einstellung **includeSpark** für den Speicherpool auf „true“ festgelegt. Daher müssen Sie das Feld **includeSpark** der Speicherkonfiguration hinzufügen, um Änderungen vorzunehmen. Die folgende JSON-Patchdatei zeigt, wie dieses hinzugefügt wird.

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

## <a id="podplacement"></a> Konfigurieren von Pod-Platzierungen mit Kubernetes-Bezeichnungen

Sie können Pod-Platzierungen auf Kubernetes-Knoten steuern, die über bestimmten Ressourcen verfügen, um verschiedene Arten von Arbeitsauslastungsanforderungen zu erfüllen. Beispielsweise können Sie sicherstellen, dass die Speicherpoolpods auf Knoten mit mehr Speicherplatz platziert werden oder SQL Server-Masterinstanzen in Knoten platziert werden, die über höhere CPU- und Arbeitsspeicherressourcen verfügen. In diesem Fall erstellen Sie zuerst einen heterogenen Kubernetes-Cluster mit unterschiedlichen Hardwaretypen. Anschließend nehmen Sie die entsprechende [Zuweisung von Knotenbezeichnungen](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) vor. Zum Zeitpunkt der Bereitstellung des Big-Data-Clusters können Sie in der Konfigurationsdatei für die Clusterbereitstellung dieselben Bezeichnungen auf Poolebene angeben. Kubernetes kümmert sich dann um die Affinität der Pods auf Knoten, die den angegebenen Bezeichnungen entsprechen. Der spezifische Bezeichnungs Schlüssel, der den Knoten im kubernetes-Cluster hinzugefügt werden muss, ist **MSSQL-Cluster-Wide**. Der Wert dieser Bezeichnung kann jede beliebige Zeichenfolge sein, die Sie auswählen.

Im folgenden Beispiel wird gezeigt, wie Sie eine benutzerdefinierte Konfigurationsdatei bearbeiten, um eine Knoten Bezeichnungs Einstellung für die SQL Server Master Instanz, den computepool, den Daten Pool & Speicherpools einzuschließen. Beachten Sie, dass in den integrierten Konfigurationen kein *nodeLabel*-Schlüssel vorhanden ist, sodass Sie entweder manuell eine benutzerdefinierte Konfigurationsdatei bearbeiten oder eine Patchdatei erstellen und auf die benutzerdefinierte Konfigurationsdatei anwenden müssen. Der SQL Server Master Instanz-Pod wird auf einem Knoten bereitgestellt, der eine Bezeichnung " **MSSQL-Cluster-Wide** " mit dem Wert " **BDC-Master**" enthält. Der computepool und die Daten Pool-Pods werden auf Knoten bereitgestellt, die eine Bezeichnung " **MSSQL-Cluster-Wide** " mit dem Wert " **BDC-SQL**" enthalten. Die Speicher Pool-Pods werden auf Knoten bereitgestellt, die eine Bezeichnung " **MSSQL-Cluster-Wide** " mit dem Wert " **BDC-Storage**" enthalten.

Erstellen Sie in Ihrem aktuellen Verzeichnis eine Datei mit dem Namen **patch.json** und dem folgenden Inhalt:

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
        "nodeLabel": "bdc-master"
      }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Compute')].spec",
      "value": {
    "type": "Compute",
        "replicas": 1,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Data')].spec",
      "value": {
    "type": "Data",
        "replicas": 2,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "$.spec.pools[?(@.spec.type == 'Storage')].spec",
      "value": {
    "type": "Storage",
        "replicas": 3,
        "nodeLabel": "bdc-storage"
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a id="jsonpatch"></a> JSON-Patchdateien

JSON-Patchdateien konfigurieren mehrere Einstellungen gleichzeitig. Weitere Informationen zu JSON-Patches finden Sie unter [JSON-Patches in Python](https://github.com/stefankoegl/python-json-patch) und [JSONPath Online Evaluator](https://jsonpath.com/).

Die folgende Datei **patch.json** führt die folgenden Änderungen durch:

- Aktualisiert den Port eines einzelnen Endpunkts in der Datei **control.json**.
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

- Aktualisiert alle Endpunkte (**port** und **serviceType**) in der Datei **control.json**.
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

- Aktualisiert die Controllerspeichereinstellungen in der Datei **control.json**. Diese Einstellungen gelten für alle Clusterkomponenten, es sei denn, sie werden auf Poolebene überschrieben.
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

- Aktualisiert den Speicherklassennamen in der Datei **control.json**.
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

- Aktualisiert die Poolspeichereinstellungen für den Speicherpool in der Datei **cluster.json**.
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

- Aktualisiert die Spark-Einstellungen für den Speicherpool in der Datei **cluster.json**.
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

- Erstellt einen Spark-Pool mit zwei Instanzen in der Datei **cluster.json**.
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
> Weitere Informationen zur Struktur und zu den Optionen zum Ändern einer Bereitstellungskonfigurationsdatei finden Sie unter [Referenz zur Bereitstellungskonfigurationsdatei für Big-Data-Cluster](reference-deployment-config.md).

Verwenden Sie **azdata bdc config**-Befehle, um die Änderungen in der JSON-Patchdatei anzuwenden. Im folgenden Beispiel wird die Datei **patch.json** auf eine Zielkonfigurationsdatei **custom/cluster.json** für die Bereitstellung angewendet.

```bash
azdata bdc config patch --config-file custom/cluster.json --patch-file ./patch.json
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Verwenden von Konfigurationsdateien in Big Data-Clusterbereitstellungen finden Sie unter [Bereitstellen von Big Data-Clustern für SQL Server in Kubernetes](deployment-guidance.md#configfile).
