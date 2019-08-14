---
title: Erstellen von Bereitstellungsskripts für eine SQL Server Always On-Verfügbarkeitsgruppe auf Kubernetes
description: In diesem Artikel wird das Erstellen von Bereitstellungsskripts für eine SQL Server Always On-Verfügbarkeitsgruppe auf Kubernetes erläutert.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 181773a19e87c34a1931cae05f5a329aedbc1239
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68000132"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>Erstellen eines Bereitstellungsskripts für eine SQL Server Always On-Verfügbarkeitsgruppe

In diesem Artikel wird die Bereitstellung einer Verfügbarkeitsgruppe auf einem Kubernetes-Cluster in einem einzigen Befehl mit einem Beispielbereitstellungsskript beschrieben. `deploy-ag.py` ist ein Python-Skript, dass die `.yaml`-Dateien für den Cluster erstellt und auf einen Kubernetes-Cluster anwenden kann.

Laden Sie die Dateien von [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script) herunter.

## <a name="before-you-start"></a>Vorbereitungen

Installieren Sie die folgenden Tools auf Ihrer Arbeitsstation.

* [Python](https://www.python.org/downloads/) (3.5 oder 3.6)
* [PyYAML](https://pyyaml.org/) – Python-Pakete
* [Kubernetes-Client](https://github.com/kubernetes-client/python) – Python-Paket

Hinzufügen von Python-Pfaden zu den Umgebungsvariablen (für Windows).

### <a name="install-the-required-components"></a>Installieren der erforderlichen Komponenten

Im folgenden Beispiel werden die PyYAML- und Kubernetes-Client-Pakete für Python installiert.

Nachdem Sie Python installiert haben, müssen Sie den Beispielordner herunterladen und extrahieren. 

Führen Sie den folgenden Befehl aus, um die erforderlichen Dateien zu konfigurieren. Ersetzen Sie `<path>` durch den Speicherort der extrahierten Beispieldateien.

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>Erstellen des Clusters und Herunterladen der Konfigurationsdatei

Im folgenden Beispiel wird der Cluster in Azure Kubernetes Service (AKS) erstellt.

Aktualisieren Sie vor dem Ausführen des Skripts die Werte in spitzen Klammern – `<>`.

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>Für Verfügbarkeitsgruppen ist die Kubernetes-Version 1.11.0 oder höher erforderlich. Im Beispiel wird 1.11.1 verwendet.

## <a name="run-the-deployment-script"></a>Ausführen des Bereitstellungsskripts

Die folgenden Beispiele veranschaulichen die Ausführung von `deploy-ag.py`.

### <a name="help"></a>Hilfe

```cmd
python ./deploy-ag.py --help
```

* **Verwendung**: `deploy-ag.py [-h] {deploy | failover} ...`
* **optionale Argumente**:
  * `-h, --help` diese Hilfemeldung anzeigen und beenden
* **Unterbefehle**:
  * Aktionen am k8s-Agent {deploy | failover}

  `deploy`

   Bereitstellen eines Satzes von SQL Server-Instanzen in einer Verfügbarkeitsgruppe

  `failover`

   Ausführen eines Failovers zu einem Zielreplikat.

### <a name="deploy-help"></a>Bereitstellen von Hilfe

```cmd
python ./deploy-ag.py deploy --help
```

* **Verwendung**:

  ```
  python ./deploy-ag.py deploy [-h] [--verbose] [--ag AG] [-n NAMESPACE]
    [--dry-run] [-s SQL_SERVERS [SQL_SERVERS ...]]
    [-p SA_PASSWORD] [-e {ON_PREM,AKS}]
    [--skip-create-namespace]
  ```

  Bereitstellen von SQL Server und k8s-Agents im Namespace (Name der Verfügbarkeitsgruppe)

* **optionale Argumente**:
  
  `-h, --help`
  
  diese Hilfemeldung anzeigen und beenden
  
  `--verbose, -v`
  
  Ausführlichkeit der Ausgabe
  
  `--ag AG`
  
  Der Name der Verfügbarkeitsgruppe. Standard=ag1
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  Der Name des k8s-Namespace. Wenn nicht angegeben, wird standardmäßig der Name der Verfügbarkeitsgruppe verwendet.

  `--dry-run`
  
  Manifeste erstellen, aber nicht anwenden.
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  Namen von SQL Server-Instanzen (bis zu 5, getrennt durch Leerzeichen) Standard=['mssql1', 'mssql2', 'mssql3']
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  Systemadministratorkennwort. Standard='SAPassword2018'
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  Namespaceerstellung überspringen.

### <a name="failover-help"></a>Failoverhilfe

```cmd
python ./deploy-ag.py failover --help
```
* **Verwendung**: 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  Manuelles Failover

* **positionelles Argument**: `target_replica`

  Name des Ziel-SQL Server-Replikats für Failover

* **optionale Argumente**:

  `-h, --help`
  
  diese Hilfemeldung anzeigen und beenden

  `--verbose, -v`
  
  Ausführlichkeit der Ausgabe

  `--ag AG`
  
  Der Name der Verfügbarkeitsgruppe. Standard=ag1

  `--namespace NAMESPACE`

  Der Name des k8s-Namespace. Wenn nicht angegeben, wird standardmäßig der Name der Verfügbarkeitsgruppe verwendet.

  `--dry-run`
  
  Manifeste erstellen, aber nicht anwenden.

### <a name="create-the-manifests---dont-apply"></a>Erstellen der Manifeste – aber nicht anwenden

Mit dem folgenden Skript werden die Manifestdateien erstellt, aber nicht angewendet.

```cmd
python ./deploy-ag.py deploy --dry-run
```

Im folgenden Beispiel werden die Manifeste für eine Verfügbarkeitsgruppe unter Namespace `AG1` mit drei Replikaten erstellt. Ersetzen Sie `<MyC0m91exP@55w0r!>` vor dem Ausführen des Skripts durch ein komplexes Kennwort.

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

Der vorherige Befehl generiert das Beispielverzeichnis für YAML-Dateien.

In diesem Fall zeigt die Befehlsausgabe an, wo die Manifestdateien erstellt werden.

![Skriptausgabe](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>Erstellen der Manifeste und anwenden

Im folgenden Beispiel werden die Manifeste für eine Verfügbarkeitsgruppe unter Namespace `ag1` mit drei Replikaten erstellt und auf Ihren Kubernetes-Cluster angewendet. Der Cluster erstellt dann die Verfügbarkeitsgruppe. Ersetzen Sie `<MyC0m91exP@55w0r!>` vor dem Ausführen des Skripts durch ein komplexes Kennwort.

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

Nach Ausführung des Skripts erstellt der Kubernetes-Operator den Speicher, die SQL Server-Instanzen und die Lastenausgleichsdienste. Sie können die Bereitstellung mit dem [Kubernetes-Dashboard](https://docs.microsoft.com/azure/aks/kubernetes-dashboard) überwachen.

Nachdem Kubernetes die SQL Server-Container erstellt hat:

1. [Stellen Sie eine Verbindung](sql-server-linux-kubernetes-connect.md) mit einer SQL Server-Instanz im Cluster her.

1. Erstellen einer Datenbank

1. Beginnen Sie die Protokollkette mit einer vollständigen Sicherung der Datenbank.

1. Fügen Sie die Datenbank der Verfügbarkeitsgruppe hinzu.

Die Verfügbarkeitsgruppe wird mit automatischem Seeding erstellt, sodass SQL Server automatisch die sekundären Datenbanken auf den entsprechenden Replikaten erstellt.

### <a name="manually-failover"></a>Manuelles Failover

Im folgenden Beispiel wird ein Failover des primären Replikats ausgeführt.

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>Nächste Schritte

[SQL Server-Verfügbarkeitsgruppe in einem Kubernetes-Cluster](sql-server-ag-kubernetes.md)
