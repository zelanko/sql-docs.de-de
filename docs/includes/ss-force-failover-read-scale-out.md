---
title: 'SQL Server: Erzwingen eines Failovers für Verfügbarkeitsgruppen'
description: Erzwingen eines Failovers für Verfügbarkeitsgruppen mit dem Clustertyp „NONE“
services: ''
author: MikeRayMSFT
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: aa0b00ec24c96aea37901cc03aac2dda9b20bed2
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2020
ms.locfileid: "88655288"
---
Jede Verfügbarkeitsgruppe hat nur ein primäres Replikat. Das primäre Replikat lässt Lese- und Schreibvorgänge zu. Sie können ein Failover ausführen, um das primäre Replikat zu ändern. In einer Verfügbarkeitsgruppe für Hochverfügbarkeit automatisiert der Cluster-Manager den Failovervorgang. In einer Verfügbarkeitsgruppe mit dem Clustertyp „NONE“ erfolgt der Failovervorgang manuell. 

Es gibt zwei Möglichkeiten, ein Failover für ein primäres Replikat in einer Verfügbarkeitsgruppe mit dem Clustertyp „NONE“ auszuführen:

- Erzwungenes manuelles Failover mit Datenverlust
- Manuelles Failover ohne Datenverlust

### <a name="forced-manual-failover-with-data-loss"></a>Erzwungenes manuelles Failover mit Datenverlust

Verwenden Sie diese Methode, wenn das primäre Replikat nicht verfügbar ist und nicht wiederhergestellt werden kann. 

Um ein Failover mit Datenverlust auszuführen, stellen Sie eine Verbindung mit der SQL Server-Instanz her, die das sekundäre Zielreplikat hostet, und führen Sie dann den folgenden Befehl aus:

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

Wenn das vorherige primäre Replikat wiederhergestellt wurde, übernimmt es auch die primäre Rolle. Um sicherzustellen, dass das vorherige primäre Replikat in eine sekundäre Rolle übergeht, führen Sie den folgenden Befehl für das vorherige primäre Replikat aus:

```SQL
ALTER AVAILABILITY GROUP [ag1]  SET (ROLE = SECONDARY);
```

### <a name="manual-failover-without-data-loss"></a>Manuelles Failover ohne Datenverlust

Verwenden Sie diese Methode, wenn das primäre Replikat verfügbar ist. Dabei müssen Sie allerdings vorübergehend oder dauerhaft die Konfiguration ändern und die SQL Server-Instanz ändern, die das primäre Replikat hostet. Um potenzielle Datenverluste zu vermeiden, stellen Sie vor der Ausführung eines manuellen Failovers sicher, dass das sekundäre Zielreplikat aktuell ist. 

So führen ein manuelles Failover ohne Datenverlust aus:

1. Verwenden Sie `SYNCHRONOUS_COMMIT` für das aktuelle primäre Replikat und das sekundäre Zielreplikat.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

1. Um zu ermitteln, ob für aktive Transaktionen ein Commit auf das primäre Replikat und gleichzeitig auf mindestens ein synchrones sekundäres Replikat ausgeführt wurde, führen Sie die folgende Abfrage aus: 

   ```SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

   Das sekundäre Replikat wird synchronisiert, wenn `synchronization_state_desc``SYNCHRONIZED` ist.

1. Aktualisieren Sie `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf 1.

   Das folgende Skript legt `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf „1“ für eine Verfügbarkeitsgruppe mit dem Namen `ag1` fest. Ersetzen Sie `ag1` vor der Ausführung des Skripts durch den Namen Ihrer Verfügbarkeitsgruppe:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1);
   ```

   Diese Einstellung stellt sicher, dass für jede aktive Transaktion ein Commit auf das primäre Replikat und auf mindestens ein synchrones sekundäres Replikat ausgeführt wurde. 
   >[!NOTE]
   >Diese Einstellung ist nicht failoverspezifisch und sollte anhand der Umgebungsanforderungen festgelegt werden.
   
1. Schalten Sie das primäre Replikat offline, um Rollenänderungen vorzubereiten.
   ```SQL
   ALTER AVAILABILITY GROUP [ag1] OFFLINE
   ```

1. Stufen Sie das sekundäre Zielreplikat auf ein primäres hoch. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ``` 

1. Aktualisieren Sie die Rolle des alten Replikats auf `SECONDARY`, und führen Sie den folgenden Befehl auf der SQL Server-Instanz aus, die das alte primäre Replikat hostet:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

   > [!NOTE] 
   > Verwenden Sie [DROP AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/drop-availability-group-transact-sql) (Verfügbarkeitsgruppe löschen), um eine Verfügbarkeitsgruppe zu löschen. Führen Sie bei Verfügbarkeitsgruppen, die mit dem Clustertyp „NONE“ oder „EXTERNAL“ erstellt wurden, den Befehl für alle Replikate aus, die der Verfügbarkeitsgruppe angehören.

1. Setzen Sie die Datenverschiebung fort, und führen Sie folgenden Befehl für jede Datenbank in der Verfügbarkeitsgruppe auf der SQL Server-Instanz aus, die das primäre Replikat hostet: 

   ```sql
   ALTER DATABASE [db1]
        SET HADR RESUME
   ```

1. Erstellen Sie jeden Listener neu, den Sie für Leseskalierungszwecke erstellt haben und der nicht von einem Cluster-Manager verwaltet wird. Wenn der ursprüngliche Listener auf das alte primäre Replikat zeigt, löschen Sie ihn, und erstellen Sie ihn neu, um auf das neue primäre Replikat zu verweisen.
