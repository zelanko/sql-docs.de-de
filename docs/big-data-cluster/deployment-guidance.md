---
title: 'Gewusst wie: Bereitstellen'
titleSuffix: SQL Server 2019 big data clusters
description: Erfahren Sie, wie Sie SQL Server-2019 big Data-Clustern (Vorschau) in Kubernetes bereitstellen.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 422c09654f214d067b7d1ad7fd8bcca1dfe8f7e8
ms.sourcegitcommit: b51edbe07a0a2fdb5f74b5874771042400baf919
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087859"
---
# <a name="how-to-deploy-sql-server-big-data-clusters-on-kubernetes"></a>Wie Sie SQL Server-big Data-Cluster in Kubernetes bereitstellen

SQL Server-big Data-Cluster kann als Docker-Container in einem Kubernetes-Cluster bereitgestellt werden. Dies ist eine Übersicht über die Schritte für Einrichtung und Konfiguration:

- Richten Sie die Kubernetes-Cluster in einem einzelnen virtuellen Computer, die Cluster von virtuellen Computern oder in Azure Kubernetes Service (AKS).
- Installieren Sie das Cluster-Konfigurationstool **Mssqlctl** auf Ihrem Clientcomputer.
- Bereitstellen von SQL Server-big Data-Cluster in einem Kubernetes-Cluster.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a id="prereqs"></a> Voraussetzungen für Kubernetes-cluster

SQL Server-big Data-Cluster erfordern eine Kubernetes-Mindestversion von mindestens v1.10 für Server und Client (Kubectl).

> [!NOTE]
> Beachten Sie, dass die Kubernetes-Versionen von Client und Server + 1 oder-1 Nebenversion werden soll. Weitere Informationen finden Sie unter [Kubernetes unterstützte Versionen und Komponenten, die datenschiefe](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

## <a id="kubernetes"></a> Kubernetes-Cluster-setup

Wenn Sie bereits einen Kubernetes-Cluster, die über die Voraussetzungen erfüllt haben, können Sie direkt zu überspringen der [Bereitstellungsschritt](#deploy). In diesem Abschnitt wird ein grundlegendes Verständnis der Kubernetes-Konzepte vorausgesetzt.  Ausführliche Informationen zu Kubernetes finden Sie unter den [Kubernetes-Dokumentation](https://kubernetes.io/docs/home).

Sie können zum Bereitstellen von Kubernetes stehen drei Möglichkeiten zur Verfügung:

| Bereitstellen von Kubernetes auf: | Description | Link |
|---|---|---|
| **Minikube** | Einen Einzelknoten-Kubernetes-Cluster auf einem virtuellen Computer. | [Anweisungen](deploy-on-minikube.md) |
| **Azure Kubernetes-Dienste (AKS)** | Managed Kubernetes-Container-Dienst in Azure. | [Anweisungen](deploy-on-aks.md) |
| **Mehrere Computer** | Ein Kubernetes-Cluster bereitgestellt, die auf physischen oder virtuellen Computern mit **Kubeadm** | [Anweisungen](deploy-with-kubeadm.md) |
  
> [!TIP]
> Ein Beispiel-Python-Skript, das sowohl AKS und SQL Server-big Data-Cluster bereitgestellt wird, finden Sie unter [stellen Sie eine SQL-Server, die big Data-in Azure Kubernetes Service (AKS Cluster)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="deploy-sql-server-2019-big-data-tools"></a>Bereitstellen von SQL Server-2019 big Data-tools

Vor der Bereitstellung von SQL Server-2019 big Data-Cluster, zuerst [die big Data-Tools installieren](deploy-big-data-tools.md):
- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **SQL Server-2019-Erweiterung**

## <a id="deploy"></a> Bereitstellen von SQL Server-big Data-cluster

Nachdem Sie Ihren Kubernetes-Cluster konfiguriert haben, können Sie mit der Bereitstellung für SQL Server-big Data-Cluster fortfahren. 

> [!NOTE]
> Wenn Sie von einer früheren Version aktualisieren, finden Sie unter den [Abschnitt dieses Artikels aktualisieren](#upgrade).

Führen Sie die Anweisungen in diesem Artikel, zum Bereitstellen eines big Data-Clusters in Azure mit allen Standardkonfigurationen für eine Dev/Test-Umgebung:

[Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Kubernetes](quickstart-big-data-cluster-deploy.md)

Wenn Sie die Bereitstellung von big Data-Cluster gemäß Ihrer Workload anpassen möchten-Anforderungen die Anweisungen im weiteren Verlauf dieses Artikels.

## <a name="verify-kubernetes-configuration"></a>Überprüfen der Kubernetes-Konfiguration

Führen Sie die **"kubectl"** Befehl aus, um die Clusterkonfiguration anzuzeigen. Stellen Sie sicher, dass diese "kubectl" auf den richtigen Clusterkontext gezeigt wird.

```bash
kubectl config view
```

## <a id="env"></a> Definieren von Umgebungsvariablen

Die Cluster-Konfiguration kann angepasst werden, mithilfe eines Satzes von Umgebungsvariablen, die übergeben werden, die `mssqlctl create cluster` Befehl. Die meisten der Umgebungsvariablen sind optional, mit Standardwerten nach unten. Beachten Sie, dass Umgebungsvariablen wie Anmeldeinformationen, die eine Benutzereingabe erfordern.

| Umgebungsvariable | Erforderlich | Standardwert | Description |
|---|---|---|---|
| **ACCEPT_EULA** | Ja | Nicht zutreffend | Akzeptieren Sie den SQL Server-Lizenzvertrag (z. B. "Y").  |
| **CLUSTER_NAME** | Ja | Nicht zutreffend | Der Name des zu SQL Server bereitstellen, big Data-in Cluster, Kubernetes-Namespace. |
| **CLUSTER_PLATFORM** | Ja | Nicht zutreffend | Die Plattform des Kubernetes-Clusters bereitgestellt wird. Kann `aks`, `minikube`, `kubernetes`|
| **CLUSTER_COMPUTE_POOL_REPLICAS** | Nein | 1 | Die Anzahl der Compute-Pool Replikate zu erstellen. In der CTP-Version 2.2 nur Wert zulässig ist 1. |
| **CLUSTER_DATA_POOL_REPLICAS** | Nein | 2 | Die Anzahl der Pools Replikate zu erstellen. |
| **CLUSTER_STORAGE_POOL_REPLICAS** | Nein | 2 | Die Anzahl der Speicher-Pool Replikate zu erstellen. |
| **DOCKER_REGISTRY** | Ja | TBD | Die private Registrierung, in dem die Bilder verwendet, um die Bereitstellung des Clusters gespeichert sind. |
| **DOCKER_REPOSITORY** | Ja | TBD | Das private Repository in der oben genannten Registrierung, in dem Bilder gespeichert sind.  Es ist erforderlich, für die Dauer der geschlossene öffentliche Vorschauversion. |
| **DOCKER_USERNAME** | Ja | Nicht zutreffend | Der Benutzername für die containerimages zugreifen, falls sie in einem privaten Repository gespeichert sind. Es ist erforderlich, für die Dauer der geschlossene öffentliche Vorschauversion. |
| **DOCKER_PASSWORD** | Ja | Nicht zutreffend | Das Kennwort für den Zugriff auf das obige privaten Repository. Es ist erforderlich, für die Dauer der geschlossene öffentliche Vorschauversion.|
| **DOCKER_EMAIL** | Ja | Nicht zutreffend | Die e-Mail, die dem obigen privaten Repository zugeordnet wird. Er ist für die Dauer der privaten Vorschau abgegrenzten erforderlich. |
| **DOCKER_IMAGE_TAG** | Nein | Neueste | Die Bezeichnung, die Bilder zu kennzeichnen. |
| **DOCKER_IMAGE_POLICY** | Nein | Always | Erzwingt immer einen Abruf der Bilder.  |
| **DOCKER_PRIVATE_REGISTRY** | Ja | 1 | Für den Zeitrahmen für die geschlossene öffentliche Vorschauversion werden soll muss dieser Wert auf 1 festgelegt werden. |
| **CONTROLLER_USERNAME** | Ja | Nicht zutreffend | Der Benutzername für die Clusterverwaltung. |
| **CONTROLLER_PASSWORD** | Ja | Nicht zutreffend | Das Kennwort für die Clusterverwaltung. |
| **KNOX_PASSWORD** | Ja | Nicht zutreffend | Das Kennwort für Knox-Benutzer. |
| **MSSQL_SA_PASSWORD** | Ja | Nicht zutreffend | Das Kennwort des SA-Benutzers für die master-SQL-Instanz. |
| **USE_PERSISTENT_VOLUME** | Nein | true | `true` Persistentes Kubernetes-Volume verwenden Ansprüche für den Pod-Speicher.  `false` für die Verwendung kurzlebiger Hostspeicher Pod-Speicher. Finden Sie unter den [Datenpersistenz](concept-data-persistence.md) finden Sie weitere Details. Wenn Sie SQL Server, die big Data-in Minikube Cluster und USE_PERSISTENT_VOLUME bereitstellen = "true", Sie müssen den Wert festlegen für `STORAGE_CLASS_NAME=standard`. |
| **STORAGE_CLASS_NAME** | Nein | default | Wenn `USE_PERSISTENT_VOLUME` ist `true` Dies gibt den Namen der Kubernetes-Speicher-Klasse verwenden. Finden Sie unter den [Datenpersistenz](concept-data-persistence.md) finden Sie weitere Details. Wenn Sie SQL Server bereitstellen, big Data-in Minikube Cluster, unterscheidet sich der Standardklassenname für Speicher und müssen Sie Sie überschreiben, indem Sie festlegen `STORAGE_CLASS_NAME=standard`. |
| **MASTER_SQL_PORT** | Nein | 31433 | Der TCP/IP-Port, den die master-SQL-Instanz an das öffentliche Netzwerk lauscht. |
| **KNOX_PORT** | Nein | 30443 | Der TCP/IP-Port, den auf Apache Knox im öffentlichen Netzwerk lauscht. |
| **GRAFANA_PORT** | Nein | 30888 | Der TCP/IP-Port, den die überwachungsanwendung Grafana im öffentlichen Netzwerk lauscht. |
| **KIBANA_PORT** | Nein | 30999 | Der TCP/IP-Port, den auf die Kibana-Log-Suchanwendung im öffentlichen Netzwerk lauscht. |

> [!IMPORTANT]
>1. Für die Dauer der eingeschränkten privaten Vorschauversion, Anmeldeinformationen für die private Docker-Registrierung erfolgt Sie bei der Selektierung Ihre [EAP-Registrierung](https://aka.ms/eapsignup).
>1. Für ein lokalen Cluster mit erstellt **Kubeadm**, den Wert für Umgebungsvariable `CLUSTER_PLATFORM` ist `kubernetes`. Auch wenn `USE_PERSISTENT_VOLUME=true`, müssen Sie vorab bereitstellen eine Kubernetes-Speicherklasse, und übergeben Sie sie durch die Verwendung der `STORAGE_CLASS_NAME`.
>1. Stellen Sie sicher, dass Sie die Kennwörter in doppelte Anführungszeichen umschließen, wenn sie keine Sonderzeichen enthält. Sie können die MSSQL_SA_PASSWORD beliebig festlegen, aber stellen Sie sicher, dass sie ausreichend komplex sind und verwenden Sie nicht die `!`, `&` oder `'` Zeichen. Beachten Sie, die doppelte Anführungszeichen Trennzeichen funktionieren nur in der bash-Befehle.
>1. Der Name Ihres Clusters muss nur Kleinbuchstaben alphanumerische Zeichen, keine Leerzeichen enthalten. Alle Kubernetes-Artefakte (Container, Pods, zustandsbehaftete Gruppen, Dienste) für den Cluster in einem Namespace mit demselben Namen wie der Cluster erstellt werden angegebenen Namen.
>1. Die **SA** Konto ist ein Systemadministrator für die Master für SQL Server-Instanz, die während des Setups erstellt wird. Nachdem erstellen Ihre SQL Server-Container, die MSSQL_SA_PASSWORD-Umgebungsvariable, die Sie angegeben haben erkennbar ausgeführt ist echo $MSSQL_SA_PASSWORD im Container. Ändern Sie aus Sicherheitsgründen Ihr SA-Kennwort gemäß der dokumentierten bewährten Methoden [hier](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Festlegen der Umgebungsvariablen, die für die Bereitstellung eines big Data-Clusters unterscheidet sich je nachdem, ob Sie Windows oder Linux-Client verwenden.  Wählen Sie die folgenden Schritte aus je nach verwendetem, die Betriebssystem Sie verwenden.

Die folgenden Umgebungsvariablen zu initialisieren, sie sind für die Bereitstellung des Clusters erforderlich:

### <a name="windows"></a>Windows

Konfigurieren Sie die folgenden Umgebungsvariablen mit einem CMD-Fenster (nicht PowerShell). Verwenden Sie nicht die Werte in Anführungszeichen ein.

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=<minikube or aks or kubernetes>

SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
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

export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
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
mssqlctl create cluster <your-cluster-name>
```

Während der Cluster-Bootstrap gibt der Client-Befehlsfenster den Bereitstellungsstatus. Während der Bereitstellung sehen Sie eine Reihe von Nachrichten, in dem sie den Pod Controller wartet:

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Nach 10 bis 20 Minuten sollten Sie eine Benachrichtigung über der Pod Controller ausgeführt wird:

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.222.222.222:30080
```

> [!IMPORTANT]
> Die gesamte Bereitstellung dauert sehr lange aufgrund der Zeitaufwand für die Container-Images für die Komponenten der big Data-Cluster herunterladen. Er sollte jedoch nicht mehrere Stunden dauern. Wenn Sie Probleme bei der Bereitstellung auftreten, finden Sie unter den [Problembehandlung](#troubleshoot) Abschnitt dieses Artikels erfahren Sie, wie zum Überwachen und überprüfen die Bereitstellung.

Wenn die Bereitstellung abgeschlossen ist, benachrichtigt die Ausgabe Sie Erfolg:

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

## <a id="masterip"></a> Abrufen von Master für SQL Server-Instanz und SQL Server big Data-Cluster-IP-Adressen

Nachdem das Bereitstellungsskript erfolgreich abgeschlossen wurde, können Sie die IP-Adresse mithilfe der unten beschriebenen Schritte master SQL Server-Instanz abrufen. Verwenden Sie diese IP-Adresse und Port-Nummer 31433 für die Verbindung mit der master SQL Server-Instanz (z. B.:  **\<Ip-Adresse\>, 31433**). Auf ähnliche Weise für die SQL Server big Data-Cluster-IP. Alle clusterendpunkte werden auf der Registerkarte "Dienstendpunkte" im Cluster-Verwaltungsportal ebenfalls beschrieben. Sie können das Cluster-Verwaltungsportal verwenden, zum Überwachen der Bereitstellung. Sie können den Portalzugriff mithilfe der externen IP-Adresse und den Port für die `service-proxy-lb` (z. B.: **https://\<Ip-Adresse\>: 30777/Portal**). Anmeldeinformationen für den Zugriff auf die Administratorportal die Werte sind `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD` oben angegebenen Umgebungsvariablen.

### <a name="aks"></a>AKS

Wenn Sie ACS verwenden, bietet Azure den Azure-LoadBalancer-Dienst. Führen Sie folgenden Befehl aus:

```bash
kubectl get svc endpoint-master-pool -n <your-cluster-name>
kubectl get svc service-security-lb -n <your-cluster-name>
kubectl get svc service-proxy-lb -n <your-cluster-name>
```

Suchen Sie nach der **externe IP-** -Wert, der dem Dienst zugewiesen ist. Verbinden Sie anschließend mit der master SQL Server-Instanz, die mit der IP-Adresse über Port 31433 (Beispiel:  **\<Ip-Adresse\>, 31433**) und mit dem External-IP-Adresse für SQL Server-big Data-clusterendpunkt `service-security-lb` Service. 

### <a name="minikube"></a>Minikube

Wenn Sie Minikube verwenden, müssen Sie führen den folgenden Befehl zum Abrufen der IP-Adresse, die Sie benötigen für die Verbindung. Geben Sie zusätzlich zu die IP-Adresse den Port für den Endpunkt zum Herstellen einer Verbindung mit erforderlichen aus. Um die Dienstendpunkte für zu erhalten. 

```bash
minikube ip
```

Unabhängig von der Plattform werden Sie Ihren Kubernetes-Cluster, ausgeführt, um alle Dienstendpunkte, die bereitgestellt werden, für den Cluster, führen Sie den folgenden Befehl zu erhalten:
```bash
kubectl get svc -n <your-cluster-name>
```

## <a id="upgrade"></a> Ein Upgrade auf eine neue Version

Derzeit ist die einzige Möglichkeit, einen big Data-Cluster auf eine neue Version ein upgrade manuell entfernen und erstellen Sie den Cluster neu. Jede Version weist eine eindeutige Version **Mssqlctl** , die nicht mit der vorherigen Version kompatibel ist. Darüber hinaus, wenn ein ältere Cluster ein Image auf einem neuen Knoten herunterzuladen musste, kann das neueste Image mit den älteren Images auf dem Cluster nicht kompatibel. Um auf die neueste Version aktualisieren, verwenden Sie die folgenden Schritte aus:

1. Sichern Sie vor dem Löschen der alten Clusters, die Daten auf dem SQL Server-Masterinstanz und HDFS aus. Für die master SQL Server-Instanz, können Sie [SQL Server-Sicherung und Wiederherstellung](data-ingestion-restore-database.md). Für HDFS Sie [können die Daten mit Kopieren **curl**](data-ingestion-curl.md).

1. Löschen Sie den alten Cluster mit der `mssqlctl delete cluster` Befehl.

   ```bash
    mssqlctl delete cluster <old-cluster-name>
   ```

1. Deinstallieren Sie alten Versionen von **Mssqlctl**.

   ```bash
   pip3 uninstall mssqlctl
   ```

   > [!IMPORTANT]
   > Sie sollten nicht installieren, die neue Version der **Mssqlctl** ohne deinstallieren zunächst älteren Versionen.

1. Installieren Sie die neueste Version des **Mssqlctl**. 
   
   **Windows:**

   ```powershell
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

   **Linux:**
   
   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl --user
   ```

   > [!IMPORTANT]
   > Für jede Version, die den Pfad zur **Mssqlctl** Änderungen. Wenn Sie zuvor installiert **Mssqlctl**, installieren Sie erneut aus dem aktuellen Pfad vor dem Erstellen des neuen Clusters.

1. Installieren Sie die neueste Version, die mithilfe der Anweisungen in der [Abschnitt bereitstellen](#deploy) dieses Artikels. 

## <a id="troubleshoot"></a> Überwachung und Problembehandlung

Verwenden Sie zum Überwachen und Problembehandlung bei einer Bereitstellung **"kubectl"** , den Status des Clusters zu überprüfen und potenzielle Probleme zu erkennen. Jederzeit während der Bereitstellung können Sie einen anderen Befehlsfenster zum Ausführen der folgenden Tests öffnen.

1. Überprüfen Sie den Status der Pods in Ihrem Cluster.

   ```cmd
   kubectl get pods -n <your-cluster-name>
   ```

   Pods enthalten sind während der Bereitstellung mit einem **STATUS** von **ContainerCreating** sind Sie weiterhin verfügbar. Wenn die Bereitstellung aus irgendeinem Grund hängt, kann diese eine Vorstellung erhalten Sie, wo das Problem möglicherweise. Betrachten Sie auch die **bereit** Spalte. Dadurch sehen Sie in den Pod wie viele Container gestartet haben. Beachten Sie, dass es sich bei Bereitstellungen auf 30 Minuten oder länger, je nach Konfiguration und Netzwerk ausführen können. Ein Großteil dieser Zeit wird für das Herunterladen der Container-Images für verschiedene Komponenten. Die folgende Tabelle zeigt bearbeitet Beispielausgabe von zwei Containern während der Bereitstellung:

   ```output
   PS C:\> kubectl get pods -n sbdc8
   NAME                                     READY   STATUS              RESTARTS   AGE
   mssql-controller-h79ft                   4/4     Running             0          13m
   mssql-storage-pool-default-0             0/7     ContainerCreating   0          6m
   ```

1. Einen einzelnen Pod für Weitere Informationen zu beschreiben. Der folgende Befehl überprüft die `mssql-storage-pool-default-0` Pod.

   ```cmd
   kubectl describe pod mssql-storage-pool-default-0 -n <your-cluster-name>
   ```

   Dies gibt ausführliche Informationen zu den Pod, einschließlich der aktuellsten Ereignisse. Wenn ein Fehler aufgetreten ist, finden Sie hier manchmal.

1. Rufen Sie die Protokolle für Container, die in einem Pod ausgeführt. Der folgende Befehl ruft die Protokolle für alle Container, die auf den Pod, der mit dem Namen `mssql-storage-pool-default-0` und gibt sie an einen Dateinamen `pod-logs.txt`:

   ```cmd
   kubectl logs mssql-storage-pool-default-0 --all-containers=true -n <your-cluster-name> > pod-logs.txt
   ```

1. Überprüfen Sie die Clusterdienste, während und nach einer Bereitstellung mit den folgenden Befehl aus:

   ```cmd
   kubectl get svc -n <your-cluster-name>
   ```

   Diese Dienste unterstützen die interne und externe Verbindungen mit der big Data-Cluster. Für externe Verbindungen dienen die folgenden Dienste:

   | Dienst | Description |
   |---|---|
   | **endpoint-master-pool** | Bietet Zugriff auf die master-Instanz.<br/>(**Externe IP-, 31433** und **SA** Benutzer) |
   | **service-mssql-controller-lb**<br/>**service-mssql-controller-nodeport** | Unterstützt die Tools und Clients, die den Cluster zu verwalten. |
   | **service-proxy-lb**<br/>**service-proxy-nodeport** | Ermöglicht den Zugriff auf die [Cluster Verwaltungsportal](cluster-admin-portal.md).<br/>(https://**EXTERNAL-IP**:30777/portal)|
   | **service-security-lb**<br/>**service-security-nodeport** | Bietet Zugriff auf das HDFS/Spark-Gateway.<br/>(**Externe IP-** und **Stamm** Benutzer) |

   > [!NOTE]
   > Den Namen des Diensts können je nach Ihrer Kubernetes-Umgebung variieren. Wenn Sie auf der Azure Kubernetes Service (AKS) bereitstellen, den Namen des Diensts enden **-lb**. Für Bereitstellungen von Minikube und Kubeadm, den Namen des Diensts enden **- Nodeport**.

1. Verwenden der [Cluster Verwaltungsportal](cluster-admin-portal.md) zum Überwachen der Bereitstellung auf die **Bereitstellung** Registerkarte. Müssen Sie warten, bis die **-Dienst-Proxy-lb** Dienst zu starten, bevor Sie den Zugriff auf dieses Portal, damit sie am Anfang einer Bereitstellungstyps nicht verfügbar sein werden.

> [!TIP]
> Weitere Informationen zur Problembehandlung des Clusters finden Sie unter ["kubectl"-Befehle zur Überwachung und Problembehandlung von SQL Server-big Data-Cluster](cluster-troubleshooting-commands.md).

## <a name="next-steps"></a>Nächste Schritte

Probieren Sie einige der neuen Funktionen, und erfahren Sie, [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md).
