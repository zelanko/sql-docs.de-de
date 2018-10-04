---
title: Sp_droppublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_droppublication_TSQL
- sp_droppublication
helpviewer_keywords:
- sp_droppublication
ms.assetid: b52b37e6-4fec-40cf-abba-7dce4ff395fd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 66bb9fbb43647b6566ef641f63b047b84e37c1bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669468"
---
# <a name="spdroppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht eine Veröffentlichung und den ihr zugeordneten Momentaufnahme-Agent. Vor dem Löschen einer Veröffentlichung müssen alle Abonnements gelöscht werden. Die Artikel in der Veröffentlichung werden automatisch gelöscht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publication=** ] **"***Veröffentlichung***"**  
 Der Name der zu löschenden Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert. Wenn **alle** angegeben ist, werden alle Veröffentlichungen aus der Veröffentlichungsdatenbank, die keine Abonnements gelöscht werden.  
  
 [  **@ignore_distributor =** ] *Ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_droppublication** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 **Sp_droppublication** rekursiv alle einer Veröffentlichung zugeordneten Artikel gelöscht und anschließend wird die Veröffentlichung selbst gelöscht. Solange für eine Veröffentlichung ein Abonnement vorhanden ist, kann sie nicht gelöscht werden. Weitere Informationen zum Entfernen von Abonnements finden Sie unter [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) und [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 Ausführen von **Sp_droppublication** zum Löschen einer Veröffentlichung entfernt nicht veröffentlichten Objekte aus der Veröffentlichungsdatenbank oder der entsprechenden Objekte aus der Abonnementdatenbank. Verwenden Sie DROP \<Objekt > um diese Objekte manuell ggf. entfernen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_droppublication**.  
  
## <a name="examples"></a>Beispiele  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen einer Veröffentlichung](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
