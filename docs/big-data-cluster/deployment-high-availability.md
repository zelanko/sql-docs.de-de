---
title: Bereitstellen SQL Server Big Data-Clusters mit hoher Verfügbarkeit
titleSuffix: Deploy SQL Server Big Data Cluster with high availability
description: Erfahren Sie, wie [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Sie (Vorschau) mit hoher Verfügbarkeit bereitstellen.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 307697f43fc1c2615f212ae5f433485814dd62d0
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874704"
---
# <a name="deploy-sql-server-big-data-cluster-with-high-availability"></a>Bereitstellen SQL Server Big Data-Clusters mit hoher Verfügbarkeit

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Zum Zeitpunkt der Bereitstellung eines Big Data Clusters (BDC) können Sie SQL Server Master so konfigurieren, dass er in einer Verfügbarkeits Gruppenkonfiguration bereitgestellt wird. Diese Konfiguration erhöht die Zuverlässigkeit von SQL Server Master, zusätzlich zu der von der Kubernetes-Infrastruktur durch die integrierten Integritäts Überwachung, Fehlererkennung und Failovermechanismen. Verfügbarkeits Gruppen (Availability Groups, AG) fügen der SQL Server Instanz Redundanz hinzu. In dieser Konfiguration werden die Überwachungs-, Fehler Erkennungs-und failovertasks von Big Data Cluster Verwaltungsdienst verwaltet, nämlich dem Steuerungs Dienst.

Außerdem werden andere Verwaltungsaufgaben wie das Einrichten von Datenbankspiegelungs-Endpunkten, das Erstellen der Verfügbarkeits Gruppe und das Hinzufügen von Datenbanken zur Verfügbarkeits Gruppe von der Big Data Cluster Plattform bereitgestellt.

Im folgenden finden Sie einige der Funktionen, die von Verfügbarkeits Gruppen aktiviert werden:

1. Wenn die Einstellungen für hohe Verfügbarkeit in der Bereitstellungs Konfigurationsdatei angegeben sind, wird `containedag` eine einzelne Verfügbarkeits Gruppe mit dem Namen erstellt. Standardmäßig `containedag` verfügt über drei Replikate, einschließlich der primären. Alle CRUD-Vorgänge für die Verfügbarkeits Gruppe werden intern verwaltet.
1. Alle Datenbanken werden automatisch der Verfügbarkeits Gruppe hinzugefügt `master` , `msdb`einschließlich und. Polybase-Konfigurations Datenbanken sind nicht in der Verfügbarkeits Gruppe enthalten, da Sie für jedes Replikat spezifische Metadaten auf Instanzebene enthalten.
1. Zum Herstellen einer Verbindung mit den Verfügbarkeits Gruppen Datenbanken wird automatisch ein externer Endpunkt bereitgestellt. Dieser Endpunkt `master-svc-external` spielt die Rolle des Verfügbarkeits Gruppen-Listener.
1. Für schreibgeschützte Verbindungen mit den sekundären Replikaten wird ein zweiter externer Endpunkt bereitgestellt. 


# <a name="deploy"></a>Bereitstellen

So stellen Sie SQL Server Master in einer Verfügbarkeits Gruppe bereit:

1. Aktivieren der `hadr` Funktion
1. Geben Sie die Anzahl der Replikate für die Verfügbarkeits Gruppe an (mindestens 3).
1. Konfigurieren Sie die Details des zweiten externen Endpunkts, der für Verbindungen mit den schreibgeschützten sekundären Replikaten erstellt wurde.

In den folgenden Schritten wird gezeigt, wie Sie eine Patchdatei erstellen, die diese Einstellungen enthält, und wie `aks-dev-test` Sie `kubeadm-dev-test` Sie auf Konfigurations Profile von oder anwenden. In den folgenden Schritten wird ein Beispiel für das Patchen `aks-dev-test` des Profils zum Hinzufügen der hochverfügbarkeitattribute erläutert. Für eine Bereitstellung in einem kubeadm-Cluster wäre ein ähnlicher Patch anwendbar, aber stellen Sie sicher, dass Sie *nodeport* für den **serviceType** im Abschnitt **Endpunkte** verwenden.

1. `patch.json` Datei erstellen

    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.resources.master.spec",
          "value": {
            "type": "Master",
            "replicas": 3,
            "endpoints": [
              {
                "name": "Master",
                "serviceType": "LoadBalancer",
                "port": 31433
              },
              {
                "name": "MasterSecondary",
                "serviceType": "LoadBalancer",
                "port": 31436
              }
            ],
            "settings": {
              "sql": {
                "hadr.enabled": "true"
              }
            }
          }
        }
      ]
    }
    ```

1. Klonen des Ziel Profils

    ```bash
    azdata bdc config init --source aks-dev-test --target custom-aks
    ```

1. Anwenden der Patchdatei auf Ihr benutzerdefiniertes Profil

    ```bash
    azdata bdc config patch -c custom-aks/bdc.json --patch-file patch.json
    ```

## <a name="connect-to-sql-server-databases"></a>Herstellen einer Verbindung mit SQL Server Datenbanken

Abhängig von der Art der Arbeitsauslastung, die Sie für SQL Server Master ausführen möchten, können Sie entweder eine Verbindung mit dem primären Replikat für Lese-/Schreib-Workloads oder die Datenbanken in den sekundären Replikaten für schreibgeschützte Workloads herstellen. Im folgenden finden Sie eine Übersicht für die einzelnen Verbindungstypen:

### <a name="connect-to-databases-on-the-primary-replica"></a>Herstellen einer Verbindung mit Datenbanken auf dem primären Replikat

Verwenden `sql-server-master` Sie für Verbindungen mit dem primären Replikat den Endpunkt. Dieser Endpunkt ist auch der Listener für die Verfügbarkeits Gruppe. Alle Verbindungen werden im Kontext der Verfügbarkeits Gruppe angezeigt. Beispielsweise führt eine Standardverbindung mit diesem Endpunkt dazu, dass eine Verbindung mit `master` der Datenbank innerhalb der Verfügbarkeits Gruppe hergestellt wird `master` , nicht mit der SQL Server Instanz-Datenbank.

```bash
azdata bdc endpoint list -e sql-server-master -o table
```

`Description                           Endpoint             Name               Protocol`
`------------------------------------  -------------------  -----------------  ----------`
`SQL Server Master Instance Front-End  13.64.235.192,31433  sql-server-master  tds`

> [!NOTE]
> Failoverereignisse können während einer verteilten Abfrage Ausführung auftreten, die auf Daten von Remote Datenquellen wie HDFS oder Daten Pool zugreift. Als bewährte Verfahrensweise sollten Anwendungen so entworfen werden, dass Sie Verbindungs Wiederholungs Logik aufweisen, wenn die von einem Failover verursachten Verbindungen getrennt werden.  
>

### <a name="connect-to-databases-on-the-secondary-replicas"></a>Verbinden mit Datenbanken auf den sekundären Replikaten

Verwenden Sie für schreibgeschützte Verbindungen mit Datenbanken in sekundären Replikaten den `sql-server-master-readonly` -Endpunkt. Dieser Endpunkt verhält sich wie ein Load Balancer für alle sekundären Replikate. Geben Sie den Benutzerdaten Bank Kontext in der Verbindungs Zeichenfolge an.

```bash
azdata bdc endpoint list -e sql-server-master-readonly -o table
```

`Description                                    Endpoint            Name                        Protocol`
`---------------------------------------------  ------------------  --------------------------  ----------`
`SQL Server Master Readable Secondary Replicas  13.64.238.24,31436  sql-server-master-readonly  tds`

### <a id="instance-connect"></a>Herstellen einer Verbindung mit SQL Server Instanz

Für bestimmte Vorgänge wie das Festlegen von Konfigurationen auf Serverebene oder das manuelle Hinzufügen einer Datenbank zur Verfügbarkeits Gruppe (für den Fall, dass die Datenbank mit einem Wiederherstellungs Workflow erstellt wurde), benötigen Sie eine Verbindung mit der Instanz. Zum Bereitstellen dieser Verbindung machen Sie einen externen Endpunkt verfügbar. Es folgt ein Beispiel, das zeigt, wie Sie diesen Endpunkt verfügbar machen und dann die Datenbank, die mit einem Wiederherstellungs Workflow erstellt wurde, der Verfügbarkeits Gruppe hinzufügen.

- Bestimmen Sie den Pod, der das primäre Replikat hostet, indem Sie eine Verbindung mit dem `sql-server-master` Endpunkt herstellen und

    ```sql
    SELECT @@SERVERNAME
   ```

- Verfügbar machen des externen Endpunkts durch Erstellen eines neuen Kubernetes-Dienstanbieter

    Führen Sie für einen kubeadm-Cluster den folgenden Befehl aus. Ersetzen `podName` Sie durch den Namen des Servers, der im vorherigen Schritt `serviceName` zurückgegeben wurde, mit dem bevorzugten Namen für den `namespaceName`erstellten Kubernetes-Dienst und * mit dem Namen Ihres BDC-Clusters.

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=NodePort
    ```

    Führen Sie für einen AKS-Cluster ausführen denselben Befehl aus, mit dem Unterschied, dass der Typ des `LoadBalancer`erstellten Dienstanbieter ist. Zum Beispiel: 

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=LoadBalancer
    ```

    Im folgenden finden Sie ein Beispiel für diesen Befehl, der für AKS ausgeführt wird, wobei der `master-0`Pod, der das primäre Host Host-

    ```bash
    kubectl -n mssql-cluster expose pod master-0 --port=1533  --name=master-sql-0 --type=LoadBalancer
    ```

    Die IP-Adresse des erstellten Kubernetes-Dienstanbieter erhalten Sie:

    ```bash
    kubectl get services -n <namespaceName>
    ```

> [!IMPORTANT]
> Als bewährte Vorgehensweise sollten Sie einen Bereinigung durchführen, indem Sie den oben erstellten Kubernetes-Dienst löschen, indem Sie den folgenden Befehl ausführen:
>
>```bash
>kubectl delete svc master-sql-0 -n mssql-cluster
>```

- Fügen Sie die Datenbank der Verfügbarkeitsgruppe hinzu.

    Damit die Datenbank der Verfügbarkeits Gruppe hinzugefügt werden kann, muss Sie im vollständigen Wiederherstellungs Modus ausgeführt werden, und es muss eine Protokoll Sicherung durchgeführt werden. Verwenden Sie die IP-Adresse des oben erstellten Kubernetes-Dienstanbieter, und stellen Sie eine Verbindung mit der SQL Server Instanz her, und führen Sie dann wie unten gezeigt die

    ```sql
    ALTER DATABASE <databaseName> SET RECOVERY FULL;
    BACKUP DATABASE <databaseName> TO DISK='<filePath>'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE <databaseName>
    ```

    Im folgenden Beispiel wird eine Datenbank namens `sales` hinzugefügt, die auf der-Instanz wieder hergestellt wurde:

    ```sql
    ALTER DATABASE sales SET RECOVERY FULL;
    BACKUP DATABASE sales TO DISK='/var/opt/mssql/data/sales.bak'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE sales
    ```

## <a name="known-limitations"></a>Bekannte Einschränkungen

Dies sind die bekannten Probleme und Einschränkungen bei Verfügbarkeits Gruppen für SQL Server Master in Big Data Cluster:

- Datenbanken, die als Ergebnis von anderen `CREATE DATABASE` Workflows `RESTORE`als `CREATE DATABASE FROM SNAPSHOT` like erstellt werden, werden nicht automatisch der Verfügbarkeits Gruppe hinzugefügt. Stellen Sie eine [Verbindung mit der Instanz her,](#instance-connect) und fügen Sie die Datenbank manuell zur Verfügbarkeits Gruppe hinzu
- Bestimmte Vorgänge wie das Ausführen von Server Konfigurations `sp_configure` Einstellungen mit erfordern eine Verbindung mit der Master Instanz. Der entsprechende primäre Endpunkt kann nicht verwendet werden. Befolgen Sie [die Anweisungen](#instance-connect) , um eine Verbindung mit der SQL Server `sp_configure`Instanz herzustellen und auszuführen.
- Die Konfiguration für hohe Verfügbarkeit muss bei der Bereitstellung von BDC erstellt werden. Die Konfiguration mit hoher Verfügbarkeit mit Verfügbarkeits Gruppen kann nach der Bereitstellung nicht aktiviert werden.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Verwenden von Konfigurationsdateien in Big Data Cluster Bereitstellungen finden [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] ](deployment-guidance.md#configfile)Sie unter Bereitstellen von auf Kubernetes.
- Weitere Informationen zur Verfügbarkeits Gruppenfunktion für SQL Server finden Sie unter [Übersicht über Always on Verfügbarkeits Gruppen (SQL Server)](https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server?view=sql-server-2017).
