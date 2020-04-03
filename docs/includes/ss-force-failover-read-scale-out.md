---
title: 'SQL Server: Erzwingen eines Failovers für Verfügbarkeitsgruppen'
description: Erzwingen eines Failovers für Verfügbarkeitsgruppen mit dem Clustertyp „NONE“
services: ''
author: MikeRayMSFT
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: 90c7c7863228ce210e56e76ab3e12c77e7ccc902
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80407982"
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

1. Legen Sie `SYNCHRONOUS_COMMIT` als sekundäres Zielreplikat fest.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. Um zu ermitteln, ob für aktive Transaktionen ein Commit auf das primäre Replikat und gleichzeitig auf mindestens ein synchrones sekundäres Replikat ausgeführt wurde, führen Sie die folgende Abfrage aus: 

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

3. Aktualisieren Sie `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf 1.

   Das folgende Skript legt `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf „1“ für eine Verfügbarkeitsgruppe mit dem Namen `ag1` fest. Ersetzen Sie `ag1` vor der Ausführung des Skripts durch den Namen Ihrer Verfügbarkeitsgruppe:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1);
   ```

   Diese Einstellung stellt sicher, dass für jede aktive Transaktion ein Commit auf das primäre Replikat und auf mindestens ein synchrones sekundäres Replikat ausgeführt wurde. 
   >[!NOTE]
   >Diese Einstellung ist nicht failoverspezifisch und sollte anhand der Umgebungsanforderungen festgelegt werden.
   
4. Schalten Sie das primäre Replikat offline, um Rollenänderungen vorzubereiten.
   ```SQL
   ALTER AVAILABILITY GROUP [ag1] OFFLINE
   ```

5. Stufen Sie das sekundäre Zielreplikat auf ein primäres hoch. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ``` 

6. Aktualisieren Sie die Rolle des alten Replikats auf `SECONDARY`, und führen Sie den folgenden Befehl auf der SQL Server-Instanz aus, die das primäre Replikat hostet:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

   > [!NOTE] 
   > Verwenden Sie [DROP AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/drop-availability-group-transact-sql) (Verfügbarkeitsgruppe löschen), um eine Verfügbarkeitsgruppe zu löschen. Führen Sie bei Verfügbarkeitsgruppen, die mit dem Clustertyp „NONE“ oder „EXTERNAL“ erstellt wurden, den Befehl für alle Replikate aus, die der Verfügbarkeitsgruppe angehören.
