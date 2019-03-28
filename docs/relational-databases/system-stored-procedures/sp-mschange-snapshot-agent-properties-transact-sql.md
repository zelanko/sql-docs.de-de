---
title: Sp_MSchange_snapshot_agent_properties (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_snapshot_agent_properties_TSQL
- sp_MSchange_snapshot_agent_properties
helpviewer_keywords:
- sp_MSchange_snapshot_agent_properties
ms.assetid: 7947a788-3fd7-469f-84db-b03ba89a153c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f5c9091e3a949e5a358f5bd1305d096491782012
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58537313"
---
# <a name="spmschangesnapshotagentproperties-transact-sql"></a>sp_MSchange_snapshot_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Eigenschaften einer Momentaufnahme-Agentauftrag, der ausgeführt wird ein [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder einer höheren Version Verteiler. Diese gespeicherte Prozedur wird verwendet, um Eigenschaften zu ändern, wenn der Verleger auf einer Instanz von ausgeführt wird [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_MSchange_snapshot_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @frequency_type= ] frequency_type  
        , [ @frequency_interval= ] frequency_interval  
        , [ @frequency_subday= ] frequency_subday  
        , [ @frequency_subday_interval= ] frequency_subday_interval  
        , [ @frequency_relative_interval= ] frequency_relative_interval  
        , [ @frequency_recurrence_factor= ] frequency_recurrence_factor  
        , [ @active_start_date= ] active_start_date  
        , [ @active_end_date= ] active_end_date  
        , [ @active_start_time_of_day= ] active_start_time_of_day  
        , [ @active_end_time_of_day= ] active_end_time_of_day  
        , [ @snapshot_job_name = ] 'snapshot_agent_name'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit, mit der der Momentaufnahme-Agent ausgeführt wird. *Frequency_type* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Bedarfsgesteuert|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**10**|Monatlicher Zeitplan|  
|**20**|Monatlich, relativ zum Häufigkeitsintervall|  
|**40**|Beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents|  
  
`[ @frequency_interval = ] frequency_interval` Ist der Wert der Häufigkeit festgelegt, die durch Anwenden *Frequency_type*. *Frequency_interval* ist **Int**, hat keinen Standardwert.  
  
`[ @frequency_subday = ] frequency_subday` Die Einheiten für *Freq_subday_interval*. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat keinen Standardwert.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum aus, denen, das der Momentaufnahme-Agent ausgeführt wird. *Frequency_relative_interval* ist **Int**, hat keinen Standardwert.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat keinen Standardwert.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an der Momentaufnahme-Agent zuerst ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat keinen Standardwert.  
  
`[ @active_end_date = ] active_end_date` Das Datum, ab der Momentaufnahme-Agent nicht mehr, ist geplant ist YYYYMMDD formatiert. *Active_end_date* ist **Int**, hat keinen Standardwert.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit aus, wenn der erste der Momentaufnahme-Agent ist, erfolgt Format: HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat keinen Standardwert.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Momentaufnahme-Agent nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat keinen Standardwert.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` Ist der Name der Name eines vorhandenen Momentaufnahme-Agent-Auftrags an, wenn ein vorhandener Auftrag verwendet wird. *Snapshot_agent_name* ist **nvarchar(100)**, hat keinen Standardwert.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Der Sicherheitsmodus wird vom Agent verwendet werden, Herstellen der Verbindung mit dem Verleger. *Publisher_security_mode* ist **Int**, hat keinen Standardwert. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung und **1** gibt die Windows-Authentifizierung. Der Wert **0** muss angegeben werden, für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Der Benutzername, der verwendet wird, Herstellen der Verbindung mit dem Verleger. *Publisher_login* ist **Sysname**, hat keinen Standardwert. *Publisher_login* muss angegeben werden, wenn *Publisher_security_mode* ist **0**. Wenn *Publisher_login* ist NULL und Herausgeber *_ ** Security_mode* ist **1**, und klicken Sie dann das angegebene Windows-Konto *Job_login* werden Beim Verbinden mit dem Verleger verwendet.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort wird verwendet werden, wenn eine Verbindung mit dem Verleger herstellen. *Publisher_password* ist **nvarchar(524)**, hat keinen Standardwert.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Es wird empfohlen, Anmeldenamen und Kennwörter zur Laufzeit bereitzustellen, um die Sicherheit zu verbessern.  
  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_login* ist **nvarchar(257)**, hat keinen Standardwert. Das Windows-Konto wird stets für Agent-Verbindungen mit dem Verteiler verwendet. Sie müssen diesen Parameter angeben, wenn Sie einen neuen Auftrag des Momentaufnahme-Agents erstellen. *Dies kann nicht geändert werden, für einen nicht-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *Verleger.*  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert. Sie müssen diesen Parameter angeben, wenn Sie einen neuen Auftrag des Momentaufnahme-Agents erstellen.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Es wird empfohlen, Anmeldenamen und Kennwörter zur Laufzeit bereitzustellen, um die Sicherheit zu verbessern.  
  
`[ @publisher_type = ] 'publisher_type'` Gibt den verlegertyp an, wenn der Verleger nicht, in einer Instanz von ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Publisher_type* ist **Sysname**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Gibt einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger an.|  
|**ORACLE**|Gibt einen standardmäßigen Oracle-Verleger an.|  
|**ORACLE-GATEWAY**|Gibt einen Oracle Gateway-Verleger an.|  
  
 Weitere Informationen zu den Unterschieden zwischen einem Oracle-Verleger und einem Oracle Gateway-Verleger finden Sie unter [Oracle-Veröffentlichung (Übersicht)](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_MSchange_snapshot_agent_properties** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
 Sie müssen alle Parameter angeben, für die Ausführung **Sp_MSchange_snapshot_agent_properties**. Führen Sie [Sp_helppublication_snapshot](../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md) auf die aktuellen Eigenschaften des Momentaufnahme-Agent-Auftrags zurückzugeben.  
  
 Wenn der Verleger ausgeführt wird, auf einer Instanz von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher, verwenden Sie [Sp_changepublication_snapshot](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md) so ändern Sie die Eigenschaften eines Auftrags des Momentaufnahme-Agents.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle auf dem Verteiler **Sp_MSchange_snapshot_agent_properties**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
  
