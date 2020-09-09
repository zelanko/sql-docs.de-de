---
description: sp_helpmergesubscription (Transact-SQL)
title: sp_helpmergesubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergesubscription
- sp_helpmergesubscription_TSQL
helpviewer_keywords:
- sp_helpmergesubscription
ms.assetid: da564112-f769-4e67-9251-5699823e8c86
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 48d40b3209311968443a6c6d2b713b4aa1e3d43a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535197"
---
# <a name="sp_helpmergesubscription-transact-sql"></a>sp_helpmergesubscription (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen über ein Abonnement (Push und Pull) für eine Mergeveröffentlichung zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Wiederveröffentlichungsabonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergesubscription [ [ @publication=] 'publication']  
    [ , [ @subscriber=] 'subscriber']  
    [ , [ @subscriber_db=] 'subscriber_db']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
    [ , [ @found=] 'found' OUTPUT]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** . Die Veröffentlichung muss bereits vorhanden sein und den Regeln für Bezeichner entsprechen. Wenn der Wert NULL oder **%** ist, werden Informationen zu allen Mergeveröffentlichungen und Abonnements in der aktuellen Datenbank zurückgegeben.  
  
`[ @subscriber = ] 'subscriber'` Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** . Mit NULL oder % werden Informationen zu allen Abonnements einer bestimmten Veröffentlichung zurückgegeben.  
  
`[ @subscriber_db = ] 'subscriber_db'` Der Name der Abonnement Datenbank. *subscriber_db*ist vom **Datentyp vom Datentyp sysname**und hat **%** den Standardwert, mit dem Informationen zu allen Abonnement Datenbanken zurückgegeben werden.  
  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. Der Verleger muss ein gültiger Server sein. *Publisher*ist vom **Datentyp vom Datentyp sysname**und **%** hat den Standardwert, mit dem Informationen zu allen Verlegern zurückgegeben werden.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db*ist vom **Datentyp vom Datentyp sysname**und hat **%** den Standardwert, mit dem Informationen zu allen Verleger Datenbanken zurückgegeben werden.  
  
`[ @subscription_type = ] 'subscription_type'` Der Abonnementtyp. *subscription_type*ist vom Datentyp **nvarchar (15)**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**Push** (Standard)|Pushabonnement|  
|**auszu**|Pull-Abonnement|  
|**zwar**|Sowohl ein Push- als auch ein Pullabonnement|  
  
`[ @found = ] 'found'OUTPUT` Ein Flag, das die Rückgabe von Zeilen angibt. " *found*" ist vom Datentyp **int** und ein Output-Parameter. der Standardwert ist NULL. **1** gibt an, dass die Veröffentlichung gefunden wurde. **0** gibt an, dass die Veröffentlichung nicht gefunden wurde.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|Name des Abonnements.|  
|**ung**|**sysname**|Name der Veröffentlichung.|  
|**publisher**|**sysname**|Name des Verlegers.|  
|**publisher_db**|**sysname**|Name der Verlegerdatenbank.|  
|**Abonnenten**|**sysname**|Der Name des Abonnenten.|  
|**subscriber_db**|**sysname**|Name der Abonnementdatenbank.|  
|**status**|**int**|Status des Abonnements:<br /><br /> **0** = alle Aufträge warten auf den Start<br /><br /> **1** = mindestens ein Auftrag wird gestartet.<br /><br /> **2** = alle Aufträge wurden erfolgreich ausgeführt.<br /><br /> **3** = mindestens ein Auftrag wird ausgeführt<br /><br /> **4** = alle Aufträge sind geplant und im Leerlauf<br /><br /> **5** = mindestens ein Auftrag versucht, nach einem vorherigen Fehler auszuführen<br /><br /> **6** = mindestens ein Auftrag konnte nicht erfolgreich ausgeführt werden.|  
|**subscriber_type**|**int**|Abonnententyp|  
|**subscription_type**|**int**|Typ des Abonnements:<br /><br /> **0** = Push<br /><br /> **1** = Pull<br /><br /> **2** = beides|  
|**priority**|**float (8)**|Zahl zur Angabe der Priorität für das Abonnement.|  
|**sync_type**|**tinyint**|Synchronisierungsart des Abonnements.|  
|**description**|**nvarchar(255)**|Kurze Beschreibung des Mergeabonnements.|  
|**merge_jobid**|**Binary (16)**|Auftrags-ID des Merge-Agents.|  
|**full_publication**|**tinyint**|Gibt an, ob das Abonnement für eine vollständige oder gefilterte Veröffentlichung besteht.|  
|**offload_enabled**|**bit**|Gibt an, ob festgelegt wurde, dass die Auslagerungsausführung eines Replikations-Agents auf dem Abonnenten ausgeführt wird. Bei NULL erfolgt die Ausführung auf dem Verleger.|  
|**offload_server**|**sysname**|Name des Servers, auf den der Agent verlagert wird.|  
|**use_interactive_resolver**|**int**|Gibt zurück, ob der interaktive Konfliktlöser während der Konfliktlösung verwendet wird. Wenn der Wert **0**ist, wird der interaktive Konflikt Löser nicht verwendet.|  
|**hostname**|**sysname**|Der Wert, der angegeben wird, wenn ein Abonnement nach dem Wert der [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) Funktion gefiltert wird.|  
|**subscriber_security_mode**|**smallint**|Der Sicherheitsmodus auf dem Abonnenten, wobei **1** die Windows-Authentifizierung und **0** die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung bedeutet.|  
|**subscriber_login**|**sysname**|Der Anmeldename auf dem Abonnenten.|  
|**subscriber_password**|**sysname**|Das tatsächliche Abonnentenkennwort wird nie zurückgegeben. Das Ergebnis wird durch eine ""-Zeichenfolge maskiert **\*\*\*\*\*\*** .|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpmergesubscription** wird bei der Mergereplikation verwendet, um auf dem Verleger oder dem wieder Veröffentlichungs Abonnenten gespeicherte Abonnement Informationen zurückzugeben.  
  
 Bei anonymen Abonnements ist der *subscription_type*Wert immer **1** (Pull). Sie müssen jedoch [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md) auf dem Abonnenten ausführen, um Informationen zu anonymen Abonnements zu erhalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** oder der Veröffentlichungs Zugriffsliste für die Veröffentlichung, zu der das Abonnement gehört, können **sp_helpmergesubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addmergesubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
