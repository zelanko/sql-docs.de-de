---
title: Offlinebereitstellung von
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie eine offline-Bereitstellung von einer SQL Server-big Data-Cluster ausführen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 49c96300792adfefa32152ec73911ba32fac47ee
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994020"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Führen Sie eine offline-Bereitstellung von einer SQL Server-big Data-cluster

Dieser Artikel beschreibt, wie eine offline-Bereitstellung von big Data-Cluster (Vorschau) eine SQL Server-2019 ausgeführt wird. Big Data-Cluster, müssen Zugriff auf die containerimages per Pull in einem Docker-Repository aus dem haben. Eine offline-Installation ist eine bei der die erforderlichen Bilder in einer privaten Docker-Repository platziert sind. Diese private Repository wird dann als Bildquelle für eine neue Bereitstellung verwendet.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Docker-Engine 1.8 und höher auf unterstütztem Linux-Betriebssystem oder Docker für Mac bzw. Windows. Weitere Informationen finden Sie unter [Install Docker (Installieren von Docker)](https://docs.docker.com/engine/installation/).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>Laden von Bildern in einem privaten repository

Die folgenden Schritte beschreiben, wie Sie zum Abrufen von containerimages aus dem Microsoft-Repository für big Data-Cluster und und drücken sie in Ihrem privaten Repository.

> [!TIP]
> Die folgenden Schritte erläutern den Prozess. Um die Aufgabe zu vereinfachen, Sie können jedoch die [automatisiertes Skript](#automated) statt diese Befehle manuell ausführen.

1. Melden Sie sich zunächst an den Microsoft-Docker-Registrierung mit dem **Docker Login** Befehl. Verwenden Sie den Benutzernamen und das Kennwort, die von Microsoft bereitgestellt, um Sie als Teil der Early Adoption Program.

   ```PowerShell
   docker login private-repo.microsoft.com -u  <SOURCE_DOCKER_USERNAME> -p <SOURCE_DOCKER_PASSWORD>
   ```

   > [!TIP]
   > Diese Befehle verwenden Sie PowerShell als Beispiel, jedoch können Sie sie ausführen, Cmd, Bash oder jeder Befehlsshell, Docker ausführen können. Unter Linux hinzufügen `sudo` für jeden Befehl.

1. Laden Sie die big Data-Cluster containerimages, indem Sie den folgenden Befehl wiederholen. Ersetzen Sie dies `<SOURCE_IMAGE_NAME>` mit jedem [ImageName](#images). Ersetzen Sie dies `<SOURCE_DOCKER_TAG>` mit dem Tag für die big Data-cluster Version, z. B. **CTP 3.0**.  

   ```PowerShell
   docker pull private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Melden Sie sich an die Ziel-Private Docker-Registrierung.

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. Kennzeichnen Sie die lokalen Images mit dem folgenden Befehl für jedes Image:

   ```PowerShell
   docker tag private-repo.microsoft.com/mssql-private-preview/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. Übertragen Sie die lokalen Images, auf das private Docker-Repository:

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a> Big Data-Cluster-containerimages

Die folgenden big Data-Cluster-containerimages sind für eine offline-Installation erforderlich:

 - **mssql-appdeploy-init**
 - **mssql-monitor-fluentbit**
 - **mssql-monitor-collectd**
 - **mssql-server-data**
 - **mssql-hadoop**
 - **mssql-java**
 - **mssql-mlservices-pythonserver**
 - **mssql-mlservices-rserver**
 - **mssql-monitor-elasticsearch**
 - **mssql-monitor-influxdb**
 - **mssql-security-knox**
 - **mssql-mlserver-r-runtime**
 - **mssql-mlserver-py-runtime**
 - **mssql-controller**
 - **mssql-portal**
 - **mssql-server-controller**
 - **mssql-monitor-grafana**
 - **mssql-monitor-kibana**
 - **mssql-service-proxy**
 - **mssql-app-service-proxy**
 - **mssql-ssis-app-runtime**
 - **mssql-monitor-telegraf**

## <a id="automated"></a> Automatisiertes Skript

Sie können einen automatisierten Python-Skript verwenden, die automatisch alle erforderlichen containerimages zu Pullen und pushen sie in einem privaten Repository.

> [!NOTE]
> Python ist eine Voraussetzung für die Verwendung des Skripts. Weitere Informationen zum Installieren von Python finden Sie unter den [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

1. In den nachfolgenden bash- oder PowerShell, laden Sie das Skript mit **curl**:

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. Führen Sie das Skript mit einem der folgenden Befehle aus:

   **Windows:**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux:**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Führen Sie die Anweisungen für die Eingabe der Microsoft-Repository und Ihrem privaten Repository-Informationen. Nach Abschluss des Skripts alle erforderlichen Bilder in Ihrem privaten Repository befinden soll.

## <a name="install-tools-offline"></a>Installieren von offline-tools

Big Data-Cluster-Bereitstellungen müssen mehrere Tools, einschließlich **Python**, **Mssqlctl**, und **"kubectl"**. Verwenden Sie die folgenden Schritte aus, um diese Tools auf einem offline-Server zu installieren.

### <a id="python"></a> Installieren Sie Python offline

1. Laden Sie eine der folgenden komprimierte Dateien mit Python an, auf einem Computer mit Internetzugriff:

   | Betriebssystem | Herunterladen |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Kopieren Sie die komprimierte Datei auf den Zielcomputer und extrahieren Sie es in einen Ordner Ihrer Wahl.

1. Führen Sie bei Windows nur `installLocalPythonPackages.bat` aus diesem Ordner, und übergeben Sie den vollständigen Pfad in den gleichen Ordner als Parameter.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

### <a id="mssqlctl"></a> Mssqlctl offline installieren

1. Auf einem Computer mit Internetzugriff und [Python](https://wiki.python.org/moin/BeginnersGuide/Download), führen Sie den folgenden Befehl auf alle deaktiviert Herunterladen der **Mssqlctl** Pakete in das aktuelle Verzeichnis.

   ```PowerShell
   pip download -r https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt
   ```

1. Herunterladen der **"Requirements.txt"** Datei.

   ```PowerShell
   curl -o requirements.txt "https://private-repo.microsoft.com/python/ctp-2.3/mssqlctl/requirements.txt"
   ```

1. Kopieren Sie die heruntergeladenen Pakete und die **"Requirements.txt"** Datei auf den Zielcomputer.

1. Führen Sie den folgenden Befehl aus, auf dem Zielcomputer, die die Verwendung des Ordners, den Sie in der vorherigen Dateien kopiert.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a> Installieren von Kubectl offline

So installieren Sie **"kubectl"** auf einem Offlinecomputer, verwenden Sie die folgenden Schritte aus.

1. Verwendung **curl** herunterladen **"kubectl"** in einen Ordner Ihrer Wahl. Weitere Informationen finden Sie unter [Installieren von Kubectl-Binärdatei, die mithilfe von Curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl).

1. Kopieren Sie den Ordner, auf den Zielcomputer.

## <a name="deploy-from-private-repository"></a>Bereitstellen von einem privaten repository

Um über das private Repository bereitzustellen, verwenden Sie die Schritte in der [Bereitstellungshandbuch](deployment-guidance.md), aber verwenden Sie eine benutzerdefinierte Bereitstellungskonfigurationsdatei, die Ihre privaten Docker-Repository-Informationen angibt. Die folgenden **Mssqlctl** Befehle veranschaulichen das Ändern der Docker-Einstellungen in einer benutzerdefinierten Bereitstellungskonfigurationsdatei mit dem Namen **custom.json**:

```bash
mssqlctl cluster config section set -c custom.json -j "$.spec.controlPlane.spec.docker.repository=<your-docker-repository>"
mssqlctl cluster config section set -c custom.json -j "$.spec.controlPlane.spec.docker.registry=<your-docker-registry>"
mssqlctl cluster config section set -c custom.json -j "$.spec.controlPlane.spec.docker.imageTag=<your-docker-image-tag>"
```

Die Bereitstellung für Docker-Benutzername und Kennwort aufgefordert, oder Sie können angeben, in der **DOCKER_USERNAME** und **DOCKER_PASSWORD** Umgebungsvariablen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Bereitstellung von big Data-Cluster finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md).
