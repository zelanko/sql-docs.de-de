---
title: Machine Learning Services (Python, R)
titleSuffix: SQL Server Big Data Clusters
description: Hier erfahren Sie, wie Sie Python- und R-Skripts auf der Masterinstanz eines SQL Server-Big Data-Clusters mit Machine Learning Services ausführen können.
author: dphansen
ms.author: davidph
ms.date: 04/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
ms.openlocfilehash: d105db3da8a6732c2884af7e42a71441eef6f077
ms.sourcegitcommit: ed5f063d02a019becf866c4cb4900e5f39b8db18
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82643340"
---
# <a name="run-python-and-r-scripts-with-machine-learning-services-on-sql-server-big-data-clusters"></a>Ausführen von Python- und R-Skripts mit Machine Learning Services auf SQL Server-Big Data-Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sie können Python- und R-Skripts auf der Masterinstanz eines [SQL Server-Big Data-Clusters](big-data-cluster-overview.md) mit [Machine Learning Services](../machine-learning/index.yml) ausführen.

> [!NOTE]
> Sie können mit den [SQL Server-Spracherweiterungen](../language-extensions/language-extensions-overview.md) auch Java-Code auf der Masterinstanz ausführen. Wenn Sie die folgenden Schritte befolgen, werden auch die Spracherweiterungen aktiviert.

## <a name="enable-machine-learning-services"></a>Aktivieren von Machine Learning Services

Machine Learning Services wird standardmäßig in Big Data-Clustern installiert und erfordert keine separate Installation.

Führen Sie diese Anweisung auf der Masterinstanz aus, um Machine Learning Services zu aktivieren:

```sql
EXEC sp_configure 'external scripts enabled', 1
RECONFIGURE WITH OVERRIDE
GO
```

Sie können nun Python- und R-Skripts auf der Masterinstanz von Big Data-Clustern ausführen. Informationen zum Ausführen Ihres ersten Skripts finden Sie in den Schnellstarts unter [Nächste Schritte](#next-steps).

>[!NOTE]
>Die Konfigurationseinstellung kann nicht für die Verbindung eines Verfügbarkeitsgruppenlisteners festgelegt werden. Wenn Big Data-Cluster mit Hochverfügbarkeit bereitgestellt werden, legen Sie `external scripts enabled` für alle Replikate fest. Weitere Informationen finden Sie unter [Aktivierung für Cluster mit Hochverfügbarkeit](#enable-on-cluster-with-high-availability).

## <a name="enable-on-cluster-with-high-availability"></a>Aktivierung für Cluster mit Hochverfügbarkeit

Wenn Sie [SQL Server-Big Data-Cluster mit Hochverfügbarkeit bereitstellen](deployment-high-availability.md), erstellt die Bereitstellung eine Verfügbarkeitsgruppe für die Masterinstanz. Legen Sie `external scripts enabled` für alle Instanzen der Verfügbarkeitsgruppe fest, um Machine Learning Services zu aktivieren. Für einen Big Data-Cluster müssen Sie `sp_configure` auf allen Replikaten der SQL Server-Masterinstanz ausführen.

Im folgenden Abschnitt wird beschrieben, wie Sie externe Skripts für alle Instanzen aktivieren.

### <a name="create-an-external-load-balancer-for-each-instance"></a>Erstellen eines externen Lastenausgleichs für jede Instanz

Erstellen Sie für jedes Replikat in der Verfügbarkeitsgruppe einen Lastenausgleich, damit Sie eine Verbindung mit der Instanz herstellen können. 

`kubectl expose pod <pod-name> --port=<connection port number> --name=<load-balancer-name> --type=LoadBalancer -n <kubernetes namespace>`

In den Beispielen dieses Artikels werden die folgenden Werte verwendet:

- `<pod-name>`: `master-#`
- `<connection port number>`: `1533`
- `<load-balancer-name>`: `mymaster-#`
- `<kubernetes namespace>`: `mssql-cluster`

Aktualisieren Sie das folgende Skript für Ihre Umgebung, und führen Sie die Befehle aus:

```bash
kubectl expose pod master-0 --port=1533 --name=mymaster-0 --type=LoadBalancer -n mssql-cluster 
kubectl expose pod master-1 --port=1533 --name=mymaster-1 --type=LoadBalancer -n mssql-cluster
kubectl expose pod master-2 --port=1533 --name=mymaster-2 --type=LoadBalancer -n mssql-cluster 
```

`kubectl` gibt die folgende Ausgabe zurück.

```bash
service/mymaster-0 exposed
service/mymaster-1 exposed
service/mymaster-2 exposed
```

Bei jedem Lastenausgleich handelt es sich um einen Masterreplikatendpunkt.

### <a name="enable-script-execution-on-each-replica"></a>Aktivieren der Skriptausführung auf allen Replikaten

1. Rufen Sie die IP-Adresse für den Masterreplikatendpunkt ab.

   Der folgende Befehl gibt die externe IP-Adresse für den Replikatendpunkt zurück. 

   `kubectl get services <load-balancer-name> -n <kubernetes namespace>`

   Führen Sie die folgenden Befehle aus, um die externe IP-Adresse für alle Replikate dieses Szenarios abzurufen:

   ```bash
   kubectl get services mymaster-0 -n mssql-cluster
   kubectl get services mymaster-1 -n mssql-cluster
   kubectl get services mymaster-2 -n mssql-cluster
   ```

   >[!NOTE]
   > Es kann einige Zeit dauern, bis die externe IP-Adresse verfügbar ist. Führen Sie das obige Skript regelmäßig aus, bis jeder Endpunkt eine externe IP-Adresse zurückgibt.

1. Stellen Sie eine Verbindung mit dem Masterreplikatendpunkt her, und aktivieren Sie die Skriptausführung.

    Führen Sie diese Anweisung aus:

    ```sql
    EXEC sp_configure 'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    GO
    ```

   Sie können den obigen Befehl beispielsweise mit `sqlcmd` ausführen. Im folgenden Beispiel wird eine Verbindung mit dem Masterreplikatendpunkt hergestellt und die Skriptausführung wird aktiviert. Ersetzen Sie die Werte im Skript durch die Werte Ihrer Umgebung.

   ```bash
   sqlcmd -S <IP address>,1533 -U <user name> -P <password> -Q "EXEC sp_configure 'external scripts enabled', 1; RECONFIGURE WITH OVERRIDE;"
   ```

   Wiederholen Sie den Schritt für alle Replikate.

### <a name="demonstration"></a>Demo

Die folgende Abbildung veranschaulicht diesen Prozess.

[![](media/machine-learning-services/example-kube-enable-scripts.png "Demonstrate enable feature on Kubernetes")](media/machine-learning-services/example-kube-enable-scripts.png#lightbox)

Sie können nun Python- und R-Skripts auf der Masterinstanz von Big Data-Clustern ausführen. Informationen zum Ausführen Ihres ersten Skripts finden Sie in den Schnellstarts unter [Nächste Schritte](#next-steps).

### <a name="delete-the-master-replica-endpoints"></a>Löschen der Masterreplikatendpunkte

Löschen Sie die Endpunkte der Replikate im Kubernetes-Cluster. Der in Kubernetes zur Verfügung gestellte Endpunkt ist ein Lastenausgleichsdienst.

Mit dem folgenden Befehl wird der Lastenausgleichsdienst gelöscht.

`kubectl delete svc <load-balancer-name> -n mssql-cluster`

Führen Sie die folgenden Befehle aus, um die Beispiele dieses Artikels abzurufen.

```bash
kubectl delete svc mymaster-0 -n mssql-cluster
kubectl delete svc mymaster-1 -n mssql-cluster
kubectl delete svc mymaster-2 -n mssql-cluster
```

## <a name="next-steps"></a>Nächste Schritte

+ [Schnellstart: Erstellen und Ausführen einfacher Python-Skripts mit SQL Server-Machine Learning Services](../machine-learning/tutorials/quickstart-python-create-script.md)
+ [Schnellstart: Erstellen und Bewerten eines Vorhersagemodells in Python mit SQL Server Machine Learning Services](../machine-learning/tutorials/quickstart-python-train-score-model.md)
+ [Schnellstart: Erstellen und Ausführen einfacher R-Skripts mit SQL Server-Machine Learning Services](../machine-learning/tutorials/quickstart-r-create-script.md)
+ [Schnellstart: Erstellen und Bewerten eines Vorhersagemodells in R mit SQL Server-Machine Learning Services](../machine-learning/tutorials/quickstart-r-train-score-model.md)
