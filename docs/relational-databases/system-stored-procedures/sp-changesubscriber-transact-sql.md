---
title: sp_changesubscriber (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 42b56712e8b441184d55bf12ce16dbcb55930374
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68762783"
---
# <a name="sp_changesubscriber-transact-sql"></a>sp_changesubscriber (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert die Optionen für einen Abonnenten. Alle Verteilungstasks für die Abonnenten des Verlegers werden aktualisiert. Diese gespeicherte Prozedur schreibt in die **MSsubscriber_info** Tabelle in der Verteilungs Datenbank. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten, auf dem die Optionen geändert werden sollen. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @type = ] type`Der Typ des Abonnenten. *Type ist vom Datentyp* **tinyint**. der Standardwert ist NULL. **0** gibt einen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten an. **1** gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder einen anderen ODBC-Datenquellen Server-Abonnenten an.  
  
`[ @login = ] 'login'`Die Anmelde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -ID für die Authentifizierung. *Login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @password = ] 'password'`Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierungs Kennwort. *Password* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert. **%** Gibt an, dass die Kenn Wort Eigenschaft nicht geändert wird.  
  
`[ @commit_batch_size = ] commit_batch_size`Wird nur aus Gründen der Abwärtskompatibilität unterstützt.  
  
`[ @status_batch_size = ] status_batch_size`Wird nur aus Gründen der Abwärtskompatibilität unterstützt.  
  
`[ @flush_frequency = ] flush_frequency`Wird nur aus Gründen der Abwärtskompatibilität unterstützt.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der der Verteilungs Task geplant werden soll. *frequency_type* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|On-Demand-Streaming|  
|**4**|Täglich|  
|**88**|Wöchentlich|  
|**Uhr**|Monatlich|  
|**32**|Monatlich, relativ|  
|**64**|Autostart|  
|**128**|Serie|  
  
`[ @frequency_interval = ] frequency_interval`Das Intervall für die *frequency_type*. *frequency_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum des Verteilungs Tasks. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|First (Erster)|  
|**2**|Sekunde|  
|**4**|Dritter|  
|**88**|Vierter|  
|**Uhr**|Last (Letzter)|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Gibt an, wie oft der Verteilungs Task während der definierten *frequency_type*wiederholt werden soll. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft innerhalb des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|Sekunde|  
|**4**|Minute|  
|**88**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für die *frequence_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der der Verteilungs Task zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der der Verteilungs Task nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem der Verteilungs Task zum ersten Mal geplant ist. dabei wird das Format YYYYMMDD verwendet. *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Verteilungs Task nicht mehr geplant ist. dabei wird das Format YYYYMMDD verwendet. *active_end_date*ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @description = ] 'description'`Ist eine optionale Textbeschreibung. die *Beschreibung* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @security_mode = ] security_mode`Der implementierte Sicherheitsmodus. *security_mode* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung|  
|**1**|Windows-Authentifizierung|  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn Artikeleigenschaften auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem Verleger geändert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changesubscriber** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_changesubscriber**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addsubscriber &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
