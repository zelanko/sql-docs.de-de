---
title: Sp_replsetoriginator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replsetoriginator
- sp_replsetoriginator_TSQL
helpviewer_keywords:
- sp_replsetoriginator
ms.assetid: 030e5226-0585-439f-b8cd-36f48367d86d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0f72558a573e0cee0ab7fb2ab9b762246964a884
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526182"
---
# <a name="spreplsetoriginator-transact-sql"></a>sp_replsetoriginator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird zum Aufrufen der Loopbackerkennung und -verarbeitung bei der Transaktionsreplikation verwendet. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replsetoriginator [ @server_name= ] 'server_name'   
    , [ @database_name= ] 'database_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server_name = ] 'server_name'` Ist der Name des Servers ein, in dem die Transaktion angewendet wird. *Originating_server* ist **Sysname**, hat keinen Standardwert.  
  
`[ @database_name = ] 'database_name'` Ist der Name der Datenbank, in dem die Transaktion angewendet wird. *Originating_db* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replsetoriginator** wird ausgeführt, indem der Verteilungs-Agent, um die Quelle der Transaktionen, die von der Replikation angewendet aufzuzeichnen. Mithilfe dieser Informationen wird die Loopbackerkennung für bidirektionale Transaktionsabonnements aufgerufen, bei denen die Loopbackeigenschaft festgelegt ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** auf dem Verleger, Mitglieder der festen Serverrolle die **Db_owner** -Datenbankrolle in der Veröffentlichungsdatenbank oder Benutzer in der veröffentlichungszugriffsliste (PAL) kann Ausführen**Sp_replsetoriginator**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
