---
title: sp_help_jobhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a04d651467b8ccff057d3dcec0cb824edae73b12
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893688"
---
# <a name="sp_help_jobhistory-transact-sql"></a>sp_help_jobhistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Stellt Informationen zu den Aufträgen für Server in der Domäne zur Multiserveradministration bereit.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die Auftrags-ID. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @step_id = ] step_id`Die Schritt-ID. *step_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @sql_message_id = ] sql_message_id`Die ID der Fehlermeldung, die von Microsoft SQL Server beim Ausführen des Auftrags zurückgegeben wird. *sql_message_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @sql_severity = ] sql_severity`Der Schweregrad der Fehlermeldung, die von SQL Server beim Ausführen des Auftrags zurückgegeben wird. *sql_severity* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @start_run_date = ] start_run_date`Das Datum, an dem der Auftrag gestartet wurde. *start_run_date*ist vom Datentyp **int**und hat den Standardwert NULL. *start_run_date* muss im Format YYYYMMDD eingegeben werden, wobei yyyy ein vierjähriges Jahr ist, mm ein aus zwei Zeichen bestehende Monats Name und DD ein zwei Zeichen täglicher Name ist.  
  
`[ @end_run_date = ] end_run_date`Das Datum, an dem der Auftrag abgeschlossen wurde. *end_run_date* ist vom Datentyp **int**und hat den Standardwert NULL. *end_run_date*muss im Format YYYYMMDD eingegeben werden, wobei yyyy ein vierstelliges Jahr ist, mm ein aus zwei Zeichen bestehenden Monatsnamen und DD ein zwei Zeichen täglicher Name ist.  
  
`[ @start_run_time = ] start_run_time`Der Zeitpunkt, zu dem der Auftrag gestartet wurde. *start_run_time* ist vom Datentyp **int**und hat den Standardwert NULL. *start_run_time*muss im Format HHMMSS eingegeben werden, wobei HH eine aus zwei Zeichen bestehende Stunden Angabe, mm eine aus zwei Zeichen bestehende Minuten Angabe und SS eine aus zwei Zeichen bestehende Sekunde des Tages ist.  
  
`[ @end_run_time = ] end_run_time`Der Zeitpunkt, zu dem die Ausführung des Auftrags abgeschlossen wurde. *end_run_time* ist vom Datentyp **int**und hat den Standardwert NULL. *end_run_time*muss im Format HHMMSS eingegeben werden, wobei HH eine aus zwei Zeichen bestehende Stunden Angabe, mm eine aus zwei Zeichen bestehende Minuten Angabe und SS eine aus zwei Zeichen bestehende Sekunde des Tages ist.  
  
`[ @minimum_run_duration = ] minimum_run_duration`Die minimale Zeitspanne für den Abschluss des Auftrags. *minimum_run_duration* ist vom Datentyp **int**und hat den Standardwert NULL. *minimum_run_duration*muss im Format HHMMSS eingegeben werden, wobei HH eine aus zwei Zeichen bestehende Stunden Angabe, mm eine aus zwei Zeichen bestehende Minuten Angabe und SS eine aus zwei Zeichen bestehende Sekunde des Tages ist.  
  
`[ @run_status = ] run_status`Der Ausführungs Status des Auftrags. *run_status* ist vom Datentyp **int**und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**0**|Fehler|  
|**1**|Erfolgreich|  
|**2**|Wiederholen (nur Schritte)|  
|**3**|Canceled|  
|**4**|In Bearbeitung befindliche Nachricht|  
|**5**|Unbekannt|  
  
`[ @minimum_retries = ] minimum_retries`Die Mindestanzahl der Wiederholungs Versuche für einen Auftrag. *minimum_retries* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @oldest_first = ] oldest_first`Gibt an, ob die Ausgabe zuerst mit den ältesten Aufträgen angezeigt werden soll. *oldest_first* ist vom Datentyp **int**. der Standardwert ist **0**, wodurch zuerst die neuesten Aufträge dargestellt werden. **1** zeigt zuerst die ältesten Aufträge an.  
  
`[ @server = ] 'server'`Der Name des Servers, auf dem der Auftrag ausgeführt wurde. der *Server* ist vom Datentyp **nvarchar (30)** und hat den Standardwert NULL.  
  
`[ @mode = ] 'mode'`Gibt an, ob SQL Server alle Spalten im Resultset (**Full**) oder eine Zusammenfassung der Spalten ausgibt. der *Modus* ist vom Datentyp **varchar (7)** und hat den Standardwert **Summary**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Die tatsächliche Spaltenliste hängt vom Wert des- *Modus*ab. Der umfassendste Satz von Spalten wird unten angezeigt und wird zurückgegeben, wenn der *Modus* voll ist.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|Verlaufseintrags-ID|  
|**job_id**|**uniqueidentifier**|Identifikationsnummer des Auftrags.|  
|**job_name**|**sysname**|Auftrags Name.|  
|**step_id**|**int**|Schritt-ID (ist **0** für einen Auftrags Verlauf).|  
|**step_name**|**sysname**|Schrittname (NULL für einen Auftragsverlauf).|  
|**sql_message_id**|**int**|Für [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritte die letzte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Fehlernummer, die beim Ausführen des Befehls gemeldet wurde.|  
|**sql_severity**|**int**|Für [!INCLUDE[tsql](../../includes/tsql-md.md)]-Schritte der höchste [!INCLUDE[tsql](../../includes/tsql-md.md)]-Fehlerschweregrad, der beim Ausführen des Befehls gemeldet wurde.|  
|**Nachricht**|**nvarchar(1024)**|Meldung zu Auftrags- oder Schrittverlauf.|  
|**run_status**|**int**|Ergebnis des Auftrags oder Schritts.|  
|**run_date**|**int**|Datum, an dem das Ausführen des Auftrags oder Schritts begann.|  
|**run_time**|**int**|Uhrzeit, zu der das Ausführen des Auftrags oder Schritts begann.|  
|**run_duration**|**int**|Vergangene Ausführungszeit des Auftrags oder Schritts im Format HHMMSS.|  
|**operator_emailed**|**nvarchar (20)**|Operator, der bezüglich dieses Auftrags per E-Mail benachrichtigt wurde (NULL für Schrittverlauf).|  
|**operator_netsent**|**nvarchar (20)**|Operator, dem bezüglich dieses Auftrags eine Netzwerknachricht gesendet wurde (NULL für Schrittverlauf).|  
|**operator_paged**|**nvarchar (20)**|Operator, der bezüglich dieses Auftrags per Pager benachrichtigt wurde (NULL für Schrittverlauf).|  
|**retries_attempted**|**int**|Die Wiederholungsversuche für den Schritt (für einen Auftragsverlauf immer 0).|  
|**server**|**nvarchar(30)**|Server, auf dem der Schritt oder Auftrag ausgeführt wird. Ist immer (**local**).|  
  
## <a name="remarks"></a>Hinweise  
 **sp_help_jobhistory** gibt einen Bericht mit dem Verlauf der angegebenen geplanten Aufträge zurück. Werden keine Parameter angegeben, enthält der Bericht den Verlauf aller geplanten Aufträge.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Mitglieder der **SQLAgentUserRole** -Daten Bank Rolle können nur den Verlauf für Aufträge anzeigen, deren Besitzer Sie sind.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. Auflisten aller Auftragsinformationen für einen Auftrag  
 Im folgenden Beispiel werden alle Auftragsinformationen für den `NightlyBackups`-Auftrag aufgelistet.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>B. Auflisten von Informationen für Aufträge, die bestimmte Bedingungen erfüllen  
 Im folgenden Beispiel werden alle Spalten und alle Auftragsinformationen für alle fehlgeschlagenen Aufträge und fehlgeschlagenen Auftragsschritte mit der Fehlermeldung `50100` (eine benutzerdefinierte Fehlermeldung) und einem Schweregrad von `20` aufgelistet.  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_purge_jobhistory &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
