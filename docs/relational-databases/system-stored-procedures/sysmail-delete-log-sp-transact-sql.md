---
title: sysmail_delete_log_sp (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_log_sp_TSQL
- sysmail_delete_log_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_log_sp
ms.assetid: e94b37a1-70ad-46a5-86c0-721892156f7c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1aa837168c5aaff963a0b475596f4e6a4d3ff85f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807559"
---
# <a name="sysmail_delete_log_sp-transact-sql"></a>sysmail_delete_log_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht Ereignisse aus dem Datenbank-E-Mail-Protokoll. Es werden entweder alle Ereignisse im Protokoll gelöscht oder nur die Ereignisse, die einem Datums- oder Typkriterium entsprechen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sysmail_delete_log_sp  [ [ @logged_before = ] 'logged_before' ]  
    [, [ @event_type = ] 'event_type' ]  
  
```  
  
## <a name="arguments"></a>Argumente  
`[ @logged_before = ] 'logged_before'`Löscht Einträge bis zu dem Datum und der Uhrzeit, die durch das *logged_before* -Argument angegeben werden. *logged_before* ist vom Datentyp **datetime** . Der Standardwert ist NULL. NULL steht für alle Daten.  
  
`[ @event_type = ] 'event_type'`Löscht Protokolleinträge des als *event_type*angegebenen Typs. *event_type* ist vom Datentyp **varchar(15)** und besitzt keinen Standardwert. Gültige Einträge sind **success**, **warning**, **error**und **informational**. NULL steht für alle Ereignistypen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die gespeicherte Prozedur **sysmail_delete_log_sp** , um Einträge dauerhaft aus dem Datenbank-E-Mail-Protokoll zu löschen. Mithilfe eines optionalen Arguments können Sie nur ältere Datensätze löschen, indem Sie ein Datum und eine Uhrzeit angeben. Ereignisse, die älter sind als dieses Argument, werden gelöscht. Mithilfe eines optionalen Arguments können Sie nur Ereignisse eines bestimmten Typs löschen. Diese werden als **event_type** -Argument angegeben.  
  
 Durch Löschen der Einträge im Datenbank-E-Mail-Protokoll werden die E-Mail-Einträge nicht aus den Datenbank-E-Mail-Tabellen gelöscht. Verwenden Sie [sysmail_delete_mailitems_sp](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md) , um E-Mails aus den Datenbank-E-Mail-Tabellen zu löschen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Prozedur zugreifen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-deleting-all-events"></a>A. Löschen aller Ereignisse  
 Im folgenden Beispiel werden alle Ereignisse im Datenbank-E-Mail-Protokoll gelöscht.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp ;  
GO  
```  
  
### <a name="b-deleting-the-oldest-events"></a>B. Löschen der ältesten Ereignisse  
 Im folgenden Beispiel werden Ereignisse im Datenbank-E-Mail-Protokoll gelöscht, die vor dem 9. Oktober 2005 liegen.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @logged_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-events-of-a-certain-type"></a>C. Löschen aller Ereignisse eines bestimmten Typs  
 Im folgenden Beispiel werden Erfolgsmeldungen im Datenbank-E-Mail-Protokoll gelöscht.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @event_type = 'success' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sysmail_event_log &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_delete_mailitems_sp &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)   
 [Erstellen eines Auftrags des SQL Server-Agents zum Archivieren von Datenbank-E-Mail-Nachrichten und Ereignisprotokollen](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
