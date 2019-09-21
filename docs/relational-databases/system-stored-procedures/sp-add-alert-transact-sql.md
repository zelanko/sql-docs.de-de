---
title: Sp_add_alert (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_alert
- sp_add_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_alert
ms.assetid: d9b41853-e22d-4813-a79f-57efb4511f09
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 848f3cffb3c05f16b339233c89892396b5443e4f
ms.sourcegitcommit: 0ea19d8e3bd9d91a416311e00a5fb0267d41949e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71174257"
---
# <a name="sp_add_alert-transact-sql"></a>sp_add_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt eine Warnung.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_alert [ @name = ] 'name'   
     [ , [ @message_id = ] message_id ]   
     [ , [ @severity = ] severity ]   
     [ , [ @enabled = ] enabled ]  
     [ , [ @delay_between_responses = ] delay_between_responses ]   
     [ , [ @notification_message = ] 'notification_message' ]   
     [ , [ @include_event_description_in = ] include_event_description_in ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @event_description_keyword = ] 'event_description_keyword_pattern' ]   
     [ , { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ]   
     [ , [ @raise_snmp_trap = ] raise_snmp_trap ]   
     [ , [ @performance_condition = ] 'performance_condition' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'`Der Name der Warnung. Der Name wird in der E-Mail- oder Pagernachricht angezeigt, die als Reaktion auf die Warnung gesendet wird. Er muss eindeutig sein und kann das Prozentzeichen ( **%** ) enthalten. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @message_id = ] message_id`Die Nachrichten Fehlernummer, die die Warnung definiert. (Dies entspricht in der Regel einer Fehlernummer in der Tabelle **sysmess** .) *message_id* ist vom Datentyp **int**und hat den Standardwert **0**. Wenn der *Schweregrad* zum Definieren der Warnung verwendet wird, muss *message_id* **0** oder NULL sein.  
  
> [!NOTE]  
>  Nur **sysmess** -Fehler, die in das Microsoft Windows-Anwendungsprotokoll geschrieben werden, können dazu führen, dass eine Warnung gesendet wird.  
  
`[ @severity = ] severity`Der Schweregrad (von **1** bis **25**), der die Warnung definiert. Jede [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der **sysmess** -Tabelle gespeicherte Nachricht, die mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] dem angegeben Schweregrad an das Windows-Anwendungsprotokoll gesendet wird, bewirkt, dass die Warnung gesendet wird. der *Schweregrad* ist vom Datentyp **int**. der Standardwert ist 0. Wenn *message_id* zum Definieren der Warnung verwendet wird, muss der *Schweregrad* **0**sein.  
  
`[ @enabled = ] enabled`Gibt den aktuellen Status der Warnung an. *aktiviert* ist vom Datentyp **tinyint**. der Standardwert ist 1 (aktiviert). Wenn der Wert **0**ist, ist die Warnung nicht aktiviert und wird nicht ausgelöst.  
  
`[ @delay_between_responses = ] delay_between_responses`Die Wartezeit (in Sekunden) zwischen den Antworten auf die Warnung. *delay_between_responses*ist vom Datentyp **int**und hat den Standardwert **0**. Dies bedeutet, dass keine Warteschlange zwischen Antworten vorliegt (jedes Vorkommen der Warnung generiert eine Antwort). Die Reaktion kann in einer oder beiden der folgenden Formen erfolgen:  
  
-   Als eine oder mehrere per E-Mail oder Pager gesendete Benachrichtigungen.  
  
-   Als auszuführender Auftrag.  
  
 Mit dem Festlegen dieses Werts kann beispielsweise verhindert werden, dass unerwünschte E-Mail-Nachrichten gesendet werden, wenn eine Warnung in kurzen Zeitabständen wiederholt auftritt.  
  
`[ @notification_message = ] 'notification_message'`Ist eine optionale zusätzliche Nachricht, die als Teil der e-Mail-, **net send**-oder Pager-Benachrichtigung an den Operator gesendet wird. *notification_message* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL. Das Angeben von *notification_message* ist nützlich zum Hinzufügen von speziellen Notizen, wie z. b  
  
`[ @include_event_description_in = ] include_event_description_in`Gibt an, ob die Beschreibung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des Fehlers als Teil der Benachrichtigungs Meldung eingeschlossen werden soll. *include_event_description_in*ist vom Datentyp **tinyint**. der Standardwert ist **5** (e-Mail und **net send**), und ein oder mehrere dieser Werte können mit einem logischen **or** -Operator kombiniert werden.  
  
> [!IMPORTANT]
>  Die Pager- und **net send** -Optionen werden in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht mehr im [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktionen zurzeit verwenden.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|None|  
|**1**|E-Mail|  
|**2**|Pager|  
|**4**|**net send**|  
  
`[ @database_name = ] 'database'`Die Datenbank, in der der Fehler auftreten muss, damit die Warnung ausgelöst wird. Wenn die *Datenbank*nicht bereitgestellt wird, wird die Warnung unabhängig davon ausgelöst, wo der Fehler aufgetreten ist. *Database* ist vom **Datentyp vom Datentyp sysname**. In eckige Klammern ([ ]) eingeschlossene Namen sind nicht zulässig. Der Standardwert ist NULL.  
  
`[ @event_description_keyword = ] 'event_description_keyword_pattern'`Die Zeichenfolge, die die Beschreibung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlers aufweisen muss. Zulässig sind Zeichen, die dem Muster des LIKE-Ausdrucks von [!INCLUDE[tsql](../../includes/tsql-md.md)] entsprechen. *event_description_keyword_pattern* ist vom Datentyp **nvarchar (100)** und hat den Standardwert NULL. Dieser Parameter ist nützlich zum Filtern von Objektnamen (z. b. **% customer_table%** ).  
  
`[ @job_id = ] job_id`Die ID des Auftrags, der als Reaktion auf diese Warnung ausgeführt werden soll. *job_id* ist vom Datentyp **uniqueidentifier**. der Standardwert ist NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, der als Reaktion auf diese Warnung ausgeführt werden soll. *job_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden, aber beide können nicht angegeben werden.  
  
`[ @raise_snmp_trap = ] raise_snmp_trap`Nicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7,0 implementiert. *raise_snmp_trap* ist vom Datentyp **tinyint**. der Standardwert ist 0.  
  
`[ @performance_condition = ] 'performance_condition'`Ein Wert, der im Format '*itemcomparatorvalue*' ausgedrückt wird. *performance_condition* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL und besteht aus diesen Elementen.  
  
|Format-Element|Beschreibung|  
|--------------------|-----------------|  
|*Element*|Ein Leistungsobjekt, ein Leistungsindikator oder die benannte Instanz des Indikators|  
|*Comparator*|Einer dieser Operatoren: >, < oder =|  
|*Wert*|Numerischer Wert des Indikators|  
  
`[ @category_name = ] 'category'`Der Name der Warnungs Kategorie. *Category* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @wmi_namespace = ] 'wmi_namespace'`Der WMI-Namespace, der nach Ereignissen abgefragt werden soll. *wmi_namespace* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Es werden nur Namespaces auf dem lokalen Server unterstützt.  
  
`[ @wmi_query = ] 'wmi_query'`Die Abfrage, die das WMI-Ereignis für die Warnung angibt. *wmi_query* ist vom Datentyp **nvarchar (512)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_add_alert** muss von der **msdb** -Datenbank aus ausgeführt werden.  
  
 Unter den folgenden Umständen werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anwendungen generierte Fehler bzw. Meldungen an das Windows-Anwendungsprotokoll gesendet und können somit Warnungen auslösen:  
  
-   **Sys. Messages** -Fehler mit Schweregrad 19 oder höher  
  
-   Jede RAISERROR-Anweisung, die mit der WITH LOG-Syntax aufgerufen wurde.  
  
-   Alle **sys. Messages** -Fehler, die mit **sp_altermessage** geändert oder erstellt wurden  
  
-   Alle Ereignisse, die mit **xp_logevent** protokolliert werden  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lässt sich das gesamte Warnungssystem auf einfache Weise mit einer grafischen Oberfläche verwalten. Dies ist die empfohlene Vorgehensweise, um eine Warnungsinfrastruktur zu konfigurieren.  
  
 Überprüfen Sie die folgenden Punkte, wenn eine Warnung nicht ordnungsgemäß funktioniert:  
  
-   Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agentdienst wird ausgeführt.  
  
-   Das Ereignis wird im Windows-Anwendungsprotokoll angezeigt.  
  
-   Die Warnung ist aktiviert.  
  
-   Ereignisse, die mit **xp_logevent** generiert werden, treten in der master-Datenbank auf. Daher wird von **xp_logevent** erst dann eine Warnung ausgelöst, wenn der **\@database_name**-Wert für die Warnung den Wert **'master'** oder NULL aufweist.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** die Prozedur **sp_add_alert**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Warnung (Test Alert) hinzugefügt, die den `Back up the AdventureWorks2012 Database`-Auftrag ausführt, wenn sie ausgegeben wird.  
  
> [!NOTE]  
>  Bei diesem Beispiel wird vorausgesetzt, dass die Meldung 55001 und der `Back up the AdventureWorks2012 Database`-Auftrag vorhanden sind. Dieses Beispiel dient lediglich zu Illustrationszwecken.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_alert  
    @name = N'Test Alert',  
    @message_id = 55001,   
   @severity = 0,   
   @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
   @job_name = N'Back up the AdventureWorks2012 Database' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_delete_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
