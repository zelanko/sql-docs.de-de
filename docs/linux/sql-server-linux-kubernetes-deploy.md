---
title: Bereitstellen einer SQL Server Always On-verfügbarkeitsgruppe in einem Kubernetes-cluster
description: In diesem Artikel werden die Parameter für die SQL Server Kubernetes Always On Availability Group-Operator globale Anforderungen erläutert.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3a5bc7dfcfd36c16b6f281db8eb57e74e97601b6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63231383"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Bereitstellen einer SQL Server Always On-verfügbarkeitsgruppe in einem Kubernetes-cluster

Im Beispiel in diesem Artikel wird eine SQL Server Always On-verfügbarkeitsgruppe in einem Kubernetes-Cluster mit drei Replikaten bereitgestellt. Die sekundären Replikate werden im synchronen Commit-Modus.

In Kubernetes, umfasst die Bereitstellung eine SQL Server-Operator, der SQL Server-Container und Laden Balancer Dienste. Der Operator orchestriert die verfügbarkeitsgruppe automatisch. In diesem Artikel wird erläutert, wie Sie:

- Bereitstellen der Operator, SQL Server-Container und Dienste des Lastenausgleichs.
- Verbinden Sie mit der verfügbarkeitsgruppe mit den Diensten.
- Hinzufügen einer Datenbank mit der verfügbarkeitsgruppe an.

## <a name="requirements"></a>Anforderungen

- Eine ACS-Kubernetes-Cluster mit der neuesten version
- Mindestens drei Knoten
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Der Zugriff auf die [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) GitHub-Repository

> [!NOTE]
> Sie können jede Art von Kubernetes-Cluster verwenden. Um einen Kubernetes-Cluster in Azure Kubernetes Service (AKS) zu erstellen, finden Sie unter [Erstellen eines AKS-Clusters](https://docs.microsoft.com/azure/aks/create-cluster).
>
> Verwenden Sie die neueste Version von Kubernetes. Die spezifische Version hängt von Ihrem Abonnement und Region ab. Finden Sie unter [unterstützt Kubernetes-Versionen in AKS](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions).  
>
> Das folgende Skript erstellt einen Kubernetes-Cluster mit vier Knoten in Azure. Vor dem Ausführen des Skripts ersetzt `<latest version>` mit den neuesten verfügbaren Version. Beispiel: `1.12.5`.
>
> ```azure-cli
> az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version <latest version> --generate-ssh-keys
> ```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>Bereitstellen der Operator, SQL Server-Container und Dienste des Lastenausgleichs

1. Erstellen Sie eine [Namespace](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).

      Dieses Beispiel verwendet einen Namespace mit dem Namen `ag1`. Führen Sie den folgenden Befehl aus, um den Namespace zu erstellen.
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      Alle Objekte, die mit dieser Lösung gehören befinden sich in der `ag1` Namespace.

1. Konfigurieren Sie und Bereitstellen Sie des SQL Server-Operator-Manifests.

      Kopieren Sie die SQL Server [ `operator.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) Datei [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      Die `operator.yaml` Datei ist das Bereitstellungsmanifest für den Kubernetes-Operator.
    
      Wenden Sie das Manifest, auf den Kubernetes-Cluster.
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. Erstellen Sie ein Geheimnis für Kubernetes mit Kennwörtern für die `sa` Konto und der Hauptschlüssel der SQL Server-Instanz.

      Erstellen Sie den geheimen Schlüssel mit `kubectl`.
      
      Das folgende Beispiel erstellt einen geheimen Schlüssel mit dem Namen `sql-secrets` in die `ag1` Namespace. Der geheime Schlüssel werden zwei Kennwörter gespeichert:
      
      - `sapassword` Speichert das Kennwort für den SQL Server `sa` Konto.
      - `masterkeypassword` Speichert das Kennwort verwendet, um den SQL Server-Hauptschlüssel zu erstellen. 
    
   Kopieren Sie das Skript auf Ihr Terminal ein. Ersetzen Sie jeden `<>` komplexes Kennwort, und führen Sie das Skript zum Erstellen des Geheimnisses.
    
   >[!NOTE]
   >Verwenden Sie das Kennwort kann nicht `&` oder `` ` `` Zeichen.
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. Stellen Sie die benutzerdefinierte SQL Server-Ressource bereit.

      Kopieren Sie das SQL Server-Manifest [ `sqlserver.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) aus [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      >[!NOTE]
      >Die `sqlserver.yaml` Datei beschreibt die SQL Server-Container, persistentes Volume Ansprüche, persistente Volumes und Lastenausgleichsdienste, die für jede SQL Server-Instanz erforderlich sind.
    
      Wenden Sie das Manifest, auf den Kubernetes-Cluster.
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
Die folgende Abbildung zeigt die erfolgreiche Anwendung des `kubectl apply` für dieses Beispiel.

![Erstellen von "SQLServers"](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

Nachdem Sie das Manifest für die SQL Server angewendet haben, wird der Operator die SQL Server-Container bereitgestellt.

Kubernetes wird die Container in Pods. Verwendung `kubectl get pods --namespace ag1` um den Status der Pods anzuzeigen. Die folgende Abbildung zeigt die Beispiel für eine Bereitstellung aus, nachdem die SQL Server-Pods bereitgestellt wurden. 

![erstellt von pods](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>Überwachen der Bereitstellung

Sie können die [Kubernetes-Dashboard mit Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/kubernetes-dashboard) zum Überwachen der Bereitstellung.

Verwendung `az aks browse` zum Starten des Dashboards. 

## <a name="connect-to-the-availability-group-with-the-services"></a>Mit der verfügbarkeitsgruppe mit den Diensten verbinden

Die [ `ag-services.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) aus [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) Beispiel wird beschrieben, den Lastenausgleich-Dienste, die Replikate der verfügbarkeitsgruppe herstellen können. 

- `ag1-primary` wird ein Endpunkt für die Verbindung mit dem primären Replikat.
- `ag1-secondary` wird ein Endpunkt für die Verbindung für jedes sekundäre Replikat.

Wenn Sie die Manifestdatei anwenden, wird Kubernetes die Dienste des Lastenausgleichs für jeden Typ des Replikats erstellt. Der Dienst einen Lastenausgleich umfasst eine IP-Adresse. Verwenden Sie diese IP-Adresse für die Verbindung der Art des Replikats, die Sie benötigen.

Führen Sie den folgenden Befehl, um die Dienste bereitzustellen.

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

Verwenden Sie nach der Bereitstellung der Dienste `kubectl get services --namespace ag1` um die IP-Adresse für die Dienste zu identifizieren.

Die IP-Adresse können Sie mit der SQL Server-Instanz, hostet jede Art des Replikats verbinden.

Die folgende Abbildung zeigt:

- Die Ausgabe von `kubectl get services` für den Namespace `ag1`.

- Die Dienste auf den Lastenausgleich, die für jeden SQL Server-Container erstellt werden. Verwenden Sie diese IP-Adressen als Endpunkte zur direkten Verbindung mit Instanzen von SQL Server im Cluster.

- Die `sqlcmd` Verbindung mit dem primären Replikat mit der `sa` Konto über den Load Balancer-Endpunkt.

![Verbinden](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe

>[!NOTE]
>Zu diesem Zeitpunkt können keine SQL Server Management Studio eine Datenbank zu einer verfügbarkeitsgruppe hinzufügen. Verwenden von Transact-SQL.

Nachdem die SQL Server-Container mit Kubernetes erstellt wird, führen Sie die folgenden Schritte aus, um eine Datenbank mit der verfügbarkeitsgruppe hinzuzufügen.

1. [Herstellen einer mit](sql-server-linux-kubernetes-connect.md) auf eine SQL Server-Instanz im Cluster.

1. Erstellen einer Datenbank

      ```sql
      CREATE DATABASE [demodb]
      ```

1. Führen Sie eine vollständige Sicherung der Datenbank, die die Protokollkette zu starten.

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. Fügen Sie die Datenbank der verfügbarkeitsgruppe hinzu.

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
Die verfügbarkeitsgruppe mit automatischem seeding, damit SQL Server erstellt automatisch die sekundären Replikate erstellt.

Sie können den Status der verfügbarkeitsgruppe aus dem SQL Server Management Studio-Verfügbarkeitsgruppen-Dashboard anzeigen.

![Dashboard](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>Nächste Schritte

- [Herstellen einer Verbindung eine SQL Server-verfügbarkeitsgruppe in einem Kubernetes-Cluster mit](sql-server-linux-kubernetes-connect.md)

- [Verwalten Sie eine SQL Server-verfügbarkeitsgruppe in einem Kubernetes-cluster](sql-server-linux-kubernetes-manage.md)

- [SQL Server unterstützt-Verfügbarkeitsgruppen, für Container in einem Kubernetes-cluster](sql-server-ag-kubernetes.md)
