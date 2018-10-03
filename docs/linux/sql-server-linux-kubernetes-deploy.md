---
title: Bereitstellen von SQLServer Always On-Verfügbarkeitsgruppe in Kubernetes-Cluster
description: In diesem Artikel werden die Parameter für die SQL Server Kubernetes Always On Availability Group-Operator globale Anforderungen erläutert.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: fe736fa57ea85e92b69d12f44fca35f4097cd3d6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160060"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-kubernetes-cluster"></a>Stellen Sie einen SQLServer Always On-Verfügbarkeitsgruppe in Kubernetes-Cluster

## <a name="requirements"></a>Anforderungen

- Ein Kubernetes-cluster
- Kubernetes-Version 1.11.0 oder höher
- Mindestens vier Knoten
- ["kubectl"](http://kubernetes.io/docs/tasks/tools/install-kubectl/).

  >[!NOTE]
  >Sie können jede Art von Kubernetes-Cluster verwenden. Um einen Kubernetes-Cluster in Azure Kubernetes Service (AKS) zu erstellen, finden Sie unter [Erstellen eines AKS-Clusters](http://docs.microsoft.com/azure/aks/create-cluster).
  > Das folgende Skript erstellt einen Kubernetes-Cluster mit vier Knoten in Azure.
  >```azure-cli
  az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.1
  >```

## <a name="steps"></a>Schritte

1. Konfigurieren des Speichers

  Konfigurieren Sie in Cloud-Umgebungen wie Azure [persistente Volumes](http://kubernetes.io/docs/concepts/storage/persistent-volumes/) für jede Instanz von SQL Server.

  Zum Erstellen von persistenten Volumes in Azure finden Sie unter `pv.yaml` und `pvc.yaml` in [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates).

  So erstellen Sie den Speicher, die den folgenden Befehl ausführen:

  ```azurecli
  kubectl apply -f <pv.yaml>
  ```

1. Kubernetes-Geheimnisse für das SA-Kennwort und den Hauptschlüssel zu erstellen.

  Das folgende Beispiel erstellt zwei geheime Schlüssel. `sapassword` ist für das SA-Kennwort und `masterkeypassword` für den Hauptschlüssel ist. Vor dem Ausführen dieser Skripts ersetzen `<MyC0mp13xP@55w04d!>` mit anderen komplexen Kennwort für jeden geheimen Schlüssel.

   ```azurecli
   kubectl create secret generic sql-secrets --from-literal='sapassword=<MyC0mp13xP@55w04d!>' --from-literal='masterkeypassword=<MyC0mp13xP@55w04d!>'
   ```

1. Konfigurieren Sie und Bereitstellen Sie des SQL Server-Operator-Manifests.

  Kopieren Sie den SQL Server-Operator `operator.yaml` Datei [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Die `operator.yaml` Datei ist die Bereitstellung Manifiest für den Kubernetes-Operator.

  Um das Manifest zu konfigurieren, aktualisieren Sie die `operator.yaml` Datei für Ihre Umgebung.

  Wenden Sie das Manifest, auf den Kubernetes-Cluster.

  ```azurecli
  kubectl apply -f operator.yaml
  ```

1. Stellen Sie die benutzerdefinierte SQL Server-Ressource bereit.

  Kopieren Sie das SQL Server-Manifest `sqlserver.yaml` aus [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files).

  Wenden Sie das Manifest, auf den Kubernetes-Cluster.

  ```azurecli
  kubectl apply -f sqlserver.yaml
  ```

Nach der Bereitstellung der SQL Server-Manifest wird der Operator die Instanzen von SQL Server als Pods in Containern bereitgestellt.

Nachdem das Skript abgeschlossen ist, erstellt der Kubernetes-Operator, den Speicher, SQL Server-Instanzen, die Load Balancer-Dienste. Sie können überwachen, die Bereitstellung mit [Kubernetes-Dashboard](http://docs.microsoft.com/azure/aks/kubernetes-dashboard).

Nachdem Kubernetes erstellt. Führen Sie die SQL Server-Container die folgenden Schritte aus, um eine Datenbank mit der verfügbarkeitsgruppe hinzuzufügen:

1. [Herstellen einer mit](sql-server-linux-kubernetes-connect.md) auf eine SQL Server-Instanz im Cluster.

1. Erstellen einer Datenbank

1. Führen Sie eine vollständige Sicherung der Datenbank, die die Protokollkette zu starten.

1. Fügen Sie die Datenbank der verfügbarkeitsgruppe hinzu.

Die verfügbarkeitsgruppe wird erstellt, mit automatischem seeding, damit SQL Server automatisch die sekundären Replikate erstellt.

## <a name="next-steps"></a>Nächste Schritte

[Verbinden Sie mit SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-linux-kubernetes-connect.md)

[Verwalten von SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-linux-kubernetes-manage.md)

[SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-ag-kubernetes.md)
