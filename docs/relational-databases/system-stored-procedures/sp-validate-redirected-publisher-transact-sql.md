---
title: Sp_validate_redirected_publisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validate_redirected_publisher
- sp_validate_redirected_publisher_TSQL
helpviewer_keywords:
- sp_validate_redirected_publisher
ms.assetid: 2b7fdbad-17e4-4442-b0b2-9b5e8f84b91d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56e490fa3a860b3fc4e18e72d674c70d29130f5b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527302"
---
# <a name="spvalidateredirectedpublisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Überprüft, ob der aktuelle Host für die Veröffentlichungsdatenbank die Replikation unterstützen kann. Muss von einer Verteilungsdatenbank ausgeführt werden. Diese Prozedur wird aufgerufen, indem **Sp_get_redirected_publisher**.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      sp_validate_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Argumente  
`[ @original_publisher = ] 'original_publisher'` Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die die Datenbank ursprünglich veröffentlicht. *Original_publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Datenbank veröffentlicht wird. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` Das Ziel der Umleitung angegeben, wenn **Sp_redirect_publisher** für das Verleger-/Datenbank-Paar aufgerufen wurde. *Redirected_publisher* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Wenn kein Eintrag für den Verleger und die Veröffentlichungsdatenbank vorhanden ist **Sp_validate_redirected_publisher** null im Ausgabeparameter zurückgegeben *@redirected_publisher*. Wenn ein Eintrag vorhanden ist, wird er im Ausgabeparameter in Erfolgs- und Fehlerfällen zurückgegeben.  
  
 Wenn die Überprüfung erfolgreich ist, **Sp_validate_redirected_publisher** eine erfolgsanzeige zurück.  
  
 Wenn die Überprüfung fehlschlägt, werden Fehler mit einer Fehlerbeschreibung ausgelöst.  
  
## <a name="permissions"></a>Berechtigungen  
 Aufrufer muss entweder ein Mitglied der **Sysadmin** festen Serverrolle, die **Db_owner** -Datenbankrolle für die Verteilungsdatenbank oder ein Mitglied einer veröffentlichungszugriffsliste für eine definierte Veröffentlichung die Publisher-Datenbank zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
