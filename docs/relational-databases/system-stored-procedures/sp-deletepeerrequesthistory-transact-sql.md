---
description: sp_deletepeerrequesthistory (Transact-SQL)
title: sp_deletepeerrequesthistory (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 11773aa1e2a03ccc9b729c902a99cda10088c718
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474350"
---
# <a name="sp_deletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht den Verlauf im Zusammenhang mit einer Veröffentlichungsstatus Anforderung, die den Anforderungs Verlauf ([MSpeer_request &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mspeer-request-transact-sql.md)) sowie den Antwort Verlauf ([MSpeer_response &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mspeer-response-transact-sql.md)) enthält. Diese gespeicherte Prozedur wird für die Veröffentlichungs Datenbank auf einem Verleger ausgeführt, der Teil einer Peer-zu-Peer-Replikations Topologie ist. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, für die die Status Anforderung durchgeführt wurde. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @request_id = ] request_id` Gibt eine einzelne Status Anforderung an, sodass alle Antworten auf diese Anforderung gelöscht werden. *request_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
`[ @cutoff_date = ] cutoff_date` Gibt ein Umstellungs Datum an, vor dem alle früheren Antwortdaten Sätze gelöscht werden. *cutoff_date* ist vom **Datentyp DateTime**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_deletepeerrequesthistory** wird in einer Peer-zu-Peer-Transaktions Replikations Topologie verwendet. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 Beim Ausführen **sp_deletepeerrequesthistory**muss entweder *request_id* oder *cutoff_date* angegeben werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_deletepeerrequesthistory**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_helppeerrequests &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [sp_requestpeerresponse &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  
