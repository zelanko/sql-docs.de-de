---
title: Konfigurieren des schreibgeschützten Routing für eine Verfügbarkeitsgruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- read-only routing
- Availability Groups [SQL Server], readable secondary replicas
- Availability Groups [SQL Server], read-only routing
- readable secondary replicas
- Availability Groups [SQL Server], client connectivity
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 7bd89ddd-0403-4930-a5eb-3c78718533d4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a129386b5c88939d68f5d7f23a5fe2b4d8ce7cca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62789530"
---
# <a name="configure-read-only-routing-for-an-availability-group-sql-server"></a>Konfigurieren des schreibgeschützten Routing für eine Verfügbarkeitsgruppe (SQL Server)
  In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]können Sie eine AlwaysOn-Verfügbarkeitsgruppe mit [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder mit PowerShell für schreibgeschütztes Routing konfigurieren. *Schreibgeschütztes Routing* bezeichnet die Fähigkeit von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], schreibgeschützte Verbindungsanforderungen an ein verfügbares [lesbares sekundäres AlwaysOn-Replikat](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) weiterzuleiten (das heißt, an ein Replikat, das unter der sekundären Rolle für schreibgeschützte Arbeitsauslastungen konfiguriert ist). Um schreibgeschütztes Routing zu unterstützen, muss die Verfügbarkeitsgruppe einen [Verfügbarkeitsgruppenlistener](../../listeners-client-connectivity-application-failover.md) besitzen. Schreibgeschützte Clients müssen die eigenen Verbindungsanforderungen an diesen Listener weiterleiten, und in den Verbindungszeichenfolgen des Clients muss die Anwendungsabsicht als "schreibgeschützt" angeben sein. Es muss sich also um *Verbindungsanforderungen für beabsichtigte Lesevorgänge*handeln.  
  
> [!NOTE]
>  Informationen zum Konfigurieren eines lesbaren sekundären Replikats finden Sie unter [Konfigurieren des schreibgeschützten Zugriffs auf ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)besitzen.  
> 
> 
> 
> [!NOTE]
>  Die Konfiguration von schreibgeschütztem Routing wird von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]nicht unterstützt.  
  

  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Die Verfügbarkeitsgruppe muss über einen Verfügbarkeitsgruppenlistener verfügen. Weitere Informationen finden Sie unter [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).  
  
-   Eine oder mehrere Replikate der verfügbarkeitsgruppe müssen so konfiguriert werden, dass in der sekundären Rolle schreibgeschützte Verbindungen akzeptiert (d. h. sein [lesbare sekundäre Replikate](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)(AlwaysOn-% 20Availability % 20Groups\).md)). Weitere Informationen finden Sie unter [Konfigurieren des schreibgeschützten Zugriffs auf ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md).  
  
-   Sie müssen mit der Serverinstanz verbunden sein, auf der das aktuelle primäre Replikat gehostet wird.  
  
###  <a name="RORReplicaProperties"></a> Welche Replikateigenschaften müssen Sie konfigurieren, um schreibgeschütztes Routing zu unterstützen?  
  
-   Für jedes lesbare sekundäre Replikat, das schreibgeschütztes Routing unterstützen soll, müssen Sie eine *URL für schreibgeschütztes Routing*angeben. Diese URL wird nur wirksam, wenn das lokale Replikat unter der sekundären Rolle ausgeführt wird. Die URL für schreibgeschütztes Routing muss nach Bedarf replikatweise angegeben werden. Jede URL für schreibgeschütztes Routing wird zum Weiterleiten von Verbindungsanforderungen für beabsichtigte Lesevorgänge an ein bestimmtes lesbares sekundäres Replikat verwendet. In der Regel wird jedem lesbaren sekundären Replikat eine URL für schreibgeschütztes Routing zugewiesen.  
  
     Informationen zum Berechnen der schreibgeschützten Routing-URL für ein Verfügbarkeitsreplikat finden Sie unter [Berechnen von read_only_routing_url für AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
-   Für jedes Verfügbarkeitsreplikat, das als primäres Replikat schreibgeschütztes Routing unterstützen soll, müssen Sie eine *Liste für schreibgeschütztes Routing* angeben. Eine Liste für schreibgeschütztes Routing wird nur wirksam, wenn das lokale Replikat unter der primären Rolle ausgeführt wird. Diese Liste muss nach Bedarf replikatweise angegeben werden. Normalerweise enthält jede Liste für schreibgeschütztes Routing jede URL für schreibgeschütztes Routing, wobei die URL des lokalen Replikats am Ende der Liste steht.  
  
    > [!NOTE]  
    >  Verbindungsanforderungen für beabsichtigte Lesevorgänge werden an das erste verfügbare lesbare sekundäre Replikat auf der Liste für schreibgeschütztes Routing des aktuellen primären Replikats weitergeleitet. Es erfolgt kein Lastenausgleich.  
  
> [!NOTE]  
>  Weitere Informationen zu Verfügbarkeitsgruppenlistenern und zum schreibgeschützten Routing finden Sie unter [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)besitzen.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
  
|Aufgabe|Berechtigungen|  
|----------|-----------------|  
|So konfigurieren Sie Replikate beim Erstellen einer Verfügbarkeitsgruppe|Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** und die CREATE AVAILABILITY GROUP-Serverberechtigung, ALTER ANY AVAILABILITY GROUP-Berechtigung oder CONTROL SERVER-Berechtigung.|  
|So ändern Sie ein Verfügbarkeitsreplikat|Erfordert die ALTER AVAILABILITY GROUP-Berechtigung für die Verfügbarkeitsgruppe, die CONTROL AVAILABILITY GROUP-Berechtigung, die ALTER ANY AVAILABILITY GROUP-Berechtigung oder die CONTROL SERVER-Berechtigung.|  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **Konfigurieren des schreibgeschützten Routings**  
  
> [!NOTE]  
>  Ein Codebeispiel finden Sie weiter unten in diesem Abschnitt unter [Beispiel (Transact-SQL)](#TsqlExample).  
  
1.  Stellen Sie eine Verbindung mit der Serverinstanz her, die das primäre Replikat hostet.  
  
2.  Wenn Sie ein Replikat für eine neue Verfügbarkeitsgruppe angeben, verwenden Sie die [-Anweisung](/sql/t-sql/statements/create-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] . Verwenden Sie zum Hinzufügen oder Ändern eines Replikats für eine vorhandene Verfügbarkeitsgruppe die [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql)[!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung.  
  
    -   Geben Sie zum Konfigurieren des schreibgeschützten Routings für die sekundäre Rolle in der ADD REPLICA- bzw. MODIFY REPLICA WITH-Klausel die SECONDARY_ROLE-Option wie folgt an:  
  
         SECONDARY_ROLE **(** READ_ONLY_ROUTING_URL **='** TCP **:// *`system-address`* : *`port`* ")**  
  
         Die URL für das schreibgeschützte Routing verfügt über die folgenden Parameter:  
  
         *system-address*  
         Ist eine Zeichenfolge, beispielsweise ein Systemname, ein vollqualifizierter Domänenname oder eine IP-Adresse, die das Zielcomputersystem eindeutig identifiziert.  
  
         *port*  
         Ist eine Portnummer, die von der Datenbank-Engine der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz verwendet wird.  
  
         Beispiel:   `SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433')`  
  
         In einer MODIFY REPLICA-Klausel ist ALLOW_CONNECTIONS optional, wenn das Replikat bereits so konfiguriert worden ist, dass es schreibgeschützte Verbindungen zulässt.  
  
         Weitere Informationen finden Sie unter [Berechnen von read_only_routing_url für AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
    -   Geben Sie zum Konfigurieren des schreibgeschützten Routings für die primäre Rolle in der ADD REPLICA- bzw. MODIFY REPLICA WITH-Klausel die PRIMARY_ROLE-Option wie folgt an:  
  
         PRIMARY_ROLE **(** READ_ONLY_ROUTING_LIST **= (" *`server`* "** [ **,** ... *n* ] **))**  
  
         wobei *server* eine Serverinstanz identifiziert, die ein schreibgeschütztes sekundäres Replikat in der Verfügbarkeitsgruppe hostet.  
  
         Beispiel:   `PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('Server1','Server2'))`  
  
        > [!NOTE]  
        >  Sie müssen die URL für das schreibgeschützte Routing festlegen, bevor Sie die schreibgeschützte Routingliste festlegen.  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 Im folgenden Beispiel werden zwei Verfügbarkeitsreplikate einer vorhandenen Verfügbarkeitsgruppe `AG1` geändert, sodass schreibgeschütztes Routing unterstützt wird, wenn eines dieser Replikate die primäre Rolle besitzt. In diesem Beispiel werden die Instanznamen `COMPUTER01` und `COMPUTER02` zur Identifikation der Serverinstanzen angegeben, die das Verfügbarkeitsreplikat hosten.  
  
```  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER01.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY));  
ALTER AVAILABILITY GROUP [AG1]  
 MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(SECONDARY_ROLE (READ_ONLY_ROUTING_URL = N'TCP://COMPUTER02.contoso.com:1433'));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER01' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER02','COMPUTER01')));  
  
ALTER AVAILABILITY GROUP [AG1]   
MODIFY REPLICA ON  
N'COMPUTER02' WITH   
(PRIMARY_ROLE (READ_ONLY_ROUTING_LIST=('COMPUTER01','COMPUTER02')));  
GO  
  
```  
  
##  <a name="PowerShellProcedure"></a> PowerShell  
 **Konfigurieren des schreibgeschützten Routings**  
  
> [!NOTE]  
>  Ein Codebeispiel finden Sie weiter unten in diesem Abschnitt unter [Beispiel (PowerShell)](#PSExample).  
  
1.  Legen Sie den Standard (`cd`) auf die Serverinstanz fest, auf der das primäre Replikat gehostet wird.  
  
2.  Wenn Sie einer Verfügbarkeitsgruppe ein Verfügbarkeitsreplikat hinzufügen, verwenden Sie das `New-SqlAvailabilityReplica`-Cmdlet. Wenn Sie ein vorhandenes Verfügbarkeitsreplikat ändern, verwenden Sie das `Set-SqlAvailabilityReplica`-Cmdlet. Die relevanten Parameter lauten wie folgt:  
  
    -   Um schreibgeschütztes routing für die sekundäre Rolle zu konfigurieren, geben die **ReadonlyRoutingConnectionUrl " *`url`* "** Parameter.  
  
         wobei *url* für den vollqualifizierten Domänennamen (FQDN) und Port der Verbindung steht, die beim Routing zum Replikat für schreibgeschützte Verbindungen verwendet werden. Beispiel:  `-ReadonlyRoutingConnectionUrl "TCP://DBSERVER8.manufacturing.Adventure-Works.com:7024"`  
  
         Weitere Informationen finden Sie unter [Berechnen von read_only_routing_url für AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx).  
  
    -   Um Verbindungszugriff für die primäre Rolle zu konfigurieren, geben **ReadonlyRoutingList " *`server`* "** [ **,** ... *n* ], wobei *Server* identifiziert eine Serverinstanz, die ein schreibgeschützten sekundäres Replikat in der verfügbarkeitsgruppe hostet. Beispiel:  `-ReadOnlyRoutingList "SecondaryServer","PrimaryServer"`  
  
        > [!NOTE]  
        >  Sie müssen die URL für das schreibgeschützte Routing für ein Replikat festlegen, bevor Sie dessen schreibgeschützte Routingliste festlegen.  
  
    > [!NOTE]  
    >  Um die Syntax eines Cmdlets anzuzeigen, verwenden Sie das `Get-Help`-Cmdlet in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell-Umgebung. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Einrichten und Verwenden des SQL Server PowerShell-Anbieters**  
  
-   [SQL Server PowerShell-Anbieter](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
###  <a name="PSExample"></a> Beispiel (PowerShell)  
 Im folgenden Beispiel werden das primäre Replikat und ein sekundäres Replikat in einer Verfügbarkeitsgruppe für das schreibgeschützte Routing konfiguriert. Im Beispiel wird zuerst jedem Replikat eine URL für das schreibgeschützte Routing zugewiesen. Anschließend wird die Liste für schreibgeschütztes Routing auf dem primären Replikat festgelegt. Verbindungen, für die in der Verbindungszeichenfolge die ReadOnly-Eigenschaft festgelegt wurde, werden an das sekundäre Replikat umgeleitet. Wenn vom sekundären Replikat nicht gelesen werden kann (durch die `ConnectionModeInSecondaryRole`-Einstellung vorgegeben), wird die Verbindung wiederum zurück an das primäre Replikat geleitet.  
  
```  
Set-Location SQLSERVER:\SQL\PrimaryServer\default\AvailabilityGroups\MyAg  
$primaryReplica = Get-Item "AvailabilityReplicas\PrimaryServer"  
$secondaryReplica = Get-Item "AvailabilityReplicas\SecondaryServer"  
  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://PrimaryServer.domain.com:1433" -InputObject $primaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingConnectionUrl "TCP://SecondaryServer.domain.com:1433" -InputObject $secondaryReplica  
Set-SqlAvailabilityReplica -ReadOnlyRoutingList "SecondaryServer","PrimaryServer" -InputObject $primaryReplica  
```  
  
##  <a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren von schreibgeschütztem Routing  
 Sobald das aktuelle primäre Replikat und die lesbaren sekundären Replikate konfiguriert worden sind, sodass sie schreibgeschütztes Routing in beiden Rollen unterstützen, können die lesbaren sekundären Replikate Anforderungen für Leseverbindungen von Clients empfangen, die über den Verfügbarkeitsgruppenlistener eine Verbindung herstellen.  
  
> [!TIP]  
>  Bei Verwendung der [Hilfsprogramm "Bcp"](../../../tools/bcp-utility.md) oder [Hilfsprogramms "Sqlcmd"](../../../tools/sqlcmd-utility.md), können Sie schreibgeschützten Zugriff für jedes sekundäre Replikat, das aktiviert ist, für den schreibgeschützten Zugriff angeben, durch Angabe der `-K ReadOnly` wechseln.  
  
###  <a name="ConnStringReqsRecs"></a> Anforderungen und Empfehlungen für Clientverbindungszeichenfolgen  
 Damit eine Clientanwendung schreibgeschütztes Routing verwendet, muss seine Verbindungszeichenfolge die folgenden Anforderungen erfüllen:  
  
-   Verwendung des TCP-Protokolls.  
  
-   Festlegen des Attributs bzw. der Eigenschaft für die Anwendungsabsicht auf schreibgeschützt  
  
-   Verweis auf den Listener einer Verfügbarkeitsgruppe, der zur Unterstützung des schreibgeschützten Routing konfiguriert worden ist.  
  
-   Verweis auf eine Datenbank in dieser Verfügbarkeitsgruppennamen.  
  
 Außerdem empfiehlt es sich, dass Verbindungszeichenfolgen Multisubnetzfailover aktivieren, das in jedem Subnetz einen parallelen Clientthread für jedes Replikat unterstützt. Dadurch wird die Zeitspanne minimiert, die nach einem Failover zum Wiederherstellen der Verbindung mit dem Client erforderlich ist.  
  
 Die Syntax für eine Verbindungszeichenfolge hängt vom SQL Server-Anbieter ab, den eine Anwendung verwendet. Die folgende Beispielverbindungszeichenfolge für den .NET Framework-Datenanbieter 4.0.2 für SQL Server veranschaulicht die Teile einer Verbindungszeichenfolge, die für schreibgeschütztes Routing erforderlich und empfohlen sind.  
  
```  
Server=tcp:MyAgListener,1433;Database=Db1;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly;MultiSubnetFailover=True  
```  
  
 Weitere Informationen zur schreibgeschützten Anwendungsabsicht und zum schreibgeschützten Routing finden Sie unter [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)besitzen.  
  
### <a name="if-read-only-routing-is-not-working-correctly"></a>Wenn schreibgeschütztes Routing nicht ordnungsgemäß funktioniert  
 Informationen zum Durchführen einer Problembehandlung an einer schreibgeschützten Routingkonfiguration finden Sie unter [Schreibgeschütztes Routing funktioniert nicht ordnungsgemäß](troubleshoot-always-on-availability-groups-configuration-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So zeigen Sie schreibgeschützte Routingkonfigurationen an**  
  
-   [sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)  
  
-   [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) (**read_only_routing_url**-Spalte)  
  
 **So konfigurieren Sie den Clientverbindungszugriff**  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Konfigurieren des schreibgeschützten Zugriffs auf ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
 **So verwenden Sie Verbindungszeichenfolgen in Anwendungen**  
  
-   [SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   **Blogs:**  
  
     [Berechnen von Read_only_routing_url für AlwaysOn](https://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-alwayson.aspx)  
  
     [SQL Server AlwaysOn-Teamblogs: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server-Technikblogs](https://blogs.msdn.com/b/psssql/)  
  
-   **Whitepaper:**  
  
     [Microsoft-Whitepapers für SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Whitepapers des SQL Server-Kundenberatungsteams](http://sqlcat.com/)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Aktive sekundäre Replikate: Lesbare sekundäre Replikate (AlwaysOn-Verfügbarkeitsgruppen)](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Informationen zum Clientverbindungszugriff auf Verfügbarkeitsreplikate &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)  
  
  
