---
title: Sp_deletepeerrequesthistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletepeerrequesthistory
- sp_deletepeerrequesthistory_TSQL
helpviewer_keywords:
- sp_deletepeerrequesthistory
ms.assetid: 63a4ec6e-ce79-4bf1-9d37-5ac88f8d6beb
author: stevestein
ms.author: sstein
ms.openlocfilehash: e1af3aad1f66f3de7dd2fce44990718980018d3e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111946"
---
# <a name="spdeletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht Verlaufsdaten im Zusammenhang mit der eine Anforderung zum Veröffentlichungsstatus, die den anforderungsverlauf enthält ([MSpeer_request &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mspeer-request-transact-sql.md)) sowie den ([MSpeer_response &#40; Transact-SQL&#41;](../../relational-databases/system-tables/mspeer-response-transact-sql.md)). Diese gespeicherte Prozedur wird für die Veröffentlichungsdatenbank auf einem Verleger in einer Peer-zu-Peer-Replikationstopologie ausgeführt. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, für die die statusanforderung ausgeführt wurde. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @request_id = ] request_id` Gibt an eine einzelne statusanforderung an, sodass alle Antworten auf diese Anforderung gelöscht werden. *Request_id* ist **Int**, hat den Standardwert NULL.  
  
`[ @cutoff_date = ] cutoff_date` Gibt ein Datum, vor dem alle früheren antwortdatensätze gelöscht werden. *Cutoff_date* ist **"DateTime"** , hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_deletepeerrequesthistory** wird in einer Peer-zu-Peer-transaktionsreplikationstopologie verwendet. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 Beim Ausführen **Sp_deletepeerrequesthistory**, entweder *Request_id* oder *Cutoff_date* muss angegeben werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_deletepeerrequesthistory**.  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [Sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [Sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  
