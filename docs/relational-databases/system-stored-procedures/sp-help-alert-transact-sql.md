---
title: sp_help_alert (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_alert
- sp_help_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_alert
ms.assetid: 850cef4e-6348-4439-8e79-fd1bca712091
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 08569c2313bfb7c9d992c510ef4c9c7548f51e64
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827743"
---
# <a name="sp_help_alert-transact-sql"></a>sp_help_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu den für einen Server definierten Warnungen zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_alert [ [ @alert_name = ] 'alert_name' ]   
     [ , [ @order_by = ] 'order_by' ]   
     [ , [ @alert_id = ] alert_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @legacy_format = ] legacy_format ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @alert_name = ] 'alert_name'`Der Name der Warnung. *alert_name* ist vom Datentyp **nvarchar (128)**. Wenn *alert_name* nicht angegeben wird, werden Informationen zu allen Warnungen zurückgegeben.  
  
`[ @order_by = ] 'order_by'`Die Sortierreihenfolge, die zum Erzeugen der Ergebnisse verwendet werden soll. *ORDER_BY*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert N '*Name*'.  
  
`[ @alert_id = ] alert_id`Die ID der Warnung, zu der Informationen gemeldet werden sollen. *alert_id*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @category_name = ] 'category'`Die Kategorie für die Warnung. *Category* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @legacy_format = ] legacy_format`Gibt an, ob ein Legacy-Resultset erzeugt werden soll. *legacy_format* ist vom Typ **Bit**. der Standardwert ist **0**. Wenn *legacy_format* **1**ist, gibt **sp_help_alert** das Resultset zurück, das von **sp_help_alert** in Microsoft SQL Server 2000 zurückgegeben wurde.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn ** \@ legacy_format** **0**ist, erstellt **sp_help_alert** das folgende Resultset.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Vom System zugewiesener eindeutiger, ganzzahliger Bezeichner.|  
|**name**|**sysname**|Der Name der Warnung (z. b. Demo: vollständiges **msdb** -Protokoll).|  
|**event_source**|**nvarchar (100)**|Quelle des Ereignisses. Es ist immer **MSSQLSERVER** für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7,0.|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Fehlernummer der Meldung, die die Warnung definiert. (Entspricht in der Regel einer Fehlernummer in der Tabelle **sysmess** .) Wenn der Schweregrad zum Definieren der Warnung verwendet wird, ist **message_id** **0** oder NULL.|  
|**severity**|**int**|Der Schweregrad (von **9** bis **25**, **110**, **120**, **130**oder **140**), der die Warnung definiert.|  
|**wodurch**|**tinyint**|Status gibt an, ob die Warnung derzeit aktiviert ist (**1**) oder nicht (**0**). Eine nicht aktivierte Warnung wird nicht gesendet.|  
|**delay_between_responses**|**int**|Wartezeit in Sekunden zwischen Antworten auf die Warnung.|  
|**last_occurrence_date**|**int**|Datum, an dem die Warnung zuletzt aufgetreten ist.|  
|**last_occurrence_time**|**int**|Uhrzeit, zu der die Warnung zuletzt aufgetreten ist.|  
|**last_response_date**|**int**|Datum, an dem die Warnung zuletzt vom **SQLServerAgent** -Dienst beantwortet wurde.|  
|**last_response_time**|**int**|Zeitpunkt, zu dem die Warnung zuletzt vom **SQLServerAgent** -Dienst beantwortet wurde.|  
|**notification_message**|**nvarchar(512)**|Optionale zusätzliche Meldung, die als Teil einer Benachrichtigung per E-Mail oder Pager an den Operator gesendet wird.|  
|**include_event_description**|**tinyint**|Gibt an, ob die Beschreibung des SQL Server-Fehlers in das Microsoft Windows-Anwendungsprotokoll als Teil der Benachrichtigungsmeldung eingeschlossen werden soll.|  
|**database_name**|**sysname**|Datenbank, in der der Fehler auftreten muss, damit die Warnung ausgelöst wird. Wenn der Datenbankname gleich NULL ist, wird die Warnung unabhängig von der Datenbank ausgelöst, in der der Fehler aufgetreten ist.|  
|**event_description_keyword**|**nvarchar (100)**|Beschreibung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlers im Windows-Anwendungsprotokoll, die der angegebenen Zeichenfolge entsprechen muss.|  
|**occurrence_count**|**int**|Gibt an, wie oft die Warnung aufgetreten ist.|  
|**count_reset_date**|**int**|Datum, an dem der **occurrence_count** zuletzt zurückgesetzt wurde.|  
|**count_reset_time**|**int**|Uhrzeit, zu der die **occurrence_count** zuletzt zurückgesetzt wurde.|  
|**job_id**|**uniqueidentifier**|ID des Auftrags, der als Antwort auf eine Warnung ausgeführt werden soll.|  
|**job_name**|**sysname**|Name des Auftrags, der als Antwort auf eine Warnung ausgeführt werden soll.|  
|**has_notification**|**int**|Ungleich 0, wenn einer oder mehrere Operatoren für diese Warnung benachrichtigt werden. Der Wert ist einer oder mehrere der folgenden Werte (ORed):<br /><br /> **1**= e-Mail-Benachrichtigung<br /><br /> **2**= Pager-Benachrichtigung<br /><br /> **4**= hat eine **net send** -Benachrichtigung.|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performance_condition**|**nvarchar(512)**|Wenn **type** der Typ **2**ist, wird in dieser Spalte die Definition der Leistungs Bedingung angezeigt. Andernfalls ist die Spalte NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Ist für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 immer '[Uncategorized]'.|  
|**wmi_namespace**|**sysname**|Wenn **type** der Typ **3**ist, wird in dieser Spalte der Namespace für das WMI-Ereignis angezeigt.|  
|**wmi_query**|**nvarchar(512)**|Wenn **type** der Typ **3**ist, wird in dieser Spalte die Abfrage für das WMI-Ereignis angezeigt.|  
|**type**|**int**|Typ des Ereignisses:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ereignis Warnung<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Leistungs Warnung<br /><br /> **3** = WMI-Ereignis Warnung|  
  
 Wenn ** \@ legacy_format** **1**ist, erstellt **sp_help_alert** das folgende Resultset.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Vom System zugewiesener eindeutiger, ganzzahliger Bezeichner.|  
|**name**|**sysname**|Der Name der Warnung (z. b. Demo: vollständiges **msdb** -Protokoll).|  
|**event_source**|**nvarchar (100)**|Quelle des Ereignisses. Es ist immer **MSSQLSERVER** für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7,0.|  
|**event_category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**int**|Fehlernummer der Meldung, die die Warnung definiert. (Entspricht in der Regel einer Fehlernummer in der Tabelle **sysmess** .) Wenn der Schweregrad zum Definieren der Warnung verwendet wird, ist **message_id** **0** oder NULL.|  
|**severity**|**int**|Der Schweregrad (von **9** bis **25**, **110**, **120**, **130**oder 1**40**), der die Warnung definiert.|  
|**wodurch**|**tinyint**|Status gibt an, ob die Warnung derzeit aktiviert ist (**1**) oder nicht (**0**). Eine nicht aktivierte Warnung wird nicht gesendet.|  
|**delay_between_responses**|**int**|Wartezeit in Sekunden zwischen Antworten auf die Warnung.|  
|**last_occurrence_date**|**int**|Datum, an dem die Warnung zuletzt aufgetreten ist.|  
|**last_occurrence_time**|**int**|Uhrzeit, zu der die Warnung zuletzt aufgetreten ist.|  
|**last_response_date**|**int**|Datum, an dem die Warnung zuletzt vom **SQLServerAgent** -Dienst beantwortet wurde.|  
|**last_response_time**|**int**|Zeitpunkt, zu dem die Warnung zuletzt vom **SQLServerAgent** -Dienst beantwortet wurde.|  
|**notification_message**|**nvarchar(512)**|Optionale zusätzliche Meldung, die als Teil einer Benachrichtigung per E-Mail oder Pager an den Operator gesendet wird.|  
|**include_event_description**|**tinyint**|Gibt an, ob die Beschreibung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlers in das Windows-Anwendungsprotokoll als Teil der Benachrichtigungsmeldung eingeschlossen werden soll.|  
|**database_name**|**sysname**|Datenbank, in der der Fehler auftreten muss, damit die Warnung ausgelöst wird. Wenn der Datenbankname gleich NULL ist, wird die Warnung unabhängig von der Datenbank ausgelöst, in der der Fehler aufgetreten ist.|  
|**event_description_keyword**|**nvarchar (100)**|Beschreibung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlers im Windows-Anwendungsprotokoll, die der angegebenen Zeichenfolge entsprechen muss.|  
|**occurrence_count**|**int**|Gibt an, wie oft die Warnung aufgetreten ist.|  
|**count_reset_date**|**int**|Datum, an dem der **occurrence_count** zuletzt zurückgesetzt wurde.|  
|**count_reset_time**|**int**|Uhrzeit, zu der die **occurrence_count** zuletzt zurückgesetzt wurde.|  
|**job_id**|**uniqueidentifier**|Identifikationsnummer des Auftrags.|  
|**job_name**|**sysname**|Ein bedarfsgesteuerter Auftrag, der als Antwort auf eine Warnung ausgeführt werden soll.|  
|**has_notification**|**int**|Ungleich 0, wenn einer oder mehrere Operatoren für diese Warnung benachrichtigt werden. Einer oder mehrere der folgenden Werte sind möglich (mit OR verknüpft):<br /><br /> **1**= e-Mail-Benachrichtigung<br /><br /> **2**= Pager-Benachrichtigung<br /><br /> **4**= hat eine **net send** -Benachrichtigung.|  
|**flags**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)].|  
|**performance_condition**|**nvarchar(512)**|Wenn **type** der Typ **2**ist, wird in dieser Spalte die Definition der Leistungs Bedingung angezeigt. Wenn **type** der Typ **3**ist, wird in dieser Spalte die Abfrage für das WMI-Ereignis angezeigt. Andernfalls weist die Spalte den Wert NULL auf.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]Ist für 7,0 immer "**[nicht kategorisiert]**" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|**type**|**int**|Warnungstyp:<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ereignis Warnung<br /><br /> **2**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Leistungs Warnung<br /><br /> **3** = WMI-Ereignis Warnung|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_help_alert** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
 Ausführliche Informationen zu **SQLAgentOperatorRole**finden Sie unter [SQL Server-Agent fester Daten bankrollen](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zur Warnung `Demo: Sev. 25 Errors` abgerufen.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sp_add_alert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
