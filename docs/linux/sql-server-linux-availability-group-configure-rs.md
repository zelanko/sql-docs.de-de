---
title: Konfigurieren Sie eine SQL Server-Verfügbarkeitsgruppe für schreibgeschützte horizontale Skalierung unter Linux
titleSuffix: SQL Server
description: Informationen Sie zum Konfigurieren der eine SQL Server immer auf Availability Group (AG) für schreibgeschützte arbeitsauslastungen unter Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 014ff123618c04f91c0e2c2a39d5ef8e5690a386
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53203869"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>Konfigurieren Sie eine SQL Server-Verfügbarkeitsgruppe für schreibgeschützte horizontale Skalierung unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können eine SQL Server immer auf Availability Group (AG) für schreibgeschützte arbeitsauslastungen unter Linux konfigurieren. Für Verfügbarkeitsgruppen gibt es zwei Architekturtypen. Eine Architektur für hochverfügbarkeit verwendet einen Cluster-Manager, um verbesserte Geschäftskontinuität zu ermöglichen. Diese Architektur kann auch schreibgeschützte Replikate enthalten. Um die Architektur für hohe Verfügbarkeit zu erstellen, finden Sie unter [Konfigurieren von SQL Server AlwaysOn-Verfügbarkeitsgruppe für hochverfügbarkeit bei Linux](sql-server-linux-availability-group-configure-ha.md). Die andere Architektur unterstützt nur Workloads zur Leseskalierung. In diesem Artikel wird erläutert, wie eine Verfügbarkeitsgruppe ohne Cluster-Manager für Workloads zur Leseskalierung erstellt wird. Diese Architektur bietet nur Leseskalierung. Sie bietet keine Hochverfügbarkeit.

>[!NOTE]
>Eine Verfügbarkeitsgruppe mit `CLUSTER_TYPE = NONE` kann Replikate enthalten, die auf verschiedenen Betriebssystemplattformen gehostet werden. Sie kann keine Unterstützung für Hochverfügbarkeit bieten. 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>Erstellen der Verfügbarkeitsgruppe

Erstellen Sie die Verfügbarkeitsgruppe. Legen Sie `CLUSTER_TYPE = NONE` fest. Darüber hinaus sollten Sie jedes Replikat mit `FAILOVER_MODE = MANUAL` festlegen. Clientanwendungen, die Analysen durchführen oder Berichte zu Workloads erstellen, können eine direkte Verbindung mit der sekundären Datenbank herstellen. Sie können auch eine schreibgeschützte Routingliste erstellen. Anforderungen zum Lesen der Verbindung werden dann über Verbindungen mit dem primären Replikat in Round-Robin-Manier an jedes der in der Routingliste enthaltene sekundäre Replikat weitergeleitet.

Das folgende Transact-SQL-Skript erstellt eine Verfügbarkeitsgruppe mit dem Namen `ag1`. Das Skript konfiguriert die Verfügbarkeitsgruppenreplikate mit `SEEDING_MODE = AUTOMATIC`. Diese Einstellung bewirkt, dass SQL Server die Datenbank automatisch auf jedem sekundären Server erstellt, nachdem diese zur Verfügbarkeitsgruppe hinzugefügt wurde. Aktualisieren Sie das folgende Skript für Ihre Umgebung. Ersetzen Sie die Werte `<node1>` und `<node2>` durch die Namen der SQL Server-Instanzen, auf denen die Replikate gehostet werden. Ersetzen Sie den Wert `<5022>` durch den Port, den Sie für den Endpunkt festgelegt haben. Führen Sie auf dem primären SQL Server-Replikat das folgende Transact-SQL-Skript aus:

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH ( 
            ENDPOINT_URL = N'tcp://<node2>:<5022>', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>Verknüpfen sekundärer SQL-Server mit der Verfügbarkeitsgruppe

Das folgende Transact-SQL-Skript verknüpft einen Server mit einer Verfügbarkeitsgruppe mit dem Namen `ag1`. Aktualisieren Sie das Skript für Ihre Umgebung. Führen Sie auf jedem sekundären SQL Server-Replikat das folgende Transact-SQL-Skript aus, um die Verfügbarkeitsgruppe zu verknüpfen:

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

Bei dieser Verfügbarkeitsgruppe handelt es sich um keine Hochverfügbarkeitskonfiguration. Wenn Sie hochverfügbarkeit benötigen, befolgen Sie die Anweisungen unter [Konfigurieren einer AlwaysOn-Verfügbarkeitsgruppe für SQL Server unter Linux](sql-server-linux-availability-group-configure-ha.md). Erstellen Sie insbesondere die Verfügbarkeitsgruppe mit `CLUSTER_TYPE=WSFC` (in Windows) oder `CLUSTER_TYPE=EXTERNAL` (in Linux). Integrieren Sie anschließend in einem Cluster-Manager, mit entweder Windows Server-Failoverclustering für Windows oder Pacemaker unter Linux.

## <a name="connect-to-read-only-secondary-replicas"></a>Verbinden mit schreibgeschützten sekundären Replikaten

Es gibt zwei Möglichkeiten für die Verbindung mit schreibgeschützten sekundären Replikaten. Anwendungen können eine direkte Verbindung mit der SQL Server-Instanz herstellen, auf der das sekundäre Replikat gehostet wird, und die Datenbanken abfragen. Sie können auch schreibgeschütztes Routing verwenden, wofür ein Listener erforderlich ist.

* [Lesbare sekundäre Replikate](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [Schreibgeschütztes Routing](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>Ausführen eines Failovers des primären Replikats auf eine schreibgeschützte Verfügbarkeitsgruppe

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>Nächste Schritte

* [Konfigurieren verteilter Verfügbarkeitsgruppen](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [Weitere Informationen zu Verfügbarkeitsgruppen](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [Ausführen eines erzwungenen manuellen Failovers](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

