---
description: sp_link_publication (Transact-SQL)
title: sp_link_publication (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c1df8b2f62ce305b89b061526415c73e07a18511
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446952"
---
# <a name="sp_link_publication-transact-sql"></a>sp_link_publication (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Legt die Konfigurations- und Sicherheitsinformationen fest, die von den Synchronisierungstriggern der Abonnements mit sofortigem Update bei der Herstellung einer Verbindung mit dem Verleger verwendet werden. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
> [!IMPORTANT]
>  Beim Konfigurieren eines Verlegers mit einem Remoteverteiler werden die Werte, die für alle Parameter, einschließlich *job_login* und *job_password*, bereitgestellt werden, als Nur-Text an den Verteiler gesendet. Sie sollten die Verbindung zwischen dem Verleger und dem zugehörigen Remoteverteiler verschlüsseln, bevor Sie diese gespeicherte Prozedur ausführen. Weitere Informationen finden Sie unter [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
> 
> [!IMPORTANT]
>  Unter bestimmten Bedingungen kann bei dieser gespeicherten Prozedur ein Fehler auftreten, wenn auf dem Abonnenten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 oder höher ausgeführt wird und auf dem Verleger eine frühere Version ausgeführt wird. Falls in diesem Szenario ein Fehler bei der gespeicherten Prozdur auftritt, sollten Sie den Verleger auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 oder höher aktualisieren.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publisher = ] 'publisher'` Der Name des Verlegers, mit dem eine Verknüpfung hergestellt werden soll. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank, mit der eine Verknüpfung hergestellt werden soll. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, mit der eine Verknüpfung hergestellt werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @security_mode = ] security_mode` Der Sicherheitsmodus, der vom Abonnenten verwendet wird, um eine Verbindung mit einem Remote Verleger für das sofortige Aktualisieren herzustellen. *security_mode* ist vom Datentyp **int**. die folgenden Werte sind möglich: [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-Authentifizierung mit der in dieser gespeicherten Prozedur angegebenen Anmeldung als *Login* und *Password*.<br /><br /> Hinweis: in früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde diese Option zum Angeben eines dynamischen Remote Prozedur Aufrufs (RPC) verwendet.|  
|**1**|Verwendet den Sicherheitskontext ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung oder Windows-Authentifizierung) des Benutzers, der die Änderung auf dem Abonnenten ausführt.<br /><br /> Hinweis: dieses Konto muss auch auf dem Verleger mit ausreichenden Berechtigungen vorhanden sein. Bei Verwendung der Windows-Authentifizierung muss die Delegierung von Sicherheitskonten unterstützt werden.|  
|**2**|Verwendet einen vorhandenen benutzerdefinierten Anmelde Namen für den verknüpften Server, der mit **sp_link_publication**erstellt wurde.|  
  
`[ @login = ] 'login'` Der Anmelde Name. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. Dieser Parameter muss angegeben werden, *security_mode* wenn security_mode **0**ist.  
  
`[ @password = ] 'password'` Das Kennwort. *Password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter muss angegeben werden, *security_mode* wenn security_mode **0**ist.  
  
`[ @distributor = ] 'distributor'` Der Name des Verteilers. *Distributor* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_link_publication** wird von Abonnements mit sofortigem Update bei der Transaktions Replikation verwendet.  
  
 **sp_link_publication** können für Pushabonnements und Pullabonnements verwendet werden. Der Aufruf ist vor oder nach dem Erstellen des Abonnements möglich. Ein Eintrag wird in der [MSsubscription_properties &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) Systemtabelle eingefügt oder aktualisiert.  
  
 Bei Pushabonnements kann der Eintrag durch [sp_subscription_cleanup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)bereinigt werden. Für Pullabonnements kann der Eintrag durch [sp_droppullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md) oder [sp_subscription_cleanup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)bereinigt werden. Sie können auch **sp_link_publication** mit einem NULL-Kennwort anrufen, um den Eintrag in der [MSsubscription_properties &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md) Systemtabelle zu löschen.  
  
 Der Standardmodus, der von einem Abonnenten mit sofortigem Update verwendet wird, wenn eine Verbindung zum Verleger hergestellt wird, ermöglicht nicht die Verwendung einer Verbindung mit der Windows-Authentifizierung. Wenn Sie eine Verbindung mit der Windows-Authentifizierung herstellen möchten, muss ein Verbindungsserver für den Verleger eingerichtet werden. Der Abonnent mit sofortigem Update sollte diese Verbindung dann für das Update des Abonnenten verwenden. Dies erfordert, dass die **sp_link_publication** mit *security_mode*  =  **2**ausgeführt werden. Bei Verwendung der Windows-Authentifizierung muss die Delegierung von Sicherheitskonten unterstützt werden.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent_failover](../../relational-databases/replication/codesnippet/tsql/sp-link-publication-tran_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_link_publication**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_droppullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
