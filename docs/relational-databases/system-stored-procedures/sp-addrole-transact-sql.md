---
title: Sp_addrole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addrole
- sp_addrole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addrole
ms.assetid: e8a21642-8440-419a-8585-93d3d9d44f00
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 1711ec3941a5fced5ef9e0c32808d6153b673e2b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68030919"
---
# <a name="spaddrole-transact-sql"></a>sp_addrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt eine neue Datenbankrolle in der aktuellen Datenbank.  
  
> [!IMPORTANT]
>  **Sp_addrole** wird aus Gründen der Kompatibilität mit früheren Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und werden in einer zukünftigen Version möglicherweise nicht unterstützt. Verwendung [CREATE ROLE](../../t-sql/statements/create-role-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addrole [ @rolename = ] 'role' [ , [ @ownername = ] 'owner' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'` Ist der Name der neuen Datenbankrolle. *role* ist vom Datentyp **sysname**und hat keinen Standardwert. *Rolle* muss ein gültiger Bezeichner (ID) sein und muss nicht in der aktuellen Datenbank bereits vorhanden.  
  
`[ @ownername = ] 'owner'` Ist der Besitzer der neuen Datenbankrolle. *Besitzer* ist eine **Sysname**, hat den Standardwert des aktuellen Benutzers ausgeführt. *Besitzer* ein Datenbankbenutzer oder eine Datenbankrolle in der aktuellen Datenbank sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Die Namen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankrollen können zwischen 1 und 128 Zeichen (Buchstaben, Sonderzeichen und Ziffern) enthalten. Die Namen von Datenbankrollen können nicht: einen umgekehrten Schrägstrich enthalten (\\), der NULL sein, oder eine leere Zeichenfolge ( **''** ).  
  
 Nachdem Sie eine Datenbankrolle hinzuzufügen, verwenden Sie [Sp_addrolemember &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) zu der Rolle Prinzipale hinzuzufügen. Wenn mit den Anweisungen GRANT, DENY oder REVOKE Berechtigungen auf die Datenbankrolle angewendet werden, erben die Mitglieder der Datenbankrolle die Berechtigungen, als würden die Berechtigungen direkt auf die Konten dieser Mitglieder angewendet.  
  
> [!NOTE]  
>  Neue Serverrollen können nicht erstellt werden. Rollen können nur auf der Datenbankebene erstellt werden.  
  
 **Sp_addrole** kann nicht innerhalb einer benutzerdefinierten Transaktion verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CREATE ROLE-Berechtigung für die Datenbank. Wenn Sie ein Schema erstellen, ist CREATE SCHEMA für die Datenbank erforderlich. Wenn *Besitzer* als Benutzer oder Gruppe angegeben wird, ist IMPERSONATE für diesen Benutzer oder Gruppe erforderlich. Wenn *Besitzer* als Rolle angegeben wird, erfordert die ALTER-Berechtigung für diese Rolle oder ein Mitglied dieser Rolle. Wenn der Besitzer als Anwendungsrolle angegeben wird, ist die ALTER-Berechtigung für diese Anwendungsrolle erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der aktuellen Datenbank die neue Rolle `Managers` hinzugefügt.  
  
```  
EXEC sp_addrole 'Managers';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)  
  
  
