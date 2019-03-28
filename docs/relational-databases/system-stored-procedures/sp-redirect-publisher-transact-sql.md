---
title: Sp_redirect_publisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_redirect_publisher_TSQL
- sp_redirect_publisher
helpviewer_keywords:
- sp_redirect_publisher
ms.assetid: af45e2b2-57fb-4bcd-a58b-e61401fb3b26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5458d7a7693c742768a9a8a5e0c2f8583f1ca9ba
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535612"
---
# <a name="spredirectpublisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt einen umgeleiteten Verleger für ein vorhandenes Verleger-/Datenbankpaar an. Wenn die Verlegerdatenbank zu einer AlwaysOn-Verfügbarkeitsgruppe gehört, ist der umgeleitete Verleger der verfügbarkeitsgruppenlistener-Namen mit der verfügbarkeitsgruppe verknüpft ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @original_publisher = ] 'original_publisher'` Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die die Datenbank ursprünglich veröffentlicht. *Original_publisher* ist **Sysname**, hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der Datenbank veröffentlicht wird. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` Der verfügbarkeitsgruppenlistener-Namen der verfügbarkeitsgruppe, die den neuen Verleger zugeordnet. *Redirected_publisher* ist **Sysname**, hat keinen Standardwert. Wenn für den Verfügbarkeitsgruppenlistener ein nicht standardmäßiger Port konfiguriert ist, geben Sie die Portnummer zusammen mit dem Listenernamen an, z. B. `'Listenername,51433'`.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **Sp_redirect_publisher** wird verwendet, damit ein Replikationsverleger mit dem aktuellen primären Replikat einer Always On-verfügbarkeitsgruppe umgeleitet werden, indem das Verleger-/Datenbankpaar Listener einer verfügbarkeitsgruppe zugeordnet. Führen Sie **Sp_redirect_publisher** nachdem der AG-Listener für die verfügbarkeitsgruppe konfiguriert wurde, die die veröffentlichte Datenbank enthält.  
  
 Wenn die Veröffentlichungsdatenbank beim ursprünglichen Verleger aus einer verfügbarkeitsgruppe auf dem primären Replikat entfernt wird, führen Sie **Sp_redirect_publisher** ohne Angabe eines Werts für die *@redirected_publisher* Parameter, um die Umleitung für das Verleger-/Datenbankpaar zu entfernen. Weitere Informationen zum Umleiten des Verlegers, finden Sie unter [Warten einer AlwaysOn-Veröffentlichungsdatenbank &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Aufrufer muss entweder ein Mitglied der **Sysadmin** festen Serverrolle, die **Db_owner** -Datenbankrolle für die Verteilungsdatenbank oder ein Mitglied einer veröffentlichungszugriffsliste für eine definierte Veröffentlichung die Publisher-Datenbank zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
