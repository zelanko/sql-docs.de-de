---
title: Erstellen einer Verfügbarkeitsgruppe (SQL Server PowerShell) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: bc69a7df-20fa-41e1-9301-11317c5270d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8085fa23357c5901ed350e81410ae4d38a3005dd
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75228798"
---
# <a name="create-an-availability-group-sql-server-powershell"></a>Erstellen einer Verfügbarkeitsgruppe (SQL Server PowerShell)
  In diesem Thema wird beschrieben, wie PowerShell-Cmdlets zum Erstellen und Konfigurieren einer AlwaysOn-Verfügbarkeitsgruppe mithilfe von PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]verwendet werden. Eine *Verfügbarkeitsgruppe* definiert einen Satz von Benutzerdatenbanken, für die als eine einzelne Einheit ein Failover ausgeführt wird, sowie einen Satz von Failoverpartnern, die als *Verfügbarkeitsreplikate*bezeichnet werden und das Failover unterstützen.  
  
> [!NOTE]  
>  Eine Einführung zu Verfügbarkeitsgruppen finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  

> [!NOTE]  
>  Als Alternative zur Verwendung von PowerShell-Cmdlets können Sie den Assistenten zum Erstellen einer Verfügbarkeitsgruppe oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]verwenden. Weitere Informationen finden Sie unter [Verwenden des Dialogfelds „Neue Verfügbarkeitsgruppe“ &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md) oder [Erstellen einer Verfügbarkeitsgruppe &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)verwendet werden.  
  
##  <a name="BeforeYouBegin"></a>Bevor Sie beginnen  
 Es wird dringend empfohlen, dass Sie diesen Abschnitt lesen, bevor Sie versuchen, Ihre erste Verfügbarkeitsgruppe zu erstellen.  
  
###  <a name="PrerequisitesRestrictions"></a>Voraussetzungen, Einschränkungen und Empfehlungen  
  
-   Überprüfen Sie vor dem Erstellen einer Verfügbarkeitsgruppe, ob sich die Hostinstanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] jeweils auf verschiedenen WSFC-Knoten (Windows Server-Failoverclustering) eines einzelnen WSFC-Failoverclusters befinden. Stellen Sie auch sicher, dass die Serverinstanzen die anderen Serverinstanzvoraussetzungen erfüllen, dass alle anderen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]-Anforderungen erfüllt sind und dass Sie die Empfehlungen berücksichtigen. Wenn Sie weitere Informationen wünschen, sollten Sie unbedingt [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) lesen.  
  
###  <a name="Security"></a>Sicherung  
  
####  <a name="Permissions"></a>Griff  
 Erfordert die Mitgliedschaft in der festen **sysadmin** -Serverrolle und die CREATE AVAILABILITY GROUP-Serverberechtigung, ALTER ANY AVAILABILITY GROUP-Berechtigung oder CONTROL SERVER-Berechtigung.  
  
###  <a name="SummaryPSStatements"></a>Zusammenfassung von Tasks und entsprechenden PowerShell-Cmdlets  
 In der folgenden Tabelle sind die grundlegenden Tasks für die Konfiguration einer Verfügbarkeitsgruppe aufgeführt, und es sind die Tasks angegeben, die von PowerShell-Cmdlets unterstützt werden. Die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Tasks müssen in der Reihenfolge ausgeführt werden, in der sie in der Tabelle dargestellt sind.  
  
|Aufgabe|PowerShell-Cmdlets (falls verfügbar) oder Transact-SQL-Anweisung|Wo der Task auszuführen ist**<sup>*</sup>**|  
|----------|--------------------------------------------------------------------|-------------------------------------------|  
|Erstellen eines Datenbankspiegelungs-Endpunkts (einmal pro [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz)|`New-SqlHadrEndPoint`|Führen Sie diesen Task auf jeder Serverinstanz aus, auf der der Datenbankspiegelungs-Endpunkt fehlt.<br /><br /> Hinweis: Verwenden Sie `Set-SqlHadrEndpoint`, um einen vorhandenen Datenbankspiegelungs-Endpunkt zu ändern.|  
|Erstellen der Verfügbarkeitsgruppe|Verwenden Sie zuerst das `New-SqlAvailabilityReplica`-Cmdlet mit dem `-AsTemplate`-Parameter, um ein Verfügbarkeitsreplikatobjekt im Arbeitsspeicher für jedes der beiden Verfügbarkeitsreplikate zu erstellen, die Sie in die Verfügbarkeitsgruppe einschließen möchten.<br /><br /> Erstellen Sie dann die Verfügbarkeitsgruppe mithilfe des `New-SqlAvailabilityGroup`-Cmdlets, und verweisen Sie auf die Verfügbarkeitsreplikatobjekte.|Führen Sie diesen Task auf der Serverinstanz aus, auf der das anfängliche primäre Replikat gehostet werden soll.|  
|Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe|`Join-SqlAvailabilityGroup`|Führen Sie diesen Task auf jeder Serverinstanz aus, auf der ein sekundäres Replikat gehostet wird.|  
|Vorbereiten der sekundären Datenbank|
  `Backup-SqlDatabase` und `Restore-SqlDatabase`|Erstellen Sie Sicherungen auf der Serverinstanz, auf der das primäre Replikat gehostet wird.<br /><br /> Stellen Sie mit dem Wiederherstellungsparameter `NoRecovery` Sicherungen auf jeder Serverinstanz wieder her, auf der ein sekundäres Replikat gehostet wird. Wenn sich die Dateipfade zwischen den Computern unterscheiden, die das primäre Replikat und das sekundäre Zielreplikat hosten, verwenden Sie ebenfalls den Wiederherstellungsparameter `RelocateFile`.|  
|Starten der Datensynchronisierung durch Hinzufügen der einzelnen sekundären Datenbanken zur Verfügbarkeitsgruppe|`Add-SqlAvailabilityDatabase`|Führen Sie diesen Task auf jeder Serverinstanz aus, auf der ein sekundäres Replikat gehostet wird.|  
  
 **<sup>*</sup>** Um eine bestimmte Aufgabe auszuführen, ändern Sie das`cd`Verzeichnis () in die angegebene Serverinstanz bzw. die angegebenen Instanzen.  
  
###  <a name="PsProviderLinks"></a>So richten Sie den SQL Server PowerShell-Anbieter ein und verwenden ihn  
  
-   [SQL Server PowerShell Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Hilfe SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
##  <a name="PowerShellProcedure"></a>Verwenden von PowerShell zum Erstellen und Konfigurieren einer Verfügbarkeits Gruppe  
  
> [!NOTE]  
>  Um die Syntax und ein Beispiel für ein bestimmtes Cmdlet anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
1.  Wechseln Sie in das Verzeichnis (`cd`) der Serverinstanz, die das primäre Replikat hosten soll.  
  
2.  Erstellen Sie für das primäre Replikat ein Verfügbarkeitsreplikatobjekt im Arbeitsspeicher.  
  
3.  Erstellen Sie für jedes der sekundären Replikate ein Verfügbarkeitsreplikatobjekt im Arbeitsspeicher.  
  
4.  Erstellen Sie die Verfügbarkeitsgruppe.  
  
    > [!NOTE]  
    >  Die maximale Länge eines Verfügbarkeitsgruppennamens beträgt 128 Zeichen.  
  
5.  Verknüpfen Sie das neue sekundäre Replikat mit der Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
6.  Erstellen Sie für jede Datenbank in der Verfügbarkeitsgruppe eine sekundäre Datenbank, indem Sie letzte Sicherungen der primären Datenbank mit RESTORE WITH NORECOVERY wiederherstellen.  
  
7.  Verknüpfen Sie alle neuen sekundären Datenbanken mit der Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
8.  Verwenden Sie optional den `dir`-Befehl von Windows, um den Inhalt der neuen Verfügbarkeitsgruppe zu überprüfen.  
  
> [!NOTE]  
>  Wenn die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkonten der Serverinstanzen unter unterschiedlichen Domänenbenutzerkonten ausgeführt werden, erstellen Sie auf jeder Serverinstanz eine Anmeldung für die andere Serverinstanz, und gewähren Sie dieser Anmeldung eine CONNECT-Berechtigung zum Zugreifen auf den lokalen Datenbankspiegelungs-Endpunkt.  
  
##  <a name="ExampleConfigureGroup"></a>Beispiel: Verwenden von PowerShell zum Erstellen einer Verfügbarkeits Gruppe  
 Im folgenden PowerShell-Beispiel wird eine einfache Verfügbarkeitsgruppe mit dem Namen `MyAG` erstellt und konfiguriert, die über zwei Verfügbarkeitsreplikate und eine Verfügbarkeitsdatenbank verfügt. Beispiel:  
  
1.  Sichert `MyDatabase` und das dazugehörige Transaktionsprotokoll.  
  
2.  Stellt `MyDatabase` und das dazugehörige Transaktionsprotokoll mithilfe der Option `-NoRecovery` wieder her.  
  
3.  Erstellt eine speicherinterne Darstellung des primären Replikats, die von der lokalen Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (mit dem Namen `PrimaryComputer\Instance`) gehostet wird.  
  
4.  Erstellt eine speicherinterne Darstellung des sekundären Replikats, die von einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (mit dem Namen `SecondaryComputer\Instance`) gehostet wird.  
  
5.  Erstellt eine Verfügbarkeitsgruppe mit dem Namen `MyAG`.  
  
6.  Verknüpft das sekundäre Replikat mit der Verfügbarkeitsgruppe.  
  
7.  Verknüpft die sekundäre Datenbank mit der Verfügbarkeitsgruppe.  
  
```powershell
# Backup my database and its log on the primary  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "PrimaryComputer\Instance"  
  
Backup-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "PrimaryComputer\Instance" `  
    -BackupAction Log   
  
# Restore the database and log on the secondary (using NO RECOVERY)  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.bak" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -NoRecovery  
  
Restore-SqlDatabase `  
    -Database "MyDatabase" `  
    -BackupFile "\\share\backups\MyDatabase.log" `  
    -ServerInstance "SecondaryComputer\Instance" `  
    -RestoreAction Log `  
    -NoRecovery  
  
# Create an in-memory representation of the primary replica.  
$primaryReplica = New-SqlAvailabilityReplica `  
    -Name "PrimaryComputer\Instance" `  
    -EndpointURL "TCP://PrimaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create an in-memory representation of the secondary replica.  
$secondaryReplica = New-SqlAvailabilityReplica `  
    -Name "SecondaryComputer\Instance" `  
    -EndpointURL "TCP://SecondaryComputer.domain.com:5022" `  
    -AvailabilityMode "SynchronousCommit" `  
    -FailoverMode "Automatic" `  
    -Version 12 `  
    -AsTemplate  
  
# Create the availability group  
New-SqlAvailabilityGroup `  
    -Name "MyAG" `  
    -Path "SQLSERVER:\SQL\PrimaryComputer\Instance" `  
    -AvailabilityReplica @($primaryReplica,$secondaryReplica) `  
    -Database "MyDatabase"  
  
# Join the secondary replica to the availability group.  
Join-SqlAvailabilityGroup -Path "SQLSERVER:\SQL\SecondaryComputer\Instance" -Name "MyAG"  
  
# Join the secondary database to the availability group.  
Add-SqlAvailabilityDatabase -Path "SQLSERVER:\SQL\SecondaryComputer\Instance\AvailabilityGroups\MyAG" -Database "MyDatabase"  
```  
  
##  <a name="RelatedTasks"></a>Verwandte Aufgaben  
 **So konfigurieren Sie eine Serverinstanz für AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Aktivieren und deaktivieren Sie AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [Erstellen Sie einen Datenbankspiegelungs-Endpunkt für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
 **So konfigurieren Sie Verfügbarkeits Gruppen-und Replikat Eigenschaften**  
  
-   [Ändern des Verfügbarkeits Modus eines Verfügbarkeits Replikats &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Ändern des Failovermodus eines Verfügbarkeits Replikats &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Erstellen oder konfigurieren Sie einen verfügbarkeitsgruppenlistener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Konfigurieren der flexiblen Failoverrichtlinie zum Steuern der Bedingungen für ein automatisches Failover (AlwaysOn-Verfügbarkeitsgruppen)](configure-flexible-automatic-failover-policy.md)  
  
-   [Geben Sie die Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeits Replikat &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeits Replikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Konfigurieren Sie den schreibgeschützten Zugriff auf ein Verfügbarkeits Replikat &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Konfigurieren Sie das schreibgeschützte Routing für eine Verfügbarkeits Gruppe &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Ändern des Sitzungs Timeouts für ein Verfügbarkeits Replikat &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **So vervollständigen Sie die Verfügbarkeits Gruppenkonfiguration**  
  
-   [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeits Gruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeits Gruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeits Gruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Erstellen oder konfigurieren Sie einen verfügbarkeitsgruppenlistener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Alternative Möglichkeiten zum Erstellen einer Verfügbarkeits Gruppe**  
  
-   [Verwenden Sie den Verfügbarkeits Gruppen-Assistenten &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden Sie das Dialog Feld neue Verfügbarkeits Gruppe &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Erstellen einer Verfügbarkeits Gruppe &#40;Transact-SQL-&#41;](create-an-availability-group-transact-sql.md)  
  
 **Problembehandlung für die AlwaysOn-Verfügbarkeitsgruppenkonfiguration**  
  
-   [Problembehandlung AlwaysOn-Verfügbarkeitsgruppen Konfiguration (SQL Server) gelöscht](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Problembehandlung bei einem fehlgeschlagenen Vorgang zum Hinzufügen einer Datei &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a>Verwandte Inhalte  
  
-   **Gt**  
  
     [AlwaysON - HADRON-Lernreihe: Nutzung des Arbeitsthreadpools für HADRON-fähige Datenbanken](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Konfigurieren von AlwaysOn mit SQL Server PowerShell](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/03/configuring-alwayson-with-sql-server-powershell.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blog zu CSS-SQL Server Technikern](https://blogs.msdn.com/b/psssql/)  
  
-   **Videos**  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 1: Einführung in die nächste Generation von Lösungen mit hoher Verfügbarkeit](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Codename "Denali" AlwaysOn-Reihe, Teil 2: Erstellen einer unternehmenswichtigen Lösung für hohe Verfügbarkeit mit AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Whitepaper**  
  
     [Microsoft SQL Server AlwaysOn-Lösungshandbuch zu hoher Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Microsoft-Whitepaper für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepaper SQL Server Kundenberatungs Teams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
