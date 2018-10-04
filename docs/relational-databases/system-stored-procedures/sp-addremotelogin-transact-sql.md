---
title: Sp_addremotelogin (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addremotelogin_TSQL
- sp_addremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addremotelogin
ms.assetid: 71b7cd36-a17d-4b12-b102-10aeb0f9268b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 409f3ea2229b57ef36b1e7e47f1684c914d5e50d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659924"
---
# <a name="spaddremotelogin-transact-sql"></a>sp_addremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt eine neue Remoteanmelde-ID auf dem lokalen Server hinzu. Dies ermöglicht es Remoteservern, eine Verbindung herzustellen und Remoteprozeduraufrufe auszuführen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Verwenden Sie stattdessen Verbindungsserver und gespeicherte Prozeduren, die über Verbindungsserver ausgeführt werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @remoteserver **=** ] **"***Remoteserver***"**  
 Der Name des Remoteservers, für den der Remoteanmeldename gilt. *remoteserver* ist vom Datentyp **sysname**und hat keinen Standardwert. Wenn nur *Remoteserver* angegeben ist, allen Benutzern *Remoteserver* Anmeldungen mit demselben Namen auf dem lokalen Server zugeordnet sind. Der Server muss dem lokalen Server bekannt sein. Dies wird mithilfe von Sp_addserver hinzugefügt. Wenn Benutzer auf *Remoteserver* Verbinden mit dem lokalen Server, der ausgeführt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um eine remote gespeicherte Prozedur auszuführen, die der lokalen Anmeldung, die auf ihrem eigenen Benutzernamen entspricht verbindenden *Remoteserver* . *Remoteserver* ist der Server, der den Remoteprozeduraufruf initiiert.  
  
 [ @loginame **=** ] **"***Anmeldung***"**  
 Die Anmelde-ID des Benutzers in der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. *Anmeldung*muss bereits vorhanden sein, auf der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn *Anmeldung* angegeben ist, allen Benutzern *Remoteserver* diesem lokalen Anmeldenamen zugeordnet sind. Wenn Benutzer auf *Remoteserver* Verbinden mit der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um eine remote gespeicherte Prozedur auszuführen, verbinden sie als *Anmeldung*.  
  
 [ @remotename **=** ] **"***Remote_name***"**  
 Die Anmelde-ID des Benutzers auf dem Remoteserver. *remote_name* ist vom Datentyp **sysname**und hat den Standardwert NULL. *Remote_name* muss vorhanden sein, auf *Remoteserver*. Wenn *Remote_name* angegeben ist, den jeweiligen Benutzer *Remote_name* zugeordnet *Anmeldung* auf dem lokalen Server. Wenn *Remote_name* auf *Remoteserver* eine Verbindung mit der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um eine remote gespeicherte Prozedur auszuführen, es stellt eine Verbindung her *Anmeldung*. Die Anmelde-ID des *Remote_name* kann sich von dem Anmeldenamen auf dem Remoteserver sein *Anmeldung*.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Um verteilte Abfragen auszuführen, verwenden Sie Sp_addlinkedsrvlogin.  
  
 Sp_addremotelogin kann nicht innerhalb einer benutzerdefinierten Transaktion verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der Sysadmin und der festen Serverrolle Securityadmin können Sp_addremotelogin ausführen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-mapping-one-to-one"></a>A. 1:1-Zuordnung  
 In diesem Beispiel werden Remotenamen lokalen Namen zugeordnet, wenn der Remoteserver `ACCOUNTS` und der lokale Server dieselben Benutzeranmeldenamen aufweisen.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-mapping-many-to-one"></a>B. 1:n-Zuordnung  
 In diesem Beispiel wird ein Eintrag erstellt, mit dem alle Benutzer auf dem Remoteserver `ACCOUNTS` dem lokalen Anmeldenamen `Albert` zugeordnet werden.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-using-explicit-one-to-one-mapping"></a>C. Verwenden einer expliziten 1:1-Zuordnung  
 Im folgenden Beispiel wird ein Remoteanmeldenamen für den Remotebenutzer `Chris` auf dem Remoteserver `ACCOUNTS` dem lokalen Benutzer `salesmgr` zugeordnet.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Sp_remoteoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
