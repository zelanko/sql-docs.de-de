---
title: DB-E-Mails und e-Mail-Benachrichtigungen mit SQL-Agent für Linux | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie DB E-Mails und e-Mail-Benachrichtigungen mit SQL Server unter Linux verwenden
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: tbd
ms.openlocfilehash: f9ce71d799414171019143912bde19330742ec27
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37984262"
---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>DB-E-Mails und e-Mail-Benachrichtigungen mit SQL-Agent für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Die folgenden Schritte zeigen das Einrichten von Datenbank-e-Mails und Ihre Verwendung mit SQL Server-Agent (**Mssql-Server-Agent**) unter Linux. 

## <a name="1-enable-db-mail"></a>1. Aktivieren von Datenbank-e-Mails

```sql
USE master 
GO 
sp_configure 'show advanced options',1 
GO 
RECONFIGURE WITH OVERRIDE 
GO 
sp_configure 'Database Mail XPs', 1 
GO 
RECONFIGURE  
GO  
```

## <a name="2-create-a-new-account"></a>2. Neues Konto erstellen
```sql
EXECUTE msdb.dbo.sysmail_add_account_sp 
@account_name = 'SQLAlerts', 
@description = 'Account for Automated DBA Notifications', 
@email_address = 'sqlagenttest@gmail.com', 
@replyto_address = 'sqlagenttest@gmail.com', 
@display_name = 'SQL Agent', 
@mailserver_name = 'smtp.gmail.com', 
@port = 587, 
@enable_ssl = 1, 
@username = 'sqlagenttest@gmail.com', 
@password = '<password>' 
GO
```

## <a name="3-create-a-default-profile"></a>3. Erstellen eines Standardprofils

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4. Fügen Sie die Database Mail-Konto ein Mailprofil für Datenbank
```sql
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp 
@profile_name = 'default', 
@principal_name = 'public', 
@is_default = 1 ; 
 ```
 
## <a name="5-add-account-to-profile"></a>5. Konto zum Profil hinzufügen 
```sql
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp   
@profile_name = 'default',   
@account_name = 'SQLAlerts',   
@sequence_number = 1;  
 ```
 
## <a name="6-send-test-email"></a>6. -E-Testmail senden
> [!NOTE]
> Möglicherweise müssen Sie wechseln zu Ihren e-Mail-Client, und aktivieren Sie die "zulassen unsicherer Clients zum Senden von e-Mails". Nicht alle Clients erkennen Datenbank-e-Mails als ein Daemon-e-Mail.

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7. Datenbank-Mailprofil mithilfe von Mssql-Conf oder die Umgebungsvariable festgelegt
Sie können die Mssql-Conf-Hilfsprogramm oder Umgebungsvariablen verwenden, um Ihre Datenbank-Mailprofil zu registrieren. In diesem Fall Wir nennen unseren standardmäßigen Profil.

```bash
# via mssql-conf
sudo /opt/mssql/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8. Richten Sie einen Operator für Benachrichtigungen zu Aufträgen für SQLAgent 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9. Senden Sie e-Mail, wenn "Agent-Test-Auftrag" erfolgreich abgeschlossen wurde 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zum Erstellen, Planen und Ausführen von Aufträgen mithilfe des SQL Server-Agents finden Sie unter [„Erstellen und Ausführen von SQL Server-Agent-Aufträgen unter Linux“](sql-server-linux-run-sql-server-agent-job.md).
