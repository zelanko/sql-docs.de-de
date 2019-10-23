---
title: sp_redirect_publisher (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 6062522ca6c5c3a311ba2f2c796f791c47e874ab
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252115"
---
# <a name="sp_redirect_publisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt einen umgeleiteten Verleger für ein vorhandenes Verleger-/Datenbankpaar an. Wenn die Verleger Datenbank zu einer Always on-Verfügbarkeits Gruppe gehört, ist der umgeleitete Verleger der verfügbarkeitsgruppenlistener-Name, der der Verfügbarkeits Gruppe zugeordnet ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @original_publisher = ] 'original_publisher'` der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], von dem die Datenbank ursprünglich veröffentlicht wurde. *original_publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` den Namen der Datenbank, die veröffentlicht wird. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` der verfügbarkeitsgruppenlistener-Name, der der Verfügbarkeits Gruppe zugeordnet ist, die der neue Verleger sein wird. *redirected_publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn für den Verfügbarkeitsgruppenlistener ein nicht standardmäßiger Port konfiguriert ist, geben Sie die Portnummer zusammen mit dem Listenernamen an, z. B. `'Listenername,51433'`.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **sp_redirect_publisher** wird verwendet, um zuzulassen, dass ein Replikations Verleger zum aktuellen primären Replikat einer Always on Verfügbarkeits Gruppe umgeleitet wird, indem das Verleger-/Datenbankpaar dem Listener einer Verfügbarkeits Gruppe zugeordnet wird. Führen Sie **sp_redirect_publisher** aus, nachdem der Verfügbarkeits Gruppen-Listener für die Verfügbarkeits Gruppe konfiguriert wurde, die die veröffentlichte Datenbank enthält.  
  
 Wenn die Veröffentlichungs Datenbank auf dem ursprünglichen Verleger aus einer Verfügbarkeits Gruppe auf dem primären Replikat entfernt wird, führen Sie **sp_redirect_publisher** ohne Angabe eines Werts für den *\@redirected_publisher-* Parameter aus, um das Umleitung für das Verleger-/Datenbankpaar. Weitere Informationen zum Umleiten des Verlegers bei finden Sie unter Verwalten [einer AlwaysOn- &#40;Veröffentlichungs&#41;Datenbank SQL Server](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Der Aufrufer muss entweder ein Mitglied der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** für die Verteilungs Datenbank oder ein Mitglied einer Veröffentlichungs Zugriffsliste für eine der Verleger Datenbank zugeordnete definierte Veröffentlichung sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
