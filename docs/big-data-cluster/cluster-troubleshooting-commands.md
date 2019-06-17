---
title: Überwachung und Problembehandlung
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält Befehle für die Überwachung und Problembehandlung von eines SQL Server-2019 big Data-Clusters (Vorschau).
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 232c39e6a98f7f55fa3a653735f39c9607fbcbf4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800737"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>Überwachung und Problembehandlung für SQL Server-big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt verschiedene nützliche Kubernetes-Befehle, die Sie verwenden können, um die Überwachung und Problembehandlung für eine SQL Server-2019 big Data-Cluster (Vorschau). Es zeigt, wie ausführliche Details des einen Pod oder andere Kubernetes-Artefakte, die in der big Data-Cluster befinden. Dieser Artikel behandelt auch allgemeine Aufgaben, wie das Kopieren von Dateien zu oder von einem Container mit einem der SQL Server-Dienste für die big Data-Cluster.

> [!TIP]
> Führen Sie den folgenden **"kubectl"** Befehle auf einem Windows ("Cmd" oder "PS") oder Linux (Bash)-Client-Computer. Sie benötigen die vorherigen Authentifizierung im Cluster und zur Ausführung in einem Clusterkontext. Z. B. für einen zuvor erstellten AKS-Cluster können ausführen `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` zum Herunterladen der Konfigurationsdatei des Kubernetes-Cluster und Festlegen des clusterkontexts.

## <a name="get-status-of-pods"></a>Abrufen des Status des pods

Sie können die `kubectl get pods` Befehl aus, um den Status des Pods im Cluster für alle Namespaces oder big Data-Cluster-Namespaces abzurufen. In den folgenden Abschnitten sind Beispiele für beide.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Anzeigen von Status alle Pods im Kubernetes-cluster

Führen Sie dem folgenden Befehl aus, um alle Pods und deren Status, einschließlich der Pods, die Teil des Namespace zu erhalten, dass SQL Server-Pods für big Data-Cluster erstellt werden:

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Status alle Pods in der SQL Server-big Data-Cluster anzeigen

Verwenden der `-n` Parameter, um einen bestimmten Namespace anzugeben. Beachten Sie, dass SQL Server, big Data-Cluster-Pods in einem neuen Namespace erstellt bei bootstrap des Clusters basierend auf den Namen des Clusters angegeben wird, in der Konfigurationsdatei der Bereitstellung erstellt werden. Der Standardname `mssql-cluster`, wird hier verwendet.

```bash
kubectl get pods -n mssql-cluster
```

Daraufhin sollte eine Ausgabe ähnlich der folgenden Liste für eine Ausführung von big Data-Cluster:

```output
PS C:\> kubectl get pods -n mssql-cluster
NAME              READY   STATUS    RESTARTS   AGE
appproxy-f2qqt    2/2     Running   0          110m
compute-0-0       3/3     Running   0          110m
control-zlncl     4/4     Running   0          118m
data-0-0          3/3     Running   0          110m
data-0-1          3/3     Running   0          110m
gateway-0         2/2     Running   0          109m
logsdb-0          1/1     Running   0          112m
logsui-jtdnv      1/1     Running   0          112m
master-0          7/7     Running   0          110m
metricsdb-0       1/1     Running   0          112m
metricsdc-shv2f   1/1     Running   0          112m
metricsui-9bcj7   1/1     Running   0          112m
mgmtproxy-x6gcs   2/2     Running   0          112m
nmnode-0-0        1/1     Running   0          110m
storage-0-0       7/7     Running   0          110m
storage-0-1       7/7     Running   0          110m
```

> [!NOTE]
> Pods enthalten sind während der Bereitstellung mit einem **STATUS** von **ContainerCreating** sind Sie weiterhin verfügbar. Wenn die Bereitstellung aus irgendeinem Grund hängt, kann diese eine Vorstellung erhalten Sie, wo das Problem möglicherweise. Betrachten Sie auch die **bereit** Spalte. Dadurch sehen Sie in den Pod wie viele Container gestartet haben. Beachten Sie, dass es sich bei Bereitstellungen auf 30 Minuten oder länger, je nach Konfiguration und Netzwerk ausführen können. Ein Großteil dieser Zeit wird für das Herunterladen der Container-Images für verschiedene Komponenten.

## <a name="get-pod-details"></a>Abrufen von Pod-details

Führen Sie den folgenden Befehl aus, um eine ausführliche Beschreibung der einen bestimmten Pod in der Ausgabe im JSON-Format zu erhalten. Sie enthält Details wie der aktuelle Kubernetes-Knoten, dem der Pod, den in den Pod und das Bild ab, das Bootstrapping für den Container ausgeführten Containern gespeichert wird. Außerdem zeigt weitere Details wie Status, Bezeichnungen und persistenten Volumes-Ansprüche, die den Pod zugeordnet sind.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

Das folgende Beispiel zeigt die Details für die `master-0` Pods in einem big Data-Cluster mit dem Namen `mssql-cluster`:

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

Wenn Fehler aufgetreten sind, sehen Sie gelegentlich den Fehler in der aktuellen Ereignisse für den Pod.

## <a name="get-pod-logs"></a>Abrufen von Pod-Protokollen

Sie können die Protokolle für Container, ausgeführt in einem Pod abrufen. Der folgende Befehl ruft die Protokolle für alle Container, die auf den Pod, der mit dem Namen `master-0` und gibt sie an einen Dateinamen `master-0-pod-logs.txt`:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a> Abrufen des Status von Diensten

Führen Sie den folgenden Befehl zum Abrufen von Details für die big Data-Clusterdienste. Zu diesen Details zählen, deren Typ aus, und die IP-Adressen, die mit der jeweiligen Dienste und Ports verknüpft ist. Beachten Sie, dass SQL Server-big Data-Cluster-Dienste in einem neuen Namespace, der bei bootstrap des Clusters basierend auf den Namen des Clusters angegeben wird, in der Bereitstellungskonfigurationsdatei erstellt erstellt werden.

```bash
kubectl get svc -n <namespace_name>
```

Das folgende Beispiel zeigt den Status für Dienste in einer big Data-Cluster mit dem Namen `mssql-cluster`:

```bash
kubectl get svc -n mssql-cluster
```

Die folgenden Dienste unterstützen, externe Verbindungen mit der big Data-Cluster:

| Dienst | Beschreibung |
|---|---|
| **master-svc-external** | Bietet Zugriff auf die master-Instanz.<br/>(**Externe IP-, 31433** und **SA** Benutzer) |
| **controller-svc-external** | Unterstützt die Tools und Clients, die den Cluster zu verwalten. |
| **mgmtproxy-svc-external** | Ermöglicht den Zugriff auf die [Cluster Verwaltungsportal](cluster-admin-portal.md).<br/>(https://**EXTERNAL-IP**:30777/portal) |
| **gateway-svc-external** | Bietet Zugriff auf das HDFS/Spark-Gateway.<br/>(**Externe IP-** und **Stamm** Benutzer) |
| **appproxy-svc-external** | Bereitstellungsszenarien für die Anwendung zu unterstützen. |

> [!TIP]
> Dies ist eine Möglichkeit zum Anzeigen der Dienste mit **"kubectl"** , aber es ist auch möglich, verwenden Sie `mssqlctl cluster endpoint list` Befehl, um diese Endpunkte anzuzeigen. Weitere Informationen finden Sie unter [erhalten Sie big Data-clusterendpunkte](deployment-guidance.md#endpoints).

## <a name="get-service-details"></a>Abrufen von Dienstdetails

Führen Sie diesen Befehl aus, um eine ausführliche Beschreibung eines Diensts in der Ausgabe im JSON-Format zu erhalten. Es enthält Details wie z. B. "Bezeichnungen", Selektor externe IP-(wenn der Dienst des Typs der LoadBalancer ist) IP-Adresse, port usw.

```bash
kubectl describe service <service_name> -n <namespace_name>
```

Das folgende Beispiel ruft die Details für die **Master-svc-External** Dienst:

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>Führen Sie Befehle in einem container

Wenn die vorhandenen Tools oder die Infrastruktur nicht auf eine bestimmte Aufgabe durchzuführen, ohne tatsächlich im Kontext des Containers werden können, Sie können melden Sie sich im Container mit `kubectl exec` Befehl. Beispielsweise müssen Sie überprüfen, ob eine bestimmte Datei vorhanden ist oder Sie Dienste im Container neu zu starten möchten. 

Verwenden der `kubectl exec` Befehl können Sie die folgende Syntax:

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

Die folgenden beiden Abschnitte bieten zwei Beispiele für die Ausführung eines Befehls in einem bestimmten Container.

### <a id="restartsql"></a> Melden Sie sich bei einem bestimmten Container, und starten Sie SQL Server-Prozess

Das folgende Beispiel zeigt die Vorgehensweise beim Neustart von SQL Server-Prozess in der `mssql-server` -Container in der `master-0` Pod:

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> Melden Sie sich bei einem bestimmten Container, und starten Sie Dienste in einem Container neu.
 
Das folgende Beispiel zeigt die Vorgehensweise beim Neustart aller Dienste, die von verwalteten **Supervisord**: 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a> Kopieren von Dateien

Wenn Sie Dateien aus dem Container auf Ihrem lokalen Computer kopieren möchten, verwenden Sie `kubectl cp` Befehl mit folgender Syntax:

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

Auf ähnliche Weise können Sie `kubectl cp` Dateien aus dem lokalen Computer in einem bestimmten Container zu kopieren.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a> Kopieren von Dateien aus einem container

Das folgende Beispiel kopiert die SQL Server-Protokolldateien aus dem Container um den `~/temp/sqlserverlogs` Pfad auf dem lokalen Computer (in diesem Beispiel ist der lokale Computer einen Linux-Client):

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> Kopieren von Dateien in container

Das folgende Beispiel kopiert die **AdventureWorks2016CTP3.bak** -Datei aus dem lokalen Computer auf den SQL Server-Masterinstanz Container (`mssql-server`) in der `master-0` Pod. Die Datei wird kopiert, um die `/tmp` Verzeichnis im Container. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a> Force Delete ein pod
 
Es empfiehlt sich nicht um einen Pod-Force-löschen. Zum Testen von Verfügbarkeit, resilienz und Dauerhaftigkeit von Daten, Sie können jedoch löschen einen Pod zum Simulieren eines Fehlers im Pod der `kubectl delete pods` Befehl.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

Das folgende Beispiel löscht den Speicher-Pool-Pod `storage-0-0`:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a> Abrufen von Pod-IP
 
Für die Problembehandlung müssen Sie die IP-Adresse des Knotens abzurufen, die ein Pod zurzeit ausgeführt wird. Rufen Sie die IP-Adresse mit der `kubectl get pods` Befehl mit folgender Syntax:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

Im folgenden Beispiel wird der IP-Adresse des Knotens an, die die `master-0` Pod ausgeführt wird:

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="cluster-administration-portal"></a>Cluster-Verwaltungsportal

Verwenden der [Cluster Verwaltungsportal](cluster-admin-portal.md) zum Überwachen des Status von Ihrer big Data-Cluster. Z. B. während der Bereitstellung, können Sie die **Bereitstellung** Registerkarte. Sie müssen warten, bis die **Mgmtproxy-svc-External** Dienst zu starten, bevor Sie den Zugriff auf dieses Portal, damit sie am Anfang einer Bereitstellungstyps nicht verfügbar sein werden.

## <a name="kubernetes-dashboard"></a>Kubernetes-dashboard

Sie können die Kubernetes-Dashboard für Weitere Informationen zu dem Cluster starten. In den folgenden Abschnitten wird erläutert, wie das Dashboard für Kubernetes in AKS und Kubernetes Kubeadm mithilfe von Bootstrap zu öffnen.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Starten Sie Dashboard, wenn der Cluster in AKS ausgeführt wird

So starten Sie das Kubernetes-Dashboard ausführen:

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Wenn Sie den folgenden Fehler erhalten: *Kann nicht für das Lauschen an Port 8001: Alle Listener Fehler beim Erstellen der folgende Fehler auf: So erstellen Sie Listener kann nicht: Fehler beim Lauschen tcp4 127.0.0.1:8001: > binden: Nur eine Verwendung der einzelnen Socket-Adressen (Protokoll/Netzwerk-Adresse/Port) ist normalerweise zulässig. So erstellen Sie Listener kann nicht: Fehler beim Lauschen tcp6: Adresse [[:: 1]]: 8001: Port in der fehlende > Behandeln von Fehlern: Kann nicht auf die angeforderten Ports überwacht werden: [{8001 9090}]* , stellen Sie sicher, dass Sie nicht gestartet haben das Dashboard bereits von einem anderen Fenster.

Wenn Sie das Dashboard in Ihrem Browser starten, erhalten Sie möglicherweise die Berechtigung Warnungen aufgrund von RBAC in AKS-Clustern standardmäßig aktiviert und das Dienstkonto, das Dashboard ein, die keine ausreichende Berechtigungen zum Zugriff auf alle Ressourcen (z. B.  *Pods ist nicht zulässig: Benutzer "System: Serviceaccount:kube-System: Kubernetes-Dashboard" Pods im Namespace "Default" kann nicht aufgelistet werden*). Führen Sie den folgenden Befehl aus, um die erforderlichen Berechtigungen zum erteilen `kubernetes-dashboard`, und klicken Sie dann das Dashboard neu zu starten:

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Starten Sie Dashboard, bei der Kubernetes-Cluster von Bootstrap wird mithilfe von kubeadm

Detaillierte Anweisungen zum Bereitstellen und konfigurieren das Dashboard in Ihrem Kubernetes-Cluster finden Sie unter [der Kubernetes-Dokumentation](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Um das Kubernetes-Dashboard zu starten, führen Sie diesen Befehl aus:

```bash
kubectl proxy
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [wie SQL Server-big Data-Cluster sind](big-data-cluster-overview.md).
