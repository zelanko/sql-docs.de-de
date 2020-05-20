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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 60cd08c7ddf8ab520b6ff5e8ffb588b1a8f118c9
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828249"
---
# <a name="sp_redirect_publisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt einen umgeleiteten Verleger für ein vorhandenes Verleger-/Datenbankpaar an. Wenn die Verleger Datenbank zu einer Always on-Verfügbarkeits Gruppe gehört, ist der umgeleitete Verleger der verfügbarkeitsgruppenlistener-Name, der der Verfügbarkeits Gruppe zugeordnet ist.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @original_publisher = ] 'original_publisher'`Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die die Datenbank ursprünglich veröffentlicht hat. *original_publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Datenbank, die veröffentlicht wird. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @redirected_publisher = ] 'redirected_publisher'`Der verfügbarkeitsgruppenlistener-Name, der der Verfügbarkeits Gruppe zugeordnet ist, die der neue Verleger sein wird. *redirected_publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn für den Verfügbarkeitsgruppenlistener ein nicht standardmäßiger Port konfiguriert ist, geben Sie die Portnummer zusammen mit dem Listenernamen an, z. B. `'Listenername,51433'`.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 mit **sp_redirect_publisher** wird die Umleitung eines Replikations Verlegers zum aktuellen primären Replikat einer Always on Verfügbarkeits Gruppe ermöglicht, indem das Verleger-/Datenbankpaar dem Listener einer Verfügbarkeits Gruppe zugeordnet wird. Führen Sie **sp_redirect_publisher** aus, nachdem der Verfügbarkeits Gruppen-Listener für die Verfügbarkeits Gruppe konfiguriert wurde, die die veröffentlichte Datenbank enthält.  
  
 Wenn die Veröffentlichungs Datenbank auf dem ursprünglichen Verleger aus einer Verfügbarkeits Gruppe auf dem primären Replikat entfernt wird, führen Sie **sp_redirect_publisher** aus, ohne einen Wert für den * \@ redirected_publisher* -Parameter anzugeben, um die Umleitung für das Verleger-/Datenbankpaar zu entfernen. Weitere Informationen zum Umleiten des Verlegers bei finden Sie unter Verwalten [einer AlwaysOn-Veröffentlichungs Datenbank &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Der Aufrufer muss entweder ein Mitglied der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** für die Verteilungs Datenbank oder ein Mitglied einer Veröffentlichungs Zugriffsliste für eine der Verleger Datenbank zugeordnete definierte Veröffentlichung sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Replikations Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
