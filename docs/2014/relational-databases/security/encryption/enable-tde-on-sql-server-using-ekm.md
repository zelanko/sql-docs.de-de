---
title: Aktivieren von TDE mithilfe von EKM | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], TDE using an EKM
- TDE, EKM how to
- EKM, TDE how to
- Transparent Data Encryption, using EKM
ms.assetid: b892e7a7-95bd-4903-bf54-55ce08e225af
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: 8b3f046017aa54f5db96878f8bfb6c435409d839
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74957231"
---
# <a name="enable-tde-using-ekm"></a>Aktivieren von TDE mit EKM
  In diesem Thema wird beschrieben, wie die transparente Datenverschlüsselung (TDE) in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] aktiviert wird, um einen Verschlüsselungsschlüssel für die Datenbank mithilfe eines asymmetrischen in einem erweiterbaren Schlüsselverwaltungsmodul mit (EKM) [!INCLUDE[tsql](../../../includes/tsql-md.md)]gespeicherten Schlüssels zu aktivieren.  
  
 TDE verschlüsselt die Speicherung einer gesamten Datenbank, indem ein symmetrischer Schlüssel verwendet wird, der als Datenbankverschlüsselungsschlüssel bezeichnet wird. Der Verschlüsselungsschlüssel für die Datenbank kann auch mithilfe eines Zertifikats geschützt werden, das mit dem Datenbank-Hauptschlüssel der Masterdatenbank geschützt wird. Weitere Informationen über das Schützen des Verschlüsselungsschlüssels für die Datenbank mit dem Datenbank-Hauptschlüssel finden Sie unter [Transparente Datenverschlüsselung &#40;TDE&#41;](transparent-data-encryption.md). Informationen zum Konfigurieren von TDE, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf einem virtuellen Azure-Computer ausgeführt wird, finden Sie unter [Erweiterbare Schlüsselverwaltung mit Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [So aktivieren Sie TDE unter Verwendung von EKM mit Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Sie müssen ein Benutzer mit hohen Privilegien (z.&#160;B. ein Systemadministrator) sein, um einen Verschlüsselungsschlüssel für die Datenbank erstellen und eine Datenbank verschlüsseln zu können. Dieser Benutzer muss vom EKM-Modul authentifiziert werden können.  
  
-   Beim Starten muss [!INCLUDE[ssDE](../../../includes/ssde-md.md)] die Datenbank öffnen. Dafür sollten Sie Anmeldeinformationen erstellen, die vom EKM authentifiziert werden, und sie einer Anmeldung hinzufügen, die auf einem asymmetrischen Schlüssel basiert. Benutzer können sich mit dieser Anmeldung nicht anmelden, [!INCLUDE[ssDE](../../../includes/ssde-md.md)] ist aber in der Lage, sich beim EKM-Gerät selbst zu authentifizieren.  
  
-   Wenn der im EKM-Modul gespeicherte asymmetrische Schlüssel verloren geht, kann die Datenbank nicht von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]geöffnet werden. Wenn der Anbieter für erweiterbare Schlüsselverwaltung eine Sicherung des asymmetrischen Schlüssels erlaubt, sollten Sie eine Sicherung erstellen und diese an einem sicheren Ort aufbewahren.  
  
-   Die für Ihren EKM-Anbieter erforderlichen Optionen und Parameter können sich von denen im unten angegebenen Codebeispiel unterscheiden. Weitere Informationen erhalten Sie vom Anbieter für erweiterbare Schlüsselverwaltung.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 In diesem Thema werden die folgenden Berechtigungen verwendet:  
  
-   Zum Ändern einer Konfigurationsoption und Ausführen der RECONFIGURE-Anweisung muss Ihnen die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
-   Erfordert die ALTER ANY CREDENTIAL-Berechtigung.  
  
-   Erfordert die ALTER ANY LOGIN-Berechtigung.  
  
-   Erfordert die CREATE ASYMMETRIC KEY-Berechtigung.  
  
-   Erfordert die CONTROL-Berechtigung für die Datenbank, um die Datenbank zu verschlüsseln.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-enable-tde-using-ekm"></a>So aktivieren Sie TDE unter Verwendung von EKM  
  
1.  Kopieren Sie die Dateien, die vom Anbieter für erweiterbare Schlüsselverwaltung bereitgestellt wurden, an einen geeigneten Speicherort auf dem Computer mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . In diesem Beispiel wird der Ordner **C:\EKM** verwendet.  
  
2.  Installieren Sie Zertifikate auf dem Computer, die ggf. vom Anbieter für erweiterbare Schlüsselverwaltung benötigt werden.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stellt keinen Anbieter für erweiterbare Schlüsselverwaltung zur Verfügung. Jeder Anbieter für erweiterbare Schlüsselverwaltung kann über andere Prozeduren zum Installieren, Konfigurieren und Autorisieren von Benutzern verfügen.  Schlagen Sie in der Dokumentation Ihres Anbieters für erweiterbare Schlüsselverwaltung nach, um diesen Schritt auszuführen.  
  
3.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
4.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
5.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Enable advanced options.  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Create a cryptographic provider, which we have chosen to call "EKM_Prov," based on an EKM provider  
  
    CREATE CRYPTOGRAPHIC PROVIDER EKM_Prov   
    FROM FILE = 'C:\EKM_Files\KeyProvFile.dll' ;  
    GO  
  
    -- Create a credential that will be used by system administrators.  
    CREATE CREDENTIAL sa_ekm_tde_cred   
    WITH IDENTITY = 'Identity1',   
    SECRET = 'q*gtev$0u#D1v'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
    GO  
  
    -- Add the credential to a high privileged user such as your   
    -- own domain login in the format [DOMAIN\login].  
    ALTER LOGIN Contoso\Mary  
    ADD CREDENTIAL sa_ekm_tde_cred ;  
    GO  
    -- create an asymmetric key stored inside the EKM provider  
    USE master ;  
    GO  
    CREATE ASYMMETRIC KEY ekm_login_key   
    FROM PROVIDER [EKM_Prov]  
    WITH ALGORITHM = RSA_512,  
    PROVIDER_KEY_NAME = 'SQL_Server_Key' ;  
    GO  
  
    -- Create a credential that will be used by the Database Engine.  
    CREATE CREDENTIAL ekm_tde_cred   
    WITH IDENTITY = 'Identity2'   
    , SECRET = 'jeksi84&sLksi01@s'   
    FOR CRYPTOGRAPHIC PROVIDER EKM_Prov ;  
  
    -- Add a login used by TDE, and add the new credential to the login.  
    CREATE LOGIN EKM_Login   
    FROM ASYMMETRIC KEY ekm_login_key ;  
    GO  
    ALTER LOGIN EKM_Login   
    ADD CREDENTIAL ekm_tde_cred ;  
    GO  
  
    -- Create the database encryption key that will be used for TDE.  
    USE AdventureWorks2012 ;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM  = AES_128  
    ENCRYPTION BY SERVER ASYMMETRIC KEY ekm_login_key ;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE AdventureWorks2012   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter  
  
-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)  
  
-   [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [Erweiterbare Schlüsselverwaltung mit Azure Key Vault &#40;SQL Server&#41;](extensible-key-management-using-azure-key-vault-sql-server.md)  
  
-   [Transparent Data Encryption mit Azure SQL-Datenbank](../../../database-engine/transparent-data-encryption-with-azure-sql-database.md)  
  
  
