---
title: sysmail_delete_mailitems_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_mailitems_sp_TSQL
- sysmail_delete_mailitems_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_mailitems_sp
ms.assetid: f87c9f4a-bda1-4bce-84b2-a055a3229ecd
author: stevestein
ms.author: sstein
ms.openlocfilehash: df7ae090efbcd448dc5df3df5355273c891da4fe
ms.sourcegitcommit: c2052b2bf7261b3294a3a40e8fed8b9e9c588c37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941173"
---
# <a name="sysmail_delete_mailitems_sp-transact-sql"></a>sysmail_delete_mailitems_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht E-Mail-Nachrichten dauerhaft aus den internen Tabellen der Datenbank-E-Mail.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_delete_mailitems_sp  [ [ @sent_before = ] 'sent_before' ]  
    [ , [ @sent_status = ] 'sent_status' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @sent_before = ] 'sent_before'`Löscht e-Mails bis zu dem Datum und der Uhrzeit, die als *sent_before* -Argument angegeben sind. Das Argument *sent_before* ist vom Datentyp **datetime**und hat den Standardwert NULL. NULL steht für alle Daten.  
  
`[ @sent_status = ] 'sent_status'`Löscht e-Mails des Typs, der durch *sent_status*angegeben wird. Das Argument *sent_status* ist vom Datentyp **varchar(8)** ohne Standardwert. Gültige Einträge sind **sent**, **unsent**, **retrying**, und **failed**. NULL steht für alle Status.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Datenbank-E-Mail-Nachrichten und deren Anlagen werden in der **msdb** Datenbank gespeichert. Nachrichten sollten in regelmäßigen Abständen gelöscht werden, um zu verhindern, dass **msdb** sehr groß wird. Zur Einhaltung eventueller Aufbewahrungspflichten verwenden Sie ein für Sie in Frage kommendes Dokumentenmanagement. Mithilfe der gespeicherten Prozedur **sysmail_delete_mailitems_sp** können Sie E-Mail-Nachrichten dauerhaft aus den Datenbank-E-Mail-Tabellen löschen. Über ein optionales Argument können Sie nur ältere E-Mails löschen, indem Sie ein Datum und eine Uhrzeit angeben. E-Mails, die älter sind als dieses Argument, werden gelöscht. Sie müssen zwingend mindestens ein Argument angeben, also entweder **@sent_before** oder **@sent_status**. Sie müssen für  **\@sent_before** oder  **\@sent_status**ein Argument angeben. Um alle Nachrichten zu löschen, verwenden  **\@Sie sent_before = getdate ()** .  
  
 Mit den E-Mails werden auch die Anlagen gelöscht, die zu diesen Nachrichten gehören. Das Löschen der E-Mails löscht allerdings keine entsprechenden Einträge in **sysmail_event_log**. Um Elemente aus dem Protokoll zu löschen, verwenden Sie die gespeicherte Prozedur [sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig besitzen nur Mitglieder der **sysadmin** -Serverrolle und der **DatabaseMailUserRole** die Berechtigungen zur Ausführung der Prozedur. Mitglieder der **Sssadmin** -Serverrolle können über diese Prozedur sämtliche E-Mails löschen, unabhängig vom Benutzer, der die E-Mail gesendet hat. Mitglieder der **DatabaseMailUserRole** können nur die von ihrem eigenen Benutzer gesendeten E-Mails löschen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-deleting-all-e-mails"></a>A. Löschen aller E-Mails  
 Im folgenden Beispiel werden alle E-Mails im Datenbank-E-Mail-System gelöscht.  
  
```  
DECLARE @GETDATE datetime  
SET @GETDATE = GETDATE();  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @GETDATE;  
GO  
```  
  
### <a name="b-deleting-the-oldest-e-mails"></a>B. Löschen der ältesten E-Mails  
 Im folgenden Beispiel werden E-Mail-Nachrichten im Datenbank-E-Mail-Protokoll gelöscht, die vor dem Datum `October 9, 2005` gesendet wurden.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-e-mails-of-a-certain-type"></a>C. Löschen aller E-Mails eines bestimmten Typs  
 Im folgenden Beispiel werden alle fehlerhaften E-Mails im Datenbank-E-Mail-Protokoll gelöscht.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_status = 'failed' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_event_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_mailattachments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md)   
 [Erstellen eines Auftrags des SQL Server-Agents zum Archivieren von Datenbank-E-Mail-Nachrichten und Ereignisprotokollen](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
