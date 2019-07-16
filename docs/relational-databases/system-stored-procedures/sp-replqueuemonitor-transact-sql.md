---
title: Sp_replqueuemonitor (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: d8c931f4ec38fe6099afa6b098445dcdbc52b0be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089998"
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet die Warteschlangennachrichten aus einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Warteschlange oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing für Abonnements mit verzögertem Aktualisieren in einer bestimmten Veröffentlichung. Falls [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlangen verwendet werden, wird diese gespeicherte Prozedur auf dem Abonnenten für die Abonnementdatenbank ausgeführt. Falls Message Queuing verwendet wird, wird sie auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
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
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL. Der Server muss für das Veröffentlichen konfiguriert sein. NULL gibt alle Verleger an.  
  
`[ @publisherdb = ] 'publisher_db' ]` Ist der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. NULL gibt alle Veröffentlichungsdatenbanken an.  
  
`[ @publication = ] 'publication' ]` Ist der Name der Veröffentlichung. *Veröffentlichung*ist **Sysname**, hat den Standardwert NULL. NULL gibt alle Veröffentlichungen an.  
  
`[ @tranid = ] 'tranid' ]` Wird die Transaktions-ID. *der Standard*ist **Sysname**, hat den Standardwert NULL. NULL gibt alle Transaktionen an.  
  
 [ **@queuetype=** ] **"***Queuetype***"** ]  
 Der Typ von Warteschlange, in der Transaktionen gespeichert werden. *Queuetype* ist **Tinyint** hat den Standardwert **0**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Alle Warteschlangentypen|  
|**1**|Message Queuing|  
|**2**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Warteschlange|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replqueuemonitor** werden in der momentaufnahmereplikation oder Transaktionsreplikation mit Abonnements mit verzögertem Aktualisieren. Die Warteschlangennachrichten, die keine SQL-Befehle enthalten oder Teil eines umfassenden SQL-Befehls sind, werden nicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_replqueuemonitor**.  
  
## <a name="see-also"></a>Siehe auch  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
