---
title: sp_help_publication_access (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_publication_access
- sp_help_publication_access_TSQL
helpviewer_keywords:
- sp_help_publication_access
ms.assetid: 9408fa13-54a0-4cb1-8fb0-845e5536ef50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7c562c039b65f99f1d3d9915f0dd00b93dc95860
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770995"
---
# <a name="sphelppublicationaccess-transact-sql"></a>sp_help_publication_access (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt eine Liste aller Anmeldenamen zurück, denen der Zugriff auf eine Veröffentlichung erteilt wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_publication_access [ @publication = ] 'publication'  
    [ , [ @return_granted = ] 'return_granted' ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @initial_list = ] initial_list ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, auf die zugegriffen werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @return_granted = ] 'return_granted'`Die Anmelde-ID. *return_granted* ist vom Typ **Bit**. der Standardwert ist 1. Wenn **0** angegeben und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet wird, werden die verfügbaren Anmeldungen, die auf dem Verleger, aber nicht auf dem Verteiler angezeigt werden, zurückgegeben. Wenn **0** angegeben ist und die Windows-Authentifizierung verwendet wird, werden die Anmeldungen zurückgegeben, denen der Zugriff auf dem Verleger oder dem Verteiler nicht ausdrücklich verweigert wird.  
  
`[ @login = ] 'login'`Die Standard-Sicherheits Anmelde-ID. *Login* ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist.  
  
`[ @initial_list = ] initial_list`Gibt an, ob alle Member mit Veröffentlichungs Zugriff oder nur diejenigen zurückgegeben werden sollen, die vor dem Hinzufügen neuer Mitglieder zur Liste Zugriff hatten. *initial_list* ist vom Typ Bit. der Standardwert ist **0**.  
  
 **1** gibt Informationen für alle Mitglieder der festen Server Rolle **sysadmin** mit gültigen Anmeldungen auf dem Verteiler zurück, die beim Erstellen der Veröffentlichung vorhanden waren, sowie den aktuellen Anmelde Namen.  
  
 **0** gibt Informationen für alle Mitglieder der festen Server Rolle **sysadmin** mit gültigen Anmeldungen auf dem Verteiler zurück, die beim Erstellen der Veröffentlichung vorhanden waren, sowie alle Benutzer in der Veröffentlichungs Zugriffsliste, die nicht zur **sysadmin gehören.** festes Server Rolle.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**LoginName**|**nvarchar(256)**|Tatsächlicher Anmeldename|  
|**Isntname**|**int**|**0** = der Anmelde Name ist kein Windows-Benutzer.<br /><br /> **1** = der Anmelde Name ist ein Windows-Benutzer.|  
|**Isntgroup**|**int**|**0** = der Anmelde Name ist keine Windows-Gruppe.<br /><br /> **1** = der Anmelde Name ist eine Windows-Gruppe.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_help_publication_access** wird für alle Replikations Typen verwendet.  
  
 Wenn sowohl **Isntname** als auch **Isntgroup** im Resultset den Wert **0**haben, wird davon ausgegangen, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Anmeldung eine Anmeldung ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_help_publication_access**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_grant_publication_access &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;(Transact-SQL)&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
