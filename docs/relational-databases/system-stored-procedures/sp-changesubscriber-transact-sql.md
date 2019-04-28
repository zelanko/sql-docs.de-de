---
title: Sp_changesubscriber (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber
- sp_changesubscriber_TSQL
helpviewer_keywords:
- sp_changesubscriber
ms.assetid: d453c451-e957-490f-b968-5e03aeddaf10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f31a00e0c42bc56dffac191ff9a934bb77b95df
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997805"
---
# <a name="spchangesubscriber-transact-sql"></a>sp_changesubscriber (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Optionen für einen Abonnenten. Alle Verteilungstasks für die Abonnenten des Verlegers werden aktualisiert. Diese gespeicherte Prozedur schreibt in die **MSsubscriber_info** Tabelle in der Verteilungsdatenbank. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changesubscriber [ @subscriber= ] 'subscriber'  
    [ , [ @type= ] type ]  
    [ , [ @login= ] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @commit_batch_size= ] commit_batch_size ]  
    [ , [ @status_batch_size= ] status_batch_size ]  
    [ , [ @flush_frequency= ] flush_frequency ]  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @security_mode= ] security_mode ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten, auf dem die Optionen ändern. *Abonnenten* ist **Sysname**, hat keinen Standardwert.  
  
`[ @type = ] type` Ist der Typ des Abonnenten. *Typ* ist **Tinyint**, hat den Standardwert NULL. **0** gibt eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten. **1** gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder andere ODBC-Datenquellenserver Abonnenten.  
  
`[ @login = ] 'login'` Ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung-Anmelde-ID. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
`[ @password = ] 'password'` Ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierungskennwort. *Kennwort* ist **Sysname**, hat den Standardwert **%**. **%** Gibt an, dass keine Änderung an der Password-Eigenschaft vorhanden ist.  
  
`[ @commit_batch_size = ] commit_batch_size` Nur für Abwärtskompatibilität unterstützt.  
  
`[ @status_batch_size = ] status_batch_size` Nur für Abwärtskompatibilität unterstützt.  
  
`[ @flush_frequency = ] flush_frequency` Nur für Abwärtskompatibilität unterstützt.  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit, mit denen des Verteilungstasks. *Frequency_type* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Bedarfsgesteuert|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ|  
|**64**|Autostart|  
|**128**|Wiederholt|  
  
`[ @frequency_interval = ] frequency_interval` Das Intervall für *Frequency_type*. *Frequency_interval* ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Verteilungstasks. Dieser Parameter wird verwendet, wenn *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall). *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Ist, wie oft der Verteilungstask während des definierten wiederholt werden soll *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday` Ist die Häufigkeit für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit, die bei der der Verteilungstask erste ist wird geplant HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Verteilungstask nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet*ist **Int**, hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an der Verteilungstask erste ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Verteilungstask nicht mehr, geplant ist JJJJMMTT. *Active_end_date*ist **Int**, hat den Standardwert NULL.  
  
`[ @description = ] 'description'` Ist eine optionale textbeschreibung. *Beschreibung* ist **nvarchar(255)**, hat den Standardwert NULL.  
  
`[ @security_mode = ] security_mode` Ist der implementierte Sicherheitsmodus. *Security_mode* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung|  
|**1**|Windows-Authentifizierung|  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, beim Ändern von Artikeleigenschaften auf einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changesubscriber** wird in allen Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_changesubscriber**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
