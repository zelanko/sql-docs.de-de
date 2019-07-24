---
title: Offline bereitstellen
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie eine Offline Bereitstellung einer SQL Server Big Data-Cluster ausführen.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cd8b3128fc11037a5ade494813611d473c995f8f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419370"
---
# <a name="perform-an-offline-deployment-of-a-sql-server-big-data-cluster"></a>Ausführen einer Offline Bereitstellung eines SQL Server Big Data Clusters

In diesem Artikel wird beschrieben, wie Sie eine Offline Bereitstellung einer SQL Server 2019 Big Data Cluster (Vorschauversion) ausführen. Big Data-Cluster müssen Zugriff auf ein docker-Repository haben, von dem Sie Container Images abrufen können. Eine Offline Installation ist eine, in der die erforderlichen Images in einem privaten docker-Repository abgelegt werden. Dieses private Repository wird dann als Image Quelle für eine neue Bereitstellung verwendet.

## <a name="prerequisites"></a>Vorraussetzungen

- Docker-Engine 1.8 und höher auf unterstütztem Linux-Betriebssystem oder Docker für Mac bzw. Windows. Weitere Informationen finden Sie unter [Install Docker (Installieren von Docker)](https://docs.docker.com/engine/installation/).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="load-images-into-a-private-repository"></a>Laden von Bildern in ein privates Repository

In den folgenden Schritten wird beschrieben, wie Sie die Big Data Cluster Container Images aus dem Microsoft-Repository abrufen und anschließend per Push in Ihr privates Repository übersetzen.

> [!TIP]
> In den folgenden Schritten wird der Prozess erläutert. Um die Aufgabe zu vereinfachen, können Sie jedoch das [automatisierte Skript](#automated) verwenden, anstatt diese Befehle manuell auszuführen.

1. Rufen Sie die Big Data Cluster Container Images ab, indem Sie den folgenden Befehl wiederholen. Ersetzen `<SOURCE_IMAGE_NAME>` Sie dies durch jeden [Bildnamen](#images). Ersetzen `<SOURCE_DOCKER_TAG>` Sie dies durch das Tag für die Big Data Cluster Version, z. b. **2019-CTP 3.2-Ubuntu**.  

   ```PowerShell
   docker pull mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG>
   ```

1. Melden Sie sich bei der privaten docker-Ziel Registrierung an.

   ```PowerShell
   docker login <TARGET_DOCKER_REGISTRY> -u <TARGET_DOCKER_USERNAME> -p <TARGET_DOCKER_PASSWORD>
   ```

1. Markieren Sie die lokalen Images mit dem folgenden Befehl für jedes Image:

   ```PowerShell
   docker tag mcr.microsoft.com/mssql/bdc/<SOURCE_IMAGE_NAME>:<SOURCE_DOCKER_TAG> <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

1. Übersetzen Sie die lokalen Images per Push in das private docker-Repository:

   ```PowerShell
   docker push <TARGET_DOCKER_REGISTRY>/<TARGET_DOCKER_REPOSITORY>/<SOURCE_IMAGE_NAME>:<TARGET_DOCKER_TAG>
   ```

### <a id="images"></a>Big Data-Cluster Container Images

Die folgenden Big Data Cluster Container Images sind für eine Offline Installation erforderlich:

 - **mssql-appdeploy-init**
 - **mssql-monitor-fluentbit**
 - **mssql-monitor-collectd**
 - **mssql-server-data**
 - **mssql-hadoop**
 - **mssql-monitor-elasticsearch**
 - **mssql-monitor-influxdb**
 - **mssql-security-knox**
 - **mssql-mlserver-r-runtime**
 - **mssql-mlserver-py-runtime**
 - **mssql-controller**
 - **mssql-server-controller**
 - **mssql-monitor-grafana**
 - **mssql-monitor-kibana**
 - **mssql-service-proxy**
 - **mssql-app-service-proxy**
 - **mssql-ssis-app-runtime**
 - **mssql-monitor-telegraf**
 - **mssql-mleap-serving-runtime**
 - **MSSQL-Sicherheit-Support**

## <a id="automated"></a>Automatisiertes Skript

Sie können ein automatisiertes Python-Skript verwenden, das automatisch alle benötigten Container Images per Pull abruft und Sie in ein privates Repository überträgt.

> [!NOTE]
> Python ist eine Voraussetzung für die Verwendung des Skripts. Weitere Informationen zum Installieren von Python finden Sie in der [Python-Dokumentation](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Laden Sie das Skript von bash oder PowerShell mit **curl**herunter:

   ```PowerShell
   curl -o push-bdc-images-to-custom-private-repo.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/offline/push-bdc-images-to-custom-private-repo.py"
   ```

1. Führen Sie dann das Skript mit einem der folgenden Befehle aus:

   **Windows:**

   ```PowerShell
   python deploy-sql-big-data-aks.py
   ```

   **Linux**

   ```bash
   sudo python deploy-sql-big-data-aks.py
   ```

1. Befolgen Sie die Anweisungen zum Eingeben des Microsoft-Repository und ihrer private Repository-Informationen. Nachdem das Skript abgeschlossen wurde, sollten sich alle erforderlichen Images in Ihrem privaten Repository befinden.

## <a name="install-tools-offline"></a>Tools Offline installieren

Big Data-Cluster Bereitstellungen erfordern mehrere Tools, einschließlich **python**, **azdata**und **kubectl**. Führen Sie die folgenden Schritte aus, um diese Tools auf einem Offline Server zu installieren.

### <a id="python"></a>Python Offline installieren

1. Laden Sie auf einem Computer mit Internet Zugriff eine der folgenden komprimierten Dateien herunter, die python enthalten:

   | Betriebssystem | Herunterladen |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Kopieren Sie die komprimierte Datei auf den Zielcomputer, und extrahieren Sie Sie in einen Ordner Ihrer Wahl.

1. Führen `installLocalPythonPackages.bat` Sie in diesem Ordner nur für Windows aus, und übergeben Sie den vollständigen Pfad an denselben Ordner wie einen-Parameter.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

### <a id="azdata"></a>Installieren von azdata offline

1. Führen Sie auf einem Computer mit Internet Zugriff und [python](https://wiki.python.org/moin/BeginnersGuide/Download)den folgenden Befehl aus, um alle **azdata** -Pakete in den aktuellen Ordner herunterzuladen.

   ```PowerShell
   pip download -r https://aka.ms/azdata
   ```

1. Kopieren Sie die heruntergeladenen Pakete und die Datei " **Requirements. txt** " auf den Zielcomputer.

1. Führen Sie den folgenden Befehl auf dem Zielcomputer aus, und geben Sie dabei den Ordner an, in den Sie die vorherigen Dateien kopiert haben.

   ```PowerShell
   pip install --no-index --find-links <path-to-packages> -r <path-to-requirements.txt>
   ```

### <a id="kubectl"></a>Installieren von kubectl offline

Führen Sie die folgenden Schritte aus, um **kubectl** auf einem Offline Computer zu installieren.

1. Verwenden Sie **curl** , um **kubectl** in einen Ordner Ihrer Wahl herunterzuladen. Weitere Informationen finden Sie unter [Installieren von kubectl Binary mithilfe von curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl).

1. Kopieren Sie den Ordner auf den Zielcomputer.

## <a name="deploy-from-private-repository"></a>Aus privatem Repository bereitstellen

Verwenden Sie zum Bereitstellen über das private Repository die im [Bereitstellungs Handbuch](deployment-guidance.md)beschriebenen Schritte. verwenden Sie jedoch eine benutzerdefinierte Bereitstellungs Konfigurationsdatei, die Ihre privaten docker-Repository-Informationen angibt. Die folgenden **azdata** -Befehle veranschaulichen, wie die Docker-Einstellungen in einer benutzerdefinierten Bereitstellungs Konfigurationsdatei namens " **Control. JSON**" geändert werden:

```bash
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.repository=<your-docker-repository>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.registry=<your-docker-registry>"
azdata bdc config replace --config-file custom/control.json --json-values "$.spec.docker.imageTag=<your-docker-image-tag>"
```

In der Bereitstellung werden Sie aufgefordert, den docker-Benutzernamen und das Kennwort einzugeben, oder Sie können Sie in den Umgebungsvariablen **DOCKER_USERNAME** und **DOCKER_PASSWORD** angeben.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Cluster Bereitstellungen finden Sie unter Bereitstellen [SQL Server Big Data Clustern auf Kubernetes](deployment-guidance.md).
