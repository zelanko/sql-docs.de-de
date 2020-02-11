---
title: Problembehandlung bei verwaisten Benutzern (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 38a33b34b64cf285e94f66c547b2309b8daf1ae8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035665"
---
# <a name="troubleshoot-orphaned-users-sql-server"></a>Problembehandlung bei verwaisten Benutzern (SQL Server)
  Der Prinzipal muss einen gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen besitzen, um sich bei einer Instanz von Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzumelden. Der Anmeldename wird bei der Authentifizierung benötigt, bei der überprüft wird, ob der Prinzipal eine Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herstellen darf. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldungen auf einer Serverinstanz werden in der **sys. server_principals** -Katalog Sicht und in der **sys. syslogins** -Kompatibilitäts Sicht angezeigt.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verwenden für den Zugriff auf die einzelnen Datenbanken einen Datenbankbenutzer, der dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen zugeordnet ist. Es gibt jedoch zwei Ausnahmen:  
  
-   Das Gastkonto.  
  
     Wenn dieses Konto in der Datenbank aktiviert ist, können die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen, die keinem Datenbankbenutzer zugeordnet sind, die Datenbank als Gastbenutzer verwenden.  
  
-   Microsoft Windows-Gruppenmitgliedschaften.  
  
     Ein von einem Windows-Benutzer erstellter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename kann eine Datenbank verwenden, wenn der Windows-Benutzer Mitglied einer Windows-Gruppe ist, die auch ein Benutzer der Datenbank ist.  
  
 Die Informationen für die Zuordnung eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamens zu einem Datenbankbenutzer werden in der Datenbank gespeichert. Hierzu zählen der Name des Datenbankbenutzers sowie die Sicherheits-ID (SID) des entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldenamens. Die Berechtigungen dieses Datenbankbenutzers werden für die Autorisierung in der Datenbank verwendet.  
  
 Ein Datenbankbenutzer, für den ein entsprechender [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldename auf einer Serverinstanz nicht oder falsch definiert ist, kann sich bei der Instanz nicht anmelden. Diese Benutzer werden als *verwaiste Benutzer* der Datenbank dieser Serverinstanz bezeichnet. Ein Datenbankbenutzer kann zu einem verwaisten Benutzer werden, wenn der entsprechende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldename gelöscht wird. Ein Datenbankbenutzer kann auch dann zu einem verwaisten Benutzer werden, wenn die Datenbank auf einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz wiederhergestellt oder an eine andere SQL Server-Instanz angefügt wird. Verwaisungen treten auf, wenn der Datenbankbenutzer einer SID zugeordnet wird, die auf der neuen Serverinstanz nicht vorhanden ist.  
  
> [!NOTE]  
>  Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmelde Name kann nicht auf eine Datenbank zugreifen, in der er keinen entsprechenden Datenbankbenutzer besitzt, es sei denn, der **Gast** ist in dieser Datenbank Weitere Informationen zum Erstellen eines Datenbank-Benutzerkontos finden Sie unter [Create User &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
## <a name="to-detect-orphaned-users"></a>So ermitteln Sie verwaiste Benutzer  
 Zum Ermitteln von verwaisten Benutzern führen Sie die folgenden Transact-SQL-Anweisungen aus:  
  
```  
USE <database_name>;  
GO;   
sp_change_users_login @Action='Report';  
GO;  
```  
  
 Die Ausgabe führt alle Benutzer der aktuellen Datenbank auf, die mit keinem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen verknüpft sind, sowie die entsprechenden SIDs (Sicherheits-IDs). Weitere Informationen finden Sie unter [sp_change_users_login &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
> [!NOTE]  
>  **sp_change_users_login** kann nicht mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldungen verwendet werden, die aus Windows erstellt wurden.  
  
## <a name="to-resolve-an-orphaned-user"></a>So lösen Sie einen verwaisten Benutzer auf  
 Zum Auflösen eines verwaisten Benutzers führen Sie folgende Prozedur aus:  
  
1.  Mit dem folgenden Befehl wird das von *<login_name>* angegebene Server Anmelde Konto erneut mit dem Datenbankbenutzer verknüpft, der durch *<database_user>* angegeben wurde.  
  
    ```  
    USE <database_name>;  
    GO  
    sp_change_users_login @Action='update_one', @UserNamePattern='<database_user>', @LoginName='<login_name>';  
    GO  
  
    ```  
  
     Weitere Informationen finden Sie unter [sp_change_users_login &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql).  
  
2.  Nachdem Sie den im letzten Schritt angegebenen Code ausgeführt haben, kann der Benutzer wieder auf die Datenbank zugreifen. Der Benutzer kann dann das Kennwort des *<login_name>* Anmelde Kontos mithilfe der gespeicherten Prozedur **sp_password** wie folgt ändern:  
  
    ```  
    USE master   
    GO  
    sp_password @old=NULL, @new='password', @loginame='<login_name>';  
    GO  
    ```  
  
    > [!IMPORTANT]  
    >  Nur Anmeldenamen mit der Berechtigung ALTER ANY LOGIN können auch die Kennwörter von anderen Benutzernamen ändern. Allerdings können die Kennwörter von Mitgliedern der **sysadmin** -Rolle nur von Mitgliedern der **sysadmin** -Rolle geändert werden.  
  
    > [!NOTE]  
    >  **sp_password** können nicht für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konten verwendet werden. Benutzer, die über das Windows-Netzwerkkonto eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen, werden durch Windows authentifiziert. Deshalb können ihre Kennwörter nur unter Windows geändert werden.  
  
     Weitere Informationen finden Sie unter [sp_password &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Benutzer &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-user-transact-sql)   
 [Erstellen der Anmeldung &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-login-transact-sql)   
 [sp_change_users_login &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)   
 [sp_addlogin &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)   
 [sp_grantlogin &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-grantlogin-transact-sql)   
 [sp_password &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)   
 [sys. sysusers &#40;Transact-SQL-&#41;](/sql/relational-databases/system-compatibility-views/sys-sysusers-transact-sql)   
 [sys. syslogins &#40;Transact-SQL-&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)  
  
  
