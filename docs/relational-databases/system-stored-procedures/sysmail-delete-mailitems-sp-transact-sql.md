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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9619ee410e0df014961e9f46a7e536508e0616c1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85639488"
---
# <a name="sysmail_delete_mailitems_sp-transact-sql"></a>sysmail_delete_mailitems_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Löscht E-Mail-Nachrichten dauerhaft aus den internen Tabellen der Datenbank-E-Mail.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_delete_mailitems_sp  [ [ @sent_before = ] 'sent_before' ]  
    [ , [ @sent_status = ] 'sent_status' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ \@sent_before = ] 'sent_before'`Löscht e-Mails bis zu dem Datum und der Uhrzeit, die als *sent_before* Argument angegeben werden. *sent_before* ist vom **Datentyp DateTime** und hat den Standardwert NULL. NULL steht für alle Daten.  
  
`[ \@sent_status = ] 'sent_status'`Löscht e-Mails des Typs, der durch *sent_status*angegeben wird. *sent_status* ist vom Datentyp **varchar (8)** und hat keinen Standardwert. Gültige Einträge werden **gesendet**, **unsent** **nicht**gesendet, **wiederholt**und sind fehlerhaft. NULL steht für alle Status.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Datenbank-E-Mail Meldungen und deren Anhänge werden in der **msdb** -Datenbank gespeichert. Nachrichten sollten in regelmäßigen Abständen gelöscht werden, um zu verhindern, dass **msdb** größer als erwartet wird, und dass Sie dem Dokument Aufbewahrungs Programm Ihrer Organisation entsprechen. Verwenden Sie die gespeicherte Prozedur **sysmail_delete_mailitems_sp** , um e-Mail-Nachrichten dauerhaft aus den Datenbank-E-Mail Tabellen zu löschen. Mithilfe eines optionalen Arguments können Sie nur ältere E-Mails löschen, indem Sie ein Datum und eine Uhrzeit angeben. E-Mails, die älter sind als dieses Argument, werden gelöscht. Ein weiteres optionales Argument ermöglicht es Ihnen, nur e-Mails eines bestimmten Typs zu löschen, die als **sent_status** Argument angegeben sind. Sie müssen für ** \@ sent_before** oder ** \@ sent_status**ein Argument angeben. Um alle Nachrichten zu löschen, verwenden Sie ** \@ sent_before = getdate ()**.  
  
 Mit den E-Mails werden auch die Anlagen gelöscht, die zu diesen Nachrichten gehören. Beim Löschen von e-Mail werden die entsprechenden Einträge in **sysmail_event_log**nicht gelöscht. Verwenden Sie [sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md) , um Elemente aus dem Protokoll zu löschen.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig wird dieser gespeicherten Prozedur die Ausführung für Mitglieder von der festen Server Rolle **sysadmin** und **DatabaseMailUserRole**erteilt. Mitglieder der festen Server Rolle **sysadmin** können diese Prozedur ausführen, um e-Mails zu löschen, die von allen Benutzern gesendet werden. Mitglieder von **DatabaseMailUserRole** können nur die von diesem Benutzer gesendeten e-Mails löschen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sysmail_allitems &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_event_log &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_mailattachments &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md)   
 [Erstellen eines Auftrags des SQL Server-Agents zum Archivieren von Datenbank-E-Mail-Nachrichten und Ereignisprotokollen](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
