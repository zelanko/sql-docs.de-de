---
description: sp_help_operator (Transact-SQL)
title: sp_help_operator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_operator
- sp_help_operator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_operator
ms.assetid: caedc43d-44b8-415a-897e-92923f6de3b8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2cbf7c84c22998b5ee7e43fadad6a42cf02d17b8
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535380"
---
# <a name="sp_help_operator-transact-sql"></a>sp_help_operator (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu den für den Server definierten Operatoren zurück.  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_operator  
     { [ @operator_name = ] 'operator_name'   
     | [ @operator_id = ] operator_id }  
```  
  
## <a name="arguments"></a>Argumente  
`[ @operator_name = ] 'operator_name'` Der Name des Operators. *operator_name* ist vom **Datentyp vom Datentyp sysname**. Wenn *operator_name* nicht angegeben wird, werden Informationen zu allen Operatoren zurückgegeben.  
  
`[ @operator_id = ] operator_id` Die ID des Operators, für den Informationen angefordert werden. *operator_id*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *operator_id* oder *operator_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID des Operators.|  
|**name**|**sysname**|Der Operator Name.|  
|**enabled**|**tinyint**|Operator steht für den Empfang von Benachrichtigungen zur Verfügung:<br /><br /> **1** = Ja<br /><br /> **0** = Nein|  
|**email_address**|**nvarchar (100)**|E-Mail-Adresse des Operators.|  
|**last_email_date**|**int**|Datum, an dem der Operator zuletzt per E-Mail benachrichtigt wurde.|  
|**last_email_time**|**int**|Uhrzeit, zu der der Operator zuletzt per E-Mail benachrichtigt wurde.|  
|**pager_address**|**nvarchar (100)**|Pageradresse des Operators.|  
|**last_pager_date**|**int**|Datum, an dem der Operator zuletzt per Pager benachrichtigt wurde.|  
|**last_pager_time**|**int**|Uhrzeit, zu der der Operator zuletzt per Pager benachrichtigt wurde.|  
|**weekday_pager_start_time**|**int**|Der Beginn des Zeitraums, während dessen der Operator an Arbeitstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**weekday_pager_end_time**|**int**|Das Ende des Zeitraums, während dessen der Operator an Arbeitstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**saturday_pager_start_time**|**int**|Der Beginn des Zeitraums, während dessen der Operator an Samstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**saturday_pager_end_time**|**int**|Das Ende des Zeitraums, während dessen der Operator an Samstagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**sunday_pager_start_time**|**int**|Der Beginn des Zeitraums, während dessen der Operator an Sonntagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**sunday_pager_end_time**|**int**|Das Ende des Zeitraums, während dessen der Operator an Sonntagen zur Verfügung steht, um Pagerbenachrichtigungen zu empfangen.|  
|**pager_days**|**tinyint**|Eine Bitmaske (**1** = Sonntag, **64** = Samstag) der Wochentage, die anzeigt, wann der Operator verfügbar ist, um Pager-Benachrichtigungen zu empfangen.|  
|**netsend_address**|**nvarchar (100)**|Operatoradresse für Benachrichtigungen per Netzwerk-Popupnachricht.|  
|**last_netsend_date**|**int**|Datum, an dem der Operator zuletzt per Netzwerk-Popupnachricht benachrichtigt wurde.|  
|**last_netsend_time**|**int**|Uhrzeit, zu der der Operator zuletzt per Netzwerk-Popupnachricht benachrichtigt wurde.|  
|**category_name**|**sysname**|Name der Operatorkategorie, zu der dieser Operator gehört.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_help_operator** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zum `François Ajenstat`-Operator ausgegeben.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_operator  
    @operator_name = N'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_update_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
