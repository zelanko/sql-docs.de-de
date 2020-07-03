---
title: sp_setnetname (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setnetname
- sp_setnetname_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setnetname
ms.assetid: f416ba81-3835-4588-b0a3-2fe75589490e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 87401c8f90f0351f797aa3572c7717bb02360e00
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881519"
---
# <a name="sp_setnetname-transact-sql"></a>sp_setnetname (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Legt die Netzwerknamen in **sys. Servers** auf die tatsächlichen Netzwerk Computernamen für Remote Instanzen von fest [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Mit dieser Prozedur können Aufrufe einer remote gespeicherten Prozedur für Computer aktiviert werden, deren Netzwerknamen ungültige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichner enthalten.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>Argumente  
 ** @server = '** *Server* **'**  
 Der Name des Remoteservers, wie er in der vom Benutzer codierten Syntax für den Aufruf einer remote gespeicherten Prozedur angesprochen wird. Für die Verwendung dieses *Servers*muss bereits genau eine Zeile in **sys. Servers** vorhanden sein. *server* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 ** @netname = '** *network_name* **'**  
 Der Netzwerkname des Computers, an den Aufrufe remote gespeicherter Prozeduren gesendet werden. *network_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 Dieser Name muss mit dem Namen des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Computernamens übereinstimmen und kann Zeichen enthalten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichnern nicht zulässig sind.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Bei einigen Aufrufen einer remote gespeicherten Prozedur, die Computer unter Windows betreffen, können Probleme auftreten, wenn der Computername ungültige Bezeichner enthält.  
  
 Da sich Verbindungsserver und Remoteserver im selben Namespace befinden, können sie nicht dieselben Namen haben. Sie können jedoch sowohl einen Verbindungs Server als auch einen Remote Server für einen angegebenen Server definieren, indem Sie unterschiedliche Namen zuweisen und mithilfe von **sp_setnetname** den Netzwerknamen eines solchen Servers auf den Netzwerknamen des zugrunde liegenden Servers festlegen.  
  
```  
--Assume sqlserv2 is actual name of SQL Server   
--database server  
EXEC sp_addlinkedserver 'sqlserv2';  
GO  
EXEC sp_addserver 'rpcserv2';  
GO  
EXEC sp_setnetname 'rpcserv2', 'sqlserv2';  
```  
  
> [!NOTE]  
>  Die Verwendung von **sp_setnetname** , um einen Verbindungs Server zurück auf den lokalen Server zu verweisen, wird nicht unterstützt. Server, auf die auf diese Weise verwiesen wird, können nicht an einer verteilten Transaktion teilnehmen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in den festen Server Rollen **sysadmin** und **festen setupadmin** .  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel enthält eine typische Befehlsfolge für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], um den Aufruf einer remote gespeicherten Prozedur auszugeben.  
  
```  
USE master;  
GO  
EXEC sp_addserver 'Win_1';  
EXEC sp_setnetname 'Win_1','Win-1';  
EXEC Win_1.master.dbo.sp_who;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
