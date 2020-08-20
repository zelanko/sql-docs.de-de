---
description: sp_addmergepullsubscription (Transact-SQL)
title: sp_addmergepullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_TSQL
- sp_addmergepullsubscription
helpviewer_keywords:
- sp_addmergepullsubscription
ms.assetid: d63909a0-8ea7-4734-9ce8-8204d936a3e4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: af86ada2400422732d910752538de54f42b01437
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489603"
---
# <a name="sp_addmergepullsubscription-transact-sql"></a>sp_addmergepullsubscription (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Fügt ein Pullabonnement zu einer Mergeveröffentlichung hinzu. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmergepullsubscription [ @publication= ] 'publication'   
    [ , [ @publisher= ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @subscriber_type= ] 'subscriber_type' ]   
    [ , [ @subscription_priority= ] subscription_priority ]   
    [ , [ @sync_type= ] 'sync_type' ]   
    [ , [ @description= ] 'description' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom Datentyp **vom Datentyp sysname**. der Standardwert ist der Name des lokalen Servers. Der Verleger muss ein gültiger Server sein.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @subscriber_type = ] 'subscriber_type'` Der Typ des Abonnenten. *subscriber_type* ist vom Datentyp **nvarchar (15)** und kann **Global**, **local** oder **Anonymous**sein. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen werden lokale Abonnements als Client Abonnements und globale Abonnements als Server Abonnements bezeichnet.  
  
`[ @subscription_priority = ] subscription_priority` Die Abonnement Priorität. *subscription_priority*ist **Real**, der Standardwert ist NULL. Für lokale und anonyme Abonnements ist die Priorität **0,0**. Die Priorität wird vom Standardresolver verwendet, um einen Gewinner zu ermitteln, wenn Konflikte erkannt werden. Für globale Abonnenten muss die Abonnementpriorität kleiner als 100 sein. Dieser Wert gibt die Priorität des Verlegers an.  
  
`[ @sync_type = ] 'sync_type'` Der Synchronisierungstyp des Abonnements. *sync_type*ist vom Datentyp **nvarchar (15)**. der Standardwert ist **automatisch**. Kann " **Automatic** " oder " **None**" sein. Wenn **automatisch**, werden das Schema und die Anfangsdaten für veröffentlichte Tabellen zuerst an den Abonnenten übertragen. Wenn **keiner**vorhanden ist, wird davon ausgegangen, dass der Abonnent bereits über das Schema und die Anfangsdaten für veröffentlichte Tabellen verfügt. Systemtabellen und Daten werden immer übertragen.  
  
> [!NOTE]  
>  Es wird nicht empfohlen, den Wert " **None**" anzugeben.  
  
`[ @description = ] 'description'` Eine kurze Beschreibung dieses Pullabonnements. die *Beschreibung*ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Dieser Wert wird vom Replikations Monitor in der Spalte Anzeige **Name** angezeigt, der zum Sortieren der Abonnements für eine überwachte Veröffentlichung verwendet werden kann.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_addmergepullsubscription** wird für die Mergereplikation verwendet.  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Agent zum Synchronisieren des Abonnements verwendet wird, muss die gespeicherte Prozedur [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) auf dem Abonnenten ausgeführt werden, um einen Agent und einen Auftrag für die Synchronisierung mit der Veröffentlichung zu erstellen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_1.sql)]  
  
 [!code-sql[HowTo#sp_addmergepullsub_websync_anon](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_2.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_addmergepullsubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Abonnieren von Veröffentlichungen](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription_agent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_changemergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
