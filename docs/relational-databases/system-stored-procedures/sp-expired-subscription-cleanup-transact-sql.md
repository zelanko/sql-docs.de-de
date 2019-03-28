---
title: Sp_expired_subscription_cleanup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_expired_subscription_cleanup
- SP_EXPIRED_SUBSCRIPTION_CLEANUP_TSQL
helpviewer_keywords:
- sp_expired_subscription_cleanup
ms.assetid: 6abc29fe-d77a-4673-9d99-ae31c688012c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c8073b4e02e1eff910654bba635819b94b5cf5b2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532512"
---
# <a name="spexpiredsubscriptioncleanup-transact-sql"></a>sp_expired_subscription_cleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Überprüft den Status aller Abonnements für jede Veröffentlichung und löscht abgelaufene Abonnements. Diese gespeicherte Prozedur ausgeführt wird, auf dem Verleger für jede Datenbank oder auf dem Verteiler für die Verteilungsdatenbank für einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_expired_subscription_cleanup [ [ @publisher = ] 'publisher' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name eines nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL. Sie sollten diesen Parameter nicht für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger festlegen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_expired_subscription_cleanup** wird in allen Replikationstypen verwendet.  
  
 **Sp_expired_subscription_cleanup** vom Auftrag Cleanup abgelaufener Abonnements zu erkennen und entfernen abgelaufene Abonnements aus Veröffentlichungsdatenbanken alle 24 Stunden ausgeführt wird. Wenn ein Abonnement nicht mehr aktuell ist, wenn es also während der Beibehaltungsdauer nicht mit dem Verleger synchronisiert wurde, wird die Veröffentlichung als abgelaufen bezeichnet. Die Ablaufverfolgungsdaten des Abonnements werden dann auf dem Verleger gelöscht. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_expired_subscription_cleanup**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
