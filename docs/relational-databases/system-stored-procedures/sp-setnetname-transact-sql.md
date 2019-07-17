---
title: Sp_setnetname (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03282ae181ec9fc032e5f64549840d3d292b385e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104398"
---
# <a name="spsetnetname-transact-sql"></a>sp_setnetname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt die Netzwerknamen **sys.servers** auf ihren tatsächlichen Netzwerkcomputernamen für Remoteinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mit dieser Prozedur können Aufrufe einer remote gespeicherten Prozedur für Computer aktiviert werden, deren Netzwerknamen ungültige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichner enthalten.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_setnetname  
@server = 'server',   
     @netname = 'network_name'  
```  
  
## <a name="arguments"></a>Argumente  
 **@server = '** *Server* **"**  
 Der Name des Remoteservers, wie er in der vom Benutzer codierten Syntax für den Aufruf einer remote gespeicherten Prozedur angesprochen wird. Genau eine Zeile in **sys.servers** muss bereits vorhanden sein, um diese Option verwenden *Server*. *server* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
 **@netname ='** *network_name* **'**  
 Der Netzwerkname des Computers, an den Aufrufe remote gespeicherter Prozeduren gesendet werden. *lt; Netzwerkname* ist **Sysname**, hat keinen Standardwert.  
  
 Dieser Name muss mit dem Namen des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Computernamens übereinstimmen und kann Zeichen enthalten, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Bezeichnern nicht zulässig sind.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Bei einigen Aufrufen einer remote gespeicherten Prozedur, die Computer unter Windows betreffen, können Probleme auftreten, wenn der Computername ungültige Bezeichner enthält.  
  
 Da sich Verbindungsserver und Remoteserver im selben Namespace befinden, können sie nicht dieselben Namen haben. Allerdings können Sie sowohl ein Verbindungsserver und definieren einen Remoteserver für einen bestimmten Server durch verschiedene Namen zuweisen und mit **Sp_setnetname** den Netzwerknamen eines dieser Elemente auf den Netzwerknamen des zugrunde liegenden Servers festlegen.  
  
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
>  Mithilfe von **Sp_setnetname** , zeigen Sie einen Verbindungsserver an den lokalen Server werden nicht unterstützt. Server, auf die auf diese Weise verwiesen wird, können nicht an einer verteilten Transaktion teilnehmen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Sysadmin** und **Setupadmin** festen Serverrollen.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel enthält eine typische Befehlsfolge für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], um den Aufruf einer remote gespeicherten Prozedur auszugeben.  
  
```  
USE master;  
GO  
EXEC sp_addserver 'Win_1';  
EXEC sp_setnetname 'Win_1','Win-1';  
EXEC Win_1.master.dbo.sp_who;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
