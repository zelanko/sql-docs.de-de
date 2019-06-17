---
title: Prinzipale (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 54aab33e754331482ef154d9172f0e41cd251db0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63011917"
---
# <a name="principals-database-engine"></a>Prinzipale (Datenbank-Engine)
  *Prinzipale* sind Entitäten, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressourcen anfordern können. Wie bei anderen Komponenten des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Autorisierungsmodells können Prinzipale hierarchisch angeordnet werden. Der Gültigkeitsbereich der Einflussbereich eines Prinzipals hängt von dem Definitionsbereich des Prinzipals ab: Windows, Server, Datenbank; und gibt an, ob der Prinzipal unteilbar ist, oder eine Auflistung. Ein Windows-Anmeldename ist ein Beispiel eines unteilbaren Prinzipals und eine Windows-Gruppe das eines Prinzipals, der eine Auflistung darstellt. Jeder Prinzipal weist eine Sicherheits-ID (SID) auf.  
  
 **Auf Windows-Prinzipale**  
  
-   Windows-Domänenanmeldename  
  
-   Lokaler Windows-Anmeldename  
  
 **SQL Server**-**Ebenen** **principals**  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldename  
  
-   Serverrolle  
  
 **Auf Datenbankebene-Prinzipale**  
  
-   Datenbankbenutzer  
  
-   Datenbankrolle  
  
-   Anwendungsrolle  
  
## <a name="the-sql-server-sa-login"></a>Der SQL Server-Anmeldename sa  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldename „sa“ ist ein Prinzipal auf Serverebene. Er wird standardmäßig bei der Installation einer Instanz erstellt. Ab [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ist die Standarddatenbank von sa „Master“. Dieses Verhalten unterscheidet sich von früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="public-database-role"></a>Datenbankrolle public  
 Jeder Datenbankbenutzer gehört der Datenbankrolle public an. Wenn einem Benutzer keine bestimmten Berechtigungen für ein sicherungsfähiges Element erteilt oder verweigert werden, erbt der Benutzer die Berechtigungen, die der Datenbankrolle public für dieses sicherungsfähige Element erteilt wurden.  
  
## <a name="informationschema-and-sys"></a>INFORMATION_SCHEMA und sys  
 Jede Datenbank enthält zwei Entitäten, die in Katalogsichten als Benutzer angezeigt werden: INFORMATION_SCHEMA und Sys. Diese Entitäten werden von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]benötigt. Es handelt sich dabei nicht um Prinzipale, die geändert oder gelöscht werden können.  
  
## <a name="certificate-based-sql-server-logins"></a>Zertifikatbasierte SQL Server-Anmeldenamen  
 Serverprinzipale, deren Name von doppelten Nummernzeichen (##) eingeschlossen ist, sind nur für die systeminterne Verwendung vorgesehen. Die folgenden Prinzipale werden bei der Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aus Zertifikaten erstellt und sollten nicht gelöscht werden.  
  
-   \##MS_SQLResourceSigningCertificate##  
  
-   \##MS_SQLReplicationSigningCertificate##  
  
-   \##MS_SQLAuthenticatorCertificate##  
  
-   \##MS_AgentSigningCertificate##  
  
-   \##MS_PolicyEventProcessingLogin##  
  
-   \##MS_PolicySigningCertificate##  
  
-   \##MS_PolicyTsqlExecutionLogin##  
  
## <a name="the-guest-user"></a>Der guest-Benutzer  
 Jede Datenbank enthält einen **Gast**. Dem **guest** -Benutzer erteilte Berechtigungen werden von Benutzern geerbt, die Zugriff auf die Datenbank, jedoch kein Benutzerkonto in der Datenbank besitzen. Die **Gast** Benutzer kann nicht gelöscht werden, aber sie kann deaktiviert werden, indem Sperren des `CONNECT` Berechtigung. Die `CONNECT` Berechtigung kann widerrufen werden, indem Sie Ausführung `REVOKE CONNECT FROM GUEST` in einer beliebigen Datenbank außer Master oder Tempdb.  
  
## <a name="client-and-database-server"></a>Client und Datenbankserver  
 Laut Definition sind ein Client und ein Datenbankserver Sicherheitsprinzipale und können gesichert werden. Diese Entitäten können gegenseitig authentifiziert werden, bevor eine sichere Netzwerkverbindung hergestellt wird. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt die [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) -Authentifizierungsprotokoll, das definiert, wie Clients mit einem Netzwerkauthentifizierungsdienst interagieren.  
  
## <a name="related-tasks"></a>Related Tasks  
 Dieser Abschnitt der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Onlinedokumentation umfasst die folgenden Themen:  
  
-   [Verwalten von Anmeldungen, Benutzern und Schemas: Vorgehensweisen](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [Rollen auf Serverebene](server-level-roles.md)  
  
-   [Rollen auf Datenbankebene](database-level-roles.md)  
  
-   [Anwendungsrollen](application-roles.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von SQL Server](../securing-sql-server.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)   
 [sys.server_principals &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)   
 [sys.sql_logins &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)   
 [sys.database_role_members &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)   
 [Rollen auf Serverebene](server-level-roles.md)   
 [Rollen auf Datenbankebene](database-level-roles.md)  
  
  
