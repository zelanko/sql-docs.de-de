---
title: sp_helpsubscriberinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpsubscriberinfo
- sp_helpsubscriberinfo_TSQL
helpviewer_keywords:
- sp_helpsubscriberinfo
ms.assetid: fbabe1ec-57cf-425c-bae7-af7f5d3198fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38b653dcb51f428692401fb87609187a82449393
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68771487"
---
# <a name="sp_helpsubscriberinfo-transact-sql"></a>sp_helpsubscriberinfo (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Zeigt Informationen zu einem Abonnenten an. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpsubscriberinfo [ [ @subscriber =] 'subscriber']  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist, wodurch alle Informationen zurückgegeben werden.  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom Datentyp **vom Datentyp sysname**. der Standardwert ist der Name des aktuellen Servers.  
  
> [!NOTE]  
>  der *Verleger* darf nicht angegeben werden, es sei denn, es handelt sich um einen Oracle-Verleger.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Gebers**|**sysname**|Name des Verlegers.|  
|**Abonnenten**|**sysname**|Der Name des Abonnenten.|  
|**type**|**tinyint**|Typ des Abonnenten:<br /><br /> **0** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)] Datenbank 1 = ODBC-Datenquelle **1** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**Anmel**|**sysname**|Anmelde-ID für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung.|  
|**password**|**sysname**|Kennwort für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung.|  
|**commit_batch_size**|**int**|Nicht unterstützt.|  
|**status_batch_size**|**int**|Nicht unterstützt.|  
|**flush_frequency**|**int**|Nicht unterstützt.|  
|**frequency_type**|**int**|Häufigkeit, mit der der Verteilungs-Agent ausgeführt wird:<br /><br /> **1** = einmal<br /><br /> **2** = Bedarfs gesteuert<br /><br /> **4** = täglich<br /><br /> **8** = wöchentlich<br /><br /> **16** = monatlich<br /><br /> **32** = monatlich, relativ<br /><br /> **64** = Autostart<br /><br /> **128** = wiederholt|  
|**frequency_interval**|**int**|Der Wert, der auf die durch *frequency_type*festgelegte Häufigkeit angewendet wird.|  
|**frequency_relative_interval**|**int**|Datum der Verteilungs-Agent, die verwendet wird, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist:<br /><br /> **1** = zuerst<br /><br /> **2** = Sekunde<br /><br /> **4** = dritte<br /><br /> **8** = Fourth<br /><br /> **16** = zuletzt|  
|**frequency_recurrence_factor**|**int**|Der von *frequency_type*verwendete Wiederholungs Faktor.|  
|**frequency_subday**|**int**|Häufigkeit der erneuten Planung während des definierten Zeitraumes:<br /><br /> **1** = einmal<br /><br /> **2** = Sekunde<br /><br /> **4** = Minute<br /><br /> **8** = Stunde|  
|**frequency_subday_interval**|**int**|Intervall für *frequency_subday*.|  
|**active_start_time_of_day**|**int**|Zeitpunkt, zu dem der Einsatz des Verteilungs-Agents zum ersten Mal geplant wird (Format: HHMMSS).|  
|**active_end_time_of_day**|**int**|Zeitpunkt, zu dem die Planung des Einsatzes des Verteilungs-Agents beendet wird (Format: HHMMSS).|  
|**active_start_date**|**int**|Datum, an dem der Einsatz des Verteilungs-Agents zum ersten Mal geplant wird (Format: YYYYMMDD).|  
|**active_end_date**|**int**|Datum, an dem die Planung des Einsatzes des Verteilungs-Agents beendet wird (Format: YYYYMMDD).|  
|**retryattempt**|**int**|Nicht unterstützt.|  
|**retrydelay**|**int**|Nicht unterstützt.|  
|**Beschreibung**|**nvarchar(255)**|Beschreibungstext des Abonnenten.|  
|**security_mode**|**int**|Implementierter Sicherheitsmodus:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung<br /><br /> **1** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung|  
|**frequency_type2**|**int**|Häufigkeit, mit der der Merge-Agent ausgeführt wird:<br /><br /> **1** = einmal<br /><br /> **2** = Bedarfs gesteuert<br /><br /> **4** = täglich<br /><br /> **8** = wöchentlich<br /><br /> **16** = monatlich<br /><br /> **32** = monatlich, relativ<br /><br /> **64** = Autostart<br /><br /> **128** = wiederholt|  
|**frequency_interval2**|**int**|Der Wert, der auf die durch *frequency_type*festgelegte Häufigkeit angewendet wird.|  
|**frequency_relative_interval2**|**int**|Datum der Merge-Agent, die verwendet wird, wenn *frequency_type* auf 32 (monatlich, relativ) festgelegt ist:<br /><br /> **1** = zuerst<br /><br /> **2** = Sekunde<br /><br /> **4** = dritte<br /><br /> **8** = Fourth<br /><br /> **16** = zuletzt|  
|**frequency_recurrence_factor2**|**int**|Der von *frequency_type * ** verwendete Wiederholungs Faktor.|  
|**frequency_subday2**|**int**|Häufigkeit der erneuten Planung während des definierten Zeitraumes:<br /><br /> **1** = einmal<br /><br /> **2** = Sekunde<br /><br /> **4** = Minute<br /><br /> **8** = Stunde|  
|**frequency_subday_interval2**|**int**|Intervall für *frequency_subday*.|  
|**active_start_time_of_day2**|**int**|Zeitpunkt, zu dem der Einsatz des Merge-Agents zum ersten Mal geplant wird (Format: HHMMSS).|  
|**active_end_time_of_day2**|**int**|Zeitpunkt, zu dem die Planung des Einsatzes des Merge-Agents beendet wird (Format: HHMMSS).|  
|**active_start_date2**|**int**|Datum, an dem der Einsatz des Merge-Agents zum ersten Mal geplant wird (Format: YYYYMMDD).|  
|**active_end_date2**|**int**|Datum, an dem die Planung des Einsatzes des Merge-Agents beendet wird (Format: YYYYMMDD).|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpsubscriberinfo** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** oder der Veröffentlichungs Zugriffsliste für die Veröffentlichung können **sp_helpsubscriberinfo**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_adddistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addpullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_changesubscriber &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
