---
title: Bereitstellen von Big Data-Clustern in SQL Server mit Hochverfügbarkeit
titleSuffix: Deploy SQL Server Big Data Cluster with high availability
description: Erfahren Sie, wie Sie Big Data-Cluster in SQL Server mit Hochverfügbarkeit bereitstellen.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 09/18/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 17aaed99c8adb73b88a2d81482fcdefc7d8f68fd
ms.sourcegitcommit: c74bb5944994e34b102615b592fdaabe54713047
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90990018"
---
# <a name="deploy-sql-server-big-data-cluster-with-high-availability"></a>Bereitstellen von Big Data-Clustern in SQL Server mit Hochverfügbarkeit

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Da SQL Server-Big Data-Cluster bei Kubernetes als containerisierte Anwendungen eingesetzt werden und Funktionen wie zustandsbehaftete Mengen und persistente Speicherung verwenden, verfügt diese Infrastruktur über integrierte Integritätsüberwachungs-, Fehlererkennungs- und Failovermechanismen, die Clusterkomponenten nutzen, um die Dienstintegrität zu erhalten. Für eine höhere Zuverlässigkeit können Sie auch die SQL Server-Masterinstanz und/oder HDFS-Namensknoten und gemeinsame Spark-Dienste konfigurieren, um sie mit zusätzlichen Replikaten in einer hochverfügbaren Konfiguration bereitzustellen. Überwachung, Fehlererkennung und automatisches Failover werden von dem Verwaltungsdienst für Big Data-Cluster verwaltet, der auch als Steuerungsdienst bezeichnet wird. Dieser Dienst wird ohne Benutzereingriff bereitgestellt – vom Einrichten der Verfügbarkeitsgruppe, Konfigurieren von Endpunkten für die Datenbankspiegelung, Hinzufügen von Datenbanken zur Verfügbarkeitsgruppe bis hin zur Failover- und Upgradekoordination. 

Die folgende Abbildung zeigt, wie eine Verfügbarkeitsgruppe in einem Big Data-Cluster in SQL Server bereitgestellt wird:

:::image type="content" source="media/deployment-high-availability/contained-ag.png" alt-text="high-availability-ag-bdc":::

Dies sind einige der Möglichkeiten, die Ihnen Verfügbarkeitsgruppen bieten:

- Wenn die Hochverfügbarkeitseinstellungen in der Konfigurationsdatei für die Bereitstellung angegeben sind, wird eine einzige Verfügbarkeitsgruppe mit dem Namen `containedag` erstellt. Standardmäßig gibt es für `containedag` drei Replikate, einschließlich des primären Replikats. Alle CRUD-Vorgänge für die Verfügbarkeitsgruppe werden intern verwaltet – auch die Erstellung der Verfügbarkeitsgruppe oder die Verknüpfung von Replikaten mit der erstellten Verfügbarkeitsgruppe. Zusätzliche Verfügbarkeitsgruppen können in der SQL Server-Masterinstanz in einem Big Data-Cluster nicht erstellt werden.
- Alle Datenbanken werden automatisch zur Verfügbarkeitsgruppe hinzugefügt, einschließlich aller Benutzer- und Systemdatenbanken wie `master` und `msdb`. Diese Funktion bietet eine Einzelsystemansicht zu den Replikaten der Verfügbarkeitsgruppen. Weitere Modelldatenbanken, `model_replicatedmaster` und `model_msdb`, werden für das Seeding des replizierten Teils der Systemdatenbanken verwendet. Zusätzlich zu diesen Datenbanken sehen Sie die Datenbanken `containedag_master` und `containedag_msdb`, wenn Sie sich direkt mit der Instanz verbinden. Die `containedag`-Datenbanken repräsentieren die Elemente `master` und `msdb` innerhalb der Verfügbarkeitsgruppe.

  > [!IMPORTANT]
  > Datenbanken, die auf der Instanz als Ergebnis von Workflows wie das Anfügen einer Datenbank erstellt wurden, werden nicht automatisch der Verfügbarkeitsgruppe hinzugefügt, und der Big Data-Clusteradministrator müsste diese manuell hinzufügen. Im Abschnitt [Verbinden mit einer SQL Server-Instanz](#instance-connect) finden Sie Anweisungen zum Aktivieren eines temporären Endpunkts der Masterdatenbank der SQL Server-Instanz. Vor dem Release von SQL Server 2019 CU2 haben Datenbanken, die aufgrund einer RESTORE-Anweisung erstellt wurden, dasselbe Verhalten aufgewiesen und erforderten, dass die Datenbanken manuell zur enthaltenen Verfügbarkeitsgruppe hinzugefügt werden.
  >
- Polybase-Konfigurationsdatenbanken sind nicht in der Verfügbarkeitsgruppe enthalten, da sie für jedes Replikat spezifische Metadaten auf Instanzebene enthalten.
- Ein externer Endpunkt wird automatisch für die Verbindung mit Datenbanken innerhalb der Verfügbarkeitsgruppe bereitgestellt. Der Endpunkt `master-svc-external` übernimmt die Rolle des Listeners der Verfügbarkeitsgruppe.
- Ein zweiter externer Endpunkt ist für schreibgeschützte Verbindungen zu den sekundären Replikaten vorgesehen, um die Workloads bei Lesevorgängen aufzuskalieren.

## <a name="deploy"></a>Bereitstellen

So stellen Sie einen SQL Server-Master in einer Verfügbarkeitsgruppe bereit:

1. Aktivieren Sie das `hadr`-Feature.
1. Geben Sie die Anzahl der Replikate für die Verfügbarkeitsgruppe an (mindestens 3).
1. Konfigurieren Sie die Details des zweiten externen Endpunkts, der für Verbindungen mit den schreibgeschützten sekundären Replikaten erstellt wurde.

Sie können entweder die integrierten `aks-dev-test-ha`- oder `kubeadm-prod`-Konfigurationsprofile verwenden, um die Big Data-Cluster anzupassen. Diese Profile enthalten die Einstellungen, die für Ressourcen erforderlich sind, für die Sie zusätzliche Hochverfügbarkeit konfigurieren können. Im Folgenden finden Sie beispielsweise einen Abschnitt in der `bdc.json`-Konfigurationsdatei, der für das Aktivieren von Verfügbarkeitsgruppen für eine SQL Server-Masterinstanz relevant ist.  

```json
{
  ...
    "spec": {
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
  ...
}
```

In den nächsten Schritten wird ein Beispiel dazu beschrieben, wie Sie die Konfiguration für Ihre Big Data-Clusterbereitstellung ausgehend von dem `aks-dev-test-ha`-Profil anpassen. Bei einer Bereitstellung in einem `kubeadm`-Cluster sind die Schritte ähnlich, aber stellen Sie sicher, dass Sie `NodePort` als `serviceType` im Abschnitt `endpoints` verwenden.

1. Klonen des Zielprofils

    ```bash
    azdata bdc config init --source aks-dev-test-ha --target custom-aks-ha
    ```

1. Optional können Sie bei Bedarf Änderungen am benutzerdefinierten Profil vornehmen. 
1. Beginnen Sie die Clusterbereitstellung mit dem oben erstellten Clusterkonfigurationsprofil.

    ```bash
    azdata bdc create --config-profile custom-aks-ha --accept-eula yes
    ```

## <a name="connect-to-sql-server-databases-in-the-availability-group"></a>Verbinden mit SQL Server-Datenbanken in der Verfügbarkeitsgruppe

Abhängig von der Art der Workload, die Sie für den SQL Server-Master ausführen möchten, können Sie sich entweder mit dem primären Replikat für Lese- bzw. Schreibworkloads oder mit den Datenbanken in den sekundären Replikaten für schreibgeschützte Workloads verbinden. Hier ist eine Übersicht über die verschiedenen Verbindungstypen:

### <a name="connect-to-databases-on-the-primary-replica"></a>Verbinden mit Datenbanken im primären Replikat

Verwenden Sie für Verbindungen mit dem primären Replikat den Endpunkt `sql-server-master`. Dieser Endpunkt ist auch der Listener für die Verfügbarkeitsgruppe. Bei Verwendung dieses Endpunkts stehen alle Verbindungen im Kontext von Datenbanken innerhalb der Verfügbarkeitsgruppe. Eine Standardverbindung mit diesem Endpunkt führt beispielsweise dazu, dass eine Verbindung mit der `master`-Datenbank innerhalb der Verfügbarkeitsgruppe und nicht mit der `master`-Datenbank der SQL Server-Instanz hergestellt wird. Führen Sie diesen Befehl aus, um nach dem Endpunkt zu suchen:

```bash
azdata bdc endpoint list -e sql-server-master -o table
```

```
Description                           Endpoint             Name               Protocol
------------------------------------  -------------------  -----------------  ----------
SQL Server Master Instance Front-End  11.11.111.111,11111  sql-server-master  tds
```

> [!NOTE]
> Failoverereignisse können während der Ausführung einer verteilten Abfrage auftreten, die auf Daten aus Remotedatenquellen wie einem HDFS oder Datenpool zugreift. Es ist eine bewährte Methode, Anwendungen so zu konzipieren, dass sie über eine Wiederholungslogik für den Fall von Verbindungsabbrüchen durch Failover verfügen.  
>

### <a name="connect-to-databases-on-the-secondary-replicas"></a>Verbinden mit Datenbanken in den sekundären Replikaten

Für schreibgeschützte Verbindungen mit Datenbanken in sekundären Replikaten verwenden Sie den Endpunkt `sql-server-master-readonly`. Dieser Endpunkt verhält sich wie ein Lastenausgleich über alle sekundären Replikate hinweg.  Bei Verwendung dieses Endpunkts stehen alle Verbindungen im Kontext von Datenbanken innerhalb der Verfügbarkeitsgruppe. Eine Standardverbindung mit diesem Endpunkt führt beispielsweise dazu, dass eine Verbindung mit der `master`-Datenbank innerhalb der Verfügbarkeitsgruppe und nicht mit der `master`-Datenbank der SQL Server-Instanz hergestellt wird. 

```bash
azdata bdc endpoint list -e sql-server-master-readonly -o table
```

```
Description                                    Endpoint            Name                        Protocol
---------------------------------------------  ------------------  --------------------------  ----------
SQL Server Master Readable Secondary Replicas  11.11.111.11,11111  sql-server-master-readonly  tds
```

## <a name="connect-to-sql-server-instance"></a><a id="instance-connect"></a> Verbinden mit einer SQL Server-Instanz

Für bestimmte Vorgänge, wie das Festlegen von Konfigurationen auf Serverebene oder das manuelle Hinzufügen einer Datenbank zur Verfügbarkeitsgruppe, müssen Sie eine Verbindung mit der SQL Server-Instanz herstellen. Vor SQL Server 2019 CU2 erforderten Vorgänge wie `sp_configure`, `RESTORE DATABASE` oder alle Verfügbarkeitsgruppen-DDLs diese Art von Verbindung. Standardmäßig enthält ein Big Data-Cluster keinen Endpunkt, der eine Instanzverbindung ermöglicht, und Sie müssen diesen Endpunkt manuell verfügbar machen. 

> [!IMPORTANT]
> Der für SQL Server-Instanzverbindungen verfügbar gemachte Endpunkt unterstützt nur die SQL-Authentifizierung, selbst in Clustern, in denen Active Directory aktiviert ist. Standardmäßig ist bei einer Big Data-Clusterbereitstellung die `sa`-Anmeldung deaktiviert und eine neue `sysadmin`-Anmeldung wird basierend auf den Werten bereitgestellt, die zum Zeitpunkt der Bereitstellung für `AZDATA_USERNAME` und `AZDATA_PASSWORD` Umgebungsvariablen bereitgestellt werden.

> [!IMPORTANT]
> Die enthaltene Verfügbarkeitsgruppen-DDL wird in BDC ausschließlich selbst verwaltet. Jeder Versuch (externer Benutzer), die enthaltene Verfügbarkeitsgruppe oder den Datenbankspiegelungs-Endpunkt zu löschen, wird nicht unterstützt und kann zu einem nicht wiederherstellbaren BDC-Status führen.

Das folgende Beispiel zeigt, wie Sie diesen Endpunkt verfügbar machen und dann die Datenbank, die mit einem Wiederherstellungsworkflow erstellt wurde, zur Verfügbarkeitsgruppe hinzufügen können. Es gelten ähnliche Anweisungen zum Einrichten einer Verbindung mit der SQL Server-Masterinstanz, wenn Sie Serverkonfigurationen mit `sp_configure` ändern möchten.

> [!NOTE]
> Ab SQL Server 2019 CU2 werden Datenbanken, die aufgrund eines Wiederherstellungsworkflows erstellt wurden, automatisch zur enthaltenen Verfügbarkeitsgruppe hinzugefügt.

- Bestimmen Sie den Pod, der das primäre Replikat hostet, indem Sie eine Verbindung mit dem `sql-server-master`-Endpunkt herstellen und Folgendes ausführen:

    ```sql
    SELECT @@SERVERNAME
   ```

- Machen Sie den externen Endpunkt verfügbar, indem Sie einen neuen Kubernetes-Dienst erstellen.

    Führen Sie für einen `kubeadm`-Cluster den folgenden Befehl aus. Ersetzen Sie `podName` durch den Namen des im vorherigen Schritt zurückgegebenen Servers, `serviceName` durch den bevorzugten Namen für den erstellten Kubernetes-Dienst und `namespaceName`* durch den Namen Ihres BDC-Clusters.

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=NodePort
    ```

    Führen Sie für einen AKS-Cluster den gleichen Befehl aus, mit dem Unterschied, dass der Typ des erstellten Diensts dabei `LoadBalancer` ist. Beispiel: 

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=LoadBalancer
    ```

    Nachfolgend finden Sie ein Beispiel für diesen Befehl, der für AKS ausgeführt wird, wobei `master-0` der Pod ist, der das primäre Replikat hostet:

    ```bash
    kubectl -n mssql-cluster expose pod master-0 --port=1533  --name=master-sql-0 --type=LoadBalancer
    ```

    Rufen Sie die IP-Adresse des erstellten Kubernetes-Diensts ab:

    ```bash
    kubectl get services -n <namespaceName>
    ```

> [!IMPORTANT]
> Als bewährte Methode sollten Sie den oben erstellten Kubernetes-Dienst löschen, indem Sie diesen Befehl ausführen:
>
>```bash
>kubectl delete svc master-sql-0 -n mssql-cluster
>```

- Fügen Sie die Datenbank der Verfügbarkeitsgruppe hinzu.

    Damit die Datenbank der Verfügbarkeitsgruppe hinzugefügt werden kann, muss Sie im vollständigen Wiederherstellungsmodus ausgeführt werden, und es muss eine Protokollsicherung durchgeführt werden. Verwenden Sie die IP-Adresse des oben erstellten Kubernetes-Diensts, und stellen Sie eine Verbindung mit der SQL Server-Instanz her. Führen Sie dann wie unten gezeigt die TSQL-Anweisungen aus.

    ```sql
    ALTER DATABASE <databaseName> SET RECOVERY FULL;
    BACKUP DATABASE <databaseName> TO DISK='<filePath>'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE <databaseName>
    ```

    Im folgenden Beispiel wird die Datenbank `sales` hinzugefügt, die auf der Instanz wiederhergestellt wurde:

    ```sql
    ALTER DATABASE sales SET RECOVERY FULL;
    BACKUP DATABASE sales TO DISK='/var/opt/mssql/data/sales.bak'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE sales
    ```

## <a name="known-limitations"></a>Bekannte Einschränkungen

Bekannte Probleme und Einschränkungen bei eigenständigen Verfügbarkeitsgruppen für SQL Server-Masterinstanzen in einem Big Data-Cluster sind:

- Die Konfiguration für Hochverfügbarkeit muss erstellt werden, sobald ein Big Data-Cluster bereitgestellt wird. Nach der Bereitstellung kann die Konfiguration für Hochverfügbarkeit mit Verfügbarkeitsgruppen nicht mehr aktiviert werden. Zurzeit ist nur die Konfiguration für Replikate mit synchronem Commit aktiviert.

> [!WARNING]
> Wenn Sie den Synchronisierungsmodus auf einen asynchronen Commit für eines der Replikate im Quorumcommit aktualisieren, führt dies zu einer ungültigen Konfiguration für Hochverfügbarkeit. Das Ausführen in dieser Konfiguration ist mit einem Datenverlustrisiko verbunden, da bei Fehlerereignissen, die das primäre Replikat betreffen, kein automatisches Failover ausgelöst wird und der Benutzer beim Auslösen eines manuellen Failovers das Datenverlustrisiko akzeptieren muss.

- Sie müssen sicherstellen, dass die [erforderlichen Zertifikate](../relational-databases/security/encryption/move-a-tde-protected-database-to-another-sql-server.md) sowohl in der SQL Server-Masterinstanz als auch in der enthaltenen Verfügbarkeitsgruppen-Masterinstanz wiederhergestellt werden, um eine TDE-fähige Datenbank erfolgreich über eine Sicherung wiederherzustellen, die auf einem anderen Server erstellt wurde. [Hier](https://www.sqlshack.com/restoring-transparent-data-encryption-tde-enabled-databases-on-a-different-server/) finden Sie ein Beispiel zur Sicherung und Wiederherstellung der Zertifikate.
- Für bestimmte Vorgänge wie das Ausführen von Serverkonfigurationseinstellungen mit `sp_configure` ist eine Verbindung mit der `master`-Datenbank der SQL Server-Instanz erforderlich, nicht mit der Verfügbarkeitsgruppe `master`. Der entsprechende primäre Endpunkt kann nicht verwendet werden. Befolgen Sie die [Anweisungen](#instance-connect), um einen Endpunkt verfügbar zu machen, eine Verbindung mit der SQL Server-Instanz herzustellen und `sp_configure` auszuführen. Sie können die SQL-Authentifizierung nur verwenden, wenn Sie den Endpunkt manuell verfügbar machen, um eine Verbindung mit der `master`-Datenbank der SQL Server-Instanz herzustellen.
- Obwohl die enthaltene msdb-Datenbank in der Verfügbarkeitsgruppe enthalten ist und die SQL-Agent-Aufträge darin repliziert werden, werden die Aufträge nur auf dem primären Replikat nach Zeitplan ausgeführt.
- Datenbanken, die vor SQL Server 2019 CU2 aufgrund von anderen Workflows als `CREATE DATABASE` und `RESTORE DATABASE`, z. B. `CREATE DATABASE FROM SNAPSHOT`, erstellt wurden, werden nicht automatisch zur Verfügbarkeitsgruppe hinzugefügt. [Stellen Sie eine Verbindung mit der Instanz her](#instance-connect), und fügen Sie die Datenbank manuell zur Verfügbarkeitsgruppe hinzu.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zum Verwenden von Konfigurationsdateien in Big Data-Clusterbereitstellungen finden Sie unter [Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in Kubernetes](deployment-guidance.md#configfile).
- Weitere Informationen zum Verfügbarkeitsgruppen-Feature für SQL Server finden Sie unter [Übersicht über Always On-Verfügbarkeitsgruppen (SQL Server)](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).
