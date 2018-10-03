---
title: Sysmail_mailattachments (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_mailattachments_TSQL
- sysmail_mailattachments
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_mailattachments database mail view
ms.assetid: aee87059-a4c1-459a-a95c-641b4e3f0e73
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c263f7e3df69b6eb3d9517b2dc973a1cb4102f7d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627308"
---
# <a name="sysmailmailattachments-transact-sql"></a>sysmail_mailattachments (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Anlage, die an die Datenbank-E-Mail übermittelt wurde. Verwenden Sie diese Sicht, wenn Sie Informationen zu Datenbank-E-Mail-Anlagen benötigen. Überprüfen Sie alle e-Mail-Nachrichten verarbeitet werden, mithilfe der Database Mail [Sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md).  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**attachment_id**|**int**|Der Bezeichner für die Anlage.|  
|**mailitem_id**|**int**|Der Bezeichner für das E-Mail-Element, das die Anlage enthält.|  
|**Dateiname**|**nvarchar(520)**|Der Dateiname der Anlage. Wenn **Attach_query_result** 1 und **Query_attachment_filename** NULL ist, Datenbank-e-Mails erstellt einen beliebigen Dateinamen.|  
|**filesize**|**int**|Die Größe der Anlage in Bytes.|  
|**attachment**|**varbinary(max)**|Der Inhalt der Anlage.|  
|**last_mod_date**|**datetime**|Das Datum und die Uhrzeit der letzten Änderung der Zeile.|  
|**last_mod_user**|**sysname**|Der Benutzer, der die Zeile zuletzt geändert hat.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie Probleme mit der Datenbank-E-Mail behandeln, können Sie diese Sicht verwenden, um die Eigenschaften der Anlagen anzuzeigen.  
  
 In den Systemtabellen gespeicherte Anlagen können dazu führen, dass die **Msdb** Datenbank vergrößert werden. Verwendung **Sysmail_delete_mailitems_sp** e-Mail-Elemente und die zugehörigen Anlagen zu löschen. Weitere Informationen finden Sie unter [erstellen Sie einen Auftrag des SQL Server-Agents zum Archivieren von Datenbank e-Mail-Nachrichten und Ereignisprotokollen](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Gewährt den **Sysadmin** Serverrolle und die **DatabaseMailUserRole** -Datenbankrolle. Beim Ausführen von einem Mitglied der **Sysadmin** festen Serverrolle in dieser Ansicht werden alle Anlagen. Für alle anderen Benutzer werden nur die von ihnen übermittelten Anlagen angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [sysmail_allitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_faileditems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)   
 [sysmail_sentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md)   
 [sysmail_unsentitems &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md)   
 [sysmail_event_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)  
  
  
