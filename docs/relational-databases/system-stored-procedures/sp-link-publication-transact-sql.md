---
title: Sp_link_publication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_link_publication_TSQL
- sp_link_publication
helpviewer_keywords:
- sp_link_publication
ms.assetid: 1945ed24-f9f1-4af6-94ca-16d8e864706e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94d074985848bb510c15907f6b17dc492904f5c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62960170"
---
# <a name="splinkpublication-transact-sql"></a>sp_link_publication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt die Konfigurations- und Sicherheitsinformationen fest, die von den Synchronisierungstriggern der Abonnements mit sofortigem Update bei der Herstellung einer Verbindung mit dem Verleger verwendet werden. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
> [!IMPORTANT]
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
> 
> [!IMPORTANT]
>  Diese gespeicherte Prozedur kann unter bestimmten Umständen fehlschlagen, wenn es sich bei dem Abonnenten ausgeführt wird, ist [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Servicepack 1 oder höher, und dem Verleger eine frühere Version ausgeführt wird. Falls in diesem Szenario ein Fehler bei der gespeicherten Prozdur auftritt, sollten Sie den Verleger auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 oder höher aktualisieren.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_link_publication [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'   
        , [ @publication = ] 'publication'   
        , [ @security_mode = ] security_mode  
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ]'password' ]  
    [ , [ @distributor = ] 'distributor' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers, zu verknüpfen. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Verlegerdatenbank zu verknüpfen. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung, zu verknüpfen. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @security_mode = ] security_mode` Der Sicherheitsmodus wird des Abonnenten für sofortige Updates eine Verbindung mit einem Remoteverleger verwendet werden. *Security_mode* ist **Int**, und kann einen der folgenden Werte sein. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung mit der Anmeldung, die in dieser gespeicherten Prozedur als angegebenen *Anmeldung* und *Kennwort*.<br /><br /> Hinweis: In früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese Option wurde verwendet, um ein dynamischer Remoteprozeduraufruf (RPC) angeben.|  
|**1**|Verwendet den Sicherheitskontext ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung oder Windows-Authentifizierung) des Benutzers, der die Änderung auf dem Abonnenten ausführt.<br /><br /> Hinweis: Dieses Konto muss auch auf dem Verleger mit ausreichenden Berechtigungen vorhanden sein. Bei Verwendung der Windows-Authentifizierung muss die Delegierung von Sicherheitskonten unterstützt werden.|  
|**2**|Verwendet eine vorhandene, benutzerdefinierte verbindungsserveranmeldung mit erstellt **Sp_link_publication**.|  
  
`[ @login = ] 'login'` Ist die Anmeldung. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. Dieser Parameter muss angegeben, wenn *Security_mode* ist **0**.  
  
`[ @password = ] 'password'` Ist das Kennwort. *Kennwort* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter muss angegeben, wenn *Security_mode* ist **0**.  
  
`[ @distributor = ] 'distributor'` Ist der Name des Verteilers. *Verteiler* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_link_publication** wird von Abonnements mit sofortigem Update bei der Transaktionsreplikation verwendet.  
  
 **Sp_link_publication** für sowohl Push-und Pullabonnements verwendet werden kann. Der Aufruf ist vor oder nach dem Erstellen des Abonnements möglich. Ein Eintrag eingefügt oder aktualisiert die [MSsubscription_properties &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) -Systemtabelle.  
  
 Bei Pushabonnements wird der Eintrag gelöscht werden durch [Sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). Bei Pullabonnements müssen Sie der Eintrag gelöscht werden durch [Sp_droppullsubscription &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md) oder [Sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md). Sie können auch aufrufen **Sp_link_publication** mit einem NULL-Kennwort löschen Sie den Eintrag in der [MSsubscription_properties &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) Systemtabelle änderungskonfigurationen auf Sicherheitsrisiken.  
  
 Der Standardmodus, der von einem Abonnenten mit sofortigem Update verwendet wird, wenn eine Verbindung zum Verleger hergestellt wird, ermöglicht nicht die Verwendung einer Verbindung mit der Windows-Authentifizierung. Wenn Sie eine Verbindung mit der Windows-Authentifizierung herstellen möchten, muss ein Verbindungsserver für den Verleger eingerichtet werden. Der Abonnent mit sofortigem Update sollte diese Verbindung dann für das Update des Abonnenten verwenden. Dies erfordert die **Sp_link_publication** für die Ausführung mit *Security_mode* = **2**. Bei Verwendung der Windows-Authentifizierung muss die Delegierung von Sicherheitskonten unterstützt werden.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent_failover](../../relational-databases/replication/codesnippet/tsql/sp-link-publication-tran_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_link_publication**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
