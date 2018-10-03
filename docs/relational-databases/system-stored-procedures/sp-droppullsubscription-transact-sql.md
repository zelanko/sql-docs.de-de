---
title: Sp_droppullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35b050798f9be9255b9ee35fdc0a8d378f03ecf5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733767"
---
# <a name="spdroppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht ein Abonnement in der aktuellen Datenbank des Abonnenten. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Pullabonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publisher=** ] **"***Verleger***"**  
 Der Name des Remoteservers. *Publisher* ist **Sysname**, hat keinen Standardwert. Wenn **alle**, das Abonnement zu die Verlegern gelöscht.  
  
 [  **@publisher_db=** ] **"***Publisher_db***"**  
 Der Name der Verlegerdatenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert. **alle** bedeutet, dass alle Verlegerdatenbanken.  
  
 [  **@publication=** ] **"***Veröffentlichung***"**  
 Ist der Veröffentlichungsname. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert. Wenn **alle**, das Abonnement ist für alle Veröffentlichungen gelöscht.  
  
 [  **@reserved=** ] *reserviert*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_droppullsubscription** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 **Sp_droppullsubscription** löscht die entsprechende Zeile in der [MSreplication_subscriptions &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) Tabelle und die entsprechenden Verteilungs-Agent auf dem Abonnenten. Wenn keine Zeilen im bleiben [MSreplication_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md), die Tabelle wird gelöscht.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle oder der Benutzer, der das Pullabonnement erstellt hat, kann ausführen **Sp_droppullsubscription**. Die **Db_owner** festen Datenbankrolle kann nur zum Ausführen **Sp_droppullsubscription** , wenn der Benutzer, die das Pullabonnement erstellt hat, die dieser Rolle gehört.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen eines Pullabonnements](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [Sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [Sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [Sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [Sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
