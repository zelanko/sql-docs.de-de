---
title: Sp_help_notification (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: d003b1f15500b1f6d0b8490d9e712a6a34b100a3
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538632"
---
# <a name="sphelpnotification-transact-sql"></a>sp_help_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste der Warnungen für einen bestimmten Operator oder eine Liste der Operatoren für eine bestimmte Warnung zurück.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @object_type = ] 'object_type'` Der Typ der zurückzugebenden Informationen. *Object_type*ist **char(9)**, hat keinen Standardwert. *Object_type* sind ALERTS, womit die dem angegebenen Operator zugewiesenen Warnungen aufgelistet *,* oder OPERATORS, womit die für die angegebene Warnung verantwortlichen Operatoren aufgelistet *.*  
  
`[ @name = ] 'name'` Ein Operatorname (Wenn *Object_type* is-OPERATOREN) oder ein Warnungsname (Wenn *Object_type* gleich ALERTS ist). *Namen* ist **Sysname**, hat keinen Standardwert.  
  
`[ @enum_type = ] 'enum_type'` Die *Object_type*Informationen, die zurückgegeben wird. *Enum_type* tatsächlich in den meisten Fällen ist. *Enum_type*ist **char(10)** und hat keinen Standardwert und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|ACTUAL|Listet nur die *object_types auf* zugeordneten *Namen*.|  
|ALL|Listet alle die*object_types auf* einschließlich derer, die nicht zugeordnet sind *Namen*.|  
|TARGET|Listet nur die *object_types auf* Übereinstimmung den angegebenen *Target_name*, unabhängig von der Zuordnung mit*Namen*.|  
  
`[ @notification_method = ] notification_method` Ein numerischer Wert, der die zurückzugebenden Spalten der Benachrichtigungsmethode bestimmt. *Notification_method* ist **Tinyint**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|E-Mail-Adresse: Gibt nur die **Use_email** Spalte.|  
|**2**|Pager: Gibt nur die **Use_pager** Spalte.|  
|**4**|NetSend: Gibt nur die **Use_netsend** Spalte.|  
|**7**|Alle: Alle Spalten werden zurückgegeben.|  
  
`[ @target_name = ] 'target_name'` Der Name einer Warnung zu suchende (Wenn *Object_type* gleich ALERTS ist) oder ein Operatorname, nach suchen (Wenn *Object_type* is-OPERATOREN). *Target_name* ist nur erforderlich, wenn *Enum_type* Ziel. *Target_name* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="return-code-valves"></a>Rückgabecode Ventilen  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *Object_type* ist **WARNUNGEN**, das Resultset Listet alle Warnungen für einen bestimmten Operator.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID der Warnung.|  
|**alert_name**|**sysname**|Name der Warnung.|  
|**use_email**|**int**|E-Mail wird zur Benachrichtigung des Operators verwendet:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**use_pager**|**int**|Pager wird zur Benachrichtigung des Operators verwendet:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**use_netsend**|**int**|Eine Netzwerk-Popupnachricht wird zur Benachrichtigung des Operators verwendet:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**has_email**|**int**|Anzahl von E-Mail-Benachrichtigungen, die für diese Warnung gesendet wurden.|  
|**has_pager**|**int**|Anzahl von Pagerbenachrichtigungen, die für diese Warnung gesendet wurden.|  
|**has_netsend**|**int**|Anzahl der **net Send** Benachrichtigungen, die für diese Warnung gesendet.|  
  
 Wenn **Object_type** ist **OPERATOREN**, das Resultset werden alle Operatoren für eine bestimmte Warnung aufgelistet.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**operator_id**|**int**|Operator-ID.|  
|**operator_name**|**sysname**|Name des Operators|  
|**use_email**|**int**|E-Mail wird zum Senden der Benachrichtigung des Operators verwendet:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**use_pager**|**int**|Pager wird zum Senden der Benachrichtigung des Operators verwendet:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**use_netsend**|**int**|Eine Netzwerk-Popupnachricht wird zur Benachrichtigung des Operators verwendet werden:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**has_email**|**int**|Operator besitzt eine E-Mail-Adresse:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**has_pager**|**int**|Operator besitzt eine Pageradresse:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**has_netsend**|**int**|Für den Operator wurde eine net send-Benachrichtigung konfiguriert.<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
  
## <a name="remarks"></a>Hinweise  
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
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
