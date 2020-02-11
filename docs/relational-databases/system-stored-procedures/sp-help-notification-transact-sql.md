---
title: sp_help_notification (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_notification
- sp_help_notification_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_notification
ms.assetid: 0273457f-9d2a-4a6f-9a16-6a6bf281cba0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 630c2f90085cedfbb5c59ba395c7d0d9ae9d9643
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67906105"
---
# <a name="sp_help_notification-transact-sql"></a>sp_help_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste der Warnungen für einen bestimmten Operator oder eine Liste der Operatoren für eine bestimmte Warnung zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_notification  
     [ @object_type = ] 'object_type' ,  
     [ @name = ] 'name' ,  
     [ @enum_type = ] 'enum_type' ,   
     [ @notification_method = ] notification_method   
     [ , [ @target_name = ] 'target_name' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @object_type = ] 'object_type'`Der Typ der Informationen, die zurückgegeben werden sollen. *object_type*ist vom Typ **char (9)** und hat keinen Standardwert. *object_type* kann eine Warnung sein, in der die Warnungen aufgelistet werden, die dem angegebenen Operator Namen oder den Operatoren zugewiesen*sind, die* die für den angegebenen Warnungs Namen verantwortlichen Operatoren auflistet *.*  
  
`[ @name = ] 'name'`Ein Operator Name (wenn *object_type* ist Operatoren) oder ein Warnungs Name (wenn *object_type* Warnungen ist). *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @enum_type = ] 'enum_type'`Die *object_type*Informationen, die zurückgegeben werden. *enum_type* ist in den meisten Fällen tatsächlich. *enum_type*ist vom Typ **char (10)** und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|ACTUAL|Listet nur die *object_types* auf, die dem *Namen*zugeordnet sind.|  
|ALL|Listet alle*object_types* auf, einschließlich derjenigen, die nicht mit dem *Namen*verknüpft sind.|  
|TARGET|Listet nur die *object_types* auf, die mit dem angegebenen *target_name*übereinstimmen, unabhängig von der Zuordnung mit dem*Namen*.|  
  
`[ @notification_method = ] notification_method`Ein numerischer Wert, der die zurück zugebende Benachrichtigungs Methoden Spalten bestimmt. *notification_method* ist vom Datentyp **tinyint**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|E-Mail: gibt nur die **use_email** Spalte zurück.|  
|**2**|Pager: gibt nur die **use_pager** Spalte zurück.|  
|**4**|Nettsend: gibt nur die **use_netsend** Spalte zurück.|  
|**19.00**|Alle: Alle Spalten werden zurückgegeben.|  
  
`[ @target_name = ] 'target_name'`Ein Warnungs Name, nach dem gesucht werden soll (wenn *object_type* Warnungen ist), oder ein Operator Name, nach dem gesucht werden soll (wenn *object_type* Operator ist). *target_name* ist nur erforderlich, wenn *enum_type* Ziel ist. *target_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-valves"></a>Rückgabe Code Ventile  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *object_type* **Warnungen**sind, listet das Resultset alle Warnungen für einen bestimmten Operator auf.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|Benachrichtigungs-ID-Nummer.|  
|**alert_name**|**sysname**|Name der Warnung.|  
|**use_email**|**int**|E-Mail wird zur Benachrichtigung des Operators verwendet:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**use_pager**|**int**|Pager wird zur Benachrichtigung des Operators verwendet:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**use_netsend**|**int**|Eine Netzwerk-Popupnachricht wird zur Benachrichtigung des Operators verwendet:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**has_email**|**int**|Anzahl von E-Mail-Benachrichtigungen, die für diese Warnung gesendet wurden.|  
|**has_pager**|**int**|Anzahl von Pagerbenachrichtigungen, die für diese Warnung gesendet wurden.|  
|**has_netsend**|**int**|Anzahl der für diese Warnung gesendeten **net send** -Benachrichtigungen.|  
  
 Wenn **object_type** **Operator**ist, listet das Resultset alle Operatoren für eine bestimmte Warnung auf.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**operator_id**|**int**|ID des Operators.|  
|**operator_name**|**sysname**|Name des Operators|  
|**use_email**|**int**|E-Mail wird zum Senden der Benachrichtigung des Operators verwendet:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**use_pager**|**int**|Pager wird zum Senden der Benachrichtigung des Operators verwendet:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**use_netsend**|**int**|Ist ein Netzwerk-Popup, das verwendet wird, um den Operator zu benachrichtigen:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**has_email**|**int**|Operator besitzt eine E-Mail-Adresse:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**has_pager**|**int**|Operator besitzt eine Pageradresse:<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
|**has_netsend**|**int**|Für den Operator wurde eine net send-Benachrichtigung konfiguriert.<br /><br /> **1** = ja<br /><br /> **0** = Nein|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese gespeicherte Prozedur muss von der **msdb** -Datenbank aus ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss ein Benutzer Mitglied der festen Serverrolle **sysadmin** sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-alerts-for-a-specific-operator"></a>A. Auflisten von Warnungen für einen bestimmten Operator  
 Im folgenden Beispiel werden alle Warnungen zurückgegeben, für die der Operator `François Ajenstat` eine Benachrichtigung beliebigen Typs erhält.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_notification   
    @object_type = N'ALERTS',  
    @name = N'François Ajenstat',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
### <a name="b-listing-operators-for-a-specific-alert"></a>B. Auflisten von Operatoren für eine bestimmte Warnung  
 Im folgenden Beispiel werden alle Operatoren zurückgegeben, die eine Benachrichtigung beliebigen Typs für die `Test Alert`-Warnung erhalten.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_notification  
    @object_type = N'OPERATORS',  
    @name = N'Test Alert',  
    @enum_type = N'ACTUAL',  
    @notification_method = 7 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
