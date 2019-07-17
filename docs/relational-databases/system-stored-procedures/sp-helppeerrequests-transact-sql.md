---
title: Sp_helppeerrequests (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5b9e2a370c9acc9c22dac7e5e60ceb10e08e46ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68137632"
---
# <a name="sphelppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu allen statusanforderungen empfangen, die von Teilnehmern in einer Peer-zu-Peer-Replikationstopologie, in denen diese Anforderungen, durch Ausführen initiiert wurden [Sp_requestpeerresponse &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) jederzeit veröffentlichte Datenbank in der Topologie. Diese gespeicherte Prozedur wird für die Veröffentlichungsdatenbank auf einem Verleger ausgeführt, der an der Peer-zu-Peer-Replikationstopologie beteiligt ist. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung in einer Peer-zu-Peer-Topologie, die für die statusanforderungen gesendet wurden. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @description = ] 'description'` Wert, der zum Identifizieren einzelner statusanforderungen, wodurch Sie zurückgegebene Antworten basierend auf Benutzer Filtern Informationen bereitgestellt definiert, wenn der Aufruf verwendet werden kann [Sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Beschreibung* ist **nvarchar(4000)** , hat den Standardwert **%** . Standardmäßig werden alle Statusanforderungen für die Veröffentlichung zurückgegeben. Dieser Parameter wird verwendet, um nur statusanforderungen mit einer Beschreibung, die dem Wert im angegebenen zurückzugeben *Beschreibung*, bei dem es sich bei Zeichenfolgen abgeglichen werden, eine [wie &#40;Transact-SQL&#41; ](../../t-sql/language-elements/like-transact-sql.md)Klausel.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifiziert eine Anforderung.|  
|**publication**|**sysname**|Name der Veröffentlichung, für die die Statusanforderung gesendet wurde.|  
|**sent_date**|**datetime**|Datum und Uhrzeit, zu der die Statusanforderung gesendet wurde.|  
|**description**|**nvarchar(4000)**|Benutzerdefinierte Informationen, die zum Identifizieren einzelner Statusanforderungen verwendet werden können.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helppeerrequests** wird in der Peer-zu-Peer-Transaktionsreplikation verwendet.  
  
 **Sp_helppeerrequests** wird verwendet, wenn das Wiederherstellen einer Datenbank in einer Peer-zu-Peer-Topologie veröffentlicht.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_helppeerrequests**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [Sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
