---
title: sp_restoremergeidentityrange (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5160e0f734f68450f868f3b1c670b1e5647524ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041053"
---
# <a name="sp_restoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mit dieser gespeicherten Prozedur werden Identitätsbereichszuweisungen aktualisiert. Dies stellt sicher, dass die automatische Identitätsbereichsverwaltung ordnungsgemäß ausgeführt wird, nachdem ein Verleger von einer Sicherung wiederhergestellt wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **all**. Wenn dieses Argument angegeben ist, werden nur Identitätsbereiche für diese Veröffentlichung wiederhergestellt.  
  
`[ @article = ] 'article'`Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert **all**. Wenn dieses Argument angegeben ist, werden nur Identitätsbereiche für diesen Artikel wiederhergestellt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_restoremergeidentityrange** wird bei der Mergereplikation verwendet.  
  
 **sp_restoremergeidentityrange** Ruft die maximalen Informationen zur Identitäts Bereichs Zuordnung vom Verteiler ab und aktualisiert Werte in der Spalte **max_used** der [MSmerge_identity_range_allocations &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md) für die Artikel, die die automatische Identitäts Bereichs Verwaltung verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_restoremergeidentityrange**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addmergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [Replizieren von Identitätsspalten](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
