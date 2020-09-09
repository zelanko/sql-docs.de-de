---
description: sp_setreplfailovermode (Transact-SQL)
title: sp_setreplfailovermode (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 205c2269ff0a87ee2afda39eb2a0db4a83bbf20a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551222"
---
# <a name="sp_setreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ermöglicht das Festlegen des Failoveroperationsmodus für Abonnements, die für sofortige Updates mit Updates über eine Warteschlange als Failover aktiviert sind. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt. Weitere Informationen zu Failovermodi finden Sie unter [aktualisierbare Abonnements für die Transaktions Replikation](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Die Veröffentlichung muss bereits vorhanden sein.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @failover_mode = ] 'failover_mode'` Der Failovermodus für das Abonnement. *failover_mode* ist vom Datentyp **nvarchar (10)** . die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**direkt** oder **synchronisiert**|Datenänderungen, die auf dem Abonnenten durchgeführt werden, werden bei ihrem Auftreten mithilfe eines Massenkopiervorgangs auf den Verleger übertragen.|  
|**Warteschlange**|Datenänderungen werden in einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Warteschlange gespeichert.|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing wurde als veraltet markiert und wird nicht mehr unterstützt.  
  
`[ @override = ] override` Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_setreplfailovermode** wird bei der Momentaufnahme-oder Transaktions Replikation verwendet, bei der Abonnements entweder für das verzögerte Update über eine Warteschlange mit einem Failover auf eine sofortige Aktualisierung oder für sofortige Updates mit Failover zum verzögertem Update über eine Warteschlange aktiviert sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_setreplfailovermode**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wechseln zwischen Update Modi für ein Aktualisier bares Transaktions Abonnement](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
