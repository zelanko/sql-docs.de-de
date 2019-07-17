---
title: Sp_dropsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropsubscription
- sp_dropsubscription_TSQL
helpviewer_keywords:
- sp_dropsubscription
ms.assetid: 7551f345-5510-4684-ab53-f9057249d13a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 923f3cd5d94bbae8cc9c0eac9361eada0cd73194
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124770"
---
# <a name="spdropsubscription-transact-sql"></a>sp_dropsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht Abonnements für bestimmte Artikel, Veröffentlichungen oder Abonnementgruppen auf dem Verleger. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
        , [ @subscriber= ] 'subscriber'  
    [ , [ @destination_db= ] 'destination_db' ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der zugeordneten Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL. Wenn **alle**, alle Abonnements für alle Veröffentlichungen für den angegebenen Abonnenten gelöscht. *Veröffentlichung* ist ein erforderlicher Parameter.  
  
`[ @article = ] 'article'` Ist der Name des Artikels. *Artikel* ist **Sysname**, hat den Standardwert NULL. Wenn **alle**, Abonnements aller Artikel für die einzelnen angegebenen Veröffentlichungen und Abonnenten werden gelöscht. Verwendung **alle** für Veröffentlichungen, die ermöglichen, sofort zu aktualisieren.  
  
`[ @subscriber = ] 'subscribe_r'` Ist der Name des Abonnenten, dessen Abonnements gelöscht werden. *Abonnenten* ist **Sysname**, hat keinen Standardwert. Wenn **alle**, alle Abonnements für alle Abonnenten werden gelöscht.  
  
`[ @destination_db = ] 'destination_db'` Ist der Name der Zieldatenbank. *Destination_db* ist **Sysname**, hat den Standardwert NULL. Bei einem Wert von NULL werden alle Abonnements dieses Abonnenten gelöscht.  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropsubscription** wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 Wenn Sie das Abonnement für den Artikel einer immediate-sync-Veröffentlichung löschen, können Sie das Abonnement nur wieder hinzufügen, wenn Sie die Abonnements für alle Artikel der Veröffentlichung löschen und sie alle in einem Schritt wieder hinzufügen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle die **Db_owner** feste Datenbankrolle oder der Benutzer, die der abonnementerstellung kann ausführen **Sp_dropsubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Löschen eines Pushabonnements](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
