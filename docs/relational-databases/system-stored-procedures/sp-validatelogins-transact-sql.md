---
title: Sp_validatelogins (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: bd29100f8f7c54906b8aeafa98a7cf67f526db8b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68021055"
---
# <a name="spvalidatelogins-transact-sql"></a>sp_validatelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen zu Windows-Benutzern und Windows-Gruppen bereit, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prinzipalen zugeordnet sind, die in der Windows-Umgebung jedoch nicht mehr vorhanden sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_validatelogins  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**SID**|**varbinary(85)**|Windows-Sicherheits-ID (SID) des Windows-Benutzers oder der Windows-Gruppe.|  
|**NT-Anmeldung**|**sysname**|Der Name des Windows-Benutzers oder der Windows-Gruppe.|  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
