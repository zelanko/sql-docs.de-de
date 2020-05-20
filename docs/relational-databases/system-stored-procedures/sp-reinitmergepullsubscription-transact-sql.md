---
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 131925ed4ef1e7521db2f41b915a5f671723a980
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826566"
---
# <a name="sp_reinitmergepullsubscription-transact-sql"></a>sp_reinitmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert all.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert all.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert all.  
  
`[ @upload_first = ] 'upload_first'`Gibt an, ob Änderungen auf dem Abonnenten hochgeladen werden, bevor das Abonnement erneut initialisiert wird. *upload_first* ist vom Datentyp **nvarchar (5)** und hat den Standardwert false. **True**gibt an, dass Änderungen hochgeladen werden, bevor das Abonnement erneut initialisiert wird. **False**gibt an, dass Änderungen nicht hochgeladen werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_reinitmergepullsubscription** wird bei der Mergereplikation verwendet.  
  
 Wenn Sie einen parametrisierten Filter hinzufügen, löschen oder ändern, können ausstehende Änderungen auf dem Abonnenten während der erneuten Initialisierung nicht auf den Verleger hochgeladen werden. Wenn Sie ausstehende Änderungen hochladen möchten, sollten Sie vor dem Ändern des Filters alle Abonnements synchronisieren.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_reinitmergepullsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergepullsubscr_1.sql)]  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_reinitmergepullsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergepullsubscr_2.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_reinitmergepullsubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erneutes Initialisieren eines Abonnements](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Abonnements erneut initialisieren](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
