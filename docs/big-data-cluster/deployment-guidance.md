---
title: Hinweise zur Bereitstellung
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie SQL Server-2019 big Data-Clustern (Vorschau) in Kubernetes bereitstellen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: a2ace569180006f54461631848ecbf5342b2c1e3
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63472039"
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

| Bereitstellen von Kubernetes auf: | Description | Link |
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
| **aks-dev-test.json** | Azure Kubernetes Service (AKS) |
| **kubeadm-dev-test.json** | Mehrere Computer (Kubeadm) |
| **minikube-dev-test.json** | minikube |

Sie können einen big Data-Cluster bereitstellen, mit **Mssqlctl Clustererstellung**. Dies fordert Sie auf eine der Standardkonfigurationen und führt Sie durch die Bereitstellung.

```bash
mssqlctl cluster create
```

> [!TIP]
> In diesem Beispiel werden Sie alle Einstellungen aufgefordert, die nicht Teil der Standardkonfiguration, wie z. B. Kennwörter sind. Beachten Sie, die die Docker-Informationen von Microsoft als Teil der SQL Server-2019 bereitgestellt ist [Early Adoption Program](https://aka.ms/eapsignup).

## <a id="customconfig"></a> Benutzerdefinierte Konfigurationen

Es ist auch möglich, eine eigene Bereitstellungskonfigurationsdatei anzupassen. Sie hierzu die folgenden Schritte aus:

1. Beginnen Sie mit einem der standardbereitstellung Profile, die die Kubernetes-Umgebung zu entsprechen. Können Sie die **Mssqlctl Config Clusterliste** Befehl, um diese aufzulisten:

   ```bash
   mssqlctl cluster config list
   ```

1. Wenn Ihre Bereitstellung anpassen möchten, erstellen Sie eine Kopie des bereitstellungsprofils mit der **Mssqlctl Cluster Config Init** Befehl. Der folgende Befehl erstellt z. B. eine Kopie der **Aks-Dev-test.json** Bereitstellungskonfigurationsdatei im aktuellen Verzeichnis:

   ```bash
   mssqlctl cluster config init --src aks-dev-test.json --target custom.json
   ```

1. Zum Anpassen der Einstellungen in der Konfigurationsdatei der Bereitstellung können Sie es in einem Tool bearbeiten, die gut für die Bearbeitung der Json-Dokumentation, wie Visual Studio Code ist. Für Skript-Automatisierung, können Sie bearbeiten, die benutzerdefinierte Konfigurationsdatei mit **Mssqlctl Clustersatz Config Abschnitt** Befehl. Der folgende Befehl ändert z. B. eine benutzerdefinierte Konfigurationsdatei aus, um den Namen des bereitgestellten Clusters von der Standardeinstellung zu ändern (**Mssql-Cluster**) zu **Test-Cluster**:  

   ```bash
   mssqlctl cluster config section set --config-file custom.json --json-values "metadata.name=test-cluster"
   ```

   > [!TIP]
   > Ist ein nützliches Tool für die Suche nach JSON-Pfaden der [JSONPath-Online-Ausdrucksauswertung](https://jsonpath.com/).

   Zusätzlich zum Übergeben von Schlüssel-Wert-Paare können auch Inline bereitstellen, JSON-Werte oder übergeben die JSON-Patch-Dateien. Weitere Informationen finden Sie unter [Konfigurieren von bereitstellungseinstellungen für big Data-Cluster](deployment-custom-configuration.md).

1. Klicken Sie dann die benutzerdefinierte Konfigurationsdatei zu übergeben **Mssqlctl Clustererstellung**. Beachten Sie, dass Sie die erforderlichen festlegen müssen [Umgebungsvariablen](#env), andernfalls werden Sie für die Werte aufgefordert werden:

   ```bash
   mssqlctl cluster create --config-file custom.json --accept-eula yes
   ```

> [!TIP]
> Weitere Informationen zur Struktur der Konfigurationsdatei für eine Bereitstellung finden Sie unter den [Bereitstellung-konfigurationsdateireferenz](reference-deployment-config.md). Weitere Konfigurationsbeispiele zur finden Sie [Konfigurieren von bereitstellungseinstellungen für big Data-Cluster](deployment-custom-configuration.md).

## <a id="env"></a> Umgebungsvariablen

Die folgenden Umgebungsvariablen werden für die Sicherheitseinstellungen verwendet, die nicht in einer Konfigurationsdatei für die Bereitstellung gespeichert werden.

| Umgebungsvariable | Description |
|---|---|---|---|
| **DOCKER_REGISTRY** | Die private Registrierung, in dem die Bilder verwendet, um die Bereitstellung des Clusters gespeichert sind. |
| **DOCKER_REPOSITORY** | Das private Repository in der oben genannten Registrierung, in dem Bilder gespeichert sind. |
| **DOCKER_USERNAME** | Der Benutzername für die containerimages zugreifen, falls sie in einem privaten Repository gespeichert sind. |
| **DOCKER_PASSWORD** | Das Kennwort für den Zugriff auf das obige privaten Repository. |
| **DOCKER_IMAGE_TAG** | Die Bezeichnung, die Bilder zu kennzeichnen. Standardmäßig **neueste**, aber es wird empfohlen, unter Verwendung des Tags, die für die Version zu Versionsprobleme mit Inkompatibilität vermieden. |
| **CONTROLLER_USERNAME** | Der Benutzername für die Clusterverwaltung. |
| **CONTROLLER_PASSWORD** | Das Kennwort für die Clusterverwaltung. |
| **KNOX_PASSWORD** | Das Kennwort für Knox-Benutzer. |
| **MSSQL_SA_PASSWORD** | Das Kennwort des SA-Benutzers für die master-SQL-Instanz. |

Diese Umgebungsvariablen festgelegt werden müssen, vor dem Aufruf **Mssqlctl Clustererstellung**. Wenn eine beliebige Variable nicht festgelegt ist, werden Sie dafür aufgefordert.

Das folgende Beispiel zeigt, wie Sie die Umgebungsvariablen für Linux (Bash) und Windows (PowerShell) festgelegt wird:

```bash
export CONTROLLER_USERNAME=<controller_user>
export CONTROLLER_PASSWORD=<password>
export DOCKER_REGISTRY=<docker-registry>
export DOCKER_REPOSITORY=<docker-repository>
export MSSQL_SA_PASSWORD=<password>
export KNOX_PASSWORD=<password>
export DOCKER_USERNAME=<docker-username>
export DOCKER_PASSWORD=<docker-password>
export DOCKER_IMAGE_TAG=ctp2.5
```

```PowerShell
SET CONTROLLER_USERNAME=admin
SET CONTROLLER_PASSWORD=<password>
SET DOCKER_REGISTRY=<docker-registry>
SET DOCKER_REPOSITORY=<docker-repository>
SET MSSQL_SA_PASSWORD=<password>
SET KNOX_PASSWORD=<password>
SET DOCKER_USERNAME=<docker-username>
SET DOCKER_PASSWORD=<docker-password>
SET DOCKER_IMAGE_TAG=ctp2.5
```

Sie müssen beim Festlegen der Umgebungsvariablen, ausführen `mssqlctl cluster create` um die Bereitstellung auszulösen. Dieses Beispiel verwendet die oben erstellte Cluster-Konfigurationsdatei:

```
mssqlctl cluster create --config-file custom.json --accept-eula yes
```

Beachten Sie die folgenden Richtlinien:

- Zu diesem Zeitpunkt Anmeldeinformationen für die private Docker-Registrierung werden bereitgestellt werden, um Sie beim selektieren Ihre [Early Adoption Program Registrierung](https://aka.ms/eapsignup). Early Adoption Program-Registrierung ist erforderlich, um SQL Server-big Data-Cluster zu testen.
- Stellen Sie sicher, dass Sie die Kennwörter in doppelte Anführungszeichen umschließen, wenn sie keine Sonderzeichen enthält. Sie können festlegen, die **MSSQL_SA_PASSWORD** , was auch immer Sie zufrieden sind, aber stellen Sie sicher, dass das Kennwort ist komplex und verwenden Sie nicht die `!`, `&` oder `'` Zeichen. Beachten Sie, die doppelte Anführungszeichen Trennzeichen funktionieren nur in der bash-Befehle.
- Die **SA** Anmeldename ist ein Systemadministrator für die master SQL Server-Instanz, die während des Setups erstellt wird. Nach dem Erstellen Ihrer SQL Server-Containers, der **MSSQL_SA_PASSWORD** Umgebungsvariable, die Sie angegeben ist mit sichtbaren $MSSQL_SA_PASSWORD im Container ausgeben. Ändern Sie aus Sicherheitsgründen Ihr SA-Kennwort gemäß der dokumentierten bewährten Methoden [hier](../linux/quickstart-install-connect-docker.md#sapassword).
- Die **DOCKER_IMAGE_TAG** in diesem Beispiel steuert, welche Sie Version installieren. In diesem Beispiel ist es der Version CTP-Version 2.5.

## <a id="unattended"></a> Unbeaufsichtigte Installation

Für eine unbeaufsichtigte Bereitstellung, müssen Sie festlegen, alle erforderlichen Umgebungsvariablen, die Verwendung einer Konfigurationsdatei und Aufruf `mssqlctl cluster create` -Befehl mit der `--accept-eula yes` Parameter. Die Beispiele im vorherigen Abschnitt veranschaulicht die Syntax für die unbeaufsichtigte Installation.

## <a id="monitor"></a> Überwachen der Bereitstellung

Während der Cluster-Bootstrap gibt der Client-Befehlsfenster den Bereitstellungsstatus. Während der Bereitstellung sehen Sie eine Reihe von Nachrichten, in dem sie den Pod Controller wartet:

```output
2019-04-12 14:40:10.0129 UTC | INFO | Waiting for controller pod to be up...
```

In weniger als 15 bis 30 Minuten sollten Sie eine Benachrichtigung über der Pod Controller ausgeführt wird:

```output
2019-04-12 15:01:10.0809 UTC | INFO | Waiting for controller pod to be up. Checkthe mssqlctl.log file for more details.
2019-04-12 15:01:40.0861 UTC | INFO | Controller pod is running.
2019-04-12 15:01:40.0884 UTC | INFO | Controller Endpoint: https://<ip-address>:30080
```

> [!IMPORTANT]
> Die gesamte Bereitstellung dauert sehr lange aufgrund der Zeitaufwand für die Container-Images für die Komponenten der big Data-Cluster herunterladen. Er sollte jedoch nicht mehrere Stunden dauern. Wenn Sie Probleme bei der Bereitstellung auftreten, finden Sie unter [Überwachung und Problembehandlung für SQL Server-big Data-Cluster](cluster-troubleshooting-commands.md).

Wenn die Bereitstellung abgeschlossen ist, benachrichtigt die Ausgabe Sie Erfolg:

```output
2019-04-12 15:37:18.0271 UTC | INFO | Monitor and track your cluster at the Portal Endpoint: https://<ip-address>:30777/portal/
2019-04-12 15:37:18.0271 UTC | INFO | Cluster deployed successfully.
```

Beachten Sie die URL von der **Portal Endpunkt** in der vorherigen Ausgabe für die Verwendung im nächsten Abschnitt.

> [!TIP]
> Der Standardname für den Cluster bereitgestellte big Data ist `mssql-cluster` , wenn durch eine benutzerdefinierte Konfiguration geändert.

## <a id="endpoints"></a> Abrufen von Endpunkten

Nachdem das Bereitstellungsskript erfolgreich abgeschlossen wurde, können Sie die IP-Adressen der externen Endpunkte für die big Data-Cluster mit den folgenden Schritten erhalten.

1. Kopieren Sie in der bereitstellungsausgabe der **Portal Endpunkt** und entfernen Sie die `/portal/` am Ende. Dies ist die URL des Management-Proxy (z. B. `https://<ip-address>:30777`).

   > [!TIP]
   > Wenn Sie nicht über die bereitstellungsausgabe verfügen, erhalten Sie die IP-Adresse für den Management-Proxy anhand der EXTERNEN IP-Ausgabe des folgenden **"kubectl"** Befehl:
   >
   > ```bash
   > kubectl get svc mgmtproxy-svc-external -n <your-cluster-name>
   > ```

1. Melden Sie sich bei der big Data-Cluster mit **Mssqlctl Anmeldung**. Legen Sie die **– Endpunkt** Parameter, um den Management-Proxy.

   ```bash
   mssqlctl login --endpoint https://<ip-address>:30777
   ```

   Geben Sie Benutzername und Kennwort, die Sie für den Controller (CONTROLLER_USERNAME und CONTROLLER_PASSWORD) konfiguriert, während der Bereitstellung.

1. Führen Sie **Mssqlctl Endpunkte Clusterliste** um eine Liste mit einer Beschreibung der einzelnen Endpunkten und ihre entsprechenden Werte für IP-Adresse und den Port abzurufen. Folgendes zeigt z. B. die Ausgabe für den Endpunkt-Verwaltungsportal:

   ```output
   {
     "description": "Management Portal",
     "endpoint": "https://<ip-address>:30777/portal",
     "ip": "<ip-address>",
     "name": "portal",
     "port": 30777,
     "protocol": "https"
   },
   ```

1. Alle clusterendpunkte werden ebenfalls beschrieben, der **Dienstendpunkte** Registerkarte im Verwaltungsportal-Cluster. Sie können das Portal mit dem Verwaltungsportal-Endpunkt im vorherigen Schritt zugreifen (z. B. `https://<ip-address>:30777/portal`). Die Anmeldeinformationen für den Zugriff auf das Verwaltungsportal sind die Werte für Controller-Benutzername und Kennwort, das Sie während der Bereitstellung angegeben. Sie können auch das Verwaltungsportal für den Cluster zum Überwachen der Bereitstellung verwenden.

### <a name="minikube"></a>Minikube

Wenn Sie Minikube verwenden, müssen Sie führen den folgenden Befehl zum Abrufen der IP-Adresse, die Sie benötigen für die Verbindung. Geben Sie zusätzlich zu die IP-Adresse den Port für den Endpunkt zum Herstellen einer Verbindung mit erforderlichen aus.

```bash
minikube ip
```

Unabhängig von der Plattform werden Sie Ihren Kubernetes-Cluster, ausgeführt, um alle Dienstendpunkte, die bereitgestellt werden, für den Cluster, führen Sie den folgenden Befehl zu erhalten:

```bash
kubectl get svc -n <your-cluster-name>
```

## <a id="connect"></a> Verbinden mit dem cluster

Weitere Informationen zum Herstellen einer Verbindung mit der big Data-Cluster, finden Sie unter [Herstellen einer Verbindung mit einer SQL Server big Data-cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Bereitstellung von big Data-Clusters finden Sie unter den folgenden Ressourcen:

- [Konfigurieren von bereitstellungseinstellungen für big Data-Cluster](deployment-custom-configuration.md)
- [Führen Sie eine offline-Bereitstellung von einer SQL Server-big Data-cluster](deploy-offline.md)
- [Workshop: Microsoft SQL Server-big Data-Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
