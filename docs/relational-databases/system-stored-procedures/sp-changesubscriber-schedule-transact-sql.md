---
title: Sp_changesubscriber_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber_schedule
- sp_changesubscriber_schedule_TSQL
helpviewer_keywords:
- sp_changesubscriber_schedule
ms.assetid: ff84e8e2-d496-482c-b23e-38a6626596e6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54098c536fa368c4a2b58d387911e646db15a4d4
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526802"
---
# <a name="spchangesubscriberschedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert den Zeitplan des Verteilungs- und Merge-Agents für einen Abonnenten. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changesubscriber_schedule [ @subscriber = ] 'subscriber', [ @agent_type = ] type  
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
  
`[ @agent_type = ] type` Ist der Typ des Agents. *Typ* ist **Smallint**, hat den Standardwert **0**. **0** zeigt einen Verteilungs-Agent. **1** zeigt einen Merge-Agent.  
  
`[ @frequency_type = ] frequency_type` Kann die Häufigkeit, mit denen des Verteilungstasks. *Frequency_type* ist **Int**, hat den Standardwert **64**. Es gibt 10 Zeitplanspalten.  
  
`[ @frequency_interval = ] frequency_interval` Ist der Wert der Häufigkeit festgelegt angewendet *Frequency_type*. *Frequency_interval* ist **Int**, hat den Standardwert **1**.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Ist das Datum des Verteilungstasks. *Frequency_relative_interval* ist **Int**, hat den Standardwert **1**.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Wird von verwendete Wiederholungsfaktor *Frequency_type*. *Frequency_recurrence_factor* ist **Int**, hat den Standardwert **0**.  
  
`[ @frequency_subday = ] frequency_subday` Wie oft ist, in Minuten, für die erneute geplante Ausführung während des definierten Zeitraums. *Frequency_subday* ist **Int**, hat den Standardwert **4**.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Das Intervall für *Frequency_subday*. *Frequency_subday_interval* ist **Int**, hat den Standardwert **5**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Ist die Zeit des Tages, bei der Verteilungstask zum ersten Mal geplant ist. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` Ist die Tageszeit, ab der Verteilungstask nicht mehr geplant. *das Format HHMMSS verwendet* ist **Int**, hat den Standardwert **235959**, womit 23:59:59 Uhr im 24-Stunden-Format).  
  
`[ @active_start_date = ] active_start_date` Das Datum, an der Verteilungstask erste ist geplant Format: YYYYMMDD. *Active_start_date* ist **Int**, hat den Standardwert **0**.  
  
`[ @active_end_date = ] active_end_date` Ist das Datum, ab der Verteilungstask nicht mehr, geplant ist JJJJMMTT. *Active_end_date* ist **Int**, hat den Standardwert **99991231**, womit der 31. Dezember 9999.  
  
`[ @publisher = ] 'publisher'` Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]  
>  *Publisher* sollte nicht verwendet werden, beim Ändern von Artikeleigenschaften auf einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changesubscriber_schedule** wird in allen Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_changesubscriber_schedule**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addsubscriber_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
