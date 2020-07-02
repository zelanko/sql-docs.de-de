---
title: sp_helppeerrequests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d86eeabda755e5b6546f3f5d800f1a35ba40e7e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786158"
---
# <a name="sp_helppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu allen von Teilnehmern in einer Peer-zu-Peer-Replikations Topologie empfangenen Status Anforderungen zurück, in denen diese Anforderungen durch Ausführen [sp_requestpeerresponse &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) in einer beliebigen veröffentlichten Datenbank in der Topologie initiiert wurden. Diese gespeicherte Prozedur wird für die Veröffentlichungsdatenbank auf einem Verleger ausgeführt, der an der Peer-zu-Peer-Replikationstopologie beteiligt ist. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung in einer Peer-zu-Peer-Topologie, für die Status Anforderungen gesendet wurden. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @description = ] 'description'`Ein Wert, der zum Identifizieren einzelner Status Anforderungen verwendet werden kann. Dadurch können Sie zurückgegebene Antworten auf der Grundlage von benutzerdefinierten Informationen filtern, die beim Aufrufen von [sp_requestpeerresponse &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)bereitgestellt werden. die *Beschreibung* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert **%** . Standardmäßig werden alle Statusanforderungen für die Veröffentlichung zurückgegeben. Dieser Parameter wird verwendet, um nur Status Anforderungen mit einer Beschreibung zurückzugeben, die mit dem in *Description*angegebenen Wert übereinstimmt, in dem Zeichen folgen mithilfe einer [like &#40;Transact-SQL-&#41;-](../../t-sql/language-elements/like-transact-sql.md) Klausel abgeglichen werden.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifiziert eine Anforderung.|  
|**ung**|**sysname**|Name der Veröffentlichung, für die die Statusanforderung gesendet wurde.|  
|**sent_date**|**datetime**|Datum und Uhrzeit, zu der die Statusanforderung gesendet wurde.|  
|**description**|**nvarchar(4000)**|Benutzerdefinierte Informationen, die zum Identifizieren einzelner Statusanforderungen verwendet werden können.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helppeerrequests** wird in der Peer-zu-Peer-Transaktions Replikation verwendet.  
  
 **sp_helppeerrequests** wird verwendet, wenn eine in einer Peer-zu-Peer-Topologie veröffentlichte Datenbank wieder hergestellt wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_helppeerrequests**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_deletepeerrequesthistory &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
