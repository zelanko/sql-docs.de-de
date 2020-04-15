---
title: sysmail_update_account_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_account_sp
- sysmail_update_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_account_sp
ms.assetid: ba2fdccc-5ed4-40ef-a479-79497b4d61aa
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3dd772a1519ea856cac0302d31be9eb7d0f9d782
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283141"
---
# <a name="sysmail_update_account_sp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Informationen in einem vorhandenen Konto für Datenbank-E-Mail.  
 
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_update_account_sp [ [ @account_id = ] account_id ] [ , ] [ [ @account_name = ] 'account_name' ] ,  
    [ @email_address = ] 'email_address' ,   
    [ @display_name = ] 'display_name' ,   
    [ @replyto_address = ] 'replyto_address' ,  
    [ @description = ] 'description' ,   
    [ @mailserver_name = ] 'server_name' ,   
    [ @mailserver_type = ] 'server_type' ,   
    [ @port = ] port_number ,   
    [ @timeout = ] 'timeout' ,  
    [ @username = ] 'username' ,  
    [ @password = ] 'password' ,  
    [ @use_default_credentials = ] use_default_credentials ,  
    [ @enable_ssl = ] enable_ssl   
```  
  
## <a name="arguments"></a>Argumente  
`[ @account_id = ] account_id`Die zu aktualisierende Konto-ID. *account_id* ist vom Datentyp **int**und hat den Standardwert NULL. Mindestens eine *account_id* oder *account_name* muss angegeben werden. Wenn beide Argumente angegeben werden, ändert die Prozedur den Namen des Kontos.  
  
`[ @account_name = ] 'account_name'`Der Name des zu aktualisierenden Kontos. *account_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. Mindestens eine *account_id* oder *account_name* muss angegeben werden. Wenn beide Argumente angegeben werden, ändert die Prozedur den Namen des Kontos.  
  
`[ @email_address = ] 'email_address'`Die neue E-Mail-Adresse, von der die Nachricht gesendet werden soll. Bei dieser Adresse muss es sich um eine Internet-E-Mail-Adresse handeln. Der Servername ist die Adresse des Servers, der von Datenbank-E-Mail zum Senden von E-Mails von diesem Konto verwendet wird. *email_address* ist **nvarchar(128)**, mit dem Standardwert NULL.  
  
`[ @display_name = ] 'display_name'`Der neue Anzeigename, der für E-Mail-Nachrichten aus diesem Konto verwendet werden soll. *display_name* ist **nvarchar(128)**, ohne Standard.  
  
`[ @replyto_address = ] 'replyto_address'`Die neue Adresse, die im Reply-To-Header von E-Mail-Nachrichten aus diesem Konto verwendet werden soll. *replyto_address* ist **nvarchar(128)**, ohne Standard.  
  
`[ @description = ] 'description'`Die neue Beschreibung für das Konto. *Beschreibung* ist **nvarchar(256)**, mit dem Standardwert NULL.  
  
`[ @mailserver_name = ] 'server_name'`Der neue Name des SMTP-Mailservers, der für dieses Konto verwendet werden soll. Der Computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der ausgeführt wird, muss in der Lage sein, die *server_name* in eine IP-Adresse aufzulösen. *server_name* ist **sysname**, ohne Standardeinstellung.  
  
`[ @mailserver_type = ] 'server_type'`Der neue Typ des Mailservers. *server_type* ist **sysname**, ohne Standard. Es wird nur ein Wert von **'SMTP'** unterstützt.  
  
`[ @port = ] port_number`Die neue Portnummer des Mailservers. *port_number* ist **int**, ohne Standardwert.  
  
`[ @timeout = ] 'timeout'`Timeout-Parameter für SmtpClient.Senden einer einzelnen E-Mail-Nachricht. *Timeout* ist **int** in Sekunden, ohne Standardeinstellung.  
  
`[ @username = ] 'username'`Der neue Benutzername, der zum Anmelden am Mailserver verwendet werden soll. *Der Benutzername* ist **sysname**, ohne Standard.  
  
`[ @password = ] 'password'`Das neue Kennwort, das zum Anmelden am Mailserver verwendet werden soll. *Kennwort* ist **sysname**, ohne Standard.  
  
`[ @use_default_credentials = ] use_default_credentials`Gibt an, ob die E-Mail mithilfe der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Anmeldeinformationen des Dienstes an den SMTP-Server gesendet werden soll. **use_default_credentials** ist vom Datentyp bit und hat keinen Standardwert. Wenn dieser Parameter 1 ist, verwendet Datenbank-E-Mail die Anmeldeinformationen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Wenn dieser Parameter 0 ist, verwendet Database Mail den ** \@Benutzernamen** und ** \@das Kennwort** für die Authentifizierung auf dem SMTP-Server. Wenn ** \@Benutzername** und ** \@Kennwort** NULL sind, verwendet es die anonyme Authentifizierung. Besprechen Sie die geeignete Angabe für diesen Parameter mit Ihrem SMTP-Administrator.  
  
`[ @enable_ssl = ] enable_ssl`Gibt an, ob Database Mail die Kommunikation mit Transport Layer Security (TLS) verschlüsselt, die zuvor als SSL (Secure Sockets Layer) bezeichnet wurde. Verwenden Sie diese Option, wenn TLS auf Ihrem SMTP-Server erforderlich ist. **enable_ssl** ist vom Datentyp bit und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn sowohl Kontoname als auch Konto-ID angegeben wird, aktualisiert die gespeicherte Prozedur nicht nur die Informationen für das Konto, sondern ändert auch noch den Kontonamen. Die Änderung des Kontonamens kann hilfreich sein, wenn ein fehlerhafter Kontoname korrigiert werden soll.  
  
 Die gespeicherte Prozedur **sysmail_update_account_sp** befindet sich in der **msdb-Datenbank** und gehört dem **dbo-Schema.** Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **sysadmin** Fixed Server-Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-changing-the-information-for-an-account"></a>A. Ändern der Informationen für ein Konto  
 Im folgenden Beispiel `AdventureWorks Administrator` wird das Konto in der **msdb-Datenbank** aktualisiert. Die Informationen für dieses Konto werden auf die bereitgestellten Werte festgelegt.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_name = 'AdventureWorks Administrator'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
### <a name="b-changing-the-name-of-an-account-and-the-information-for-an-account"></a>B. Ändern des Namens eines Kontos und der Informationen für ein Konto  
 Im folgenden Beispiel wird der Name des Kontos mit der Konto-ID `125` geändert, und die Informationen für dieses Konto werden aktualisiert. Der Name des Kontos lautet `Backup Mail Server`.  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_id = 125  
    ,@account_name = 'Backup Mail Server'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp-backup.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Erstellen eines Datenbank-E-Mail-Kontos](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Database Mail Gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
