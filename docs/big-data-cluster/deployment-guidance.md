---
title: 'Gewusst wie: Bereitstellen von SQL Server-big Data in Kubernetes-Clustern | Microsoft-Dokumentation'
description: Erfahren Sie, wie Sie SQL Server-2019 big Data-Clustern (Vorschau) in Kubernetes bereitstellen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/08/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: de19577b4a83bc10875bf56f4c0f2924828a00ea
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051182"
---
# <a name="how-to-deploy-sql-server-big-data-cluster-on-kubernetes"></a>Gewusst wie: Bereitstellen von SQL Server, big Data in Kubernetes-cluster

SQL Server-big Data-Cluster kann als Docker-Container in einem Kubernetes-Cluster bereitgestellt werden. Dies ist eine Übersicht über die Schritte für Einrichtung und Konfiguration:

- Richten Sie die Kubernetes-Cluster in einem einzelnen virtuellen Computer, die Cluster von virtuellen Computern oder in Azure Kubernetes Service (AKS).
- Installieren Sie das Cluster-Konfigurationstool **Mssqlctl** auf Ihrem Clientcomputer.
- Bereitstellen von SQL Server-big Data-Cluster in einem Kubernetes-Cluster.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Voraussetzungen für Kubernetes-cluster

SQL Server-big Data-Cluster erfordert eine minimale v1.10-Version, Kubernetes, sowohl Server-als auch. Um eine bestimmte Version auf Kubectl-Client installieren zu können, finden Sie unter [Installieren von Kubectl über Curl binäre](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl).  Neueste Versionen von Minikube und AKS sind mindestens 1.10. Für AKS, benötigen Sie Verwendung `--kubernetes-version` -Parameter eine anderen Version als Standard fest.

> [!NOTE]
> Beachten Sie, dass die Kubernetes-Versionen von Client und Server + 1 oder-1 Nebenversion werden soll. Weitere Informationen finden Sie unter [Kubernetes unterstützte Versionen und Komponenten, die datenschiefe](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Kubernetes-Cluster-setup

Wenn Sie bereits einen Kubernetes-Cluster, die über die Voraussetzungen erfüllt haben, können Sie direkt zu überspringen der [Bereitstellungsschritt](#deploy). In diesem Abschnitt wird ein grundlegendes Verständnis der Kubernetes-Konzepte vorausgesetzt.  Ausführliche Informationen zu Kubernetes finden Sie unter den [Kubernetes-Dokumentation](https://kubernetes.io/docs/home).

Sie können zum Bereitstellen von Kubernetes stehen drei Möglichkeiten zur Verfügung:

| Bereitstellen von Kubernetes auf: | Description |
|---|---|
| **Minikube** | Einen Einzelknoten-Kubernetes-Cluster auf einem virtuellen Computer. |
| **Azure Kubernetes-Dienste (AKS)** | Managed Kubernetes-Container-Dienst in Azure. |
| **Mehrere Computer** | Ein Kubernetes-Cluster bereitgestellt, die auf physischen oder virtuellen Computern mit **Kubeadm** |

Anleitungen dazu eine der folgenden Optionen des Kubernetes-Cluster für eine SQL Server-big Data-Cluster konfigurieren sollten finden Sie in den folgenden Artikeln:

   - [Konfigurieren von Minikube](deploy-on-minikube.md)
   - [Konfigurieren von Kubernetes in Azure Kubernetes Service](deploy-on-aks.md)
   - [Konfigurieren von Kubernetes auf mehreren Computern mit kubeadm](deploy-with-kubeadm.md)
   
> [!TIP]
> Ein Beispiel-Python-Skript, das sowohl AKS und SQL Server-big Data-Cluster bereitgestellt wird, finden Sie unter [stellen Sie eine SQL-Server, die big Data-in Azure Kubernetes Service (AKS Cluster)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a id="deploy"></a> Bereitstellen von SQL Server-big Data-cluster

Nachdem Sie Ihren Kubernetes-Cluster konfiguriert haben, können Sie mit der Bereitstellung für SQL Server-big Data-Cluster fortfahren. Führen Sie die Anweisungen in diesem Artikel, zum Bereitstellen eines big Data-Clusters in Azure mit allen Standardkonfigurationen für eine Dev/Test-Umgebung:

[Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Kubernetes](quickstart-big-data-cluster-deploy.md)

Wenn Sie Ihre big Data-Clusterkonfiguration gemäß Ihren workloadanforderungen anpassen möchten, führen Sie den nächsten Satz von Anweisungen.

## <a name="verify-kubernetes-configuration"></a>Überprüfen der Kubernetes-Konfiguration

Führen Sie die **"kubectl"** Befehl aus, um die Clusterkonfiguration anzuzeigen. Stellen Sie sicher, dass diese "kubectl" auf den richtigen Clusterkontext gezeigt wird.

```bash
kubectl config view
```

## <a id="mssqlctl"></a> Installieren Sie mssqlctl

**Mssqlctl** ist ein Befehlszeilenprogramm, das in Python geschrieben wurde, ermöglicht das Clustern von Administratoren zum Starten und Verwalten der big Data-Cluster über REST-APIs. Die Python-Mindestversion erforderlich ist, V3. 5. Außerdem benötigen Sie `pip` dient zum Herunterladen und installieren **Mssqlctl** Tool. 

### <a name="windows-mssqlctl-installation"></a>Windows-Mssqlctl-installation

1. Laden Sie auf einem Windows-Client die erforderlichen Python-Pakets aus [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Für python3.5.3 und höher, ist auch pip3 installiert, bei der Installation von Python. 

   > [!TIP] 
   > Wählen Sie bei der Installation von Python3 Python zu Ihrem Pfad hinzu. Wenn Sie nicht, können später zu finden, wo sich pip3 befindet und diese manuell zu Ihrem Pfad hinzufügen.

1. Stellen Sie sicher, dass der neueste **Anforderungen** Paket.

   ```cmd
   python -m pip install requests
   python -m pip install requests --upgrade
   ```

1. Installieren Sie **Mssqlctl** mit den folgenden Befehl aus:

   ```bash
   pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
   ```

### <a name="linux-mssqlctl-installation"></a>Linux-Mssqlctl-installation

Unter Linux müssen Sie installieren die **python3** und **python3-Pip** Pakete aus, und führen Sie dann `sudo pip3 install --upgrade pip`. Dadurch wird die neueste 3.5-Version von Python und Pip installiert. Das folgende Beispiel zeigt, wie diese Befehle für Ubuntu funktionieren würde (Wenn Sie eine andere Plattform verwenden, ändern Sie die Befehle für Ihr Paket-Manager):

1. Installieren Sie die erforderlichen Python-Pakete:

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip && /
   sudo -H pip3 install --upgrade pip
   ```

1. Stellen Sie sicher, dass der neueste **Anforderungen** Paket.

   ```bash
   sudo -H python3 -m pip install requests
   sudo -H python3 -m pip install requests --upgrade
   ```

1. Installieren Sie **Mssqlctl** mit den folgenden Befehl aus:

   ```bash
   pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl
   ```

## <a name="define-environment-variables"></a>Definieren von Umgebungsvariablen

Die Cluster-Konfiguration kann angepasst werden, mithilfe eines Satzes von Umgebungsvariablen, die übergeben werden, die `mssqlctl create cluster` Befehl. Die meisten der Umgebungsvariablen sind optional, mit Standardwerten nach unten. Beachten Sie, dass Umgebungsvariablen wie Anmeldeinformationen, die eine Benutzereingabe erfordern.

| Umgebungsvariable | Required | Standardwert | Description |
|---|---|---|---|
| **ACCEPT_EULA** | Benutzerkontensteuerung | – | Akzeptieren Sie den SQL Server-Lizenzvertrag (z. B. "Y").  |
| **CLUSTERNAME** | Benutzerkontensteuerung | – | Der Name des zu SQL Server bereitstellen, big Data-in Cluster, Kubernetes-Namespace. |
| **CLUSTER_PLATFORM** | Benutzerkontensteuerung | – | Die Plattform des Kubernetes-Clusters bereitgestellt wird. Kann `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | nein | 1 | Die Anzahl der Compute-Pool Replikate zu erstellen. In CTP2. 0 nur Wert zulässig ist 1. |
| **CLUSTER_DATA_POOL_REPLICAS** | nein | 2 | Die Anzahl der Pools Replikate zu erstellen. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | nein | 2 | Die Anzahl der Speicher-Pool Replikate zu erstellen. |
| **DOCKER_REGISTRY** | Benutzerkontensteuerung | TBD | Die private Registrierung, in dem die Bilder verwendet, um die Bereitstellung des Clusters gespeichert sind. |
| **DOCKER_REPOSITORY** | Benutzerkontensteuerung | TBD | Das private Repository in der oben genannten Registrierung, in dem Bilder gespeichert sind.  Es ist erforderlich, für die Dauer der geschlossene öffentliche Vorschauversion. |
| **DOCKER_USERNAME** | Benutzerkontensteuerung | – | Der Benutzername für die containerimages zugreifen, falls sie in einem privaten Repository gespeichert sind. Es ist erforderlich, für die Dauer der geschlossene öffentliche Vorschauversion. |
| **DOCKER_PASSWORD** | Benutzerkontensteuerung | – | Das Kennwort für den Zugriff auf das obige privaten Repository. Es ist erforderlich, für die Dauer der geschlossene öffentliche Vorschauversion.|
| **DOCKER_EMAIL** | Benutzerkontensteuerung | – | Die e-Mail, die dem obigen privaten Repository zugeordnet wird. Er ist für die Dauer der privaten Vorschau abgegrenzten erforderlich. |
| **DOCKER_IMAGE_TAG** | nein | Neueste | Die Bezeichnung, die Bilder zu kennzeichnen. |
| **DOCKER_IMAGE_POLICY** | nein | Always | Erzwingt immer einen Abruf der Bilder.  |
| **DOCKER_PRIVATE_REGISTRY** | Benutzerkontensteuerung | 1 | Für den Zeitrahmen für die geschlossene öffentliche Vorschauversion werden soll muss dieser Wert auf 1 festgelegt werden. |
| **CONTROLLER_USERNAME** | Benutzerkontensteuerung | – | Der Benutzername für die Clusterverwaltung. |
| **CONTROLLER_PASSWORD** | Benutzerkontensteuerung | – | Das Kennwort für die Clusterverwaltung. |
| **KNOX_PASSWORD** | Benutzerkontensteuerung | – | Das Kennwort für Knox-Benutzer. |
| **MSSQL_SA_PASSWORD** | Benutzerkontensteuerung | – | Das Kennwort des SA-Benutzers für die master-SQL-Instanz. |
| **USE_PERSISTENT_VOLUME** | nein | true | `true` Persistentes Kubernetes-Volume verwenden Ansprüche für den Pod-Speicher.  `false` für die Verwendung kurzlebiger Hostspeicher Pod-Speicher. Finden Sie unter den [Datenpersistenz](concept-data-persistence.md) finden Sie weitere Details. Wenn Sie SQL Server, die big Data-in Minikube Cluster und USE_PERSISTENT_VOLUME bereitstellen = "true", Sie müssen den Wert festlegen für `STORAGE_CLASS_NAME=standard`. |
| **STORAGE_CLASS_NAME** | nein | default | Wenn `USE_PERSISTENT_VOLUME` ist `true` Dies gibt den Namen der Kubernetes-Speicher-Klasse verwenden. Finden Sie unter den [Datenpersistenz](concept-data-persistence.md) finden Sie weitere Details. Wenn Sie SQL Server bereitstellen, big Data-in Minikube Cluster, unterscheidet sich der Standardklassenname für Speicher und müssen Sie Sie überschreiben, indem Sie festlegen `STORAGE_CLASS_NAME=standard`. |
| **MASTER_SQL_PORT** | nein | 31433 | Der TCP/IP-Port, den die master-SQL-Instanz an das öffentliche Netzwerk lauscht. |
| **KNOX_PORT** | nein | 30443 | Der TCP/IP-Port, den auf Apache Knox im öffentlichen Netzwerk lauscht. |
| **GRAFANA_PORT** | nein | 30888 | Der TCP/IP-Port, den die überwachungsanwendung Grafana im öffentlichen Netzwerk lauscht. |
| **KIBANA_PORT** | nein | 30999 | Der TCP/IP-Port, den auf die Kibana-Log-Suchanwendung im öffentlichen Netzwerk lauscht. |

> [!IMPORTANT]
>1. Für die Dauer der eingeschränkten privaten Vorschauversion, Anmeldeinformationen für die private Docker-Registrierung erfolgt Sie bei der Selektierung Ihre [EAP-Registrierung](https://aka.ms/eapsignup).
>1. Für ein lokalen Cluster mit erstellt **Kubeadm**, den Wert für Umgebungsvariable `CLUSTER_PLATFORM` ist `kubernetes`. Auch wenn `USE_PERSISTENT_VOLUME=true`, müssen Sie vorab bereitstellen eine Kubernetes-Speicherklasse, und übergeben Sie sie durch die Verwendung der `STORAGE_CLASS_NAME`.
>1. Stellen Sie sicher, dass Sie die Kennwörter in doppelte Anführungszeichen umschließen, wenn sie keine Sonderzeichen enthält. Sie können die MSSQL_SA_PASSWORD beliebig festlegen, aber stellen Sie sicher, dass sie ausreichend komplex sind und verwenden Sie nicht die `!`, `&` oder `‘` Zeichen. Beachten Sie, die doppelte Anführungszeichen Trennzeichen funktionieren nur in der bash-Befehle.
>1. Der Name Ihres Clusters muss nur Kleinbuchstaben alphanumerische Zeichen, keine Leerzeichen enthalten. Alle Kubernetes-Artefakte (Container, Pods, zustandsbehaftete Gruppen, Dienste) für den Cluster in einem Namespace mit demselben Namen wie der Cluster erstellt werden angegebenen Namen.
>1. Die **SA** Konto ist ein Systemadministrator für die Master für SQL Server-Instanz, die während des Setups erstellt wird. Nachdem erstellen Ihre SQL Server-Container, die MSSQL_SA_PASSWORD-Umgebungsvariable, die Sie angegeben haben erkennbar ausgeführt ist echo $MSSQL_SA_PASSWORD im Container. Ändern Sie aus Sicherheitsgründen Ihr SA-Kennwort gemäß der dokumentierten bewährten Methoden [hier](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Festlegen der Umgebungsvariablen, die für die Bereitstellung eines big Data-Clusters unterscheidet sich je nachdem, ob Sie Windows oder Linux-Client verwenden.  Wählen Sie die folgenden Schritte aus je nach verwendetem, die Betriebssystem Sie verwenden.

Die folgenden Umgebungsvariablen zu initialisieren, sie sind für die Bereitstellung des Clusters erforderlich:

### <a name="windows"></a>Windows

Konfigurieren Sie die folgenden Umgebungsvariablen mit einem CMD-Fenster (nicht PowerShell). Verwenden Sie nicht die Werte in Anführungszeichen ein.

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linux"></a>Linux

Die folgenden Umgebungsvariablen zu initialisieren. In bash bleibt können Sie jeden Wert in Anführungszeichen.

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=<minikube or aks or kubernetes>

export CONTROLLER_USERNAME="<controller_admin_name – can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password – can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password – can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your Docker email, use the username provided by Microsoft>"
export DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="minikube-settings"></a>Minikube-Einstellungen

Wenn Sie auf die Minikube bereitstellen und `USE_PERSISTENT_VOLUME=true` (Standard), müssen Sie auch den Standardwert für überschreiben `STORAGE_CLASS_NAME` -Umgebungsvariablen angegeben.

Verwenden Sie den folgenden Befehl in Windows für Minikube-Bereitstellungen:

```cmd
SET STORAGE_CLASS_NAME=standard
```

Verwenden Sie den folgenden Befehl unter Linux für Minikube-Bereitstellungen:

```bash
export STORAGE_CLASS_NAME=standard
```

Alternativ können Sie unterdrücken, Verwendung von persistenten Volumes durch Festlegen auf Minikube `USE_PERSISTENT_VOLUME=false`.

### <a name="kubadm-settings"></a>Kubadm-Einstellungen

Wenn Sie mit Kubeadm auf Ihren eigenen physischen oder virtuellen Computern bereitstellen, müssen Sie eine Kubernetes-Speicherklasse vorab bereitstellen und übergeben Sie sie durch die Verwendung der `STORAGE_CLASS_NAME`. Alternativ können Sie unterdrücken, Verwendung von persistenten Volumes durch Festlegen von `USE_PERSISTENT_VOLUME=false`. Weitere Informationen zu den beständigen Speicher benötigen, finden Sie unter [Dauerhaftigkeit von Daten mit SQL Server, die big Data-in Kubernetes Cluster](concept-data-persistence.md).

## <a name="deploy-sql-server-big-data-cluster"></a>Bereitstellen von SQL Server Big Data-Clustern

Die Create-Cluster-API dient zum Initialisieren des Kubernetes-Namespaces und den anwendungspods in den Namespace bereitstellen. Führen Sie zum Bereitstellen von SQL Server-big Data-Cluster in Ihrem Kubernetes-Cluster den folgenden Befehl ein:

```bash
mssqlctl create cluster <name of your cluster>
```

Während der Cluster-Bootstrap gibt der Client-Befehlsfenster den Bereitstellungsstatus. Sie können auch den Bereitstellungsstatus überprüfen, indem Sie diese Befehle in einem anderen Cmd-Fenster ausführen:

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

Sie können eine präzisere Status und die Konfiguration für die einzelnen Pod mit finden Sie unter:
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

Sobald der Controller-Pod ausgeführt wird, können Sie auf die Registerkarte "Bereitstellung" im Verwaltungsportal-Cluster zum Überwachen der Bereitstellung nutzen.

## <a id="masterip"></a> Abrufen von Master für SQL Server-Instanz und SQL Server big Data-Cluster-IP-Adressen

Nachdem das Bereitstellungsskript erfolgreich abgeschlossen wurde, können Sie die IP-Adresse mithilfe der unten beschriebenen Schritte master SQL Server-Instanz abrufen. Verwenden Sie diese IP-Adresse und Port-Nummer 31433 für die Verbindung mit der master SQL Server-Instanz (z. B.:  **\<Ip-Adresse\>, 31433**). Auf ähnliche Weise für die SQL Server big Data-Cluster-IP. Alle clusterendpunkte werden auf der Registerkarte "Dienstendpunkte" im Cluster-Verwaltungsportal ebenfalls beschrieben. Sie können das Cluster-Verwaltungsportal verwenden, zum Überwachen der Bereitstellung. Sie können den Portalzugriff mithilfe der externen IP-Adresse und den Port für die `service-proxy-lb` (z. B.: **https://\<Ip-Adresse\>: 30777**). Anmeldeinformationen für den Zugriff auf die Administratorportal die Werte sind `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD` oben angegebenen Umgebungsvariablen.

### <a name="aks"></a>AKS

Wenn Sie ACS verwenden, bietet Azure den Azure-LoadBalancer-Dienst. Führen Sie folgenden Befehl aus:

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
kubectl get svc service-proxy-lb -n <name of your cluster>
```

Suchen Sie nach der **externe IP-** -Wert, der dem Dienst zugewiesen ist. Verbinden Sie anschließend mit der master SQL Server-Instanz, die mit der IP-Adresse über Port 31433 (Beispiel:  **\<Ip-Adresse\>, 31433**) und mit dem External-IP-Adresse für SQL Server-big Data-clusterendpunkt `service-security-lb` Service. 

### <a name="minikube"></a>Minikube

Wenn Sie Minikube verwenden, müssen Sie führen den folgenden Befehl zum Abrufen der IP-Adresse, die Sie benötigen für die Verbindung. Geben Sie zusätzlich zu die IP-Adresse den Port für den Endpunkt zum Herstellen einer Verbindung mit erforderlichen aus. Um die Dienstendpunkte für zu erhalten. 

```bash
minikube ip
```

Unabhängig von der Plattform werden Sie Ihren Kubernetes-Cluster, ausgeführt, um alle Dienstendpunkte, die bereitgestellt werden, für den Cluster, führen Sie den folgenden Befehl zu erhalten:
```bash
kubectl get svc -n <name of your cluster>
```

## <a name="next-steps"></a>Nächste Schritte

Nach der erfolgreichen Bereitstellung von SQL Server, die big Data-mit Kubernetes Cluster, [die big Data-Tools installieren](deploy-big-data-tools.md) und einige der neuen Funktionen testen, und erfahren Sie, [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md).
