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
ms.openlocfilehash: d3c84d15087c3cb6bb63380bc6cf0c75e773b883
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74055218"
---
# <a name="sp_replqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Listet die Warteschlangen Nachrichten aus einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Warteschlange oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing für Abonnements mit verzögertem Update über eine bestimmte Veröffentlichung. Falls [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlangen verwendet werden, wird diese gespeicherte Prozedur auf dem Abonnenten für die Abonnementdatenbank ausgeführt. Falls Message Queuing verwendet wird, wird sie auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` ist der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Der Server muss für das Veröffentlichen konfiguriert sein. NULL gibt alle Verleger an.  
  
`[ @publisherdb = ] 'publisher_db' ]` ist der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. NULL gibt alle Veröffentlichungsdatenbanken an.  
  
`[ @publication = ] 'publication' ]` ist der Name der Veröffentlichung. *Publication*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. NULL gibt alle Veröffentlichungen an.  
  
`[ @tranid = ] 'tranid' ]` ist die Transaktions-ID. *tranid*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. NULL gibt alle Transaktionen an.  
  
`[ @queuetype = ] 'queuetype' ]` ist der Typ der Warteschlange, in der Transaktionen gespeichert werden. Queue *Type* ist vom Datentyp **tinyint** . der Standardwert ist **0**. die folgenden Werte sind möglich.  
  
|ReplTest1|und Beschreibung|  
|-----------|-----------------|  
|**0**|Alle Warteschlangentypen|  
|**1**|Message Queuing|  
|**2**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Remarks  
 **sp_replqueuemonitor** wird bei der Momentaufnahme-oder Transaktions Replikation mit Abonnements mit verzögertem Update über eine Warteschlange verwendet. Die Warteschlangennachrichten, die keine SQL-Befehle enthalten oder Teil eines umfassenden SQL-Befehls sind, werden nicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_replqueuemonitor**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
