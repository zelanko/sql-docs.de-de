---
title: Hinweise zur Bereitstellung
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie SQL Server 2019 Big Data Cluster (Vorschauversion) auf Kubernetes bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e6f2eefd37c45753e3051722448b80d88712df26
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419419"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Bereitstellen von SQL Server Big Data Clustern auf Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server Big Data Cluster als docker-Container in einem Kubernetes-Cluster bereitgestellt wird. Dies ist eine Übersicht über die Setup-und Konfigurationsschritte:

- Richten Sie einen Kubernetes-Cluster auf einer einzelnen VM, einem Cluster mit virtuellen Computern oder in Azure Kubernetes Service (AKS) ein.
- Installieren Sie das Cluster Konfigurationstool **azdata** auf dem Client Computer.
- Stellen Sie eine SQL Server Big Data-Cluster in einem Kubernetes-Cluster bereit.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>Installieren von SQL Server 2019 Big Data Tools

Installieren Sie vor dem Bereitstellen eines SQL Server 2019 Big Data Cluster zunächst [die Big Data Tools](deploy-big-data-tools.md):

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019-Erweiterung**

## <a id="prereqs"></a>Kubernetes Voraussetzungen

SQL Server Big Data-Cluster benötigen mindestens Version 1.10 von mindestens v 1.10 für Server und Client (kubectl).

> [!NOTE]
> Beachten Sie, dass die Client-und Server Kubernetes Versionen innerhalb von + 1 oder-1 neben Version liegen sollten. Weitere Informationen finden Sie unter [Kubernetes Release Notes and Version rabw SKU Policy)](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a>Einrichten des Kubernetes-Clusters

Wenn Sie bereits über einen Kubernetes-Cluster verfügen, der die oben genannten Voraussetzungen erfüllt, können Sie direkt mit dem [Bereitstellungs Schritt fort](#deploy)fahren. In diesem Abschnitt wird ein grundlegendes Verständnis der Kubernetes-Konzepte vorausgesetzt.  Ausführliche Informationen zu Kubernetes finden Sie in der [Kubernetes-Dokumentation](https://kubernetes.io/docs/home).

Sie können Kubernetes auf drei Arten bereitstellen:

| Kubernetes bereitstellen auf: | Beschreibung | Link |
|---|---|---|
| **Azure Kubernetes Services (AKS)** | Einen verwalteten Kubernetes-Containerdienst in Azure. | [Anweisungen](deploy-on-aks.md) |
| **Mehrere Computer (kubeadm)** | Ein Kubernetes-Cluster, der auf physischen oder virtuellen Computern mithilfe von **kubeadm** bereitgestellt wird | [Anweisungen](deploy-with-kubeadm.md) |
| **Minikube** | Ein Kubernetes-Cluster mit einem einzelnen Knoten in einem virtuellen Computer. | [Anweisungen](deploy-on-minikube.md) |

> [!TIP]
> Ein python-Beispielskript, das sowohl AKS als auch einen SQL Server Big Data Cluster in einem Schritt bereitstellt [, finden Sie unter Schnellstart: Stellen Sie SQL Server Big Data-Cluster in Azure Kubernetes Service (](quickstart-big-data-cluster-deploy.md)AKS) bereit.

### <a name="verify-kubernetes-configuration"></a>Kubernetes-Konfiguration überprüfen

Führen Sie den Befehl **kubectl** aus, um die Cluster Konfiguration anzuzeigen. Stellen Sie sicher, dass kubectl auf den richtigen Cluster Kontext verweist.

```bash
kubectl config view
```

Nachdem Sie den Kubernetes-Cluster konfiguriert haben, können Sie mit der Bereitstellung eines neuen SQL Server Big Data Cluster fortfahren. Wenn Sie ein Upgrade von einer früheren Version durchführen, finden Sie weitere Informationen unter [Upgrade SQL Server Big Data Clusters](deployment-upgrade.md).

## <a id="deploy"></a>Bereitstellungs Übersicht

Die meisten Big Data Cluster Einstellungen werden in einer JSON-Bereitstellungs Konfigurationsdatei definiert. Sie können ein Standard Bereitstellungs Profil für AKS, `kubeadm`oder `minikube` verwenden, oder Sie können Ihre eigene Bereitstellungs Konfigurationsdatei für die Verwendung während des Setups anpassen. Aus Sicherheitsgründen werden Authentifizierungs Einstellungen über Umgebungsvariablen übermittelt.

In den folgenden Abschnitten finden Sie weitere Informationen zum Konfigurieren Ihrer Big Data Cluster Bereitstellungen sowie Beispiele für allgemeine Anpassungen. Außerdem können Sie die benutzerdefinierte Bereitstellungs Konfigurationsdatei jederzeit mithilfe eines Editors wie vs Code bearbeiten.

## <a id="configfile"></a>Standardkonfigurationen

Big Data-Cluster Bereitstellungs Optionen sind in JSON-Konfigurationsdateien definiert. Es gibt drei Standard Bereitstellungs Profile mit Standardeinstellungen für dev/Test-Umgebungen:

| Bereitstellungs Profil | Kubernetes-Umgebung |
|---|---|
| **AKS-dev-Test** | Azure Kubernetes Service (AKS) |
| **kubeadm-dev-Test** | Mehrere Computer (kubeadm) |
| **minikube-dev-test** | Minikube |

Sie können einen Big Data Cluster bereitstellen, indem Sie **azdata BDC Create**ausführen. Dadurch werden Sie aufgefordert, eine der Standardkonfigurationen auszuwählen und Sie durch die Bereitstellung zu leiten.

Wenn Sie zum ersten Mal `azdata` ausführen, müssen `--accept-eula` Sie einschließen, um den Endbenutzer-Lizenzvertrag (EULA) zu akzeptieren.

```bash
azdata bdc create --accept-eula
```

In diesem Szenario werden Sie zur Eingabe von Einstellungen aufgefordert, die nicht Teil der Standardkonfiguration sind, z. b. Kenn Wörter. 

> [!NOTE]
> Ab SQL Server 2019 CTP 3,2 haben Sie nicht mehr Mitglied in das SQL Server 2019-Programm für die [frühzeitige Einführung](https://aka.ms/eapsignup) , um die Vorschau Versionen von Big Data Cluster kennenzulernen.

> [!IMPORTANT]
> Der Standardname des Big Data Clusters ist **MSSQL-Cluster**. Dies ist wichtig zu wissen, um einen der **kubectl** -Befehle auszuführen, die den Kubernetes-Namespace mit dem `-n` -Parameter angeben.

## <a id="customconfig"></a>Benutzerdefinierte Konfigurationen

Es ist auch möglich, Ihr eigenes Profil für die Bereitstellungs Konfiguration anzupassen. Führen Sie hierzu die folgenden Schritte aus:

1. Beginnen Sie mit einem der Standard Bereitstellungs Profile, die ihrer Kubernetes-Umgebung entsprechen. Sie können den Befehl **azdata BDC config List** verwenden, um Sie aufzulisten:

   ```bash
   azdata bdc config list
   ```

1. Erstellen Sie eine Kopie des Bereitstellungs Profils mit dem Befehl **azdata BDC config init** , um die Bereitstellung anzupassen. Der folgende Befehl erstellt z. b. eine Kopie der **AKS-dev-Test-** Bereitstellungs Konfigurationsdateien in einem `custom`Zielverzeichnis namens:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

   azdata
   > Der `--target` gibt ein Verzeichnis an, das die Konfigurationsdateien " **Cluster. JSON** " und " **Control. JSON**" `--source` auf Grundlage des-Parameters enthält.

1. Zum Anpassen der Einstellungen in Ihrem Bereitstellungs Konfigurations Profil können Sie die Bereitstellungs Konfigurationsdatei in einem Tool bearbeiten, das für die Bearbeitung von JSON-Dateien geeignet ist, z. b. vs Code. Bei der Skript gesteuerten Automatisierung können Sie auch das benutzerdefinierte Bereitstellungs Profil mithilfe des Befehls " **azdata BDC config** " bearbeiten. Der folgende Befehl ändert z. b. ein benutzerdefiniertes Bereitstellungs Profil, um den Namen des bereitgestellten Clusters von der Standardeinstellung (**MSSQL-Cluster**) in **Test-Cluster**zu ändern:  

   ```bash
   azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
   ```

   > Ein nützliches Tool für die Suche nach JSON-Pfaden ist der [jsonpath Online Evaluator](https://jsonpath.com/).

   Zusätzlich zum Übergeben von Schlüssel-Wert-Paaren können Sie auch Inline-JSON-Werte bereitstellen oder JSON-Patchdateien übergeben. Weitere Informationen finden Sie unter [Konfigurieren von Bereitstellungs Einstellungen für Big Data Cluster](deployment-custom-configuration.md).

1. Übergeben Sie dann die benutzerdefinierte Konfigurationsdatei an **azdata BDC Create**. Beachten Sie, dass Sie die erforderlichen [Umgebungsvariablen](#env)festlegen müssen. andernfalls werden Sie zur Eingabe der Werte aufgefordert:

   ```bash
   azdata bdc create --config-profile custom --accept-eula yes
   ```

> Weitere Informationen zur Struktur einer Bereitstellungs Konfigurationsdatei finden Sie in der [Referenz zur Bereitstellungs Konfigurationsdatei](reference-deployment-config.md). Weitere Konfigurationsbeispiele finden Sie unter [Konfigurieren von Bereitstellungs Einstellungen für Big Data Cluster](deployment-custom-configuration.md).

## <a id="env"></a>Umgebungsvariablen

Die folgenden Umgebungsvariablen werden für Sicherheitseinstellungen verwendet, die nicht in einer Bereitstellungs Konfigurationsdatei gespeichert werden. Beachten Sie, dass die Docker-Einstellungen außer den Anmelde Informationen in der Konfigurationsdatei festgelegt werden können.

| Umgebungsvariable | Anforderung |Beschreibung |
|---|---|---|
| **CONTROLLER_USERNAME** | Erforderlich |Der Benutzername für den Cluster Administrator. |
| **CONTROLLER_PASSWORD** | Erforderlich |Das Kennwort für den Cluster Administrator. |
| **MSSQL_SA_PASSWORD** | Erforderlich |Das Kennwort des SA-Benutzers für die SQL-Master Instanz. |
| **KNOX_PASSWORD** | Erforderlich |Das Kennwort für Knox-Benutzer. |
| **ACCEPT_EULA**| Erforderlich für die erste Verwendung von`azdata`| Erfordert keinen Wert. Wenn er als Umgebungsvariable festgelegt ist, wendet er EULA auf SQL Server `azdata`und an. Wenn Sie nicht als Umgebungsvariable festgelegt ist, `--accept-eula` können Sie in den ersten `azdata` Befehl verwenden.|
| **DOCKER_USERNAME** | Optional | Der Benutzername für den Zugriff auf die Container Images, wenn Sie in einem privaten Repository gespeichert sind. Weitere Informationen zur Verwendung eines privaten docker-Repository für Big Data Cluster Bereitstellung finden Sie im Thema [Offline Bereitstellungen](deploy-offline.md) .|
| **DOCKER_PASSWORD** | Optional |Das Kennwort für den Zugriff auf das oben genannte private Repository. |

Diese Umgebungsvariablen müssen vor dem Aufrufen von **azdata BDC Create**festgelegt werden. Wenn eine Variable nicht festgelegt ist, werden Sie dazu aufgefordert.

Im folgenden Beispiel wird gezeigt, wie die Umgebungsvariablen für Linux (bash) und Windows (PowerShell) festgelegt werden:

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
```

Nachdem Sie die Umgebungsvariablen festgelegt haben, `azdata bdc create` müssen Sie ausführen, um die Bereitstellung zu initiieren. In diesem Beispiel wird das oben erstellte Cluster Konfigurations Profil verwendet:

```bash
azdata bdc create --config-profile custom --accept-eula yes
```

Beachten Sie die folgenden Richtlinien:

- Stellen Sie sicher, dass Sie das Kennwort in doppelte Anführungszeichen einschließen, wenn es Sonderzeichen enthält. Sie können den **MSSQL_SA_PASSWORD** auf einen beliebigen Wert festlegen, aber stellen Sie sicher, dass das Kennwort ausreichend komplex ist `!`und `&` nicht `'` die Zeichen, oder verwenden. Beachten Sie, dass Trennzeichen für doppelte Anführungszeichen nur in bash-Befehlen funktionieren.
- Der **sa** -Anmelde Name ist ein Systemadministrator auf der SQL Server Master Instanz, die während des Setups erstellt wird. Nachdem Sie den SQL Server Container erstellt haben, kann die **MSSQL_SA_PASSWORD** -Umgebungsvariable, die Sie `echo $MSSQL_SA_PASSWORD` angegeben haben, durch Ausführen im Container erkannt werden. Ändern Sie aus Sicherheitsgründen das SA-Kennwort gemäß den [hier](../linux/quickstart-install-connect-docker.md#sapassword)dokumentierten bewährten Methoden.

## <a id="unattended"></a>Unbeaufsichtigte Installation

Bei einer unbeaufsichtigten Bereitstellung müssen Sie alle erforderlichen Umgebungsvariablen festlegen, eine Konfigurationsdatei verwenden und den `azdata bdc create` Befehl mit dem `--accept-eula yes` -Parameter aufrufen. Die Beispiele im vorherigen Abschnitt veranschaulichen die Syntax für eine unbeaufsichtigte Installation.

## <a id="monitor"></a>Überwachen der Bereitstellung

Beim Cluster-Bootstrap wird der Bereitstellungs Status im Client Befehlsfenster ausgegeben. Während des Bereitstellungs Prozesses sollte eine Reihe von Nachrichten angezeigt werden, die auf den Controller Pod warten:

```output
Waiting for cluster controller to start.
```

In 15 bis 30 Minuten sollten Sie benachrichtigt werden, dass der Controller Pod ausgeführt wird:

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> Die gesamte Bereitstellung kann aufgrund der Zeit, die zum Herunterladen der Container Images für die Komponenten des Big Data Clusters erforderlich ist, viel Zeit in Anspruch nehmen. Es sollte jedoch nicht mehrere Stunden dauern. Wenn Sie Probleme mit der Bereitstellung haben, finden Sie weitere Informationen unter [Überwachung und Problembehandlung SQL Server Big Data Cluster](cluster-troubleshooting-commands.md).

Wenn die Bereitstellung abgeschlossen ist, werden Sie von der Ausgabe über Erfolg benachrichtigt:

```output
Cluster deployed successfully.
```

> [!TIP]
> Der Standardname für den bereitgestellten Big Data Cluster `mssql-cluster` ist, sofern er nicht durch eine benutzerdefinierte Konfiguration geändert wird.

## <a id="endpoints"></a>Abrufen von Endpunkten

Nachdem das Bereitstellungs Skript erfolgreich abgeschlossen wurde, können Sie die IP-Adressen der externen Endpunkte für den Big Data Cluster mithilfe der folgenden Schritte abrufen.

1. Suchen Sie nach der Bereitstellung die IP-Adresse des Controller Endpunkts entweder aus der Standardausgabe der Bereitstellung oder anhand der externen IP-Ausgabe des folgenden **kubectl** -Befehls:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie den Standardnamen während der Bereitstellung nicht geändert haben `-n mssql-cluster` , verwenden Sie im vorherigen Befehl. **MSSQL-Cluster** ist der Standardname für den Big Data Cluster.

1. Melden Sie sich mit der [azdata-Anmeldung](reference-azdata.md)beim Big Data-Cluster an. Legen Sie den Parameter **--Controller-Endpoint** auf die externe IP-Adresse des Controller Endpunkts fest.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Geben Sie den Benutzernamen und das Kennwort für den Controller (CONTROLLER_USERNAME und CONTROLLER_PASSWORD) während der Bereitstellung an.

1. Führen Sie die [azdata BDC Endpoint List](reference-azdata-bdc-endpoint.md) aus, um eine Liste mit einer Beschreibung der einzelnen Endpunkte und ihrer entsprechenden IP-Adresse und Port Werte zu erhalten. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   Die folgende Liste zeigt die Beispielausgabe dieses Befehls:

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

Sie können auch alle Dienst Endpunkte, die für den Cluster bereitgestellt wurden, durch Ausführen des folgenden **kubectl** -Befehls erhalten:

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

### <a name="minikube"></a>Minikube

Wenn Sie minikube verwenden, müssen Sie den folgenden Befehl ausführen, um die IP-Adresse zu erhalten, mit der Sie eine Verbindung herstellen müssen. Geben Sie zusätzlich zur IP-Adresse den Port für den Endpunkt an, mit dem Sie eine Verbindung herstellen müssen.

```bash
minikube ip
```

## <a id="status"></a>Überprüfen des Cluster Status

Nach der Bereitstellung können Sie den Status des Clusters mit dem Befehl [azdata BDC Status Show](reference-azdata-bdc-status.md) überprüfen.

```bash
azdata bdc status show -o table
```

> [!TIP]
> Zum Ausführen der Status Befehle müssen Sie sich zunächst mit dem **azdata-Anmelde** Befehl anmelden, der im Abschnitt vorherige Endpunkte angezeigt wurde.

Das folgende Beispiel zeigt die Ausgabe dieses Befehls:

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

In diesem Zusammenfassungs Status können Sie auch mit den folgenden Befehlen einen ausführlicheren Status erhalten:

- [Status des azdata-BDC-Steuer Elements](reference-azdata-bdc-control-status.md)
- [Status des azdata-BDC-Pools](reference-azdata-bdc-pool-status.md)

Die Ausgabe dieser Befehle enthält URLs zu kibana-und grafana-Dashboards für eine ausführlichere Analyse.

Zusätzlich zur Verwendung von **azdata**können Sie auch Azure Data Studio verwenden, um sowohl Endpunkte als auch Statusinformationen zu ermitteln. Weitere Informationen zum Anzeigen des Cluster Status mit **azdata** und Azure Data Studio finden [Sie unter How to View the Status of a Big Data Cluster](view-cluster-status.md).

## <a id="connect"></a>Herstellen einer Verbindung mit dem Cluster

Weitere Informationen zum Herstellen einer Verbindung mit dem Big Data-Cluster finden Sie unter [Herstellen einer Verbindung mit einem SQL Server Big Data Cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Bereitstellung von Big Data Clustern finden Sie in den folgenden Ressourcen:

- [Konfigurieren von Bereitstellungs Einstellungen für Big Data Cluster](deployment-custom-configuration.md)
- [Ausführen einer Offline Bereitstellung eines SQL Server Big Data Clusters](deploy-offline.md)
- [Werkstatt Architektur von Microsoft SQL Server Big Data Clustern](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
