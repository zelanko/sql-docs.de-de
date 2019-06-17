---
title: Configure SQL Server AlwaysOn-Verfügbarkeitsgruppe für hochverfügbarkeit bei Linux
titleSuffix: SQL Server
description: Informationen Sie zum Erstellen einer SQL Server immer auf Availability Group (AG) für hohe Verfügbarkeit unter Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: e339d83503c8fa1f5cdd383004fa93d41529d12d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713436"
---
# <a name="configure-sql-server-always-on-availability-group-for-high-availability-on-linux"></a>Configure SQL Server AlwaysOn-Verfügbarkeitsgruppe für hochverfügbarkeit bei Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt, wie Sie eine SQL Server immer auf Availability Group (AG) für hohe Verfügbarkeit unter Linux zu erstellen. Es gibt zwei Arten von Konfiguration für Verfügbarkeitsgruppen. Ein *hochverfügbarkeit* Konfiguration verwendet einen Cluster-Manager, um die Geschäftskontinuität bereitzustellen. Diese Konfiguration kann auch schreibgeschützte Replikate enthalten. Dieses Dokument erläutert, wie Sie die Verfügbarkeitsgruppe für hohe Verfügbarkeit zu erstellen.

Sie können auch erstellen eine Verfügbarkeitsgruppe ohne einen Cluster-Manager für *leseskalierung*. Die Verfügbarkeitsgruppe für die leseskalierung stellt nur schreibgeschützten Replikaten für Leistung horizontale Skalierung bereit. Es bietet keine hohen Verfügbarkeit. Um eine Verfügbarkeitsgruppe für schreibgeschützte horizontale Skalierung zu erstellen, finden Sie unter [konfigurieren Sie eine SQL Server-Verfügbarkeitsgruppe für schreibgeschützte horizontale Skalierung unter Linux](sql-server-linux-availability-group-configure-rs.md).

Konfigurationen, die hohe Verfügbarkeit und Datenschutz zu gewährleisten müssen zwei oder drei synchrone Replikate übernehmen. Mit drei synchronen Replikaten kann die Verfügbarkeitsgruppe automatisch wiederhergestellt, auch wenn ein Server nicht verfügbar ist. Weitere Informationen finden Sie unter [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md). 

Alle Server müssen entweder physisch oder virtuell sein, und virtuelle Server muss auf die gleiche Virtualisierungsplattform. Diese Anforderung ist, da die Agents Umgrenzung plattformspezifisch sind. Finden Sie unter [Richtlinien für Gastcluster](https://access.redhat.com/articles/29440#guest_policies).

## <a name="roadmap"></a>Roadmap

Die Schritte zum Erstellen einer Verfügbarkeitsgruppe auf Linux-Servern für hochverfügbarkeit unterscheiden sich von den Schritten in einem Windows Server-Failovercluster. Die folgende Liste beschreibt die allgemeinen Schritte: 

1. [Konfigurieren von SQL Server auf drei Clusterservern](sql-server-linux-setup.md).

   >[!IMPORTANT]
   >Alle drei Server in der Verfügbarkeitsgruppe müssen auf der gleichen Plattform – physisch oder virtuell – sein, da hoher Verfügbarkeit von Linux umgrenzungs-Agents verwendet, um die Ressourcen auf den Servern zu isolieren. Die Umgrenzung-Agents sind spezifisch für jede Plattform.

2. Erstellen Sie die Verfügbarkeitsgruppe. Dieser Schritt wird in diesem aktuellen Artikel behandelt. 

3. Konfigurieren Sie eine Clusterressourcen-Manager, z.B. Pacemaker.
   
   Die Möglichkeit, einen Cluster-Ressourcen-Manager zu konfigurieren, hängt von der jeweilige Linux-Distribution. Finden Sie unter folgenden Links, um spezifische Anweisungen Verteilung: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >Produktionsumgebungen sind erforderlich, einen umgrenzungs-Agent, wie STONITH für hohe Verfügbarkeit. Die Demos in dieser Dokumentation verwenden keine Umgrenzung-Agents. Die Demos sind für Tests und Überprüfung nur auf. 
   
   >Ein Linux-Cluster verwendet Umgrenzung, um den Cluster in einen bekannten Zustand zurückzugeben. Die Möglichkeit zum Konfigurieren der Umgrenzung hängt davon ab, die Verteilung und der Umgebung. Umgrenzung ist derzeit nicht in eine Cloud-Umgebungen verfügbar. Weitere Informationen finden Sie unter [Supportrichtlinien für RHEL High Availability Cluster - Virtualisierungsplattformen](https://access.redhat.com/articles/29440).
   
   >SLES, finden Sie unter [SUSE Linux Enterprise-Erweiterung für hohe Verfügbarkeit](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. Fügen Sie der Verfügbarkeitsgruppe als Ressource im Cluster hinzu.  

   Die Möglichkeit, die Verfügbarkeitsgruppe als Ressource im Cluster hinzufügen, hängt von der Linux-Distribution. Finden Sie unter folgenden Links, um spezifische Anweisungen Verteilung: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Erstellen der Verfügbarkeitsgruppe

In die Beispielen in diesem Abschnitt wird erläutert, wie die verfügbarkeitsgruppe mit Transact-SQL zu erstellen. Sie können auch den SQL Server Management Studio Assistenten für Verfügbarkeitsgruppen verwenden. Wenn Sie eine Verfügbarkeitsgruppe mit dem Assistenten zum Erstellen, gibt es einen Fehler zurück, wenn Sie die Replikate der Verfügbarkeitsgruppe hinzufügen. Um dieses Problem zu beheben, gewähren `ALTER`, `CONTROL`, und `VIEW DEFINITIONS` auf den Pacemaker unter der Verfügbarkeitsgruppe auf allen Replikaten. Nachdem Sie auf dem primären Replikat Berechtigungen gewährt werden, fügen Sie die Knoten an die Verfügbarkeitsgruppe mithilfe des Assistenten, jedoch für hohe Verfügbarkeit funktioniert ordnungsgemäß, erteilen Sie Berechtigung auf allen Replikaten.

Für eine Konfiguration mit hoher Verfügbarkeit, die automatische Failover wird sichergestellt, ist die Verfügbarkeitsgruppe über mindestens drei Replikate erforderlich. Eine der folgenden Konfigurationen kann es sich um hohe Verfügbarkeit unterstützen:

- [Drei synchroner Replikate](sql-server-linux-availability-group-ha.md#threeSynch)

- [Zwei synchronen Replikaten sowie ein Replikat für die Konfiguration](sql-server-linux-availability-group-ha.md#twoSynch)

Weitere Informationen finden Sie unter [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md).

>[!NOTE]
>Die Verfügbarkeitsgruppen können zusätzliche synchrone oder asynchrone Replikate enthalten. 

Erstellen der Verfügbarkeitsgruppe für hochverfügbarkeit unter Linux. Verwenden der [CREATE AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/create-availability-group-transact-sql) mit `CLUSTER_TYPE = EXTERNAL`. 

* Verfügbarkeitsgruppe – `CLUSTER_TYPE = EXTERNAL` gibt an, dass eine externe clusterentität die Verfügbarkeitsgruppe verwaltet. Pacemaker ist ein Beispiel für eine externe clusterentität. Wenn der Clustertyp der Verfügbarkeitsgruppe, die extern ist, 

* Legen Sie die primären und sekundäre Replikaten `FAILOVER_MODE = EXTERNAL`. 
   Gibt an, dass das Replikat mit einem externen Cluster-Manager, z.B. Pacemaker interagiert. 

Die folgende Transact-SQL-Skripts erstellen Sie eine Verfügbarkeitsgruppe für hochverfügbarkeit, die mit dem Namen `ag1`. Das Skript konfiguriert die Verfügbarkeitsgruppenreplikate mit `SEEDING_MODE = AUTOMATIC`. Diese Einstellung bewirkt, dass SQL Server, um die Datenbank automatisch auf jedem sekundären Server zu erstellen. Aktualisieren Sie das folgende Skript für Ihre Umgebung. Ersetzen Sie die `<node1>`, `<node2>`, oder `<node3>` Werte mit den Namen der SQL Server-Instanzen, die die Replikate hosten. Ersetzen Sie die `<5022>` mit dem Port, den Sie für die datenbankspiegelungs-Endpunkt Daten festlegen. Um die Verfügbarkeitsgruppe zu erstellen, führen Sie die folgende Transact-SQL für SQL Server-Instanz, die das primäre Replikat hostet.

Führen Sie **nur eine** der folgenden Skripts aus: 

- [Erstellen einer Verfügbarkeitsgruppe mit drei synchronen Replikaten](#threeSynch).
- [Erstellen einer Verfügbarkeitsgruppe mit zwei synchronen Replikaten und einem Replikat für die Konfiguration](#configOnly)
- [Erstellen einer Verfügbarkeitsgruppe mit zwei synchronen Replikaten](#readScale).

<a name="threeSynch"></a>

- Erstellen der Verfügbarkeitsgruppe mit drei synchronen Replikaten

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
       WITH (DB_FAILOVER = ON, CLUSTER_TYPE = EXTERNAL)
       FOR REPLICA ON
           N'<node1>' 
            WITH (
               ENDPOINT_URL = N'tcp://<node1>:<5022>',
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'<node2>' 
            WITH ( 
               ENDPOINT_URL = N'tcp://<node2>:<5022>', 
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'<node3>'
           WITH( 
              ENDPOINT_URL = N'tcp://<node3>:<5022>', 
              AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
              FAILOVER_MODE = EXTERNAL,
              SEEDING_MODE = AUTOMATIC
              );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```

   >[!IMPORTANT]
   >Führen Sie nach der Ausführung des vorherigen Skripts, um eine Verfügbarkeitsgruppe mit drei synchronen Replikaten erstellen nicht das folgende Skript aus:

<a name="configOnly"></a>
- Verfügbarkeitsgruppe mit zwei synchronen Replikaten und einem Replikat für die Konfiguration zu erstellen:

   >[!IMPORTANT]
   >Diese Architektur ermöglicht es, eine beliebige Edition von SQL Server, um das dritte Replikat gehostet wird. Das dritte Replikat kann z. B. in SQL Server Enterprise Edition gehostet werden. Für die Enterprise Edition, ist der einzige gültige Endpunkttyp `WITNESS`. 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1] 
      WITH (CLUSTER_TYPE = EXTERNAL) 
      FOR REPLICA ON 
       N'<node1>' WITH ( 
          ENDPOINT_URL = N'tcp://<node1>:<5022>', 
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'<node2>' WITH (  
          ENDPOINT_URL = N'tcp://<node2>:<5022>',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'<node3>' WITH ( 
          ENDPOINT_URL = N'tcp://<node3>:<5022>', 
          AVAILABILITY_MODE = CONFIGURATION_ONLY  
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```
<a name="readScale"></a>

- Erstellen der Verfügbarkeitsgruppe mit zwei synchronen Replikaten

   Zwei Replikate mit den Verfügbarkeitsmodus für synchrone einschließen. Das folgende Skript erstellt z. B. eine Verfügbarkeitsgruppe namens `ag1`. `node1` und `node2` Hosten der Replikate im synchronen Modus mit automatischem seeding und automatischem Failover.

   >[!IMPORTANT]
   >Führen Sie nur das folgende Skript zum Erstellen einer Verfügbarkeitsgruppe mit zwei synchronen Replikaten. Das folgende Skript kann nicht ausgeführt werden, wenn Sie die beiden vorhergehenden Skript ausgeführt haben. 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
      N'node1' WITH (
         ENDPOINT_URL = N'tcp://node1:5022',
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      ),
      N'node2' WITH ( 
         ENDPOINT_URL = N'tcp://node2:5022', 
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```


Sie können auch konfigurieren, eine Verfügbarkeitsgruppe mit `CLUSTER_TYPE=EXTERNAL` mit SQL Server Management Studio oder PowerShell. 

### <a name="join-secondary-replicas-to-the-ag"></a>Verknüpfen Sie sekundärer Replikate mit der Verfügbarkeitsgruppe

Der Pacemaker-Benutzer benötigt `ALTER`, `CONTROL`, und `VIEW DEFINITION` Berechtigungen für die verfügbarkeitsgruppe auf allen Replikaten. Zum Gewähren von Berechtigungen führen Sie das folgende Transact-SQL-Skript, nachdem die verfügbarkeitsgruppe auf dem primären Replikat und jedem sekundären Replikat erstellt wird, sobald sie mit der verfügbarkeitsgruppe hinzugefügt werden. Ersetzen Sie vor dem Ausführen des Skripts `<pacemakerLogin>` mit dem Namen des Benutzerkontos Pacemaker.

```Transact-SQL
GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO <pacemakerLogin>
GRANT VIEW SERVER STATE TO <pacemakerLogin>
```

Die folgende Transact-SQL-Skript verknüpft eine SQL Server-Instanz zu einer Verfügbarkeitsgruppe mit dem Namen `ag1`. Aktualisieren Sie das Skript für Ihre Umgebung. Führen Sie die folgende Transact-SQL, um die Verfügbarkeitsgruppe zu verknüpfen, auf jeder SQL Server-Instanz, die ein sekundäres Replikat hostet.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>Nachdem Sie die Verfügbarkeitsgruppe erstellt haben, müssen Sie die Integration mit einer Clustertechnologie wie Pacemaker für hohe Verfügbarkeit konfigurieren. Für eine schreibgeschützte-Konfiguration mithilfe von Verfügbarkeitsgruppen, beginnend mit [!INCLUDE [SQL Server version](../includes/sssqlv14-md.md)], Einrichten eines Clusters ist nicht erforderlich.

Wenn Sie die in diesem Dokument beschriebenen Schritte ausführen, müssen Sie eine Verfügbarkeitsgruppe, die noch nicht gruppiert ist. Der nächste Schritt ist, um den Cluster hinzuzufügen. Diese Konfiguration ist für Read leseskalierung/zum Lastenausgleich Szenarien gültig, es ist nicht vollständig für hohe Verfügbarkeit. Für hohe Verfügbarkeit müssen Sie die Verfügbarkeitsgruppe als Clusterressource hinzufügen. Finden Sie unter [nächste Schritte](#next-steps) Anweisungen. 

## <a name="notes"></a>Hinweise

>[!IMPORTANT]
>Nachdem Sie den Cluster konfigurieren, und fügen Sie die Verfügbarkeitsgruppe als Clusterressource, keine Transact-SQL ein Failover der Verfügbarkeitsgruppe-Ressourcen können. Ressourcen für SQL Server-Clusters unter Linux sind nicht so eng mit dem Betriebssystem verknüpft, wie sie auf einem Windows Server Failover Cluster (WSFC) sind. SQL Server-Dienst ist nicht über das Vorhandensein des Clusters. Alle Orchestrierung erfolgt über die Verwaltungstools. In RHEL oder Ubuntu verwenden `pcs`. Verwenden Sie SLES `crm`. 

>[!IMPORTANT]
>Wenn die Verfügbarkeitsgruppe eine Clusterressource ist, besteht ein bekanntes Problem in der aktuellen Version, in denen erzwungenes Failover mit Datenverlust, ein asynchrones Replikat nicht funktioniert. Dies wird in der bevorstehenden Version behoben. Manuelle oder automatische Failover auf ein synchrones Replikat ist erfolgreich.


## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von Red Hat Enterprise Linux-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-rhel.md)

[Konfigurieren von SUSE Linux Enterprise Server-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-sles.md)

[Konfigurieren Sie Ubuntu-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-ubuntu.md)
