---
title: sp_addremotelogin (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: eb45ce1c3e1786eb5a9a3cd630741dd4df773c40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030960"
---
# <a name="sp_addremotelogin-transact-sql"></a>sp_addremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt eine neue Remoteanmelde-ID auf dem lokalen Server hinzu. Dies ermöglicht es Remoteservern, eine Verbindung herzustellen und Remoteprozeduraufrufe auszuführen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Verwenden Sie stattdessen Verbindungsserver und gespeicherte Prozeduren, die über Verbindungsserver ausgeführt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @remoteserver **=** ] **'**_Remote Server_**'**  
 Der Name des Remoteservers, für den der Remoteanmeldename gilt. *Remote Server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Wenn nur *Remote Server* angegeben ist, werden alle Benutzer von *Remote Server* vorhandenen Anmeldungen desselben Namens auf dem lokalen Server zugeordnet. Der Server muss dem lokalen Server bekannt sein. Dies wird mit sp_addserver hinzugefügt. Wenn Benutzer von *Remote Server* eine Verbindung mit dem lokalen Server herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem ausgeführt wird, um eine remote gespeicherte Prozedur auszuführen, wird eine Verbindung mit der lokalen Anmeldung hergestellt, die ihrer eigenen Anmeldung auf dem *Remote Server*entspricht. *Remote Server* ist der Server, der den Remote Prozedur aufrufsvorgang initiiert.  
  
 [ @loginame **=** ] **'**_Login_**'**  
 Die Anmelde-ID des Benutzers in der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Login* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. die *Anmeldung*muss bereits in der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vorhanden sein. Wenn *Login* angegeben wird, werden alle Benutzer von *Remote Server* diesem speziellen lokalen Anmelde Namen zugeordnet. Wenn Benutzer von *Remote Server* eine Verbindung mit der lokalen Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von herstellen, um eine remote gespeicherte Prozedur auszuführen, stellen Sie eine Verbindung als *Login*her.  
  
 [ @remotename **=** ] **'**_remote_name_**'**  
 Die Anmelde-ID des Benutzers auf dem Remoteserver. *remote_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. auf dem *Remote Server*muss *remote_name* vorhanden sein. Wenn *remote_name* angegeben wird, wird der jeweilige Benutzer *remote_name* der *Anmeldung* auf dem lokalen Server zugeordnet. Wenn *remote_name* auf *Remote Server* eine Verbindung mit der lokalen Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von herstellt, um eine remote gespeicherte Prozedur auszuführen, wird die Verbindung als *Login*hergestellt. Die Anmelde-ID *remote_name* kann sich von der Anmelde-ID auf dem Remote Server, der *Anmeldung*, unterscheiden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Führen Sie verteilte Abfragen mit sp_addlinkedsrvlogin aus.  
  
 sp_addremotelogin kann nicht innerhalb einer benutzerdefinierten Transaktion verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrollen sysadmin und securityadmin können sp_addremotelogin ausführen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addlinkedsrvlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
