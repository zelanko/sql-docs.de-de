---
title: xp_enumgroups (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_enumgroups_TSQL
- xp_enumgroups
dev_langs:
- TSQL
helpviewer_keywords:
- xp_enumgroups
ms.assetid: 0bd3ed36-e260-469c-a5ff-b033fb9ea59d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 885e29f8abbeb185017bc2472566e41596a56900
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68116771"
---
# <a name="xp_enumgroups-transact-sql"></a>xp_enumgroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt eine Liste lokaler Microsoft Windows-Gruppen oder lokaler Gruppen bereit, die in einer angegebenen Windows-Domäne definiert sind.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_enumgroups [ 'domain_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 **"** *domain_name* **"**  
 Der Name der Windows-Domäne, für die eine Liste von globalen Gruppen aufgezählt wird. *domain_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**group**|**sysname**|Name der Windows-Gruppe|  
|**geäußert**|**sysname**|Eine von Windows bereitgestellte Beschreibung der Windows-Gruppe|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn *domain_name* der Name des Windows-basierten Computers ist, auf dem eine Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von ausgeführt wird, oder kein Domänen Name angegeben ist, listet **xp_enumgroups** die lokalen Gruppen auf dem Computer auf, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird.  
  
 **xp_enumgroups** kann nicht verwendet werden, wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz von unter Windows 98 ausgeführt wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Daten Bank Rolle **db_owner** in der **Master** -Datenbank oder die Mitgliedschaft in der festen Server Rolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Gruppen in der `sales`-Domäne aufgelistet.  
  
```  
EXEC xp_enumgroups 'sales';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_grantlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_loginconfig &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
