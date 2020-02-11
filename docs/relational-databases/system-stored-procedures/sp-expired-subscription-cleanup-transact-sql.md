---
title: sp_expired_subscription_cleanup (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: fb556a464077092cacd7107a8c2b4b124c6db707
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124428"
---
# <a name="sp_expired_subscription_cleanup-transact-sql"></a>sp_expired_subscription_cleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Überprüft den Status aller Abonnements für jede Veröffentlichung und löscht abgelaufene Abonnements. Diese gespeicherte Prozedur wird auf dem Verleger für eine beliebige Datenbank oder auf dem Verteiler für die Verteilungs Datenbank für einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_expired_subscription_cleanup [ [ @publisher = ] 'publisher' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name eines nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verlegers. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Sie sollten diesen Parameter nicht für einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger festlegen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_expired_subscription_cleanup** wird bei allen Replikations Typen verwendet.  
  
 **sp_expired_subscription_cleanup** wird vom Auftrag Cleanup abgelaufener Abonnements ausgeführt, um alle 24 Stunden abgelaufene Abonnements aus Veröffentlichungs Datenbanken zu erkennen und zu entfernen. Wenn ein Abonnement nicht mehr aktuell ist, wenn es also während der Beibehaltungsdauer nicht mit dem Verleger synchronisiert wurde, wird die Veröffentlichung als abgelaufen bezeichnet. Die Ablaufverfolgungsdaten des Abonnements werden dann auf dem Verleger gelöscht. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_expired_subscription_cleanup**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_mergesubscription_cleanup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
