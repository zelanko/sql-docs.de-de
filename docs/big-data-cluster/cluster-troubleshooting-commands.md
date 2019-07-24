---
title: Überwachung und Problembehandlung
titleSuffix: SQL Server big data clusters
description: Dieser Artikel bietet hilfreiche Befehle zum Überwachen und behandeln von Problemen mit einem SQL Server 2019 Big Data-Cluster (Vorschau).
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 272249b7bd6c22895b7d10e7fbce4a20cb647a49
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419478"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>Überwachung und Problembehandlung für SQL Server Big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel werden verschiedene nützliche Kubernetes-Befehle beschrieben, mit denen Sie einen SQL Server 2019 Big Data-Cluster (Vorschauversion) überwachen und Probleme beheben können. Es wird gezeigt, wie ausführliche Details zu einem Pod oder anderen Kubernetes-Artefakten angezeigt werden, die sich im Big Data Cluster befinden. In diesem Artikel werden auch allgemeine Aufgaben behandelt, wie z. b. das Kopieren von Dateien in einen oder aus einem Container, der einen der SQL Server Big Data Cluster Dienste ausführen.

> [!TIP]
> Führen Sie die folgenden **kubectl** -Befehle auf einem Windows-Client Computer (cmd oder PS) oder einem Linux-Client Computer (bash) aus. Sie erfordern eine vorherige Authentifizierung im Cluster und einen Cluster Kontext, der für ausgeführt werden soll. Beispielsweise können Sie für einen zuvor erstellten AKS-Cluster ausführen `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>` , um die Kubernetes-Cluster Konfigurationsdatei herunterzuladen und den Cluster Kontext festzulegen.

## <a name="get-status-of-pods"></a>Status von PODs erhalten

Sie können den `kubectl get pods` -Befehl verwenden, um den Status von Pods im Cluster entweder für alle Namespaces oder den Big Data Cluster-Namespace zu erhalten. In den folgenden Abschnitten werden Beispiele für beides veranschaulicht.

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Anzeigen des Status aller Pods im Kubernetes-Cluster

Führen Sie den folgenden Befehl aus, um alle Pods und deren Status zu erhalten, einschließlich der Pods, die Teil des Namespace sind, in dem SQL Server Big Data Cluster-Pods erstellt werden:

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>Anzeigen des Status aller Pods im SQL Server Big Data-Cluster

Verwenden Sie `-n` den-Parameter, um einen bestimmten Namespace anzugeben. Beachten Sie, dass SQL Server Big Data Cluster-Pods in einem neuen Namespace erstellt werden, der auf der Grundlage des in der Bereitstellungs Konfigurationsdatei angegebenen Cluster namens auf der Grundlage des Cluster namens erstellt wurde. Der Standardname `mssql-cluster`wird hier verwendet.

```bash
kubectl get pods -n mssql-cluster
```

Es sollte eine Ausgabe angezeigt werden, die der folgenden Liste für einen ausgelaufenden Big Data Cluster ähnelt:

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
> Während der Bereitstellung werden Pods mit dem **Status** **containercreating** weiterhin angezeigt. Wenn die Bereitstellung aus irgendeinem Grund nicht mehr vorhanden ist, erhalten Sie eine Vorstellung von der Ursache des Problems. Sehen Sie sich auch die Spalte **bereit** an. Dies gibt Aufschluss darüber, wie viele Container im Pod gestartet wurden. Beachten Sie, dass die bereit Stellungen je nach Konfiguration und Netzwerk 30 Minuten oder länger dauern können. Ein Großteil dieser Zeit wird für das Herunterladen der Container Images für verschiedene Komponenten aufgewendet.

## <a name="get-pod-details"></a>Pod-Details erhalten

Führen Sie den folgenden Befehl aus, um eine ausführliche Beschreibung eines bestimmten Pod in der Ausgabe des JSON-Formats zu erhalten. Sie enthält Details, z. b. den aktuellen Kubernetes-Knoten, auf dem sich der Pod befindet, die Container, die im Pod ausgeführt werden, und das Bild, das zum Bootstrap der Container verwendet wird. Außerdem werden weitere Details angezeigt, wie z. b. Bezeichnungen, Status und persistente volumeansprüche, die dem Pod zugeordnet sind.

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

Das folgende Beispiel zeigt die Details für den `master-0` Pod in einem Big Data Cluster mit `mssql-cluster`dem Namen:

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

Wenn Fehler aufgetreten sind, kann der Fehler in den letzten Ereignissen für den Pod manchmal angezeigt werden.

## <a name="get-pod-logs"></a>Pod-Protokolle erhalten

Sie können die Protokolle für Container abrufen, die in einem Pod ausgeführt werden. Der folgende Befehl ruft die Protokolle für alle Container ab, die im Pod mit `master-0` dem Namen ausgeführt werden, und gibt `master-0-pod-logs.txt`Sie an einen Dateinamen aus:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a>Status der Dienste erhalten

Führen Sie den folgenden Befehl aus, um Details für die Big Data Cluster Dienste anzuzeigen. Diese Details umfassen den Typ und die IP-Adressen, die den jeweiligen Diensten und Ports zugeordnet sind. Beachten Sie, dass SQL Server Big Data-Cluster Dienste in einem neuen Namespace erstellt werden, der auf der Grundlage des in der Bereitstellungs Konfigurationsdatei angegebenen Cluster namens in einem neuen Namespace erstellt wurde.

```bash
kubectl get svc -n <namespace_name>
```

Im folgenden Beispiel wird der Status für Dienste in einem Big Data Cluster mit `mssql-cluster`dem Namen angezeigt:

```bash
kubectl get svc -n mssql-cluster
```

Die folgenden Dienste unterstützen externe Verbindungen mit dem Big Data-Cluster:

| Dienst | Beschreibung |
|---|---|
| **master-svc-external** | Bietet Zugriff auf die Master Instanz.<br/>(**Extern-IP, 31433** und **sa** -Benutzer) |
| **controller-svc-external** | Unterstützt Tools und Clients, von denen der Cluster verwaltet wird. |
| **gateway-svc-external** | Bietet Zugriff auf das HDFS/Spark-Gateway.<br/>(**Extern-IP** und der **root** -Benutzer) |
| **appproxy-svc-external** | Unterstützung von Anwendungs Bereitstellungs Szenarien. |

> [!TIP]
> Dies ist eine Möglichkeit, die Dienste mit **kubectl**anzuzeigen, aber es ist auch möglich `azdata bdc endpoint list` , diese Endpunkte mit dem Befehl anzuzeigen. Weitere Informationen finden Sie unter [Get Big Data Cluster Endpunkte](deployment-guidance.md#endpoints).

## <a name="get-service-details"></a>Dienst Details anzeigen

Führen Sie diesen Befehl aus, um eine ausführliche Beschreibung eines Dienstanbieter in der JSON-Format Ausgabe zu erhalten. Sie enthält Details wie z. b. Bezeichnungen, Selektor, IP, externe IP-Adresse (wenn der Dienst vom Typ "LoadBalancer" ist), "Port" usw.

```bash
kubectl describe service <service_name> -n <namespace_name>
```

Im folgenden Beispiel werden Details für den Dienst " **Master-SVC-extern** " abgerufen:

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>Ausführen von Befehlen in einem Container

Wenn Sie durch vorhandene Tools oder die Infrastruktur keine bestimmte Aufgabe ausführen können, ohne sich tatsächlich im Kontext des Containers befinden zu müssen, können Sie sich mit `kubectl exec` dem Befehl beim Container anmelden. Beispielsweise müssen Sie möglicherweise überprüfen, ob eine bestimmte Datei vorhanden ist, oder Sie müssen die Dienste im Container neu starten. 

Verwenden Sie die `kubectl exec` folgende Syntax, um den Befehl zu verwenden:

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

In den folgenden beiden Abschnitten werden zwei Beispiele für das Ausführen eines Befehls in einem bestimmten Container bereitgestellt.

### <a id="restartsql"></a>Anmelden bei einem bestimmten Container und Neustarten SQL Server Prozesses

Im folgenden Beispiel wird gezeigt, wie Sie den SQL Server Prozess im `mssql-server` Container `master-0` im Pod neu starten:

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a>Anmelden bei einem bestimmten Container und Neustarten von Diensten in einem Container
 
Im folgenden Beispiel wird gezeigt, wie alle durch die **supervisord**verwalteten Dienste neu gestartet werden: 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a>Dateien kopieren

Wenn Sie Dateien aus dem Container auf den lokalen Computer kopieren müssen, verwenden `kubectl cp` Sie den Befehl mit der folgenden Syntax:

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

Auf ähnliche Weise können Sie `kubectl cp` verwenden, um Dateien vom lokalen Computer in einen bestimmten Container zu kopieren.

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a>Kopieren von Dateien aus einem Container

Im folgenden Beispiel werden die SQL Server Protokolldateien aus dem Container in den `~/temp/sqlserverlogs` Pfad auf dem lokalen Computer kopiert (in diesem Beispiel ist der lokale Computer ein Linux-Client):

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a>Dateien in Container kopieren

Im folgenden Beispiel wird die Datei **AdventureWorks2016CTP3. bak** vom lokalen Computer in den SQL Server Master-instanzcontainer`mssql-server`() im `master-0` Pod kopiert. Die Datei wird in das `/tmp` Verzeichnis im Container kopiert. 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a>Löschen eines Pod erzwingen
 
Es wird nicht empfohlen, ein Pod zu erzwingen. Zum Testen von Verfügbarkeit, Resilienz oder Daten Persistenz können Sie jedoch einen Pod löschen, um einen Pod-Fehler `kubectl delete pods` mit dem Befehl zu simulieren.

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

Im folgenden Beispiel wird `storage-0-0`der Speicherpool Pod gelöscht:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a>Pod-IP-Adresse
 
Zur Problembehandlung müssen Sie möglicherweise die IP-Adresse des Knotens erhalten, auf dem ein Pod derzeit ausgeführt wird. Um die IP-Adresse zu erhalten, `kubectl get pods` verwenden Sie den Befehl mit der folgenden Syntax:

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

Im folgenden Beispiel wird die IP-Adresse des Knotens abgerufen `master-0` , auf dem der Pod ausgeführt wird:

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="kubernetes-dashboard"></a>Kubernetes-Dashboard

Sie können das Kubernetes-Dashboard starten, um weitere Informationen zum Cluster zu erhalten. In den folgenden Abschnitten wird erläutert, wie das Dashboard für Kubernetes unter AKS und für Kubernetes Bootstrap mithilfe von kubeadm gestartet wird.
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>Dashboard starten, wenn der Cluster in AKS ausgeführt wird

Zum Starten des Kubernetes-Dashboards führen Sie Folgendes aus:

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> Wenn Sie die folgende Fehlermeldung erhalten: *An Port 8001 kann nicht gelauscht werden: Es konnten nicht alle Listener mit den folgenden Fehlern erstellt werden: Listener kann nicht erstellt werden: Fehler beim lauschen tcp4 127.0.0.1:8001: > bind: Normalerweise ist nur eine Verwendung der einzelnen Socketadressen (Protokoll/Netzwerkadresse/Port) zulässig. Listener kann nicht erstellt werden: Fehler beim lauschen tcp6: Address [[:: 1]]: 8001: fehlender Port in > Adress Fehler: An den angeforderten Ports kann nicht gelauscht werden: [{8001 9090}* ]. Stellen Sie sicher, dass Sie das Dashboard nicht bereits in einem anderen Fenster gestartet haben.

Wenn Sie das Dashboard in Ihrem Browser starten, erhalten Sie möglicherweise Berechtigungs Warnungen, weil RBAC standardmäßig in AKS-Clustern aktiviert ist, und das vom Dashboard verwendete Dienst Konto verfügt nicht über ausreichende Berechtigungen für den Zugriff auf alle Ressourcen  *(z. b. Pods sind unzulässig: Benutzer "System: ServiceAccount: Kube-System: kubernetes-Dashboard" kann keine Pods im Namespace "Default"* auflisten). Führen Sie den folgenden Befehl aus, um die erforderlichen `kubernetes-dashboard`Berechtigungen für zu erhalten, und starten Sie dann das Dashboard neu:

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Dashboard starten, wenn der Kubernetes-Cluster mithilfe von kubeadm Bootstrap ist

Ausführliche Anweisungen zum Bereitstellen und Konfigurieren des Dashboards in Ihrem Kubernetes-Cluster finden Sie in [der Kubernetes-Dokumentation](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/). Führen Sie den folgenden Befehl aus, um das Kubernetes-Dashboard zu starten:

```bash
kubectl proxy
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind SQL Server Big Data Cluster](big-data-cluster-overview.md).
