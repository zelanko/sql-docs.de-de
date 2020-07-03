---
title: sp_mergesubscription_cleanup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergesubscription_cleanup
- sp_mergesubscription_cleanup_TSQL
helpviewer_keywords:
- sp_mergesubscription_cleanup
ms.assetid: bfad414f-2bda-4bf5-9507-56a1e743dfc4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: feb13050f5b508298ec45d5fde4ffde9aa510c9d
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891592"
---
# <a name="sp_mergesubscription_cleanup-transact-sql"></a>sp_mergesubscription_cleanup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt Metadaten, z. b. Trigger und Einträge, in " **sysmergeabonnements** " und " **sysmergearticles** ", nachdem das angegebene Mergepushabonnement auf dem Verleger entfernt wurde. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
> [!NOTE]  
>  Bei einem Pullabonnement werden Metadaten entfernt, wenn [sp_dropmergepullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md) ausgeführt wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_mergesubscription_cleanup [ @publisher =] 'publisher'  
        , [ @publisher_db =] 'publisher_db'  
        , [ @publication =] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_mergesubscription_cleanup** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_mergesubscription_cleanup**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Löschen eines Pushabonnements](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_expired_subscription_cleanup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-expired-subscription-cleanup-transact-sql.md)   
 [sp_subscription_cleanup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
