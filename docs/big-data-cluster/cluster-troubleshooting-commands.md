---
title: Verwenden Sie "kubectl" für die Überwachung/Problembehandlung
titleSuffix: SQL Server 2019 big data clusters
description: In diesem Artikel bieten nützliche Kubectl-Befehle für die Überwachung und Problembehandlung für eine SQL Server-2019 big Data-Cluster (Vorschau).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 624c4ad4f53c0ad78cf5b972c976aadc57fd35d3
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017906"
---
# <a name="kubectl-commands-for-monitoring-and-troubleshooting-sql-server-big-data-clusters"></a>"Kubectl"-Befehle zur Überwachung und Problembehandlung von SQL Server-big Data-Cluster

Dieser Artikel beschreibt verschiedene nützliche Kubernetes-Befehle, die Sie verwenden können, um die Überwachung und Problembehandlung für eine SQL Server-2019 big Data-Cluster (Vorschau). Dieser Artikel behandelt allgemeine Aufgaben, wie das Kopieren von Dateien zu oder von einem Container mit einem der SQL Server-Dienste für die big Data-Cluster. Es wird gezeigt, wie zeigen Sie ausführliche Details einen Pod oder andere Kubernetes-Artefakte, die in der big Data-Cluster befinden.

## <a name="kubectl-command-examples"></a>Beispiele für die Kubectl-Befehl

Führen Sie den folgenden **"kubectl"** Befehle auf einem Windows ("Cmd" oder "PS") oder Linux (Bash)-Client-Computer. Sie benötigen die vorherigen Authentifizierung im Cluster und zur Ausführung in einem Clusterkontext. Z. B. für einen zuvor erstellten AKS-Cluster können ausführen `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` zum Herunterladen der Konfigurationsdatei des Kubernetes-Cluster und Festlegen des clusterkontexts.

## <a name="get-status-of-pods"></a>Abrufen des Status des pods

Sie können die `kubectl get pods` Befehl aus, um den Status des Pods im Cluster für alle Namespaces oder big Data-Cluster-Namespaces abzurufen. In den folgenden Abschnitten sind Beispiele für beide.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Anzeigen von Status alle Pods im Kubernetes-cluster

Führen Sie dem folgenden Befehl aus, um alle Pods und deren Status, einschließlich der Pods, die Teil des Namespace zu erhalten, dass SQL Server-Pods für big Data-Cluster erstellt werden:

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Status alle Pods in der SQL Server-big Data-Cluster anzeigen

Verwenden der `-n` Parameter, um einen bestimmten Namespace anzugeben. Beachten Sie, dass es sich bei den Namen des Clusters im angegebenen SQL Server-Pods für big Data-Cluster, in einem neuen Namespace, die zum Zeitpunkt der bootstrap erstellt erstellt werden anhand der `mssqlctl cluster create --name <cluster_name>` Befehl.

```bash
kubectl get pods -n <namespace_name>
```

Der folgende Befehl zeigt z. B. den Status des Pods in einem big Data-Cluster mit dem Namen `big_data_cluster`:

```bash
kubectl get pods -n big_data_cluster
```

## <a name="get-pod-details"></a>Abrufen von Pod-details

Führen Sie den folgenden Befehl aus, um eine ausführliche Beschreibung der einen bestimmten Pod in der Ausgabe im JSON-Format zu erhalten. Sie enthält Details wie der aktuelle Kubernetes-Knoten, dem der Pod, den in den Pod und das Bild ab, das Bootstrapping für den Container ausgeführten Containern gespeichert wird. Außerdem zeigt weitere Details wie Status, Bezeichnungen und persistenten Volumes-Ansprüche, die den Pod zugeordnet sind.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

Das folgende Beispiel zeigt die Details für die `mssql-data-pool-master-0` Pods in einem big Data-Cluster mit dem Namen `big_data_cluster`:

```bash
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="get-status-of-services"></a>Abrufen des Status von Diensten

Führen Sie den folgenden Befehl zum Abrufen von Details für die big Data-Clusterdienste. Zu diesen Details zählen, deren Typ aus, und die IP-Adressen, die mit der jeweiligen Dienste und Ports verknüpft ist. Beachten Sie, dass SQL Server-big Data-Cluster-Dienste, in einem neuen Namespace, die zum Zeitpunkt bootstrap basierend auf den Namen des Clusters im angegebenen erstellt erstellt werden die `mssqlctl cluster create --name <cluster_name>` Befehl.

```bash
kubectl get svc -n <namespace_name>
```

Das folgende Beispiel zeigt den Status für Dienste in einer big Data-Cluster mit dem Namen `big_data_cluster`:

```bash
kubectl get svc -n big_data_cluster
```

## <a name="get-service-details"></a>Abrufen von Dienstdetails

Führen Sie diesen Befehl aus, um eine ausführliche Beschreibung eines Diensts in der Ausgabe im JSON-Format zu erhalten. Es enthält Details wie z. B. "Bezeichnungen", Selektor externe IP-(wenn der Dienst des Typs der LoadBalancer ist) IP-Adresse, port usw.
```
kubectl describe pod  <pod_name> -n <namespace_name>
```

Beispiel:
```
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="run-commands-in-a-container"></a>Führen Sie Befehle in einem container

Wenn die vorhandenen Tools oder die Infrastruktur nicht auf eine bestimmte Aufgabe durchzuführen, ohne tatsächlich im Kontext des Containers werden können, Sie können melden Sie sich im Container mit `kubectl exec` Befehl. Beispielsweise müssen Sie überprüfen, ob eine bestimmte Datei vorhanden ist oder Sie Dienste im Container neu zu starten möchten. 

Verwenden der `kubectl exec` Befehl können Sie die folgende Syntax:

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

Die folgenden beiden Abschnitte bieten zwei Beispiele für die Ausführung eines Befehls in einem bestimmten Container.

### <a id="restartsql"></a> Melden Sie sich bei einem bestimmten Container, und starten Sie SQL Server-Prozess

Das folgende Beispiel zeigt die Vorgehensweise beim Neustart von SQL Server-Prozess in der `mssql-server` -Container in der `mssql-master-pool-0` Pod:

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> Melden Sie sich bei einem bestimmten Container, und starten Sie Dienste in einem Container neu.
 
Das folgende Beispiel zeigt die Vorgehensweise beim Neustart aller Dienste, die von verwalteten **Supervisord**: 

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
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
kubectl cp mssql-master-pool-0:/var/opt/mssql/log -c mssql-server -n big_data_cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> Kopieren von Dateien in container

Das folgende Beispiel kopiert die **AdventureWorks2016CTP3.bak** -Datei aus dem lokalen Computer auf den SQL Server-Masterinstanz Container (`mssql-server`) in der `mssql-master-pool-0` Pod. Die Datei wird kopiert, um die `/tmp` Verzeichnis im Container. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n big_data_cluster
```

## <a id="forcedelete"></a> Force Delete ein pod
 
Es empfiehlt sich nicht um einen Pod-Force-löschen. Zum Testen von Verfügbarkeit, resilienz und Dauerhaftigkeit von Daten, Sie können jedoch löschen einen Pod zum Simulieren eines Fehlers im Pod der `kubectl delete pods` Befehl.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

Das folgende Beispiel löscht den Speicher-Pool-Pod `mssql-storage-pool-default-0`:

```bash
kubectl delete pods mssql-storage-pool-default-0 -n big_data_cluster --grace-period=0 --force
```

## <a id="getip"></a> Abrufen von Pod-IP
 
Für die Problembehandlung müssen Sie die IP-Adresse des Knotens abzurufen, die ein Pod zurzeit ausgeführt wird. Rufen Sie die IP-Adresse mit der `kubectl get pods` Befehl mit folgender Syntax:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

Im folgenden Beispiel wird der IP-Adresse des Knotens an, die die `mssql-master-pool-0` Pod ausgeführt wird:

```bash
kubectl get pods mssql-master-pool-0 -o yaml -n big_data_cluster | grep hostIP
```

## <a name="start-the-kubernetes-dashboard"></a>Starten Sie das Kubernetes-dashboard

Sie können die Kubernetes-Dashboard für Weitere Informationen zu dem Cluster starten. In den folgenden Abschnitten wird erläutert, wie das Dashboard für Kubernetes in AKS und Kubernetes Kubeadm mithilfe von Bootstrap zu öffnen.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Starten Sie Dashboard, wenn der Cluster in AKS ausgeführt wird

So starten Sie das Kubernetes-Dashboard ausführen:
 
```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Wenn Sie den folgenden Fehler erhalten: *Kann nicht für das Lauschen an Port 8001: Alle Listener Fehler beim Erstellen der folgende Fehler auf: So erstellen Sie Listener kann nicht: Fehler beim Lauschen tcp4 127.0.0.1:8001: > binden: Nur eine Verwendung der einzelnen Socket-Adressen (Protokoll/Netzwerk-Adresse/Port) ist normalerweise zulässig. So erstellen Sie Listener kann nicht: Fehler beim Lauschen tcp6: Adresse [[:: 1]]: 8001: Port in der fehlende > Behandeln von Fehlern: Kann nicht auf die angeforderten Ports überwacht werden: [{8001 9090}]*, stellen Sie sicher, dass Sie nicht gestartet haben das Dashboard bereits von einem anderen Fenster.

Wenn Sie das Dashboard in Ihrem Browser starten, erhalten Sie möglicherweise die Berechtigung Warnungen aufgrund von RBAC in AKS-Clustern standardmäßig aktiviert und das Dienstkonto, das Dashboard ein, die keine ausreichende Berechtigungen zum Zugriff auf alle Ressourcen (z. B.  *Pods ist nicht zulässig: Benutzer "System: Serviceaccount:kube-System: Kubernetes-Dashboard" Pods im Namespace "Default" kann nicht aufgelistet werden*). Führen Sie den folgenden Befehl aus, um die erforderlichen Berechtigungen zum erteilen `kubernetes-dashboard`, und klicken Sie dann das Dashboard neu zu starten:

```
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Starten Sie Dashboard, bei der Kubernetes-Cluster von Bootstrap wird mithilfe von kubeadm

Detaillierte Anweisungen zum Bereitstellen und konfigurieren das Dashboard in Ihrem Kubernetes-Cluster finden Sie unter [der Kubernetes-Dokumentation](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Um das Kubernetes-Dashboard zu starten, führen Sie diesen Befehl aus:

```
kubectl proxy
```

## <a name="next-steps"></a>Nächste Schritte

Überwachung und Problembehandlung, SQL Server für big Data-Cluster, finden Sie unter den [Cluster Verwaltungsportal](cluster-admin-portal.md).