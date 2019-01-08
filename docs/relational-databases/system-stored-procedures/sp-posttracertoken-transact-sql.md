---
title: Sp_posttracertoken (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- posttracerttoken
- posttracerttoken_TSQL
- sp_posttracertoken
- sp_posttracertoken_TSQL
helpviewer_keywords:
- sp_posttracertoken
ms.assetid: 24da5cd2-1c45-475e-93db-5bdf660f1c2c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 41053bee3449ae44f843c24069c11a288131950b
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589349"
---
# <a name="spposttracertoken-transact-sql"></a>sp_posttracertoken (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Mit dieser Prozedur wird ein Überwachungstoken in das Transaktionsprotokoll am Verleger platziert, und der Prozess der Nachverfolgung von Statistiken über Latenzzeiten wird gestartet. Informationen werden erfasst, wenn das Überwachungstoken in das Transaktionsprotokoll geschrieben wird, wenn es vom Protokolllese-Agent aufgenommen wird und vom Verteilungs-Agent angewendet wird. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt. Weitere Informationen finden Sie unter [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_posttracertoken [ @publication = ] 'publication'   
    [ , [ @tracer_token_id = ] tracer_token_id OUTPUT  
    [ , [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication**=] **"**_Veröffentlichung_**"**  
 Der Name der Veröffentlichung, für die die Latenzzeit ermittelt wird. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [  **@tracer_token_id=** ] _Tracer_token_id_**Ausgabe**  
 Die ID des eingefügten Überwachungstokens. *Tracer_token_id* ist **Int** hat den Standardwert NULL, und es ist ein OUTPUT-Parameter. Dieser Wert kann verwendet werden, zum Ausführen [Sp_helptracertokenhistory &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md) oder [Sp_deletetracertokenhistory &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md) ohne die erste Ausführung [Sp_helptracertokens &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md).  
  
 [  **@publisher=** ] **"**_Verleger_**"**  
 Gibt einen nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat den Standardwert NULL und sollte nicht angegeben werden, für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_posttracertoken** wird in Transaktionsreplikationen verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-posttracertoken-trans_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_posttracertoken**.  
  
## <a name="see-also"></a>Siehe auch  
 [Messen der Latenzzeit und Überprüfen der Verbindungen bei Transaktionsreplikationen](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
