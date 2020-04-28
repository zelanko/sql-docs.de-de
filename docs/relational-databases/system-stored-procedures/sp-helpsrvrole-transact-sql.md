---
title: sp_helpsrvrole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpsrvrole_TSQL
- sp_helpsrvrole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrole
ms.assetid: 5c7f39f3-c261-4f70-8beb-08242d4ac242
author: stevestein
ms.author: sstein
ms.openlocfilehash: a632e6923ab3127a363650c63533fa548d1acc12
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006126"
---
# <a name="sp_helpsrvrole-transact-sql"></a>sp_helpsrvrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Liste der festen Serverrollen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpsrvrole [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @srvrolename = ] 'role'`Der Name der Server Rolle "Fixed". *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. die *Rolle* kann einen der folgenden Werte aufweisen.  
  
|Server Rolle "Fixed"|Beschreibung|  
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
|Beschreibung|**sysname**|Beschreibung von ServerRole.|  
  
## <a name="remarks"></a>Bemerkungen  
 Feste Serverrollen werden auf Serverebene definiert und haben Berechtigungen, um spezifische Verwaltungsfunktionen auf Serverebene auszuführen. Feste Serverrollen können nicht hinzugefügt, entfernt oder geändert werden.  
  
 Informationen zum Hinzufügen oder Entfernen von Mitgliedern zu Server Rollen finden Sie unter [Alter Server Role &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Alle Anmeldungen sind Mitglied von Public. sp_helpsrvrole erkennt die public-Rolle nicht, da von intern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht als Rolle implementiert wird.  
  
 sp_helpsrvrole nimmt keine benutzerdefinierte Server Rolle als Argument an. Informationen zum Auflisten der benutzerdefinierten Server Rollen finden Sie in den Beispielen unter [Alter Server Role &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der public-Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-the-fixed-server-roles"></a>A. Auflisten der festen Serverrollen  
 Die folgende Abfrage gibt eine Liste fester Serverrollen zurück.  
  
```  
EXEC sp_helpsrvrole ;  
```  
  
### <a name="b-listing-fixed-and-user-defined-server-roles"></a>B. Auflisten fester und benutzerdefinierter Serverrollen  
 Die folgende Abfrage gibt eine Liste fester und benutzerdefinierter Serverrollen zurück.  
  
```  
SELECT * FROM sys.server_principals WHERE type = 'R' ;  
```  
  
### <a name="c-returning-a-description-of-a-fixed-server-role"></a>C. Zurückgeben einer Beschreibung für eine feste Serverrolle  
 Die folgende Abfrage gibt den Namen und den Speicherort der festen Serverrollen von `diskadmin` zurück.  
  
```  
sp_helpsrvrole 'diskadmin' ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Rollen auf Server Ebene](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [sp_addsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
