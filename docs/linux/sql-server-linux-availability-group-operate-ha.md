---
title: Verfügbarkeitsgruppe SQL Server unter Linux arbeiten
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 03/01/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 24a9d3d9ee0fd65b08e30f40a0597eadf47c6b76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916038"
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Always On-Verfügbarkeitsgruppen unter Linux arbeiten

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>Aktualisieren der verfügbarkeitsgruppe

Vor dem upgrade von einer verfügbarkeitsgruppe befindet, überprüfen Sie die Muster und Praktiken auf [ein Upgrade von Verfügbarkeitsgruppen-replikatsinstanzen](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).

In den folgenden Abschnitten wird erläutert, wie ein paralleles Upgrade mit SQL Server-Instanzen unter Linux mit Verfügbarkeitsgruppen ausgeführt wird. 

### <a name="upgrade-steps-on-linux"></a>Upgradeschritte für Linux

Wenn Replikate der verfügbarkeitsgruppe für Instanzen von SQL Server unter Linux sind, ist der Clustertyp der verfügbarkeitsgruppe entweder `EXTERNAL` oder `NONE`. Eine verfügbarkeitsgruppe, die von einem Cluster-Manager verwaltet wird, neben Windows Server-Failovercluster (WSFC) ist `EXTERNAL`. Pacemaker mit Corosync ist ein Beispiel für einen externen Cluster-Manager. Eine verfügbarkeitsgruppe ohne Cluster-Manager verfügt Clustertyp `NONE` die Aktualisierung hier erläuterten Schritte sind spezifisch für Verfügbarkeitsgruppen der Clustertyp `EXTERNAL` oder `NONE`.

Die Reihenfolge, in der Sie Instanzen aktualisieren, hängt ab, wenn ihre Rolle ist die sekundäre Datenbank und davon, ob sie die synchrone oder asynchrone Replikate hosten. Aktualisieren Sie die Instanzen von SQL Server, die zuerst asynchrone sekundäre Replikate zu hosten. Aktualisieren Sie Instanzen, die synchronen sekundären Replikate hosten. 

   >[!NOTE]
   >Wenn eine verfügbarkeitsgruppe nur die asynchrone Replikate, um Datenverluste zu vermeiden ein Replikat als synchron zu ändern, und warten, bis er synchronisiert wird. Klicken Sie dann ein upgrade dieses Replikat aus.
   
Bevor Sie beginnen, müssen Sie jede Datenbank sichern.

1. Beenden Sie die Ressource, auf dem Knoten, die das sekundäre Replikat als Ziel für das Upgrade hostet.
   
   Beenden Sie vor dem Ausführen von Upgrade-Befehls, der Ressource, damit der Cluster nicht werden überwacht und es unnötig fehl. Im folgenden Beispiel wird eine speicherorteinschränkung auf dem Knoten, der sich ergeben, wird für die Ressource beendet werden soll. Update `ag_cluster-master` mit dem Ressourcennamen und `nodeName1` mit dem Knoten hostet das Replikat als Ziel für das Upgrade.

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. Upgrade von SQL Server auf dem sekundären Replikat.

   Das folgende Beispiel-Upgrades `mssql-server` und `mssql-server-ha` Pakete.

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. Entfernen Sie die Einschränkung für den Standort.

   Beenden Sie vor dem Ausführen von Upgrade-Befehls, der Ressource, damit der Cluster nicht werden überwacht und es unnötig fehl. Im folgenden Beispiel wird eine speicherorteinschränkung auf dem Knoten, der sich ergeben, wird für die Ressource beendet werden soll. Update `ag_cluster-master` mit dem Ressourcennamen und `nodeName1` mit dem Knoten hostet das Replikat als Ziel für das Upgrade.

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   Als bewährte Methode, stellen Sie sicher die Ressource wird gestartet (mithilfe von `pcs status` Befehl) und das sekundäre Replikat ist verbunden und Zustand nach dem Upgrade "synchronisiert".

1. Nachdem alle sekundären Replikate aktualisiert werden, manuell ein Failover auf eines der synchronen sekundären Replikaten.

   Für Verfügbarkeitsgruppen mit `EXTERNAL` Clustertyp, verwenden Sie die Clusterverwaltungstools, nicht über; Verfügbarkeitsgruppen mit `NONE` Clustertyp sollten Transact-SQL verwenden, um ein Failover auszuführen. 
   Im folgenden Beispiel wird ein Failover einer verfügbarkeitsgruppe mit die Verwaltungstools. Ersetzen Sie dies `<targetReplicaName>` durch den Namen des synchronen sekundären Replikats, das primäre werden soll:

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >Die folgenden Schritte gelten nur für Verfügbarkeitsgruppen, die nicht über einen Cluster-Manager verfügen.

   Wenn der Clustertyp Gruppe ist `NONE`manuell ein Failover. Führen Sie die folgenden Schritte wie folgt aus:

      a. Der folgende Befehl legt das primäre Replikat zum sekundären Standort. Ersetzen Sie dies `AG1` mit dem Namen der verfügbarkeitsgruppe. Führen Sie den Transact-SQL-Befehl für die Instanz von SQL Server hostet, die das primäre Replikat.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      b. Der folgende Befehl legt ein synchrones sekundäres Replikat zum primären Replikat. Führen den folgenden Transact-SQL-Befehl auf der Zielinstanz von SQL Server - Instanz hostet, die das synchrone sekundäre Replikat.

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. Nach dem Failover aktualisieren Sie SQL Server auf dem alten primären Replikat durch Wiederholen der vorherigen Prozedur ein.

   Das folgende Beispiel-Upgrades `mssql-server` und `mssql-server-ha` Pakete.

   ```bash
   # add constraint for the resource to stop on the upgraded node
   # replace 'nodename2' with the name of the cluster node targeted for upgrade
   pcs constraint location ag_cluster-master avoids nodeName2
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   
   ```bash
   # upgrade mssql-server and mssql-server-ha packages
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```

   ```bash
   # remove the constraint; make sure the resource is started and replica is connected and synchronized
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```

1. Bereinigen Sie für ein Verfügbarkeitsgruppen mit einem externen Cluster-Manager -, in dem Clustertyp "EXTERNAL" ist die Einschränkung für den Standort, der durch das manuelle Failover verursacht wurde. 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. Fortsetzen der datenverschiebung für das neu aktualisierte sekundäre Replikat – das frühere primäre Replikat. Dieser Schritt ist erforderlich, wenn Sie eine höhere Version Instanz von SQL Server Protokollblöcken, die mit einer niedrigeren Version einer Instanz in einer verfügbarkeitsgruppe übertragen wird. Führen Sie den folgenden Befehl auf dem neuen sekundären Replikat (das frühere primäre Replikat).

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

Nach dem Upgrade aller Server können Sie ein Failback. Führen einen Sie Failover auf den ursprünglichen primären -, falls erforderlich. 

## <a name="drop-an-availability-group"></a>Löschen einer verfügbarkeitsgruppe

Führen Sie zum Löschen einer verfügbarkeitsgruppe [DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md). Wenn der Typ des Clusters ist `EXTERNAL` oder `NONE` führen Sie den Befehl auf jeder Instanz von SQL Server, die ein Replikat hostet. Z. B. Löschen einer verfügbarkeitsgruppe mit dem Namen `group_name` führen Sie den folgenden Befehl:

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von Red Hat Enterprise Linux-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-rhel.md)

[Konfigurieren von SUSE Linux Enterprise Server-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-sles.md)

[Konfigurieren Sie Ubuntu-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-ubuntu.md)
