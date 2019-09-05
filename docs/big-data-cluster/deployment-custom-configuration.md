---
title: Konfigurieren von Bereitstellungen
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie eine Big-Data-Clusterbereitstellung mit Konfigurationsdateien anpassen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a0da84d60a9513b0ca81a0256218928372882e72
ms.sourcegitcommit: 0c6c1555543daff23da9c395865dafd5bb996948
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70304827"
---
# <a name="configure-deployment-settings-for-cluster-resources-and-services"></a>Konfigurieren von Bereitstellungs Einstellungen für Cluster Ressourcen und-Dienste

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ausgehend von einem vordefinierten Satz von Konfigurations Profilen, die in das azdata-Verwaltungs Tool integriert sind, können Sie die Standardeinstellungen problemlos so ändern, dass Sie Ihren BDC-workloadanforderungen besser entsprechen. Beginnend mit der Release Candidate-Version wurde die Struktur der Konfigurationsdateien aktualisiert, um Ihnen die granulare Aktualisierung von Einstellungen für jeden Dienst der Ressource zu ermöglichen. 

Sie können auch Konfigurationen auf Ressourcenebene festlegen oder die Konfigurationen für alle Dienste in einer Ressource aktualisieren. Im folgenden finden Sie eine Zusammenfassung der Struktur für **BDC. JSON**:

```json
{
    "apiVersion": "v1",
    "metadata": {
        "kind": "BigDataCluster",
        "name": "mssql-cluster"
    },
    "spec": {
        "resources": {
            "nmnode-0": {...
            },
            "sparkhead": {...
            },
            "zookeeper": {...
            },
            "gateway": {...
            },
            "appproxy": {...
            },
            "master": {...
            },
            "compute-0": {...
            },
            "data-0": {...
            },
            "storage-0": {...
        },
        "services": {
            "sql": {
                "resources": [
                    "master",
                    "compute-0",
                    "data-0",
                    "storage-0"
                ]
            },
            "hdfs": {
                "resources": [
                    "nmnode-0",
                    "zookeeper",
                    "storage-0",
                    "sparkhead"
                ],
                "settings": {...
            },
            "spark": {
                "resources": [
                    "sparkhead",
                    "storage-0"
                ],
                "settings": {...
            }
        }
    }
}
```

Zum Aktualisieren von Konfigurationen auf Ressourcenebene, wie z. b. Instanzen in einem Pool, aktualisieren Sie die Ressourcen Spezifikation. Um beispielsweise die Anzahl von Instanzen im computepool zu aktualisieren, ändern Sie diesen Abschnitt in der Konfigurationsdatei **BDC. JSON** :
```json
"resources": {
    ...
    "compute-0": {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Compute",
            "replicas": 4
        }
    }
    ...
}
``` 

Gleiches gilt für das Ändern der Einstellungen eines einzelnen Dienstanbieter innerhalb einer bestimmten Ressource. Wenn Sie z. b. die Spark-Speichereinstellungen nur für die Spark-Komponente im Speicherpool ändern möchten, aktualisieren Sie die Ressource " **Storage-0** " mit einem Abschnitt " **Einstellungen** " für den **Spark** -Dienst in der Konfigurationsdatei " **BDC. JSON".** .
```json
"resources":{
    ...
     "storage-0": {
        "metadata": {
            "kind": "Pool",
            "name": "default"
        },
        "spec": {
            "type": "Storage",
            "replicas": 2,
            "settings": {
                "spark": {
                    "driverMemory": "2g",
                    "driverCores": "1",
                    "executorInstances": "3",
                    "executorMemory": "1536m",
                    "executorCores": "1"
                }
            }
        }
    }
    ...
}
```

Wenn Sie dieselben Konfigurationen für einen Dienst, der mehreren Ressourcen zugeordnet ist, anwenden möchten, aktualisieren Sie die entsprechenden **Einstellungen** im Abschnitt " **Dienste** ". Wenn Sie z. b. dieselben Einstellungen für Spark sowohl für Speicherpool-als auch für Spark-Pools festlegen möchten, aktualisieren Sie den Abschnitt " **Einstellungen** " im Abschnitt " **Spark** -Dienst" in der Konfigurationsdatei " **BDC. JSON** ".

```json
"services": {
    ...
    "spark": {
        "resources": [
            "sparkhead",
            "storage-0"
        ],
        "settings": {
            "driverMemory": "2g",
            "driverCores": "1",
            "executorInstances": "3",
            "executorMemory": "1536m",
            "executorCores": "1"
        }
    }
    ...
}
```


Sie können einen beliebigen JSON-Format-Editor verwenden (z. B. VS Code), um die Konfigurationsdateien für Ihre Clusterbereitstellung anzupassen. Verwenden Sie den Befehl **azdata bdc config**, um für diese Bearbeitungen Skripts zu erstellen und sie zu automatisieren. In diesem Artikel wird erläutert, wie Sie Big-Data-Clusterbereitstellungen konfigurieren, indem Sie Bereitstellungskonfigurationsdateien ändern. Er enthält Beispiele zum Ändern der Konfiguration für verschiedene Szenarios. Weitere Informationen zur Verwendung von Konfigurationsdateien in Bereitstellungen finden Sie im [Leitfaden zur Bereitstellung](deployment-guidance.md#configfile).

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Installieren Sie azdata](deploy-install-azdata.md).

- Bei jedem der Beispiele in diesem Abschnitt wird davon ausgegangen, dass Sie eine Kopie einer der Standardkonfigurationen erstellt haben. Weitere Informationen finden Sie unter [Create a custom configuration (Erstellen einer benutzerdefinierten Konfiguration)](deployment-guidance.md#customconfig). Der folgende Befehl erstellt z. b. ein Verzeichnis `custom` mit dem Namen, das zwei JSON-Bereitstellungs Konfigurationsdateien, **BDC. JSON** und **Control. JSON**, basierend auf der Standardkonfiguration **AKS-dev-Test** enthält:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

## <a id="clustername"></a> Ändern von Clusternnamen

Der Clustername entspricht dem Namen des Big-Data-Clusters und dem Kubernetes-Namespace, der bei der Bereitstellung erstellt wird. Sie wird im folgenden Teil der Bereitstellungs Konfigurationsdatei " **BDC. JSON** " angegeben:

```json
"metadata": {
    "kind": "BigDataCluster",
    "name": "mssql-cluster"
},
```

Der folgende Befehl sendet ein Schlüssel-Wert-Paar an den **--json-values**-Parameter, um den Big-Data-Clusternamen in **test-cluster** zu ändern:

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "metadata.name=test-cluster"
```

> [!IMPORTANT]
> Der Name Ihres Big-Data-Clusters darf nur alphanumerische Zeichen (Kleinbuchstaben) und keine Leerzeichen enthalten. Alle Kubernetes-Artefakte (Container, Pods, zustandsbehaftete Sets, Dienste) für den Cluster werden in einem Namespace mit dem gleichen Namen wie der angegebene Clustername erstellt.

## <a id="ports"></a> Aktualisieren von Endpunktports

Endpunkte werden für den Controller in der **Datei "Control. JSON** " und für das Gateway und SQL Server Master Instanz in den entsprechenden Abschnitten in " **BDC. JSON**" definiert. Der folgende Teil der Konfigurationsdatei **control.json** zeigt die Endpunktdefinitionen für den Controller an:

```json
{
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
}
```

Im folgenden Beispiel wird das Inline-JSON-Format verwendet, um den Port für den **Controller**-Endpunkt zu ändern:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.endpoints[?(@.name==""Controller"")].port=30000"
```

## <a id="replicas"></a> Konfigurieren von Poolreplikaten

Die Konfigurationen der einzelnen Ressourcen, z. b. der Speicherpool, werden in der Konfigurationsdatei **BDC. JSON** definiert. Der folgende Teil von " **BDC. JSON** " zeigt beispielsweise eine **Storage-0-** Ressourcendefinition:

```json
"storage-0": {
    "metadata": {
        "kind": "Pool",
        "name": "default"
    },
    "spec": {
        "type": "Storage",
        "replicas": 2,
        "settings": {
            "spark": {
                "driverMemory": "2g",
                "driverCores": "1",
                "executorInstances": "3",
                "executorMemory": "1536m",
                "executorCores": "1"
            }
        }
    }
}
```

Sie können die Anzahl der Instanzen in einem Pool konfigurieren, indem Sie den **Replikate**-Wert für die einzelnen Pools ändern. Im folgenden Beispiel wird das Inline-JSON-Format verwendet, um diese Werte für die Speicher- und Datenpools in `10` bzw. `4` zu ändern:

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.storage-0.spec.replicas=10"
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.data-0.spec.replicas=4"
```

## <a id="storage"></a> Konfigurieren des Speichers

Sie können auch die Speicherklasse und die Merkmale ändern, die für die einzelnen Pools verwendet werden. Im folgenden Beispiel wird eine benutzerdefinierte Speicher Klasse zu den Speicher-und Datenpools zugewiesen und die Größe des Anspruchs für persistente Volumes zum Speichern von Daten auf 500 GB für HDFS (Speicherpool) und 100 GB für den Daten Pool aktualisiert. Erstellen Sie zuerst eine „patch.json“-Datei (wie unten beschrieben), die zusätzlich zu *Typ* und *Replikaten* den neuen *Speicher*-Abschnitt enthält.

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "500Gi",
            "className": "myHDFSStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myHDFSStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.data-0.spec",
      "value": {
        "type": "Data",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "100Gi",
            "className": "myDataStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myDataStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    }
  ]
}
```

Anschließend können Sie den Befehl **azdata BDC config Patch** zum Aktualisieren der Konfigurationsdatei **BDC. JSON** verwenden.
```bash
azdata bdc config patch --config-file custom/bdc.json --patch ./patch.json
```

> [!NOTE]
> Eine auf **kubeadm-dev-test** basierende Konfigurationsdatei besitzt keine Speicherdefinition für die einzelnen Pools, aber Sie können sie mit dem obigen Prozess bei Bedarf hinzufügen.

Weitere Informationen zur Speicherkonfiguration finden Sie unter [Datenpersistenz mit Big-Data-Cluster für SQL Server in Kubernetes](concept-data-persistence.md).

## <a id="sparkstorage"></a> Konfigurieren von Speicherpools ohne Spark

Sie können die Speicherpools auch so konfigurieren, dass sie ohne Spark ausgeführt werden, und einen separaten Spark-Pool erstellen. Dies ermöglicht es Ihnen, Spark-Computeleistung unabhängig vom Speicher zu skalieren. Informationen zum Konfigurieren des Spark-Pools finden Sie im [JSON-Patchdateibeispiel](#jsonpatch) am Ende dieses Artikels.


Standardmäßig ist die Einstellung " **includespark** " für die Speicherpool Ressource auf "true" festgelegt, sodass Sie das Feld " **includespark** " in der Speicherkonfiguration bearbeiten müssen, um Änderungen vorzunehmen. Der folgende Befehl zeigt, wie dieser Wert mithilfe von Inline-JSON bearbeitet wird.

```bash
azdata bdc config replace --config-file custom/bdc.json --json-values "$.spec.resources.storage-0.spec.settings.spark.includeSpark=false"
```

## <a id="podplacement"></a> Konfigurieren von Pod-Platzierungen mit Kubernetes-Bezeichnungen

Sie können Pod-Platzierungen auf Kubernetes-Knoten steuern, die über bestimmten Ressourcen verfügen, um verschiedene Arten von Arbeitsauslastungsanforderungen zu erfüllen. Beispielsweise können Sie sicherstellen, dass die Speicherpool-ressourcenpods auf Knoten mit mehr Speicherplatz oder SQL Server Master Instanzen in Knoten platziert werden, die über höhere CPU-und Arbeitsspeicher Ressourcen verfügen. In diesem Fall erstellen Sie zuerst einen heterogenen Kubernetes-Cluster mit unterschiedlichen Hardwaretypen. Anschließend nehmen Sie die entsprechende [Zuweisung von Knotenbezeichnungen](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/) vor. Zum Zeitpunkt der Bereitstellung des Big-Data-Clusters können Sie in der Konfigurationsdatei für die Clusterbereitstellung dieselben Bezeichnungen auf Poolebene angeben. Kubernetes kümmert sich dann um die Affinität der Pods auf Knoten, die den angegebenen Bezeichnungen entsprechen. Der spezifische Bezeichnungs Schlüssel, der den Knoten im kubernetes-Cluster hinzugefügt werden muss, ist **MSSQL-Cluster-Wide**. Der Wert dieser Bezeichnung kann jede beliebige Zeichenfolge sein, die Sie auswählen.

Im folgenden Beispiel wird gezeigt, wie Sie eine benutzerdefinierte Konfigurationsdatei bearbeiten, um eine Knoten Bezeichnungs Einstellung für die SQL Server Master Instanz, den computepool, den Daten Pool & Speicherpools einzuschließen. Es gibt keinen *noschabel* -Schlüssel in den integrierten Konfigurationen, sodass Sie entweder manuell eine benutzerdefinierte Konfigurationsdatei bearbeiten oder eine Patchdatei erstellen und auf die benutzerdefinierte Konfigurationsdatei anwenden müssen. Der SQL Server Master Instanz-Pod wird auf einem Knoten bereitgestellt, der eine Bezeichnung " **MSSQL-Cluster-Wide** " mit dem Wert " **BDC-Master**" enthält. Der computepool und die Daten Pool-Pods werden auf Knoten bereitgestellt, die eine Bezeichnung " **MSSQL-Cluster-Wide** " mit dem Wert " **BDC-SQL**" enthalten. Die Speicher Pool-Pods werden auf Knoten bereitgestellt, die eine Bezeichnung " **MSSQL-Cluster-Wide** " mit dem Wert " **BDC-Storage**" enthalten.

Erstellen Sie in Ihrem aktuellen Verzeichnis eine Datei mit dem Namen **patch.json** und dem folgenden Inhalt:

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.master.spec",
      "value": {
        "type": "Master",
        "replicas": 1,
        "endpoints": [
          {
            "name": "Master",
            "serviceType": "NodePort",
            "port": 31433
          }
        ],
        "settings": {
          "sql": {
            "hadr.enabled": "false"
          }
        },
        "nodeLabel": "bdc-master"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.compute-0.spec",
      "value": {
        "type": "Compute",
        "replicas": 1,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.data-0.spec",
      "value": {
        "type": "Data",
        "replicas": 2,
        "nodeLabel": "bdc-sql"
      }
    },
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 3,
        "nodeLabel": "bdc-storage",
        "settings": {
          "spark": {
            "includeSpark": "true"
          }
        }
      }
    }
  ]
}
```

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
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

- Aktualisiert die Pool Speichereinstellungen für den Speicherpool in **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.resources.storage-0.spec",
      "value": {
        "type": "Storage",
        "replicas": 2,
        "storage": {
          "data": {
            "size": "100Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          },
          "logs": {
            "size": "32Gi",
            "className": "myStorageClass",
            "accessMode": "ReadWriteOnce"
          }
        }
      }
    }
  ]
}
```

- Aktualisiert die Spark-Einstellungen für den Speicherpool in **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec.services.spark.settings",
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

- Erstellt einen Spark-Pool mit 2 Instanzen in **BDC. JSON**.
```json
{
  "patch": [
    {
      "op": "add",
      "path": "spec.resources.spark-0",
      "value": {
        "metadata": {
          "kind": "Pool",
          "name": "default"
        },
        "spec": {
          "type": "Spark",
          "replicas": 2
        }
      }
    },
    {
      "op": "add",
      "path": "spec.services.spark.resources/-",
      "value": "spark-0"
    },
    {
      "op": "add",
      "path": "spec.services.hdfs.resources/-",
      "value": "spark-0"
    },
    {
      "op": "add",
      "path": "spec.services.spark.settings",
      "value": {
        "DriverMemory": "2g",
        "DriverCores": "1",
        "ExecutorInstances": "2",
        "ExecutorMemory": "2g",
        "ExecutorCores": "1"
      }
    }
  ]
}
```

> [!TIP]
> Weitere Informationen zur Struktur und zu den Optionen zum Ändern einer Bereitstellungskonfigurationsdatei finden Sie unter [Referenz zur Bereitstellungskonfigurationsdatei für Big-Data-Cluster](reference-deployment-config.md).

Verwenden Sie **azdata bdc config**-Befehle, um die Änderungen in der JSON-Patchdatei anzuwenden. Im folgenden Beispiel wird die Datei **Patch. JSON** auf eine Ziel Bereitstellungs Konfigurationsdatei " **Custom/BDC. JSON**" angewendet.

```bash
azdata bdc config patch --config-file custom/bdc.json --patch-file ./patch.json
```

## <a name="disable-elasticsearch-to-run-in-privileged-mode"></a>Deaktivieren von elasticsearch für die Durchführung im privilegierten Modus
Standardmäßig wird der elasticsearch-Container in Big Data Cluster im Berechtigungs Modus ausgeführt. Dadurch wird sichergestellt, dass der Container zur Initialisierung des Containers über ausreichende Berechtigungen verfügt, um eine Einstellung auf dem Host zu aktualisieren, wenn eine höhere Menge an Protokollen von elasticsearch verarbeitet wird. Weitere Informationen zu diesem Thema finden Sie in [diesem Artikel](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html). 

Um den Container, der elasticsearch ausführt, für die Ausführung im privilegierten Modus zu deaktivieren, müssen Sie den Abschnitt " **Einstellungen** " in der **Datei "Control. JSON** " aktualisieren und den Wert von " **VM. Max _map_count** " auf " **-1**" festlegen. Im folgenden finden Sie ein Beispiel dafür, wie dieser Abschnitt aussehen würde:
```json
"settings": {
    "ElasticSearch": {
        "vm.max_map_count": "-1"
      }
}
```

Sie können die Datei " **Control. JSON** " Bearbeiten und den obigen Abschnitt der **Spezifikation**hinzufügen. Sie können aber auch eine Patchdatei **elasticsearch-Patch. JSON** wie unten beschrieben erstellen und die Datei " **config. JSON** " mithilfe der **azdata** CLI Patchen:

```json
{
  "patch": [
    {
      "op": "replace",
      "path": "spec",
      "value": {
        "docker": {
            "registry": "mcr.microsoft.com",
            "repository": "mssql/bdc",
            "imageTag": "2019-RC1-ubuntu",
            "imagePullPolicy": "Always"
        },
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
        ],
        "settings": {
            "ElasticSearch": {
                "vm.max_map_count": "-1"
             }
        }
       }
    }
  ]
}
```

Führen Sie diesen Befehl aus, um die Konfigurationsdatei zu patchen:
```
azdata bdc config patch --config-file control.json --patch-file elasticsearch-patch.json
```

> [!IMPORTANT]
> Es wird empfohlen, die **max_map_count** -Einstellung manuell auf jedem Host im Kubernetes-Cluster manuell zu aktualisieren, gemäß den Anweisungen in [diesem Artikel](https://www.elastic.co/guide/en/elasticsearch/reference/current/vm-max-map-count.html).
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Verwenden von Konfigurationsdateien in Big Data Cluster Bereitstellungen finden [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ](deployment-guidance.md#configfile)Sie unter Bereitstellen von auf Kubernetes.
