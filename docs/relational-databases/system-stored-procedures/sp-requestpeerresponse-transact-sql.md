---
title: Sp_requestpeerresponse (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_requestpeerresponse_TSQL
- sp_requestpeerresponse
helpviewer_keywords:
- sp_requestpeerresponse
ms.assetid: cbe13c22-4d7d-4a36-b194-7a13ce68ef27
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8d75b208cc91d52d20fb4e94340809cd6857fa1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129732"
---
# <a name="sprequestpeerresponse-transact-sql"></a>sp_requestpeerresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wenn diese Prozedur auf einem Knoten in einer Peer-zu-Peer-Topologie ausgeführt wird, fordert sie von jedem anderen Knoten in der Topologie eine Antwort an. Durch Ausführen dieser Prozedur und Überprüfen der entsprechenden Antworten können Sie sicherstellen, dass alle früheren Befehle an die antwortenden Knoten übermittelt wurden. Diese gespeicherte Prozedur wird auf dem anfordernden Knoten auf jeder Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_requestpeerresponse [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
    [ , [ @request_id = ] request_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung in einer Peer-zu-Peer-Topologie, die für die der Status überprüft wird. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @description = ] 'description'` Benutzerdefinierte Informationen, die zum Identifizieren einzelner statusanforderungen verwendet werden kann. *Beschreibung* ist **nvarchar(4000)** , hat den Standardwert NULL.  
  
`[ @request_id = ] request_id` Gibt die ID der neuen Anforderung zurück. *Request_id* ist **Int** und ein OUTPUT-Parameter ist. Dieser Wert kann verwendet werden, bei der Ausführung [Sp_helppeerresponses &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) um alle Antworten auf eine statusanforderung anzuzeigen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_requestpeerresponse** wird in der Peer-zu-Peer-Transaktionsreplikation verwendet.  
  
 **Sp_requestpeerresponse** wird verwendet, um sicherzustellen, dass alle Befehle von allen anderen Knoten erhalten haben, bevor das Wiederherstellen einer Datenbank in einer Peer-zu-Peer-Topologie veröffentlicht. Die Prozedur wird außerdem beim Replizieren von DDL-Änderungen (Data Definition Language) verwendet, die vorgenommen wurden, während ein Knoten offline war. Damit kann abgeschätzt werden, wann diese Änderungen bei den anderen Knoten ankommen.  
  
 **Sp_requestpeerresponse** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_requestpeerresponse**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [Sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
