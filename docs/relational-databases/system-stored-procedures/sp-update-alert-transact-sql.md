---
description: sp_update_alert (Transact-SQL)
title: sp_update_alert (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_alert_TSQL
- sp_update_alert
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_alert
ms.assetid: 4bbaeaab-8aca-4c9e-abc1-82ce73090bd3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a7abcc7d0f4ad148f18e90a29a8f411804e0d4a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446722"
---
# <a name="sp_update_alert-transact-sql"></a>sp_update_alert (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Aktualisiert die Einstellungen einer vorhandenen Warnung.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_update_alert   
     [ @name =] 'name'   
     [ , [ @new_name =] 'new_name']   
     [ , [ @enabled =] enabled]   
     [ , [ @message_id =] message_id]   
     [ , [ @severity =] severity]   
     [ , [ @delay_between_responses =] delay_between_responses]   
     [ , [ @notification_message =] 'notification_message']   
     [ , [ @include_event_description_in =] include_event_description_in]   
     [ , [ @database_name =] 'database']   
     [ , [ @event_description_keyword =] 'event_description_keyword']   
     [ , [ @job_id =] job_id | [@job_name =] 'job_name']   
     [ , [ @occurrence_count = ] occurrence_count]   
     [ , [ @count_reset_date =] count_reset_date]   
     [ , [ @count_reset_time =] count_reset_time]   
     [ , [ @last_occurrence_date =] last_occurrence_date]   
     [ , [ @last_occurrence_time =] last_occurrence_time]   
     [ , [ @last_response_date =] last_response_date]   
     [ , [ @last_response_time =] last_response _time]  
     [ , [ @raise_snmp_trap =] raise_snmp_trap]  
     [ , [ @performance_condition =] 'performance_condition' ]   
     [ , [ @category_name =] 'category']  
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'` Der Name der Warnung, die aktualisiert werden soll. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @new_name = ] 'new_name'` Ein neuer Name für die Warnung. Der Name muss eindeutig sein. *new_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @enabled = ] enabled` Gibt an, ob die Warnung aktiviert (**1**) oder nicht aktiviert (**0**) ist. *aktiviert* ist vom Datentyp **tinyint**. der Standardwert ist NULL. Eine Warnung muss aktiviert sein, um ausgelöst werden zu können.  
  
`[ @message_id = ] message_id` Eine neue Meldung oder Fehlernummer für die Warnungs Definition. In der Regel entspricht *message_id* einer Fehlernummer in der **sysmess** -Tabelle. *message_id* ist vom Datentyp **int**und hat den Standardwert NULL. Eine Nachrichten-ID kann nur verwendet werden, wenn die Einstellung für den Schweregrad für die Warnung den Wert **0**hat.  
  
`[ @severity = ] severity` Ein neuer Schweregrad (von **1** bis **25**) für die Warnungs Definition. Jede [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Nachricht, die mit dem angegebenen Schweregrad an das Windows-Anwendungsprotokoll gesendet wird, aktiviert die Warnung. der *Schweregrad* ist vom Datentyp **int**und hat den Standardwert NULL. Ein Schweregrad kann nur verwendet werden, wenn die Einstellung für die Nachrichten-ID für die Warnung den Wert **0**hat.  
  
`[ @delay_between_responses = ] delay_between_responses` Die Neue Wartezeit (in Sekunden) zwischen den Antworten auf die Warnung. *delay_between_responses* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @notification_message = ] 'notification_message'` Der überarbeitete Text einer zusätzlichen Nachricht, die als Teil der e-Mail-, **net send**-oder Pager-Benachrichtigung an den Operator gesendet wurde. *notification_message* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL.  
  
`[ @include_event_description_in = ] include_event_description_in` Gibt an, ob die Beschreibung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlers aus dem Windows-Anwendungsprotokoll in die Benachrichtigungs Meldung eingeschlossen werden soll. *include_event_description_in* ist vom Datentyp **tinyint**. der Standardwert ist NULL. die folgenden Werte sind möglich.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Keine|  
|**1**|E-Mail|  
|**2**|Pager|  
|**4**|**NET SEND**|  
|**7**|All|  
  
`[ @database_name = ] 'database'` Der Name der Datenbank, in der der Fehler auftreten muss, damit die Warnung ausgelöst wird. *Database* ist vom **Datentyp sysname.** In eckige Klammern ([ ]) eingeschlossene Namen sind nicht zulässig. Der Standardwert ist NULL.  
  
`[ @event_description_keyword = ] 'event_description_keyword'` Eine Sequenz von Zeichen, die in der Beschreibung des Fehlers im Fehlermeldungs Protokoll gefunden werden muss. Zulässig sind Zeichen, die dem Muster des LIKE-Ausdrucks von [!INCLUDE[tsql](../../includes/tsql-md.md)] entsprechen. *event_description_keyword* ist vom Datentyp **nvarchar (100)** und hat den Standardwert NULL. Dieser Parameter ist nützlich zum Filtern von Objektnamen (z. b. **% customer_table%**).  
  
`[ @job_id = ] job_id` Die Auftrags-ID. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL. Wenn *job_id* angegeben wird, müssen *job_name* ausgelassen werden.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags, der als Reaktion auf diese Warnung ausgeführt wird. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *job_name* angegeben wird, müssen *job_id* ausgelassen werden.  
  
`[ @occurrence_count = ] occurrence_count` Gibt zurück, wie oft die Warnung aufgetreten ist. *occurrence_count* ist vom Datentyp **int**und hat den Standardwert NULL. der Wert kann nur auf **0**festgelegt werden.  
  
`[ @count_reset_date = ] count_reset_date` Setzt das Datum zurück, an dem die Anzahl der Vorkommen zuletzt zurückgesetzt wurde. *count_reset_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @count_reset_time = ] count_reset_time` Setzt die Uhrzeit zurück, zu der die Anzahl der Vorkommen zuletzt zurückgesetzt wurde. *count_reset_time* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @last_occurrence_date = ] last_occurrence_date` Setzt das Datum zurück, an dem die Warnung zuletzt aufgetreten ist. *last_occurrence_date* ist vom Datentyp **int**und hat den Standardwert NULL. der Wert kann nur auf **0**festgelegt werden.  
  
`[ @last_occurrence_time = ] last_occurrence_time` Setzt die Uhrzeit zurück, zu der die Warnung zuletzt aufgetreten ist. *last_occurrence_time* ist vom Datentyp **int**und hat den Standardwert NULL. der Wert kann nur auf **0**festgelegt werden.  
  
`[ @last_response_date = ] last_response_date` Setzt das Datum zurück, an dem die Warnung zuletzt vom SQLServerAgent-Dienst beantwortet wurde. *last_response_date* ist vom Datentyp **int**und hat den Standardwert NULL. der Wert kann nur auf **0**festgelegt werden.  
  
`[ @last_response_time = ] last_response_time` Setzt die Uhrzeit zurück, zu der die Warnung zuletzt vom SQLServerAgent-Dienst beantwortet wurde. *last_response_time* ist vom Datentyp **int**und hat den Standardwert NULL. der Wert kann nur auf **0**festgelegt werden.  
  
`[ @raise_snmp_trap = ] raise_snmp_trap` Bleiben.  
  
`[ @performance_condition = ] 'performance_condition'` Ein Wert im Format **'**_itemcomparatorvalue_**'**. *performance_condition* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL und besteht aus diesen Elementen.  
  
|Format-Element|Beschreibung|  
|--------------------|-----------------|  
|*Item*|Ein Leistungsobjekt, ein Leistungsindikator oder die benannte Instanz des Indikators|  
|*Vergleichs Operator*|Einer dieser Operatoren: **>** , **<** , **=**|  
|*Wert*|Numerischer Wert des Indikators|  
  
`[ @category_name = ] 'category'` Der Name der Warnungs Kategorie. *Category* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL.  
  
`[ @wmi_namespace = ] 'wmi_namespace'` Der WMI-Namespace, der nach Ereignissen abgefragt werden soll. *wmi_namespace* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @wmi_query = ] 'wmi_query'` Die Abfrage, die das WMI-Ereignis für die Warnung angibt. *wmi_query* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Nur **sysmess** -Dateien, die in das Windows-Anwendungsprotokoll geschrieben werden, [!INCLUDE[msCoName](../../includes/msconame-md.md)] können eine Warnung auslösen.  
  
 **sp_update_alert** ändert nur die Warnungs Einstellungen, für die Parameterwerte angegeben werden. Wird ein Parameter nicht angegeben, wird die aktuelle Einstellung beibehalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur müssen Benutzer ein Mitglied der festen Server Rolle **sysadmin** sein.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Aktivierungseinstellung von `Test Alert` in `0` geändert.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_alert  
    @name = N'Test Alert',  
    @enabled = 0 ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
