---
title: Bereitstellen einer SQL Server-Always On-Verfügbarkeitsgruppe in einem Kubernetes-Cluster
description: In diesem Artikel werden die globalen Anforderungen für die Parameter für die Kubernetes-Always On-Verfügbarkeitsgruppenoperatoren in SQL Server erläutert.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a4811c1f41c4c8b9a566dc13b3de713576b4980d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952625"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Bereitstellen einer SQL Server-Always On-Verfügbarkeitsgruppe in einem Kubernetes-Cluster

Im Beispiel in diesem Artikel wird eine SQL Server-Always On-Verfügbarkeitsgruppe in einem Kubernetes-Cluster mit drei Replikaten bereitgestellt. Die sekundären Replikate befinden sich im synchronen Commitmodus.

Die Bereitstellung in Kubernetes beinhaltet einen SQL Server-Operator, die SQL Server-Container und Lastenausgleichsdienste. Der Operator orchestriert die Verfügbarkeitsgruppe automatisch. In diesem Artikel wird Folgendes erläutert:

- Bereitstellen des Operators, der SQL Server-Container und der Lastenausgleichsdienste
- Herstellen einer Verbindung zwischen der Verfügbarkeitsgruppe und den Diensten
- Hinzufügen einer Datenbank zur Verfügbarkeitsgruppe

## <a name="requirements"></a>Anforderungen

- Ein AKS-Kubernetes-Cluster mit der aktuellen Version
- Mindestens drei Knoten
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Zugriff auf das GitHub-Repository [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)

> [!NOTE]
> Sie können jede Art von Kubernetes-Cluster verwenden. Informationen zum Erstellen eines Kubernetes-Clusters in Azure Kubernetes Service (AKS) finden Sie unter [Erstellen eines AKS-Clusters](https://docs.microsoft.com/azure/aks/create-cluster).
>
> Verwenden Sie die neueste Version von Kubernetes. Die bestimmte Version hängt von Ihrem Abonnement und Ihrer Region ab. Informationen hierzu finden Sie unter [Unterstützte Kubernetes-Versionen in AKS](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions).  
>
> Mit dem folgenden Skript wird in Azure ein Kubernetes-Cluster mit vier Knoten erstellt. Ersetzen Sie vor der Ausführung des Skripts `<latest version>` durch die neueste verfügbare Version. Beispiel: `1.12.5`.
>
> ```azure-cli
> az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version <latest version> --generate-ssh-keys
> ```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>Bereitstellen des Operators, der SQL Server-Container und der Lastenausgleichsdienste

1. Erstellen Sie einen [Namespace](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/).

      In diesem Beispiel wird ein Namespace mit der Bezeichnung `ag1` verwendet. Führen Sie den folgenden Befehl aus, um den Namespace zu erstellen.
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      Alle Objekte, die zu dieser Lösung gehören, befinden sich im Namespace `ag1`.

1. Konfigurieren Sie das SQL Server-Operatormanifest, und stellen Sie es bereit.

      Kopieren Sie die SQL Server-Datei [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) aus [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      Die `operator.yaml`-Datei ist das Bereitstellungsmanifest für den Kubernetes-Operator.
    
      Wenden Sie das Manifest auf den Kubernetes-Cluster an.
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. Erstellen Sie ein Geheimnis für Kubernetes mit Kennwörtern für das `sa`-Konto und für den Hauptschlüssel der SQL Server-Instanz.

      Erstellen Sie das Geheimnis mit `kubectl`.
      
      Im folgenden Beispiel wird ein Geheimnis namens `sql-secrets` im Namespace `ag1` erstellt. Das Geheimnis speichert zwei Kennwörter:
      
      - `sapassword` speichert das Kennwort für das SQL Server-Konto `sa`.
      - `masterkeypassword` speichert das Kennwort, mit dem der SQL Server-Hauptschlüssel erstellt wird. 
    
   Kopieren Sie das Skript in das Terminal. Ersetzen Sie `<>` durch ein komplexes Kennwort, und führen Sie das Skript aus, um das Geheimnis zu erstellen.
    
   >[!NOTE]
   >Für das Kennwort dürfen die Zeichen `&` und `` ` `` nicht verwendet werden.
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. Stellen Sie die benutzerdefinierte SQL Server-Ressource bereit.

      Kopieren Sie das SQL Server-Manifest [`sqlserver.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) aus [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).
    
      >[!NOTE]
      >In der Datei `sqlserver.yaml` werden die SQL Server-Container, persistente Volumeansprüche, persistente Volumes und Lastenausgleichsdienste beschrieben, die für jede SQL Server-Instanz erforderlich sind.
    
      Wenden Sie das Manifest auf den Kubernetes-Cluster an.
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
Die folgende Abbildung zeigt die erfolgreiche Anwendung von `kubectl apply` für dieses Beispiel.

![Erstellen von sqlservers](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

Nachdem Sie das SQL Server-Manifest angewendet haben, stellt der Operator die SQL Server-Container bereit.

Kubernetes platziert die Container in Pods. Verwenden Sie `kubectl get pods --namespace ag1`, um den Status der Pods anzuzeigen. Die folgende Abbildung zeigt die beispielhafte Bereitstellung, nachdem die SQL Server-Pods bereitgestellt wurden. 

![Erstellte Pods](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>Überwachen der Bereitstellung

Sie können das [Kubernetes-Dashboard mit Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/kubernetes-dashboard) zum Überwachen der Bereitstellung verwenden.

Verwenden Sie `az aks browse`, um das Dashboard zu starten. 

## <a name="connect-to-the-availability-group-with-the-services"></a>Herstellen einer Verbindung zwischen der Verfügbarkeitsgruppe und den Diensten

Im Beispiel [`ag-services.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) aus [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) werden die Lastenausgleichsdienste beschrieben, die eine Verbindung mit Verfügbarkeitsgruppenreplikaten herstellen können. 

- `ag1-primary` stellt einen Endpunkt zum Herstellen einer Verbindung mit dem primären Replikat bereit.
- `ag1-secondary` stellt einen Endpunkt zum Herstellen einer Verbindung mit dem sekundären Replikat bereit.

Wenn Sie die Manifestdatei anwenden, erstellt Kubernetes die Lastenausgleichsdienste für jeden Replikattyp. Der Lastenausgleichsdienst umfasst eine IP-Adresse. Verwenden Sie diese IP-Adresse, um eine Verbindung mit dem benötigten Replikatstyp herzustellen.

Führen Sie den folgenden Befehl aus, um die Dienste bereitzustellen.

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

Verwenden Sie nach Bereitstellung der Dienste `kubectl get services --namespace ag1`, um die IP-Adresse für die Dienste zu identifizieren.

Mit der IP-Adresse können Sie eine Verbindung mit der SQL Server-Instanz herstellen, die die einzelnen Replikatstypen hostet.

Die folgende Abbildung zeigt Folgendes:

- Die Ausgabe von `kubectl get services` für den Namespace `ag1`.

- Die Lastenausgleichsdienste, die für jeden SQL Server-Container erstellt werden. Verwenden Sie die IP-Adressen als Endpunkte, um eine direkte Verbindung mit den Instanzen von SQL Server im Cluster herzustellen.

- Die `sqlcmd`-Verbindung mit dem primären Replikat und mit dem `sa`-Konto über den Lastenausgleichsendpunkt.

![Verbinden](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe

>[!NOTE]
>Zu diesem Zeitpunkt ist das Hinzufügen einer Datenbank zu einer Verfügbarkeitsgruppe mit SQL Server Management Studio nicht möglich. Verwenden Sie Transact-SQL.

Führen Sie zum Hinzufügen einer Datenbank zur Verfügbarkeitsgruppe die folgenden Schritte aus, nachdem Kubernetes die SQL Server-Container erstellt hat.

1. [Stellen Sie eine Verbindung](sql-server-linux-kubernetes-connect.md) mit einer SQL Server-Instanz im Cluster her.

1. Erstellen einer Datenbank

      ```sql
      CREATE DATABASE [demodb]
      ```

1. Beginnen Sie die Protokollkette mit einer vollständigen Sicherung der Datenbank.

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. Fügen Sie die Datenbank zur Verfügbarkeitsgruppe hinzu.

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
Die Verfügbarkeitsgruppe wird mit automatischem Seeding erstellt, sodass SQL Server automatisch die sekundären Replikate erstellt.

Sie können den Status der Verfügbarkeitsgruppe über das Dashboard „Verfügbarkeitsgruppen“ in SQL Server Management Studio anzeigen.

![Dashboard](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>Nächste Schritte

- [Herstellen einer Verbindung mit einer SQL Server-Verfügbarkeitsgruppe in einem Kubernetes-Cluster](sql-server-linux-kubernetes-connect.md)

- [Verwalten einer SQL Server-Verfügbarkeitsgruppe in einem Kubernetes-Cluster](sql-server-linux-kubernetes-manage.md)

- [SQL Server unterstützt Verfügbarkeitsgruppen in Containern in einem Kubernetes-Cluster](sql-server-ag-kubernetes.md)
