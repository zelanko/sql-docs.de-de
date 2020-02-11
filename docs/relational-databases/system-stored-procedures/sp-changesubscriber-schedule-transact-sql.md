---
title: sp_changesubscriber_schedule (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 22ecb1601108562607d1fdc550daaa945fe72910
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770732"
---
# <a name="sp_changesubscriber_schedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert den Zeitplan des Verteilungs- und Merge-Agents für einen Abonnenten. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten. *Abonnent* ist vom **Datentyp vom Datentyp sysname**. Der Name des Abonnenten muss innerhalb der Datenbank eindeutig sein und darf nicht bereits vorhanden sein. Außerdem darf er nicht gleich NULL sein.  
  
`[ @agent_type = ] type`Der Typ des Agents. *Type ist vom Datentyp* **smallint**. der Standardwert ist **0**. **0** gibt eine Verteilungs-Agent an. **1** gibt eine Merge-Agent an.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der der Verteilungs Task geplant werden soll. *frequency_type* ist vom Datentyp **int**und hat den Standardwert **64**. Es gibt 10 Zeitplanspalten.  
  
`[ @frequency_interval = ] frequency_interval`Der Wert, der auf die von *frequency_type*festgelegte Häufigkeit angewendet wird. *frequency_interval* ist vom Datentyp **int**und hat den Standardwert **1**.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum des Verteilungs Tasks. *frequency_relative_interval* ist vom Datentyp **int**und hat den Standardwert **1**.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft (in Minuten) während des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**. der Standardwert ist **4**.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für die *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert **5**.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der der Verteilungs Task zum ersten Mal geplant ist. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der der Verteilungs Task nicht mehr geplant ist. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert **235959**, was bedeutet 11:59:59 Uhr. im 24-Stunden-Format).  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem der Verteilungs Task zum ersten Mal geplant ist. dabei wird das Format YYYYMMDD verwendet. *active_start_date* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Verteilungs Task nicht mehr geplant ist. dabei wird das Format YYYYMMDD verwendet. *active_end_date* ist vom Datentyp **int**und hat den Standardwert **99991231**, was bedeutet, dass der 31. Dezember 9999.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn Artikeleigenschaften auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem Verleger geändert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changesubscriber_schedule** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_changesubscriber_schedule**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addsubscriber_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
