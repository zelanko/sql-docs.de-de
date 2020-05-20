---
title: sp_help_jobactivity (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobactivity_TSQL
- sp_help_jobactivity
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobactivity
ms.assetid: d344864f-b4d3-46b1-8933-b81dec71f511
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 755ba9552945e0e983fa5eef6cc53de1c29be5e3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827635"
---
# <a name="sp_help_jobactivity-transact-sql"></a>sp_help_jobactivity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet Informationen zum Laufzeitstatus von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Aufträgen auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobactivity { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @session_id = ] session_id ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die Auftrags-ID. *job_id*ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags. *job_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @session_id = ] session_id`Die Sitzungs-ID, zu der Informationen gemeldet werden sollen. *session_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt das folgende Resultset zurück:  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Agent-Sitzungs-ID.|  
|**job_id**|**uniqueidentifier**|ID für den Auftrag.|  
|**job_name**|**sysname**|Der Name des Auftrags.|  
|**run_requested_date**|**datetime**|Datum, zu dem die Ausführung des Auftrags angefordert wurde.|  
|**run_requested_source**|**sysname**|Die Quelle der Anforderung zum Ausführen des Auftrags. Enthält einen der folgenden Werte:<br /><br /> **1** = nach einem Zeitplan ausführen<br /><br /> **2** = ausführen als Reaktion auf eine Warnung<br /><br /> **3** = beim Start ausführen<br /><br /> **4** = ausführen nach Benutzer<br /><br /> **6** = Ausführung mit CPU-Leerlauf Zeitplan|  
|**queued_date**|**datetime**|Datum, an dem die Anforderung in die Warteschlange aufgenommen wurde. NULL, wenn der Auftrag direkt ausgeführt wurde.|  
|**start_execution_date**|**datetime**|Datum, an dem der Auftrag einem ausführbaren Thread zugewiesen wurde.|  
|**last_executed_step_id**|**int**|Die Schritt-ID des zuletzt ausgeführten Auftragsschritts.|  
|**last_executed_step_date**|**datetime**|Uhrzeit, zu der die Ausführung des zuletzt ausgeführten Auftragsschritts begonnen hat.|  
|**stop_execution_date**|**datetime**|Uhrzeit, zu der die Ausführung des Auftrags beendet wurde.|  
|**next_scheduled_run_date**|**datetime**|Datum, an dem die nächste Ausführung des Auftrags geplant ist.|  
|**job_history_id**|**int**|ID für den Auftragsverlauf in der Auftragsverlaufstabelle.|  
|**Nachricht**|**nvarchar(1024)**|Meldung, die während der letzten Ausführung des Auftrags ausgegeben wurde.|  
|**run_status**|**int**|Status, der während der letzten Ausführung des Auftrags zurückgegeben wurde:<br /><br /> **0** = Fehler<br /><br /> **1** = erfolgreich<br /><br /> **3** = abgebrochen<br /><br /> **5** = Unbekannter Status|  
|**operator_id_emailed**|**int**|ID des Operators, der durch eine E-Mail-Nachricht bei Beendigung des Auftrags benachrichtigt wurde.|  
|**operator_id_netsent**|**int**|ID-Nummer des Operators, der bei Abschluss des Auftrags über **net send** benachrichtigt wurde.|  
|**operator_id_paged**|**int**|ID des Operators, der durch einen Pager bei Beendigung des Auftrags benachrichtigt wurde.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Prozedur stellt eine Momentaufnahme des aktuellen Status des Auftrags bereit. Die zurückgegebenen Ergebnisse stellen Informationen zu dem Zeitpunkt der Anforderungsverarbeitung dar.  
  
 Vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent wird bei jedem Start des Agent-Diensts eine Sitzungs-ID erstellt. Die Sitzungs-ID wird in der **msdb. dbo. syssessions**-Tabelle gespeichert.  
  
 Wenn keine *session_id* bereitgestellt wird, werden Informationen über die letzte Sitzung aufgelistet.  
  
 Wenn keine *job_name* oder *job_id* bereitgestellt wird, werden Informationen zu allen Aufträgen aufgeführt.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **sysadmin** -Rolle können die Aktivität für Aufträge anzeigen, die sich im Besitz anderer Benutzer befinden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel ist die Aktivität für alle Aufträge aufgeführt, zu deren Anzeige der Benutzer berechtigt ist.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobactivity ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
