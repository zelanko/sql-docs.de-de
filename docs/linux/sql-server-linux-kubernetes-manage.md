---
title: Verwalten einer SQL Server Always On Availability Group Kubernetes
description: In diesem Artikel wird erläutert, wie Sie eine SQL Server AlwaysOn-Verfügbarkeitsgruppe in Kubernetes zu verwalten.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 808f49ff5060ba6a6ffe9e864cfc2710fe6251e6
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705525"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Verwalten von SQLServer Always On-Verfügbarkeitsgruppe Kubernetes

Verwalten einer AlwaysOn-Verfügbarkeitsgruppe in Kubernetes, erstellen Sie ein Manifest, und klicken Sie auf den Cluster anwenden. Das Manifest ist eine `.yaml` Datei.  

In die Beispielen in diesem Artikel gelten für alle Kubernetes-Cluster. Die Szenarien in diesen Beispielen werden für einen Cluster in Azure Kubernetes Service angewendet.

Sehen Sie ein Beispiel für die vollständige Bereitstellung im [Bereitstellen einer SQL Server AlwaysOn-Verfügbarkeitsgruppe in Kubernetes-Cluster](sql-server-linux-kubernetes-deploy.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Failover – SQL Server-verfügbarkeitsgruppe auf Kubernetes

Um ein Failover oder Verschiebung eines primären Replikats auf einen anderen Knoten in einer verfügbarkeitsgruppe befindet, führen Sie die folgenden Schritte aus:

1. Definieren Sie einen Auftrag in einer Manifestdatei an.

  [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml) – in der [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) Github-Repository wird beschrieben, einen failoverauftrag.

  Kopieren Sie die Manifestdatei, in der Verwaltung der Terminalserver.

  Aktualisieren Sie die Datei für Ihre Umgebung.

  - Ersetzen Sie dies `<containerName>` mit den podnamen (z. B. mssql2-0) des Ziels Gruppe erwarteten Verfügbarkeit.
  - Wenn die verfügbarkeitsgruppe nicht die `ag1` Namespace ersetzen `ag1` mit dem Namespace.

  Diese Datei definiert einen failoverauftrag, der mit dem Namen `manual-failover`.

1. Verwenden Sie zum Bereitstellen des Auftrags `kubectl apply`. Das folgende Skript wird den Auftrag bereitgestellt.

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  Nachdem der Auftrag bereitgestellt wurde, führt Kubernetes, mit der SQL Server-Operator, die folgenden Aufgaben aus:
  
  - Stuft die sekundäre Datenbank des primären Replikats
  
  - Stuft das angegebene Replikat zum primären Replikat
  
  Nachdem Sie den manifest-Datei anwenden, führt Kubernetes den Auftrag an. Der Auftrag wird den Supervisor eine neue übergeordnete Instanz wählen und das primäre Replikat mit der SQL Server-Instanz, von der übergeordneten Instanz verschiebt.

1. Stellen Sie sicher, dass der Auftrag abgeschlossen ist.
  
  Nachdem der Auftrag Kubernetes ausgeführt wurde, können Sie das Protokoll überprüfen.
  
  Das folgende Beispiel gibt den Status des Auftrags mit dem Namen `manual-failover`.

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. Löscht den Auftrag für manuelles Failover. 

  >[!IMPORTANT]
  >Sie müssen den Auftrag manuell löschen, bevor Sie ein weiteres Manuelles Failover ausführen.
  > 
  >Das Auftragsobjekt in Kubernetes bleibt nach dem Abschluss, damit Sie deren Status anzeigen können. Sie müssen die alten Aufträge manuell zu löschen, nach deren Status zu beachten. Den Auftrag gelöscht wird, auch die Kubernetes-Protokolle. Wenn Sie den Auftrag nicht löschen, fehl, wenn Sie den Namen des Auftrags und die Pod-Auswahl ändern, zukünftige Failover-Aufträgen auf. Weitere Informationen finden Sie unter [Ausführen von Aufträgen – bis zum Abschluss](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/).

  Der folgende Befehl löscht den Auftrag.

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>Rotieren von Anmeldeinformationen

Rotieren von Anmeldeinformationen zum Zurücksetzen des Kennworts für den SQL Server `sa` -Konto und der SQL Server [Diensthauptschlüssel](../relational-databases/security/encryption/service-master-key.md). 

Um diese Aufgabe abzuschließen, Sie Erstellen neuer geheimer Schlüssel im Kubernetes-Cluster und erstellen Sie dann auf einen Auftrag, um die Anmeldeinformationen zu drehen.

Stellen Sie vor dem Rotieren von Anmeldeinformationen einen neuen geheimen Schlüssel, für das Kennwort und den Hauptschlüssel ein.

Das folgende Skript erstellt einen geheimen Schlüssel mit dem Namen `new-sql-secrets`. Ersetzen Sie vor dem Ausführen des Skripts `<>` mit komplexe Kennwörter für die `sapassword` und `masterkeypassword`. Verwenden Sie andere Kennwörter für jeden entsprechenden Wert ein.

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

Führen Sie die folgenden Schritte aus, für jede Instanz von SQL Server, die der Hauptschlüssel benötigt oder `sa` Kennwort.

1. Kopie [ `rotate-creds.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) zu Ihrem terminal Administration.

  [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) in der [Sql Server Samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/) Github-Repository ist ein Beispiel für ein Manifest für diesen Auftrag.

  Bevor Sie dieses Manifest anwenden, aktualisieren Sie das Manifest für Ihre Umgebung. Überprüfen Sie, und ändern Sie die folgenden Einstellungen nach Bedarf.

  - Überprüfen Sie den Namespace aus. Aktualisieren Sie bei Bedarf. Im folgende Beispiel in einem Manifest zu einem Namespace namens gilt `ag1`.

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - Überprüfen Sie den Namen der SQL Server-Instanz aus. Aktualisieren Sie bei Bedarf. Im folgende Beispiel in einer Manifestdatei Spezifikation angewendet wird, eine SQL Server-Instanz, die mit dem Namen `mssql1`.

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  Speichern Sie die aktualisierte Manifestdatei auf Ihrer Arbeitsstation.

1. Verwendung `kubectl` zum Bereitstellen des Auftrags.

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes aktualisiert den Hauptschlüssel und `sa` Kennwort für eine Instanz von SQL Server in einer verfügbarkeitsgruppe.

1. Stellen Sie sicher, dass der Auftrag abgeschlossen ist. Führen Sie den folgenden Befehl aus: Um sicherzustellen, dass der Auftrag abgeschlossen ist, ausführen 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  Nach erfolgreicher Ausführung des Auftrags, den Hauptschlüssel und `sa` Kennwort für eine Instanz von SQL Server werden aktualisiert.


1. Bevor Sie den Auftrag erneut ausführen, löschen Sie den Auftrag. Jeder Auftragsname muss eindeutig sein.

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

Festzulegende gleich `sa` Kennwort für alle Instanzen von SQL Server, wiederholen Sie die oben genannten Schritte für jede Instanz von SQL Server.

## <a name="next-steps"></a>Nächste Schritte

[Zugriff auf das Kubernetes-Dashboard mit Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-ag-kubernetes.md)
