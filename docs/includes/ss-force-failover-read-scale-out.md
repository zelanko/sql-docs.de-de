---
title: 'SQL Server: Erzwingen eines Failovers für Verfügbarkeitsgruppen'
description: Erzwingen eines Failovers für Verfügbarkeitsgruppen mit dem Clustertyp „NONE“
services: ''
author: MikeRayMSFT
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: f5655e73481d830c848aea34c4a4f49613be0913
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
Jede Verfügbarkeitsgruppe verfügt über nur ein primäres Replikat. Das primäre Replikat lässt Lese- und Schreibvorgänge zu. Sie können ein Failover ausführen, um das primäre Replikat zu ändern. In einer Verfügbarkeitsgruppe für Hochverfügbarkeit automatisiert der Cluster-Manager den Failovervorgang. In einer Verfügbarkeitsgruppe mit Clustertyp „NONE“ erfolgt der Failovervorgang manuell. 

Es gibt zwei Möglichkeiten, ein Failover für ein primäres Replikat in einer Verfügbarkeitsgruppe mit dem Clustertyp „NONE“ auszuführen:

- Erzwungenes manuelles Failover mit Datenverlust
- Manuelles Failover ohne Datenverlust

### <a name="forced-manual-failover-with-data-loss"></a>Erzwungenes manuelles Failover mit Datenverlust

Verwenden Sie diese Methode, wenn das primäre Replikat nicht verfügbar ist und nicht wiederhergestellt werden kann. 

Stellen Sie eine Verbindung mit der SQL Server-Instanz her, die das sekundäre Zielreplikat hostet, und führen Sie folgenden Befehl aus, um ein Failover mit Datenverlust auszuführen:

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-failover-without-data-loss"></a>Manuelles Failover ohne Datenverlust

Verwenden Sie diese Methode, wenn das primäre Replikat verfügbar ist. Dabei müssen Sie allerdings vorübergehend oder dauerhaft die Konfiguration ändern und die SQL Server-Instanz ändern, die das primäre Replikat hostet. Bevor Sie das manuelle Failover ausführen, stellen Sie sicher, dass das sekundäre Zielreplikat aktuell ist, um potenzielle Datenverluste zu vermeiden. 

So führen ein manuelles Failover ohne Datenverlust aus:

1. Legen Sie `SYNCHRONOUS_COMMIT` als sekundäres Zielreplikat fest.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. Führen Sie die folgende Abfrage aus, um zu ermitteln, ob für aktive Transaktionen ein Commit auf das primäre Replikat und gleichzeitig auf mindestens ein synchrones sekundäres Replikat ausgeführt wurde: 

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

   Das sekundäre Replikat wird synchronisiert, wenn `synchronization_state_desc` `SYNCHRONIZED` ist.

3. Aktualisieren Sie `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf 1.

   Das folgende Skript legt `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf 1 für eine Verfügbarkeitsgruppe namens `ag1` fest. Ersetzen Sie `ag1` vor der Ausführung des Skripts durch den Namen Ihrer Verfügbarkeitsgruppe.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   Diese Einstellung stellt sicher, dass für jede aktive Transaktion ein Commit auf das primäre Replikat und auf mindestens ein synchrones sekundäres Replikat ausgeführt wurde. 

4. Stufen Sie das primäre Replikat auf ein sekundäres Replikat herunter. Anschließend ist es schreibgeschützt. Führen Sie diesen Befehl auf der SQL Server-Instanz aus, die das primäre Replikat hostet, um die Rolle auf `SECONDARY` zu aktualisieren:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

5. Stufen Sie das sekundäre Zielreplikat auf ein primäres hoch. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Wenn Sie eine Verfügbarkeitsgruppe löschen möchten, verwenden Sie [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Bei Verfügbarkeitsgruppen, die mit dem Clustertyp „NONE“ oder „EXTERNAL“ erstellt wurden, muss der Befehl für alle Replikate ausgeführt werden, die der Verfügbarkeitsgruppe angehören.