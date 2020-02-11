---
title: sp_changesubstatus (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubstatus
- sp_changesubstatus_TSQL
helpviewer_keywords:
- sp_changesubstatus
ms.assetid: 9370e47a-d128-4f15-9224-1c3642770c39
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c10e05098a611e51583b2b1132f811d36b0f20a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771329"
---
# <a name="sp_changesubstatus-transact-sql"></a>sp_changesubstatus (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Ändert den Status eines vorhandenen Abonnenten. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changesubstatus [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
        , [ @status = ] 'status'  
    [ , [ @previous_status = ] 'previous_status' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
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
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @distribution_jobid = ] distribution_jobid ]  
    [ , [ @from_auto_sync = ] from_auto_sync ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @offloadagent= ] remote_agent_activation ]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] dts_package_location ]  
    [ , [ @skipobjectactivation = ] skipobjectactivation  
  [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist. Wenn *Publication* nicht angegeben wird, sind alle Veröffentlichungen betroffen.  
  
`[ @article = ] 'article'`Der Name des Artikels. Er muss für die Veröffentlichung eindeutig sein. der *Artikel* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert. Wenn der *Artikel* nicht angegeben wird, sind alle Artikel betroffen.  
  
`[ @subscriber = ] 'subscriber'`Der Name des Abonnenten, dessen Status geändert werden soll. *Subscriber* ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist. Wenn der *Abonnent* nicht angegeben wird, wird der Status für alle Abonnenten in den angegebenen Artikel geändert.  
  
`[ @status = ] 'status'`Der Abonnement Status in der **sysabonnements** -Tabelle. der *Status* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**enden**|Der Abonnent ist synchronisiert und empfängt Daten.|  
|**VSTE**|Es ist ein Eintrag für einen Abonnenten ohne Abonnement vorhanden.|  
|**zehnmal**|Der Abonnent fordert Daten an, ist aber noch nicht synchronisiert.|  
  
`[ @previous_status = ] 'previous_status'`Der vorherige Status des Abonnements. *previous_status* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Mithilfe dieses Parameters können Sie alle Abonnements ändern, die den Status aktuell aufweisen, sodass Sie Gruppenfunktionen für einen bestimmten Satz von Abonnements zulassen (z. b. das Zurücksetzen aller aktiven Abonnements auf **abonniert**).  
  
`[ @destination_db = ] 'destination_db'`Der Name der Zieldatenbank. *destination_db* ist vom **%** **Datentyp vom Datentyp sysname**und hat den Standardwert.  
  
`[ @frequency_type = ] frequency_type`Die Häufigkeit, mit der der Verteilungs Task geplant werden soll. *frequency_type* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_interval = ] frequency_interval`Der Wert, der auf die von *frequency_type*festgelegte Häufigkeit angewendet werden soll. *frequency_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`Das Datum des Verteilungs Tasks. Dieser Parameter wird verwendet, wenn *frequency_type* auf 32 (monatlich, relativ) festgelegt ist. *frequency_relative_interval* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|First (Erster)|  
|**2**|Sekunde|  
|**4**|Dritter|  
|**88**|Vierter|  
|**Uhr**|Last (Letzter)|  
|NULL (Standard)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`Der von *frequency_type*verwendete Wiederholungs Faktor. *frequency_recurrence_factor* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @frequency_subday = ] frequency_subday`Gibt an, wie oft (in Minuten) während des definierten Zeitraums neu geplant werden soll. *frequency_subday* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**1**|Einmalig|  
|**2**|Sekunde|  
|**4**|Minute|  
|**88**|Hour|  
|NULL (Standard)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`Das Intervall für die *frequency_subday*. *frequency_subday_interval* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`Die Tageszeit, zu der der Verteilungs Task zum ersten Mal geplant ist. dabei wird das Format HHMMSS verwendet. *active_start_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`Die Tageszeit, zu der der Verteilungs Task nicht mehr geplant ist. dabei wird das Format HHMMSS verwendet. *active_end_time_of_day* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_start_date = ] active_start_date`Das Datum, an dem der Verteilungs Task zum ersten Mal geplant ist. dabei wird das Format YYYYMMDD verwendet. *active_start_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @active_end_date = ] active_end_date`Das Datum, an dem der Verteilungs Task nicht mehr geplant ist. dabei wird das Format YYYYMMDD verwendet. *active_end_date* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @optional_command_line = ] 'optional_command_line'`Ist eine optionale Eingabeaufforderung. *optional_command_line* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL.  
  
`[ @distribution_jobid = ] distribution_jobid`Die Auftrags-ID der Verteilungs-Agent auf dem Verteiler für das Abonnement, wenn der Abonnement Status von "inaktiv" in "aktiv" geändert wird. In anderen Fällen wird sie nicht definiert. Wenn an einem einzelnen Aufruf dieser gespeicherten Prozedur mehrere Verteilungs-Agents beteiligt sind, ist Ergebnis nicht definiert. *distribution_jobid* ist **Binary (16)** und hat den Standardwert NULL.  
  
`[ @from_auto_sync = ] from_auto_sync` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] remote_agent_activation`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn *remote_agent_activation* auf einen anderen Wert als **0** festgelegt wird, wird ein Fehler generiert.  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  Die Aktivierung des Remote-Agents wurde als veraltet markiert und wird nicht mehr unterstützt. Dieser Parameter wird nur zur Aufrechterhaltung der Abwärtskompatibilität von Skripts unterstützt. Wenn Sie *remote_agent_server_name* auf einen nicht-NULL-Wert festlegen, wird ein Fehler generiert.  
  
`[ @dts_package_name = ] 'dts_package_name'`Gibt den Namen des DTS-Pakets (Data Transformation Services) an. *dts_package_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Für ein Paket mit dem Namen **DTSPub_Package** Sie z. b `@dts_package_name = N'DTSPub_Package'`. angeben.  
  
`[ @dts_package_password = ] 'dts_package_password'`Gibt das Kennwort für das Paket an. *dts_package_password* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL, der angibt, dass die Kenn Wort Eigenschaft unverändert bleiben soll.  
  
> [!NOTE]  
>  Ein DTS-Paket muss über ein Kennwort verfügen.  
  
`[ @dts_package_location = ] dts_package_location`Gibt den Speicherort des Pakets an. *dts_package_location* ist vom Datentyp **int**und hat den Standardwert **0**. Bei **0**befindet sich der Speicherort des Pakets auf dem Verteiler. Bei **1**befindet sich der Speicherort des Pakets auf dem Abonnenten. Der Speicherort des Pakets kann **Distributor** oder **Subscriber**sein.  
  
`[ @skipobjectactivation = ] skipobjectactivation` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @distribution_job_name = ] 'distribution_job_name'`Der Name des Verteilungs Auftrags. *distribution_job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn Artikeleigenschaften auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einem Verleger geändert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_changesubstatus** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 **sp_changesubstatus** ändert den Status des Abonnenten in der **sysabonnements** -Tabelle mit dem geänderten Status. Bei Bedarf wird der Artikel Status in der **sysarticles** -Tabelle aktualisiert, um den Status "aktiv" oder "inaktiv" anzugeben. Bei Bedarf wird das Replikationsflag in der **sysobjects** -Tabelle für die replizierte Tabelle auf on oder OFF festgelegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** oder der Ersteller des Abonnements können **sp_changesubstatus**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
