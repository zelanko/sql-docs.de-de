---
title: sp_validatelogins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_validatelogins
- sp_validatelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_validatelogins
ms.assetid: 6ac52e21-e20d-469b-ad40-5aa091e06b61
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 149831d9926161f697c69a893c00784230480940
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723016"
---
# <a name="sp_validatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Stellt Informationen zu Windows-Benutzern und Windows-Gruppen bereit, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prinzipalen zugeordnet sind, die in der Windows-Umgebung jedoch nicht mehr vorhanden sind.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_validatelogins  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**SID**|**varbinary(85)**|Windows-Sicherheits-ID (SID) des Windows-Benutzers oder der Windows-Gruppe.|  
|**NT Login**|**sysname**|Der Name des Windows-Benutzers oder der Windows-Gruppe.|  
  
## <a name="remarks"></a>Hinweise  
 Falls der verwaiste Prinzipal auf Serverebene einen Datenbankbenutzer besitzt, muss der Datenbankbenutzer entfernt werden, bevor der verwaiste Serverprinzipal entfernt werden kann. Verwenden Sie zum Entfernen eines Datenbankbenutzers [DROP USER](../../t-sql/statements/drop-user-transact-sql.md). Falls der Prinzipal auf Serverebene sicherungsfähige Elemente in der Datenbank besitzt, muss der Besitz der sicherungsfähigen Elemente übertragen werden, oder die sicherungsfähigen Elemente müssen gelöscht werden. Verwenden Sie [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md), um den Besitz von sicherungsfähigen Datenbankelementen zu übertragen.  
  
 Verwenden Sie [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md), um Zuordnungen zu nicht mehr vorhandenen Windows-Benutzern und Windows-Gruppen zu entfernen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** oder **securityadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Windows-Benutzer und Windows-Gruppen angezeigt, die nicht mehr vorhanden sind, die jedoch weiterhin auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zugreifen können.  
  
```  
EXEC sp_validatelogins;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Drop User &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [Drop Login &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
