---
description: sp_reinitpullsubscription (Transact-SQL)
title: sp_reinitpullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitpullsubscription_TSQL
- sp_reinitpullsubscription
helpviewer_keywords:
- sp_reinitpullsubscription
ms.assetid: 7d9abe49-ce92-47f3-82c9-aea749518c91
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 74a3aa00a5b298639b1e643842af1d834a664d58
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446845"
---
# <a name="sp_reinitpullsubscription-transact-sql"></a>sp_reinitpullsubscription (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Diese Prozedur markiert ein Transaktionspullabonnement oder ein anonymes Abonnement für die Neuinitialisierung bei der nächsten Ausführung des Verteilungs-Agents. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Pullabonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_reinitpullsubscription [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**. der Standardwert all gibt an, dass alle Abonnements für die erneute Initialisierung markiert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_reinitpullsubscription** wird bei der Transaktions Replikation verwendet.  
  
 **sp_reinitpullsubscription** wird für die Peer-zu-Peer-Transaktions Replikation nicht unterstützt.  
  
 **sp_reinitpullsubscription** können vom Abonnenten aufgerufen werden, um das Abonnement während der nächsten Durchführung der Verteilungs-Agent erneut zu initialisieren.  
  
 Abonnements von Veröffentlichungen, die mit dem Wert **false** für ** \@ immediate_sync** erstellt wurden, können vom Abonnenten nicht erneut initialisiert werden.  
  
 Sie können ein Pullabonnement erneut initialisieren, indem Sie **sp_reinitpullsubscription** auf dem Abonnenten oder **sp_reinitsubscription** auf dem Verleger ausführen.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_reinitpullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitpullsubscriptio_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_reinitpullsubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erneutes Initialisieren eines Abonnements](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
