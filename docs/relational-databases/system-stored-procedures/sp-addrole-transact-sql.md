---
title: sp_addrole (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: f364de4eb2760c5beeae17360fb84ffd52fd7181
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85876744"
---
# <a name="sp_addrole-transact-sql"></a>sp_addrole (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Erstellt eine neue Datenbankrolle in der aktuellen Datenbank.  
  
> [!IMPORTANT]
>  **sp_addrole** ist aus Gründen der Kompatibilität mit früheren Versionen von enthalten [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und wird in einer zukünftigen Version möglicherweise nicht mehr unterstützt. Verwenden Sie stattdessen [Create Role](../../t-sql/statements/create-role-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addrole [ @rolename = ] 'role' [ , [ @ownername = ] 'owner' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'`Der Name der neuen Daten Bank Rolle. *role* ist vom Datentyp **sysname**und hat keinen Standardwert. die *Rolle* muss ein gültiger Bezeichner (ID) sein und darf nicht bereits in der aktuellen Datenbank vorhanden sein.  
  
`[ @ownername = ] 'owner'`Ist der Besitzer der neuen Daten Bank Rolle. *Owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert des aktuell ausgeführten Benutzers. der *Besitzer* muss ein Datenbankbenutzer oder eine Daten Bank Rolle in der aktuellen Datenbank sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Die Namen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankrollen können zwischen 1 und 128 Zeichen (Buchstaben, Sonderzeichen und Ziffern) enthalten. Die Namen von Daten bankrollen können nicht: einen umgekehrten Schrägstrich ( \\ ), NULL oder eine leere Zeichenfolge (**' '**) enthalten.  
  
 Nachdem Sie eine Daten Bank Rolle hinzugefügt haben, verwenden Sie [sp_addrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) , um der Rolle Prinzipale hinzuzufügen. Wenn mit den Anweisungen GRANT, DENY oder REVOKE Berechtigungen auf die Datenbankrolle angewendet werden, erben die Mitglieder der Datenbankrolle die Berechtigungen, als würden die Berechtigungen direkt auf die Konten dieser Mitglieder angewendet.  
  
> [!NOTE]  
>  Neue Serverrollen können nicht erstellt werden. Rollen können nur auf der Datenbankebene erstellt werden.  
  
 **sp_addrole** kann nicht innerhalb einer benutzerdefinierten Transaktion verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CREATE ROLE-Berechtigung für die Datenbank. Wenn Sie ein Schema erstellen, ist CREATE SCHEMA für die Datenbank erforderlich. Wenn *Owner* als Benutzer oder Gruppe angegeben ist, muss für diesen Benutzer bzw. diese Gruppe ein Identitätswechsel durchgeführt werden. Wenn *Owner* als Rolle angegeben wird, benötigt die ALTER-Berechtigung für diese Rolle oder für ein Mitglied dieser Rolle. Wenn der Besitzer als Anwendungsrolle angegeben wird, ist die ALTER-Berechtigung für diese Anwendungsrolle erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der aktuellen Datenbank die neue Rolle `Managers` hinzugefügt.  
  
```  
EXEC sp_addrole 'Managers';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)  
  
  
