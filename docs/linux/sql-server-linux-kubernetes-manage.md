---
title: Verwalten einer SQL Server-Always On-Verfügbarkeitsgruppe in Kubernetes
description: In diesem Artikel wird das Verwalten einer SQL Server-Always On-Verfügbarkeitsgruppe in Kubernetes erläutert.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 893e502c35ae33ce6ff87efd88049db97a40f875
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952542"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>Verwalten einer SQL Server-Always On-Verfügbarkeitsgruppe in Kubernetes

Um eine Always On-Verfügbarkeitsgruppen in Kubernetes zu verwalten, erstellen Sie ein Manifest, und wenden Sie es auf den Cluster an. Das Manifest ist eine `.yaml`-Datei.  

Die Beispiele in diesem Artikel gelten für alle Kubernetes-Cluster. Die Szenarien in diesen Beispielen gelten für einen Cluster in Azure Kubernetes Service.

Ein Beispiel für die komplette Bereitstellung finden Sie unter [Bereitstellen einer SQL Server-Always On-Verfügbarkeitsgruppe in einem Kubernetes-Cluster](sql-server-linux-kubernetes-deploy.md).

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>Failover: SQL Server-Verfügbarkeitsgruppe in Kubernetes

Um ein Failover oder eine Verschiebung eines primären Replikats zu einem anderen Knoten in einer Verfügbarkeitsgruppe auszuführen, gehen Sie folgendermaßen vor:

1. Definieren Sie einen Auftrag in einer Manifestdatei.

  [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml): Diese Datei im GitHub-Repository [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) beschreibt einen Failoverauftrag.

  Kopieren Sie die Manifestdatei in Ihr Verwaltungsterminal.

  Aktualisieren Sie die Datei für Ihre Umgebung.

  - Ersetzen Sie `<containerName>` durch den Podnamen (z.B. mssql2-0) des erwarteten Verfügbarkeitsgruppenziels.
  - Wenn sich die Verfügbarkeitsgruppe nicht im Namespace `ag1` befindet, ersetzen Sie `ag1` durch den Namespace.

  Diese Datei definiert einen Failoverauftrag namens `manual-failover`.

1. Verwenden Sie `kubectl apply` zum Bereitstellen des Auftrags. Mit dem folgenden Skript wird der Auftrag bereitgestellt.

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  Nach der Bereitstellung des Auftrags führt Kubernetes mit dem SQL Server-Operator die folgenden Aufgaben aus:
  
  - Herabstufen des primären Replikats zu einem sekundären Replikat
  
  - Heraufstufen des angegebenen Replikats zum primären Replikat
  
  Nach dem Anwenden der Manifestdatei führt Kubernetes den Auftrag aus. Durch den Auftrag wählt der Supervisor einen neuen Leader aus und verschiebt das primäre Replikat in die SQL Server-Instanz des Leaders.

1. Überprüfen Sie, ob der Auftrag abgeschlossen ist.
  
  Nachdem Kubernetes den Auftrag ausgeführt hat, können Sie das Protokoll überprüfen.
  
  Das folgende Beispiel gibt den Status des Auftrags `manual-failover` zurück.

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. Löschen Sie den manuellen Failoverauftrag. 

  >[!IMPORTANT]
  >Sie müssen den Auftrag manuell löschen, bevor Sie einen weiteren manuellen Failoverauftrag ausgeben.
  > 
  >Das Auftragsobjekt in Kubernetes bleibt nach Abschluss des Vorgangs erhalten, sodass Sie den Status anzeigen können. Sie müssen alte Aufträge manuell löschen, nachdem Sie ihren Status gesehen haben. Durch das Löschen eines Auftrags werden auch die Kubernetes-Protokolle gelöscht. Wenn Sie den Auftrag nicht löschen, treten bei zukünftigen Failoveraufträgen Fehler auf, es sei denn, Sie ändern den Auftragsnamen und die Podauswahl. Weitere Informationen finden Sie unter [Jobs - Run to Completion](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) (Aufträge – Ausführen bis Abschluss).

  Der folgende Befehl löscht den Auftrag.

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>Rotieren von Anmeldeinformationen

Rotieren sie Anmeldeinformationen, um das Kennwort für das SQL Server-Konto `sa` und den [Diensthauptschlüssel](../relational-databases/security/encryption/service-master-key.md) für SQL Server zurückzusetzen. 

Um diese Aufgabe abzuschließen, erstellen Sie neue Geheimnisse im Kubernetes-Cluster und erstellen dann einen Auftrag, um die Anmeldeinformationen zu rotieren.

Erstellen Sie vor dem Rotieren von Anmeldeinformationen ein neues Geheimnis für das Kennwort und den Hauptschlüssel.

Das folgende Skript erstellt ein Geheimnis namens `new-sql-secrets`. Bevor Sie das Skript ausführen, ersetzen Sie `<>` durch komplexe Kennwörter für `sapassword` und `masterkeypassword`. Verwenden Sie für jeden entsprechenden Wert unterschiedliche Kennwörter.

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

Führen Sie die folgenden Schritte für jede Instanz von SQL Server aus, die den Hauptschlüssel oder das `sa`-Kennwort benötigt.

1. Kopieren Sie [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) in Ihr Verwaltungsterminal.

  [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) im GitHub-Repository [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/) ist ein Beispiel für ein Manifest für diesen Auftrag.

  Bevor Sie dieses Manifest anwenden, aktualisieren Sie das Manifest für Ihre Umgebung. Überprüfen Sie die folgenden Einstellungen, und ändern Sie sie nach Bedarf.

  - Überprüfen Sie den Namespace. Aktualisieren Sie ihn ggf. Das folgende Beispiel in einem Manifest gilt für einen Namespace mit dem Namen `ag1`.

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - Überprüfen Sie den Namen der SQL Server-Instanz. Aktualisieren Sie ihn ggf. Das folgende Beispiel in einer Manifestspezifikation gilt für eine SQL Server-Instanz namens `mssql1`.

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  Speichern Sie die aktualisierte Manifestdatei auf Ihrer Arbeitsstation.

1. Verwenden Sie `kubectl`, um den Auftrag bereitzustellen.

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes aktualisiert den Hauptschlüssel und das `sa`-Kennwort für eine Instanz von SQL Server in einer Verfügbarkeitsgruppe.

1. Überprüfen Sie, ob der Auftrag abgeschlossen ist. Führen Sie den folgenden Befehl aus: Überprüfen Sie, ob der Auftrag abgeschlossen ist, und führen Sie Folgendes aus: 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  Nachdem der Auftrag erfolgreich ausgeführt wurde, werden der Hauptschlüssel und das `sa`-Kennwort für eine Instanz von SQL Server aktualisiert.


1. Bevor Sie den Auftrag erneut ausführen, löschen Sie diesen Auftrag. Jeder Auftragsname muss eindeutig sein.

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

Um das gleiche `sa`-Kennwort für alle Instanzen von SQL Server festzulegen, wiederholen Sie die oben genannten Schritte für jede SQL Server-Instanz.

## <a name="next-steps"></a>Nächste Schritte

[Zugriff auf das Kubernetes-Dashboard mit Azure Kubernetes Service (AKS)](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[SQL Server-Verfügbarkeitsgruppe in einem Kubernetes-Cluster](sql-server-ag-kubernetes.md)
