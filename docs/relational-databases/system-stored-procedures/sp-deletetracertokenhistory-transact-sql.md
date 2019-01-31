---
title: sp_deletetracertokenhistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f8f1a91210cbd263a9225cef54bcf27a81bf2bf4
ms.sourcegitcommit: dc3543e81e32451568133e9b1b560f7ee76d7fb5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2019
ms.locfileid: "55428597"
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt Überwachungstoken-Datensätze aus der [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) und [MStracer_history &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md) -Systemtabellen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_deletetracertokenhistory [ @publication = ] 'publication'   
    [ , [ @tracer_id = ] tracer_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=** ] **'***publication***'**  
 Der Name der Veröffentlichung, in die das Überwachungstoken eingefügt wurde. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@tracer_id=** ] *tracer_id*  
 Die ID des zu löschenden Überwachungstokens. *Tracer_id* ist **Int**, hat den Standardwert NULL. Wenn **null**, und klicken Sie dann alle Überwachungstoken, die zur Veröffentlichung gehörenden gelöscht werden.  
  
 [ **@cutoff_date=** ] *cutoff_date*  
 Gibt das Umstellungsdatum an, sodass alle vor diesem Datum in die Veröffentlichung eingefügten Überwachungstoken entfernt werden. *Cutoff_date* ist "DateTime", hat den Standardwert NULL.  
  
 [ **@publisher=** ] **'***publisher***'**  
 Der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL.  
  
> [!NOTE]
>  Dieser Parameter sollte nur angegeben werden, für nicht - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herausgeber oder beim Ausführen der gespeicherten Prozedur vom Verteiler.  
  
 [ **@publisher_db=** ] **'***publisher_db***'**  
 Der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird ignoriert, wenn die gespeicherte Prozedur auf dem Verleger ausgeführt wird.  
  
> [!NOTE]
>  Dieser Parameter sollte angegeben werden, wenn die gespeicherte Prozedur vom Verteiler ausgeführt.  

## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_deletetracertokenhistory** wird in Transaktionsreplikationen verwendet.  
  
 Beim Ausführen **Sp_deletetracertokenhistory**, Sie können nur eines angeben *Tracer_id* oder *Cutoff_date*. Wenn Sie beide Parameter angeben, wird eine Fehlermeldung angezeigt.  
  
 Wenn Sie nicht ausgeführt werden **Sp_deletetracertokenhistory** um Überwachungstoken-Metadaten zu entfernen, die Informationen bei der regelmäßig verlaufscleanups entfernt werden wird.  
  
 Überwachungstoken-IDs können bestimmt werden, indem Sie Ausführung [Sp_helptracertokens &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) oder durch Abfragen der [MStracer_tokens &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) -Systemtabelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle, die **Db_owner** feste Datenbankrolle in der Veröffentlichungsdatenbank oder **Db_owner** fester Datenbankname oder  **Replmonitor** Rollen in der Verteilungsdatenbank können ausführen **Sp_deletetracertokenhistory**.  
  
## <a name="see-also"></a>Siehe auch  
 [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_helptracertokenhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)  
  
  
