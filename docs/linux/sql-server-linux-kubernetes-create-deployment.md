---
title: Erstellen von Bereitstellungsskripts für SQL Server AlwaysOn-Verfügbarkeitsgruppe in Kubernetes
description: In diesem Artikel wird erläutert, wie zum Erstellen von Bereitstellungsskripts für eine SQL Server AlwaysOn-Verfügbarkeitsgruppe in Kubernetes
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 70a83efa128d8d58776907541fef9d6888af51e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705674"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>Erstellen von Bereitstellungsskripts für SQL Server AlwaysOn-Verfügbarkeitsgruppe

Dieser Artikel beschreibt, wie Sie eine verfügbarkeitsgruppe für einen Kubernetes-Cluster in einem einzigen Befehl mit einer Beispiel-Bereitstellungsskript bereitstellen. `deploy-ag.py` ist ein Python-Skript, erstellt die `.yaml` -Dateien für den Cluster und kann auf einen Kubernetes-Cluster anwenden.

Herunterladen die Dateien aus Datei [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script).

## <a name="before-you-start"></a>Vorbereitungen

Installieren Sie die folgenden Tools auf Ihrer Arbeitsstation.

* [Python](https://www.python.org/downloads/) (3.5 oder 3.6)
* [PyYAML](https://pyyaml.org/) -Python-Pakete
* [Kubernetes-Client](https://github.com/kubernetes-client/python) -Python-Paket

Fügen Sie Python-Pfade zu den Umgebungsvariablen (für Windows).

### <a name="install-the-required-components"></a>Installieren der erforderlichen Komponenten

Im folgende Beispiel oben werden die PyYAML und Kubernetes-Client-Pakete für Python installiert.

Nach der Installation von Python herunterladen Sie und extrahieren Sie den Beispielordner. 

Führen Sie den folgenden Befehl, um die erforderlichen Dateien zu konfigurieren. Ersetzen Sie dies `<path>` durch den Speicherort der Beispieldateien extrahiert.

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>Cluster erstellen und Herunterladen der Datei "App.config"

Das folgende Beispiel erstellt den Cluster in Azure Kubernetes Service (AKS).

Bevor Sie das Skript ausführen, aktualisieren Sie die Werte in spitzen Klammern - `<>`.

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>Verfügbarkeitsgruppen erfordern Kubernetes-Version 1.11.0 oder höher. Im Beispiel wird die 1.11.1.

## <a name="run-the-deployment-script"></a>Ausführen des Bereitstellungsskripts

Die folgenden Beispiele veranschaulichen, wie Sie ausführen `deploy-ag.py`.

### <a name="help"></a>Help

```cmd
python ./deploy-ag.py --help
```

* **usage**: `deploy-ag.py [-h] {deploy | failover} ...`
* **Optionale Argumente**:
  * `-h, --help` Zeigen Sie diese hilfemeldung an und beenden
* **subcommands**:
  * Aktionen auf k8s Agent {bereitstellen | Failover}

  `deploy`

   Bereitstellen Sie eine Reihe von SQL-Server in einer Verfügbarkeitsgruppe

  `failover`

   Führen Sie ein Failover zu einem Zielreplikat.

### <a name="deploy-help"></a>Bereitstellen von Hilfe

```cmd
python ./deploy-ag.py deploy --help
```

* **usage**:

  ```
  python ./deploy-ag.py deploy [-h] [--verbose] [--ag AG] [-n NAMESPACE]
    [--dry-run] [-s SQL_SERVERS [SQL_SERVERS ...]]
    [-p SA_PASSWORD] [-e {ON_PREM,AKS}]
    [--skip-create-namespace]
  ```

  Bereitstellen von SQL Server und k8s-Agents in namespace(AG name)

* **Optionale Argumente**:
  
  `-h, --help`
  
  Zeigen Sie diese hilfemeldung an und beenden
  
  `--verbose, -v`
  
  Ausführlichkeit der Ausgabe
  
  `--ag AG`
  
  Der Name der Verfügbarkeitsgruppe. Default=ag1
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  Der Name des k8s-Namespace. Der Standardwert ist AG-Namens, wenn nicht angegeben.

  `--dry-run`
  
  Erstellen Sie die Manifeste, aber nicht angewendet werden.
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  Namen von Instanzen von SQL Server Standard (bis zu 5, getrennt durch Leerzeichen) = ['"MSSQL1"', 'mssql2', 'mssql3']
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  SA-Kennwort. Default='SAPassword2018'
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  Überspringen Sie die Namespace-Erstellung.

### <a name="failover-help"></a>Failover-Hilfe

```cmd
python ./deploy-ag.py failover --help
```
* **usage**: 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  Ein manuelles failover

* **positionelle Argumente**: `target_replica`

  Name des Ziel-SQL Server-Replikat für failover

* **Optionale Argumente**:

  `-h, --help`
  
  Zeigen Sie diese hilfemeldung an und beenden

  `--verbose, -v`
  
  Ausführlichkeit der Ausgabe

  `--ag AG`
  
  Der Name der Verfügbarkeitsgruppe. Default=ag1

  `--namespace NAMESPACE`

  Der Name des k8s-Namespace. Der Standardwert ist AG-Namens, wenn nicht angegeben

  `--dry-run`
  
  Erstellen, aber die Manifeste werden nicht angewendet.

### <a name="create-the-manifests---dont-apply"></a>Erstellen Sie die Manifeste: nicht anwendbar

Das folgende Skript erstellt die Manifestdateien jedoch nicht angewendet werden.

```cmd
python ./deploy-ag.py deploy --dry-run
```

Das folgende Beispiel erstellt die Manifeste für eine verfügbarkeitsgruppe unter Namespace `AG1` mit drei Replikaten. Ersetzen Sie vor dem Ausführen des Skripts `<MyC0m91exP@55w0r!>` mit einem komplexen Kennwort.

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

Der vorherige Befehl wird das Beispielverzeichnis der Yaml-Dateien generiert.

In diesem Fall zeigt die Ausgabe des Befehls, wo die Manifesten-Dateien erstellt werden.

![Ausgabe des Skripts](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>Die Manifeste erstellen und anwenden

Das folgende Beispiel erstellt die Manifeste für eine verfügbarkeitsgruppe unter Namespace `ag1` mit drei Replikaten und wendet sie auf den Kubernetes-Cluster. Der Cluster wird dann die verfügbarkeitsgruppe erstellt. Ersetzen Sie vor dem Ausführen des Skripts `<MyC0m91exP@55w0r!>` mit einem komplexen Kennwort.

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

Nachdem das Skript abgeschlossen ist, erstellt der Kubernetes-Operator den Speicher, SQL Server-Instanzen, die Load Balancer-Dienste. Sie können überwachen, die Bereitstellung mit [Kubernetes-Dashboard](https://docs.microsoft.com/azure/aks/kubernetes-dashboard).

Nachdem der Kubernetes die SQL Server-Container erstellt hat:

1. [Herstellen einer mit](sql-server-linux-kubernetes-connect.md) auf eine SQL Server-Instanz im Cluster.

1. Erstellen einer Datenbank

1. Führen Sie eine vollständige Sicherung der Datenbank, die die Protokollkette zu starten.

1. Fügen Sie die Datenbank der verfügbarkeitsgruppe hinzu.

Die verfügbarkeitsgruppe wird erstellt, mit automatischem seeding, damit SQL Server auf die entsprechenden Replikate automatisch die sekundären Datenbanken erstellt werden.

### <a name="manually-failover"></a>Ein manuelles failover

Im folgenden Beispiel wird ein Failover des primären Replikats.

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>Nächste Schritte

[SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-ag-kubernetes.md)
