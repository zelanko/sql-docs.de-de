---
description: sp_helpsrvrolemember (Transact-SQL)
title: sp_helpsrvrolemember (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpsrvrolemember
- sp_helpsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrolemember
ms.assetid: d0714913-8d6b-4de3-b042-3ae9934f839d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 189e26484ced5c955db570ad2d5f4cbe4a36e78c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89535099"
---
# <a name="sp_helpsrvrolemember-transact-sql"></a>sp_helpsrvrolemember (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt Informationen zu Mitgliedern einer festen Serverrolle von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpsrvrolemember [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @srvrolename = ] 'role'` Der Name einer Server Rolle mit fester Größe. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. Wenn *Role*nicht angegeben wird, enthält das Resultset Informationen zu allen festgelegten Server Rollen.  
  
 die *Rolle* kann einen der folgenden Werte aufweisen.  
  
|Server Rolle "Fixed"|BESCHREIBUNG|  
|-----------------------|-----------------|  
|Serverrollen|Systemadministratoren|  
|securityadmin|Sicherheitsadministratoren|  
|serveradmin|Serveradministratoren|  
|setupadmin|Setupadministratoren|  
|processadmin|Prozessadministratoren|  
|diskadmin|Datenträgeradministratoren|  
|dbcreator|Datenbankersteller|  
|bulkadmin|Kann BULK INSERT-Anweisungen ausführen|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|ServerRole|**sysname**|Name der Serverrolle.|  
|MemberName|**sysname**|Name eines Mitglieds von ServerRole.|  
|MemberSID|**varbinary(85)**|Sicherheits-ID des Mitgliedsnamens|  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie sp_helprolemember, um die Mitglieder einer Daten Bank Rolle anzuzeigen.  
  
 Alle Anmeldungen sind Mitglied von Public. sp_helpsrvrolemember erkennt die public-Rolle nicht, da von intern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht als Rolle implementiert wird.  
  
 Informationen zum Hinzufügen oder Entfernen von Mitgliedern zu Server Rollen finden Sie unter [Alter Server Role &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 sp_helpsrvrolemember nimmt keine benutzerdefinierte Server Rolle als Argument an. Informationen zum Bestimmen der Mitglieder einer benutzerdefinierten Server Rolle finden Sie in den Beispielen unter [Alter Server Role &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel listet die Mitglieder der festen Serverrolle `sysadmin` auf.  
  
```  
EXEC sp_helpsrvrolemember 'sysadmin';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_helprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_helprolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprolemember-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
