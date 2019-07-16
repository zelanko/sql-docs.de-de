---
title: Hinweise zur Bereitstellung
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie SQL Server-2019 big Data-Clustern (Vorschau) in Kubernetes bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0f2993d15cecd87879cabc50918d784a16750b30
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958415"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Wie Sie SQL Server-big Data-Cluster in Kubernetes bereitstellen

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

SQL Server-big Data-Cluster wird als Docker-Container in einem Kubernetes-Cluster bereitgestellt. Dies ist eine Übersicht über die Schritte für Einrichtung und Konfiguration:

- Richten Sie einen Kubernetes-Cluster auf einem einzelnen virtuellen Computer, die Cluster von virtuellen Computern oder in Azure Kubernetes Service (AKS).
- Installieren Sie das Cluster-Konfigurationstool **Mssqlctl** auf Ihrem Clientcomputer.
- Stellen Sie eine SQL Server-big Data-Cluster in einem Kubernetes-Cluster bereit.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="install-sql-server-2019-big-data-tools"></a>Installieren von SQL Server-2019 big datatools

Vor der Bereitstellung von einer SQL Server-2019 big Data-Cluster zuerst [die big Data-Tools installieren](deploy-big-data-tools.md):

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **SQL Server-2019-Erweiterung**

## <a id="prereqs"></a> Kubernetes-Voraussetzungen

SQL Server-big Data-Cluster erfordern eine Kubernetes-Mindestversion von mindestens v1.10 für Server und Client (Kubectl).

> [!NOTE]
> Beachten Sie, dass der Client und Server-Kubernetes-Versionen in + 1 oder-1 Nebenversion werden soll. Weitere Informationen finden Sie unter [Kubernetes unterstützte Versionen und Komponenten, die datenschiefe](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

### <a id="kubernetes"></a> Kubernetes-Cluster-setup

Wenn Sie bereits einen Kubernetes-Cluster, die die oben aufgeführten Voraussetzungen erfüllt haben, können Sie direkt zu überspringen der [Bereitstellungsschritt](#deploy). In diesem Abschnitt wird ein grundlegendes Verständnis der Kubernetes-Konzepte vorausgesetzt.  Ausführliche Informationen zu Kubernetes finden Sie unter den [Kubernetes-Dokumentation](https://kubernetes.io/docs/home).

Sie können zum Bereitstellen von Kubernetes stehen drei Möglichkeiten zur Verfügung:

| Bereitstellen von Kubernetes auf: | Beschreibung | Link |
|---|---|---|
| **Azure Kubernetes-Dienste (AKS)** | Managed Kubernetes-Container-Dienst in Azure. | [Anweisungen](deploy-on-aks.md) |
| **Mehrere Computer (Kubeadm)** | Ein Kubernetes-Cluster bereitgestellt, die auf physischen oder virtuellen Computern mit **Kubeadm** | [Anweisungen](deploy-with-kubeadm.md) |
| **Minikube** | Einen Einzelknoten-Kubernetes-Cluster auf einem virtuellen Computer. | [Anweisungen](deploy-on-minikube.md) |

> [!TIP]
> Ein Beispiel-Python-Skript, das bereitgestellt wird, sowohl AKS und eine SQL-Server, die big Data-in einem Schritt Cluster, finden Sie unter [Schnellstart: Bereitstellen von SQL Server, die big Data-in Azure Kubernetes Service (AKS Cluster)](quickstart-big-data-cluster-deploy.md).

### <a name="verify-kubernetes-configuration"></a>Überprüfen der Kubernetes-Konfiguration

Führen Sie die **"kubectl"** Befehl aus, um die Clusterkonfiguration anzuzeigen. Stellen Sie sicher, dass diese "kubectl" auf den richtigen Clusterkontext gezeigt wird.

```bash
kubectl config view
```

Nachdem Sie Ihren Kubernetes-Cluster konfiguriert haben, können Sie mit der Bereitstellung einer neuen SQL Server-big Data-Cluster fortfahren. Wenn Sie von einer früheren Version aktualisieren, finden Sie unter [das upgrade von SQL Server-big Data-Cluster](deployment-upgrade.md).

## <a id="deploy"></a> Übersicht über die Bereitstellung

Ab CTP-Version 2.5, werden die meisten big Data-Cluster-Einstellungen in einer JSON-Bereitstellungskonfigurationsdatei definiert. Sie können ein Standardprofil für die Bereitstellung für AKS Kubeadm, oder Minikube oder eigene Bereitstellungskonfigurationsdatei Setup zu verwendende anpassen. Aus Gründen der Sicherheit werden die Authentifizierungseinstellungen für die über Umgebungsvariablen übergeben.

Die folgenden Abschnitte enthalten, Weitere Informationen zum Konfigurieren Sie Ihre big Data-Bereitstellungen sowie Beispiele für häufige Anpassungen zu Clustern. Darüber hinaus können Sie immer mit einem Editor wie VSCode z. B. die benutzerdefinierte Bereitstellung-Konfigurationsdatei bearbeiten.

## <a id="configfile"></a> Standardkonfigurationen

Big Data-Clusterbereitstellung, die Optionen in der JSON-Konfigurationsdateien definiert sind. Es gibt drei standard-bereitstellungsprofile mit Standardeinstellungen für Dev/Test-Umgebungen:

| Bereitstellungsprofil | Kubernetes-Umgebung |
|---|---|
| **AKS-Dev-test** | Azure Kubernetes Service (AKS) |
| **Kubeadm-Dev-test** | Mehrere Computer (Kubeadm) |
| **minikube-dev-test** | Minikube |

Sie können einen big Data-Cluster bereitstellen, mit **Mssqlctl Bdc erstellen**. Dies fordert Sie auf eine der Standardkonfigurationen und führt Sie durch die Bereitstellung.

```bash
mssqlctl bdc create
```

In diesem Szenario werden Sie alle Einstellungen aufgefordert, die nicht Teil der Standardkonfiguration, wie z. B. Kennwörter sind. Beachten Sie, die die Docker-Informationen von Microsoft als Teil der SQL Server-2019 bereitgestellt ist [Early Adoption Program](https://aka.ms/eapsignup).

> [!IMPORTANT]
> Der Standardname der big Data-Cluster ist **Mssql-Cluster**. Dies ist wichtig zu wissen, um einen Ausführen der **"kubectl"** Befehle, die angeben, die Kubernetes-Namespace mit dem `-n` Parameter.

## <a id="customconfig"></a> Benutzerdefinierte Konfigurationen

Es ist auch möglich, Ihre eigenen bereitstellungsprofils anzupassen. Sie hierzu die folgenden Schritte aus:

1. Beginnen Sie mit einem der standardbereitstellung Profile, die die Kubernetes-Umgebung zu entsprechen. Können Sie die **Mssqlctl BDC-Config-Liste** Befehl, um diese aufzulisten:

   ```bash
   mssqlctl bdc config list
   ```

1. Wenn Ihre Bereitstellung anpassen möchten, erstellen Sie eine Kopie des bereitstellungsprofils mit der **Mssqlctl BDC-Config Init** Befehl. Beispielsweise der folgende Befehl erstellt eine Kopie der **Aks-Dev-Test** Bereitstellungskonfigurationsdatei in ein Zielverzeichnis an, mit dem Namen `custom`:

   ```bash
   mssqlctl bdc config init --source aks-dev-test --target custom
   ```

   > [!TIP]
   > Die `--target` gibt ein Verzeichnis, das die Konfigurationsdatei enthält basierend auf den `--source` Parameter.

1. Zum Anpassen der Einstellungen in Ihrem Bereitstellungsprofil für die Konfiguration können Sie die Konfigurationsdatei der Bereitstellung in einem Tool bearbeiten, die gut für die Bearbeitung der JSON-Dateien, z. B. Visual Studio Code ist. Für Skript-Automatisierung, Sie können auch bearbeiten das Profil mit benutzerdefiniertem **Mssqlctl BDC-Config Abschnitt Satz** Befehl. Der folgende Befehl ändert z. B. eine benutzerdefinierte Bereitstellung-Profil, um den Namen des bereitgestellten Clusters von der Standardeinstellung zu ändern (**Mssql-Cluster**) zu **Test-Cluster**:  

   ```bash
   mssqlctl bdc config section set --config-profile custom --json-values "metadata.name=test-cluster"
   ```

   > [!TIP]
   > Die `--config-profile` gibt einen Verzeichnisnamen für Ihr Profil für die benutzerdefinierte Bereitstellung, aber die tatsächlichen Änderungen erfolgen für die Bereitstellung JSON-Konfigurationsdatei in das Verzeichnis an. Ist ein nützliches Tool für die Suche nach JSON-Pfaden der [JSONPath-Online-Ausdrucksauswertung](https://jsonpath.com/).

   Zusätzlich zum Übergeben von Schlüssel-Wert-Paare können auch Inline bereitstellen, JSON-Werte oder übergeben die JSON-Patch-Dateien. Weitere Informationen finden Sie unter [Konfigurieren von bereitstellungseinstellungen für big Data-Cluster](deployment-custom-configuration.md).

1. Klicken Sie dann die benutzerdefinierte Konfigurationsdatei zu übergeben **Mssqlctl Bdc erstellen**. Beachten Sie, dass Sie die erforderlichen festlegen müssen [Umgebungsvariablen](#env), andernfalls werden Sie für die Werte aufgefordert werden:

   ```bash
   mssqlctl bdc create --config-profile custom --accept-eula yes
   ```

> [!TIP]
> Weitere Informationen zur Struktur der Konfigurationsdatei für eine Bereitstellung finden Sie unter den [Bereitstellung-konfigurationsdateireferenz](reference-deployment-config.md). Weitere Konfigurationsbeispiele zur finden Sie [Konfigurieren von bereitstellungseinstellungen für big Data-Cluster](deployment-custom-configuration.md).

## <a id="env"></a> Umgebungsvariablen

Die folgenden Umgebungsvariablen werden für die Sicherheitseinstellungen verwendet, die nicht in einer Konfigurationsdatei für die Bereitstellung gespeichert werden. Beachten Sie, dass Docker-Einstellungen, mit Ausnahme von Anmeldeinformationen in der Konfigurationsdatei festgelegt werden können.

| Umgebungsvariable | Beschreibung |
|---|---|---|---|
| **DOCKER_USERNAME** | Der Benutzername für die containerimages zugreifen, falls sie in einem privaten Repository gespeichert sind. |
| **DOCKER_PASSWORD** | Das Kennwort für den Zugriff auf das obige privaten Repository. |
| **CONTROLLER_USERNAME** | Der Benutzername für die Clusterverwaltung. |
| **CONTROLLER_PASSWORD** | Das Kennwort für die Clusterverwaltung. |
| **KNOX_PASSWORD** | Das Kennwort für Knox-Benutzer. |
| **MSSQL_SA_PASSWORD** | Das Kennwort des SA-Benutzers für die master-SQL-Instanz. |

Diese Umgebungsvariablen festgelegt werden müssen, vor dem Aufruf **Mssqlctl Bdc erstellen**. Wenn eine beliebige Variable nicht festgelegt ist, werden Sie dafür aufgefordert.

Das folgende Beispiel zeigt, wie Sie die Umgebungsvariablen für Linux (Bash) und Windows (PowerShell) festgelegt wird:

```bash
export CONTROLLER_USERNAME=admin
export CONTROLLER_PASSWORD=<password>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
export DOCKER_USERNAME=<docker-username>
export DOCKER_PASSWORD=<docker-password>
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
SET DOCKER_USERNAME=<docker-username>
SET DOCKER_PASSWORD=<docker-password>
```

Nach dem Festlegen der Umgebungsvariablen, müssen Sie ausführen `mssqlctl bdc create` um die Bereitstellung auszulösen. Dieses Beispiel verwendet das Cluster-Konfigurationsprofil oben erstellt haben:

```
mssqlctl bdc create --config-profile custom --accept-eula yes
```

Beachten Sie die folgenden Richtlinien:

- Zu diesem Zeitpunkt Anmeldeinformationen für die private Docker-Registrierung werden bereitgestellt werden, um Sie beim selektieren Ihre [Early Adoption Program Registrierung](https://aka.ms/eapsignup). Early Adoption Program-Registrierung ist erforderlich, um SQL Server-big Data-Cluster zu testen.
- Stellen Sie sicher, dass Sie die Kennwörter in doppelte Anführungszeichen umschließen, wenn sie keine Sonderzeichen enthält. Sie können festlegen, die **MSSQL_SA_PASSWORD** , was auch immer Sie zufrieden sind, aber stellen Sie sicher, dass das Kennwort ist komplex und verwenden Sie nicht die `!`, `&` oder `'` Zeichen. Beachten Sie, die doppelte Anführungszeichen Trennzeichen funktionieren nur in der bash-Befehle.
- Die **SA** Anmeldename ist ein Systemadministrator für die master SQL Server-Instanz, die während des Setups erstellt wird. Nach dem Erstellen Ihrer SQL Server-Containers, der **MSSQL_SA_PASSWORD** Umgebungsvariable, die Sie angegeben ist mit sichtbaren $MSSQL_SA_PASSWORD im Container ausgeben. Ändern Sie aus Sicherheitsgründen Ihr SA-Kennwort gemäß der dokumentierten bewährten Methoden [hier](../linux/quickstart-install-connect-docker.md#sapassword).

## <a id="unattended"></a> Unbeaufsichtigte Installation

Für eine unbeaufsichtigte Bereitstellung, müssen Sie festlegen, alle erforderlichen Umgebungsvariablen, die Verwendung einer Konfigurationsdatei und Aufruf `mssqlctl bdc create` -Befehl mit der `--accept-eula yes` Parameter. Die Beispiele im vorherigen Abschnitt veranschaulicht die Syntax für die unbeaufsichtigte Installation.

## <a id="monitor"></a> Überwachen der Bereitstellung

Während der Cluster-Bootstrap gibt der Client-Befehlsfenster den Bereitstellungsstatus. Während der Bereitstellung sehen Sie eine Reihe von Nachrichten, in dem sie den Pod Controller wartet:

```output
Waiting for cluster controller to start.
```

In weniger als 15 bis 30 Minuten sollten Sie eine Benachrichtigung über der Pod Controller ausgeführt wird:

```output
Cluster controller endpoint is available at 11.111.111.11:30080.
Cluster control plane is ready.
```

> [!IMPORTANT]
> Die gesamte Bereitstellung dauert sehr lange aufgrund der Zeitaufwand für die Container-Images für die Komponenten der big Data-Cluster herunterladen. Er sollte jedoch nicht mehrere Stunden dauern. Wenn Sie Probleme bei der Bereitstellung auftreten, finden Sie unter [Überwachung und Problembehandlung für SQL Server-big Data-Cluster](cluster-troubleshooting-commands.md).

Wenn die Bereitstellung abgeschlossen ist, benachrichtigt die Ausgabe Sie Erfolg:

```output
Cluster deployed successfully.
```

> [!TIP]
> Der Standardname für den Cluster bereitgestellte big Data ist `mssql-cluster` , wenn durch eine benutzerdefinierte Konfiguration geändert.

## <a id="endpoints"></a> Abrufen von Endpunkten

Nachdem das Bereitstellungsskript erfolgreich abgeschlossen wurde, können Sie die IP-Adressen der externen Endpunkte für die big Data-Cluster mit den folgenden Schritten erhalten.

1. Nach der Bereitstellung finden Sie die IP-Adresse des Endpunkts Controller anhand der EXTERNEN IP-Ausgabe des folgenden **"kubectl"** Befehl:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie nicht den Standardnamen bei der Bereitstellung geändert haben, verwenden Sie `-n mssql-cluster` im vorherigen Befehl. **MSSQL-Cluster** ist der Standardname für die big Data-Cluster.

1. Melden Sie sich bei der big Data-Cluster mit [Mssqlctl Anmeldung](reference-mssqlctl.md). Legen Sie die **--controllerendpunkt** Parameter, um die externe IP-Adresse des Endpunkts Controller.

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Geben Sie Benutzername und Kennwort, die Sie für den Controller (CONTROLLER_USERNAME und CONTROLLER_PASSWORD) konfiguriert, während der Bereitstellung.

1. Führen Sie [Mssqlctl Bdc-Endpunktliste](reference-mssqlctl-bdc-endpoint.md) um eine Liste mit einer Beschreibung der einzelnen Endpunkten und ihre entsprechenden Werte für IP-Adresse und den Port abzurufen. 

   ```bash
   mssqlctl bdc endpoint list -o table
   ```

   Die folgende Liste enthält Beispiel für die Ausgabe dieses Befehls:

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

Sie können auch alle Dienstendpunkte, die für den Cluster bereitgestellt werden, durch Ausführen des folgenden Befehls abrufen **"kubectl"** Befehl:

```bash
kubectl get svc -n <your-big-data-cluster-name>
```

### <a name="minikube"></a>Minikube

Wenn Sie Minikube verwenden, müssen Sie führen den folgenden Befehl zum Abrufen der IP-Adresse, die Sie benötigen für die Verbindung. Geben Sie zusätzlich zu die IP-Adresse den Port für den Endpunkt zum Herstellen einer Verbindung mit erforderlichen aus.

```bash
minikube ip
```

## <a id="status"></a> Überprüfen Sie den Clusterstatus

Nach der Bereitstellung können Sie den Status des Clusters mit dem Überprüfen der [Mssqlctl BDC-Status anzeigen](reference-mssqlctl-bdc-status.md) Befehl.

```bash
mssqlctl bdc status show -o table
```

> [!TIP]
> Um die Status-Befehle auszuführen, muss zunächst der Anmeldung mit der **Mssqlctl Anmeldung** -Befehl, der im vorherigen Abschnitt "Endpoints" gezeigt wurde.

Das folgende Beispiel zeigt eine Beispielausgabe für diesen Befehl aus:

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

Zusätzlich zu diesen Statusübersicht können Sie auch ausführlichere Statusinformationen mit den folgenden Befehlen abrufen:

- [Status der BDC-mssqlctl](reference-mssqlctl-bdc-control-status.md)
- [Status des Speicherpools von Mssqlctl bdc](reference-mssqlctl-bdc-pool-status.md)

Die Ausgabe dieser Befehle enthalten URLs zu Kibana und Grafana-Dashboards für eine ausführlichere Analyse an. 

Zusätzlich zur Verwendung von **Mssqlctl**, Sie können auch Studio für Azure Data verwenden, um sowohl Endpunkte und Statusinformationen zu suchen. Weitere Informationen zum Anzeigen des Clusterstatus mit **Mssqlctl** und Azure Data Studio, finden Sie unter [Gewusst wie: Anzeigen des Status einer big Data-Cluster](view-cluster-status.md).

## <a id="connect"></a> Verbinden mit dem cluster

Weitere Informationen zum Herstellen einer Verbindung mit der big Data-Cluster, finden Sie unter [Herstellen einer Verbindung mit einer SQL Server big Data-cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Bereitstellung von big Data-Clusters finden Sie unter den folgenden Ressourcen:

- [Konfigurieren von bereitstellungseinstellungen für big Data-Cluster](deployment-custom-configuration.md)
- [Führen Sie eine offline-Bereitstellung von einer SQL Server-big Data-cluster](deploy-offline.md)
- [Workshop: Microsoft SQL Server-big Data-Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
