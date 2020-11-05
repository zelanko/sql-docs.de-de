---
description: sp_reinitmergesubscription (Transact-SQL)
title: sp_reinitmergesubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitmergesubscription_TSQL
- sp_reinitmergesubscription
helpviewer_keywords:
- sp_reinitmergesubscription
ms.assetid: 249a4048-e885-48e0-a92a-6577f59de751
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bc1d2d3dc8b9763d19410b2a9773fb7766d22140
ms.sourcegitcommit: b3a711a673baebb2ff10d7142b209982b46973ae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93364741"
---
# <a name="sp_reinitmergesubscription-transact-sql"></a>sp_reinitmergesubscription (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Markiert ein Mergeabonnement für die Neuinitialisierung bei der nächsten Ausführung des Merge-Agents. Diese gespeicherte Prozedur wird auf dem Verleger in der Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_reinitmergesubscription [ [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber'  
    [ , [ @subscriber_db = ] 'subscriber_db'  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert **all**.  
  
`[ @subscriber = ] 'subscriber'` Der Name des Abonnenten. *Subscriber* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert **all**.  
  
`[ @subscriber_db = ] 'subscriber_db'` Der Name der Abonnenten Datenbank. *subscriber_db* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert **all**.  
  
`[ @upload_first = ] 'upload_first'` Gibt an, ob Änderungen auf dem Abonnenten hochgeladen werden, bevor das Abonnement erneut initialisiert wird. *upload_first* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **True** gibt an, dass Änderungen hochgeladen werden, bevor das Abonnement erneut initialisiert wird. **False** gibt an, dass Änderungen nicht hochgeladen werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_reinitmergesubscription** wird bei der Mergereplikation verwendet.  
  
 **sp_reinitmergesubscription** können vom Verleger aufgerufen werden, um Mergeabonnements erneut zu initialisieren. Wir empfehlen auch die erneute Ausführung des Momentaufnahme-Agents.  
  
 Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
## <a name="examples"></a>Beispiele  

### <a name="a-reinitialize-the-push-subscription-and-lose-pending-changes"></a>A. Erneutes Initialisieren des Pushabonnements und Verlust von ausstehenden Änderungen

 [!code-sql[HowTo#sp_reinitmergepushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_1.sql)]  
  
### <a name="b-reinitialize-the-push-subscription-and-upload-pending-changes"></a>B. Erneutes Initialisieren des Pushabonnements und Hochladen von ausstehenden Änderungen
 [!code-sql[HowTo#sp_reinitmergepushsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_2.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_reinitmergesubscription** ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erneutes Initialisieren von Abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
