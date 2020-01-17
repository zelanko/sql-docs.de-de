---
title: Konfigurieren verteilter Verfügbarkeitsgruppen
description: 'In diesem Thema wird beschrieben, wie Sie eine verteilte Always On-Verfügbarkeitsgruppe erstellen und konfigurieren. '
ms.custom: seodec18
ms.date: 08/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c54ec57756ca2f840ac3f15771143cf697798e9f
ms.sourcegitcommit: 56fb0b7750ad5967f5d8e43d87922dfa67b2deac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2019
ms.locfileid: "75002041"
---
# <a name="configure-an-always-on-distributed-availability-group"></a>Konfigurieren verteilter Always On-Verfügbarkeitsgruppen  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Sie müssen zwei Verfügbarkeitsgruppen mit eigenen Listenern erstellen, um eine verteilte Verfügbarkeitsgruppe zu erstellen. Anschließend kombinieren Sie diese Verfügbarkeitsgruppen zu einer verteilten Verfügbarkeitsgruppe. Die folgenden Schritte stellen ein einfaches Beispiel in Transact-SQL dar. Dieses Beispiel deckt nicht alle Details zum Erstellen von Verfügbarkeitsgruppen und Listenern ab, stattdessen legt es den Schwerpunkt auf die Herausarbeitung der wichtigsten Anforderungen.

Eine technische Übersicht über verteilte Verfügbarkeitsgruppen finden Sie unter [Verteilte Verfügbarkeitsgruppen](distributed-availability-groups.md).

## <a name="prerequisites"></a>Voraussetzungen

### <a name="set-the-endpoint-listeners-to-listen-to-all-ip-addresses"></a>Festlegen der Endpunktlistener zur Überwachung aller IP-Adressen

Stellen Sie sicher, dass die Endpunkte zwischen den verschiedenen Verfügbarkeitsgruppen in der verteilten Verfügbarkeitsgruppe kommunizieren können. Wenn eine Verfügbarkeitsgruppe für ein bestimmtes Netzwerk auf den Endpunkt festgelegt ist, funktioniert die verteilte Verfügbarkeitsgruppe nicht richtig. Konfigurieren Sie den Listener aller Server, die ein Replikat in der verteilten Verfügbarkeitsgruppe hosten, so, dass er auf alle IP-Adressen lauscht (`LISTENER_IP = ALL`).

#### <a name="create-a-listener-to-listen-to-all-ip-addresses"></a>Erstellen eines Listeners zur Überwachung aller IP-Adressen

Das folgende Skript erstellt z.B. einen Listenerendpunkt auf TCP-Port 5022, der alle IP-Adressen überwacht.  

```sql
CREATE ENDPOINT [aodns-hadr] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
FOR DATA_MIRRORING (
   ROLE = ALL, 
   AUTHENTICATION = WINDOWS NEGOTIATE,
   ENCRYPTION = REQUIRED ALGORITHM AES
)
GO
```

#### <a name="alter-a-listener-to-listen-to-all-ip-addresses"></a>Ändern eines Listeners zur Überwachung aller IP-Adressen

Das folgende Skript ändert z.B. einen Listenerendpunkt so, dass er alle IP-Adressen überwacht.  

```sql
ALTER ENDPOINT [aodns-hadr] 
    AS TCP (LISTENER_IP = ALL)
GO
```

## <a name="create-first-availability-group"></a>Erstellen der ersten Verfügbarkeitsgruppe

### <a name="create-the-primary-availability-group-on-the-first-cluster"></a>Erstellen der ersten Verfügbarkeitsgruppe auf dem ersten Cluster  
Erstellen Sie eine Verfügbarkeitsgruppe für den ersten Windows Server-Failovercluster (WSFC).   In diesem Beispiel heißt die Verfügbarkeitsgruppe `ag1` für die Datenbank `db1`. Das primäre Replikat der primären Verfügbarkeitsgruppe wird in einer verteilten Verfügbarkeitsgruppe als **globales primäres Replikat** bezeichnet. Server1 ist in diesem Beispiel das primäre Replikat.        
  
```sql  
CREATE AVAILABILITY GROUP [ag1]   
FOR DATABASE db1   
REPLICA ON N'server1' WITH (ENDPOINT_URL = N'TCP://server1.contoso.com:5022',  
    FAILOVER_MODE = AUTOMATIC,  
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server2' WITH (ENDPOINT_URL = N'TCP://server2.contoso.com:5022',   
    FAILOVER_MODE = AUTOMATIC,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
  
```  
  
>[!NOTE]
>Im vorherigen Beispiel wird automatisches Seeding verwendet, wobei **SEEDING_MODE** sowohl für die Replikate als auch für die verteilte Verfügbarkeitsgruppe auf **AUTOMATIC** festgelegt ist. Diese Konfiguration legt fest, dass die sekundären Replikate und sekundären Verfügbarkeitsgruppen automatisch aufgefüllt werden, ohne eine manuelle Sicherung und Wiederherstellung der primären Datenbank erforderlich zu machen.  
  
### <a name="join-the-secondary-replicas-to-the-primary-availability-group"></a>Verknüpfen der sekundären Replikate mit der primären Verfügbarkeitsgruppe  
Alle sekundären Replikate müssen mithilfe von **ALTER AVAILABILITY GROUP** mit der Option **JOIN** mit der Verfügbarkeitsgruppe verknüpft werden. Da in diesem Beispiel automatisches Seeding verwendet wird, müssen Sie außerdem **ALTER AVAILABILITY GROUP** mit der Option **GRANT CREATE ANY DATABASE** aufrufen. Diese Einstellung ermöglicht der Verfügbarkeitsgruppe, die Datenbank zu erstellen und mit dem automatischen Seeding aus dem ersten Replikat zu beginnen.  
  
In diesem Beispiel werden die folgenden Befehle auf dem sekundären Replikat `server2`ausgeführt, um die Verknüpfung mit der Verfügbarkeitsgruppe `ag1` herzustellen. Der Verfügbarkeitsgruppe ist es damit gestattet, Datenbanken auf dem sekundären Replikat zu erstellen.  
  
```sql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  

>[!NOTE]
>Wenn die Verfügbarkeitsgruppe eine Datenbank auf einem sekundären Replikat erstellt, legt sie als Datenbankbesitzer das Konto fest, das die Anweisung `ALTER AVAILABILITY GROUP` ausgeführt hat, um die Berechtigung zum Erstellen von Datenbanken zu erteilen. Ausführliche Informationen finden Sie unter [Grant create database permission on secondary replica to availability group (Erteilen der Berechtigung zum Erstellen von Datenbanken auf dem sekundären Replikat von Verfügbarkeitsgruppen)](automatic-seeding-secondary-replicas.md#grantCreate).
  
### <a name="create-a-listener-for-the-primary-availability-group"></a>Erstellen eines Listeners für die primäre Verfügbarkeitsgruppe  

Fügen Sie im nächsten Schritt einen Listener für die primäre Verfügbarkeitsgruppe auf dem ersten WSFC hinzu. In diesem Beispiel hat der Listener den Namen `ag1-listener`. Weitere Informationen zum Erstellen eines Listeners finden Sie unter [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server &#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```sql
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( 
        WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , 
        PORT = 60173);    
GO  
```  
  

## <a name="create-second-availability-group"></a>Erstellen der zweiten Verfügbarkeitsgruppe  
 Erstellen Sie anschließend auf dem zweiten WSFC eine zweite Verfügbarkeitsgruppe, `ag2`. Die Datenbank wird in diesem Fall nicht angegeben, da sie automatisch per Seeding aus der primären Verfügbarkeitsgruppe aufgefüllt wird.  Das primäre Replikat der sekundären Verfügbarkeitsgruppe wird in einer verteilten Verfügbarkeitsgruppe als **Weiterleitung** bezeichnet. In diesem Beispiel ist Server3 die Weiterleitung. 
  
```sql  
CREATE AVAILABILITY GROUP [ag2]   
FOR   
REPLICA ON N'server3' WITH (ENDPOINT_URL = N'TCP://server3.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server4' WITH (ENDPOINT_URL = N'TCP://server4.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
```  
  
> [!NOTE]  
> Die sekundäre Verfügbarkeitsgruppe muss denselben Endpunkt für die Datenbankspiegelung verwenden (in diesem Beispiel Port 5022). Andernfalls wird die Replikation nach einem lokalen Failover beendet.  
  
### <a name="join-the-secondary-replicas-to-the-secondary-availability-group"></a>Verknüpfen der sekundären Replikate mit der sekundären Verfügbarkeitsgruppe  
 In diesem Beispiel werden die folgenden Befehle auf dem sekundären Replikat `server4`ausgeführt, um die Verknüpfung mit der Verfügbarkeitsgruppe `ag2` herzustellen. Der Verfügbarkeitsgruppe wird dann erlaubt, Datenbanken auf dem sekundären Replikat zu erstellen, um das automatische Seeding zu unterstützen.  
  
```sql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### <a name="create-a-listener-for--the-secondary-availability-group"></a>Erstellen eines Listeners für die sekundäre Verfügbarkeitsgruppe  
 Fügen Sie im nächsten Schritt einen Listener für die sekundäre Verfügbarkeitsgruppe auf dem zweiten WSFC hinzu. In diesem Beispiel hat der Listener den Namen `ag2-listener`. Weitere Informationen zum Erstellen eines Listeners finden Sie unter [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server &#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
## <a name="create-distributed-availability-group-on-first-cluster"></a>Erstellen einer verteilten Verfügbarkeitsgruppe auf dem ersten Cluster  
 Erstellen Sie auf dem ersten WSFC eine verteilte Verfügbarkeitsgruppe (die in diesem Beispiel den Namen `distributedag` trägt). Verwenden Sie den **CREATE AVAILABILITY GROUP** -Befehl mit der **DISTRIBUTED** -Option. Der **AVAILABILITY GROUP ON**-Parameter gibt die Memberverfügbarkeitsgruppen `ag1` und `ag2` an.  
  
```sql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  Die **LISTENER_URL** gibt den Listener für jede Verfügbarkeitsgruppe zusammen mit dem Datenbankspiegelungs-Endpunkt der Verfügbarkeitsgruppe an. In diesem Beispiel ist das Port `5022` (nicht Port `60173` , der zum Erstellen des Listeners verwendet wurde). Wenn Sie beispielsweise in Azure einen Lastenausgleich verwenden, [fügen Sie eine Regel für den Lastenausgleich für den Port der verteilten Verfügbarkeitsgruppe hinzu](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-alwayson-int-listener#add-load-balancing-rule-for-distributed-availability-group). Fügen Sie zusätzlich zum SQL Server-Instanzport die Regel für den Listenerport hinzu. 

### <a name="cancel-automatic-seeding-to-forwarder"></a>Abbrechen des automatischen Seedings für die Weiterleitung
Falls es erforderlich ist, die Initialisierung der Weiterleitung abzubrechen, bevor die zwei Verfügbarkeitsgruppen synchronisiert werden, ändern Sie die verteilte Verfügbarkeitsgruppe mit ALTER, indem Sie den SEEDING_MODE-Parameter der Weiterleitung auf MANUAL festlegen und das Seeding sofort abbrechen. Führen Sie den Befehl für die globale primäre Datenbank aus: 

```sql
-- Cancel automatic seeding.  Connect to global primary but specify DAG AG2
ALTER AVAILABILITY GROUP [distributedag]   
   MODIFY  
   AVAILABILITY GROUP ON  
   'ag2' WITH  
   (  SEEDING_MODE = MANUAL  );   
```

  
## <a name="join-distributed-availability-group-on-second-cluster"></a>Verknüpfen der verteilten Verfügbarkeitsgruppe auf dem zweiten Cluster  
 Verknüpfen Sie anschließend die verteilte Veerfügbarkeitsgruppe auf dem zweiten WSFC.  
  
```sql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

## <a name="failover"></a> Verknüpfen der Datenbank auf dem sekundären Replikat der zweiten Verfügbarkeitsgruppe
Nachdem die Datenbank auf dem sekundären Replikat der zweiten Verfügbarkeitsgruppe in einen Wiederherstellungsstatus versetzt wurde, müssen Sie sie manuell mit der Verfügbarkeitsgruppe verknüpfen.

```sql  
ALTER DATABASE [db1] SET HADR AVAILABILITY GROUP = [ag2];   
```
  
## <a name="failover"></a> Failover auf eine sekundäre Verfügbarkeitsgruppe  

Zurzeit wird nur manuelles Failover unterstützt. So führen Sie ein manuelles Failover für eine verteilte Verfügbarkeitsgruppe aus:

1. Legen Sie die verteilte Verfügbarkeitsgruppe auf synchrone Commits fest, um sicherzustellen, dass keine Daten verloren gehen.
1. Warten Sie, bis die verteilte Verfügbarkeitsgruppe synchronisiert wurde.
1. Legen Sie die Rolle der verteilten Verfügbarkeitsgruppe für das globale, primäre Replikat auf `SECONDARY` fest.
1. Testen Sie die Failoverbereitschaft.
1. Führen Sie einen Failover der primären Verfügbarkeitsgruppe aus.

In den folgenden Transact-SQL-Beispielen werden die ausführlichen Schritte zum Ausführen eines Failover für die verteilte Verfügbarkeitsgruppe namens `distributedag` veranschaulicht:

1. Legen Sie die verteilte Verfügbarkeitsgruppe auf einen synchronen Commit fest, indem Sie folgenden Code auf dem globalen primären Replikat *und* der Weiterleitung ausführen.   
    
      ```sql  
      -- sets the distributed availability group to synchronous commit 
       ALTER AVAILABILITY GROUP [distributedag] 
       MODIFY 
       AVAILABILITY GROUP ON
       'ag1' WITH 
        ( 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT 
        ), 
        'ag2' WITH  
        ( 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT 
        );
       
       -- verifies the commit state of the distributed availability group
       select ag.name, ag.is_distributed, ar.replica_server_name, ar.availability_mode_desc, ars.connected_state_desc, ars.role_desc, 
       ars.operational_state_desc, ars.synchronization_health_desc from sys.availability_groups ag  
       join sys.availability_replicas ar on ag.group_id=ar.group_id
       left join sys.dm_hadr_availability_replica_states ars
       on ars.replica_id=ar.replica_id
       where ag.is_distributed=1
       GO

      ```  
   >[!NOTE]
   >In einer verteilten Verfügbarkeitsgruppe hängt der Synchronisierungsstatus der zwei Verfügbarkeitsgruppen vom Verfügbarkeitsmodus beider Replikate ab. Für den synchronen Commitmodus müssen sowohl die aktuell primäre Verfügbarkeitsgruppe als auch die aktuell sekundäre Verfügbarkeitsgruppe den Verfügbarkeitsmodus `SYNCHRONOUS_COMMIT` aufweisen. Aus diesem Grund müssen Sie das obige Skript auf dem globalen primären Replikat und der Weiterleitung ausführen.

1. Warten Sie, bis sich der Status der verteilten Verfügbarkeitsgruppe in `SYNCHRONIZED`geändert hat. Führen Sie die folgende Abfrage auf dem globalen primären Replikat aus, bei dem es sich um das primäre Replikat der primären Verfügbarkeitsgruppe handelt. 
    
      ```sql  
      SELECT ag.name
             , drs.database_id
             , drs.group_id
             , drs.replica_id
             , drs.synchronization_state_desc
             , drs.end_of_log_lsn 
        FROM sys.dm_hadr_database_replica_states drs,
        sys.availability_groups ag
          WHERE drs.group_id = ag.group_id;      
      ```  

    Führen Sie den nächsten Schritt aus, sobald **synchronization_state_desc** für die Verfügbarkeitsgruppe gleich `SYNCHRONIZED`ist. Ist **synchronization_state_desc** nicht gleich `SYNCHRONIZED`, führen Sie den Befehl alle fünf Sekunden aus, bis die Änderung erfolgt ist. Wechseln Sie erst zum nächsten Schritt, wenn **synchronization_state_desc** = `SYNCHRONIZED` ist. 

1. Legen Sie auf dem globalen primären Replikat die Rolle der verteilten Verfügbarkeitsgruppe auf `SECONDARY` fest. 

    ```sql
    ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
    ```  

    Zu diesem Zeitpunkt ist die verteilte Verfügbarkeitsgruppe nicht verfügbar.

1. Testen Sie die Failoverbereitschaft. Führen Sie die folgende Abfrage aus:

    ```sql
    SELECT ag.name, 
        drs.database_id, 
        drs.group_id, 
        drs.replica_id, 
        drs.synchronization_state_desc, 
        drs.end_of_log_lsn 
    FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
    WHERE drs.group_id = ag.group_id; 
    ```  
    Die Verfügbarkeitsgruppe ist für das Failover eingerichtet, wenn **synchronization_state_desc** gleich `SYNCHRONIZED` ist und wenn **end_of_log_lsn** für beide Verfügbarkeitsgruppen identisch ist. 

1. Führen Sie ein Failover von der primären Verfügbarkeitsgruppe auf die sekundäre Verfügbarkeitsgruppe aus. Führen Sie den folgenden Befehl auf dem SQL-Server aus, der das primäre Replikat der sekundären Verfügbarkeitsgruppe hostet. 

    ```sql
    ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
    ```  

    Nach diesem Schritt ist die verteilte Verfügbarkeitsgruppe verfügbar.
      
Nachdem Sie die obigen Schritte ausgeführt haben, erfolgt ein Failover für die verteilte Verfügbarkeitsgruppe ohne Datenverlust. Wenn zwischen den Verfügbarkeitsgruppen eine geografische Entfernung liegt, die Wartezeit verursacht, ändern Sie den Verfügbarkeitsmodus zurück zu „ASYNCHRONOUS_COMMIT“. 
  
## <a name="remove-a-distributed-availability-group"></a>Entfernen einer verteilten Verfügbarkeitsgruppe  
 Die folgende Transact-SQL-Anweisung entfernt eine verteilte Verfügbarkeitsgruppe mit dem Namen `distributedag`:  
  
```sql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## <a name="create-distributed-availability-group-on-failover-cluster-instances"></a>Erstellen einer verteilten Verfügbarkeitsgruppe auf Failoverclusterinstanzen

Sie können eine verteilte Verfügbarkeitsgruppe mit einer Verfügbarkeitsgruppe auf einer Failoverclusterinstanz (FCI) erstellen. In diesem Fall benötigen Sie keinen Verfügbarkeitsgruppenlistener. Verwenden Sie den virtuellen Netzwerknamen (VNN) für das primäre Replikat der FCI-Instanz. Im folgenden Beispiel ist eine verteilte Verfügbarkeitsgruppe namens SQLFCIDAG dargestellt. Eine Verfügbarkeitsgruppe ist SQLFCIAG. SQLFCIAG besitzt zwei FCI-Replikate. Der VNN für das primäre FCI-Replikat ist FCI SQLFCIAG-1, und der VNN für das sekundäre FCI-Replikat ist SQLFCIAG-2. Die verteilte Verfügbarkeitsgruppe enthält außerdem SQLAG-DR zur Wiederherstellung im Notfall.

![Verteilte AlwaysOn-Verfügbarkeitsgruppe](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 Mit der folgenden DDL-Anweisung wird diese verteilte Verfügbarkeitsgruppe erstellt. 

```sql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

Die Listener-URL ist mit dem VNN der primären FCI-Instanz identisch.

## <a name="manually-fail-over-fci-in-distributed-availability-group"></a>Ausführen eines manuellen Failovers für die FCI in der verteilten Verfügbarkeitsgruppe

Um ein manuelles Failover für die FCI-Verfügbarkeitsgruppe auszuführen, aktualisieren Sie die verteilte Verfügbarkeitsgruppe, um die Änderung der Listener-URL zu übernehmen. Führen Sie z. B. folgende DDL-Anweisung sowohl für die primäre als auch die sekundäre Verfügbarkeitsgruppe von SQLFCIAG aus:

```sql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2.contoso.com:5022'
    )
```  
  
## <a name="next-steps"></a>Nächste Schritte

 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
