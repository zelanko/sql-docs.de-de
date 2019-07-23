---
title: DROP EVENT NOTIFICATION (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP EVENT NOTIFICATION
- DROP_EVENT_NOTIFICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event notifications [SQL Server], removing
- deleting event notifications
- dropping event notifications
- DROP EVENT NOTIFICATION statement
- removing event notifications
ms.assetid: 0ffd8f47-4ea3-4238-9e73-c318df710cf7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: befa0085a7fc1a52ae02ba9443617b0593bb14ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67910052"
---
# <a name="drop-event-notification-transact-sql"></a>DROP EVENT NOTIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt einen Ereignisbenachrichtigungstrigger aus der aktuellen Datenbank.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP EVENT NOTIFICATION notification_name [ ,...n ]  
ON { SERVER | DATABASE | QUEUE queue_name }  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 *notification_name*  
 Der Name der zu entfernenden Ereignisbenachrichtigung. Es können mehrere Ereignisbenachrichtigungen angegeben werden. Verwenden Sie [sys.event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md), um eine Liste der aktuell erstellten Ereignisbenachrichtigungen anzuzeigen.  
  
 SERVER  
 Gibt den Bereich der Ereignisbenachrichtigungsanwendungen auf den aktuellen Server an. SERVER muss angegeben werden, wenn SERVER beim Erstellen der Ereignisbenachrichtigung angegeben wurde.  
  
 DATABASE  
 Gibt den Bereich der Ereignisbenachrichtigungsanwendungen auf die aktuelle Datenbank an. DATABASE muss angegeben werden, wenn DATABASE beim Erstellen der Ereignisbenachrichtigung angegeben wurde.  
  
 QUEUE *queue_name*  
 Gibt den Bereich der Ereignisbenachrichtigungsanwendungen auf die durch *queue_name* angegebene Warteschlange an. QUEUE musst angegebenen werden, wenn das Element beim Erstellen der Ereignisbenachrichtigung angegeben wurde. *queue_name* ist der Name der Warteschlange und muss ebenfalls angegeben werden.  
  
## <a name="remarks"></a>Remarks  
 Wenn eine Ereignisbenachrichtigung innerhalb einer Transaktion ausgelöst und innerhalb derselben Transaktion gelöscht wird, wird die Ereignisbenachrichtigungsinstanz gesendet und die Ereignisbenachrichtigung dann gelöscht.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Löschen einer Ereignisbenachrichtigung, deren Bereich auf Datenbankebene definiert ist, muss ein Benutzer mindestens Besitzer der Ereignisbenachrichtigung sein oder über die ALTER ANY DATABASE EVENT NOTIFICATION-Berechtigung für die aktuelle Datenbank verfügen.  
  
 Zum Löschen einer Ereignisbenachrichtigung, deren Bereich auf Serverebene definiert ist, muss ein Benutzer mindestens Besitzer der Ereignisbenachrichtigung sein oder über die ALTER ANY EVENT NOTIFICATION-Berechtigung für den Server verfügen.  
  
 Um eine Ereignisbenachrichtigung für eine bestimmte Warteschlange zu löschen, muss ein Benutzer mindestens Besitzer der Ereignisbenachrichtigung sein oder über die ALTER-Berechtigung für die übergeordnete Warteschlange verfügen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Ereignisbenachrichtigung erstellt und dann gelöscht, deren Bereich eine bestimmte Datenbank ist.  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE EVENT NOTIFICATION NotifyALTER_T1  
ON DATABASE  
FOR ALTER_TABLE  
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984';  
GO  
DROP EVENT NOTIFICATION NotifyALTER_T1  
ON DATABASE;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-notification-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)   
 [sys.events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-events-transact-sql.md)  
  
  
