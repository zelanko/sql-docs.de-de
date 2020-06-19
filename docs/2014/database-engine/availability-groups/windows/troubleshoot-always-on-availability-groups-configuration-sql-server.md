---
title: Problembehandlung AlwaysOn-Verfügbarkeitsgruppen Konfiguration (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [SQL Server], deploying
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], configuring
ms.assetid: 8c222f98-7392-4faf-b7ad-5fb60ffa237e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 165036ba539c3392b1944282bd9d6126eb471a97
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936341"
---
# <a name="troubleshoot-alwayson-availability-groups-configuration-sql-server"></a>Problembehandlung für die AlwaysOn-Verfügbarkeitsgruppenkonfiguration (SQL Server)
  Dieses Thema enthält Informationen, um Sie beim Beheben typischer Probleme beim Konfigurieren von Serverinstanzen für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]zu unterstützen. Typische Konfigurationsprobleme: [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ist deaktiviert, Konten werden falsch konfiguriert, der Datenbankspiegelungs-Endpunkt ist nicht vorhanden, auf den Endpunkt kann nicht zugegriffen werden (SQL Server-Fehler 1418), Netzwerkzugriff ist nicht vorhanden und der Befehl zum Verknüpfen der Datenbank schlägt fehl (SQL Server-Fehler 35250).

> [!NOTE]
>  Stellen Sie sicher, dass die [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Voraussetzungen erfüllt sind. Weitere Informationen finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).

 **In diesem Thema:**

|`Section`|BESCHREIBUNG|
|-------------|-----------------|
|[AlwaysOn-Verfügbarkeitsgruppen sind nicht aktiviert](#IsHadrEnabled)|Wenn eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nicht für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]aktiviert ist, wird von der Instanz die Verfügbarkeitsgruppenerstellung nicht unterstützt. Es können außerdem keine Verfügbarkeitsreplikate gehostet werden.|
|[Konten](#Accounts)|Erläutert die Anforderungen für eine ordnungsgemäße Konfiguration der Konten, unter denen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird.|
|[Endpunkte](#Endpoints)|Erläutert, wie Probleme mit dem Datenbankspiegelungs-Endpunkt einer Serverinstanz diagnostiziert werden.|
|[System Name](#SystemName)|Fasst die Alternativen zum Angeben des Systemnamens einer Serverinstanz in einer Endpunkt-URL zusammen.|
|[Netzwerkzugriff](#NetworkAccess)|Dokumentiert die Anforderung, dass jeder Serverinstanz, die ein Verfügbarkeitsreplikat hostet, der Zugriff auf den Port aller anderen Serverinstanzen über TCP ermöglicht werden muss.|
|[Endpunktzugriff (SQL Server-Fehler 1418)](#Msg1418)|Enthält Informationen zu dieser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Fehlermeldung.|
|[Fehler beim Verknüpfen der Datenbank (SQL Server Fehler 35250)](#JoinDbFails)|Erläutert die möglichen Ursachen und die Lösung des Fehlers beim Verknüpfen von sekundären Datenbanken mit einer Verfügbarkeitsgruppe aufgrund einer inaktiven Verbindung mit dem primären Replikat.|
|[Schreibgeschütztes Routing funktioniert nicht ordnungsgemäß](#ROR)||
|[Verwandte Aufgaben](#RelatedTasks)|Enthält eine Liste aufgabenbezogener Themen in der [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] -Onlinedokumentation, die besonders relevant für die Problembehandlung an einer Verfügbarkeitsgruppenkonfiguration sind.|
|[Verwandte Inhalte](#RelatedContent)|Enthält eine Liste von relevanten Ressourcen außerhalb der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Onlinedokumentation.|

##  <a name="alwayson-availability-groups-is-not-enabled"></a><a name="IsHadrEnabled"></a>AlwaysOn-Verfügbarkeitsgruppen ist nicht aktiviert.
 Die Funktion [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] muss auf allen Instanzen von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]aktiviert werden. Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).

##  <a name="accounts"></a><a name="Accounts"></a>Buchhaltungs
 Die Konten, unter denen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, müssen ordnungsgemäß konfiguriert sein.

1.  Verfügen die Konten über die richtigen Berechtigungen?

    1.  Falls die Partner unter demselben Domänenbenutzerkonto ausgeführt werden, sind die richtigen Benutzeranmeldenamen automatisch in beiden **master** -Datenbanken vorhanden. Dadurch wird die Sicherheitskonfiguration der Datenbank vereinfacht und wird somit empfohlen.

    2.  Wenn zwei Serverinstanzen als unterschiedliche Konten ausgeführt werden, muss die Anmeldung für die Konten in **master** auf der Remoteserverinstanz erstellt werden, und dieser Anmeldung müssen CONNECT-Berechtigungen gewährt werden, damit eine Verbindung mit dem Datenbankspiegelungs-Endpunkt dieser Serverinstanz hergestellt werden kann. Weitere Informationen finden Sie unter[Einrichten von Anmeldekonten für die Daten Bank Spiegelung oder AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md).

2.  Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als integriertes Konto, z. B. Lokales System, Lokaler Dienst oder Netzwerkdienst, oder als Nicht-Domänenkonto ausgeführt wird, müssen Sie Zertifikate zur Endpunktauthentifizierung verwenden. Wenn die Dienstkonten Domänenkonten in derselben Domäne verwenden, können Sie CONNECT-Zugriff für jedes Dienstkonto an allen Replikatspeicherorten gewähren oder Zertifikate verwenden. Weitere Informationen finden Sie unter [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt (Transact-SQL)](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).

##  <a name="endpoints"></a><a name="Endpoints"></a> Endpunkte
 Endpunkte müssen ordnungsgemäß konfiguriert sein.

1.  Stellen Sie sicher, dass jede Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die ein Verfügbarkeitsreplikat hosten wird (jeder *Replikatspeicherort*) einen Datenbankspiegelungs-Endpunkt besitzt. Um festzustellen, ob auf einer bestimmten Serverinstanz bereits ein Datenbankspiegelungs-Endpunkt vorhanden ist, verwenden Sie die Katalogsicht [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) . Weitere Informationen finden Sie unter [Create a Database Mirroring Endpoint for Windows Authentication (Transact-SQL) (Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung (Transact-SQL))](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) oder [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections (Transact-SQL) (Ermöglichen des Verwendens von Zertifikaten für ausgehende Verbindungen für einen Datenbankspiegelungs-Endpunkt (Transact-SQL))](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md).

2.  Überprüfen Sie, ob die Portnummern richtig sind.

     Verwenden Sie die folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung, um den Port zu identifizieren, der derzeit dem Endpunkt der Datenbankspiegelung einer Serverinstanz zugeordnet ist:

    ```
    SELECT type_desc, port FROM sys.tcp_endpoints;
    GO
    ```

3.  Bei Problemen mit der Einrichtung von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , die schwer zu erklären sind, empfiehlt es sich, jede Serverinstanz zu prüfen, um zu ermitteln, ob von der Serverinstanz die richtigen Ports überwacht werden. Informationen zum Überprüfen der Verfügbarkeit von Ports finden Sie unter [MSSQLSERVER_1418](../../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).

4.  Stellen Sie sicher, dass die Endpunkte gestartet wurden (STATE=STARTED). Verwenden Sie auf jeder Serverinstanz folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung:

    ```
    SELECT state_desc FROM sys.database_mirroring_endpoints
    ```

     Weitere Informationen zur **state_desc**-Spalte finden Sie unter [database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).

     Verwenden Sie die folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung, um einen Endpunkt zu starten:

    ```
    ALTER ENDPOINT Endpoint_Mirroring 
    STATE = STARTED 
    AS TCP (LISTENER_PORT = <port_number>)
    FOR database_mirroring (ROLE = ALL);
    GO
    ```

     Weitere Informationen finden Sie unter [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).

5.  Stellen Sie sicher, dass der Anmeldename auf dem anderen Server über CONNECT-Berechtigungen verfügt. Führen Sie auf jeder Serverinstanz die folgende [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung aus, um zu ermitteln, wer über CONNECT-Berechtigungen für einen Endpunkt verfügt:

    ```
    SELECT 'Metadata Check';
    SELECT EP.name, SP.STATE, 
       CONVERT(nvarchar(38), suser_name(SP.grantor_principal_id)) 
          AS GRANTOR, 
       SP.TYPE AS PERMISSION,
       CONVERT(nvarchar(46),suser_name(SP.grantee_principal_id)) 
          AS GRANTEE 
       FROM sys.server_permissions SP , sys.endpoints EP
       WHERE SP.major_id = EP.endpoint_id
       ORDER BY Permission,grantor, grantee; 
    GO

    ```

##  <a name="system-name"></a><a name="SystemName"></a> System Name
 Für den Systemnamen einer Serverinstanz in einer Endpunkt-URL können Sie jeden beliebigen Namen verwenden, der das System eindeutig bezeichnet. Die Serveradresse kann ein Systemname sein (wenn sich die Systeme in derselben Domäne befinden), ein vollqualifizierter Domänenname oder eine IP-Adresse (vorzugsweise eine statische IP-Adresse). Bei Verwendung des vollqualifizierten Domänennamens ist eine problemfreie Funktionsweise sichergestellt. Weitere Informationen finden Sie unter [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)zu unterstützen.

##  <a name="network-access"></a><a name="NetworkAccess"></a> Network Access
 Jeder Serverinstanz, die ein Verfügbarkeitsreplikat hostet, muss der Zugriff auf den Port aller anderen Serverinstanzen über TCP ermöglicht werden. Dies ist insbesondere von Bedeutung, wenn sich die Serverinstanzen in unterschiedlichen Domänen befinden, die sich nicht vertrauen (nicht vertrauenswürdige Domänen).

##  <a name="endpoint-access-sql-server-error-1418"></a><a name="Msg1418"></a> Endpunktzugriff (SQL Server-Fehler 1418)
 In dieser Meldung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird angegeben, dass die in der Endpunkt-URL angegebene Servernetzwerkadresse nicht erreicht werden kann oder nicht vorhanden ist. Es wird vorgeschlagen, den Namen der Netzwerkadresse zu überprüfen und den Befehl erneut auszugeben. Weitere Informationen finden Sie unter [MSSQLSERVER_1418](../../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).

##  <a name="join-database-fails-sql-server-error-35250"></a><a name="JoinDbFails"></a> Fehler beim Verknüpfen der Datenbank (SQL Server-Fehler 35250)
 Dieser Abschnitt erläutert die möglichen Ursachen und die Lösung des Fehlers beim Verknüpfen von sekundären Datenbanken mit einer Verfügbarkeitsgruppe aufgrund einer inaktiven Verbindung mit dem primären Replikat.

 **Lösung:**

1.  Überprüfen Sie die Firewalleinstellung, um zu ermitteln, ob die Endpunktportkommunikation zwischen den Serverinstanzen, auf denen das primäre Replikat gehostet wird, und dem sekundären Replikat (standardmäßig Port 5022) möglich ist.

2.  Überprüfen Sie, ob das Netzwerkdienstkonto über Verbindungsberechtigung für den Endpunkt verfügt.

##  <a name="read-only-routing-is-not-working-correctly"></a><a name="ROR"></a>Schreib geschütztes Routing funktioniert nicht ordnungsgemäß
 Überprüfen Sie die folgenden Konfigurationswerteinstellungen und korrigieren Sie sie gegebenenfalls.

||Am...|Aktion|Kommentare|Link|
|------|---------|------------|--------------|----------|
|![Markieren](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|dem aktuellen primären Replikat|Stellen Sie sicher, dass der Listener der Verfügbarkeitsgruppe online ist.|**So überprüfen Sie, ob der Listener online ist:**<br /><br /> `SELECT * FROM sys.dm_tcp_listener_states;`<br /><br /> **So starten Sie einen Offlinelistener neu:**<br /><br /> `ALTER AVAILABILITY GROUP myAG RESTART LISTENER 'myAG_Listener';`|[sys.dm_tcp_listener_states &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)<br /><br /> [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)|
|![Markieren](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|dem aktuellen primären Replikat|Stellen Sie sicher, dass READ_ONLY_ROUTING_LIST nur Serverinstanzen enthält, die ein lesbares sekundäres Replikat hosten.|**So identifizieren Sie lesbare sekundäre Replikate:** sys.availability_replicas (Spalte**econdary_role_allow_connections_desc** )<br /><br /> **So zeigen Sie eine schreibgeschützte Routingliste an:** sys.availability_read_only_routing_lists<br /><br /> **So ändern Sie eine schreibgeschützte Routingliste:** ALTER AVAILABILITY GROUP|[sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)<br /><br /> [sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)<br /><br /> [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)|
|![Markieren](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|jedem Replikat in read_only_routing_list|Stellen Sie sicher, dass die Windows-Firewall den Port READ_ONLY_ROUTING_URL nicht blockiert.|-|[Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../configure-windows/configure-a-windows-firewall-for-database-engine-access.md)|
|![Markieren](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|jedem Replikat in read_only_routing_list|Überprüfen Sie in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager die folgenden Aspekte:<br /><br /> SQL Server-Remoteverbindung ist aktiviert.<br /><br /> TCP/IP ist aktiviert.<br /><br /> Die IP-Adressen sind ordnungsgemäß konfiguriert.|-|[Anzeigen oder Ändern von Servereigenschaften &#40;SQL Server&#41;](../../configure-windows/view-or-change-server-properties-sql-server.md)<br /><br /> [Konfigurieren eines Servers zur Überwachung eines bestimmten TCP-Ports &#40;SQL Server-Konfigurations-Manager&#41;](../../configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)|
|![Markieren](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|jedem Replikat in read_only_routing_list|Stellen Sie sicher, dass die READ_ONLY_ROUTING_URL (TCP<strong>:// *`system-address`* :</strong>*Port*) den richtigen voll qualifizierten Domänen Namen (FQDN) und die richtige Portnummer enthält.|-|[Berechnen von read_only_routing_url für AlwaysOn](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)<br /><br /> [sys.availability_replicas &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)<br /><br /> [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)|
|![Markieren](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")|Clientsystem|Überprüfen Sie, ob der Clienttreiber schreibgeschütztes Routing unterstützt.|-|[AlwaysOn-Clientkonnektivität (SQL Server)](always-on-client-connectivity-sql-server.md)|

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben

-   [Erstellung und Konfiguration von Verfügbarkeitsgruppen &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)

-   [Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)

-   [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)

-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)

-   [Problembehandlung bei einem fehlgeschlagenen Vorgang zum Hinzufügen einer Datei &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)

-   [Verwaltung von Anmeldungen und Aufträgen für die Datenbanken einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../logins-and-jobs-for-availability-group-databases.md)

-   [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](../../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)

##  <a name="related-content"></a><a name="RelatedContent"></a> Verwandte Inhalte

-   [Anzeigen von Ereignissen und Protokollen für einen Failovercluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)

-   [Get-ClusterLog-Failovercluster-Cmdlet](https://technet.microsoft.com/library/ee461045.aspx)

-   [SQL Server AlwaysOn-Teamblog: Der offizielle SQL Server AlwaysOn-Teamblog](https://blogs.msdn.com/b/sqlalwayson/)

## <a name="see-also"></a>Weitere Informationen
 [Transport Sicherheit für Daten Bank Spiegelung und AlwaysOn-Verfügbarkeitsgruppen &#40;&#41;SQL Server](../../database-mirroring/transport-security-database-mirroring-always-on-availability.md) [Client Network Configuration](../../configure-windows/client-network-configuration.md) [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;](prereqs-restrictions-recommendations-always-on-availability.md) SQL Server&#41;


