---
title: Sp_addserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addserver
- sp_addserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addserver
- renaming servers
- machine names [SQL Server]
- computer names
ms.assetid: 160a6b29-5e80-44ab-80ec-77d4280f627c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab5c15d15c77688c06eedec1d54e82c7b8199380
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492928"
---
# <a name="spaddserver-transact-sql"></a>sp_addserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Definiert den Namen der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn der Computer, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hostet, umbenannt wird, verwenden Sie **sp_addserver** , um der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz den neuen Computernamen mitzuteilen. Diese Prozedur muss in allen auf dem Computer gehosteten [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanzen ausgeführt werden. Der Instanzname von [!INCLUDE[ssDE](../../includes/ssde-md.md)] kann nicht geändert werden. Installieren Sie zum Ändern des Instanznamens für eine benannte Instanz eine neue Instanz mit dem gewünschten Namen, trennen Sie die Datenbankdateien aus der alten Instanz, fügen Sie der neuen Instanz die Datenbanken an, und löschen Sie die alte Instanz. Alternativ können Sie einen Aliasnamen für den Client auf dem Clientcomputer erstellen, um die Verbindung auf einen anderen Server- und Instanznamen oder die **Server: Port** -Kombination umzuleiten, ohne den Namen der Instanz auf dem Computer zu ändern.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addserver [ @server = ] 'server' ,  
     [ @local = ] 'local'   
     [ , [ @duplicate_ok = ] 'duplicate_OK' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server = ] 'server'` Ist der Name des Servers. Servernamen müssen eindeutig sein und den Regeln für [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Computernamen entsprechen; es sind jedoch keine Leerzeichen zulässig. *server* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 Sind mehrere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen auf einem Computer installiert, verhält sich jede Instanz so, als ob sie sich auf einem gesonderten Server befindet. Geben Sie eine benannte Instanz an, indem Sie auf *server* als *servername\instancename*verweisen.  
  
`[ @local = ] 'LOCAL'` Gibt an, dass der Server, der als lokaler Server hinzugefügt wird. **@local** ist **varchar(10)**, hat den Standardwert NULL. Angeben von **@local** als **lokalen** definiert **@server** als Name des lokalen Servers und bewirkt, dass der @@SERVERNAME Funktion, um den Wert zurück der *Server*.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup legt diese Variable während der Installation auf den Computernamen fest. Standardmäßig melden sich Benutzer mit dem Computernamen bei einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz an, ohne dass zusätzliche Konfigurationsschritte erforderlich sind.  
  
 Die lokale Definition wird erst nach dem Neustarten von [!INCLUDE[ssDE](../../includes/ssde-md.md)] wirksam. In jeder Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]kann nur ein lokaler Server definiert werden.  
  
`[ @duplicate_ok = ] 'duplicate_OK'` Gibt an, ob ein doppelter Servername zulässig ist. **@duplicate_OK** ist **varchar(13)**, hat den Standardwert NULL. **@duplicate_OK** den Wert ist nur möglich **Duplicate_OK** oder NULL. Wenn **duplicate_OK** angegeben wird und der hinzugefügte Servername bereits vorhanden ist, wird kein Fehler ausgelöst. Wenn keine benannten Parameter verwendet werden, **@local** muss angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie **sp_serveroption**, um Serveroptionen festzulegen oder zu löschen.  
  
 **sp_addserver** kann nicht innerhalb einer benutzerdefinierten Transaktion verwendet werden.  
  
 Die Verwendung von **sp_addserver** zum Hinzufügen eines Remoteservers wird eingestellt. Verwenden Sie stattdessen [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **setupadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Eintrag für den Namen des Computers, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hostet, in `ACCOUNTS`geändert.  
  
```  
sp_addserver 'ACCOUNTS', 'local';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Umbenennen eines Computers, das eine eigenständige Instanz von SQLServer hostet](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Sicherheitsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
