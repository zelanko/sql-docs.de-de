---
title: Bereitstellen ein SQL Server-Containers in Kubernetes mit Azure Kubernetes-Dienste (AKS) | Microsoft-Dokumentation
description: In diesem Tutorial zeigt, wie Sie eine SQL Server-hochverfügbarkeitslösung mit Kubernetes in Azure Kubernetes Service bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: sql-linux,mvc
ms.technology: linux
ms.openlocfilehash: 44f81a23d341e549243b8e99366fef435be04ffa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47808628"
---
# <a name="deploy-a-sql-server-container-in-kubernetes-with-azure-kubernetes-services-aks"></a>Bereitstellen eines SQL Server-Containers in Kubernetes mit Azure Kubernetes-Dienste (AKS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Erfahren Sie, wie eine SQL Server-Instanz unter Kubernetes in Azure Kubernetes Service (AKS) mit permanenten Speicher für hohe Verfügbarkeit (HA) konfigurieren zu können. Die Lösung bietet resilienz. Wenn SQL Server-Instanz ein Fehler auftritt, erstellt neu Kubernetes automatisch in einem neuen Pod. Kubernetes bietet auch besseren Schutz vor einem Ausfall eines Knotens.

Dieses Tutorial veranschaulicht, wie Sie eine hoch verfügbare SQL Server-Instanz in einem Container in AKS zu konfigurieren. Sie können auch [erstellen Sie eine SQL Server-verfügbarkeitsgruppe auf Kubernetes](tutorial-sql-server-ag-kubernetes.md). Um die zwei verschiedenen Kubernetes-Lösungen vergleichen zu können, finden Sie unter [hochverfügbarkeit für SQL Server-Containern](sql-server-linux-container-ha-overview.md).

> [!div class="checklist"]
> * Erstellen Sie ein SA-Kennwort
> * Erstellen von Speicher
> * Erstellen der Bereitstellung
> * Herstellen einer Verbindung mit SQL Server Management Studio (SSMS)
> * Überprüfen Sie, ob Fehler und Wiederherstellung

## <a name="ha-solution-on-kubernetes-running-in-azure-kubernetes-service"></a>HA-Lösung unter Kubernetes in Azure Kubernetes Service ausgeführt wird

Kubernetes 1.6 und höher bietet Unterstützung für [Speicherklassen](http://kubernetes.io/docs/concepts/storage/storage-classes/), [persistentes Volume Ansprüche](http://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims), und die [Volumetyp für Azure-Datenträger](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). Sie können erstellen und verwalten Ihre SQL Server-Instanzen nativ in Kubernetes. In diesem Artikel gezeigt, wie zum Erstellen einer [Bereitstellung](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) , ähnlich einer freigegebenen Datenträger für die Failoverclusterinstanz Konfiguration mit hoher Verfügbarkeit zu erreichen. In dieser Konfiguration eingepackt Kubernetes clusterorchestrator. Wenn eine SQL Server-Instanz in einem Container ein Fehler auftritt, startet der Orchestrator eine andere Instanz des Containers, der an den gleichen persistenten Speicher angefügt wird.

![Diagramm der SQL Server von Kubernetes-cluster](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Im obigen Diagramm `mssql-server` ist ein Container in einem [Pod](http://kubernetes.io/docs/concepts/workloads/pods/pod/). Kubernetes orchestriert die Ressourcen im Cluster. Ein [Replikatgruppe](http://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) wird sichergestellt, dass der Pod automatisch nach einem Knotenausfall wiederhergestellt wird. Anwendungen eine Verbindung mit dem Dienst herstellen. In diesem Fall stellt der Dienst einen Load Balancer, der eine IP-Adresse hostet, die gleich nach einem Ausfall der bleibt die `mssql-server`.

Im folgenden Diagramm stellen die `mssql-server` Container ein Fehler aufgetreten. Als Orchestrator garantiert Kubernetes die richtige Anzahl von fehlerfreien Instanzen im Replikat festgelegt, und startet einen neuen Container entsprechend der Konfiguration. Der Orchestrator startet einen neuen Pod auf denselben Knoten und `mssql-server` Verbindung mit dem gleichen permanenten Speicher. Der Dienst eine Verbindung herstellt, auf das neu erstellte `mssql-server`.

![Diagramm der SQL Server von Kubernetes-cluster](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

Im folgenden Diagramm das hosting der Knoten die `mssql-server` Container ein Fehler aufgetreten. Der Orchestrator startet den neuen Pod auf einem anderen Knoten, und `mssql-server` Verbindung mit dem gleichen permanenten Speicher. Der Dienst eine Verbindung herstellt, auf das neu erstellte `mssql-server`.

![Diagramm der SQL Server von Kubernetes-cluster](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

## <a name="prerequisites"></a>Erforderliche Komponenten

* **Kubernetes-cluster**
   - Dieses Lernprogramm setzt voraus, einen Kubernetes-Cluster. Verwenden Sie die Schritte ["kubectl"](https://kubernetes.io/docs/user-guide/kubectl/) zum Verwalten des Clusters. 

   - Finden Sie unter [Bereitstellen eines Azure Container Service (AKS)-Clusters](http://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster) zu erstellen und Verbinden mit einem Einzelknoten-Kubernetes-Cluster in AKS mit `kubectl`. 

   >[!NOTE]
   >Zum Schutz gegen den Ausfall eines Knotens erfordert ein Kubernetes-Cluster mehr als einem Knoten.

* **Azure-Befehlszeilenschnittstelle 2.0.23**
   - Die Anweisungen in diesem Tutorial wurden für Azure-Befehlszeilenschnittstelle 2.0.23 überprüft.

## <a name="create-an-sa-password"></a>Erstellen Sie ein SA-Kennwort

Erstellen Sie ein SA-Kennwort im Kubernetes-Cluster. Verwalten von Kubernetes können vertrauliche Informationen, wie Kennwörter als [Geheimnisse](http://kubernetes.io/docs/concepts/configuration/secret/).

Der folgende Befehl erstellt ein Kennwort für das SA-Konto:

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   Ersetzen Sie dies `MyC0m9l&xP@ssw0rd` mit einem komplexen Kennwort.

   Um ein Geheimnis in Kubernetes mit dem Namen `mssql` , die den Wert enthält `MyC0m9l&xP@ssw0rd` für die `SA_PASSWORD`, führen Sie den Befehl.


## <a name="create-storage"></a>Erstellen von Speicher

Konfigurieren einer [persistentes Volume](http://kubernetes.io/docs/concepts/storage/persistent-volumes/) und [permanenter volumeanspruch](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection) im Kubernetes-Cluster. Führen Sie die folgenden Schritte aus: 

1. Erstellen Sie ein Manifest Definition die Speicherklasse und des persistenten Volumes Anspruch.  Das Manifest gibt an, die Storage-Bereitstellung, Parameter und [freigeben Richtlinie](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming). Kubernetes-Cluster verwendet dieses Manifest, um dem permanenten Speicher zu erstellen. 

   Der folgende Yaml-Beispiel definiert eine Speicherklasse und permanenter volumeanspruch. Die Storage-Klasse Provisioner `azure-disk`, da dieser Kubernetes-Cluster in Azure bereitgestellt wird. Der speicherkontotyp wird `Standard_LRS`. Den Namen der permanenter volumeanspruch `mssql-data`. Persistentes Volume Anspruch Metadaten enthält eine Anmerkung verbinden, die es wieder zurück in die Storage-Klasse. 

   ```yaml
   kind: StorageClass
   apiVersion: storage.k8s.io/v1beta1
   metadata:
        name: azure-disk
   provisioner: kubernetes.io/azure-disk
   parameters:
     storageaccounttype: Standard_LRS
     kind: Managed
   ---
   kind: PersistentVolumeClaim
   apiVersion: v1
   metadata:
     name: mssql-data
     annotations:
       volume.beta.kubernetes.io/storage-class: azure-disk
   spec:
     accessModes:
     - ReadWriteOnce
     resources:
       requests:
         storage: 8Gi
   ```

   Speichern Sie die Datei (z. B. **pvc.yaml**).

1. Erstellen Sie die permanenter volumeanspruch in Kubernetes.

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   `<Path to pvc.yaml file>` ist der Speicherort, in dem Sie die Datei gespeichert.

   Des persistenten Volumes wird automatisch als Azure Storage-Konto erstellt und an die permanenter volumeanspruch gebunden. 

    ![Screenshot des Anspruchs-Befehls persistentes volume](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. Vergewissern Sie sich die permanenter volumeanspruch.

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   `<PersistentVolumeClaim>` ist der Name des Anspruchs persistentes Volume.

   In den vorherigen Schritt, heißt die permanenter volumeanspruch `mssql-data`. Um die Metadaten über die permanenter volumeanspruch anzuzeigen, führen Sie den folgenden Befehl aus:

   ```azurecli
   kubectl describe pvc mssql-data
   ```

   Die zurückgegebene Metadaten enthält einen Wert mit dem `Volume`. Dieser Wert entspricht dem Namen des BLOBs.

   ![Screenshot der zurückgegebenen Metadaten, wie z.B. die Menge](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

   Teil des Namens des BLOBs in der folgenden Abbildung aus dem Azure-Portal mit dem Wert für Volume übereinstimmt: 

   ![Screenshot des Azure-Portal-Blob-name](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. Vergewissern Sie sich das persistente Volume.

   ```azurecli
   kubectl describe pv
   ```

   `kubectl` Gibt Metadaten für das persistente Volume, das automatisch erstellt und an die permanenter volumeanspruch gebunden wurde. 

## <a name="create-the-deployment"></a>Erstellen der Bereitstellung

In diesem Beispiel wird der Container, der SQL Server-Instanz als ein Objekt der Kubernetes-Bereitstellung beschrieben. Die Bereitstellung erstellt eine Replikatgruppe. Die Replikatgruppe erstellt den Pod. 

In diesem Schritt erstellen Sie ein Manifest, um den Container basierend auf dem SQL Server beschreiben [Mssql-Server-Linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) Docker-Image. Das manifest verweisen die `mssql-server` permanenter volumeanspruch, und die `mssql` Geheimnis, das Sie bereits auf den Kubernetes-Cluster angewendet. Das Manifest beschreibt auch eine [Service](http://kubernetes.io/docs/concepts/services-networking/service/). Dieser Dienst ist ein Lastenausgleich. Der Load Balancer wird sichergestellt, dass die IP-Adresse erhalten bleibt, nachdem SQL Server-Instanz wiederhergestellt wird. 

1. Erstellen Sie ein Manifest (eine YAML-Datei), um die Bereitstellung zu beschreiben. Im folgende Beispiel wird eine Bereitstellung, einschließlich eines Containers, der basierend auf dem SQL Server-Container-Image beschrieben.

   ```yaml
   apiVersion: apps/v1beta1
   kind: Deployment
   metadata:
     name: mssql-deployment
   spec:
     replicas: 1
     template:
       metadata:
         labels:
           app: mssql
       spec:
         terminationGracePeriodSeconds: 10
         containers:
         - name: mssql
           image: mcr.microsoft.com/mssql/server/mssql-server-linux
           ports:
           - containerPort: 1433
           env:
           - name: ACCEPT_EULA
             value: "Y"
           - name: SA_PASSWORD
             valueFrom:
               secretKeyRef:
                 name: mssql
                 key: SA_PASSWORD 
           volumeMounts:
           - name: mssqldb
             mountPath: /var/opt/mssql
         volumes:
         - name: mssqldb
           persistentVolumeClaim:
             claimName: mssql-data
   ---
   apiVersion: v1
   kind: Service
   metadata:
     name: mssql-deployment
   spec:
     selector:
       app: mssql
     ports:
       - protocol: TCP
         port: 1433
         targetPort: 1433
     type: LoadBalancer
   ```

   Kopieren Sie den vorherigen Code in eine neue Datei mit dem Namen `sqldeployment.yaml`. Aktualisieren Sie die folgenden Werte ein: 

   * `value: "Developer"`: Legt fest, den Container zum Ausführen von SQL Server Developer Edition. Developer-Edition ist nicht für die Produktion lizenziert. Wenn die Bereitstellung für die Produktion ist, legen Sie die passende Edition (`Enterprise`, `Standard`, oder `Express`). 

      >[!NOTE]
      >Weitere Informationen finden Sie unter [wie SQL Server-Lizenz](http://www.microsoft.com/sql-server/sql-server-2017-pricing).

   * `persistentVolumeClaim`: Dieser Wert ist erforderlich, einen Eintrag für `claimName:` , der den Namen für die permanenter volumeanspruch zugeordnet. Dieses Tutorial verwendet `mssql-data`. 

   * `name: SA_PASSWORD`: Das containerimage entsprechend das SA-Kennwort konfiguriert, wie in diesem Abschnitt definiert.

     ```yaml
     valueFrom:
       secretKeyRef:
         name: mssql
         key: SA_PASSWORD 
     ```

     Wenn den Container in Kubernetes bereitgestellt wird, verweist er auf den geheimen Schlüssel mit dem Namen `mssql` um den Wert für das Kennwort abzurufen. 

   >[!NOTE]
   >Mithilfe der `LoadBalancer` Diensttyp, der SQL Server-Instanz ist Remote (über das Internet) an Port 1433.

   Speichern Sie die Datei (z. B. **sqldeployment.yaml**).

1. Die Bereitstellung zu erstellen.

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   `<Path to sqldeployment.yaml file>` ist der Speicherort, in dem Sie die Datei gespeichert.

   ![Screenshot der Bereitstellungsbefehl](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   Die Bereitstellung und dem Dienst werden erstellt. SQL Server-Instanz werden in einem Container, in den permanenten Speicher verbunden ist.

   Geben Sie zum Anzeigen des Status des Pods `kubectl get pod`.

   ![Screenshot des Get-Pod-Befehls](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   Weist den Status in der vorherigen Abbildung der Pod `Running`. Dieser Status gibt an, dass der Container bereit ist. Dies kann einige Minuten dauern.

   >[!NOTE]
   >Nachdem die Bereitstellung erstellt wurde, dauert es einige Minuten, bevor Sie der Pod angezeigt wird. Die Verzögerung ist, da Sie der Cluster Ruft die [Mssql-Server-Linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) -Image aus Docker Hub. Nach dem das Bild beim ersten abgerufen werden wird, möglicherweise nachfolgender Bereitstellungen schneller, wenn die Bereitstellung auf einen Knoten, die bereits für das Image darauf zwischengespeichert. 

1. Stellen Sie sicher, dass die Dienste ausgeführt werden. Führen Sie den folgenden Befehl aus:

   ```azurecli
   kubectl get services 
   ```

   Dieser Befehl gibt die Dienste, die ausgeführt werden, sowie die internen und externen IP-Adressen für die Dienste zurück. Beachten Sie die externe IP-Adresse für den `mssql-deployment` Service. Verwenden Sie diese IP-Adresse für die Verbindung mit SQL Server. 

   ![Screenshot des Get-Service-Befehls](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Weitere Informationen über den Status der Objekte im Kubernetes-Cluster ausgeführt wird:

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>Verbinden Sie mit SQL Server-Instanz

Wenn Sie den Container wie beschrieben konfiguriert haben, können Sie mit einer Anwendung von außerhalb von virtuellen Azure-Netzwerk verbinden. Verwenden der `sa` -Konto und die externe IP-Adresse für den Dienst. Verwenden Sie das Kennwort, das Sie als das Kubernetes-Geheimnis konfiguriert haben. 

Sie können die folgenden Anwendungen verwenden, für die Verbindung mit der SQL Server-Instanz. 

* [SSMS](http://docs.microsoft.com/sql/linux/sql-server-linux-manage-ssms)

* [SSDT](http://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssdt)

* sqlcmd
   
   Verbindung mit `sqlcmd`, führen Sie den folgenden Befehl:

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   Ersetzen Sie die folgenden Werte ein:
      
    - `<External IP Address>` mit der IP-Adresse für den `mssql-deployment` Service 
    - `MyC0m9l&xP@ssw0rd` mit Ihrem Kennwort

## <a name="verify-failure-and-recovery"></a>Überprüfen Sie, ob Fehler und Wiederherstellung

Um Fehler und die Wiederherstellung zu überprüfen, können Sie den Pod löschen. Führen Sie die folgenden Schritte aus:

1. Listen Sie den Pod, der SQL Server ausgeführt wird.

   ```azurecli
   kubectl get pods
   ```

   Notieren Sie den Namen des Pods SQL Server ausgeführt wird.

1. Löschen Sie den Pod.

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0` der Wert wird aus dem vorherigen Schritt für den podnamen zurückgegeben werden. 

Kubernetes wird neu erstellt automatisch den Pod zum Wiederherstellen einer SQL Server-Instanz, und Verbinden mit dem permanenten Speicher. Verwendung `kubectl get pods` , stellen Sie sicher, dass ein neuer Pod bereitgestellt wird. Verwendung `kubectl get services` um sicherzustellen, dass die IP-Adresse für den neuen Container identisch ist. 

## <a name="summary"></a>Zusammenfassung

In diesem Tutorial haben Sie gelernt, wie SQL Server-Container in einem Kubernetes-Cluster für hohe Verfügbarkeit bereitstellen. 

> [!div class="checklist"]
> * Erstellen Sie ein SA-Kennwort
> * Erstellen von Speicher
> * Erstellen der Bereitstellung
> * Herstellen einer Verbindung mit SQL Server Management Studio (SSMS)
> * Überprüfen Sie, ob Fehler und Wiederherstellung

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
>[Einführung in Kubernetes](http://docs.microsoft.com/azure/aks/intro-kubernetes)


