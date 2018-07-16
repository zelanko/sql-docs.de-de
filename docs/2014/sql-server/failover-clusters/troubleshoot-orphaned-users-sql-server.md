---
title: Problembehandlung bei verwaisten Benutzern (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- orphaned users [SQL Server]
- logins [SQL Server], orphaned users
- troubleshooting [SQL Server], user accounts
- user accounts [SQL Server], orphaned users
- failover [SQL Server], managing metadata
- database mirroring [SQL Server], metadata
- users [SQL Server], orphaned
ms.assetid: 11eefa97-a31f-4359-ba5b-e92328224133
caps.latest.revision: 33
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5ac7577269daca9d8d5974c3a98ade1a681d6d79
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317850"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a>Problembehandlung bei verwaisten Benutzern (SQL Server)
  Der Prinzipal muss einen gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen besitzen, um sich bei einer Instanz von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzumelden. Der Anmeldename wird bei der Authentifizierung benötigt, bei der überprüft wird, ob der Prinzipal eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herstellen darf. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamen auf einer Serverinstanz werden in der **Sys. server_principals** -Katalogsicht und die **sys.syslogins** -kompatibilitätssicht angezeigt.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verwenden für den Zugriff auf die einzelnen Datenbanken einen Datenbankbenutzer, der dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen zugeordnet ist. Es gibt jedoch zwei Ausnahmen:  
  
-   Das Gastkonto.  
  
     Wenn dieses Konto in der Datenbank aktiviert ist, können die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen, die keinem Datenbankbenutzer zugeordnet sind, die Datenbank als Gastbenutzer verwenden.  
  
-   Microsoft Windows-Gruppenmitgliedschaften.  
  
     Ein von einem Windows-Benutzer erstellter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename kann eine Datenbank verwenden, wenn der Windows-Benutzer Mitglied einer Windows-Gruppe ist, die auch ein Benutzer der Datenbank ist.  
  
 Die Informationen für die Zuordnung eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamens zu einem Datenbankbenutzer werden in der Datenbank gespeichert. Hierzu zählen der Name des Datenbankbenutzers sowie die Sicherheits-ID (SID) des entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamens. Die Berechtigungen dieses Datenbankbenutzers werden für die Autorisierung in der Datenbank verwendet.  
  
 Ein Datenbankbenutzer, für den ein entsprechender [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename auf einer Serverinstanz nicht oder falsch definiert ist, kann sich bei der Instanz nicht anmelden. Diese Benutzer werden als *verwaiste Benutzer* der Datenbank dieser Serverinstanz bezeichnet. Ein Datenbankbenutzer kann zu einem verwaisten Benutzer werden, wenn der entsprechende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename gelöscht wird. Ein Datenbankbenutzer kann auch dann zu einem verwaisten Benutzer werden, wenn die Datenbank auf einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz wiederhergestellt oder an eine andere SQL Server-Instanz angefügt wird. Verwaisungen treten auf, wenn der Datenbankbenutzer einer SID zugeordnet wird, die auf der neuen Serverinstanz nicht vorhanden ist.  
  
> [!NOTE]  
>  Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung kann nicht zugegriffen werden eine Datenbank, in dem es einen entsprechenden Datenbankbenutzer fehlt, es sei denn, **Gast** in dieser Datenbank aktiviert ist. Weitere Informationen zum Erstellen einer Datenbank-Benutzerkonto, finden Sie unter [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
## <a name="to-detect-orphaned-users"></a>So ermitteln Sie verwaiste Benutzer  
 Zum Ermitteln von verwaisten Benutzern führen Sie die folgenden Transact-SQL-Anweisungen aus:  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 Die Ausgabe führt alle Benutzer der aktuellen Datenbank auf, die mit keinem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verknüpft sind, sowie die entsprechenden SIDs (Sicherheits-IDs). Weitere Informationen finden Sie unter [Sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
> [!NOTE]  
>  **Sp_change_users_login** kann nicht verwendet werden, mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldungen, die von Windows erstellt werden.  
  
## <a name="to-resolve-an-orphaned-user"></a>So lösen Sie einen verwaisten Benutzer auf  
 Zum Auflösen eines verwaisten Benutzers führen Sie folgende Prozedur aus:  
  
1.  Der folgende Befehl serveranmeldekonto der gemäß *< Login_name >* mit dem Datenbankbenutzer gemäß *< Database_user >*.  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     Weitere Informationen finden Sie unter [Sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
2.  Nachdem Sie den im letzten Schritt angegebenen Code ausgeführt haben, kann der Benutzer wieder auf die Datenbank zugreifen. Der Benutzer kann dann das Kennwort des Ändern der *< Login_name >* Anmeldekonto mit den **Sp_password** gespeicherte Prozedur wie folgt:  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  Nur Anmeldenamen mit der Berechtigung ALTER ANY LOGIN können auch die Kennwörter von anderen Benutzernamen ändern. Allerdings können die Kennwörter von Mitgliedern der **sysadmin** -Rolle nur von Mitgliedern der **sysadmin** -Rolle geändert werden.  
  
    > [!NOTE]  
    >  **Sp_password** kann nicht verwendet werden, für die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konten. Benutzer, die über das Windows-Netzwerkkonto eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen, werden durch Windows authentifiziert. Deshalb können ihre Kennwörter nur unter Windows geändert werden.  
  
     Weitere Informationen finden Sie unter [Sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)   
 [sp_change_users_login &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)   
 [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)   
 [sp_grantlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql)   
 [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)   
 [sys.sysusers &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)   
 [Sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
