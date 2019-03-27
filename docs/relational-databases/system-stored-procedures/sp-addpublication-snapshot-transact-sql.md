---
title: Sp_addpublication_snapshot (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpublication_snapshot_TSQL
- sp_addpublication_snapshot
helpviewer_keywords:
- sp_addpublication_snapshot
ms.assetid: 192b6214-df6e-44a3-bdd4-9d933a981619
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35b18161e9d0022e0f7df29498a94c40646a5055
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493974"
---
# <a name="spaddpublicationsnapshot-transact-sql"></a>sp_addpublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Erstellt den Momentaufnahme-Agent für die angegebene Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addpublication_snapshot [ @publication= ] 'publication'  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @snapshot_job_name = ] 'snapshot_agent_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit, mit der der Momentaufnahme-Agent ausgeführt wird. *Frequency_type* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal.|  
|**4** (Standard)|Pro Tag.|  
|**8**|Wöchentlich|  
|**16**|Monatlich|  
|**32**|Monatlich, relativ zum Häufigkeitsintervall.|  
|**64**|Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent gestartet wird.|  
|**128**|Ausführen, wenn sich der Computer im Leerlauf befindet|  
  
`[ @frequency_interval = ] frequency_interval` Ist der Wert der Häufigkeit festgelegt, die durch Anwenden *Frequency_type*. *Frequency_interval* ist **Int**, und kann einen der folgenden Werte.  
  
|Wert für frequency_type|Auswirkung auf frequency_interval|  
|------------------------------|-----------------------------------|  
|**1**|*Frequency_interval* wird nicht verwendet.|  
|**4** (Standard)|Jede *Frequency_interval* Tage; der Standard ist täglich.|  
|**8**|*Frequency_interval* kann einen oder mehrere der folgenden (in Kombination mit einem [ &#124; (bitweises OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) logischen Operator):<br /><br /> **1** = Sonntag&#124;<br /><br /> **2** = Monday &#124;<br /><br /> **4** = Dienstag&#124;<br /><br /> **8** = Mittwoch&#124;<br /><br /> **16** = Thursday &#124;<br /><br /> **32** = Freitag&#124;<br /><br /> **64** = Samstag|  
|**16**|Auf der *Frequency_interval* Tag des Monats.|  
|**32**|*Frequency_interval* ist eine der folgenden:<br /><br /> **1** = Sonntag&#124;<br /><br /> **2** = Monday &#124;<br /><br /> **3** = Dienstag&#124;<br /><br /> **4** = Mittwoch&#124;<br /><br /> **5** = Thursday &#124;<br /><br /> **6** = Freitag&#124;<br /><br /> **7** = Samstag&#124;<br /><br /> **8** = Tag&#124;<br /><br /> **9** = Arbeitstag&#124;<br /><br /> **10** = Wochenendtag|  
|**64**|*Frequency_interval* wird nicht verwendet.|  
|**128**|*Frequency_interval* wird nicht verwendet.|  
  
`[ @frequency_subday = ] frequency_subday` Die Einheit für *Freq_subday_interval*. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4** (Standard)|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert von 5, womit alle 5 Minuten.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum aus, denen, das der Momentaufnahme-Agent ausgeführt wird. *Frequency_relative_interval* ist **Int**, hat den Standardwert 1.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert 0.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an der Momentaufnahme-Agent zuerst ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert 0.  
  
`[ @active_end_date = ] active_end_date` Das Datum, ab der Momentaufnahme-Agent nicht mehr, ist geplant ist YYYYMMDD formatiert. *Active_end_date* ist **Int**, hat den Standardwert 99991231, womit der 31. Dezember 9999.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit aus, wenn der erste der Momentaufnahme-Agent ist, erfolgt Format: HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert 0.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Momentaufnahme-Agent nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert 235959, womit 23:59:59 Uhr auf dem 24-Stunden-Format an.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` Ist der Name der Name eines vorhandenen Momentaufnahme-Agent-Auftrags an, wenn ein vorhandener Auftrag verwendet wird. *Snapshot_agent_name* ist **nvarchar(100)** hat den Standardwert NULL. Dieser Parameter dient der internen Verwendung und sollte beim Erstellen einer neuen Veröffentlichung nicht angegeben werden. Wenn *Snapshot_agent_name* angegeben ist, klicken Sie dann *Job_login* und *Job_password* muss NULL sein.  
  
`[ @publisher_security_mode = ] publisher_security_mode` Der Sicherheitsmodus wird vom Agent verwendet werden, Herstellen der Verbindung mit dem Verleger. *Publisher_security_mode* ist **Smallint**, hat den Standardwert 1. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung und **1** gibt die Windows-Authentifizierung. Der Wert **0** muss angegeben werden, für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` Der Benutzername, der verwendet wird, Herstellen der Verbindung mit dem Verleger. *Publisher_login* ist **Sysname**, hat den Standardwert NULL. *Publisher_login* muss angegeben werden, wenn *Publisher_security_mode* ist **0**. Wenn *Publisher_login* ist NULL und *Publisher_security_mode* ist **1**, und klicken Sie dann das angegebene Konto *Job_login* wird verwendet werden, wenn Herstellen einer Verbindung mit dem Verleger.  
  
`[ @publisher_password = ] 'publisher_password'` Das Kennwort wird verwendet werden, wenn eine Verbindung mit dem Verleger herstellen. *Publisher_password* ist **Sysname**, hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Es wird empfohlen, Anmeldenamen und Kennwörter zur Laufzeit bereitzustellen, um die Sicherheit zu verbessern.  
  
`[ @job_login = ] 'job_login'` Ist der Anmeldename für das Konto, unter dem der Agent ausgeführt wird. Verwenden Sie bei Azure SQL-Datenbank verwaltete Instanzen ein SQL Server-Konto. *Job_login* ist **nvarchar(257)**, hat den Standardwert NULL. Dieses Konto wird immer für agentverbindungen mit dem Verteiler verwendet. Sie müssen diesen Parameter angeben, wenn Sie einen neuen Auftrag des Momentaufnahme-Agents erstellen.  
  
> [!NOTE]
>  Für nicht - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber, dies muss die gleiche Anmeldung, die im angegebenen [Sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
`[ @job_password = ] 'job_password'` Ist das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *Job_password* ist **Sysname**, hat keinen Standardwert. Sie müssen diesen Parameter angeben, wenn Sie einen neuen Auftrag des Momentaufnahme-Agents erstellen.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Es wird empfohlen, Anmeldenamen und Kennwörter zur Laufzeit bereitzustellen, um die Sicherheit zu verbessern.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, beim Erstellen einer Momentaufnahme-Agent auf einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addpublication_snapshot** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-snapsh_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addpublication_snapshot**.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Erstellen und Anwenden der Momentaufnahme](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_startpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
