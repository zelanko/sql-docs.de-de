---
title: sysmail_add_account_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_account_sp
- sysmail_add_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_account_sp
ms.assetid: 65e15e2e-107c-49c3-b12c-f4edf0eb1617
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7af8aa1693f303f76c04219e384d13a0bbaf6afe
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211284"
---
# <a name="sysmail_add_account_sp-transact-sql"></a>sysmail_add_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Erstellt ein neues Datenbank-E-Mail-Konto, in dem Informationen zu einem SMTP-Konto gespeichert sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_add_account_sp  [ @account_name = ] 'account_name',  
    [ @email_address = ] 'email_address' ,  
    [ [ @display_name = ] 'display_name' , ]  
    [ [ @replyto_address = ] 'replyto_address' , ]  
    [ [ @description = ] 'description' , ]  
    [ @mailserver_name = ] 'server_name'   
    [ , [ @mailserver_type = ] 'server_type' ]  
    [ , [ @port = ] port_number ]  
    [ , [ @username = ] 'username' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @use_default_credentials = ] use_default_credentials ]  
    [ , [ @enable_ssl = ] enable_ssl ]  
    [ , [ @account_id = ] account_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @account_name = ] 'account_name'`Der Name des hinzu zufügenden Kontos. *account_name* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @email_address = ] 'email_address'`Die e-Mail-Adresse, von der die Nachricht gesendet wird. Bei dieser Adresse muss es sich um eine Internet-E-Mail-Adresse handeln. *email_address* ist vom Datentyp **nvarchar (128)** und hat keinen Standardwert. Beispielsweise kann ein Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den-Agent e-Mail von der Adresse **SqlAgent@Adventure-Works.com** senden.  
  
`[ @display_name = ] 'display_name'`Der Anzeige Name, der in e-Mail-Nachrichten von diesem Konto verwendet wird. *display_name* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Beispielsweise kann ein Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den-Agent den Namen **SQL Server-Agent automatisierten Mailer** in e-Mail-Nachrichten anzeigen.  
  
`[ @replyto_address = ] 'replyto_address'`Die Adresse, an die Antworten auf Nachrichten von diesem Konto gesendet werden. *replyto_address* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Antworten auf ein Konto für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den-Agent können z. b. an den Datenbankadministrator weitergeleitet werden. **danw@Adventure-Works.com**  
  
`[ @description = ] 'description'`Eine Beschreibung für das Konto. die *Beschreibung* ist vom Datentyp **nvarchar (256)** und hat den Standardwert NULL.  
  
`[ @mailserver_name = ] 'server_name'`Der Name oder die IP-Adresse des SMTP-Mailservers, der für dieses Konto verwendet werden soll. Der Computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem ausgeführt wird, muss in der Lage sein, den *Servername* in eine IP-Adresse aufzulösen. *Servername* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @mailserver_type = ] 'server_type'`Der Typ des e-Mail-Servers. *server_type* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **' SMTP '** .  
  
`[ @port = ] port_number`Die Portnummer für den e-Mail-Server. *Portnummer* ist vom Datentyp **int**. der Standardwert ist 25.  
  
`[ @username = ] 'username'`Der Benutzername, der zur Anmeldung beim e-Mail-Server verwendet werden soll. *username* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Wenn dieser Parameter NULL ist, verwendet Datenbank-E-Mail keine Authentifizierung für dieses Konto. Wenn für den Mailserver keine Authentifizierung erforderlich ist, verwenden Sie NULL als Wert für den Benutzernamen.  
  
`[ @password = ] 'password'`Das Kennwort, das für die Anmeldung am e-Mail-Server verwendet werden soll. *Password* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Ein Kennwort muss nur bereitgestellt werden, wenn ein Benutzername angegeben wird.  
  
`[ @use_default_credentials = ] use_default_credentials`Gibt an, ob die e-Mail mithilfe der Anmelde Informationen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]an den SMTP-Server gesendet werden soll. **use_default_credentials** ist vom Typ Bit. der Standardwert ist 0. Wenn dieser Parameter 1 ist, verwendet Datenbank-E-Mail die Anmeldeinformationen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Wenn dieser Parameter 0 ist, sendet Datenbank-E-Mail den **@username** - **@password** Parameter und den-Parameter, falls vorhanden **@username** , **@password** und sendet andernfalls eine e-Mail ohne-und-Parameter  
  
`[ @enable_ssl = ] enable_ssl`Gibt an, ob Datenbank-E-Mail die Kommunikation mit Secure Sockets Layer verschlüsselt. **Enable_ssl** ist vom Typ Bit. der Standardwert ist 0.  
  
`[ @account_id = ] account_id OUTPUT`Gibt die Konto-ID für das neue Konto zurück. *account_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Datenbank-E-Mail stellt separate Parameter für **@email_address** , **@display_name** und **@replyto_address** bereit. Der **@email_address** -Parameter ist die Adresse, von der die Nachricht gesendet wird. Der **@display_name** -Parameter ist der Name, der im Feld **from:** der e-Mail-Nachricht angezeigt wird. Der **@replyto_address** -Parameter ist die Adresse, an die Antworten auf die e-Mail-Nachricht gesendet werden. Beispiel: Ein Konto, das für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendet wird, soll E-Mail-Nachrichten von einer E-Mail-Adresse senden, die nur für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendet wird. Nachrichten von dieser Adresse sollen über einen Anzeigenamen verfügen, sodass die Empfänger problemlos feststellen können, dass die Nachricht vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent gesendet wurde. Wenn ein Empfänger auf die Nachricht antwortet, soll die Antwort an den Datenbankadministrator und nicht an die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendete Adresse gesendet werden. In diesem Szenario verwendet **SqlAgent@Adventure-Works.com** das Konto als e-Mail-Adresse. Der Anzeige Name ist auf **SQL Server-Agent automatisierten Mailer**festgelegt. Das Konto verwendet **danw@Adventure-Works.com** als Antwort auf die Adresse, sodass Antworten auf Nachrichten, die von diesem Konto gesendet werden, an den Datenbankadministrator und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht an die e-Mail-Adresse des Agents gesendet werden Durch die Bereitstellung unabhängiger Einstellungen für diese drei Parameter ermöglicht es Datenbank-E-Mail Ihnen, die Konfiguration von Nachrichten an Ihre Anforderungen anzupassen.  
  
 Der **@mailserver_type** -Parameter unterstützt den Wert **' SMTP '** .  
  
 Gibt an, dass 1 e-Mail mithilfe der Anmelde Informationen [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]von an den SMTP-Server gesendet wird. **@use_default_credentials** Wenn **@use_default_credentials** den Wert 0 hat **@username** und **@password** ein für ein Konto angegeben ist, verwendet das Konto die SMTP-Authentifizierung. Und sind die Anmelde Informationen, die das Konto für den SMTP-Server verwendet, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht die Anmelde Informationen für oder das Netzwerk, in dem sich der Computer befindet. **@password** **@username**  
  
 Die gespeicherte Prozedur **sysmail_add_account_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Konto mit dem Namen `AdventureWorks Administrator` erstellt. Das Konto verwendet die E-Mail-Adresse `dba@Adventure-Works.com` und sendet E-Mail-Nachrichten an den SMTP-Mailserver `smtp.Adventure-Works.com`. Die von diesem Konto gesendeten e `AdventureWorks Automated Mailer` -Mail-Nachrichten werden in der Zeile **von:** der Nachricht angezeigt. Antworten auf Nachrichten von diesem Konto werden an `danw@Adventure-Works.com` gesendet.  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)   
 [Erstellen eines Datenbank-E-Mail Kontos](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Datenbank-E-Mail gespeicherter &#40;Prozeduren (Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
