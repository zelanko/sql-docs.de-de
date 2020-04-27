---
title: Verwaltung von Anmeldungen und Aufträgen für die Datenbanken einer Verfügbarkeits Gruppe (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: d7da14d3-848c-44d4-8e49-d536a1158a61
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a19d5d39a3133ffc664f5ea7050645e2a28a8a20
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774282"
---
# <a name="management-of-logins-and-jobs-for-the-databases-of-an-availability-group-sql-server"></a>Verwaltung von Anmeldungen und Aufträgen für die Datenbanken einer Verfügbarkeitsgruppe (SQL Server)
  Sie sollten routinemäßig den gleichen Satz von Benutzeranmeldungen und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agentaufträgen auf jeder primären Datenbank einer AlwaysOn-Verfügbarkeitsgruppe und den entsprechenden sekundären Datenbanken beibehalten. Die Anmeldungen und die Aufträge müssen auf jeder Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] reproduziert werden, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hostet.  
  
-   **[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Agentaufträge**  
  
     Sie müssen relevante Aufträge von der Serverinstanz, die das ursprüngliche primäre Replikat hostet, manuell auf die Serverinstanzen kopieren, die die ursprünglichen sekundären Replikate hosten. Für alle Datenbanken müssen Sie am Anfang jedes relevanten Auftrags Logik hinzufügen, damit der Auftrag nur auf der primären Datenbank ausgeführt wird, das heißt nur dann, wenn das lokale Replikat das primäre Replikat für die Datenbank ist.  
  
     Die Serverinstanzen, die die Verfügbarkeitsreplikate einer Verfügbarkeitsgruppe hosten, könnten unterschiedlich konfiguriert sein, z. B. mit anderen Bandlaufwerkbuchstaben. Bei den Aufträgen für die einzelnen Verfügbarkeitsreplikate müssen derartige Unterschiede berücksichtigt werden.  
  
     Beachten Sie, dass Sicherungsaufträge die [sys.fn_hadr_is_preferred_backup_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) -Funktion verwenden können, um zu identifizieren, ob das lokale Replikat entsprechend den Sicherungseinstellungen der Verfügbarkeitsgruppe das bevorzugte Replikat für Sicherungen ist. Mit dem [Wartungsplanungs-Assistenten](../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md) erstellte Sicherungsaufträge verwenden diese Funktion systemintern. Für andere Sicherungsaufträge empfiehlt es sich, diese Funktion in den Sicherungsaufträgen als Bedingung zu verwenden, sodass sie nur auf dem bevorzugten Replikat ausgeführt werden. Weitere Informationen finden Sie unter [aktive sekundäre Replikate: Sicherung auf sekundären Replikaten (AlwaysOn-Verfügbarkeitsgruppen)](availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
-   **Anmeldungen**  
  
     Wenn Sie eigenständige Datenbanken verwenden, können Sie enthaltene Benutzer in den Datenbanken konfigurieren. Für diese Benutzer müssen Sie keine Anmeldenamen auf den Serverinstanzen erstellen, die ein sekundäres Replikat hosten. Für eine nicht eigenständige Verfügbarkeitsdatenbank müssen Sie Benutzer für die Anmeldungen auf den Serverinstanzen erstellen, die die Verfügbarkeitsreplikate hosten. Weitere Informationen finden Sie unter [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
     Wenn eine Ihrer Anwendungen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Authentifizierung oder eine lokale Windows-Anmeldung verwendet, siehe [Anmeldenamen von Anwendungen, die die SQL Server-Authentifizierung oder eine lokale Windows-Anmeldung verwenden](../../2014/database-engine/logins-and-jobs-for-availability-group-databases.md#SSauthentication)weiter unten in diesem Thema.  
  
    > [!NOTE]  
    >  Ein Datenbankbenutzer, für den die SQL Server-Anmeldung auf einer Serverinstanz nicht oder falsch definiert ist, kann sich bei der Instanz nicht anmelden. Diese Benutzer werden als *verwaiste Benutzer* der Datenbank dieser Serverinstanz bezeichnet. Wenn ein Benutzer auf einer bestimmten Serverinstanz ein verwaister Benutzer ist, können Sie jederzeit die Benutzeranmeldungen einrichten. Weitere Informationen finden Sie unter [Problembehandlung bei verwaisten Benutzern &#40;SQL Server&#41;](../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)aus.  
  
-   **Weitere Metadaten**  
  
     Anmeldenamen und Aufträge sind nicht die einzigen Informationen, die auf jeder Serverinstanz, die für eine gegebene Verfügbarkeitsgruppe ein sekundäres Replikat hostet, neu erstellt werden müssen. Beispielsweise müssen Sie möglicherweise Serverkonfigurationseinstellungen, Anmeldeinformationen, verschlüsselte Daten, Berechtigungen, Replikationseinstellungen, Service Broker-Anwendungen, Trigger (auf Serverebene) usw., neu erstellen. Weitere Informationen finden Sie unter [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Server Instanz &#40;SQL Server&#41;](../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).  
  
##  <a name="logins-of-applications-that-use-sql-server-authentication-or-a-local-windows-login"></a><a name="SSauthentication"></a> Anmeldenamen von Anwendungen, die die SQL Server-Authentifizierung oder eine lokale Windows-Anmeldung verwenden  
 Wenn eine Anwendung die SQL Server-Authentifizierung oder eine lokale Windows-Anmeldung verwendet, können nicht übereinstimmende SIDs verhindern, dass der Anmeldename der Anwendung auf einer Remoteinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aufgelöst wird. Aufgrund der nicht übereinstimmenden SIDs wird der Anmeldename auf der Remoteserverinstanz als verwaister Benutzer behandelt. Dieses Problem kann auftreten, wenn von einer Anwendung nach einem Failover eine Verbindung mit einer gespiegelten oder Protokollversand-Datenbank hergestellt wird bzw. wenn eine Verbindung mit einer Replikationsabonnenten-Datenbank hergestellt wird, die von einer Sicherung initialisiert wurde.  
  
 Um dieses Problem zu vermeiden, sollten Sie Vorbeugemaßnahmen ergreifen, wenn Sie eine solche Anwendung für die Verwendung einer Datenbank einrichten, die auf einer Remoteinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]gehostet wird. Eine Vorbeugungsmaßnahme besteht darin, die Anmeldenamen und Kennwörter von der lokalen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf die Remoteinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zu übertragen. Weitere Informationen zur Vermeidung dieses Problems finden Sie im KB-Artikel 918992:[übertragen von Anmeldungen und Kenn Wörtern zwischen Instanzen von SQL Server](https://support.microsoft.com/kb/918992/)).  
  
> [!NOTE]  
>  Dieses Problem betrifft lokale Windows-Konten auf unterschiedlichen Computern. Bei Domänenkonten tritt das Problem jedoch nicht auf, da die SID auf allen Computern identisch ist.  
  
 Weitere Informationen finden Sie unter [Verwaiste Benutzer bei Datenbankspiegelung und Protokollversand](https://blogs.msdn.com/b/sqlserverfaq/archive/2009/04/13/orphaned-users-with-database-mirroring-and-log-shipping.aspx) (Blog zur Datenbank-Engine).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen eines Anmelde namens](../relational-databases/security/authentication-access/create-a-login.md)  
  
-   [Erstellen Sie einen Datenbankbenutzer](../relational-databases/security/authentication-access/create-a-database-user.md).  
  
-   [Erstellen eines Auftrags](../ssms/agent/create-a-job.md)  
  
-   [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Eigenständige Datenbanken](../relational-databases/databases/contained-databases.md)   
 [Erstellen von Aufträgen](../ssms/agent/create-jobs.md)  
  
  
