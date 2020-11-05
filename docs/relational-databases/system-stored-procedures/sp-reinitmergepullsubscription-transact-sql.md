---
description: sp_reinitmergepullsubscription (Transact-SQL)
title: sp_reinitmergepullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitmergepullsubscription
- sp_reinitmergepullsubscription_TSQL
helpviewer_keywords:
- sp_reinitmergepullsubscription
ms.assetid: 48464bc9-60aa-4886-b526-163f010102b8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 06b65044129dd302d516eabe3b9c13f6352d3035
ms.sourcegitcommit: b3a711a673baebb2ff10d7142b209982b46973ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93364805"
---
# <a name="sp_reinitmergepullsubscription-transact-sql"></a>sp_reinitmergepullsubscription (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Markiert ein Mergepullabonnement für die Neuinitialisierung bei der nächsten Ausführung des Merge-Agents. Diese gespeicherte Prozedur wird auf dem Abonnenten in der Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_reinitmergepullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert all.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert all.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert all.  
  
`[ @upload_first = ] 'upload_first'` Gibt an, ob Änderungen auf dem Abonnenten hochgeladen werden, bevor das Abonnement erneut initialisiert wird. *upload_first* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **True** gibt an, dass Änderungen hochgeladen werden, bevor das Abonnement erneut initialisiert wird. **False** gibt an, dass Änderungen nicht hochgeladen werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_reinitmergepullsubscription** wird bei der Mergereplikation verwendet.  
  
 Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
## <a name="examples"></a>Beispiele  

### <a name="a-reinitialize-the-pull-subscription-and-lose-pending-changes"></a>A. Das Pullabonnement erneut initialisieren und ausstehende Änderungen verlieren.

[!code-sql[HowTo#sp_reinitmergepullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergepullsubscr_1.sql)]  
  
### <a name="b-reinitialize-the-pull-subscription-and-upload-pending-changes"></a>B. Das Pullabonnement erneut initialisieren und ausstehende Änderungen hochladen

 [!code-sql[HowTo#sp_reinitmergepullsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergepullsubscr_2.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_reinitmergepullsubscription** ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erneutes Initialisieren eines Abonnements](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
