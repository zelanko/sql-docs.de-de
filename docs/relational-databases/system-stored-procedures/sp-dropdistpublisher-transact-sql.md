---
title: Sp_dropdistpublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistpublisher
- sp_dropdistpublisher_TSQL
helpviewer_keywords:
- sp_dropdistpublisher
ms.assetid: c0bdd3de-3be0-455c-898a-98d4660e7ce3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ee7d2a6a50e03f6b0029e69dbf2b5c211004fe18
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52813022"
---
# <a name="spdropdistpublisher-transact-sql"></a>sp_dropdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht einen Verteilungsverleger. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropdistpublisher [ @publisher = ] 'publisher'  
    [ , [ @no_checks = ] no_checks ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@publisher=** ] **"***Verleger***"**  
 Der Verleger, der gelöscht werden soll. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@no_checks=** ] *No_checks*  
 Gibt an, ob **Sp_dropdistpublisher** stellt sicher, dass der Verleger den Server als Verteiler deinstalliert hat. *No_checks* ist **Bit**, hat den Standardwert **0**.  
  
 Wenn **0**, Replikation stellt sicher, dass der Remoteverleger den lokalen Server als Verteiler deinstalliert hat. Wenn es sich beim Verleger um einen lokalen Verleger handelt, überprüft die Replikation, ob sich auf dem lokalen Server keine Veröffentlichungs- oder Verteilungsobjekte mehr befinden.  
  
 Wenn **1**, alle dem Verteilungsverleger zugeordneten Replikationsobjekte gelöscht, selbst wenn ein Remoteverleger nicht erreicht werden kann. Nach dem auf diese Weise muss der Remoteverleger deinstallieren, mithilfe von Replikation [Sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md) mit **@ignore_distributor**  =  **1**.  
  
 [  **@ignore_distributor=** ] *Ignore_distributor*  
 Gibt an, ob Verteilungsobjekte auf dem Verteiler bleiben, wenn der Verleger entfernt wird. *Ignore_distributor* ist **Bit** und kann einen der folgenden Werte:  
  
 **1** = für Verteilungsobjekte, die zu gehören die *Verleger* verbleiben auf dem Verteiler.  
  
 **0** = für Verteilungsobjekte der *Verleger* werden bereinigt auf dem Verteiler.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_dropdistpublisher** wird in allen Replikationstypen verwendet.  
  
 Wenn Sie einen Oracle-Verleger, wenn dies nicht möglich, so löschen Sie den Verleger löschen **Sp_dropdistpublisher** gibt einen Fehler und die Verteilungsobjekte für den Verleger werden entfernt.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistpublisher-tra_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_dropdistpublisher**.  
  
## <a name="see-also"></a>Siehe auch  
 [Deaktivieren der Veröffentlichung und Verteilung](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
