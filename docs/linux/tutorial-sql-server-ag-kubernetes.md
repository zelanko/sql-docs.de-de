---
title: Konfigurieren Sie eine SQL Server Always On-verfügbarkeitsgruppe auf Docker-Containern in Kubernetes | Microsoft-Dokumentation
description: Dieses Tutorial veranschaulicht, wie eine SQL Server always on-verfügbarkeitsgruppe mit Kubernetes in Azure Container Service bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: tutorial
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux,mvc
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d21866f3f7004dff1ea86ca4f608580a79ab754
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049360"
---
# <a name="configure-a-sql-server-always-on-availability-group-on-docker-containers-in-kubernetes-with-azure-kubernetes-service-aks"></a>Konfigurieren Sie eine SQL Server Always On-verfügbarkeitsgruppe auf Docker-Containern in Kubernetes mit Azure Kubernetes Service (AKS)

Dieses Tutorial veranschaulicht, wie Sie eine hoch verfügbare SQL Server-Instanz in einem Container in AKS zu konfigurieren. Sie können auch [bereitstellen ein SQL Server-Containers in Kubernetes](tutorial-sql-server-containers-kubernetes.md). Um die zwei verschiedenen Kubernetes-Lösungen vergleichen zu können, finden Sie unter [hochverfügbarkeit für SQL Server-Containern](sql-server-linux-container-ha-overview.md).

In diesem Tutorial erfahren Sie, wie Sie:  

> [!div class="checklist"]
> * Erstellen von Speicher
> * Bereitstellen Sie den SQL Server-Operator in einem Kubernetes-cluster 
> * Erstellen des Kubernetes-Geheimnisse
> * Bereitstellen von SQL Server-Instanzen und Health-agents
> * Eine Verbindung mit dem primären Replikat herstellen
> * Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe

Dieses Tutorial veranschaulicht die Architektur in [Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/). Wenn Sie nicht über ein Azure-Abonnement verfügen, erstellen eine [kostenloses Konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) bevor Sie beginnen.

In diesem Diagramm steht für die Lösung, die Sie in diesem Tutorial machen:

![Kubernetes-ag-cluster](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

### <a name="deployment-methodology-for-kubernetes"></a>Bereitstellungsmethode für Kubernetes

Einige der Schritte in diesem Artikel erstellen Sie ein Manifest, und klicken Sie dann das Manifest bereitstellen, für den Cluster. Das Manifest ist eine yaml-Datei mit der Beschreibung des Kubernetes-Objekte, die Sie bereitstellen.

Die yaml-Dateien in diesem Beispiel finden Sie unter [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability).

Die Objekte umfassen, Speicher, Operatoren, Pods, Container und Dienste.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Allgemeine Kenntnisse im Umgang mit diesen Technologien

  * [Kubernetes](http://kubernetes.io) Version 1.8
  * [Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/)
  * [SQLServer unter Docker](quickstart-install-connect-docker.md)
  * [SQL Server Always On-verfügbarkeitsgruppe](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

* Ein Kubernetes-Cluster mit vier Knoten.

  Anweisungen hierzu finden Sie unter [Tutorial: Bereitstellen eines Azure Kubernetes Service (AKS)-Clusters](http://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster).

* Installieren Sie [ `kubectl` ](https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster#install-the-kubectl-cli).

## <a name="configuration-and-deployment-procedures"></a>Konfiguration und Bereitstellung von Prozeduren

Das Lernprogramm zeigt die yaml-Dateien in Ihrem Kubernetes-Cluster anwenden.

## <a name="create-the-secrets"></a>Die geheimen Schlüssel erstellen

Um die Kubernetes-Geheimnisse zum Speichern die Kennwörter für das SQL Server-SA-Konto und den SQL Server-Hauptschlüssel zu erstellen, führen Sie den folgenden Befehl aus.

```azurecli
kubectl create secret generic sql-secrets --from-literal=sapassword="MyC0m9l&xP@ssw0rd" --from-literal=masterkeypassword="MyC0m9l&xP@ssw0rd2"
```

Verwenden Sie in einer produktionsumgebung einen anderen, komplexes Kennwort.

## <a name="deploy-the-operator"></a>Den Operator bereitstellen

Ein Kubernetes-Operator stellt Instanzen von SQL Server bereit und konfiguriert die verfügbarkeitsgruppe im Kubernetes-Cluster. 

Sehen Sie ein Beispiel für Bediener am [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml)

Herunterladen `operator.yaml` aus [Sql-Server-Beispiele](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/)

Bereitstellen Sie den Operator wird als ein Replikat Kubernetes-Bereitstellung.

Den Operator bereitstellen zu können:

Bereitstellen den Operator mit der `kubectl apply` Befehl.

```azurecli
kubectl apply -f operator.yaml
```

## <a name="create-the-sql-server-ag-deployment"></a>Erstellen der Bereitstellung von SQL Server-Verfügbarkeitsgruppe

Im nächste Schritt werden die SQL Server-Instanzen und der verfügbarkeitsgruppe in einem Kubernetes-Bereitstellung erstellt. Nachdem Sie diese Bereitstellung auf den Cluster anwenden, wird der Operator die SQL Server-Instanzen als Docker-Container bereitgestellt. Diese Bereitstellung führt zu drei StatefulSets mit einen Pod. Jeder Pod umfasst zwei Container:

* SQL Server-Instanz basierend auf den `mssql-server` Image
* HA-supervisor

Darüber hinaus beschreibt die Bereitstellung einen Load Balancer-Dienst für den Listener der verfügbarkeitsgruppe

Mssql-Server bereitstellen:

1. Kopie [sqlserver.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) auf Ihrem Computer.
2. Update `sqlserver.yaml` für Ihre Umgebung.


Zum Bereitstellen von SQL Server-Instanzen aus, und die verfügbarkeitsgruppe erstellen, führen Sie den folgenden Befehl aus.

```azurecli
kubectl apply -f sqlserver.yaml
```

## <a name="deploy-ag-services"></a>Bereitstellen von AG-Dienste

Erstellen Sie Load Balancer-Dienste für direkte Aufrufe Replikate in der verfügbarkeitsgruppe im Kubernetes-Cluster.

[AG-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) vier Dienste erstellt.

* AG1 primären eine Verbindung mit dem primären Replikat.
* AG1-Secondary-Synchronisierung eine Verbindung mit einem synchronen sekundären Replikat.
* AG1-Secondary-Async eine Verbindung mit einem asynchronen sekundären Replikats.
* AG1-Secondary-Konfiguration eine Verbindung mit einer reinen konfigurationsreplikat. 

  >[!NOTE]
  >Dieser Load Balancer Dienste dienen als Beispiele. In diesem Tutorial besteht nicht die reine konfigurationsreplikat.


Stellen Sie die Load Balancer-Dienste bereit, damit Sie eine Verbindung mit der verfügbarkeitsgruppe herstellen können.

Führen Sie den folgenden Befehl, um die Dienste bereitzustellen.

```azurecli
kubectl apply -f ag-services.yaml
```

### <a name="monitor-the-deployment"></a>Überwachen der Bereitstellung

Sie können [Kubernetes-Dashboard mit Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard) zum Überwachen der Bereitstellung. 

Verwendung `az aks browse` zum Starten des Dashboards. 

Nach der Bereitstellung kann nur AG Mitgliedschaft Liste und Post-Init-T-SQL-Skript aktualisiert werden. Andere Eigenschaften können nicht aktualisiert werden – die Ressource gelöscht und neu erstellt werden muss. Anmeldeinformationen für die Benutzer automatisch generierter gedreht werden können, mithilfe einer `mssql-server-k8s-rotate-creds` Auftrag.

## <a name="connect-to-the-sql-server-instance-hosting-the-primary-replica"></a>Verbinden Sie mit der SQL Server-Instanz, die das primäre Replikat hostet

Die `ag-services.yaml` wird beschrieben, einen Kubernetes-Dienstnamen `ag1-primary`. `ag1-primary` erstellt einen Azure Load Balancer, die das primäre Replikat hostet SQL Server-Instanz zu verweisen. Verwenden Sie die externe IP-Adresse des Diensts als Zielserver `sa` als Konto und das Kennwort erstellt weiter oben in der `mssql secret` für das Kennwort.

Verwendung `kubectl get services` dieser IP-Adresse abrufen.

Zum Beispiel:

![Beispiel eines Diensts zu erhalten](media\tutorial-sql-server-ag-containers-kubernetes\KubernetesGetServices.png)

In der Abbildung oben `ag1-primary` Dienst verfügt über eine externe IP-Adresse `104.42-50.138`. 

Verwenden Sie zum Verbinden mit SQL Server mit SQL-Authentifizierung die `sa` -Konto, das den Wert für `sapassword` aus den geheimen Schlüssel, die Sie erstellt haben, und diese IP-Adresse.

Zum Beispiel:

```cmd
sqlcmd -S 104.42.50.138 -U sa -P "MyC0m9l&xP@ssw0rd"
```

![Herstellen einer Verbindung mit sqlcmd](./media/tutorial-sql-server-ag-containers-kubernetes/sqlcmdConnect.png)

Sie können auch eine Verbindung herstellen mit [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md).

Um die Verbindung zu überprüfen, führen Sie die folgende Abfrage mit der SQL Server-Instanz, die das primäre Replikat hostet:

```sql
SELECT @@SERVERNAME;
```

Die Abfrage gibt den Namen des SQL Server-Instanz, die das primäre Replikat hostet.

An diesem Punkt verfügt über der Kubernetes-Cluster auf drei Instanzen von SQL Server in der Docker-Container aus. Eine verfügbarkeitsgruppe umfasst alle drei Instanzen von SQL Server, aber es ist keine Datenbank in der verfügbarkeitsgruppe. Der nächste Schritt ist das Hinzufügen eine Datenbank mit der verfügbarkeitsgruppe.

## <a name="add-a-database-to-the-availability-group"></a>Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe

So fügen Sie eine Datenbank mit der verfügbarkeitsgruppe hinzu:

1. Erstellen einer Datenbank

  ```sql
  CREATE DATABASE [DemoDB]
  ```

1. Erstellen Sie eine vollständige Sicherung der Datenbank um die Protokollkette für die Transaktion zu starten.

  ```sql
  BACKUP DATABASE [DemoDB] 
  TO  DISK = N'/var/opt/mssql/data/DemoDB.bak' 
    WITH NOFORMAT, 
    NOINIT,  
    NAME = N'DemoDB-Full Database Backup', 
    SKIP, 
    NOREWIND, 
    NOUNLOAD,  
    STATS = 10;
  GO
  ```

1. Fügen Sie die Datenbank mit der verfügbarkeitsgruppe

  ```sql
  ALTER AVAILABILITY GROUP ag1 ADD DATABASE [DemoDB]; 
  ```

Das Replikat wird automatisch mit dem automatischen seeding-Modus konfiguriert, damit die verfügbarkeitsgruppe die Datenbank auf die sekundären Replikate liefert.

In SQL Server Management Studio können Sie eine Verbindung mit dem primären Replikat herstellen und finden Sie unter der verfügbarkeitsgruppe auf dem Dashboard.

Das folgende Beispiel zeigt die verfügbarkeitsgruppe mit Replikaten auf drei Knoten, die auf dem Dashboard konfiguriert.

![AG1-Dashboard](./media/tutorial-sql-server-ag-containers-kubernetes/ssms_AG1.png)

## <a name="verify-failure-and-recovery"></a>Überprüfen Sie, ob Fehler und Wiederherstellung

Um zu überprüfen, bei der fehlererkennung und das Failover können Sie den Pod, der das primäre Replikat hostet löschen. Kubernetes wird festlegen, ob ein neues primäres Replikat und den Listener umleiten. Anschließend wird es den gelöschten Pod neu erstellen. 

Führen Sie die folgenden Schritte aus, um diesen Prozess zu veranschaulichen:

1. Listen Sie den Pod, der SQL Server ausgeführt wird.

   ```azurecli
   kubectl get pods
   ```

2. Identifizieren Sie den Pod, der das primäre Replikat ausgeführt.

   Entweder eine Verbindung herstellen, mit dem primären Replikat mithilfe der externen IP- und Abfrage `@@servername` oder `kubectl` um den entsprechenden Pod zu erhalten. Dieser Befehl gibt den Namen des Pods zurück, der den Container mit dem primären Replikat der Verfügbarkeitsgruppe enthält:

   ```azurecli
   kubectl get pods --selector="role.ag.mssql.microsoft.com/ag1"="primary" --output=jsonpath={.items..metadata.name}
   ```

3. Löschen Sie den Pod.

   ```azurecli
   kubectl delete pod <podName>
   ```

Ersetzen Sie dies `<podName>` mit dem Wert aus dem vorherigen Schritt für den podnamen zurückgegeben. 

Kubernetes automatisch ein Failover auf eines der sekundären Replikate verfügbar Synchronisierung als auch den gelöschten Pod erstellt.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Löschen Sie die Ressourcengruppe und alle zugehörigen Ressourcen aus, wenn Sie nicht mehr benötigen. Führen Sie den folgenden Befehl aus:
>[!WARNING]
>Dieser Befehl löscht komplett alles, was in der Ressourcengruppe. Keine der Komponenten des Kubernetes-Clusters ist verfügbar, nachdem Sie die Ressourcengruppe löschen.

```azurecli
az group delete --name <MyResourceGroup>
```

Ersetzen Sie zum Ausführen des obigen Befehls `<MyResourceGroup>` mit dem Namen Ihrer Ressourcengruppe. 

Azure löscht die Ressourcengruppe aus.

## <a name="summary"></a>Zusammenfassung

In diesem Tutorial haben Sie gelernt, wie Sie:  

> [!div class="checklist"]
> * Erstellen von Speicher
> * Bereitstellen Sie den SQL Server-Operator in einem Kubernetes-cluster 
> * Erstellen des Kubernetes-Geheimnisse
> * Bereitstellen von SQL Server-Instanzen und Health-agents
> * Eine Verbindung mit dem primären Replikat herstellen
> * Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
>[Einführung in Kubernetes](http://docs.microsoft.com/azure/aks/intro-kubernetes)
>[Verwalten von SQLServer in Kubernetes](sql-server-linux-kubernetes-manage.md)