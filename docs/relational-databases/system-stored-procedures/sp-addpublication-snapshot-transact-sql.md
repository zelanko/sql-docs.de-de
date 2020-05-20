---
title: sp_addpublication_snapshot (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3447b9111ec6d6a6fd6a4084f884647cbd38eec2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820683"
---
# <a name="sp_addpublication_snapshot-transact-sql"></a>sp_addpublication_snapshot (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt den Momentaufnahme-Agent für die angegebene Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
> [!IMPORTANT]  
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der die Momentaufnahmen-Agent ausgeführt wird. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmal.|  
|**4** (Standard)|Tä.|  
|**8**|Wöchentlich|  
|**Uhr**|Monatlich.|  
|**32**|Monatlich, relativ zum Häufigkeitsintervall.|  
|**64**|Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent gestartet wird.|  
|**128**|Ausführen, wenn sich der Computer im Leerlauf befindet|  
  
`[ @frequency_interval = ] frequency_interval`Der Wert, der auf die von *frequency_type*festgelegte Häufigkeit angewendet werden soll. *frequency_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert für frequency_type|Auswirkung auf frequency_interval|  
|------------------------------|-----------------------------------|  
|**1**|*frequency_interval* wird nicht verwendet.|  
|**4** (Standard)|Alle *frequency_interval* Tage, wobei der Standardwert täglich ist.|  
|**8**|*frequency_interval* ist eine oder mehrere der folgenden (kombiniert mit einem [&#124; (bitweisen OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) logischen Operator):<br /><br /> **1** = Sonntag &#124;<br /><br /> **2** = Montag &#124;<br /><br /> **4** = Dienstag &#124;<br /><br /> **8** = Mittwoch &#124;<br /><br /> **16** = Donnerstag &#124;<br /><br /> **32** = Freitag &#124;<br /><br /> **64** = Samstag|  
|**Uhr**|Am *frequency_interval* Tag des Monats.|  
|**32**|*frequency_interval* ist einer der folgenden:<br /><br /> **1** = Sonntag &#124;<br /><br /> **2** = Montag &#124;<br /><br /> **3** = Dienstag &#124;<br /><br /> **4** = Mittwoch &#124;<br /><br /> **5** = Donnerstag &#124;<br /><br /> **6** = Freitag &#124;<br /><br /> **7** = Samstag &#124;<br /><br /> **8** = Tag &#124;<br /><br /> **9** = wochentags&#124;<br /><br /> **10** = Wochenendtag|  
|**64**|*frequency_interval* wird nicht verwendet.|  
|**128**|*frequency_interval* wird nicht verwendet.|  
  
`[ @frequency_subday = ] frequency_subday`Ist die Einheit für *freq_subday_interval*. *frequency_subday* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|Sekunde|  
|**4** (Standard)|Minute|  
|**8**|Stunde|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für die *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert 5. Dies bedeutet alle 5 Minuten.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum, an dem die Momentaufnahmen-Agent ausgeführt wird. *frequency_relative_interval* ist vom Datentyp **int**und hat den Standardwert 1.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem die Momentaufnahmen-Agent zum ersten Mal geplant ist, formatiert als YYYYMMDD. *active_start_date* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Momentaufnahmen-Agent nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**und hat den Standardwert 99991231, was bedeutet, dass der 31. Dezember 9999.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der die Momentaufnahmen-Agent zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert 0.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der die Momentaufnahmen-Agent nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert 235959, was bedeutet 11:59:59 Uhr. gemessen auf einem 24-Stunden-Format.  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'`Der Name eines vorhandenen Momentaufnahmen-Agent Auftrags namens, wenn ein vorhandener Auftrag verwendet wird. *snapshot_agent_name* ist vom Datentyp **nvarchar (100)** und hat den Standardwert NULL. Dieser Parameter dient der internen Verwendung und sollte beim Erstellen einer neuen Veröffentlichung nicht angegeben werden. Wenn *snapshot_agent_name* angegeben wird, müssen *job_login* und *job_password* NULL sein.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Der Sicherheitsmodus, der vom Agent beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_security_mode* ist vom Datentyp **smallint**. der Standardwert ist 1. **0** gibt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung an, und **1** gibt die Windows-Authentifizierung an. Für nicht--Verleger muss ein Wert von **0** angegeben werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`Der Anmelde Name, der beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. *publisher_login* muss angegeben werden, wenn *publisher_security_mode* den Wert **0**hat. Wenn *publisher_login* NULL und *publisher_security_mode* 1 ist, wird das in *job_login* angegebene Konto verwendet, wenn **eine**Verbindung mit dem Verleger hergestellt wird.  
  
`[ @publisher_password = ] 'publisher_password'`Das Kennwort, das beim Herstellen einer Verbindung mit dem Verleger verwendet wird. *publisher_password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Es wird empfohlen, Anmeldenamen und Kennwörter zur Laufzeit bereitzustellen, um die Sicherheit zu verbessern.  
  
`[ @job_login = ] 'job_login'`Der Anmelde Name für das Konto, unter dem der Agent ausgeführt wird. Verwenden Sie auf verwaltete Azure SQL-Datenbank-Instanz ein SQL Server Konto. *job_login* ist vom Datentyp **nvarchar (257)** und hat den Standardwert NULL. Dieses Konto wird immer für Agentverbindungen mit dem Verteiler verwendet. Sie müssen diesen Parameter angeben, wenn Sie einen neuen Auftrag des Momentaufnahme-Agents erstellen.  
  
> [!NOTE]
>  Bei nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verlegern muss es sich hierbei um denselben Anmelde Namen handeln, der in [sp_adddistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)angegeben ist.  
  
`[ @job_password = ] 'job_password'`Das Kennwort für das Windows-Konto, unter dem der Agent ausgeführt wird. *job_password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Sie müssen diesen Parameter angeben, wenn Sie einen neuen Auftrag des Momentaufnahme-Agents erstellen.  
  
> [!IMPORTANT]  
>  Speichern Sie keine Authentifizierungsinformationen in Skriptdateien. Es wird empfohlen, Anmeldenamen und Kennwörter zur Laufzeit bereitzustellen, um die Sicherheit zu verbessern.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn ein Momentaufnahmen-Agent auf einem Verleger erstellt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addpublication_snapshot** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-snapsh_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addpublication_snapshot**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Erstellen und Anwenden der Momentaufnahme](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [sp_addpublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_startpublication_snapshot &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
