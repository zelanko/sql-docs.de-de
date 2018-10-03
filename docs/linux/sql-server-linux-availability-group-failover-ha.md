---
title: Verwalten von Failover der verfügbarkeitsgruppe – SQL Server unter Linux | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 1fe1a785314b30e0f6027c845da5ac2b34692966
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796718"
---
# <a name="always-on-availability-group-failover-on-linux"></a>Failover von AlwaysOn-Verfügbarkeitsgruppe unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Im Kontext einer verfügbarkeitsgruppe (AG) sind die primäre und sekundäre Rolle von verfügbarkeitsreplikaten normalerweise Rahmen wird als Failover bezeichnet. Failover können in drei Formen auftreten: automatisches Failover (ohne Datenverlust), geplantes manuelles Failover (ohne Datenverlust) und erzwungenes manuelles Failover (mit möglichem Datenverlust), welches in der Regel *erzwungenes Failover*genannt wird. Beim automatischen und geplanten manuellen Failover bleiben alle Daten erhalten. Eine Verfügbarkeitsgruppe ein Failover auf das verfügbarkeitsreplikat-Ebene. D. h. eine Verfügbarkeitsgruppe führt ein Failover auf eine ihrer sekundären Replikate (das aktuelle failoverziel). 

Hintergrundinformationen zum Failover finden Sie unter [Failover und failovermodi](../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md).

## <a name="failover"></a>Manuelles failover

Verwenden Sie die Clusterverwaltungstools, um ein Failover einer Verfügbarkeitsgruppe, die von einem externen Cluster-Manager verwaltet werden. Verwenden Sie z. B. wenn eine Projektmappe Pacemaker verwendet, um einen Linux-Cluster zu verwalten, `pcs` um ein manuelles Failover für RHEL oder Ubuntu auszuführen. Verwenden Sie unter SLES `crm`. 

> [!IMPORTANT]
> Unter normalen Betriebs wird kein Failover ausgeführt mit Transact-SQL oder SQL Server-Management-Tools wie SSMS oder PowerShell. Wenn `CLUSTER_TYPE = EXTERNAL`, der einzige zulässige Wert für `FAILOVER_MODE` ist `EXTERNAL`. Mit diesen Einstellungen werden alle failoveraktionen für manuelle oder automatische vom externen Cluster-Manager ausgeführt. Informationen zum Erzwingen eines Failovers mit potenziellem Datenverlust finden Sie unter [Failover erzwingen](#forceFailover).

### <a name="a-namemanualfailovermanual-failover-steps"></a><a name="manualFailover">Schritte für das manuelle failover

Zum Ausführen eines Failovers muss das sekundäre Replikat, das das primäre Replikat wird synchron sein. Wenn ein sekundäres Replikat asynchron ist [Ändern des Verfügbarkeitsmodus](../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md).

Manuelles Failover in zwei Schritten.

   Zuerst[ manuelles Failover der Tabulatortaste verschieben AG-Ressource](#manualMove) aus dem Clusterknoten, der die Ressourcen, um einen neuen Knoten besitzt.

   Der Cluster die AG-Ressource ein Failover und fügt Sie eine speicherorteinschränkung hinzu. Diese Einschränkung wird konfiguriert, die Ressource, die auf dem neuen Knoten ausgeführt wird. Entfernen Sie diese Einschränkung, um ein Failover in der Zukunft ausgeführt werden.

   Zweitens [Entfernen der speicherorteinschränkung](#removeLocConstraint).

#### <a name="a-namemanualmovestep-1-manually-fail-over-by-moving-availability-group-resource"></a><a name="manualMove">Schritt 1. Manuelles Failover durch Verfügbarkeitsgruppen-Ressource verschieben

Um manuell ein Failover einer Verfügbarkeitsgruppe-Ressource, die mit dem Namen *Ag_cluster* auf Clusterknoten, die mit dem Namen *nodeName2*, führen Sie den entsprechenden Befehl für Ihre Distribution:

- **RHEL/Ubuntu-Beispiel**

   ```bash
   sudo pcs resource move ag_cluster-master nodeName2 --master
   ```

- **SLES-Beispiel**

   ```bash
   crm resource migrate ag_cluster nodeName2
   ```

>[!IMPORTANT]
>Nachdem Sie eine Ressource manuell ein Failover, müssen Sie eine speicherorteinschränkung entfernen, die automatisch hinzugefügt wird.

#### <a name="a-nameremovelocconstraint-step-2-remove-the-location-constraint"></a><a name="removeLocConstraint"> Schritt 2. Entfernen der Speicherorteinschränkung

Während eines manuellen Failovers der `pcs` Befehl `move` oder `crm` Befehl `migrate` Fügt eine speicherorteinschränkung für die Ressource auf dem neuen Zielknoten platziert werden. Um die neue Einschränkung anzuzeigen, führen Sie den folgenden Befehl nach dem Verschieben der Ressource aus:

- **RHEL/Ubuntu-Beispiel**

   ```bash
   sudo pcs constraint list --full
   ```

- **SLES-Beispiel**

   ```bash
   crm config show
   ```

Ein Beispiel für die Einschränkung, die aufgrund eines manuellen Failovers erstellt wird. 
 `Enabled on: Node1 (score:INFINITY) (role: Master) (id:cli-prefer-ag_cluster-master)`

- **RHEL/Ubuntu-Beispiel**

   Im folgenden Befehl ist `cli-prefer-ag_cluster-master` die ID der Einschränkung, die entfernt werden muss. `sudo pcs constraint list --full` gibt diese ID zurück. 
   
   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```
   
- **SLES-Beispiel**

   In den folgenden Befehl `cli-prefer-ms-ag_cluster` ist die ID der Einschränkung. `crm config show` gibt diese ID zurück. 
   
   ```bash
   crm configure
   delete cli-prefer-ms-ag_cluster 
   commit
   ```

>[!NOTE]
>Das automatische Failover fügt keine Speicherorteinschränkung hinzu, also ist keine Bereinigung notwendig. 

Weitere Informationen:  
- [Red Hat - Managing Cluster Resources (Red Hat – Verwalten von Clusterressourcen)](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-manageresource-HAAR.html)
- [Pacemaker – Manuelles Verschieben von Ressourcen](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-pcs/html/Clusters_from_Scratch/_move_resources_manually.html)
 [SLES-Administratorhandbuch - Ressourcen](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.resource) 
 
## <a name="forceFailover"></a> Erzwungenen failover 

Ein erzwungenes Failover ist ausschließlich für die notfallwiederherstellung vorgesehen. In diesem Fall kann nicht mit Tools für die Clusterverwaltung Failover, da das primäre Rechenzentrum ausgefallen ist. Wenn Sie ein Failover auf ein nicht synchronisiertes sekundäres Replikat erzwingen, ist Datenverlust möglich. Erzwingen Sie Failover nur, wenn Sie den Dienst an die Verfügbarkeitsgruppe sofort wiederherstellen müssen und bereit sind, besteht das Risiko, dass Daten verloren gehen.

Wenn Sie die Clusterverwaltungstools verwenden können nicht für die Interaktion mit dem Cluster – z. B. wenn der Cluster nicht mehr reagiert, auf einen Notfall zurückzuführen im primären Rechenzentrum ist, müssen Sie möglicherweise Erzwingen eines Failovers den externen Cluster-Manager zu umgehen. Dieses Verfahren wird für normale Vorgänge nicht empfohlen, da besteht das Risiko von Datenverlusten. Verwenden Sie diese Option, wenn Sie die Clusterverwaltungstools zum Ausführen der failoveraktion fehl. Dieses Verfahren ist funktionell ähnelt [Ausführen eines erzwungenen manuellen Failovers](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md) auf eine Verfügbarkeitsgruppe in Windows.
 
Dieser Prozess für das Erzwingen eines Failovers ist spezifisch für SQL Server unter Linux.

1. Stellen Sie sicher, dass die AG-Ressource nicht mehr vom Cluster verwaltet wird. 

      - Legen Sie die Ressource auf dem Ziel-Clusterknoten in den nicht verwalteten Modus. Mit diesem Befehl signalisiert den Ressourcen-Agent, Verwaltung und Überwachung von Ressourcen beenden. Zum Beispiel: 
      
      ```bash
      sudo pcs resource unmanage <resourceName>
      ```

      - Wenn der Versuch, den ressourcenmodus auf den nicht verwalteten Modus festgelegt ein Fehler auftritt, löschen Sie die Ressource. Zum Beispiel:

      ```bash
      sudo pcs resource delete <resourceName>
      ```

      >[!NOTE]
      >Wenn Sie eine Ressource löschen, löscht es auch alle zugehörigen Einschränkungen. 

1. Legen Sie auf der Instanz von SQL Server, die das sekundäre Replikat hostet, die Sitzung Kontextvariable `external_cluster`.

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Ein Failover der Verfügbarkeitsgruppe mit Transact-SQL. Ersetzen Sie im folgenden Beispiel `<MyAg>` durch den Namen Ihrer Verfügbarkeitsgruppe. Verbinden mit der Instanz von SQL Server, das das sekundäre Zielreplikat hostet, und führen Sie den folgenden Befehl aus:

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <MyAg> FORCE_FAILOVER_ALLOW_DATA_LOSS;
   ```

1.  Schalten Sie nach einem erzwungenen Failover der Verfügbarkeitsgruppe in einen fehlerfreien Zustand vor dem Neustart die ressourcenüberwachung für Cluster und die Verwaltung oder die AG-Ressource neu zu erstellen. Überprüfen Sie die [wichtige Aufgaben nach einem erzwungenen Failover](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md#FollowUp).

1.  Starten Sie Cluster Ressourcen überwachen und verwalten:

   Um die Cluster Resource Überwachung und Verwaltung neu zu starten, führen Sie den folgenden Befehl aus:

   ```bash
   sudo pcs resource manage <resourceName>
   sudo pcs resource cleanup <resourceName>
   ```

   Wenn Sie die Clusterressource gelöscht, neu erstellen. Um die Clusterressource neu zu erstellen, befolgen Sie die Anweisungen unter [erstellen verfügbarkeitsgruppenressource](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource).

>[!Important]
>Verwenden Sie nicht die vorherigen Schritten für Übungen zur notfallwiederherstellung, da das Risiko für Datenverluste. Stattdessen Ändern des asynchronen Replikats als synchron und die Anweisungen für die [normalen Manuelles Failover](#manualFailover).

## <a name="database-level-monitoring-and-failover-trigger"></a>Ebene endpunktüberwachung und -Failover-Trigger auf Datenbankebene

Für `CLUSTER_TYPE=EXTERNAL`, die Failover-Triggersemantik unterscheiden sich im Vergleich zu den WSFC. Wenn die Verfügbarkeitsgruppe auf einer Instanz von SQL Server in einem WSFC ist, wechselt von `ONLINE` Status für die Datenbank bewirkt, die Integrität der Verfügbarkeitsgruppe dass um einen Fehler zu melden. Als Antwort wird der Cluster-Manager eine Failover-Aktion ausgelöst. Unter Linux kann nicht die SQL Server-Instanz mit dem Cluster kommunizieren. Überwachung für die Integrität der erfolgt *indirekte*. Wenn Benutzer sich, für die Datenbank auf Überwachung und Failover entschieden (durch Festlegen der Option `DB_FAILOVER=ON` beim Erstellen der Verfügbarkeitsgruppe), der Cluster überprüft, ob der Datenbankstatus ist `ONLINE` jedes Mal, wenn sie eine Überwachung Aktion ausgeführt wird. Der Cluster fragt den Status im `sys.databases`. Für sämtliche Staaten unterscheiden `ONLINE`, es wird ein Failover ausgelöst, automatisch (wenn automatisches Failover-Bedingungen erfüllt sind). Die tatsächliche Zeit des Failovers hängt von der Häufigkeit der Überwachungsaktion sowie den Zustand der Datenbank in sys.databases aktualisiert wird.

Automatisches Failover erfordert mindestens ein synchrones Replikat.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren von Red Hat Enterprise Linux-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-rhel.md)

[Konfigurieren von SUSE Linux Enterprise Server-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-sles.md)

[Konfigurieren Sie Ubuntu-Cluster für die Verfügbarkeitsgruppe für SQL Server-Clusterressourcen](sql-server-linux-availability-group-cluster-ubuntu.md)
