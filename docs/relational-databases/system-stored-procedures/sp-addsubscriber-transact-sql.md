---
title: sp_addsubscriber (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscriber
- sp_addsubscriber_TSQL
helpviewer_keywords:
- sp_addsubscriber
ms.assetid: b8a584ea-2a26-4936-965b-b84f026e39c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa4ea771197f08fc16989176f486d6a29c8c9940
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769041"
---
# <a name="spaddsubscriber-transact-sql"></a>sp_addsubscriber (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Fügt einen neuen Abonnenten zu einem Verleger hinzu, wobei dieser für den Empfang von Veröffentlichungen aktiviert wird. Diese gespeicherte Prozedur wird für Momentaufnahme- und Transaktionsveröffentlichungen auf dem Verleger in der Veröffentlichungsdatenbank ausgeführt. Für Mergeveröffentlichungen, die einen Remoteverteiler verwenden, wird diese gespeicherte Prozedur auf dem Verteiler ausgeführt.  
  
> [!IMPORTANT]  
>  Diese gespeicherte Prozedur wurde als veraltet markiert. Es ist nicht mehr erforderlich, einen Abonnenten ausdrücklich auf dem Verleger zu registrieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addsubscriber [ @subscriber = ] 'subscriber'  
    [ , [ @type = ] type ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @commit_batch_size = ] commit_batch_size ]  
    [ , [ @status_batch_size = ] status_batch_size ]  
    [ , [ @flush_frequency = ] flush_frequency ]  
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
    [ , [ @description = ] 'description' ]  
    [ , [ @security_mode = ] security_mode ]  
    [ , [ @encrypted_password = ] encrypted_password ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subscriber = ] 'subscriber'`Der Name des Servers, der den Veröffentlichungen auf diesem Server als gültiger Abonnent hinzugefügt werden soll. *Subscriber* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @type = ] type`Der Typ des Abonnenten. *Type ist vom Datentyp* **tinyint**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**0** (Standardwert)|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnent|  
|**1**|ODBC-Datenquellenserver|  
|**2**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet-Datenbank|  
|**3**|OLE DB-Anbieter|  
  
`[ @login = ] 'login'`Die Anmelde-ID für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Authentifizierung. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @password = ] 'password'`Das Kennwort für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Authentifizierung. *Password* ist vom Datentyp **nvarchar (524)** und hat den Standardwert NULL.  
  
> [!IMPORTANT]  
>  Verwenden Sie kein leeres Kennwort. Verwenden Sie ein sicheres Kennwort.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @commit_batch_size = ] commit_batch_size`Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
> [!NOTE]  
>  Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @status_batch_size = ] status_batch_size`Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
> [!NOTE]  
>  Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @flush_frequency = ] flush_frequency`Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten.  
  
> [!NOTE]  
>  Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der der Replikations-Agent geplant werden soll. *frequency_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
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
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
 **[@frequency_interval=** ] *frequency_interval*  
 Der Wert, der auf die von *frequency_type*festgelegte Häufigkeit angewendet wird. *frequency_interval* ist vom Datentyp **int**und hat den Standardwert 1.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum des Replikations-Agents. Dieser Parameter wird verwendet, wenn *frequency_type* auf **32** (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**1** (Standard)|Erster|  
|**2**|Zweimal|  
|**4**|Dritter|  
|**8**|Vierter|  
|**16**|Letzter|  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft innerhalb des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1**|Einmal|  
|**2**|Zweimal|  
|**4** (Standard)|Minute|  
|**8**|Hour|  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert **5**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der der Replikations-Agent zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der der Replikations-Agent nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day*ist vom Datentyp **int**. der Standardwert ist 235959. der Wert ist 11:59:59 Uhr. gemessen auf einem 24-Stunden-Format.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem der Replikations-Agent zum ersten Mal geplant ist, formatiert als YYYYMMDD. *active_start_date* ist vom Datentyp **int**und hat den Standardwert 0.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Replikations-Agent nicht mehr geplant ist, formatiert als YYYYMMDD. *active_end_date* ist vom Datentyp **int**. der Standardwert ist 99991231, d. h. der 31. Dezember 9999.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @description = ] 'description'`Eine Textbeschreibung des Abonnenten. die *Beschreibung* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @security_mode = ] security_mode`Der implementierte Sicherheitsmodus. *security_mode* ist vom Datentyp **int**und hat den Standardwert 1. **0** gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-Authentifizierung an. **1** gibt die Windows-Authentifizierung an.  
  
> [!NOTE]  
>  Dieser Parameter wurde als veraltet markiert und wird aus Gründen der Abwärtskompatibilität von Skripts beibehalten. Die-Eigenschaft wird jetzt auf Abonnement Basis beim Ausführen von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)angegeben. Wenn ein Wert angegeben wird, wird er beim Erstellen von Abonnements auf diesem Abonnenten als Standard verwendet, und eine Warnmeldung wird zurückgegeben.  
  
`[ @encrypted_password = ] encrypted_password`Dieser Parameter wurde als veraltet markiert und wird nur aus Gründen der Abwärtskompatibilität bereitgestellt, wobei *encrypted_password* auf einen beliebigen Wert festgelegt wird. **0** führt jedoch zu einem Fehler.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte beim Veröffentlichen von einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger nicht verwendet werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_addsubscriber** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
 **sp_addsubscriber** ist nicht erforderlich, wenn der Abonnent nur anonyme Abonnements für Mergeveröffentlichungen hat.  
  
 **sp_addsubscriber** schreibt in die [MSsubscriber_info](../../relational-databases/system-tables/mssubscriber-info-transact-sql.md) -Tabelle in der **Verteilungs** Datenbank.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_addsubscriber**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Erstellen eines Pullabonnements](../../relational-databases/replication/create-a-pull-subscription.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)  
  
  
