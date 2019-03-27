---
title: Sp_addsubscriber_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscriber_schedule_TSQL
- sp_addsubscriber_schedule
helpviewer_keywords:
- sp_addsubscriber_schedule
ms.assetid: a6225033-5c3b-452f-ae52-79890a3590ed
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d9c899f5ae956f9e434bb7374d95aaa186a2923
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493791"
---
# <a name="spaddsubscriberschedule-transact-sql"></a>sp_addsubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt dem Verteilungs- und Merge-Agent einen Zeitplan hinzu. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addsubscriber_schedule [ @subscriber = ] 'subscriber'  
    [ , [ @agent_type = ] agent_type ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subscriber = ] 'subscriber'` Ist der Name des Abonnenten. *Abonnenten* ist **Sysname**. Der Name des Abonnenten muss innerhalb der Datenbank eindeutig sein und darf nicht bereits vorhanden sein. Außerdem darf er nicht gleich NULL sein.  
  
`[ @agent_type = ] agent_type` Ist der Typ des Agents. *Agent_type* ist **Smallint**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0** (Standardwert)|Verteilungs-Agent|  
|**1**|Merge-Agent|  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit, mit denen der Verteilungs-Agent zu planen. *Frequency_type* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Bedarfsgesteuert|  
|**4**|Täglich|  
|**8**|Wöchentlicher Zeitplan|  
|**16**|Monatlicher Zeitplan|  
|**32**|Monatlich, relativ|  
|**64** (Standard)|Autostart|  
|**128**|Wiederholt|  
  
`[ @frequency_interval = ] frequency_interval` Ist der Wert der Häufigkeit festgelegt, die durch Anwenden *Frequency_type*. *Frequency_interval* ist **Int**, hat den Standardwert **1**.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Verteilungs-Agents. Dieser Parameter wird verwendet, wenn *Frequency_type* nastaven NA hodnotu **32** (mit relativem Monatsintervall). *Frequency_relative_interval* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1** (Standard)|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert **0**.  
  
`[ @frequency_subday = ] frequency_subday` Ist die Häufigkeit für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4** (Standard)|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert **5**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Die Tageszeit aus, wenn der erste der Verteilungs-Agent ist, erfolgt Format: HHMMSS. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Die Tageszeit, ab der Verteilungs-Agent nicht mehr, wird geplant ist HHMMSS verwendet. *das Format HHMMSS verwendet*ist **Int**, hat den Standardwert 235959, womit 23:59:59 Uhr auf dem 24-Stunden-Format an.  
  
`[ @active_start_date = ] active_start_date` Das Datum, an den Verteilungs-Agent zuerst ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert **0**.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Verteilungs-Agent nicht mehr, geplant JJJJMMTT. *Active_end_date* ist **Int**, hat den Standardwert 99991231, womit der 31. Dezember 9999.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht angegeben werden, für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addsubscriber_schedule** wird in Momentaufnahme-, Transaktions- und Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_addsubscriber_schedule**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_changesubscriber_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-schedule-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
