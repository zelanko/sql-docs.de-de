---
title: sp_validate_redirected_publisher (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: b01fba8260e86d135e740964022187b9914e5fc0
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252050"
---
# <a name="sp_validate_redirected_publisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Überprüft, ob der aktuelle Host für die Veröffentlichungsdatenbank die Replikation unterstützen kann. Muss von einer Verteilungsdatenbank ausgeführt werden. Diese Prozedur wird von **sp_get_redirected_publisher**aufgerufen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      sp_validate_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Argumente  
`[ @original_publisher = ] 'original_publisher'` der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], von dem die Datenbank ursprünglich veröffentlicht wurde. *original_publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` den Namen der Datenbank, die veröffentlicht wird. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` das Ziel der Umleitung, das angegeben wurde, als **sp_redirect_publisher** für das Verleger-/Datenbankpaar aufgerufen wurde. *redirected_publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Wenn kein Eintrag für den Verleger und die Veröffentlichungs Datenbank vorhanden ist, gibt **sp_validate_redirected_publisher** NULL im Output *-Parameter \@redirected_publisher*zurück. Wenn ein Eintrag vorhanden ist, wird er im Ausgabeparameter in Erfolgs- und Fehlerfällen zurückgegeben.  
  
 Wenn die Überprüfung erfolgreich ist, gibt **sp_validate_redirected_publisher** einen Erfolgsindikator zurück.  
  
 Wenn die Überprüfung fehlschlägt, werden Fehler mit einer Fehlerbeschreibung ausgelöst.  
  
## <a name="permissions"></a>Berechtigungen  
 Der Aufrufer muss entweder ein Mitglied der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** für die Verteilungs Datenbank oder ein Mitglied einer Veröffentlichungs Zugriffsliste für eine der Verleger Datenbank zugeordnete definierte Veröffentlichung sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
