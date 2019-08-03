---
title: sp_replqueuemonitor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
author: stevestein
ms.author: sstein
ms.openlocfilehash: baf3281ade8e62b30f87e01a7024dc12d7032667
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770912"
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Listet die Warteschlangen Nachrichten aus [!INCLUDE[msCoName](../../includes/msconame-md.md)] einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Warte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Schlange oder Message Queuing für Abonnements mit verzögertem Update über eine angegebene Veröffentlichung. Falls [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlangen verwendet werden, wird diese gespeicherte Prozedur auf dem Abonnenten für die Abonnementdatenbank ausgeführt. Falls Message Queuing verwendet wird, wird sie auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Der Server muss für das Veröffentlichen konfiguriert sein. NULL gibt alle Verleger an.  
  
`[ @publisherdb = ] 'publisher_db' ]`Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. NULL gibt alle Veröffentlichungsdatenbanken an.  
  
`[ @publication = ] 'publication' ]`Der Name der Veröffentlichung. *Publication*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. NULL gibt alle Veröffentlichungen an.  
  
`[ @tranid = ] 'tranid' ]`Die Transaktions-ID. *tranid*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. NULL gibt alle Transaktionen an.  
  
 **[@queuetype=** ] **'***QueueType***'** ]  
 Der Typ von Warteschlange, in der Transaktionen gespeichert werden. Queue *Type* ist vom Datentyp **tinyint** . der Standardwert ist **0**. die folgenden Werte sind möglich.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Alle Warteschlangentypen|  
|**1**|Message Queuing|  
|**2**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replqueuemonitor** wird bei der Momentaufnahme-oder Transaktions Replikation mit Abonnements mit verzögertem Update über eine Warteschlange verwendet. Die Warteschlangennachrichten, die keine SQL-Befehle enthalten oder Teil eines umfassenden SQL-Befehls sind, werden nicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_replqueuemonitor**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
