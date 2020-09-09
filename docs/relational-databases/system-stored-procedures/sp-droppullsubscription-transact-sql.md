---
description: sp_droppullsubscription (Transact-SQL)
title: sp_droppullsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e4e7e0f9292d9ed94139b9facfe496821b91fb03
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543440"
---
# <a name="sp_droppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Löscht ein Abonnement in der aktuellen Datenbank des Abonnenten. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Pullabonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Remote Servers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn **alle**, wird das Abonnement auf allen Verlegern abgelegt.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Verleger Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. **all** bezeichnet alle Verleger Datenbanken.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn **dies der Wert ist,** wird das Abonnement für alle Veröffentlichungen gelöscht.  
  
`[ @reserved = ] reserved` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_droppullsubscription** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 **sp_droppullsubscription** löscht die entsprechende Zeile in der [MSreplication_subscriptions &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) Tabelle und den entsprechenden Verteiler-Agent auf dem Abonnenten. Wenn [MSreplication_subscriptions &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)keine Zeilen verbleiben, wird die Tabelle gelöscht.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der Benutzer, der das Pullabonnement erstellt hat, können **sp_droppullsubscription**ausführen. Die **db_owner** festgelegte Daten Bank Rolle kann nur **sp_droppullsubscription** ausgeführt werden, wenn der Benutzer, der das Pullabonnement erstellt hat, zu dieser Rolle gehört.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Löschen eines Pullabonnements](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
