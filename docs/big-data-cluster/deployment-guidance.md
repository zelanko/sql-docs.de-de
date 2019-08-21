---
title: Hinweise zur Bereitstellung
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] wie Sie (Vorschau) auf Kubernetes bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1520254a8a7817db612bf5e42706113495a832de
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652356"
---
# <a name="how-to-deploy-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-kubernetes"></a>Bereitstellen auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Kubernetes

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Big-Data-Cluster für SQL Server werden als Docker-Container auf einem Kubernetes-Cluster bereitgestellt. Im Folgenden finden Sie eine Übersicht über die Einrichtungs-und Konfigurationsschritte:

- Einrichten eines Kubernetes-Clusters auf einer einzelnen VM, auf einem VM-Cluster oder in Azure Kubernetes Service (AKS)
- Installieren des Clusterkonfigurationstools **azdata** auf dem Clientcomputer
- Bereitstellen eines Big-Data-Clusters für SQL Server auf einem Kubernetes-Cluster

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>Installieren von Big-Data-Tools für SQL Server 2019

Bevor Sie einen Big-Data-Cluster für SQL Server 2019 bereitstellen können, müssen Sie zuerst die folgenden [Big-Data-Tools installieren](deploy-big-data-tools.md):

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019-Erweiterung**

## <a id="prereqs"></a> Anforderungen an Kubernetes

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]erfordert mindestens Version 1.10 für Server und Client (kubectl).

> [!NOTE]
> Die Kubernetes-Nebenversionen von Server und Client dürfen nach oben oder unten höchstens um die Zahl 1 abweichen. Weitere Informationen finden Sie unter [Kubernetes-Versionshinweise und SKU-Richtlinien für Versionsabweichungen](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a> Einrichten des Kubernetes-Clusters

Wenn Sie bereits über einen Kubernetes-Cluster verfügen, der die oben genannten Anforderungen erfüllt, können Sie direkt mit dem [Bereitstellungsschritt](#deploy) fortfahren. In diesem Abschnitt werden grundlegende Kubernetes-Kenntnisse vorausgesetzt.  Ausführliche Informationen finden Sie in der [Kubernetes-Dokumentation](https://kubernetes.io/docs/home).

Sie können Kubernetes auf drei Arten bereitstellen:

| Bereitstellung von Kubernetes auf bzw. in: | Beschreibung | Link |
|---|---|---|
| **Azure Kubernetes Service (AKS)** | Ein Managed Kubernetes-Containerdienst in Azure. | [Anweisungen](deploy-on-aks.md) |
| **Mehreren Computern (kubeadm)** | Ein Kubernetes-Cluster, der auf physischen oder virtuellen Computern mithilfe von **kubeadm** bereitgestellt wird. | [Anweisungen](deploy-with-kubeadm.md) |
| **Minikube** | Ein Kubernetes-Cluster mit einem einzelnen Knoten auf einer VM. | [Anweisungen](deploy-on-minikube.md) |

> [!TIP]
> Sie können auch ein Skript erstellen, mit dem die Bereitstellung von AKS und eines Big-Data-Clusters in einem Schritt ausgeführt wird. Weitere Informationen finden Sie im Artikel zur Verwendung eines [Python-Skripts](quickstart-big-data-cluster-deploy.md) oder im Artikel zur Nutzung eines [Notebooks in Azure Data Studio](deploy-notebooks.md).

### <a name="verify-kubernetes-configuration"></a>Überprüfen der Kubernetes-Konfiguration

Führen Sie den Befehl **kubectl** aus, um sich die Clusterkonfiguration anzeigen zu lassen. Stellen Sie sicher, dass kubectl auf den richtigen Clusterkontext verweist.

```bash
kubectl config view
```

Nachdem Sie den Kubernetes-Cluster konfiguriert haben, können Sie mit der Bereitstellung eines neuen Big-Data-Clusters für SQL Server fortfahren. Wenn Sie ein Upgrade von einer vorherigen Version durchführen, finden Sie weitere Informationen unter [Upgrade [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ](deployment-upgrade.md).

## <a id="deploy"></a> Übersicht über die Bereitstellung

Die meisten Einstellungen für Big-Data-Cluster werden in einer JSON-Konfigurationsdatei für Bereitstellungen definiert. Sie können ein Standardbereitstellungsprofil für AKS, `kubeadm` oder `minikube` verwenden. Alternativ können Sie auch eine eigene Konfigurationsdatei für Bereitstellungen während der Einrichtung anpassen. Aus Sicherheitsgründen werden Authentifizierungseinstellungen mithilfe von Umgebungsvariablen übermittelt.

In den folgenden Abschnitten finden Sie weitere Informationen darüber, wie Sie Bereitstellungen von Big-Data-Clustern konfigurieren. Außerdem lernen Sie Beispiele für übliche Anpassungen kennen. Sie können jederzeit die benutzerdefinierte Konfigurationsdatei für Bereitstellungen mit einem Editor wie beispielsweise VS Code bearbeiten.

## <a id="configfile"></a> Standardkonfigurationen

Die Bereitstellungsoptionen für Big-Data-Cluster werden in JSON-Konfigurationsdateien definiert. Es gibt drei Bereitstellungsprofile mit Standardeinstellungen für Entwicklungs- und Testumgebungen (dev/test):

| Bereitstellungsprofil | Kubernetes-Umgebung |
|---|---|
| **aks-dev-test** | Azure Kubernetes Service (AKS) |
| **kubeadm-dev-test** | Mehrere Computer (kubeadm) |
| **minikube-dev-test** | Minikube |

Sie können einen Big-Data-Cluster bereitstellen, indem Sie **azdata bdc create** ausführen. Dadurch werden Sie aufgefordert, eine der Standardkonfigurationen auszuwählen. Anschließend werden Sie durch die Bereitstellungsschritte geführt.

Wenn Sie zum ersten Mal `azdata` ausführen, müssen Sie auch `--accept-eula=yes` angeben, um die Lizenzbedingungen zu akzeptieren.

```bash
azdata bdc create --accept-eula=yes
```

In diesem Szenario werden Sie aufgefordert, Informationen wie Kennwörter anzugeben, die nicht Teil der Standardkonfiguration sind. 

> [!IMPORTANT]
> Der Standardname für den Big-Data-Cluster ist **mssql-cluster**. Sie benötigen diesen, um **kubectl**-Befehle ausführen zu können, mit denen der Kubernetes-Namespace mithilfe des `-n`-Parameters angeben wird.

## <a id="customconfig"></a> Benutzerdefinierte Konfigurationen

Sie haben auch die Möglichkeit, ein eigenes Bereitstellungsprofil anzupassen. Dazu können Sie die folgenden Schritte nutzen:

1. Beginnen Sie mit einem Standardbereitstellungsprofil, das für Ihre Kubernetes-Umgebung geeignet ist. Sie können sich alle Profile mit dem Befehl **azdata bdc config list** anzeigen lassen:

   ```bash
   azdata bdc config list
   ```

1. Erstellen Sie eine Kopie des Bereitstellungsprofils mit dem Befehl **azdata bdc config init**, um die Bereitstellung anzupassen. Mit dem folgenden Befehl wird beispielsweise eine Kopie der **aks-dev-test**-Konfigurationsdatei für Bereitstellungen in einem Zielverzeichnis namens `custom` erstellt:

   ```bash
   azdata bdc config init --source aks-dev-test --target custom
   ```

   azdata
   > Mit `--target` wird ein Verzeichnis angegeben, das in Abhängigkeit des `--source`-Parameters die Konfigurationsdateien **cluster.json** und **control.json** enthält.

1. Sie können die Einstellungen in Ihrem Bereitstellungsprofil anpassen, indem Sie die Konfigurationsdatei für Bereitstellungen in einem Tool bearbeiten. Dieses muss sich zur Bearbeitung von JSON-Dateien eignen. Für diese Aufgabe können Sie beispielweise VS Code verwenden. Zur skriptbasierten Automatisierung können Sie auch das benutzerdefinierte Bereitstellungsprofil mit dem Befehl **azdata bdc config** bearbeiten. Mit dem folgenden Befehl wird z. B. ein benutzerdefiniertes Bereitstellungsprofil angepasst. Dabei wird der Standardname des bereitgestellten Clusters (**mssql-cluster**) in **test-cluster** geändert:  

   ```bash
   azdata bdc config replace --config-file custom/cluster.json --json-values "metadata.name=test-cluster"
   ```
   
> [!TIP]
> Sie können den Clusternamen auch zum Zeitpunkt der Bereitstellung übergeben, indem Sie den Parameter *--name* für den Befehl *azdata create bdc* verwenden. Die Befehlsparameter haben Vorrang vor den Werten in den Konfigurationsdateien.

   > Ein nützliches Tool zum Ermitteln von JSON-Pfaden ist [JSONPath Online Evaluator](https://jsonpath.com/).

   Sie können darin nicht nur Schlüssel-Wert-Paare, sondern auch Inline-JSON-Werte angeben und JSON-Patchdateien übergeben. Weitere Informationen finden Sie unter [Konfigurieren von Bereitstellungseinstellungen für Big-Data-Cluster](deployment-custom-configuration.md).

1. Übergeben Sie dem Befehl **azdata bdc create** anschließend die benutzerdefinierte Konfigurationsdatei. Beachten Sie, dass Sie die erforderlichen [Umgebungsvariablen](#env) festlegen müssen. Andernfalls werden Sie aufgefordert, die entsprechenden Werte einzugeben:

   ```bash
   azdata bdc create --config-profile custom --accept-eula yes
   ```

> Weitere Informationen zur Struktur einer Konfigurationsdatei für Bereitstellungen finden Sie in der zugehörigen [Referenzdokumentation](reference-deployment-config.md). Weitere Konfigurationsbeispiele finden Sie unter [Konfigurieren von Bereitstellungseinstellungen für Big-Data-Cluster](deployment-custom-configuration.md).

## <a id="env"></a> Umgebungsvariablen

Die folgenden Umgebungsvariablen werden für Sicherheitseinstellungen verwendet, die nicht in einer Konfigurationsdatei für Bereitstellungen gespeichert werden. Beachten Sie, dass Docker-Einstellungen mit Ausnahme der Anmeldeinformationen in der Konfigurationsdatei festgelegt werden können.

| Umgebungsvariable | Anforderung |Beschreibung |
|---|---|---|
| **CONTROLLER_USERNAME** | Erforderlich |Der Benutzername für den Clusteradministrator. |
| **CONTROLLER_PASSWORD** | Erforderlich |Das Kennwort für den Clusteradministrator. |
| **MSSQL_SA_PASSWORD** | Erforderlich |Das Kennwort des Systemadministrators für die SQL-Masterinstanz. |
| **KNOX_PASSWORD** | Erforderlich |Das Kennwort für den Knox-Benutzer. |
| **ACCEPT_EULA**| Erforderlich für die erste Verwendung von `azdata`| Erfordert keinen Wert. Wenn dieser Wert als Umgebungsvariable festgelegt ist, werden die Lizenzbedingungen für SQL Server und `azdata` akzeptiert. Wenn er nicht als Umgebungsvariable festgelegt ist, können Sie `--accept-eula` angeben, wenn Sie den Befehl `azdata` zum ersten Mal verwenden.|
| **DOCKER_USERNAME** | Optional | Der Benutzername, mit dem auf Containerimages zugegriffen wird, wenn diese in einem privaten Repository gespeichert sind. Weitere Informationen darüber, wie Sie ein privates Docker-Repository zur Bereitstellung von Big-Data-Clustern nutzen, finden Sie im Artikel [Offlinebereitstellungen](deploy-offline.md).|
| **DOCKER_PASSWORD** | Optional |Das Kennwort, mit dem auf das oben erwähnte private Repository zugegriffen wird. |

Sie müssen diese Umgebungsvariablen festlegen, bevor Sie **azdata bdc create** aufrufen. Wenn eine Variable nicht festgelegt ist, werden Sie aufgefordert, diese anzugeben.

Im folgenden Beispiel wird gezeigt, wie Sie die Umgebungsvariablen für Linux (Bash) und Windows (PowerShell) festlegen:

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

Nachdem Sie die Umgebungsvariablen festgelegt haben, müssen Sie `azdata bdc create` ausführen, um die Bereitstellung auszulösen. Im folgenden Beispiel wird das oben erstellte Clusterkonfigurationsprofil verwendet:

```bash
azdata bdc create --config-profile custom --accept-eula yes
```

Beachten Sie die folgenden Richtlinien:

- Setzen Sie das Kennwort immer in doppelte Anführungszeichen, wenn es Sonderzeichen enthält. Sie können für **MSSQL_SA_PASSWORD** eine beliebige Zeichenfolge festlegen. Das Kennwort muss jedoch ausreichend komplex sein und darf nicht die Zeichen `!`, `&` oder `'` enthalten. Doppelte Anführungszeichen können nur in Bash-Befehlen als Trennzeichen verwendet werden.
- Die **Systemadministratoranmeldung** ist ein Systemadministrator auf der SQL Server-Masterinstanz und wird bei der Einrichtung erstellt. Nachdem Sie den SQL Server-Container erstellt haben, können Sie die von Ihnen festgelegte Umgebungsvariable **MSSQL_SA_PASSWORD** ermitteln, indem Sie `echo $MSSQL_SA_PASSWORD` im Container ausführen. Ändern Sie aus Sicherheitsgründen das Systemadministratorkennwort, und beachten Sie dabei die [entsprechenden Best Practices](../linux/quickstart-install-connect-docker.md#sapassword).

## <a id="unattended"></a>Unbeaufsichtigtes Installieren

Bei einer unbeaufsichtigten Bereitstellung müssen Sie alle erforderlichen Umgebungsvariablen festlegen, eine Konfigurationsdatei verwenden und den Befehl `azdata bdc create` mit dem `--accept-eula yes`-Parameter aufrufen. Die Beispiele im vorherigen Abschnitt veranschaulichen die Syntax für eine unbeaufsichtigte Installation.

## <a id="monitor"></a> Überwachen der Bereitstellung

Während des Clusterbootstraps wird der Bereitstellungsstatus im Befehlsfenster des Clients ausgegeben. Im Verlauf des Bereitstellungsprozesses sollten mehrere Wartemeldungen für den Controllerpod angezeigt werden:

```output
Waiting for cluster controller to start.
```

Nach 15 bis 30 Minuten sollten Sie benachrichtigt werden, dass der Controllerpod ausgeführt wird:

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> Die vollständige Bereitstellung kann einige Zeit in Anspruch nehmen, da die Containerimages für die Komponenten des Big-Data-Clusters heruntergeladen werden müssen. Der Vorgang sollte jedoch nicht mehrere Stunden dauern. Wenn bei der Bereitstellung Probleme auftreten, finden Sie weitere Informationen unter [Überwachung [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]und ](cluster-troubleshooting-commands.md)Problembehandlung.

Nachdem die Bereitstellung erfolgreich abgeschlossen wurde, wird die folgende Meldung ausgegeben:

```output
Cluster deployed successfully.
```

> [!TIP]
> Der Standardname für den bereitgestellten Big-Data-Cluster ist `mssql-cluster`, falls er nicht durch eine benutzerdefinierte Konfiguration geändert wird.

## <a id="endpoints"></a> Abrufen von Endpunkten

Nachdem das Bereitstellungsskript erfolgreich ausgeführt wurde, können Sie die IP-Adressen der externen Endpunkte für den Big-Data-Cluster mithilfe der folgenden Schritte abrufen.

1. Suchen Sie nach der Bereitstellung die IP-Adresse des Controllerendpunkts in der Standardausgabe. Alternativ können Sie sich auch die Ausgabe des folgenden **kubectl**-Befehls ansehen und die IP-Adresse unter „EXTERNAL-IP“ ablesen:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie den Standardnamen während der Bereitstellung nicht geändert haben, verwenden Sie im vorherigen Befehl `-n mssql-cluster`. **mssql-cluster** ist der Standardname für den Big-Data-Cluster.

1. Melden Sie sich beim Big-Data-Cluster mit [azdata login](reference-azdata.md) an. Legen Sie den Parameter **--controller-endpoint** auf die externe IP-Adresse des Controllerendpunkts fest.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Geben Sie den Benutzernamen und das Kennwort an (CONTROLLER_USERNAME und CONTROLLER_PASSWORD), die Sie während der Bereitstellung für den Controller konfiguriert haben.

1. Führen Sie [azdata bdc endpoint list](reference-azdata-bdc-endpoint.md) aus, um eine Liste mit Beschreibungen jedes Endpunkts sowie deren entsprechende IP-Adressen und Portwerte abzurufen. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   Die folgende Liste zeigt eine Beispielausgabe dieses Befehls an:

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

Sie können auch alle Dienstendpunkte, die für den Cluster bereitgestellt wurden, durch die Ausführung des folgenden **kubectl**-Befehls abrufen:

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

### <a name="minikube"></a>Minikube

Wenn Sie Minikube verwenden, müssen Sie den unten stehenden Befehl ausführen, um die IP-Adressen abzurufen, die Sie für die Verbindung benötigen. Geben Sie zusätzlich zur IP-Adresse den Port für den Endpunkt an, mit dem Sie eine Verbindung herstellen müssen.

```bash
minikube ip
```

## <a id="status"></a> Überprüfen des Clusterstatus

Nach der Bereitstellung können Sie den Status des Clusters mit dem Befehl [azdata bdc status show](reference-azdata-bdc-status.md) überprüfen.

```bash
azdata bdc status show -o table
```

> [!TIP]
> Zum Ausführen der Statusbefehle müssen Sie sich zunächst mit dem Befehl **azdata login** anmelden, der im vorangegangenen Abschnitt zu Endpunkten gezeigt wurde.

Im Folgenden wird eine Beispielausgabe dieses Befehls angezeigt:

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

Mit den folgenden Befehlen können Sie sich zusätzliche Statusinformationen anzeigen lassen:

- [azdata bdc control status](reference-azdata-bdc-control-status.md)
- [azdata bdc pool status](reference-azdata-bdc-pool-status.md)

Die Ausgaben dieser Befehle enthalten URLs zu Kibana-und Grafana-Dashboards. Dort ist eine ausführlichere Analyse möglich.

Zusätzlich zu **azdata** können Sie auch Azure Data Studio verwenden, um Endpunkt- und Statusinformationen zu ermitteln. Weitere Informationen darüber, wie Sie mit **azdata** und Azure Data Studio den Clusterstatus abrufen können, finden Sie unter [Anzeigen des Status eines Big-Data-Clusters](view-cluster-status.md).

## <a id="connect"></a> Herstellen einer Verbindung mit dem Cluster

Weitere Informationen darüber, wie Sie eine Verbindung mit dem Big-Data-Cluster herstellen, finden Sie unter [Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server über Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie weitere Informationen zur Bereitstellung von Big-Data-Clustern:

- [Konfigurieren von Bereitstellungseinstellungen für Big-Data-Cluster](deployment-custom-configuration.md)
- [Durchführen einer Offlinebereitstellung von Big-Data-Clustern für SQL Server](deploy-offline.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] -Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
