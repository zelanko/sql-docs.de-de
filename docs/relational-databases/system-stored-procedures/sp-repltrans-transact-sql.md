---
description: sp_repltrans (Transact-SQL)
title: sp_repltrans (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f8808b5955e18e56d9c49f8ce315a5f201c7837e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534894"
---
# <a name="sp_repltrans-transact-sql"></a>sp_repltrans (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt ein Resultset aller Transaktionen im Transaktionsprotokoll der Veröffentlichungsdatenbank zurück, die zwar für die Replikation gekennzeichnet, aber noch nicht als verteilt gekennzeichnet sind. Diese gespeicherte Prozedur wird auf dem Verleger für eine Veröffentlichungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>Resultsets  
 **sp_repltrans** gibt Informationen zur Veröffentlichungs Datenbank zurück, aus der Sie ausgeführt wird, sodass Sie derzeit nicht verteilte Transaktionen anzeigen können (die im Transaktionsprotokoll verbleibenden Transaktionen, die nicht an den Verteiler gesendet wurden). Das Resultset zeigt für jede Transaktion die Protokollfolgenummer des ersten und letzten Datensatzes an. **sp_repltrans** ist [sp_replcmds &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) vergleichbar, gibt jedoch keine Befehle für die Transaktionen zurück.  
  
## <a name="remarks"></a>Hinweise  
 **sp_repltrans** wird bei der Transaktions Replikation verwendet.  
  
 **sp_repltrans** wird für nicht--Verleger nicht unterstützt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_repltrans**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_repldone &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
