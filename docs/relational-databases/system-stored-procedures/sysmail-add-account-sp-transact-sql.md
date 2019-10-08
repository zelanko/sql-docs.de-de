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
ms.openlocfilehash: 32b8c8b1bbac53b099afc64f06a0eb5137292555
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006089"
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
`[ @account_name = ] 'account_name'` den Namen des hinzu zufügenden Kontos. *account_name* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
`[ @email_address = ] 'email_address'` die e-Mail-Adresse, von der die Nachricht gesendet werden soll. Bei dieser Adresse muss es sich um eine Internet-E-Mail-Adresse handeln. *email_address* ist vom Datentyp **nvarchar (128)** und hat keinen Standardwert. Beispielsweise kann ein Konto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent eine e-Mail von der Adresse **SqlAgent@Adventure-Works.com** senden.  
  
`[ @display_name = ] 'display_name'` der Anzeige Name, der in e-Mail-Nachrichten von diesem Konto verwendet werden soll. *display_name* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Beispielsweise kann ein Konto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent den Namen **SQL Server-Agent automatisierten Mailer** in e-Mail-Nachrichten anzeigen.  
  
`[ @replyto_address = ] 'replyto_address'` die Adresse, an die Antworten auf Nachrichten von diesem Konto gesendet werden. *replyto_address* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Antworten auf ein Konto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent können z. b. an den Datenbankadministrator **danw@Adventure-Works.com** weitergeleitet werden.  
  
`[ @description = ] 'description'` ist eine Beschreibung für das Konto. die *Beschreibung* ist vom Datentyp **nvarchar (256)** und hat den Standardwert NULL.  
  
`[ @mailserver_name = ] 'server_name'` den Namen oder die IP-Adresse des SMTP-Mailservers, der für dieses Konto verwendet werden soll. Der Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, muss in der Lage sein, den *Servername* in eine IP-Adresse aufzulösen. *Servername* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @mailserver_type = ] 'server_type'` der Typ des e-Mail-Servers. *server_type* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **' SMTP '** .  
  
`[ @port = ] port_number` die Portnummer für den e-Mail-Server. *Portnummer* ist vom Datentyp **int**. der Standardwert ist 25.  
  
`[ @username = ] 'username'` den Benutzernamen, der für die Anmeldung beim e-Mail-Server verwendet werden soll. *username* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Wenn dieser Parameter NULL ist, verwendet Datenbank-E-Mail keine Authentifizierung für dieses Konto. Wenn für den Mailserver keine Authentifizierung erforderlich ist, verwenden Sie NULL als Wert für den Benutzernamen.  
  
`[ @password = ] 'password'` das Kennwort, das für die Anmeldung beim e-Mail-Server verwendet werden soll. *Password* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Ein Kennwort muss nur bereitgestellt werden, wenn ein Benutzername angegeben wird.  
  
`[ @use_default_credentials = ] use_default_credentials` gibt an, ob die e-Mail mit den Anmelde Informationen des [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] an den SMTP-Server gesendet werden soll. **use_default_credentials** ist vom Typ Bit. der Standardwert ist 0. Wenn dieser Parameter 1 ist, verwendet Datenbank-E-Mail die Anmeldeinformationen von [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Wenn dieser Parameter 0 ist, sendet Datenbank-E-Mail die Parameter " **\@username** " und " **\@password** ", falls vorhanden, und sendet andernfalls eine e-Mail ohne **\@Username-** und **\@password** -Parameter.  
  
`[ @enable_ssl = ] enable_ssl` gibt an, ob Datenbank-E-Mail die Kommunikation mit Secure Sockets Layer verschlüsselt. **Enable_ssl** ist vom Typ Bit. der Standardwert ist 0.  
  
`[ @account_id = ] account_id OUTPUT` gibt die Konto-ID für das neue Konto zurück. *account_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Datenbank-E-Mail stellt separate Parameter für **\@email_address**, **\@display_name**und **\@replyto_address**bereit. Der Parameter " **\@email_address** " ist die Adresse, von der die Nachricht gesendet wird. Der Parameter " **\@display_name** " ist der Name, der im Feld **from:** der e-Mail-Nachricht angezeigt wird. Der Parameter " **\@replyto_address** " ist die Adresse, an die Antworten auf die e-Mail-Nachricht gesendet werden. Beispiel: Ein Konto, das für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendet wird, soll E-Mail-Nachrichten von einer E-Mail-Adresse senden, die nur für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendet wird. Nachrichten von dieser Adresse sollen über einen Anzeigenamen verfügen, sodass die Empfänger problemlos feststellen können, dass die Nachricht vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent gesendet wurde. Wenn ein Empfänger auf die Nachricht antwortet, soll die Antwort an den Datenbankadministrator und nicht an die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendete Adresse gesendet werden. In diesem Szenario verwendet das Konto **SqlAgent@Adventure-Works.com** als e-Mail-Adresse. Der Anzeige Name ist auf **SQL Server-Agent automatisierten Mailer**festgelegt. Das Konto verwendet **danw@Adventure-Works.com** als Antwort auf die Adresse, sodass Antworten auf Nachrichten, die von diesem Konto gesendet werden, an den Datenbankadministrator anstatt an die e-Mail-Adresse für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent gesendet werden. Durch die Bereitstellung unabhängiger Einstellungen für diese drei Parameter ermöglicht es Datenbank-E-Mail Ihnen, die Konfiguration von Nachrichten an Ihre Anforderungen anzupassen.  
  
 Der **\@mailserver_type-** Parameter unterstützt den Wert **' SMTP '** .  
  
 Wenn **\@use_default_credentials** ist, wird eine e-Mail mit den Anmelde Informationen des [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] an den SMTP-Server gesendet. Wenn **\@use_default_credentials** den Wert 0 hat und ein **\@username** -und **\@password-Kennwort** für ein Konto angegeben ist, verwendet das Konto die SMTP-Authentifizierung. Die **\@username** und **\@password** sind die Anmelde Informationen, die das Konto für den SMTP-Server verwendet, nicht die Anmelde Informationen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder das Netzwerk, in dem sich der Computer befindet.  
  
 Die gespeicherte Prozedur **sysmail_add_account_sp** wird in der **msdb** -Datenbank gespeichert und befindet sich im Besitz des **dbo** -Schemas. Handelt es sich bei der aktuellen Datenbank nicht um **msdb**, muss die Prozedur mit einem dreiteiligen Namen ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Über die Ausführungsberechtigungen für diese Prozedur verfügen standardmäßig die Mitglieder der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Konto mit dem Namen `AdventureWorks Administrator` erstellt. Das Konto verwendet die E-Mail-Adresse `dba@Adventure-Works.com` und sendet E-Mail-Nachrichten an den SMTP-Mailserver `smtp.Adventure-Works.com`. E-Mail-Nachrichten, die von diesem Konto gesendet werden, werden `AdventureWorks Automated Mailer` in der Zeile **von:** der Nachricht angezeigt. Antworten auf Nachrichten von diesem Konto werden an `danw@Adventure-Works.com` gesendet.  
  
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
 [Erstellen Sie ein Datenbank-E-Mail Konto](../../relational-databases/database-mail/create-a-database-mail-account.md) .  
 [Datenbank-E-Mail gespeicherter &#40;Prozeduren (Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
